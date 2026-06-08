# OpenAI Adapter File Processing with Oracle Integration Cloud

This repository contains a sample Oracle Integration Cloud (OIC) package demonstrating how to use the OpenAI Adapter for processing images, PDFs, and Word documents.

The solution uses:

- Upload File Operation
- Responses Operation
- OpenAI File IDs
- Structured JSON Extraction

This repository accompanies my Medium article:

Beyond Chat: Processing Images, PDFs, and Documents with the OpenAI Adapter in Oracle Integration Cloud
Blog Link: https://medium.com/@sarfarazMerchant/beyond-chat-processing-images-pdfs-and-documents-with-the-openai-adapter-in-oracle-integration-86253d02f84b

## Architecture

<img width="1024" height="559" alt="image" src="https://github.com/user-attachments/assets/bad9f50f-7232-478b-9300-67816a2b29b9" />


## Included Use Cases

### Use Case 1 - Restaurant Invoice Extraction

Input:
- JPG/PNG invoice image

Output:
- Invoice Number
- Date
- Line Items
- Tax
- Total Amount

### Use Case 2 - Persian / Arabic Document Processing

Input:
- PDF document

Output:
- Page-wise JSON
- Title extraction
- Paragraph preservation
- Original language retention

## Prerequisites

- Oracle Integration Cloud
- OpenAI Adapter
- OpenAI API Key
- Access to OpenAI Models

## Importing the Package

1. Download the .car file from this repository.

2. Login to Oracle Integration Cloud.

3. Navigate to:

   Home → Projects

4. Click Import Project.

5. Upload the provided .car file.

6. Review imported integrations.

7. Configure the OpenAI Connection using your API Key.

8. Activate all integrations.

## Running Use Case 1 - Invoice Processing

Step 1:
Upload an invoice image using the Upload File integration.
Purpose must be "vision" for images and "user_data" for Files.

Step 2:
Capture the returned File ID.

Step 3:
Invoke the Process File integration.

Parameters:

FileType=(input_image for image and input_file for any files)

FileId=<Returned File ID>

instruction=Extract invoice details and return valid JSON ( instruction as per you requiremt)

Step 4:
Review the structured JSON response.

## Running Use Case 2 - PDF Processing

Step 1:
Upload the PDF document using the Upload File integration.
Purpose must be "vision" for images and "user_data" for Files.

Step 2:
Capture the returned File ID.

Step 3:
Invoke the Process File integration.

Parameters:

FileType=input_file

FileId=<Returned File ID>

instruction=Extract page-wise content and return valid JSON

Step 4:
Review the JSON output.

## Lessons Learned

Use clean file names — avoid spaces and special characters when uploading files.

Upload once, reuse many times — leverage the returned File ID instead of sending file content repeatedly.

Parameterize your integration — File ID, File Type, and Instructions make the solution highly reusable.

Prompt engineering matters — clear instructions significantly improve extraction quality and consistency.

Expect an additional parsing step — JSON responses are returned inside the Result field.

One integration can support multiple document types — images, PDFs, and Word documents can be processed using the same pattern.

The OpenAI Adapter is more than chat — it can extract, understand, and structure information from documents and images.

## Disclaimer

This repository is intended for learning and demonstration purposes.

Users must provide their own OpenAI API key.

No customer data or credentials are included.
