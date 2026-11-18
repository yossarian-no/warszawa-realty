# 🏙️ Warszawa Realty — analiza rynku najmu mieszkań w Warszawie

Projekt analityczny badający, **od czego zależą ceny wynajmu mieszkań w Warszawie**: parametry lokalu, lokalizacja, otoczenie i różnice między dzielnicami.

> 🚧 **Status:** projekt w trakcie realizacji

---

## 🎯 Cel projektu

Celem jest odpowiedź na pytania, które zadaje sobie zarówno osoba szukająca mieszkania, jak i właściciel lub inwestor:
*ile powinno kosztować to mieszkanie, gdzie najem jest najbardziej opłacalny i co realnie podnosi cenę?*

---

## ❓ Pytania badawcze

### 1. Ceny w dzielnicach
- Jaka jest średnia i mediana ceny najmu oraz ceny za m² w poszczególnych dzielnicach?
- Które dzielnice są najdroższe, a które najtańsze, i jak duży jest rozrzut cen wewnątrz każdej z nich?
- Jak zmienia się cena wraz z odległością od centrum miasta?

### 2. Parametry mieszkania
- Jak powierzchnia i liczba pokoi wpływają na cenę? Czy małe mieszkania są droższe w przeliczeniu na m²?
- Czy piętro ma znaczenie (parter, ostatnie piętro, wysokie piętra w wieżowcach)?
- Jak na cenę wpływa wiek budynku, rodzaj zabudowy (blok, kamienica, apartamentowiec) i materiał?
- Ile „kosztuje” balkon, winda, miejsce parkingowe, ochrona czy komórka lokatorska?

### 3. Lokalizacja i otoczenie
- Czy bliskość metra podnosi cenę najmu i o ile?
- Jak na cenę wpływa odległość od szkół, przedszkoli, sklepów, restauracji, uczelni czy przychodni?
- Czy liczba punktów usługowych w okolicy (POI) przekłada się na wyższą cenę?

### 4. Model ceny i okazje
- Które czynniki najsilniej wyjaśniają cenę najmu?
- Jaką cenę „powinno” mieć dane mieszkanie i które oferty są **niedoszacowane** względem rynku?

### 5. Rynek w szerszym kontekście
- Jak zmieniały się ceny najmu z miesiąca na miesiąc w badanym okresie?
- Gdzie najem jest najbardziej opłacalny dla inwestora? *(stopa zwrotu z najmu = roczny czynsz / cena zakupu, porównanie ofert najmu i sprzedaży w dzielnicach)*
- Jak Warszawa wypada na tle innych dużych miast w Polsce?

---

## 📊 Dane

Główne źródło: [Apartment Prices in Poland](https://www.kaggle.com/datasets/krzysztofjamroz/apartment-prices-in-poland) (Kaggle)
- comiesięczne oferty najmu i sprzedaży mieszkań z 15 największych miast Polski (sierpień 2023 – czerwiec 2024),
- parametry mieszkań oraz odległości do punktów zainteresowania (OpenStreetMap),
- do analizy wybierane są oferty z Warszawy.

Dane dodatkowe:
- granice dzielnic i lokalizacje stacji metra — otwarte dane m.st. Warszawy (do przypisania dzielnic i liczenia odległości).

> Surowe dane nie są przechowywane w repozytorium — instrukcja pobrania znajduje się w sekcji „Jak uruchomić”.

---

## 🛠️ Technologie

| Obszar | Narzędzia |
|---|---|
| Przetwarzanie danych | Python, pandas, NumPy, GeoPandas |
| Baza danych / SQL | DuckDB (SQL: CTE, funkcje okna, agregacje) |
| Analiza i statystyka | SciPy, statsmodels |
| Modelowanie | scikit-learn (regresja liniowa, Random Forest) |
| Wizualizacja | Matplotlib, Seaborn, Power BI |

---

## 📁 Struktura projektu

```
warszawa-realty/
├── data/
│   ├── raw/          # surowe dane z Kaggle (nie w repo)
│   ├── external/     # dane dodatkowe: dzielnice, metro (nie w repo)
│   └── processed/    # dane po czyszczeniu (nie w repo)
├── notebooks/        # notatniki Jupyter: czyszczenie, EDA, model
├── src/              # skrypty Pythona: pobieranie, czyszczenie, ładowanie do bazy
├── sql/              # zapytania analityczne SQL
├── dashboard/        # plik dashboardu Power BI
├── images/           # wykresy i zrzuty ekranu do README
├── requirements.txt
└── README.md
```

---

## 🗺️ Plan prac

- [ ] Pobranie danych i wybór ofert z Warszawy
- [ ] Czyszczenie danych (duplikaty, braki, wartości odstające)
- [ ] Przypisanie dzielnic i obliczenie odległości do metra
- [ ] Załadowanie danych do DuckDB i analiza w SQL
- [ ] Eksploracyjna analiza danych (EDA) i testy statystyczne
- [ ] Model ceny najmu i wyszukiwanie niedoszacowanych ofert
- [ ] Dashboard w Power BI
- [ ] Podsumowanie wniosków

---

## 💡 Najważniejsze wnioski

*Sekcja zostanie uzupełniona po zakończeniu analizy.*

---

## ▶️ Jak uruchomić

```bash
git clone https://github.com/yossarian-no/warszawa-realty.git
cd warszawa-realty
python -m venv .venv
.venv\Scripts\activate        # Windows
pip install -r requirements.txt
```

Pobranie danych z Kaggle (wymaga pliku `kaggle.json` z kluczem API):

```bash
kaggle datasets download -d krzysztofjamroz/apartment-prices-in-poland -p data/raw --unzip
```

---

## 👤 Autor

**Vasil Kusmartsev** — [GitHub](https://github.com/yossarian-no)
