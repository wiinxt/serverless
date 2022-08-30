# Comptabilité mon-entreprise.fr

Introduction : https://plaintextaccounting.org

### Exemples de rapport

Compte de résultat (somme des recettes et dépenses) :

```
$ hledger -B is
```

La vue année par année avec les prévisions (montant budgeté mais pas encore de bon de commande) :

```
$ hledger is -Y -B --forecast --depth 2
```

Balance des tiers (a qui doit-on de l'argent ? qui nous doit de l'argent ?) :

```
$ hledger bal tiers
```

La liste des dépenses :

```
$ hledger reg charges -B
```

Pour le suivi de l'exécution par rapport au budget prévisionnel :

```
$ hledger bal charges -B -p 2020 --budget
```

Temps passé par développeur par mois :

```
$ hledger bal dév -M
```

### Installation

```
sudo apt install hledger hledger-ui hledger-web
```

Pour les autres plateformes : https://hledger.org/download.html

Pour éviter de préciser le paramètre `-f me.journal` à chaque commande, on peut utiliser la variable
d'environnement `$LEDGER_FILE`, qui est définie dans le fichier `.envrc`. Pour la charger automatiquement :

```
$ sudo apt install direnv
```

Puis modifier le `bashrc` ou équivalent https://direnv.net/docs/hook.html

Puis dans le répertoire courant

```
$ direnv allow
```

### Rappel de principes comptables

- On utilise les comptes `financement` et `charges` pour enregistrer les recettes et les dépenses.
- Si un paiement n'est pas fait immédiatement, on impute un compte de `tiers`.
