# Serviços Cloud de Inteligência Artificial com Azure

Curso de **Serviços Cloud de Inteligência Artificial na Azure**, com foco na construção de uma solução de mineração de conhecimento baseada no **Azure AI Search**. A solução permite extrair, enriquecer e consultar dados de forma inteligente a partir de documentos armazenados na nuvem.

---

## Objetivo

Criar um pipeline completo que:

- Indexa documentos no Azure Blob Storage
- Aplica habilidades cognitivas (AI Skills)
- Envia os dados para um índice pesquisável
- Armazena os resultados enriquecidos no Knowledge Store
- Permite consultas com filtros e análise inteligente

---

## Etapas

### 1. Criação de Recursos

Foram criados os seguintes recursos na Azure:

- **Azure AI Search**: responsável por indexar e permitir consultas inteligentes.
- **Azure AI Services**: utilizado para aplicar habilidades cognitivas (OCR, sentimentos, etc.).
- **Azure Blob Storage**: para armazenar os arquivos de entrada (documentos .txt, imagens, etc.).

> Obs: Os recursos devem estar localizados na mesma região.

---

### 2. Upload dos Documentos

- Criação de um container chamado `coffee-reviews` no Blob Storage.
- Upload de arquivos com avaliações de clientes, extraídos de um pacote compactado.

---

### 3. Indexação e Enriquecimento

Através do assistente **Import data**, foram realizadas as seguintes ações:

- **Conexão com o Blob Storage**
- **Criação do índice de busca**
- **Aplicação de habilidades cognitivas (skillset)**:
  - OCR e união de texto em campo único
  - Extração de localizações, frases-chave, sentimentos
  - Geração de tags e legendas para imagens

Os dados enriquecidos foram armazenados no **Knowledge Store** para análises posteriores.

---

### 4. Configuração do Indexador

O **indexador** foi configurado para executar o pipeline de processamento automaticamente.

- Nome do índice: `coffee-index`
- Nome do indexador: `coffee-indexer`
- Codificação de chaves em Base-64 ativada

O indexador extrai conteúdo, executa os skills de IA e popula o índice de busca.

---

### 5. Consulta no Search Explorer

Consultas no índice foram realizadas com o **Search Explorer**, usando JSON para validar e filtrar dados:

Consulta geral:
```json
{
  "search": "*",
  "count": true
}
```
Consulta por localização:

```json
{
  "search": "locations:'Chicago'",
  "count": true
}
```
Consulta por sentimento negativo:
```
{
  "search": "sentiment:'negative'",
  "count": true
}
```
## Conclusão
Este aprendizado demonstrou como utilizar serviços da Azure para construir uma solução de Inteligência Artificial aplicada à busca e análise de documentos. As etapas de ingestão, enriquecimento e consulta tornam essa solução poderosa para casos de uso em grandes volumes de dados textuais e multimídia.
