# Curriculum Engine: Automation Blueprint

**Entity:** Just 1 Team LLC (DBA SEL Academy)  
**Process:** Curriculum Module to Multi-Asset Product  
**Platform:** Zapier (or Make.com)  
**Status:** Ready for Deployment  

---

## 1. System Overview

The Curriculum Engine transforms a single piece of intellectual property (a completed curriculum module) into four distinct assets with zero additional human intervention. 

**The Math of Leverage:**
* **Current State:** 1 Input → Manual Slide Creation → Manual PDF Design → Manual Kajabi Upload → Manual Social Copywriting = ~8-12 hours of founder time per module.
* **Target State:** 1 Input → Zapier Automation → 4 Outputs = 0 hours of founder time.

---

## 2. The Trigger

**App:** Google Drive  
**Event:** "New File in Folder"  
**Folder:** `SEL Academy/Curriculum/Ready for Processing`  

*Operational Rule:* When Tascha finishes a module (e.g., `RED_Module_Enhanced.md`), she drops it into this specific Google Drive folder. This is the only manual step in the entire process.

---

## 3. Step 1: Slide Deck Generation

**App:** OpenAI (ChatGPT) / Google Slides (or Canva)  
**Action:** "Create Presentation"

* **Prompt to AI:** "You are an expert instructional designer. Extract the key learning objectives, frameworks (like DOES-C or ROYGBIV), and actionable strategies from the attached curriculum text. Create a 10-15 slide presentation outline. For each slide, provide a Title, 3 concise bullet points, and speaker notes."
* **Design Constraint (Visual Accessibility):** The automation routes the AI output into a Google Slides template that utilizes a neutral color palette (navy and gold). This ensures bold colors stand out without creating a high-stimuli environment, accommodating neurodiverse learners.
* **Output:** A draft Google Slides presentation saved to the `SEL Academy/Curriculum/Outputs/Slides` folder.

---

## 4. Step 2: PDF Workbook Creation

**App:** Document Studio (or Google Docs + Google Drive)  
**Action:** "Create Document from Template" & "Convert to PDF"

* **Logic:** The automation maps the core content of the module (Overview, Core Values, What You'll Learn, Reflection Questions) into a pre-designed Google Doc template. 
* **Design Constraint (Nonlinear Thinkers):** The template is structured with clear headings, ample white space, and visual anchors rather than dense text blocks.
* **Output:** The populated Google Doc is automatically converted to a PDF and saved to `SEL Academy/Curriculum/Outputs/Workbooks`.

---

## 5. Step 3: Kajabi Course Upload

**App:** Kajabi (via Webhooks/API if direct integration is limited)  
**Action:** "Create Lesson"

* **Logic:** The automation creates a new lesson within the designated Kajabi course (e.g., *Waya Wisdom* or *Beyond Boundaries*).
* **Data Mapping:**
    * **Lesson Title:** Pulled from the document title.
    * **Lesson Body:** The raw markdown/text of the module.
    * **Downloads:** The Zap attaches the PDF Workbook generated in Step 2 via its public Google Drive link.
* **Output:** A drafted lesson in Kajabi, ready for final review and publishing.

---

## 6. Step 4: Social Content Extraction

**App:** OpenAI (ChatGPT) / Notion (or Google Sheets)  
**Action:** "Generate Social Posts"

* **Prompt to AI:** "Act as an expert educational copywriter. Read the attached curriculum module. Extract 5 distinct, highly engaging social media posts suitable for LinkedIn and Instagram. Focus on the neurochemical insights (DOES-C), the cultural connections (Mashkawiziiwin), and practical advice for educators. Include appropriate emojis and hashtags."
* **Output:** The 5 generated posts are automatically appended to the `Social Media Content Calendar` database in Notion, tagged with the module name and marked as "Ready for Review."

---

## 7. The Final Notification

**App:** Slack or Email  
**Action:** "Send Message"

* **Message:** "✅ **Curriculum Engine Complete:** The module `[File Name]` has been processed. 
    * Slides generated: [Link]
    * PDF Workbook generated: [Link]
    * Kajabi Lesson drafted: [Link]
    * 5 Social Posts added to Notion: [Link]"

---

## 8. Implementation Steps

1. **Create the Google Drive Folders:** Set up the "Ready for Processing" and "Outputs" folders.
2. **Design the Templates:** Create the master Google Slides template and the master Google Doc workbook template. Ensure both adhere to the navy/gold, visually accessible brand guidelines.
3. **Build the Zap:** Connect Google Drive, OpenAI, Google Docs/Slides, Kajabi, and Notion in Zapier.
4. **Test with a Live File:** Drop `RED_Module_Enhanced.md` into the trigger folder and verify all four outputs generate correctly.
