# Predykcja sukcesu finansowego filmów z wykorzystaniem NLP
*(Use of NLP in movie boxoffice prediction)*

Projekt łączy informatykę, ekonometrię i analizę języka naturalnego (NLP) w celu przewidywania komercyjnego sukcesu produkcji filmowych. Projekt ten powstał w ramach pracy licencjackiej.

Głównym celem tego badania było sprawdzenie, czy dodanie wektorowych reprezentacji tekstu (opisy fabuły i słowa kluczowe) do modeli opartych na klasycznych danych liczbowych (np. budżet, popularność) realnie poprawia trafność prognoz finansowych w branży kinowej.

---

## Główne założenia i metodyka

* **Zbiór danych:** Przeanalizowano około 3.2 tyś. amerykańskich produkcji z bazy The Movie Database (TMDB) z lat 2010–2023.
* **NLP i Embeddings:** Aby algorytmy mogły zrozumieć kontekst fabuły, wykorzystano model `Qwen3-Embedding-0.6B`, który przekształcił krótkie opisy (*overview*) oraz słowa kluczowe (*keywords*) w wielowymiarowe wektory właściwościowe. Wymiarowość zredukowano przy użyciu algorytmów UMAP oraz PCA (do 200 komponentów zachowujących 85% wariancji).
* **Uczenie Maszynowe:** Wykorzystano modele bazowe (Regresja Liniowa, Random Forest) oraz zaawansowane algorytmy oparte na drzewach decyzyjnych (`XGBoost`, `LightGBM`). Modele testowano w zadaniach regresji oraz klasyfikacji (przypisanie filmu do klas: *Flop, Average, Hit, Blockbuster*).
* **Wyjaśnialność:** Za pomocą analizy SHAP zidentyfikowano czynniki mające największy wpływ na rynkowy sukces lub porażkę filmu.

<img width="1354" height="316" alt="image" src="https://github.com/user-attachments/assets/a5fac1bd-ba56-4f62-8103-6ab2c195eac9" />

---

## Kluczowe wyniki

Eksperyment jednoznacznie potwierdził, że włączenie cech tekstowych do analizy drastycznie poprawia skuteczność predykcji. 

Najlepszy klasyfikator, **XGBoost Classifier zasilony wektorami właściwościowymi**, osiągnął:
* **Dokładność (Accuracy):** 81,05%
* **F1-score:** 0,8193

<img width="580" height="455" alt="s-blob-v1-IMAGE-_QAwugraFAk" src="https://github.com/user-attachments/assets/d902343c-deae-46cb-b5e1-0e5e6455a36a" />

Stanowi to niemal **dwukrotną poprawę** względem tego samego modelu bazującego wyłącznie na standardowych, liczbowych metadanych (który osiągnął dokładność na poziomie zaledwie 41,03%). Analiza SHAP dodatkowo potwierdziła, że to właśnie komponenty tekstowe stanowiły najistotniejsze cechy predykcyjne w modelu.

---

## Wykorzystane technologie i narzędzia

* **Język:** Python
* **Obróbka i eksploracja danych:** `pandas`, `scikit-learn`
* **Modele predykcyjne:** `XGBoost`, `LightGBM`
* **NLP & Redukcja wymiarowości:** `Hugging Face` (Qwen3-Embedding-0.6B), `UMAP`, `PCA`
* **Interpretowalność modeli:** `SHAP`

---

## Autor

**Szymon Płaziak** *Uniwersytet Ekonomiczny w Poznaniu* *Kierunek: Informatyka i ekonometria*
