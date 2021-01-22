# JPK-VDEK
Prosty program do wysyłania JPK VAT z deklaracją (https://jpk-vdek.herokuapp.com/).

## Wstęp
Od 1 października 2020 r. wszyscy podatnicy zarejestrowani jako czynni podatnicy
VAT muszą obowiązkowo składać JPK_VAT z Deklaracją (JPK-VDEK).
(źródło: https://www.podatki.gov.pl/jednolity-plik-kontrolny/jpk-vat-z-deklaracja/jpk-vat-z-deklaracja-info/)

Dokument elektroniczny JPK-VDEK składa się z ewidencji VAT
(zakupy i sprzedaż, które wynikają z ewidencji VAT przedsiębiorcy za dany okres)
oraz z deklaracji VAT.

Niestety, przesłanie takiego dokumentu nie jest proste. Wymaga on zgodności ze
schematami XSD, odpowiedniej kompresji danych i ich właściwego zaszyfrowania.
(źródło: https://www.podatki.gov.pl/jednolity-plik-kontrolny/jpk-vat-z-deklaracja/pliki-do-pobrania-jpk-vat-z-deklaracja/#jpk-vat)

W tym celu powstał ten program.

## Licencja

Program jest na warunkach Powszechnej Licencji Publicznej GNU wersja 3 lub nowsza (http://www.gnu.org/licenses/gpl.html).

## Wymagania

Do poprawnego działania programu wymagane jest środowisko Java (Java Runtime Environment, JRE)
w wersji 8 lub nowszej.

## Instalacja

Program ma dwie wersje:

- DeskApp - Program graficzny do interaktywnego tworzenia ewidencji i deklaracji VAT, utrzymywania listy dostawców i kontrahentów, zarządzania wersjami roboczymi, podpowiedziami podczas wypełniania treścią, i wysyłania dokumentów do Ministerstwa Finansów.

- ConsoleApp - Program z wiersza poleceń do wysyłania gotowych dokumentów do Ministerstwa Finansów.

### DeskApp

Pobierz program `deskapp.zip` z https://github.com/piotrkot/jpk-vdek/releases.

Rozpakuj plik `deskapp.zip` do katalogu `deskapp`.

#### Windows

Uruchom plik `jpk-vdek.bat` z katalogu `deskapp`.

#### Linux

Uruchom plik `jpk-vdek.sh` z katalogu `deskapp`.

### Środowisko testowe

Ministerstwo Finansów udostępniło środowisko testowe do wysyłania JPK-VDEK. Aby program połączył się ze środowiskiem testowym należy:

- dla systemu Windows:

W pliku `jpk-vdek.bat` zamienić

`set ENV=PROD`

na

`set ENV=TEST`

- dla systemu Linux:

w pliku `jpk-vdek.sh` zamienić

`export ENV=PROD`

na

`export ENV=TEST`

W tym środowisku dane podatnika mogą być dowolne, jednak jedynie NIP parzysty pozwoli z powodzeniem zakończyć wysyłkę. Dla nieparzystej wartości NIP pojawi się błąd.


### Zrzuty ekranu

![](../master/screens/Ekran%20wstępny%20-%20wprowadzanie%20danych%20podatnika.png?raw=true "Ekran wstępny - wprowadzanie danych podatnika/użytkownika")
![](../master/screens/Ekran%20główny%20-%20autouzupełnienie%20urzędu.png?raw=true "Ekran główny - autouzupełnienie urzędu")
![](../master/screens/Ekran%20główny%20-%20sprzedaż%20-%20podpowiedź%20kontrahenta.png?raw=true "Ekran główny - sprzedaż - podpowiedź kontrahenta")
![](../master/screens/Ekran%20główny%20-%20zakup%20-%20podpowiedź%20dostawcy.png?raw=true "Ekran główny - zakup - podpowiedź dostawcy")
![](../master/screens/Ekran%20główny%20-%20wysyłka%20-%20progres.png?raw=true "Ekran główny - wysyłka - progres")
![](../master/screens/Ekran%20główny%20-%20wysyłka%20-%20sukces.png?raw=true "Ekran główny - wysyłka - sukces")

## ConsoleApp

Pobierz program `consoleapp.zip` z https://github.com/piotrkot/jpk-vdek/releases.

Rozpakuj plik `consoleapp.zip` do katalogu `consoleapp`.

#### Windows

Uruchom plik `jpk-vdek-cmd.bat` z katalogu `consoleapp`.

#### Linux

Uruchom plik `jpk-vdek-cmd.sh` z katalogu `consoleapp`.

### Opcje użycia

- `--help` - Wyświetlenie komunikatu pomocy.
- `--test` - Użycie środowiska testowego Ministerstwa Finansów. Bez tej opcji użyte zostanie środowisko produkcyjne. W środowisku testowym wysłanie dokumentu zakończy się sukcesem jedynie dla parzystych wartości NIP.
- `--out=<katalog>` - Wskazanie katalogu do zapisu UPO. Bez tej opcji użyty zostanie katalog bieżący.
- `--doc=<dokument>` - Wskazanie dokumentu JPK z Deklaracją do wysłania.
- `--auth=<kwota>` - Wskazanie kwoty przychodu wykazanej w zeznaniu za rok przedostatni (np. dnia 25.04.2020 będzie to rok 2018).

### Przykład

`$> jpk-vdek-cmd.sh --test --out=/tmp --doc=jpk.xml --auth=10,50`

## Kontakt

jpk.vdek@gmail.com

