# Lokalizator opon i felg

Ta paczka zawiera pliki strony do GitHub Pages oraz aktualizację Google Apps Script dla modułu felg.

## 1. Pliki do repozytorium GitHub

W głównym katalogu repozytorium umieść:

- `index.html`
- `manifest.webmanifest`
- `favicon.png`
- `icon-192.png`
- `icon-512.png`
- `icon-512-maskable.png`

Następnie włącz GitHub Pages w ustawieniach repozytorium: **Settings → Pages → Deploy from a branch → main → /(root)**.

## 2. Google Apps Script

Plik `apps-script/Code.gs` zawiera zaktualizowany kod serwera. Nie jest on uruchamiany przez GitHub Pages.

1. Zrób kopię obecnego `Code.gs` oraz arkusza Google.
2. Otwórz TEN SAM projekt Google Apps Script, który jest połączony z używanym arkuszem.
3. Zastąp zawartość pliku `Code.gs` zawartością z `apps-script/Code.gs` i zapisz.
4. Pozostaw pozostałe pliki projektu, w szczególności `kolor.gs`, bez zmian.
5. Wybierz **Wdróż → Zarządzaj wdrożeniami → Edytuj** przy istniejącym wdrożeniu, wybierz **Nowa wersja** i wdróż. Zachowaj dotychczasowy adres `/exec`.

Adres API jest zapisany w `index.html`. Jeśli wdrożenie Google Apps Script, z którego korzysta aplikacja, jest inne niż dotychczasowe, trzeba świadomie podmienić `API_URL` w `index.html` na adres właściwego wdrożenia.

## 3. Zmiany w module felg

- Numer OEM można wpisać jako maksymalnie 7 cyfr.
- Po wyjściu z pola numeru OEM aplikacja sprawdza kartę `Katalog` i uzupełnia puste pola Styling, Rozmiar i Uwagi, jeśli znajdzie numer.
- Gdy numeru nie ma w katalogu, dane można wpisać ręcznie.
- Styling, Rozmiar i Uwagi są opcjonalne.
- Ilość i Lokalizacja pozostają wymagane.
- Zachowane są dotychczasowe pola ID Kompletu, tabela listy felg, edycja, usuwanie i pozostałe funkcje aplikacji.
- Moduł opon nie został zmieniony.

## 4. Ważne

Samo używanie tego samego adresu e-mail Google nie gwarantuje połączenia z właściwym skryptem. Liczy się dokładny adres wdrożenia Apps Script. Paczka zachowuje adres API z przekazanego pliku `index.html`.

Nie usuwaj ani nie zmieniaj zakładek w arkuszu Google. Kod korzysta z istniejących kart `Arkusz1`, `Felgi` oraz `Katalog`.
