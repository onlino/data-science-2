# TODOs
This is a list of TODOs for the next years, mostly for internal purposes of the teachers.

Karel:

Ondra:

- Pripravit cviceni na GAN
- HW2 specifikovat že je to fine-tuning classification modelu; submission ma obsahovat model
- https://masters.donntu.ru/2012/fknt/umiarov/library/lecun.pdf

HW 1
- do zadání rozepsat, co má úloha všechno mít
  - data exploration
  - predictor definition
  - variable encoding
  - hyperparameter selection
  - model score validation
  - SHAP value interpretation

Next year
(Karel) 
- TODO random forest, doplnit nazev promenne do ktere ulozit model do zadani
- opravit popis u Random Forest sekce (The task is to predict if tomorrow is going to rain) - neni pravda predikujeme teplotu
- random forest paramaters add random_state
- XGBoost better code for permutation importance

```python
res = []
for pred in tqdm(cols_pred):
    pi, iqr95, iqr05 = permutation_importance(
        dt=data[test_mask][cols_pred + [col_target]], 
        predictor=pred,
        target=col_target,
        model=booster,
        n_iters=10
    )
    res.append((pred, pi, iqr05, iqr95))
res = pd.DataFrame(res, columns = ['predictor', 'permutation_importance', 'iqr05', 'iqr95'])
res = res.sort_values('permutation_importance', ascending=False).reset_index(drop=True)
res
```

- prozkoumat categorical variables support v XGBoost
- xgboost plot marginal dependence vsechny variables
- hyperparam add optuna
- make sure to be aligned with: V podmínkách pro zakončení předmětu je třeba smazat prohlášení typu "Podmínky udělení zápočtu neumožňují opravné termíny" či "Zápočet nelze opakovat" a místo toho jednoznačně uvést, které součásti zápočtu lze opravovat a jakým způsobem, tak aby bylo dodrženo právo studenta na minimálně dvě opravy jednotlivých částí. Pokud se k zápočtu např. vyžaduje úspěšné vyřešení šesti úkolů z osmi zadaných, je tím už právo na dvě opravy naplněno, protože student může libovolné dva úkoly vyřešit špatně nebo nevyřešit vůbec, a zápočet i tak dostane. V případě bodovacích systémů, kdy se nasčítávají body za různé úkoly či testy, stačí dát možnost dva z oněch bodovaných výstupů vylepšit či nahradit, případně získat dodatečné body za nějakou práci navíc. V případě, že vyučující si s formulací podmínek zápočtu neví rady, jsem ochoten poradit či pomoci."

