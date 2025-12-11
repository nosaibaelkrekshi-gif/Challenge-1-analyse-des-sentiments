#  Système d'Analyse de Sentiments Multi-niveaux

**Projet Master 1 - Analyse de Sentiments pour Avis Clients**

---

##  Table des Matières
* [À Propos](#-à-propos)
* [Fonctionnalités](#-fonctionnalités)
* [Installation](#-installation)
* [Utilisation](#-utilisation)
* [Architecture](#️-architecture)
* [Résultats](#-résultats)
* [Technologies](#-technologies)
* [Auteur](#-auteur)

---

##  À Propos

Ce projet implémente un système complet d'analyse de sentiments capable d'analyser des avis clients à plusieurs niveaux de granularité. Développé pour une entreprise d'e-commerce, il utilise des techniques avancées de **Traitement du Langage Naturel (NLP) en français** basées sur les modèles **Transformer** (Hugging Face) et la librairie **spaCy** pour garantir une haute précision.

**Dépôt GitHub du Projet :** `https://github.com/nosaibaelkrekshi-gif/Challenge-1-analyse-des-sentiments.git`

### Objectifs du Projet
- Analyse multi-niveaux : Document, Phrase, Aspect
- Analyse multi-types : Polarité (avec comparaison), Aspects, Émotions
- Utilisation de modèles Deep Learning (`transformers`) optimisés pour le français
- Visualisations professionnelles (Dashboard)
- Tests unitaires (obligatoires) et Export de données (JSON, CSV)

---

##  Fonctionnalités

###  Challenge 1 : Analyse Multi-niveaux
| Niveau | Fonctionnalité | Outils |
| :--- | :--- | :--- |
| **Document** | Classification en 5 catégories (Très Positif → Très Négatif) et Statistiques globales. | HF BERT |
| **Phrase** | Découpage (via spaCy) et analyse phrase par phrase. Détection des **contradictions internes**. | spaCy, HF BERT |
| **Aspect** | Identification d'aspects clés (Produit, Prix, Service, Livraison) et sentiment spécifique par aspect. | spaCy (mots-clés contextuels) |

###  Challenge 2 : Analyse Multi-types
| Type | Implémentation | Justification Technique |
| :--- | :--- | :--- |
| **Analyse de Polarité** | **3 méthodes comparées :** **HF BERT** (principal), VADER, TextBlob. Calcul de la **cohérence** entre les méthodes pour évaluer la robustesse. | HF BERT est utilisé comme méthode principale pour sa robustesse en français. |
| **Détection d'Émotions** | Modèle Deep Learning (HF) pour détecter 6 émotions (Joie, Colère, Tristesse, etc.). L'intensité émotionnelle est calculée pour identifier les avis **"émotionnellement chargés"**. | Modèle RoBERTa/DistilBERT optimisé pour la classification fine. |

---

##  Installation

### Prérequis
* Python 3.8 ou supérieur
* pip

### Installation des Dépendances
```bash
# Cloner le repository
git clone [https://github.com/nosaibaelkrekshi-gif/Challenge-1-analyse-des-sentiments.git](https://github.com/nosaibaelkrekshi-gif/Challenge-1-analyse-des-sentiments.git)
cd Challenge-1-analyse-des-sentiments

# Créer un environnement virtuel (recommandé)
python -m venv venv
source venv/bin/activate  # Sur Windows: venv\Scripts\activate

# Installer les dépendances principales (scikit-learn retiré)
pip install pandas numpy matplotlib seaborn transformers spacy nltk textblob

# Télécharger les modèles linguistiques nécessaires
python -m spacy download fr_core_news_sm
python -m nltk.downloader vader_lexicon punkt


#### Utilisation

Exécution Basique
Le script analyse_sentiments_challenges.py contient les données d'entrée par défaut et exécute automatiquement les tests unitaires avant de lancer l'analyse complète.

Bash
    'python analyse_sentiments_challenges.py'


#### Sorties Générées
Le programme génère automatiquement :

- analyse_sentiments_dashboard.png - Visualisations
- resultats_analyse_sentiments_complet.json - Données complètes et détaillées
- resultats_analyse_sentiments.csv - Tableau synthétique exportable


#### rchitecture
L'architecture est centrée autour de la classe AnalyseurSentimentsComplet qui encapsule la logique métier et les méthodes de reporting.

Classe Principale

class AnalyseurSentimentsComplet:
    """
    Orchestre l'analyse de sentiments multi-niveaux et multi-types.
    """
    
    # ... Fonctions d'analyse (document, phrase, aspect, polarité, émotion)
    
    def analyser_tous_avis(avis_liste)
    
    # Reporting
    def generer_resume_global()
    def generer_visualisations()
    def exporter_resultats()


##### Résultats
L'exécution produit un tableau de bord visuel ainsi qu'une synthèse console des scores moyens et des aspects les plus critiques.

Dashboard Visuel
- Le dashboard (fichier analyse_sentiments_dashboard.png) synthétise :
- La distribution globale des sentiments.
- La comparaison des scores moyens des trois méthodes de polarité (HF BERT vs VADER vs TextBlob).
- Une Heatmap des scores de sentiment par aspect (Produit, Prix, Service, Livraison).
- L'intensité émotionnelle moyenne détectée.

### Technologies

- Python Langage principal
- transformers Analyse de Polarité et Émotions Modèles Deep Learning (BERT, RoBERTa) pour une gestion contextuelle du français.
- spaCySegmentation et Extraction d'AspectsModèle fr_core_news_sm pour une segmentation précise en phrases et extraction de contexte.
- NLTK/VADERAnalyse de Polarité secondaireUtilisé pour la comparaison multi-méthodes.
- Pandas, NumPy Manipulation de données et calculs statistiques
- Matplotlib/SeabornVisualisations et Reporting


Extensions Futures
[ ] Interface web avec Streamlit ou FastAPI.
[ ] Modélisation ABSA (Aspect-Based Sentiment Analysis) basée sur l'arbre de dépendance syntaxique (plus avancé que l'approche par mots-clés).
[ ] Détection de sarcasme/ironie.

####  Auteur
	Nosaiba Elkrekshi
	Master 1 - Nexa  Data IA * GitHub : @NosaibaElkrekshi-gif