# Chat avec plusieurs pdfs
Cette application permet de discuter avec plusieurs documents PDF en utilisant un modèle de traitement du langage naturel pour répondre aux questions de manière contextuelle en fonction du contenu des documents PDF chargés.
![MultiPDF Chat App Diagram](./docs/PDF-LangChain.jpg)
## Fonctionnement de l'Algorithme
### Chargement des Documents PDF
L'application commence par charger plusieurs documents PDF. Vous pouvez télécharger ces PDF en utilisant l'interface utilisateur.

### Extraction du Texte
Une fois les PDF chargés, l'application extrait le contenu textuel de ces documents. Elle parcourt chaque page de chaque PDF pour obtenir le texte.

### Découpage du Texte en Chunks
Le texte extrait est ensuite divisé en "chunks" (morceaux) plus petits, ce qui permet de le traiter de manière efficace. Les chunks sont des portions de texte d'une certaine longueur.

### Création d'un Vecteur Store
L'application utilise un modèle de traitement du langage naturel pour générer des représentations vectorielles (embeddings) de ces chunks de texte. Ces embeddings sont des représentations numériques du contenu textuel.

### Recherche de Similarité
Lorsque vous posez une question, l'application compare votre question avec les chunks de texte extraits et identifie les morceaux de texte les plus similaires sur le plan sémantique.

### Génération de Réponses
Les morceaux de texte sélectionnés sont ensuite transmis à un modèle de traitement du langage naturel (comme GPT-3 ou un autre modèle pré-entraîné) pour générer une réponse basée sur le contenu pertinent des PDFs.

### Interaction Utilisateur
L'interface utilisateur vous permet de poser des questions en langage naturel concernant les documents PDF chargés. Les réponses sont affichées dans l'interface utilisateur.

### Dépendances et Installation
Pour utiliser cette application, vous devez cloner le référentiel, installer les dépendances requises et obtenir une clé API d'OpenAI. Cette clé API doit être ajoutée à un fichier .env dans le répertoire du projet.

### Utilisation
Lorsque tout est configuré, vous pouvez exécuter l'application en utilisant la commande streamlit run app.py. L'application s'ouvrira dans votre navigateur par défaut, où vous pourrez charger vos documents PDF et poser des questions en langage naturel.

## Bibliothèques Utilisées
- Streamlit: Streamlit est une bibliothèque Python utilisée pour créer des applications web interactives avec une syntaxe simple. Dans ce projet, Streamlit est utilisé pour créer l'interface utilisateur et gérer l'interaction avec l'utilisateur.

- PyPDF2: PyPDF2 est une bibliothèque Python qui permet de manipuler des fichiers PDF. Elle est utilisée ici pour extraire le texte des documents PDF chargés.

- dotenv: La bibliothèque dotenv permet de charger des variables d'environnement depuis un fichier .env. Dans ce projet, elle est utilisée pour stocker la clé API d'OpenAI de manière sécurisée.

- langchain: Il s'agit d'une bibliothèque personnalisée qui comprend plusieurs modules importants pour le traitement du langage naturel, notamment :

- CharacterTextSplitter: Un module pour diviser le texte en "chunks" (morceaux) plus petits.
- OpenAIEmbeddings et HuggingFaceInstructEmbeddings: Ces modules permettent de générer des embeddings (représentations numériques) à partir du texte en utilisant des modèles de langage naturel tels qu'OpenAI GPT-3 ou Hugging Face Transformers.
- FAISS: Cette bibliothèque est utilisée pour créer un "vector store" à partir des embeddings, ce qui permet une recherche efficace de similarité.
- ConversationBufferMemory: Un module pour stocker l'historique des conversations.
- ConversationalRetrievalChain: Ce module gère le processus de recherche de réponses en utilisant les embeddings et l'historique des conversations.
- htmlTemplates: Il s'agit d'un ensemble de modèles HTML utilisés pour afficher les messages de l'interface utilisateur.

- HuggingFaceHub: Cette bibliothèque est utilisée pour accéder à des modèles de langage naturel pré-entraînés disponibles sur le hub de Hugging Face.