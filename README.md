# LLM: Financial Analyst of Companies Annual Reports

## Freelance Consulting Project

## Introduction 

Companies annual reports are a cornerstone in the landscape of investment decision-making, particularly when it comes to investing in publicly traded companies. These documents serve as a comprehensive mirror, reflecting a company's financial health, business operations, and strategic direction. In essence, they provide a holistic view of a company's performance and potential, making them an indispensable tool for evaluating the viability and attractiveness of an investment.

However, the manual analysis of these annual reports is a time-consuming and labor-intensive process. The sheer volume of data and complexity of information contained within these documents can pose a significant challenge, requiring extensive effort and expertise to decipher and interpret effectively.

The goal of this work is to leverage the LLM capabilities to create an AI assistant, tailored specifically for financial analysts and traders, which can adeptly navigate and interpret the complexities of annual reports. This innovative tool is designed to answer queries based on the given report in the most challenging yet used format : PDFs.


## Architecture

<p align="center">
  <img src="https://github.com/saadelmoutaouakil/LLM-Financial-Analyst/blob/main/Architecture.png" />
</p>

The execution flow of this project is divided into two main stages:

### Indexing Stage
The Indexing Stage comprises two major steps:
1. **Preprocessing the files:** This involves preparing the files for further processing.
2. **Producing the Embedding Vector Database:** This step involves creating a database of embedding vectors which are crucial for the querying process.

### Querying Stage
The Querying Stage encompasses the entire process from the user's query input to the generation of the response by the LLM model.

## Tools Used in the Project

### PDF to HTML Conversion
- **Tool:** Adobe Acrobat Reader Pro
- *Note:* The Adobe API does not support conversion to HTML format. As a result, the Python libraries tested do not maintain the original structure of the PDF, especially in the context of converting PDF tables to HTML tables. Instead, these open-source libraries usually create HTML output by interpreting the PDF tables as images. This approach requires the reconstruction of HTML tables using an additional layer of Optical Character Recognition (OCR).

### Models and Technologies
- **LLM Model:** OpenAI GPT 3.5 Turbo
- **Embedding Model:** OpenAI Ada 002
- **Retrieval-Augmented Generation (RAG):** LLamaIndex


## Example Use-Case on Apple Annual Report of 2023 (10-K SEC filing)

The first step, is to check that our LLM is able to answer queries for which answers are written in plain text in the PDF. 

For example: How many shares did the company repurchase in 2023? And for what cost? 

**The answer is provided in the PDF in page 47, Note 10:**

<p align="center">
  <img src="https://github.com/saadelmoutaouakil/LLM-Financial-Analyst/blob/main/Query%201%20PDF.png" />
</p>

**The LLM answers correctly by:** "The company has repurchased 471 million shares of its common stock in 2023. The cost of these repurchased shares is $76.6 billion, excluding excise tax."

<p align="center">
  <img src="https://github.com/saadelmoutaouakil/LLM-Financial-Analyst/blob/main/Query%201%20LLM_Answer.png" />
</p>

The second step, is to check that our LLM is able to answer simple and direct queries for which answers are only stated in a Table in the PDF.
For example : "What was the research and development percentage of total net sales in 2023? "

**The asnwer is provided in the PDF in page 26, under the Operating Expenses Table**:

<p align="center">
  <img src="https://github.com/saadelmoutaouakil/LLM-Financial-Analyst/blob/main/Query%202%20PDF.png" />
</p>

**The LLM answers correctly by:** "Research and development percentage of total net sales in 2023 is 8%."

<p align="center">
  <img src="https://github.com/saadelmoutaouakil/LLM-Financial-Analyst/blob/main/Query%202%20LLM_Answer.png" />
</p>

The last step, is to check that our LLM is able to answer complex queries for which answers are only stated in a Table in the PDF.
For example : "How much was the Total gross margin in 2023 vs 2022? How much comes from Products, and how much from services?
I want the answers in numbers and in percentage if available. Give me the result with its units (Millions, thousands, etc)."

**The asnwer is provided in the PDF in page 26, under the Gross Margin Table, with the units set to Millions:**

<p align="center">
  <img src="https://github.com/saadelmoutaouakil/LLM-Financial-Analyst/blob/main/Query%203%20PDF.png" />
</p>

**The LLM answers correctly by:** "Total gross margin in 2023 was $169,148 million, and in 2022 it was $170,782 million. From the total gross margin in 2023, $108,803 million came from Products and $60,345 million came from Services. The gross margin percentage for Products was 36.5%, and for Services, it was 70.8%."


<p align="center">
  <img src="https://github.com/saadelmoutaouakil/LLM-Financial-Analyst/blob/main/Query%203%20LLM_Answer.png" />
</p>

