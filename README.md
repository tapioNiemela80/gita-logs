# 🔴 ☢️ BHAGAVAD GITAN LOKIT ☢️ 🔴

## LUKU 1: Sanjayan näky ja Kurukshetran commit-historia

**Sokea omistaja kysyy tilannetta**

Dhritarashtra oli sokea. Hän ei ollut koskaan katsonut koodikantaa itse, eikä hänellä ollut pääsyä suorituskykymittareihin. Hän oli tuoteomistaja (Product Owner), joka istui johtoryhmän huoneessa ja halusi tietää vain yhden asian: joko sprinteissä valatut ominaisuudet olivat tuotannossa.

Hän kääntyi Sanjayan puoleen. Sanjay oli tiimin arkkitehtuurikuiskaaja ja CI/CD-putken ylläpitäjä, jolle oli suotu *divya-drishti* – jumalallinen näkyvystoiminto, reaaliaikainen kaikkien mikropalvelulokeihin ja PR-katselmointeihin yltävä observability-työkalu.

**Dhritarashtra:**

*"Sanjay! Kun minun tiimini (Kauravat) ja Pandavat kumpikin kokoontuivat Kurukshetran repo-haaraan tekemään katselmointejaan, mitä koodipohjalle tapahtui?"*

**Sanjay raportoi taistelukentältä**

**Sanjay:**

*"Oi kuningas, Duryodhana – Just Ship It -legioonan komentaja – katsoi Pandavien arkkitehtuurikenttää. Hän näki heidän DDD-mallinsa jäsenneltynä, Value Objectien suojattuna ja tietokantamigraatioiden luotettavana. Hän säikähti ja riensi heti vanhan opettajansa Dronan puoleen."*

Duryodhana katsoi Pandavien repo-haaraa ja yritti lohduttautua vähättelemällä heidän tietomalliaan.

**Duryodhana:**

*"Katso, mestari, miten laaja heidän domain-mallinsa on! Heillä on siellä ehdottomia invariantteja, tiukkoja Aggregate Rooteja ja immutaabeleita luokkia. Mutta katso meidän armeijaamme! Meillä on täällä nopeat getterit ja setterit, julkiset muuttujat, globaali tila ja pikaiset hotfixit. Meidän joukkomme ovat rajattomat, heidän mallinsa on kankea!"*

Duryodhana käski puhaltaa taistelutorviin: mergetköön kukin omat muutoshaaransa ilman arkkitehtuurikatselmointia! Ilmaan kajahti sotatorvien sarvi: *Just Ship It!*

Putket kääntyivät keltaisiksi, ja varoitukset täyttivät build-lokit.

Vastapuolella Pandavien sotavaunuissa istuivat Arjuna ja hänen vaununajajansa Krishna. Heidän sotavaununsa ei pyörinyt millään tavallisella alustalla, vaan se oli rakennettu täydellisesti testatun asynkronisen tapahtumaytimen päälle.

Arjuna pyysi Krishnaa ajamaan vaunut kahden haaran väliin.

**Arjuna kahden armeijan välissä**

**Arjuna:**

*"Krishna, aja minun kehitysympäristöni tähän keskelle. Haluan nähdä ne, jotka ovat ryhtyneet tähän taisteluun. Haluan nähdä muutoksen, joka minun pitäisi hyväksyä tai hylätä."*

Krishna ajoi vaunut keskelle Kurukshetran commit-historiaa – feature-haaran ja `main`-haaran väliin, paikkaan, jossa paikallisesti järkevä muutos ja domain-mallin pitkäaikainen eheys kohtasivat.

Arjuna katsoi molemmille puolille, ja hänen sydämensä murtui.

Toisella puolella – Just Ship It -rintamassa – seisoi hänen omia vanhoja committejaan. Siellä olivat luokat, jotka hän oli itse kirjoittanut viisi vuotta sitten kiireessä periaatteella *"korjataan tämä myöhemmin"*. Siellä oli Drona, vanha opetuskoodipohja, josta hän oli oppinut ensimmäiset ohjelmointikielensä. Siellä oli Bhishma, vanha infrastruktuuri, jota kukaan ei uskaltanut purkaa. Siellä olivat hänen tiimikaverinsa, joiden kanssa hän oli juonut kahvia ja juhlinut onnistuneita tuotantoonsiirtoja.

Ja toisella puolella olivat DDD-ihanteet, joita hän oli lupautunut puolustamaan.

**Arjuna:**

*"Krishna! Kun näen omat kollegani ja oman historiallisen koodini vastakkain tuolla kentällä, käteni alkavat täristä. Suuni kuivuu. Minun näppäimistöni tippuu sylistäni."*

**Mielen lamaannus (Arjuna Vishada Yoga)**

Arjuna katsoi merge requestia. Muutos oli pieni: `Money`-Value Objectin sisäinen rakenne haluttiin paljastaa getter-metodeilla, jotta mapperi voisi rakentaa ulkoisen DTO:n.

```java
public final class Money {

    private final BigDecimal amount;
    private final Currency currency;

    public BigDecimal getAmount() {
        return amount;
    }

    public Currency getCurrency() {
        return currency;
    }
}
```

Perustelu oli moitteeton:

> Tarvitsemme vain summan ja valuutan mapperissa. Muutos ei muuta käyttäytymistä.

Pipeline oli vihreä. Kaikki testit menivät läpi. `Money` oli edelleen immutaabeli, eikä yksikään nykyinen käyttötapaus rikkoutunut.

Juuri siksi Arjuna pelkäsi muutosta.

**Arjuna:**

*"Krishna, miten voisin hylätä tämän? He todella tarvitsevat summan ja valuutan rajapintaan. Kentät ovat jo olemassa, eikä niiden lukeminen muuta oliota. Kollegani eivät tee mitään ilmeisen väärää.*

*Mutta jos hyväksyn tämän, `Money` lakkaa vähitellen olemasta laskennan suorittava käsite. Sen sisäinen rakenne leviää mappereihin, palveluihin ja ehtoihin. Jokainen ottaa summan ulos, tekee sille jotakin ja yrittää koota rahan takaisin.*

*Jos puolustan kapselointia, näytän dogmaatikolta. Jos hyväksyn getterit perustelematta rajaa, autan itse rakentamaan sen aneemisen mallin, jota vastaan olen luvannut taistella.*

*Mitä hyötyä on vihreästä buildista, jos jokainen vihreä testi vahvistaa mallia, joka sanoo domainista yhä vähemmän?"*

Arjuna ei pelännyt kahta metodia. Hän pelkäsi maailmaa, joka alkaisi rakentaa niiden varaan.

Hän ei halunnut painaa *Approve*, hän ei halunnut painaa *Reject*.

**Sanjay:**

*"Näin sanottuaan Arjuna heitti jousensa – oman IDE-ikkunansa – kiinni taistelukentän keskellä. Hän istui alas sotavaunujen pohjalle, sulki terminaalin ja puristi päätään käsissään, murheen murtamana."*

## LUKU 2: Krishnan arkkitehtuurikoulu ja kuolemattomat invariantit

**Arjuna luhistuu näppäimistön äärelle**

**Sanjay:**

*"Katsoessaan Arjunaa, joka istui kyyneleet silmissä suljetun läppärin ääressä, Krishna – sovellusarkkitehtuurin korkein haltija – katsoi häntä lempeän napakasti ja lausui seuraavat sanat."*

**Krishna:**

*"Arjuna! Mistä tämä heikkous tulee keskellä kiireisintä sprinttiä? Tämä ei ole arkkitehdin arvoista, eikä se vie sinua tuotantoon. Nouse ylös, sulje valituskanava Slackissa ja tartu toimeen!"*

**Arjuna:**

*"Krishna, miten voisin hylätä tämän muutoksen? Mapperi todella tarvitsee rahan representaation. Getterit eivät muuta tilaa, eikä nykyinen testi rikkoudu. Mutta miten voisin hyväksyä sen, että muu järjestelmä alkaa käyttää `Money`-olion sisäistä rakennetta omana ohjelmointimallinaan?"*

Krishna katsoi diffiä ja kysyi:

*"Tarvitseeko mapperi `Money`-olion sisäisen rakenteen – vai tarvitseeko se `Money`-oliolta representaation?"*

**Invariantin kuolemattomuus (Sankhya Yoga)**

Krishna hymyili kevyesti. Hän ei julistanut jokaista getteriä adharmaksi eikä tarjonnut yhtä universaalia rajapintaa. Hän siirsi keskustelun käsitteen vastuuseen, jota Arjuna ei ollut vielä osannut ilmaista.

**Krishna:**

*"Sinä murehdit asioita, joita ei pitäisi murehtia, vaikka puhut viisaita sanoja. Viisas arkkitehti ei murehdi sitä, mikä poistetaan, eikä sitä, mikä luodaan.*

*Ei ole koskaan ollut aikaa, jolloin tätä liiketoimintasääntöä ei olisi ollut olemassa. Eikä tule aikaa, jolloin se lakkaa olemasta.*

*Niin kuin ilmaantunut käsite käy läpi lapsuuden, nuoruuden ja vanhuuden, samoin data vaihtaa muotoaan toteutuksesta toiseen. DTO tarvitsee representaation, mutta representaation ei tarvitse määrätä käsitteen käyttäytymistä."*

`Money` voi itse suojella laskentaa ja tarjota samalla rajalle eksplisiittisen representaation:

```java
public final class Money {

    private final BigDecimal amount;
    private final Currency currency;

    public Money subtract(Money other) {
        requireSameCurrency(other);
        return new Money(amount.subtract(other.amount), currency);
    }

    public MoneyRepresentation representation() {
        return new MoneyRepresentation(amount, currency);
    }
}
```

Tämä ei ole ainoa oikea API. Joskus `record Money(BigDecimal amount, Currency currency)` on täysin rehellinen malli, ja joskus infrastruktuurin adapteri saa lukea pysyvyyteen tarvittavan representaation. Ratkaisevaa ei ole getterin syntaksi vaan se, **kuka tekee rahan liiketoiminnalliset päätökset**.

```java
var discountedAmount = money.getAmount()
        .subtract(discount.getAmount());

return new Money(discountedAmount, money.getCurrency());
```

Kun tällainen laskenta leviää ulkopuolelle, `Money` on nimellisesti Value Object mutta käytännössä jälleen kaksi primitiiviä. Ulkopuolinen koodi vastaa nyt laskutoimituksesta, valuutan säilymisestä, pyöristyksestä, tuloksen validiudesta ja uuden olion kokoamisesta.

> **Value Object saa tarjota ulkoisen representaation. Sen ei tarvitse luovuttaa sisäistä rakennettaan muun järjestelmän ohjelmointimalliksi.**

Krishna katsoi getter-metodeja, DTO:ta ja niiden takana olevaa käsitettä. Ne eivät olleet sama asia.

**Krishna:**

*"Sillä, mikä on pelkkää toteutustapaa (accidental complexity), ei ole pysyvää olemassaoloa. Sillä, mikä on aito liiketoiminnan invariantti (essential complexity), ei ole lakkaamista.*

*Koodirivit, frameworkit, getterit ja tietokantaskeemat syntyvät ja kuolevat. Ne ovat kuin vaatteita, jotka käsite pukee päälleen ja riisuu taas pois. Jos `Money` muuttuu luokasta recordiksi tai sen DTO korvataan toisella representaatiolla, luuletko rahan arvon ja valuutan yhteyden kuolleen?*

*Sitä yhteyttä ei voi poistaa refaktoroinnilla eikä suojella pelkällä `private`-avainsanalla. Se säilyy vain, jos järjestelmä tekee rahaa koskevat päätökset sen mukaisesti."*

**Nishkama Karma – Toimi ilman kiintymystä tuloksiin**

Arjuna katsoi Krishnaa hämmentyneenä. Jos koodi kerran vanhenee kuitenkin ja kaikki muuttuu legacyksi, miksi vaivautua puolustamaan katselmoinnissa yhtäkään invarianttia?

Krishna vastasi Gitan kuuluisimmalla opetuksella:

**Krishna:**

*"Sinulla on oikeus vain itse työhön — tässä tapauksessa rehelliseen katselmointiin — ei koskaan sen hedelmiin (kuten ikuiseen monumenttiin, täydelliseen arkkitehtuuriin tai kehuihin ohjausryhmältä).*

*Älä koskaan tee työtä vain saadaksesi ticketin suljetuksi. Älä myöskään kiinny toimettomuuteen ja väistä kannanottoa. Tee työsi vakaasti, vapaana kiintymyksestä hyväksyntään tai hylkäykseen. Tätä mielen tasapainoa kutsutaan refaktoroinniksi."*

Koodaa ilman kiintymystä hedelmiin:

Tavoite: Suljettu Jira-tiketti, kehut ---\> Sitoo sinut pelkoon ja stressiin

Tavoite: Mallin rehellisyys TÄNÄÄN ---\> Nishkama Karma (Vapaus toimia)

**Krishna:**

*"Se, joka tekee työnsä peläten PR-hylkäystä tai odottaen bonuspisteitä, on tulostensa orja. Mutta se, joka keskittyy itse liiketoimintamallin ymmärtämiseen tässä hetkessä, saavuttaa tyynen mielen – vaikka koodikanta myrskyäisi ympärillä."*

**Sthitaprajna – Vakaa arkkitehti**

Arjuna pyyhki kyynelensä ja kysyi jotain hyvin käytännöllistä:

**Arjuna:**

*"Mistä tunnistaa arkkitehdin tai seniorikehittäjän, jonka mieli on vakaa (Sthitaprajna)? Miten hän puhuu code review'ssa? Miten hän reagoi, kun P1-tuotantokriisi iskee kello 16.55 perjantaina?"*

**Krishna:**

*"Se, jota tuotannon hälytykset eivät lamaannuta eikä pikaiset onnistumiset sokaise, on vakaa mieleltään.*

*Niin kuin kilpikonna vetää raajansa kuoren sisään, vakaa kehittäjä vetää huomionsa pois Slackin paniikista, turhista framework-hypeistä ja somen väittelyistä. Hän ei vihaa legacy-koodia, eikä hän palvo uutta muotikieltä.*

*Kun muut vellovat vaatimusten meressä kuin myrskyävä meri, vakaa arkkitehti pysyy tyynenä. Hänen koodikantaansa virtaa uusia vaatimuksia joka päivä, mutta hän ei paisu dogmatismista eikä murene kiireestä. Hän saavuttaa rauhan."*

**Luvun II lopputulos**

Arjunalle alkaa hahmottua uusi näkökulma:

1.  Vanhan koodin poistaminen tai muuttaminen ei ole arkkitehtoninen murha, jos sen alla oleva liiketoiminnan **invariantti** säilytetään ja kirkastetaan.

2.  Työ täytyy tehdä laadukkaasti **tässä ja nyt**, riippumatta siitä, tuleeko koodista ensi vuonna legacyä vai ei.

3.  Koodarin vapaus löytyy siitä, ettei hän sido identiteettiään työnsä hedelmiin (hypeen, monumentteihin, refaktoroinnin täydellisyyteen).

Arjuna ottaa hiljaa kiinni Gandivastaan ja avaa diffin uudelleen. Hän ei vielä hyväksy eikä hylkää, mutta hänen kätensä eivät enää tärise.

**Arjuna:**

*"Opetuksesi on kirkas, Krishna. Mutta jos viisaus ja vakaus ovat tärkeämpiä kuin pelkkä hätäinen toiminta, miksi sinä silti käsket minun ryhtyä tähän vaikeaan taisteluun ja ottamaan kantaa tähän Merge Requestiin?"*

## LUKU 3: Karma Yoga ja tekojen orkestraatio

**Arjunan kysymys: "Miksi ottaa kantaa, jos ymmärrys on vielä kesken?"**

Arjuna oli kuunnellut Krishnan opetusta domain-käsitteiden kuolemattomuudesta ja tyynen mielen merkityksestä. Hänen mieleensä syttyi kuitenkin välittömästi houkutteleva ajatus.

**Arjuna:**

*"Krishna! Jos kerran ymmärrys, kirkas arkkitehtuuri ja tyyni mieli ovat paljon parempia kuin hätäinen suorittaminen, miksi ihmeessä ajat minua katselmoimaan tämän Merge Requestin ja lausumaan siitä mielipiteeni?*

*Eikö olisi parempi, että jäämme tähän neuvotteluhuoneeseen, pidämme jatkuvia Event Storming -työpajoja, piirrämme Miro-boardille täydellisiä luokkakaavioita emmekä koskaan koske tuotantokoodiin? Eikö toimettomuus ole turvallisempaa?"*

**Krishna vastaa: Kukaan ei voi olla toimimatta**

Krishna katsoi Arjunaa ja pudisti päätään hymyillen.

**Krishna:**

*"Tässä maailmassa on kaksi polkua, oi synnitön: ymmärtämisen polku (knowledge crunching) ja toiminnan polku (Karma Yoga). Mutta kuuntele tarkasti: ne eivät ole kaksi eri pakoreittiä vastuusta.*

*Kukaan ei saavuta vapautta teknisestä velasta pelkästään jättämällä ottamatta kantaa. Kukaan ei suojele domainia poistamalla itseään revieweriksi ja toivomalla, että seuraava ymmärtää enemmän.*

*Katselmoinnin luonto pakottaa sinut toimimaan. Hyväksyminen on teko, muutospyyntö on teko, kysymys on teko – ja hiljaisuuskin vaikuttaa siihen, millainen malli päätyy tuotantoon."*

TOIMINNAN DYNAMIIKKA

Pelkkä speksaus ilman koodia Kaaottinen Just Ship It

(Valheellinen toimettomuus) (Sokea kiintymys tulokseen)

\\ /

\\ /

---\> KARMA YOGA \<---

(Rehellinen teko tässä ja nyt:

rehellinen kannanotto ilman egoa)

**Krishna:**

*"Se, joka sulkee diffin ja teeskentelee olevansa arkkitehtuurin yläpuolella, mutta käy silti mielessään jatkuvaa väittelyä siitä, miten muut tekevät virheitä, on valheellinen ihminen.*

*Mutta se, joka avaa diffin uudelleen, tekee epäilyksensä näkyväksi kysymyksenä ja perustelee arvionsa ilman egoa tai kiintymystä voittoon – hän toimii erinomaisesti."*

**Karman hedelmät ja epähedelmät**

Arjuna jäi miettimään Krishnan sanoja. Hän oli oppinut, ettei tekoon saanut kiintyä, mutta tuotantojärjestelmissä jokainen teko näytti silti jättävän jäljen.

**Arjuna:**

*"Jos minun ei pidä kiintyä työni hedelmiin, tarkoittaako se, etteivät seuraukset kuulu minulle?"*

Krishna pudisti päätään.

**Krishna:**

*"Kiintymättömyys ei ole seurauksista piittaamattomuutta. Karma tarkoittaa juuri sitä, ettei yksikään teko jää ilman seurausta.*

*Jokainen commit tavoittelee hedelmää. Mutta jokainen commit tuottaa myös epähedelmiä."*

Hedelmä on se tulos, jota muutoksella tavoiteltiin ja joka kirjoitettiin Jira-tikettiin:

> Mapperi saa muodostettua DTO:n.

Epähedelmät ovat muutoksen tahattomia ja usein viiveellä kypsyviä seurauksia:

- `Money`-olion sisäisestä rakenteesta tulee yleinen API.

- laskenta alkaa siirtyä Value Objectin ulkopuolelle

- valuuttasääntö kopioituu useaan palveluun

- seuraava kehittäjä pitää ratkaisuun syntynyttä sattumaa suunniteltuna käytäntönä

- AI tulkitsee sen *established project conventioniksi* ja monistaa sen kaikkialle

**Krishna:**

*"Hedelmän löydät Jira-tiketistä. Viisas katselmoija etsii epähedelmiä."*

**Tekninen velka karmallisena perintönä**

Menneisyydessä tehty pikaratkaisu ei katoa, kun tiketti suljetaan tai sen tekijä vaihtaa projektia. Se jatkaa elämäänsä nykyhetkessä bugina, hidasteena, vaikeana testidatana ja selityksenä, jonka jokainen uusi kehittäjä joutuu oppimaan.

Nykyinen tiimi ei ehkä aiheuttanut tätä velkaa, mutta se toimii sen seurausten keskellä. Refaktorointi ei pyyhi historiaa olemattomaksi. Se on teknisen karman **tietoista sovittamista**: vanhan oletuksen tunnistamista, sen seurausten ymmärtämistä ja uuden tiedon kirjoittamista takaisin malliin.

> **Et ole syyllinen kaikkeen perimääsi koodiin. Olet kuitenkin vastuussa siitä, mitä siirrät seuraaville.**

**Event Sourcing – järjestelmä, joka muistaa tekonsa**

Tavallinen tilamalli kertoo helposti vain, mikä on totta nyt. Event Sourcing kertoo myös, millaisten tekojen seurauksena nykyhetkeen päädyttiin:

```text
AccountOpened
MoneyDeposited
PaymentDebited
PaymentReversed
```

Virheellistä veloitusta ei normaalisti poisteta tapahtumahistoriasta ja teeskennellä, ettei sitä koskaan tapahtunut. Sen jälkeen kirjataan uusi korjaava tapahtuma. Historia kertoo sekä teon että sen korjauksen.

**Krishna:**

*"Mennyttä tapahtumaa ei voi tehdä tapahtumattomaksi. Voit vain tehdä uuden teon, joka muuttaa sen seurauksia."*

Tämä on syyn ja seurauksen laki lähes kirjaimellisena arkkitehtuurina. Se ei silti tee event storesta metafyysisesti ikuista: tietosuoja, säilytysajat ja virheellisesti tallennettu henkilötieto voivat velvoittaa poistamaan tai muuttamaan historiaa. Dharma ei ole patternin sokea noudattaminen.

**Sivuvaikutukset – näkymätön karma**

Kaikki seuraukset eivät ilmesty heti eivätkä pysy saman Bounded Contextin sisällä. Vuotava kapselointi, jaettu tietokanta tai epäselvä integraatiosopimus voi käynnistää reaktion, jonka alkuperäinen tekijä kohtaa vasta kuukausia myöhemmin – tai jonka kohtaa joku aivan toinen.

```text
Money-getterit
    → ulkopuolinen laskenta
        → kopioituneet valuuttasäännöt
            → kontekstien välinen riippuvuus
                → muutos, jota kukaan ei enää uskalla tehdä
```

Karma ei tässä ole rangaistus eikä syytös. Se on syyn ja seurauksen tunnistamista. Koodikuiskaaja ei kysy ensimmäisenä, kuka teki virheen. Hän kysyy:

> *"Mitä tämä kipu kertoo aikaisemmasta päätöksestä – ja millaisia epähedelmiä oma päätöksemme jättää seuraaville?"*

**Krishna:**

*"Älä kiinny työsi hedelmiin. Älä kuitenkaan kuvittele, etteivät tekosi tuottaisi epähedelmiä."*

**Uhri järjestelmän ylläpitämiseksi (Yajna)**

Krishna selitti seuraavaksi, miksi koodikanta vaatii jatkuvaa, epäitsekästä huolenpitoa.

**Krishna:**

*"Aikoinaan, kun maailmankaikkeuden Arkkitehti loi ensimmäiset järjestelmät ja kehittäjät, hän sanoi: 'Toimikaa Yajnalla (yhteisellä uhrilla ja panoksella). Tämä ylläpitää teitä.'*

*Uhri ohjelmistokehityksessä tarkoittaa tätä:*

- Kirjoitat yksikkötestin, vaikka kukaan ei kysy sitä.

- Dokumentoit Invariantin seuraavaa kehittäjää varten.

- Korjaat pienen bugin ohi kulkiessasi (Boy Scout Rule).

*Joka nauttii koodikannan eduista – valmiista kirjastoista, CI/CD-putkista ja muiden tekemistä pohjista – mutta ei itse uhraa aikaansa mallin selkeyttämiseen, on koodivaras!*

*Ne, jotka koodaavat vain rikastuttaakseen omaa ansioluetteloaan tai sulkeakseen oman tiketinsä piittaamatta kokonaisuudesta, syövät omaa synnyttämäänsä teknistä velkaa."*

**Esimerkin näyttäminen (Lokasamgraha)**

**Krishna:**

*"Katso minua, Arjuna! Minulla ei ole mitään saavutettavaa tässä repossassa. Ei ole olemassa tikettiä, joka minun pitäisi sulkea saadakseni palkan. Silti minä toimin lakkaamatta.*

Jos minä lakkoilisin ja lopettaisin domain-mallin suojelemisen, nämä järjestelmät luhistuisivat. Minusta tulisi kaikkien tulevien bugien ja sekaannusten aiheuttaja.

*Sitä, mitä johtava kehittäjä (Senior Architect) tekee, muut seuraavat. Minkä standardin hän asettaa omilla Merge Requesteillaan, sitä koko tiimi noudattaa.*

*Viisas koodaa yhtä huolellisesti ja energeettisesti kuin hätäisin 'Just Ship It' -kehittäjä, mutta ilman itsekkyyttä. Hänen tavoitteensa on koodikannan terveys (Lokasamgraha), ei oma ego."*

**Roolien sekaannus ja eettinen velvollisuus**

**Arjuna:**

"Krishna, miksi ihminen sitten lankeaa tekemään huonoja ratkaisuja? Mikä saa kehittäjän levittämään `Money`-olion sisäisen rakenteen kaikkialle, vaikka hän näkee laskennan jo valuvan mapperiin?"

**Krishna:**

*"Se on Himo ja Viha – kiireen, aikataulupaineen ja 'minä haluan tämän valmiiksi Nyt' -asenteen synnyttämiä käskyttäjiä.*

Paine sumentaa ymmärryksen samoin kuin savu peittää tulen tai pöly peittää peilin. Se saa kehittäjän unohtamaan Ubiquitous Languagen ja tarttumaan oikotiehen.

*Mutta muista tämä:*

Parempi on suorittaa oma velvollisuutensa (Svadharma) epätäydellisesti, kuin toisen velvollisuus täydellisesti.

Kehittäjän dharma on suojella domain-mallia ja ilmaista se koodissa. Älä yritä toimia Product Ownerina, joka myy sielunsa aikatauluille, äläkä arkkitehtipoliisina, joka pysäyttää kaiken. Tee oma osasi rehellisesti."

**Luvun III päätös**

Arjuna ymmärtää nyt, että ymmärrys ilman valmiutta toimia sen perusteella voi muuttua pakoiluksi. Katselmointi ei ole sivusta huutelua, vaan se on täydellinen alusta harjoittaa **Karma Yogaa**:

1.  Ota kantaa **tässä ja nyt** sen ymmärryksen varassa, joka sinulla on – ja tee samalla epävarmuutesi näkyväksi.

2.  Katselmoi epäitsekkäästi palvellen yhteistä ymmärrystä ja koodikannan terveyttä (Lokasamgraha), älä omaa egoasi tai tarvetta voittaa keskustelua.

3.  Älä odota täydellistä varmuutta: katselmoijan dharma on esittää olennainen havainto rehellisesti, ei omistaa lopullista totuutta.

Arjuna nostaa Gandivansa – eli avaa diffin uudelleen.

**Arjuna:**

*"Komentosi on selvä. En pakene työpajoihin enkä myöskään pakene niistä. Palaan Merge Requestiin ja kirjoitan sen kysymyksen, jonka nyt osaan esittää."*

## LUKU 4: Vanhin commit ja tiedon sukupolvet

**Tieto, joka opetettiin ensimmäisille ohjelmoijille**

Arjuna oli saanut jousensa (IDE:nsä) valmiiksi, mutta hänen mielessään versoi uusi epäilys. Krishna puhui Domain-Driven Designistä ja käsitteiden eheydestä ikuisena totuutena, mutta ala oli täynnä muuttuvia trendejä.

Krishna katsoi Arjunaa ja sanoi:

**Krishna:**

*"Tämän muuttumattoman tiedon minä opetin ensin Ada Lovelacelle. Ada näki, ettei koneen tehtävä ollut vain laskea numeroita, vaan että se voisi käsitellä ihmisen sille antamia symboleja ja merkityksiä.*

*Turingille minä opetin, että laskennan periaate voidaan erottaa siitä fyysisestä koneesta, jolla se suoritetaan.*

*Von Neumannille annoin ohjelman ja tiedon yhteisen muistin. Hän rakensi siitä maailman – ja jätti teille samalla globaalin muuttuvan tilan siunaukset ja kiroukset. Minä annoin hänelle yhteisen muistin. Hän ei voinut tietää, mitä Enterprise Java tekisi sillä.*

*Grace Hopperille minä opetin, ettei ihmisen tarvitse ikuisesti puhua koneen ehdoilla, vaan koneen kieli voidaan tuoda lähemmäksi ihmisten käyttämiä käsitteitä.*

*McCarthylle minä kuiskasin, että ohjelma voi käsitellä symboleja, kuvata omaa rakennettaan ja rakentua myös muuttumattomien arvojen varaan.*

*Näin tämä oppi kulki sukupolvelta toiselle tietojenkäsittelyn paramparassa. Syntaksi muuttui, koneet vaihtuivat ja abstraktiot kasvoivat, mutta kysymys pysyi samana: miten ihmisen ymmärrys voidaan ilmaista koneelle menettämättä sen merkitystä?*

*Pitkän ajan kuluessa, kiireen, pirstaloituneiden repojen ja Hype-Driven Developmentin seurauksena tämä kysymys katosi koodikannoista. Tämän saman tiedon minä ilmoitan nyt sinulle, koska sinä olet minun tiimikaverini ja ystäväni – ja koska sinulla on rohkeutta kysyä vaikeita kysymyksiä."*

**Arjunan hämmennys: "Kuinka voit olla niin vanha?"**

Arjuna katsoi Krishnaa kummissaan.

**Arjuna:**

*"Krishna! Ada Lovelace kuoli lähes sata vuotta ennen ensimmäistä Jira-tikettiä. Turing ja von Neumann kuolivat ennen kuin sinä liityit tähän konsulttiyritykseen. Grace Hopper oli jo amiraali, kun sinä vielä väitit CV:ssäsi osaavasi JavaScriptiä.*

*Miten sinä muka opetit heitä?"*

Krishna vastasi syvällä ja rauhallisella äänellä:

**Krishna:**

*"Minulla ja sinulla on takana kymmeniä tuhansia committeja, ohjelmointikieliä ja projekteja, oi Arjuna. Sinä näet ihmiset, syntaksit ja teknologiat. Minä puhun siitä kysymyksestä, joka syntyy uudelleen jokaisessa sukupolvessa.*

*Minä en ollut heidän frameworkinsa. Minä olin heidän vaikea kysymyksensä.*

*Aina kun järjestelmän ymmärrys rappeutuu, aina kun Ubiquitous Language muuttuu sanoiksi ilman yhteistä merkitystä ja malli alkaa valehdella domainista, minä palaan uudelleen kysymyksen muodossa.*

KNOWLEDGE CRUNCHINGIN KIERTO

Havainto ---\> Vaikea kysymys ---\> Model Storming ---\> Esimerkki tai testi

^                                                                    \|

\|---------------------- Tarkentunut malli \<-----------------------\|

**Krishna:**

*"En palaa uutena frameworkina enkä arkkitehtina, joka tuo valmiin totuuden. Palaan, kun kehittäjä, domain-asiantuntija ja käyttäjä kokoontuvat saman esimerkin äärelle ja uskaltavat huomata, etteivät he vielä tarkoita samalla sanalla samaa asiaa.*

*Knowledge crunchingissa vanha oletus saa kuolla ja tarkempi malli syntyä. Model Stormingissa ymmärrys saa väliaikaisen muodon, jota voidaan koetella ja muuttaa. Näin dharmaa ei palauteta kerran – se löydetään uudelleen jokaisessa keskustelussa, testissä ja refaktoroinnissa."*

**Tekemättömyys teossa (Akarma)**

Sitten Krishna palaa opetukseen, joka hämmentää kehittäjiä kaikkein eniten: miten koodaaminen ja koodaamatta jättäminen suhtautuvat toisiinsa?

**Krishna:**

*"Mitä on toiminta (Karma) ja mitä on toimettomuus (Akarma)? Tässä viisaimmatkin seniorit menevät sekaisin.*

Se, joka näkee toimettomuudessa toiminnan ja toiminnassa toimettomuuden, on viisas ihmisten joukossa.

*Mitä tämä tarkoittaa ohjelmoinnissa?"*

1.  Toiminta toimettomuudessa: Kehittäjä istui kaksi tuntia hiljaa, ei kirjoittanut riviäkään koodia, mutta löysi väärän oletuksen tietomallista. Hän säästi tiimiltä kolmen kuukauden turhan työn. Ulkoa päin se näytti toimettomuudelta, mutta se oli suurin arkkitehtoninen teko!

2.  Toimettomuus toiminnassa: Toinen kehittäjä ja AI-generoija tuottivat 3 000 riviä mapper-luokkia, rajapintoja ja controllereita ilman, että he ymmärsivät liiketoiminnan tarvetta sekuntiakaan. Ulkoa päin se näytti valtavalta toiminnalta, mutta domainin kannalta mitään ei tapahtunut – se oli täydellistä toimettomuutta.

**Krishna:**

"Viisas koodari on se, jonka jokainen teko on puhdistettu hemmottelevasta kiintymyksestä. Hänen koodinsa ei ole täynnä turhia abstraktioita (accidental complexity), vaan vain sitä, mikä kuuluu itse ongelmaan (essential complexity)."

**Tietoisuuden tuli polttaa teknisen velan**

**Krishna:**

*"Niin kuin syttynyt tuli polttaa polttopuut tuhaksi, samoin Tiedon Tuli (Jnana) polttaa kaiken teknisen velan ja virheelliset oletukset.*

*Ei ole mitään niin puhdistavaa tässä maailmassa kuin aito ymmärrys domainista. Kun sinulla on se tieto, et enää lankea oikoteihin eikä sinua sokaise yksikään uusi framework-hype.*

*Ota tämä Tieto miekaksesi, leikkaa sillä poikki se epäilys, joka kumpuaa tietämättömyydestä ja istuu sydämessäsi! Nouse, Arjuna, tartu Gandivaan ja palaa diffiin!"*

**Luvun IV päätös**

Arjuna alkaa nähdä oman roolinsa pidemmässä jatkumossa:

1.  Ohjelmistoarkkitehtuurin perussäännöt eivät ole viime viikon muoti-ilmiö, vaan **ikuista viisautta**, joka vain pukeutuu eri kieliin eri vuosikymmeninä.

2.  Rivimäärät ja git-commitien tiheys eivät kerro mitään työn arvosta – **pysähtyminen ja oikean kysymyksen esittäminen** on usein tehokkainta koodaamista.

3.  Ymmärrys (Knowledge Crunching) polttaa epävarmuuden pois.

Arjuna katsoo nyt koodia ilman pelkoa. Hän ymmärtää, että jokainen rehellinen katselmointi voi jatkaa tätä tiedon ikuista ketjua.

**Arjuna:**

*"Epäilykseni alkavat väistyä, Krishna. Mutta kerro minulle vielä: kumpi on lopulta parempi – luopua kaikista huonoista luokista kerralla (Sanyasa), vai refaktoroida niitä pikkuhiljaa toiminnan kautta (Karma Yoga)?"*

## LUKU 5: Sanyasa Yoga eli suuren uudelleenkirjoituksen ansa

**Arjunan kysymys: "Eikö olisi helpompaa vain tuhota tämä ja aloittaa alusta?"**

Arjuna oli oppinut toiminnan merkityksen ja ymmärtänyt koodin historialliset kerrokset. Mutta katsoessaan edelleen monoliitin syövereitä ja sekavia luokkarakenteita, hänen mieleensä nousi kaikkien ohjelmoijien suurin houkutus.

**Arjuna:**

*"Krishna! Toisaalta kiittelet luopumista (Sanyasa – vanhan koodipohjan hylkäämistä ja Big Rewrite -projektia) ja toisaalta kehotat minua jatkamaan refaktorointia toiminnan kautta (Karma Yoga).*

*Sano minulle selkeästi: kumpi polku on parempi? Eikö olisi paljon helpompaa heittää koko tämä repo roskakoriin, perustaa uusi greenfield-projekti tyhjältä pöydältä ja kirjoittaa kaikki puhtaalle paperille?"*

**Krishna vastaa: Uudelleenkirjoituksen illuusio**

Krishna katsoi Arjunaa lempeästi, mutta napakasti, kuten kokenut arkkitehti, joka on nähnyt jo kymmenen epäonnistunutta greenfield-uudistusta.

**Krishna:**

*"Sekä koodista luopuminen (Rewrite) että sen refaktorointi (Karma Yoga) voivat johtaa korkeimpaan tulokseen. Mutta näistä kahdesta toiminnallinen refaktorointi on huomattavasti parempi!*

*Luopuminen ilman kurinalaisuutta ja ymmärrystä tuo mukanaan vain suurta tuskaa.*

*Sinä luulet, että uudessa repossa kaikki on puhdasta. Mutta jos sinulla on samat virheelliset oletukset ja sama epäselvä kieli mukanasi, viet vain vanhat haamusi uuteen projektiin! Viiden kuukauden kuluttua 'uusi uljas greenfield-projektisi' on aivan yhtä suuri legacy-sotku kuin tämä vanha monoliitti."*

GREENFIELD-HARHA (BIG REWRITE)

Vanha monoliitti (Sotku, mutta toimii)

│

├───\> "Heitetään roskakoriin ja aloitetaan alusta!"

│

▼

Uusi Repo (Greenfield)

│

├───\> Ei ymmärretty vanhoja piilosääntöjä

├───\> Kopioitiin samat oletukset

│

▼

Tulos: Kaksi legacy-järjestelmää yhden sijaan!

**Krishna:**

*"Toiminnallinen luopuja (Karma-Sanyasi) on se, joka ei vihaa vanhaa koodia eikä ihannoi uutta frameworkia. Hän ei pakenemaan greenfield-haaveisiin, vaan tekee muutokset elävään järjestelmään pala palalta.*

*Sitä, joka näkee, että syvällinen arkkitehtuurisuunnittelu (Sankhya) ja käytännön refaktorointi (Karma) ovat sama asia, voidaan kutsua todelliseksi näkijäksi."*

**Tyyni koodari keskellä tuotantoa**

Krishna selitti seuraavaksi, miltä näyttää kehittäjä, joka on saavuttanut sisäisen rauhan keskellä monimutkaista järjestelmää.

**Krishna:**

*"Se, joka on puhdistanut mielensä, voittanut egonsa ja oppinut näkemään saman Ubiquitous Languagen kaikkialla, ei tahraannu koodatessaan – vaikka hänen kätensä koskisivat kaikkein kauheimpaan legacy-metodiin.*

*Vaikka hän näkee, kuulee, tekee HTTP-kutsuja, lukee tietokannasta ja kirjoittaa lokia, hän ajattelee:*

*'En minä (minun egoni) tätä tee. Se on vain tyyppijärjestelmä ja runtime, joka suorittaa tehtäväänsä.'*

*Hän asettaa jokaisen muutoksensa Bounded Contextin suojiin, aivan kuten lootuksenkukka kasvaa vedessä mutta sen lehtiin ei tartu pisaraakaan mutaa. Hän tekee työnsä ilman kiintymystä, ja siksi tuotantobugit eivät pysty murtamaan hänen rauhaansa."*

**Yhdenvertainen katse käsitteisiin**

**Krishna:**

*"Viisas arkkitehti katsoo samalla yhdenvertaisella silmällä (Sama-darshina) niin pientä apuluokkaa, suurta Aggregate Rootia kuin monimutkaista ulkoista rajapintaakin.*

*Hän ei väheksy pientä Value Objectia, eikä hän pelkää tuotantokannassa makaavaa miljardin rivin taulua. Hän ymmärtää, että niitä kaikkia koskevat samat dharman lait: jokaisella pitää olla selkeä rooli, rajat ja merkitys."*

**Luvun V päätös**

Arjunalle kirkastuu syvä totuus uudelleenkirjoituksen (Big Rewrite) ja refaktoroinnin suhteesta:

1.  **Pako greenfield-projektiin on harha:** Jos et ymmärrä domainia vanhassa koodissa, et hallitse sitä uudessakaan.

2.  **Lootuksenkukan periaate:** Voit koodata kaikkein rumimmassa legacy-ympäristössä menettämättä ammattitaitoasi ja rauhaasi, kunhan erotat oman egosi järjestelmän rakenteista ja teet jokaisen pienen muutoksen kurinalaisesti.

3.  Arkkitehdin tehtävä ei ole unelmoida tyhjästä pöydästä, vaan **tuoda valoa ja järjestystä siihen maastoon, jossa tiimi tänään seisoo**.

Arjuna katsoo monoliittia uusin silmin. Hän ei enää haaveile repon poistamisesta.

**Arjuna:**

*"Ymmärrän, Krishna. En pakene uuteen repoon. Alan siivota tätä maastoa tässä ja nyt. Mutta miten hallitsen mieleni ja keskittymiseni, kun ympärilläni laulavat Slack-ilmoitukset ja jatkuvat keskeytykset?"*

## LUKU 6: Dhyana Yoga ja Deep Workin taito

**Mielen hallinta keskeytysten aikakaudella**

Arjuna oli valmis refaktoroimaan elävää koodia, mutta hän huomasi heti uuden esteen. Aina kun hän yritti syventyä monimutkaiseen async-vuohon, hänen huomionsa herpaantui.

Slack lauloi punaisia ilmoituksia, Teams-palaverikutsu syrjäytti kalenterin, ja selainikkunassa vilkkuivat uudet teknologiauutiset.

**Arjuna:**

*"Krishna! Mieli on levoton, raju, vaativa ja piintynyt! Sen hallitseminen tuntuu minusta yhtä mahdottomalta kuin myrskytuulen sitominen solmuun.*

*Miten voin mallintaa syvällisiä liiketoimintasääntöjä, kun mieleni hyppii tiketti-ilmoituksista kahvihuonejuoruun ja sieltä tuotantolokeihin sekunnin murto-osassa?"*

**Krishna vastaa: Abhyasa ja Vairagya (Harjoitus ja irti päästäminen)**

Krishna katsoi Arjunaa ymmärtäväisesti. Tämä ei ollut uusi ongelma – se oli ihmismielen ikuinen taistelu.

**Krishna:**

*"Ilman muuta mieli on vaikea hallita, oi valtavakätinen! Mutta se on mahdollista saavuttaa kahdella asialla: **Abhyasalla** (säännöllisellä harjoituksella) ja **Vairagyalla** (irti päästämisellä ja kurinalaisuudella).*

*Se, joka ei hallitse mieltään, ei voi saavuttaa syvää fokaalista keskittymistä (Deep Work). Mutta se, joka hallitsee itsensä ja yrittää oikeilla menetelmillä, saavuttaa menestyksen."*

DEEP WORKIN TILA (DHYANA)

Puhelin 🔕 │ Slack Do Not Disturb 🌙 │ IDE Fullscreen 💻

────────────────────────────────────────────────────────

│

▼

YKSI FOCUS (Ekagra)

│

▼

Virheetön Domain-malli

**Miten koodari pystyttää meditaatiopaikan?**

Krishna antoi hyvin käytännölliset ohjeet siitä, miten koodarin tulee valmistautua syvätyöjaksoon:

**Krishna:**

*"Valitkoon kehittäjä puhtaan ja rauhallisen työtilan, missä ei ole turhia häiriötekijöitä. Asettakoon hän työskentelyasentonsa ergonomiseksi – ei liian korkealle eikä liian matalalle.*

*Kytkeköön hän pois Slack-ilmoitukset, sulkekoon sosiaalisen median välilehdet ja laittakoon puhelimensa hiljaiselle.*

*Istukoon hän siinä vakaasti, pitäköön selkänsä suorana ja kohdistakoon katseensa vain edessään olevaan koodiin – katsomatta sivuilleen.*

*Älköön hän syökö liikaa raskasta lounasta ennen syvätyöjaksoa, älköönkä myöskään kärsikö nälässä. Älköön hän valvoko koko yötä kofeiinin voimalla, älköönkä nukkuko puolta päivää. Kohtuus kaikessa on joogan avain!"*

**Mielen vertauskuva: Tuuleton paikka**

Krishna käytti kaunista vertauskuvaa kuvaillakseen keskittyneen koodarin mieltä.

**Krishna:**

*"Niin kuin kynttilän liekki ei lepata tuulettomassa paikassa, samoin on sen arkkitehdin mieli tyyni, joka harjoittaa syventymistä domain-malliin.*

*Kun mieli rauhoittuu koodin äärellä, kehittäjä kokee iloa, joka ylittää aistien tason. Hän ei enää horju pois totuudesta, kohtasi hän mitä tahansa refaktorointihaasteita.*

*Tätä tilasta erossa olemista – irti päästämistä kiireestä ja hälystä – kutsutaan todelliseksi Deep Workiksi."*

**Arjunan pelko: "Mitä jos epäonnistun kesken kaiken?"**

Arjunaa pohditutti vielä yksi asia.

**Arjuna:**

*"Krishna! Entä jos kehittäjä yrittää tätä, laittaa ilmoitukset pois ja syvenny koodiin, mutta menettää silti keskittymisensä? Entä jos hän ei saa PR:ää valmiiksi eikä silti nauti 'Just Ship It' -porukan pikaisista voitoista? Onko hän kuin hajonnut pilvi, joka ei kuulu taivaalle eikä maahan?"*

**Krishna:**

*"Arjuna! Ei hyvän koodin tekijä koskaan päädy perikatoon – ei tässä sprintissä eikä tulevissa!*

*Se, joka pyrkii rehelliseen arkkitehtuuriin mutta lankeaa kesken kaiken, syntyy uudelleen parempaan ympäristöön. Hän päätyy tiimiin, jossa on hyvät koodauskäytännöt ja viisaat seniorit.*

*Siellä hän löytää jälleen sen ymmärryksen tason, jonka hän saavutti edellisessä projektissaan, ja jatkaa siitä eteenpäin. Yksikään hyvän mallin eteen tehty työtunti ei mene koskaan hukkaan."*

**Luvun VI päätös**

Arjuna oppii keskittymisen ja itsekurin merkityksen:

1.  **Mieli on työkalu, ei isäntä:** Slackin ja Teamsin orjuudesta voi päästä eroisiksi luomalla tietoisia syvätyön (Deep Work) rajoja.

2.  **Kohtuus kaikessa:** Paras koodi ei synny yön yli kestävissä energiajuomamaratoneissa, vaan tasaisessa, ergonomisessa ja kirkkaassa arjessa.

3.  **Ponnistelu ei mene hukkaan:** Vaikka sprintti menisi myöhästyneeksi, oppi ja pystytetty itsekuri kantavat seuraavaan projektiin.

Arjuna laittaa kuulokkeet korvilleen, aktivoi *Do Not Disturb* -tilan ja katsoo suoraan edessä olevaa luokkaa.

**Arjuna:**

*"Mieleni on tyyni, Krishna. Suljen ulkopuolisen maailman. Olen valmis ymmärtämään järjestelmän syvimmän olemuksen."*

## LUKU 7: Jnana-Vijnana Yoga eli abstraktion ja runtime-todellisuuden synteesi

**Pelkkä tektikirjaoppi ei riitä**

Arjuna oli saavuttanut tyynen mielentilan ja oppinut sulkemaan häiriötekijät pois. Hän tunsi DDD-terminologian ja Bounded Contextien rajoitukset. Mutta Krishna tiesi, että pelkkä teoreettinen tieto (Jnana) ilman käytännön kokemusta runtime-käyttäytymisestä (Vijnana) tekee arkkitehdistä vain norsunluutornissa istuvan haaveilijan.

**Krishna:**

*"Kuuntele nyt, oi Arjuna! Minä kerron sinulle täydellisesti sekä teoreettisen arkkitehtuuritiedon (Jnana) että sen käytännön suorituskyky-ymmärryksen (Vijnana). Kun tämän tiedät, mitään muuta tietämisen arvoista ei tässä koodikannassa sinulle jää.*

*Tuhatta kehittäjää kohden on ehkä yksi, joka pyrkii todella ymmärtämään arkkitehtuurin syvimmän olemuksen. Ja niistä harvoista, jotka pyrkivät, tuskin yksikään tuntee minun suoritusympäristöni todellista luontoa."*

**Kahdeksankertainen fyysinen alusta (Prakriti)**

Krishna selitti, miten koko ohjelmistoalusta rakentuu elementeistä, joita ilman mikään koodi ei voi suorittua.

**Krishna:**

*"Minun alempi luontoni (eli fyysinen infra ja runtime) koostuu kahdeksasta elementistä:*

1.  **Levytila** (Maa – persistentti tallennus)

2.  **Verkko-IO** (Vesi – data-virrat ja pakettiliikenne)

3.  **CPU-syklit** (Tuli – prosessointiteho)

4.  **RAM-muisti** (Ilma – dynaaminen tila)

5.  **Osoiteavaruus** (Eetteri – muistipaikat ja osoittimet)

6.  **Kääntäjä ja Runtime** (Mieli – koodin tulkinta)

7.  **Tyyppijärjestelmä** (Äly – abstraktiorajat)

8.  **Ego** (Ego – kehittäjän oma mielipide siitä, miten koodi tulisi kirjoittaa)

Alempi luonto (Infrastruktuuri / Prakriti)

\[RAM\] \[CPU\] \[Network\] \[Disk\] \[Runtime\] \[Type System\]

│

▼

Kaikki kytkeytyy yhteen ilmentymään

▲

│

Korkeampi luonto (Domain / Purusha)

\[Liiketoiminta-invariantit ja merkitys\]

**Krishna:**

*"Tämä on vasta alempi luontoni, Arjuna! Mutta tunne myös minun korkeampi luontoni: se Elävä Henki (Domain-malli), joka puhaltaa merkityksen näihin muistipaikkoihin ja pitää koko sovellusta pystyssä.*

*Ilman liiketoimintalogiikkaa CPU vain polttaa sähköä ja RAM-muisti on pelkkää satunnaista kohinaa."*

**Kuin helmet kaikki riippuvat minusta**

Krishna näyttää Arjunalle järjestelmän sellaisena kuin CI/CD-pipeline tai kääntäjä ei sitä näe.

Käyttöliittymä näyttää rahamäärän. API välittää sen representaationa, jossa määrä ja valuutta kulkevat yhdessä. Application Service antaa `Money`-olion Aggregate Rootille, joka tekee sitä koskevan liiketoimintapäätöksen. Domain-eventti kantaa päätöksen tuloksen, projektio näyttää sen asiakkaalle ja tietokantataulu säilyttää teknisen representaation määränä ja valuuttakoodina.

Ne näyttävät erillisiltä osilta:

\[ UI \] ──\> \[ Command \] ──\> \[ Aggregate \] ──\> \[ Domain Event \] ──\> \[ Projection \] ──\> \[ Database \]

Mutta niiden läpi kulkee sama merkitys kuin näkymätön lanka helminauhan läpi.

**Krishna:**

*"Kuin helmet lankaan pujotettuina, kaikki riippuvat minusta.*

*Minä olen Yhteinen Kieli (Ubiquitous Language) kerrosten läpi,*

*minä olen se merkitys, joka pitää järjestelmän yhdessä:*

*minä olen Money käyttäjän ruudulla,*

*minä olen määrän ja valuutan yhteys rajapinnan viestissä,*

*minä olen Money Aggregaatin päätöksenteossa,*

*minä olen päätöksen seurauksena syntyneen Eventin sanomassa,*

*minä olen pysyvyys tietokannan sarakkeessa.*

Ilman minua nämä ovat vain erillisiä teknisiä kuoria –

minä olen se lanka, joka tekee niistä yhden todellisuuden."

**Lanka katkeaa – getterit eivät ole vain kaksi viatonta ovea**

Domain-Driven Designissä tuo lanka on domainin merkitys, jota Ubiquitous Language yrittää tehdä näkyväksi. Osia ei yhdistä ensisijaisesti Java, JSON, Kafka tai vierasavain. Niitä yhdistää väite siitä, mistä liiketoiminnassa puhutaan.

**Krishna:**

*"Jos Money tarkoittaa aggregaatissa määrän ja valuutan muodostamaa muuttumatonta kokonaisuutta, mutta sen getterit opettavat muun järjestelmän käsittelemään niitä kahtena toisistaan irrallisena primitiivinä, helminauha alkaa katketa.*

*Kaikki helmet voivat silti olla tallella. Jokainen komponentti voi toimia omassa erillisessä yksikkötestissään. Järjestelmä ei vain enää puhu samaa todellisuutta päästä päähän."*

Ubiquitous Language ei ole järjestelmän koriste tai dokumentaation kuorrute. **Se on lanka, joka pitää sen osat samassa todellisuudessa.**

**Koodin Kolme Laatua (Gunat) järjestelmässä**

Sitten Krishna paljastaa Arjunalle, miten koodi ja kehittäjät jakaantuvat kolmeen laatuun (*Guna*):

**Krishna:**

*"Minun ilmentymäni koodikannassa kietoutuu kolmeen laatuun:*

1.  **Sattva (Puhtaus ja tasapaino):** Selkeä, luettava, testattu ja stabiili koodi. Se luo rauhaa tiimiin ja pitää järjestelmän selkeänä.

2.  **Rajas (Intohimo ja ego):** Hätäiset pikaratkaisut, 'älykkäät' kikkailut ja suorituspaineessa syntynyt koodi. Se tuottaa nopeasti tuloksia, mutta jättää jälkeensä teknistä velkaa.

3.  **Tamas (Hämäryys ja laiskuus):** Spagettikoodi, kopioitu ilman ymmärrystä, ilman testejä tai poikkeudenhallintaa. Se johtaa hämmennykseen ja tuotantokatkoihin.

*Nämä kolme laatua hämärtävät kehittäjän mielen, jotta hän näkisi vain tekniset puitteet eikä merkityksen lankaa."*

**Arjunan tehtävä katselmoijana**

Arjunan levottomuus Merge Requestin äärellä ei siis ole makuasia tai turhaa pikkutarkkuutta. Hän tuntee sormissaan kohdan, jossa merkityksen lanka on katkeamassa tai Rajas/Tamas hallitsee muutosta.

Hänen tehtävänsä ei ole julistaa omaa tulkintaansa ainoaksi totuudeksi, vaan osoittaa katkos ja kysyä:

// Arjuna's PR Review Comment:

*"Tarvitseeko mapperi näitä gettereitä, vai tarvitseeko se Money-oliolta yhden eksplisiittisen representaation? Ja mikä estää muuta koodia ottamasta `amount`- ja `currency`-arvoja ulos ja tekemästä rahan päätöksiä Money-olion puolesta?"*

**Luvun VII päätös**

**Krishna:**

*"Kuka tahansa voi oppia syntaksin, frameworkit ja Gunat (Jnana), mutta se, joka näkee näkymättömän merkityksen langan koodikerrosten läpi ja suojelee Yhteistä Kieltä, omistaa syvän arkkitehtonisen viisauden (Vijnana)."*

Arjuna katsoi koodikantaa uudella tavalla: hän näki laadut, mutta ennen kaikkea hän näki langasta riippuvat helmet.

**Arjuna:**

*"Olen löytänyt langan. En enää katsele vain helmiä tai koodin pintaa, vaan sitä, mikä pitää ne yhdessä."*

## LUKU 8: Akshara Brahma Yoga eli tietokantamigraatiot ja ikuinen tila

**Arjunan kysymys: "Mitä tapahtuu, kun prosessi kuolee?"**

Arjuna oli oppinut näkemään koodin laadut ja suoritusympäristön rakenteen. Mutta prosessien väliaikaisuus täytti hänet silti epävarmuudella.

**Arjuna:**

*"Krishna! Mikä on se Ikuinen Tila (Brahma)? Mikä on sovelluksen perusolemus (Adhyatma), ja mitä ovat nämä tietokanta-transaktiot ja tapahtumat (Karma)?*

*Ja ennen kaikkea: Miten järjestelmä säilyttää identiteettinsä silloin, kun podi saa SIGKILL-signaalin, kontti kaatuu ja muisti pyyhkiytyy tyhjäksi? Miten tietoisuus ja tila säilyvät tuotannon kaatumisen hetkellä?"*

**Krishna vastaa: Viimeisen hetken ajatus ja muistin pysyvyys**

Krishna katsoi Arjunaa ja valaisi prosessin kuolevaisuuden ja datan kuolemattomuuden eroa.

**Krishna:**

*"Ikuinen ja muuttumaton (Akshara) on se kaikkein syvin tietomalli, joka ei tuhoudu vaikka jokainen sovelluspalvelin ajettaisiin alas.*

*Kuuntele tarkasti tämä laki:*

Mitä tilaa sovellus edustaa viimeisellä muistisivullaan ennen sammumistaan, siihen tilaan se myös herää uudelleenkäynnistyksessä.

*Se prosessi, joka unelmoi uncommitted datasta ja hallitsemattomista tilamuutoksista kuolemansa hetkellä, herää uudelleen korruptoituneena ja bugisena.*

*Mutta se prosessi, joka tekee hallitun alasajon (graceful shutdown), kirjoittaa tilansa eheyden ACID-transaktiolla levylle ja muistaa Bounded Contextinsa – se herää uuteen inkarnaatioon virheettömänä ja valmiina palvelemaan."*

PROSESSIN ALASAJO JA HERÄÄMINEN

Ajoaika (In-Memory State) ───\[SIGTERM\]───\> Graceful Shutdown

│ │

▼ ▼

\`SIGKILL\` (Kaaos) ACID Commit / WAL Log

│ │

▼ ▼

Tietokannan korruptio Ikuinen Tila (Akshara)

(Uudelleensyntymä buginen) (Puhdas uudelleenkäynnistys)

**Kaksi polkua: Epäsynkroninen ja synkroninen migraatio**

Krishna selitti seuraavaksi kaksi tapaa, joilla tila voi siirtyä vanhasta schemasta uuteen – valon ja pimeyden polut.

**Krishna:**

*"On kaksi polkua, joita pitkin koodi ja data siirtyvät versiosta toiseen: Valon polku ja Pimeyden polku.*

**1. Valon polku (Zero-Downtime Migration):**

*Tämä on yhteensopivien migraatioiden polku. Siinä vanha ja uusi schema elävät rinnakkain, data kirjoitetaan hallitusti molempiin suuntiin, ja vanhat luokat poistetaan vasta kun uudet ovat täysin vakaita. Tämä polku johtaa ikuiseen saatavuuteen (99.999% uptime), eikä siltä palaava järjestelmä koe katkoja.*

**2. Pimeyden polku (Downtime Migration & Force Push):**

*Tämä on hätäisten tietokantalukkojen ja 'ajetaan kanta alas yöllä' -asenteen polku. Järjestelmä pysäytetään, dataa muokataan suorilla SQL-skripteillä ilman varmuuskopioita, ja toivotaan parasta. Tämä polku johtaa takaisin tuotantokriiseihin ja manuaaliseen tietojen korjailuun."*

**Unohda väliaikainen, muista Ikuinen**

**Krishna:**

*"Kaikki maailmat ja järjestelmät – jopa kaikkein suurimmat Pilvi-alustat ja kalleimmat klusterit – tulevat ja menevät. Ne syntyvät päivän alussa (Deployment) ja tuhoutuvat yön tullessa (Teardown).*

*Mutta näiden ilmestyvien ja katoavien podien takana on Ikuinen Suoritusympäristö.*

*Älä siis kiinnitä sydäntäsi siihen, pyöriikö sovelluksesi säikeessä X vai podissa Y. Muista minun ikuinen Bounded Contextini kaikkina aikoina, ja käy taisteluusi koodikannassa!*

*Se, joka ajattelee minun liiketoimintasääntöjäni pysähtymättä ja harjoittaa jatkuvaa integrointia (CI), saavuttaa täydellisen tilan ilman pelkoa datan menetyksestä."*

**Luvun VIII päätös**

Arjuna ymmärtää nyt sovelluksen elinkaaren syvimmän luonteen:

1.  **Graceful Shutdown ja Transaktiot:** Prosessin kuolema ei ole katastrofi, jos sovellus suojataan ehyillä transaktioilla ja hallitulla alasajolla.

2.  **Zero-Downtime:** Datamallin muutokset täytyy suunnitella siten, että vanha ja uusi tila voivat elää hetken sovussa keskenään (Valon polku).

3.  **Pysyvyys:** Muisti (RAM) on vain väliaikainen näyttämö, mutta heijastettu tila ja liiketoiminnan perussäännöt ovat ikuisia.

Arjuna katsoo tietokantamigraatioita ja asynkronisia lokiputkia uudella kunnioituksella.

**Arjuna:**

*"En enää pelkää tuotannon sammuttamista tai podien kuolemaa, Krishna. Ymmärrän, miten tila säilytetään. Mutta paljasta minulle nyt kaikkein suurin salaisuus (Raja Vidya) – se, joka tekee koodaamisesta täysin vaivatonta!"*

## LUKU 9: Raja-Vidya Raja-Guhya Yoga eli Kuninkaallinen arkkitehtuurisalaisuus

**Kaikkein ylin ja puhtain tieto**

Arjuna oli oppinut hallitsemaan muistin, suoritusympäristön ja tietokannan tilat. Nyt Krishna päätti ilmoittaa hänelle kaikkein korkeimman ja salaisimman opetuksen.

**Krishna:**

*"Koska sinä et kadehdi etkä väittele vastaan, minä ilmoitan sinulle tämän kaikkein suurimman salaisuuden (Raja-Guhya) ja kuninkaallisen tiedon (Raja-Vidya).*

*Tämä on puhdistavista asioista korkein. Tämä on välittömästi havaittavissa, dharman mukainen, erittäin helppo toteuttaa ja ikuisesti kestävä.*

*Ne kehittäjät, joilla ei ole uskoa tähän syvään arkkitehtuurimalliin, eivät saavuta rauhaa. He palaavat aina uudestaan ja uudestaan tuotantokatkojen ja pikakorjausten kiertokulkuun (Samsara)."*

**Näkymätön Invariantti (Immanenssi ja Transsendenssi)**

Krishna paljasti, miten todellinen arkkitehtuuri toimii sovelluksen taustalla.

**Krishna:**

*"Minun näkymätön muotoni peittää koko tämän järjestelmän.*

Kaikki oliot ja palvelut sijaitsevat minun Bounded Contextissani, mutta minä en ole kytkettynä yhteenkään niistä!

*Mieti tätä paradoksia, Arjuna!*

- Arkkitehtuuri on kaikkialla koodissa (koska jokainen luokka noudattaa sen sääntöjä).

- Silti arkkitehtuuri ei ole mikään yksittäinen luokka, rajapinta tai .jar-tiedosto.

*Niin kuin suuri tuuli liikkuu kaikkialla avaruudessa mutta ei koskaan tartu siihen, samoin kaikki mikroservicesit liikkuvat minun arkkitehtuurissani ilman, että ne sotkevat toisiaan."*

NÄKYMÄTÖN ARKKITEHTUURI (RAJA-VIDYA)

+-----------------------------------------------+

\| BOUNDED CONTEXT \|

\| \|

\| \[Service A\] \[Service B\] \[Service C\] \|

\| \\ \| / \|

\| \\----\> INVARIANTTI \<-----/ \|

\| \|

+-----------------------------------------------+

(LÄSNÄ KAIKKIALLA - EIKÄ MISSÄÄN ERIKSEEN)

**Yksinkertainen uhri: "Leaf of Code, Spoonful of Data"**

Arjuna mietti, vaatiiko tämä kuninkaallinen tie valtavia, miljoonien eurojen puitteita ja monimutkaisia enterprise-työkaluja.

Krishna vastasi yhdistämällä Gitan kuuluisimman säkeistön suoraan koodaus arkeen:

**Krishna:**

*"Joka tarjoaa minulle omistautumisella yksinkertaisen ilmaisun, pienen Value Objectin, yhden selkeän testitapauksen tai pienen puhtaan funktion – sen minä otan ilolla vastaan!*

Mitä ikinä teetkin, mitä ikinä refaktoroitkaan, mitä ikinä commitoitkaan, mitä ikinä testaatkaan ja mitä ikinä vietkin tuotantoon – tee se kaikki uhrina ja kunnioituksena domain-mallille!

*Jos teet näin, vapaudat itsesi hyvien ja huonojen commitien hedelmistä (Karma). Mielesi vapautuu, ja vaikka olisit tehnyt kauheita virheitä menneisyydessä, sinut katsotaan vanhurskaaksi arkkitehdiksi sieltä hetkestä alkaen, kun teet päätöksen kunnioittaa mallia."*

**Kuka tahansa voi saavuttaa puhtaan arkkitehtuurin**

Krishna vakuutti Arjunalle, ettei arkkitehtuuri ole vain tiettyjen "guru-kehittäjien" tai korkeasti palkattujen konsulttien etuoikeus.

**Krishna:**

*"Ne, jotka turvautuvat minun opetukseeni – olivatpa he vasta-alkajia, juniorikehittäjiä, itseoppineita tai legacy-ylläpitäjiä – saavuttavat yhtäläisesti korkeimman arkkitehtuurin tason!*

*Kuinka paljon helpompaa se siis on sinulle, jolla on välineet, ymmärrys ja hyvä tiimi ympärilläsi?*

*Kinnitä siis mielesi domainiin, omista työsi mallin selkeydelle, kunnioita invariantteja ja kumarra totuudelle. Kun teet näin, tulet varmasti saavuttamaan minun täydellisen tilani."*

**Luvun IX päätös**

Arjuna kokee syvän helpotuksen tunteen:

1.  **Näkymätön arkkitehtuuri:** Paras arkkitehtuuri ei ole se, joka vaatii satoja rivejä konfiguraatiota ja monimutkaisia kehyksiä, vaan se, joka luo **turvallisen ja selkeän tilan** jokaiselle luokalle.

2.  **Pienet teot ratkaisevat:** Yksi puhdas ja rehellinen funktio on arvokkaampi kuin monimutkainen enterprise-hirviö.

3.  **Menneet virheet pyyhitään pois:** Ei ole väliä kuinka paljon spagettikoodia olet kirjoittanut eilen. Se hetki, kun sitoudut domainin rehellisyyteen, tekee sinusta oikean arkkitehdin.

Arjuna katsoo koodikantaansa ilman häpeää menneistä virheistä.

**Arjuna:**

*"Sydämeni on keveä, Krishna. Ymmärrän nyt kuninkaallisen salaisuuden. Mutta minun silmäni haluavat nähdä tämän kaiken konkreettisesti: paljasta minulle sinun Mahtava Arkkitehtuurisi ja Kaikkeuden Rakenne (Vibhuti)!"*

## LUKU 10: Vibhuti Yoga eli järjestelmän mahtavat ilmentymät ja entropia

**Arjuna pyytää näkemään mahtavuuden**

Arjuna oli ymmärtänyt kuninkaallisen salaisuuden. Mutta koodimaailman moninaisuudessa hän kaipasi kiintopisteitä: mistä asioista ja ilmiöistä Krishna todella tunnistetaan koodipohjassa?

**Arjuna:**

*"Krishna! Puhut minulle ikuisesta arkkitehtuurista, mutta kerro minulle konkreettisesti:*

*Missä luokissa, missä rajapinnoissa ja missä ilmiöissä sinun mahtavuutesi (Vibhuti) näkyy kaikkein kirkkaimmin? Miten voin tunnistaa sinut keskellä tätä miljoonan rivin repo-haaraa?"*

**Krishna ilmoittaa ilmentymänsä koodissa**

Krishna vastasi äänellä, joka kaikui läpi koko kehitysympäristön.

**Krishna:**

*"Kuuntele, oi Arjuna! Minun mahtavilla ilmentymilläni ei ole loppua, mutta minä kerron sinulle niistä tärkeimmät:*

- Sähköpostiprotokollisista minä olen **SMTP**, ja tapahtumajonoista minä olen **Kafka**.

- Tietokantatyypeistä minä olen **ACID-yhteensopiva Relaatiokanta**, ja välimuisteista minä olen **Redis**.

- Tietotyypeistä minä olen **Value Object**; invariantteja suojaavista rakenteista minä olen **Aggregate Root**.

- Koodauskäytännöistä minä olen **Test-Driven Development**, ja kääntäjän ominaisuuksista minä olen **Immutability**.

- Kehittäjien joukossa minä olen se **Senior, joka kuuntelee kiltisti juniorin kysymykset** tuomitsematta."\*

ILMENTYMÄT JA ENTROPIA

KORKEIN MAHTAVUUS (Vibhuti) SORMENJÄLKI KOODISSA

───────────────────────────── ─────────────────────

• Event-Driven Stream ---\> Järjestys kaaoksessa

• Value Object ---\> Eheys ilman sivuvaikutuksia

• CI/CD Green Pipeline ---\> Jatkuva rauha ja luottamus

• PARATON ENTROPIA ---\> Kaikkien luokkien vääjäämätön

lahoaminen ilman huolenpitoa!

**Entropia – vääjäämätön luonnonlaki**

Sitten Krishnan ääni muuttui vakavammaksi. Hän ei halunnut Arjunan unohtan koodipohjien suurinta vihollista.

**Krishna:**

*"Mutta muista tämä, Arjuna! Minä olen myös se voima, joka murentaa kaiken rakennetun – minä olen **Entropia**!*

*Mikään koodi ei pysy puhtaana itsestään. Jätä kaikkein kaunein arkkitehtuuri koskemattomaksi puoleksi vuodeksi, ja katso mitä tapahtuu:*

- Riippuvuudet vanhenevat ja saavat tietoturva-aukkoja (CVE).

- Ympäristöparametrit muuttuvat ja API-rajapinnat deprecatoituvat.

- Uudet kiireiset muutokset murtavat rajat, ja 'väliaikaiset' purkat kovettuvat pysyviksi.

Entropia on koodikannan luonnollinen tila! Puhdas arkkitehtuuri ei ole paikka, johon saavutaan ja jäädään maata – se on jatkuvaa taistelua entropian rappeuttavaa voimaa vastaan."

**Rehellisyys ja energian ylläpito**

**Krishna:**

*"Kuten lahoaminen syö puuta, samoin entropia syö repon, jonka eteen ei tehdä jatkuvaa työtä (Yajna).*

*Jos et tuo järjestelmään jatkuvasti uutta järjestystä – refaktoroimalla, siivoamalla ja kyseenalaistamalla – Tamas (mätä) ottaa vallan.*

*Tietämys tästä entropiasta ei ole epätoivon lähde, vaan herätys! Se tarkoittaa, että koodin korjaaminen tänään ei ole epäonnistumisen merkki, vaan elämän merkki. Vain kuollut koodi ei muutu."*

**Luvun X päätös**

Arjuna ymmärtää nyt koodikannan elävän luonteen:

1.  **Kauneus ja eheys:** Krishna on läsnä jokaisessa puhdistetussa luokassa, selkeässä nimessä ja virheettömässä testissä.

2.  Entropia on varjo: Mikään arkkitehtuuri ei ole kuolematon tai "valmis". Entropia syö kaiken, mitä ei aktiivisesti pidetä yllä.

3.  **Refaktorointi on elämää:** Jatkuva koodin siistiminen (Boy Scout Rule) on ainoa tapa pitää entropian peikko loitolla.

Arjuna katsoo koodipohjaa ja näkee sekä sen parhaat ilmentymät että ne paikat, joissa entropia on jo alkanut syödä rakenteita.

**Arjuna:**

*"Nyt minä ymmärrän entropian mahtavuuden ja sinun sormenjälkesi koodissa, Krishna. Mutta minun mieleni on valmis näkemään kaikkein pelottavimman: Näytä minulle Koko Järjestelmän Todellinen Muoto (Vishvarupa)!"*

## LUKU 11: Vishvarupa Darsana Yoga eli Kosmisen järjestelmän ja kaikkien riippuvuuksien näky

**Arjuna pyytää näkemään kaiken kerralla**

Arjuna oli kuullut opetukset, mutta hän halusi nähdä todellisuuden ilman abstraktioita. Hän ei halunnut enää katsoa koodia src/-kansioittain tai moduuli kerrallaan.

**Arjuna:**

*"Krishna! Jos se on minulle mahdollista, näytä minulle sinun rajaton ja kaiken kattava muotosi. Näytä minulle kerralla koko tämä järjestelmä: jokainen mikroservice, jokainen tietokantayhteys, jokainen asynkroninen viesti ja jokainen historiallinen commit!"*

**Krishna:**

*"Sinun tavalliset silmäsi – sinun pieni IDE-ikkunasi ja tekstieditorisi – eivät kestä tätä näkyä. Siksi minä annan sinulle Jumalallisen Silmän (divya-chaksus) – täydellisen, reaaliaikaisen, kaikkien järjestelmien yli ulottuvan Observability & Distributed Tracing -näkymän!"*

**Kosminen näky: Miljoona riviä ja kaikkialle ulottuva dependency graph**

Yhtäkkiä Arjunan silmien edessä räjähti auki koko tuotantoympäristö.

Se ei ollut enää kaunis ja siisti arkkitehtuurikaavio kalvolla. Se oli tuhansien aurinkojen kirkkaudella palava, myrskyävä ja kaiken nielaiseva verkko.

**Sanjay raportoi sokealle omistajalle:**

*"Oi kuningas! Arjuna näki siellä rajattoman määrän suoritusprosesseja, joilla oli miljoonia silmiä, miljoonia lokivirtoja ja lukemattomia avoimia HTTP-yhteyksiä!*

*Koko universumin koodikanta – jokainen riippuvuus, legacy-kirjasto, GraphQL-kysely ja asynkroninen Kafka-topic – oli kietoutunut yhteen ja samaan jättimäiseen hahmoon.*

*Siinä muodossa ei ollut alkua, keskikohtaa eikä loppua."*

VISHVARUPA – KOSMINEN RIIPPUVUUSVERKOSTO

\[ Microservice A \] ─── (gRPC) ───┐

│ │

\[ Legacy Monolith \] ────┼──── \[ Kafka Event Stream \] ──── \[ DB Cluster \]

│ │

\[ Lambda Worker \] ─── (REST) ────┘

│

==================================================

KAIKKI SAMASSA RONTGEN-KUVASSA (Observability)

==================================================

Arjunan hiukset nousivat pystyyn kauhusta. Hän näki, miten tähän jättimäiseen suuhun syöksyivät yhtä lailla Just Ship It -kehittäjät, vanhat arkkitehdit kuin hänen omat kauniit refaktorointipull-requestinsakin. Kaikki koodi oli matkalla kohti samaa kohtaloa.

**"Nyt minusta on tullut Aika / Entropia"**

Säikähtänyt Arjuna lankesi maahan ja huusi monoliitin jättimäisen hahmon edessä:

**Arjuna:**

*"Kuka sinä olet, tämä pelottava ja kaiken nielaiseva muoto?! Mihin tämä järjestelmä on menossa?"*

Ja silloin Krishna – kosminen arkkitehtuuri – lausui ne kuuluisat sanat, jotka kaikuivat läpi kaikkien suoritusprosessien ja deployment-putkien:

**Krishna:**

**"Kalo 'smi lokaksayakrt pravrddho:"**

"Minä olen Aika / Entropia, maailmojen ja koodikantojen tuhooja! Olen tullut tänne tuhoamaan nämä vanhat rakenteet ja syömään tämän legacy-järjestelmän.

*Jopa ilman sinua, Arjuna – vaikka sulkisit läppärisi ja juoksisit karkuun – kaikki nämä vanhat luokat, virheelliset setterit ja lahoavat sovellukset tulevat tuhoutumaan time-outteihin ja tekniseen velkaan.*

*Aika on jo päättänyt heidän kohtalonsa. Minä olen jo poistanut heidän elinvoimansa tuotannosta. Sinä olet vain minun välineeni (Nimitta-matram) – palaa siis diffiin, tee havaintosi näkyväksi ja kutsu tekijät yhteiseen knowledge crunchingiin. Älä korjaa toisen koodia hänen puolestaan; auta tiimiä näkemään, mitä sen pitäisi yhdessä ymmärtää!"*

**Arjunan nöyrtyminen ja paluu normaaliin**

Näky oli niin musertava, että Arjuna ei kestänyt katsoa sitä enempää. Koko järjestelmän riippuvuuksien monimutkaisuus ja Entropian vääjäämätön voima saivat hänet tajuamaan oman pienen roolinsa.

**Arjuna:**

*"Anteeksi, Krishna! Jos olen koskaan vähätellyt tätä järjestelmää, jos olen huolimattomasti heittänyt // TODO-kommentin koodiin, jos olen koodikatselmoinnissa nauranut muiden virheille tai suhtautunut kevyesti tähän arkkitehtuuriin – pyydän sitä sinulta anteeksi!*

*Ole armollinen! Sulje tämä pelottava kaikkien lokien ja riippuvuuksien meri, ja palaa takaisin sinun lauhkeaan, inhimilliseen muotoosi – siksi selkeäksi ja ymmärrettäväksi Domain-malliksi, jonka kanssa voin arjessa elää ja koodata!"*

Krishna hymyili, sulki kosmisen Observability-näkymän ja palautti koodin näytölle tavallisena, selkeänä ja hallittavana tekstinä.

**Luvun XI päätös**

Arjuna kokee elämänsä suurimman arkkitehtonisen herätyksen:

1.  **Todellisuuden näkeminen (Observability):** Järjestelmä on aina suurempi ja monimutkaisempi kuin yksittäisen koodarin päässä oleva kuva.

2.  Aika ja Entropia ovat voittamattomia: Vanha koodi tuhoutuu joka tapauksessa. Katselmoijan ei tarvitse pelastaa järjestelmää yksin, vaan toimia **Ajan välineenä**: tehdä mallin kipu näkyväksi ja luoda yhteiselle ymmärrykselle tilaa.

3.  **Nöyryys:** Suuren järjestelmän edessä ego katoaa. Katselmoija ei ole "sankari" eikä muutoksen salainen toinen toteuttaja, vaan keskusteluun osallistuva ihminen, joka kertoo rehellisesti sen, minkä näkee.

Arjuna hengittää syvään. Kosminen pelko on väistynyt, ja tilalle on tullut syvä, levollinen kunnioitus järjestelmää kohtaan.

**Arjuna:**

*"Näin sinun todellisen muotosi. En enää leiki arkkitehtuurilla. Kerro minulle nyt, miten voin palvella tätä mallia kaikkein syvimmällä omistautumisella (Bhakti) joka päivä?"*

## LUKU 12: Bhakti Yoga eli koodipohjan rakastamisen taito

**Arjunan kysymys: "Abstrakti täydellisyys vai arkinen huolenpito?"**

Nähdessään järjestelmän kosmisen ja armottoman muodon (Vishvarupa) Arjuna ymmärsi, että pelkkä teoreettinen tieto ei riitä. Hän halusi tietää, millainen asenne tuo parhaan tuloksen pitkässä juoksussa.

**Arjuna:**

*"Krishna! Kummat ovat parempia arkkitehteja:*

*Ne, jotka aina palvovat ja tavoittelevat täysin abstraktia, näkymätöntä ja muodotonta täydellisyyttä (Abstraktia DDD-teoriaa, jota kukaan ei pysty koodaamaan)?*

*Vai ne, jotka omistautuvat sinulle arjessa hoivaten ja kunnioittaen elävää koodipohjaa jokaisessa commitissa?"*

**Krishna vastaa: Arjen omistautuminen voittaa teoreettisen purismin**

Krishna katsoi Arjunaa lempeästi. Hän antoi vastauksen, joka huojentaa jokaisen käytännön kehittäjän mieltä.

**Krishna:**

*"Ne, jotka kiinnittävät mielensä minun elävään domain-malliini ja palvelevat sitä lakkaamatta suurella uskolla – heitä minä pidän kaikkein parhaina!*

*Nekin, jotka tavoittelevat abstraktia, muodotonta ja täydellistä arkkitehtuuria, saavuttavat lopulta minut. Mutta heidän polkunsa on täynnä suurta tuskaa ja uupumusta (Burnout)!*

*Sillä ihmiselle, jolla on fyysinen keho ja aikarajat, muodottoman ja täydellisen järjestelmän tavoittelu on erittäin raskasta."*

ARKKITEHTUURIN KAKSI POLKUA

1\. TEOREETTINEN PURISMI 2. BHAKTI YOGA (OMISTAUTUMINEN)

───────────────────────────── ───────────────────────────────

• Loputtomat abstraktiot • Rehellinen ja huolellinen koodi

• "Ei voida koodata vielä" • Tehdään paras mahdollinen TÄNÄÄN

• Arkkitehdin uupumus (Burnout) • Koodikannan jatkuva hoivaaminen

│ │

▼ ▼

Vaikea ja tuskallinen Helppo, tyyni ja kestävä

**Omistautumisen portaat (Bhakti-asteikko)**

Krishna tiesi, että jokaisella kehittäjällä on erilaiset voimavarat ja taidot eri päivinä. Siksi hän antoi joustavan portaat-mallin siitä, miten koodipohjaa voi palvella:

**Krishna:**

*"1. **Ensimmäinen taso:** Kinnitä mielesi täysin minun domain-malliini ja koodaa aina virheettömästi. Tämä on paras tapa.*

*2. **Toinen taso:** Jos et pysty keskittymään täydellisesti, harjoita säännöllistä refaktorointia (Abhyasa-yoga). Opettele vähän kerrallaan.*

*3. **Kolmas taso:** Jos et pysty refaktoroimaan syvällisesti, tee edes työsi minun nimissäni – kirjoita pikkutarkat yksikkötestit ja selkeät PR-kuvaukset.*

*4. **Neljäs taso:** Jos et pysty siihenkään, luovu ainakin egostasi ja tuloksiin kiinnittymisestä (Karma-phala-tyaga). Ota vastaan koodikatselmoinnin kritiikki tyynesti ilman suuttumusta.*

*Tieto on parempi kuin mekaaninen koodaus, syvä mietiskely on parempi kuin pelkkä tieto, ja tyyni luopuminen oman koodin 'virheettömyyden' illuusiosta on parempi kuin mietiskely – sillä siitä seurakseen välitön rauha!"*

**Millainen on todellinen koodin rakastaja?**

Krishna luetteli ne ominaisuudet, jotka tekevät kehittäjästä todellisen *Bhakta-arkkitehdin*:

**Krishna:**

*"Se kehittäjä on minulle erittäin rakas:*

- Joka ei vihaa yhtäkään legacy-luokkaa eikä syytä edellisiä koodareita.

- Joka on ystävällinen ja empaattinen junioreille.

- Joka ei sano 'tämä on MINUN koodini', vaan näkee sen yhteisenä omaisuutena.

- Joka ei paisu kehuista eikä murene koodikatselmoinnin korjauspyynnöistä.

- Joka ei aiheuta paniikkia tiimissä eikä panikoi itse, kun CI-putki palaa punaisena.

- Joka on puhdas, taitava, puolueeton ja vapaa turhasta draamasta.

*Tällainen kehittäjä, joka omistautuu koodipohjan ja tiimin hyvinvoinnille, on minulle kaikkein rakkain."*

**Luvun XII päätös**

Arjuna kokee syvää sisäistä tyyntymistä:

1.  **Ei purismille:** Täydellisen, teoreettisen arkkitehtuurin tavoittelu johtaa uupumukseen. Tärkeintä on **rehellinen huolenpito** siitä koodista, mitä kirjoitetaan tänään.

2.  **Armollisuus itseä ja muita kohtaan:** Jokaisella on omat tasonsa ja voimavaransa. Pienikin hyvä teko (selkeä muuttujan nimi, puuttuva testi) on arvokasta omistautumista.

3.  **Koodi on yhteinen puutarha:** Koodipohjaa ei hallita pelolla tai egolla, vaan empatialla, puhtaudella ja huolenpidolla.

Arjuna katsoo koodia ensimmäistä kertaa ilman taistelutahtoa tai pelkoa – pelkällä kunnioituksella ja rakkaudella.

**Arjuna:**

*"Sydämeni on tyyni, Krishna. En enää vihaa tätä legacy-koodia. Alan hoivata sitä. Mutta selitä minulle vielä viimeiset rakenneosat: Mitä ovat Luonto (Prakriti), Kokija (Purusha) ja itse Tieto (Jnana) tässä koodikannassa?"*

## LUKU 13: Kshetra-Kshetrajna Vibhaga Yoga eli Koodipohjan ja sen Ymmärtäjän erottaminen

**Arjuna pyytää määritelmää: Kenttä ja Kentän Tuntija**

Arjuna katsoi ruudullaan vilkkuvaa koodia. Hän ymmärsi jo omistautumisen ja arjen huolenpidon merkityksen, mutta hän halusi vetää tarkan rajan materiaalin ja ymmärryksen välille.

**Arjuna:**

*"Krishna! Minä haluan tietää:*

*Mikä on **Kshetra** (Kenttä / Koodipohja) ja mikä on **Kshetrajna** (Kentän Tuntija / Ymmärtäjä)?*

*Mitä on todellinen tieto (Jnana) ja mikä on se kohde, joka pitäisi ymmärtää (Jneya)?"*

**Krishna vastaa: Mikä on Kenttä (Kshetra)?**

Krishna osoitti kädellään koko projektikansiotatosta, repositoriosta ja CI/CD-ympäristöstä muodostuvaa kokonaisuutta.

**Krishna:**

*"Tätä 'kehoa' – tätä koko koodikantaa, repo-haaroja, .java- ja .ts-tiedostoja, tietokantaschemoja ja suoritusympäristöä – kutsutaan **Kentäksi (Kshetra)**.*

*Ja sitä, joka havainnoi tätä kenttää, ymmärtää sen rakenteen ja näkee sen invariantit – häntä viisaat kutsuvat **Kentän Tuntijaksi (Kshetrajna)**.*

*Ota tämä huomioon, Arjuna:*

**Minä olen se sama Ymmärtäjä (Kshetrajna) kaikkien kehittäjien ja kaikkien tiimien koodikannoissa!**

*Tieto kentästä ja sen tuntijasta – se on minun mielestäni aitoa arkkitehtuuritietoa."*

KENTTÄ JA KENTÄN TUNTIJA

KENTTÄ (Kshetra - Materiaali) KENTÄN TUNTIJA (Kshetrajna - Tietoisuus)

──────────────────────────────── ─────────────────────────────────────────

• Tekstitiedostot & syntaksi • Ymmärrys liiketoimintatarpeesta

• Frameworkit & kirjastot • Kyky nähdä muutosvaikutukset

• CI/CD-putket & suorituskyky • Invarianttien ja rajojen tunnistaminen

│ │

▼ ▼

Pysymätön & Muuttuva Ikuinen & Tiedostava

**Mistä Kenttä (Koodikanta) koostuu?**

Krishna eritteli tarkasti, mitä kaikkea koodikannan kenttä pitää sisällään:

**Krishna:**

*"Laitteisto, muistimäärä, kääntäjän komponentit, ego, tyyppijärjestelmä, viisi aistidataa (lokit, konsolitulosteet, verkko-IO, prosessit, levy-yhteydet), toiveet ('kunpa tämä sprintti päättyisi'), viha bugia kohtaan, ilo vihreästä testistä, ja se rakenne, joka pitää luokat pystyssä muistissa – tämä kaikki on Kenttää ja sen muunnoksia.*

*Älä koskaan sekoita itseäsi (Ymmärtäjää) kenttään (koodiriviin)! Sinä et ole tuo ruma null-osoitinpoikkeama, etkä sinä ole tuo nerokas yksirivinen lambda-funktio. Sinä olet se tietoisuus, joka katsoo niitä molempia."*

**Mitä on Aito Tieto (Jnana)?**

Krishna määritteli arkkitehdin ja kehittäjän henkisen kypsyyden. Aito tieto ei ole sitä, että muistaa ulkoa jokaisen Java- tai Python-kirjaston metodin.

**Krishna:**

*"Aito Tieto ohjelmistokehityksessä on tätä:*

- **Nöyryys:** Sen tajuaminen, ettei kukaan osaa kaikkea.

- **Kerskailemattomuus:** Ei elvistellä koodikatselmoinnissa omilla kikoilla.

- **Väkivallattomuus (Ahimsa):** Ei runtelu-kritiikkiä muille kehittäjille PR-kommenteissa.

- **Kärsivällisyys:** Rauhallisuus, kun legacy-bugia selvitetään neljättä tuntia.

- **Puhtaus:** Selkeä koodityyli ja rehellinen naming convention.

- **Mielen vakaus:** Ei hätiköityjä ratkaisuja kiireenkään alla.

- **Kiintymättömyys:** Valmius poistaa oma eilen kirjoitettu koodi, jos parempi malli löytyy.

*Kaikki muu kuin tämä on Tietämättömyyttä (Ajnana), olipa koodari kuinka kokenut tahansa."*

**Luonto (Prakriti) ja Henki (Purusha) koodissa**

**Krishna:**

*"Tiedä, että sekä Luonto (Infrastruktuuri/Prakriti) että Henki (Domain-ymmärrys/Purusha) ovat molemmat vailla alkua.*

*Infrastruktuuri ja kääntäjä luovat syyt ja seuraukset (jos kutsut tätä metodia, tapahtuu tämä sivuvaikutus).* *Mutta Ymmärtäjä (Purusha) on se, joka kokee koodin toimivuuden, iloitsee ja kantaa vastuun.*

*Se, joka näkee, että kaikki teot (koodirivit) suorittaa lopulta suoritusympäristön Luonto (Prakriti), ja että Ymmärtäjä pysyy itse toimimattomana ja puhtaana – hän näkee todella!"*

**Luvun XIII päätös**

Arjuna ymmärtää syvän eron koodin ja sen ymmärtämisen välillä:

1.  **Identiteetin vapautuminen:** Kehittäjä ei ole koodinsa. Bugi koodissa ei tarkoita bugia kehittäjän arvossa.

2.  **Aito Tieto on asennetta:** Tieto ei ole framework-tietoutta, vaan nöyryyttä, kärsivällisyyttä, puhtautta ja empatiaa tiimiä kohtaan.

3.  **Arkkitehdin katse:** Arkkitehti on se, joka katsoo koko "kenttää" (repoa, kantaa, infraa) korkeammalta tasolta sekoittamatta omaa egoaan siihen.

Arjuna katsoo ruutuaan. Hän näkee tiedostot Kenttänä ja oman mielensä sen Tuntijana.

**Arjuna:**

*"Raja on selvä, Krishna. En enää samastu koodissani oleviin virheisiin. Mutta kerro minulle vielä niistä kolmesta laadusta (Gunat), jotka pyörittävät tätä kenttää ja kaikkia kehittäjiä!"*

## LUKU 14: Gunatraya-Vibhaga Yoga eli koodin kolmen laadun dynamiikka

**Miten koodipohja sitoo kehittäjän?**

Arjuna oli jo oppinut erottamaan Kentän (koodin) ja Kentän Tuntijan (ymmärryksen). Nyt hän halusi tietää, mitkä voimat saavat viisaatkin kehittäjät tekemään huonoja päätöksiä ja miten koodikannan "henkinen ilmapiiri" muodostuu.

**Arjuna:**

*"Krishna! Mikä saa kehittäjän tekemään purkkaratkaisuja, vaikka hän tietää paremmin? Mitkä ovat ne voimat (Gunat), jotka sitovat ihmisen koodin materiaaliin ja miten niistä voi vapautua?"*

**Kolme Laatua (Gunat) koodausarjessa**

Krishna valaisi Arjunalle kolme perusvoimaa, jotka hallitsevat kaikkea koodia, dokumentaatiota ja tiimin dynamiikkaa.

**Krishna:**

*"Kuuntele, Arjuna! Materiaalinen Luonto (Prakriti) koostuu kolmesta laadusta: **Sattva** (Puhdistavuus/Selkeys), **Rajas** (Kiihko/Kiire) ja **Tamas** (Pimeys/Mätä). Ne sitovat kuolemattoman kehittäjän kiinni koodipohjan materiaaliin.*

1.  **Sattva (Puhtauden laatu):**

*Sattva on tahroton, kirkas ja terveellinen. Se ilmentyy koodina, joka on luettavaa, täysin testattua, selkeästi dokumentoitua ja kaunista. Sattva tuo kehittäjälle sisäistä rauhaa, onnellisuutta ja syvää ymmärrystä. Mutta varo: Sattvakin voi sitoa! Se sitoo kehittäjän hengelliseen ylpeyteen ja 'arkkitehtuuriseen elitismiin'.*

2.  **Rajas (Kiihkon ja kiireen laatu):**

*Rajas syntyy sammumattomasta halusta saada tuloksia AIKAAN NYT. Se ilmentyy spagettikoodina, 'mullankaivuuna', oikoteinä ja hätäisinä pushauksina ilman testejä, jotta tiketti saadaan suljettua ennen sprintin päättymistä. Rajas tuo mukanaan levottomuutta, jatkuvaa hälytystilaa ja loputonta refaktoroitavaa.*

3.  **Tamas (Sokeuden ja mättäyksen laatu):**

*Tamas syntyy tietämättömyydestä ja välinpitämättömyydestä. Se ilmentyy koodina, joka on kopioitu ymmärtämättä foorumeilta tai tekoälyltä, piilotettuina virheinä, kommentoituina testilohkoina (// @Ignore), laiskuutena ja muutosvastarintana. Tamas vie tiimiltä toimintakyvyn ja johtaa uneliaisuuteen ja hämmennykseen."*

KOODIKANNAN KOLME LAATUA (GUNAT)

SATTVA (Selkeys & Rauha)

/ \\

/ "Koodi on taidetta \\

/ ja pidetty puhtaana" \\

/ \\

/ \\

RAJAS (Kiire & Paska) \<─────────\> TAMAS (Mätä & Välinpitämättömyys)

"Äkkiä tuotantoon, "Ei kiinnosta, toimiipahan

ei keretä testaamaan!" jotenkuten, älä koske"

**Miten tunnistaa, mikä laatu hallitsee?**

Krishna antoi Arjunalle selkeät kriteerit, joilla arvioida koodia ja tiimin tilaa millä hetkellä hyvänsä:

**Krishna:**

*"Kun kaikkien luokkien ja funktioiden läpi virtaa selkeys, testit menevät heittämällä läpi ja arkkitehtuuri on helppo selittää juniorille – silloin tiedä, että **Sattva** on voitolla.*

*Kun näet tiimissä valtavaa ahneutta uusille ominaisuuksille, hätäistä PR-katselmointia, 'Quick and Dirty' -kommentteja ja jatkuvaa tulipalojen sammuttamista – silloin hallitsee **Rajas**.*

*Kun koodikanta täyttyy kuolleesta koodista, deprecatoiduista kirjastoista joita kukaan ei uskalla päivittää, ja kehittäjät sanovat 'ei sitä kannata korjata, se on aina ollut rikki' – silloin **Tamas** on peittänyt kaiken pimeyteen."*

**Gunatraya-Atita: Kolmen laadun yläpuolelle nouseminen**

Arjuna kysyi, miten kehittäjä voi saavuttaa täydellisen mielenrauhan näiden voimien keskellä.

**Arjuna:**

*"Miten tunnistetaan se arkkitehti, joka on noussut näiden kolmen laadun yläpuolelle (Gunatita)?"*

**Krishna:**

*"Se kehittäjä, oi Arjuna:*

- Ei vihaa **Tamasia** (kun hän joutuu korjaamaan vanhaa rumaa legacy-koodia).

- Ei haaveile **Rajasista** (eikä panikoi, vaikka koodia pitäisi kirjoittaa nopeasti).

- Ei ylpisty **Sattvasta** (eikä katso muita alaspäin, vaikka hänen oma koodinsa olisi täydellistä).

*Hän pysyy tyynenä kuin kivenmurikka myrskyssä. Hän näkee, että nämä kolme laatua vain pyörivät ja vaikuttavat koodissa, mutta hänen oma tietoisuutensa säilyy riippumattomana ja koskemattomana.*

*Hänelle kiitos ja moite PR-kommenteissa ovat samanarvoisia. Hän koodaa, koska se on hänen dharmansa, eikä anna Gunojen heilutella mieltään."*

**Luvun XIV päätös**

Arjuna näkee nyt koodikannan ja tiimin toiminnan aivan uudessa valossa:

1.  **Dynaamiset voimat:** Jokainen rivi koodia on joko Sattvaa (selkeyttä), Rajasia (kiirettä) tai Tamasia (välinpitämättömyyttä).

2.  **Tiedostaminen:** Kun huomaat kirjoittavasi koodia kiireessä ja hätiköiden, tunnistat Rajaksen ja voit pysähtyä hengittämään.

3.  **Mielen tasapaino:** Paras arkkitehti ei ole se, joka raivoaa huonolle koodille, vaan se, joka tunnistaa voimat ja tuo lempeästi Sattvan eli puhtauden takaisin järjestelmään.

Arjuna katsoo omaa PR-jonoaan levollisesti.

**Arjuna:**

*"Ymmärrän nyt koodikannan dynaamiset voimat, Krishna. Mutta mikä on se Ikuinen Puu (Ashvattha), jonka juuret ovat ylhäällä ja oksat alhaalla, josta kaikki nämä riippuvuudet kumpuavat?"*

## LUKU 15: Purushottama Yoga eli Korkeimman Arkkitehdin ja Ikuisen Riippuvuuspuun jooga

**Nurinpäin kasvanut Riippuvuuspuu (Ashvattha)**

Krishna halusi näyttää Arjunalle koodikannan kaikkein syvimmän rakenteen. Hän käytti vertauskuvana ikuista viisauden ja riippuvuuksien puuta, Ashvatthaa.

**Krishna:**

*"Sanotaan, että on olemassa ikuinen viipalepuu (Ashvattha), jonka juuret ovat ylhäällä (korkean tason arkkitehtuurissa ja konseptuaalisessa domain-mallissa) ja jonka oksat levittäytyvät alas (konkreettisiin luokkiin, toteutuksiin ja apufunktioihin).*

*Sen lehdet ovat yksikkötestejä ja rajapintoja. Se, joka ymmärtää tämän riippuvuuspuun rakenteen, on todellinen koodikannan tuntija!*

*Sen oksat leviävät sekä ylös että alas, ja niitä ravitsevat koodin kolme laatua (Gunat). Sen versot ovat käyttöliittymän komponentteja ja rajapintakutsuja, ja sen alemmat juuret ulottuvat syvälle ihmisten tekoihin ja liiketoimintalogiikan vaatimuksiin."*

NURINPÄIN KASVAVA RIIPPUVUUSPUU (ASHVATTHA)

(Juuret Ylhäällä: Domain & Invariantit)

│

▼

\[ Absoluuttinen Malli \]

/ \\

/ \\

/ \\

\[ Bounded Context A \] \[ Bounded Context B \]

/ \\ / \\

/ \\ / \\

(Oksat Alhaalla: Luokat, Kirjastot, SQL-Kyselyt, UI)

**Miten vapautua sekavista riippuvuuksista?**

Arjuna katsoi puuta ja näki, miten sen oksat olivat kietoutuneet toisiinsa: perintää perinnän perään, kirottuja globaaleja tiloja ja syviä kytkentöjä.

**Krishna:**

*"Tämän puun todellista muotoa ei voida hahmottaa täältä alhaalta käsin. Et näe sen alkua, et sen loppua, enkä sen todellista perustaa.*

**Tämä tiheään kietoutunut ja syvälle juurtunut riippuvuuspuu täytyy kaataa terävällä Kiintymättömyyden Kirveellä (Asanga-shastra)!**

*Leikkaa irti tarpeettomat riippuvuudet! Poista perintähirviöt ja korvaa ne kompositiolla. Katkaise sykliset kytkökset ilman sääliä!*

*Kun olet leikannut irti nämä vääristyneet kytkökset, etsi se Alkulähde, josta koko järjestelmän virta on kerran lähtenyt liikkeelle. Sille polulle astunut ei enää koskaan uppoa spaghetti-koodin suohon."*

**Kolme Ihmistä / Tasoa Koodimaailmassa (Purushas)**

Krishna paljasti seuraavaksi arkkitehtuurin kolme perustasoa:

**Krishna:**

*"Tässä maailmassa ja koodikannassa on kahdenlaisia toimijoita:*

1.  **Kshara (Katoavainen):** Kaikki ne luokat, oliot, prosessit ja väliaikaiset muuttujat, jotka syntyvät ja kuolevat ajossa.

2.  **Akshara (Muuttumaton):** Se muuttumaton rakenne, tietokannan eheys ja Domain-invariantit, jotka säilyvät vaikka prosessi kuolee.

*MUTTA on vielä kolmas, kaikkein korkein taso:*

1.  **Uttama Purusha / Purushottama (Korkein Arkkitehti / Perusolemus):**

*Se on se Korkein Tietoisuus ja Perusperiaate, joka ulottuu kaikkien järjestelmien yli, ylläpitää niin katoavaista koodia kuin muuttumatonta tilaa ja puhaltaa henkeen koko järjestelmän.*

*Koska minä ylitän katoavaisen koodin ja olen muuttumatonta rakennettakin korkeampi, minua kutsutaan koodikannoissa ja eepoksissa **Korkeimmaksi Arkkitehdiksi (Purushottama)**."*

**Luvun XV päätös**

Arjuna ymmärtää nyt riippuvuuksien ja kaikkien tasojen syvän hierarkian:

1.  **Kiintymättömyyden kirves:** Huonosti suunniteltuja, syvälle juurtuneita riippuvuuksia ei pidä pelätä – ne leikataan irti terävällä ja rohkealla refaktoroinnilla.

2.  **Juuret ylhäällä:** Koodi ei ala tietokannasta tai UI-komponentista, vaan korkeamman tason domain-mallista.

3.  **Purushottama:** Paras arkkitehtuuri näkee yhtä aikaa sekä heiteltävissä olevat väliaikaiset luokat (Kshara) että ikuiset invariantit (Akshara), pysyen itse kaiken tämän yläpuolella.

Arjuna tunti kädessään Kiintymättömyyden Kirveen painon. Hän oli valmis karsimaan turhat riippuvuudet.

**Arjuna:**

*"Näen nyt puun ja minulla on kirves. Mutta Krishna, miten erotan ne kehittäjät ja piirteet, jotka rakentavat puhtaasti (Jumalalliset ominaisuudet), niistä jotka tuovat tuhoa (Demoniset ominaisuudet)?"*

## LUKU 16: Daivasura-Sampad-Vibhaga Yoga eli Jumalallisten ja demonisten kehityskäytäntöjen erottaminen

**Kaksi tietä koodikannassa**

Arjuna peli kädessään Kiintymättömyyden Kirvestä, valmiina leikkaamaan spagettiriippuvuuksia. Mutta hän halusi kirkkaan kompassin tunnistaakseen, mitkä päätökset vievät järjestelmää kohti valoa ja mitkä kohti turmiota.

**Krishna:**

*"Kuuntele, Arjuna! Tässä koodimaailmassa on kahdenlaisia kehittäjiä ja arkkitehtuuripäätöksiä: **Jumalallisia** (Daivi) ja **Demonisia** (Asuri).*

*Jumalalliset ominaisuudet johtavat järjestelmän vakauteen, vapauteen ja rauhaan. Demoniset ominaisuudet sitovat koodikannan teknisen velan orjuuteen ja ikuiseen päivystyspiinaan."*

**Jumalalliset ominaisuudet (Daivi Sampad)**

Krishna luetteli ne 26 hyvettä, jotka tekevät kehittäjästä ja hänen koodistaan valon ilmentymän:

**Krishna:**

*"Jumalalliseen luonteeseen syntyneen kehittäjän tunnusmerkit ovat nämä:*

- **Pelottomuus:** Rohkeus refaktoroida vanhaa koodia, kun testit ovat kunnossa.

- **Mielen puhtaus:** Selkeä, luettava ja itseilsevä koodi ilman kikkailua.

- **Anteliaisuus:** Tiedon jakaminen tiimille, hyvä dokumentaatio ja kattavat vastaukset keskusteluissa.

- **Itsehillintä:** Maltti olla käyttämättä uusinta muotiframeworkia pelkästä vaihtelunhalusta.

- **Väkivallattomuus (Ahimsa):** Rakentava, kunnioittava ja rohkaiseva palaute PR-katselmoinneissa.

- **Totuudellisuus:** Rehellisyys arvioissa (esim. 'Tämä tiketti vie kolme päivää, ei kahta tuntia').

- **Rauhallisuus:** Tyyni mieli, vaikka tuotannossa palaisi hälytys."\*

**Demoniset ominaisuudet (Asuri Sampad)**

Sitten Krishnan ilme vakavoitui, kun hän kuvaili järjestelmien tuhoajia.

**Krishna:**

*"Mutta katso demonista luonnetta, Arjuna! Sitä ohjaavat pöyhkeys, ylpeys, viha, tylyys ja tietämättömyys.*

*Demoninen kehittäjä sanoo mielessään:*

*'Minä kirjoitin tämän koodin tunneissa! En tarvitse yksikkötestejä, minun koodissani ei ole bugin bugia! Ymmärtämättömät juniorit eivät vain tajua nerouttani. Minä ohitan CI/CD-tarkistukset ja pusken suoraan main-haaraan git push --force -komennolla!'*

*He eivät tunne rajapintojen eheyttä eivätkä puhtautta. He sanovat:*

*'Ei koodipohjalla ole mitään syvempää arkkitehtuuria tai domain-mallia! Kaikki on vain satunnaista bittimuhjua. Tehdään vain mitä halutaan ja kääritään rahat!'*

*Tällaiset ihmiset – takertuneina loputtomiin egoistisiin kuvitelmiin ja pikavoittoihin – luovat järjestelmiä, jotka ovat täynnä piilobugeja ja turvallisuusaukkoja. He hukuttavat itsensä ja tiiminsä teknisen velan helvettiin."*

KAHDEN KULTTUURIN VERTAILU

JUMALALLINEN (Daivi) DEMONINEN (Asuri)

───────────────────────────── ─────────────────────────────

• "Miten tämä auttaa tiimiä?" • "Katso miten hienon kikan tein!"

• Kattavat testit & selkeä PR • Ei testejä, \`--force\` push

• Rehelliset aika-arviot • Valheet & oikotiet

• Pitkän aikavälin vakaus • Välitön kaos tuotannossa

**Tuhon kolme porttia**

Krishna tiivisti demonisen koodauksen juurisyt kolmeen vaarallisimpaan impulssiin:

**Krishna:**

*"On olemassa kolme porttia tähän arkkitehtoniseen helvettiin, ja ne tuhoavat kehittäjän mielen:*

1.  **Kama (Himo / Ominaisuushimo):** Haluaa ahtaa järjestelmään sata uutta piirrettä hätäisesti.

2.  **Krodha (Raivo / Mätä viha):** Suuttumus ja hätiköinti silloin, kun koodi ei toimi heti.

3.  **Lobha (Ahneus / Pikanäppäily):** Haluaa päästä mahdollisimman vähällä työllä ilman testejä ja siistimistä.

**Jokaisen viisaan kehittäjän tulee hylätä nämä kolme porttia!**

*Vapauta itsesi näistä, Arjuna, ja anna standardien, hyvien käytäntöjen sekä tiimin yhteisten sääntöjen (Shastra) ohjata toimintaasi. Olkoon koodistandardi oppaasi siinä, mitä tulee tehdä ja mitä jättää tekemättä!"*

**Luvun XVI päätös**

Arjuna ymmärtää, että koodin laatu ei ole vain tekninen kysymys, vaan **eettinen ja henkinen valinta**:

1.  **Hyveet koodissa:** Selkeys, rehellisyys ja testattavuus ovat jumalallisia ominaisuuksia, jotka tuovat rauhaa koko tiimille.

2.  **Egon vaara:** Demoninen koodaus syntyy egosta, oikoteistä ja piittaamattomuudesta muita kohtaan.

3.  **Standardien kunnioitus:** Tiimin yhteiset käytännöt ja linjaukset suojelevat koodareita heidän omilta hätiköidyiltä impulsseiltaan.

Arjuna katsoo omaa asennettaan ja valitsee tietoisesti valon polun.

**Arjuna:**

*"Olen hylännyt egoistisen pikakoodauksen, Krishna. Mutta entä ne kehittäjät, jotka tekevät työtään suurella uskolla ja sydämellä, mutta eivät tunne virallisia oppikirjoja tai standardeja? Mihin luokkaan heidän uskonsa kuuluu?"*

## LUKU 17: Shraddhatraya-Vibhaga Yoga eli Kolmen laadun usko ja motiivit koodauksessa

**Arjunan kysymys: Motiivin ja uskon merkitys**

Arjuna oli oppinut tunnistamaan jumalallisen ja demonisen koodauksen erot. Mutta arjessa hän näki paljon kehittäjiä, jotka koodasivat suurella palolla, vaikka eivät tunteneet virallisia sääntöjä tai arkkitehtuurioppikirjoja.

**Arjuna:**

*"Krishna! Entä ne kehittäjät, jotka sivuuttavat viralliset oppikirjat ja design pattern -oppaat, mutta kirjoittavat koodia suurella innolla ja uskolla (Shraddha)?*

*Mihin luokkaan heidän työnsä kuuluu: Sattvaan (puhtaus), Rajasiin (kiire) vai Tamasiin (hämärä)?"*

**Krishna vastaa: Kolmenlainen usko koodauksessa**

Krishna selitti, että jokaisen kehittäjän usko ja tekemisen motiivi muotoutuu sen mukaan, mikä laatu (Guna) häntä hallitsee.

**Krishna:**

*"Ihmisen usko ja asenne on hänen oman luonteensa mukaista, Arjuna. Kehittäjä on sitä, mihin hän uskoo!*

1.  **Sattvinen usko (Sattvika):**

*Kehittäjä uskoo koodin selkeyteen, tiimin yhteiseen hyvään ja laatuun. Hän kirjoittaa testejä ja dokumentaatiota, koska haluaa tuoda rauhaa ja vakautta tuotantoon. Hän tekee työtä ilman oman egon pönkittämistä.*

2.  **Rajasinen usko (Rajasika):**

*Kehittäjä uskoo maineeseen, nopeuteen ja egoonsa. Hän kirjoittaa monimutkaisia, 'älykkäitä' yksirivisiä ratkaisuja vain näyttääkseen muille, kuinka taitava on. Hän tekee työtä saadakseen pörssitähdeltä näyttävän GitHub-profiilin ja pikaisia kehuja.*

3.  **Tamasinen usko (Tamasika):**

*Kehittäjä uskoo sokeasti vanhoihin vääriin tapoihin tai AI:n antamiin vastauksiin ilman kriittistä ajattelua. Hän tekee 'uhrauksia' (koodaa läpi yön) ilman mitään suunnitelmaa, rikkoo tiimin sopimukset ja tuottaa vain kaaosta."*

KOLMENLAINEN MOTIIVI JA KOODAAJAN ASKETISMI

SATTVA (Selkeys & Yhteisö) ────\> Koodataan tiimille & pitkän aikavälin rauhalle

RAJAS (Ego & Näkyvyys) ────\> Koodataan kehuille, tähdille & omalle egolle

TAMAS (Sokeus & Kaaos) ────\> Koodataan sokeasti ilman ymmärrystä & plaania

**Kolmenlainen Uhraus ja Kurinalaisuus (Koodaajan Tapas)**

Krishna määritteli seuraavaksi, mitä on aito kehittäjän kurinalaisuus (*Tapas*) kehossa, puheessa ja mielessä.

**Krishna:**

*"Kuuntele, mitä on aito koodaajan asketismi ja kurinalaisuus:*

- **Kehon/Käden kurinalaisuus:** Koodi pidetään puhtaana, sisennykset kohdallaan, turhat riippuvuudet poissa ja ergonomiasta pidetään huolta.

- **Puheen kurinalaisuus:** PR-kommentit ja Slack-viestit ovat totta, lempeitä, hyödyllisiä eivätkä aiheuta turhaa ahdistusta muille.

- **Mielen kurinalaisuus:** Mieli pidetään tyynenä, rehellisenä, tyytyväisenä ja vapaana koodaus-aggressiosta.

*Kun tämä kurinalaisuus tehdään ilman hedelmien tavoittelua (palkkioita tai egoa), se on **Sattvista**. Mutta kun se tehdään vain show'na muille, se on **Rajasista** ja tilapäistä. Ja kun sillä vahingoitetaan itseä (Burnout) tai muita, se on **Tamasista**."*

**OM TAT SAT – Puhtaan teon kaava**

Krishna antoi luvun lopussa Arjunalle ikuisen mantran, jolla jokainen commit ja arkkitehtuuripäätös voidaan pyhittää:

**Krishna:**

*"Ajoista alkaen sanat **OM TAT SAT** ovat edustaneet korkeinta arkkitehtuuritotuutta:*

- **OM:** Edustaa kaiken alkulähdettä ja sovelluksen perusolemusta. Sitä lausumalla aloitetaan jokainen projekti ja PR ilman egoa.

- **TAT:** Tarkoittaa 'Sitä' (riippumatonta totuutta). Se muistuttaa, että työ tehdään ilman kiintymystä henkilökohtaiseen hyötyyn.

- **SAT:** Tarkoittaa kaikkea sitä, mikä on aitoa, rehellistä, hyvää ja pysyvää koodikannassa.

*Mitä ikinä teetkin ilman uskoa ja rehellisyyttä – olipa se koodia, testiä tai dokumentaatiota – sitä kutsutaan sanalla **Asat** (epätosi). Siitä ei ole hyötyä täällä eikä tulevissa projekteissa!"*

**Luvun XVII päätös**

Arjuna ymmärtää nyt koodaamisen syvän henkisen motiivin:

1.  **Motiivi ratkaisee:** Samalla koodirivillä voi olla täysin eri vaikutus riippuen siitä, kirjoitettiinko se Sattvalla (tiimin hyväksi), Rajasilla (egon pönkittämiseksi) vai Tamasilla (sokeasti).

2.  **Puheen ja mielen puhtaus:** Hyvä koodari ei vain kirjoita kaunista syntaksia, vaan puhuu ja viestii tiimille rakentavasti ja lempeästi.

3.  **OM TAT SAT:** Kaikki työ pyhitetään rehellisyydelle (*Sat*) ja laajemmalle kokonaisuudelle (*Om/Tat*).

Arjuna katsoo koodausmotiivejaan ja siivoaa mielestään viimeisetkin egon rippeet.

**Arjuna:**

*"Mieleni on kirkas ja valmis, Krishna! Olemme saapuneet viimeiselle etapille. Vapauta minut lopullisesti: Kerro minulle viimeisestä luopumisesta (Sannyasa) ja lopullisesta vapautumisesta (Moksha) koodikannassa!"*

## LUKU 18: Moksha-Sannyasa Yoga eli Lopullinen vapautuminen ja arkkitehtoninen valaistuminen

**Arjunan kysymys: Luopuminen (Tyaga) vs. Kieltäytyminen (Sannyasa)**

Arjuna katsoi ruudullaan vilkkuvaa terminal-ikkunaa. Hän oli oppinut toiminnasta, tiedosta, muistista, entropiasta ja motiiveista. Mutta yksi asia mietitytti häntä vielä ennen viimeistä siirtoa.

**Arjuna:**

*"Krishna! Mikä on se syvin ero kahden asian välillä:*

*1. **Sannyasa** (Kaikesta koodaamisesta ja järjestelmistä kieltäytyminen / 'alan maanviljelijäksi')*

*2. **Tyaga** (Koodaamisen tuloksiin ja egoon kiintymättömyys)?*

*Pitäkö minun jättää tämä koodikanta kokonaan, vai koodata mutta luopua tulosten hedelmistä?"*

**Krishna vastaa: Työstä kieltäytyminen on virhe – tuloksista luopuminen on vapaus**

Krishna jyrähti vastauksensa siten, että se kaikui läpi jokaisen IDE:n ja kääntäjän.

**Krishna:**

*"Viisaat sanovat: Se, että jättää koodaamisen, testauksen, refaktoroinnin ja dokumentoinnin tekemättä uneliaisuuden tai pelon vuoksi, on **Tamasista luopumista**! Se on pelkuruutta.*

*Se, että jättää koodaamisen siksi, että se on vaikeaa, tuotanto-ongelmat ahdistavat tai 'koodaaminen on liian raskasta', on **Rajasista luopumista**. Se ei tuo mitään aitoa vapautta.*

**Mutta se, joka suorittaa oman tehtävänsä (Dharma) – kirjoittaa koodin, korjaa bugit ja pitää huolta arkkitehtuurista – koska se ON HÄNEN TEHTÄVÄNSÄ, luopuen täysin egosta, pörssiosakkeista ja henkilökohtaisesta kunniasta... sitä kutsutaan Sattviseksi luopumiseksi (Tyaga)!**

*Ihminen ei voi koskaan luopua toiminnasta täysin. Niin kauan kuin sinulla on läppäri ja rooli tiimissä, sinun täytyy toimia. Mutta se, joka ei ole kiintynyt toimintansa hedelmiin, on TODELLINEN LUOPUJA (Tyagi)."*

**Viisi tekijää jokaisen commitin takana**

Krishna paljasti, että yksikään kehittäjä ei ole yksin vastuussa järjestelmän toiminnasta tai kaatumisesta:

**Krishna:**

*"Oppineet sanovat, että minkä tahansa koodirivin tai arkkitehtuuripäätöksen toteutumiseen tarvitaan aina **viisi tekijää**:*

1.  **Alusta (Adhisthana):** Tietokone, muisti, laitteisto ja OS.

2.  **Toimija (Karta):** Kehittäjä / Kehittäjän tila.

3.  **Työkalut (Karana):** IDE, kääntäjä, CI/CD-putki ja frameworkit.

4.  **Eri toiminnot (Cesta):** Näppäimistön painallukset, verkkokutsut ja CPU-syklit.

5.  **Kohtalo / Arkkitehtoninen Laki (Daivam):** Asiat, joihin emme voi vaikuttaa (kuten sähkökatkot tai yleiset verkkohäiriöt).

*Tämän tietäen: Se, joka luulee että 'MINÄ YKSIN tein tämän hienon järjestelmän' tai 'MINUN SYYTÄNI on tämä katko', on sokea egolle! Hän ei näe näitä viittä tekijää."*

**Parempi oma velvollisuus epätäydellisesti**

Arjuna yrittää vielä kerran ojentaa päätöksen pois käsistään:

**Arjuna:**

*"Tekijä tuntee toteutuksen paremmin. Arkkitehti tuntee kokonaisuuden paremmin. Product owner tuntee tarpeen paremmin. Antakaamme jonkun heistä päättää."*

Krishna ei kiistä tätä. Jokainen heistä todella näkee osan, jota Arjuna ei näe. Mutta juuri siksi kenenkään ei pitäisi suorittaa kaikkien muiden velvollisuutta.

**Krishna:**

**"Parempi suorittaa oma velvollisuutensa (Svadharma) epätäydellisesti kuin toisen täydellisesti."**

Sama pätee järjestelmän sisällä:

- **Aggregate Root** suojelee invariantteja.

- **Application Service** orkestroi käyttötapauksen.

- **Saga** koordinoi pitkää prosessia.

- **Outbox** huolehtii luotettavasta välityksestä.

- **Projektio** vastaa lukukysymyksiin.

- **SQL** hakee tietoa tehokkaasti.

- **Domain-eventti** kertoo, mitä domainissa tapahtui.

Ongelma ei ole, etteivätkö nämä voisi teknisesti tehdä toistensa työtä. Projektio *voi* sisältää business-päätöksen. Saga *voi* muuttaa domain-tilaa. Controller *voi* validoida invariantin. Mapperi *voi* laskea hinnan. Aggregate Root *voi* koota raportin.

Ne voivat jopa tehdä sen täydellisesti.

**Silti ne tekevät toisen velvollisuutta.**

**Krishna:**

*"Arkkitehtoninen raja ei estä komponenttia tekemästä työtään. Se estää sitä tekemästä jonkun toisen työtä."*

Myös katselmoijalla on oma rajallinen dharmansa. Hän ei omista tekijän työtä, liiketoiminnan totuutta eikä koko järjestelmän tulevaisuutta. Hän omistaa vain oman rehellisen havaintonsa ja velvollisuuden tuoda se yhteiseen keskusteluun.

MR:n hyväksyminen ei tarkoita, että muutos on täydellinen. Hylkääminen ei tarkoita, että tekijä on epäonnistunut. Kysymyksen esittäminen ei tarkoita, että kysyjä tietää vastauksen.

Arjuna ei siis paina vielä *Approve* eikä *Reject*. Hän ei myöskään poista itseään revieweriksi. Hän kirjoittaa kommentin:

// Arjuna's PR Review Comment:

*"En vastusta näitä getter-metodeja siksi, että getter olisi itsessään väärin. En vielä ymmärrä, tarvitseeko mapperi vain rahan ulkoisen representaation vai olemmeko tekemässä `amount`- ja `currency`-kentistä yleisen API:n, jonka varaan myös laskenta alkaa rakentua. Voimmeko käydä yhden konkreettisen käyttötapauksen läpi ja sopia, missä rahan päätökset tehdään, ennen kuin hyväksymme muutoksen?"*

Se ei ratkaise sotaa. Se ei edes ratkaise merge requestia.

Mutta se palauttaa keskusteluun langan, näkymättömän työn ja kunkin oman velvollisuuden.

**Arjuna:** *"Ymmärränkö minä nyt domainin?"*

**Krishna:** *"Et. Mutta nyt tiedät, mitä kysyä."*

**Krishnan Lopullinen Kehotus ja Sanoma**

Sitten Krishna astui aivan Arjunan viereen, katsoi häntä silmiin ja lausui koko Bhagavad Gitan kuuluisimman loppusäkeen (*Charama Shloka*):

**Krishna:**

**"Sarva-dharman parityajya mam ekam sharanam vraja:**

**Hylkää kiintymys dogmaattisiin sääntöihin, turhiin framework-taisteluihin ja omaan täydellisyyteesi. Etsi turvaa domainin rehellisestä ymmärtämisestä.**

*Mikään yksittäinen malli ei ole minä, mutta jokainen totuudellinen malli ilmaisee jotakin minusta.*

*Minä vapautan sinut kaikista menneistä koodausvirheistä, huonoista commiteista ja teknisen velan syyllisyydestä. Älä murehdi (Ma shucah)!"*

**Arjunan Herääminen (Nasto Mohah)**

Taistelukentällä – ja koodieditorin ääressä – laskeutui täydellinen, syvä hiljaisuus. Epäilys oli tiessään. Pelko tuotannon kaatumisesta oli sulanut pois.

**Krishna:**

*"Oletko kuullut tämän opetuksen keskittyneellä mielellä, Arjuna? Onko tietämättömyydestä syntynyt hämmennyksesi haihtunut?"*

**Arjuna:**

*"Nasto mohah smritir labdha tvat-prasadan maya 'cyuta:*

**Hämmennykseni on kadonnut! Olen saanut takaisin muistini ja ymmärrykseni sinun armostasi, oi Muuttumaton!**

**Seison tässä täysin vakaana, ilman epäilystä. Minä teen niin kuin sinä käsket (Karisye vacanam tava)!**"\*

\[ ARJUNA TARTTUU NÄPPÄIMISTÖÖN \]

• Pelko kadonnut.

• Ego poistettu.

• Oma velvollisuus tunnistettu.

• Kommentti jätetty MR-katselmointiin.

• Decision: Request changes submitted.

• Attachment to outcome: none.

**Sanjaya päättää eepoksen**

Eepoksen lopussa Sokean Omistajan (Dhritarashtra) ministeri Sanjaya sulkee reaaliaikaisen yhteys-lokinsa syvällä kunnioituksella:

**Sanjaya:**

*"Näin minä kuulin tämän ihmeellisen ja karvat pystyyn nostattavan keskustelun Mestarillisen Arkkitehdin (Krishna) ja jaloimman Kehittäjän (Arjuna) välillä.*

**Missä ikinä on Krishna, Korkein Arkkitehti, ja missä ikinä on Arjuna, jousensa ja näppäimistönsä kohottanut Kehittäjä – siellä on varmasti KESTÄVÄ TYYNEYS, VOITTO, MAHTAVA SUORITUSKYKY JA TÄYDELLINEN RAUHA!**

*Tämä on minun lopullinen näkemykseni."*

**🕉️ BHAGAVAD GITAN LOKIT - VALMIS 🕉️**

Arjuna ei sulkenut läppäriään. Hän ei juossut karkuun. Hän kysyi oikean kysymyksen ja täytti oman dharmansa. Build oli vihreä. Tuotanto oli stabiili. Mieli oli vapaa.

Aum Shanti, Shanti, Shanti. 🚀✨

**GitLab:**

Merge request cannot be merged.  
Source branch is 37 commits behind target branch.

**Samsara.**
