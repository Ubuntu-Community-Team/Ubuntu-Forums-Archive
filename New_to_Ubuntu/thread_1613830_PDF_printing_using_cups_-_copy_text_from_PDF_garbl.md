---
title: "PDF printing using cups - copy text from PDF garbled"
date: 2010-11-04
forum: New to Ubuntu
---

### Post by cwmoser on 2010-11-04
I have a PDF printer driver installed using cups which I use to create a PDF files.  Later when I display the PDF file and try to copy text from the file, I get a bunch of graphic symbols for characters.  Is there a way to fix this so that the copied text can be pasted into other applications?

Thanks

Carl

---

### Post by cwmoser on 2010-11-05
Anybody notice when you print a document to a file using the Cups PDF driver and try to copy text from the PDF file that its garbled?

Here is an example:
I copied this from the PDF fie:
"Continued working on converting the Image Replicator from a program to a service."

... and below is what it looks like pasted:
4393:0/47343.43;07932,0#05.,9471742,5747,294,807;.0


Carl

---

### Post by realruntime on 2010-11-05
How did you install the cups PDF printer? I just tried with

apt-get install cups-pdf

But in my apps (e. g. Openoffice) there is no PDF printer visible... (I know... Openoffice creates PDF by itself, but in other apps I would need it).

---

### Post by rsgangr on 2010-11-05
I have just tried this, both with "Document Viewer" and with "Adobe".

In "Document Viewer" I marked the required text using the Left mouse button, went into "Text Editor" and pasted the text by pressing the mouse wheel.

In "Adobe" I followed the path "Tools/Select & Zoom/Select Tool" and marked the required text using the Left mouse button, went into "Text Editor" and pasted the text by pressing the  mouse wheel.

Both worked perfectly.

I cannot think of a reason why you are experiencing difficulty - sorry!

---

### Post by cwmoser on 2010-11-05
Did some more testing and noted that the garbled text occurs when I print PDF using applications that utilize WINE - like my Quicken and Quick Books.  The CUPS printer PDF driver seems to allow for text to be extracted from the PDF file if it was created using Open Office Writer or if it was output using FireFox.  The Windows apps utilizing Wine appears to be the issue with me.

Any ideas why this happens?

Thanks

Carl

---

### Post by cwmoser on 2010-11-08
Did a little more checking.  Apparently the text embedded in a PDF generated via Wine is in a different character encoding.

Here is what I have found:
I put the following text in QuickBooks and had it create a PDF output:
[B]01234567890
ABCDEFGH XYZ
abcdefgh xyz[/B]

Then I pasted it into an Editor and got a Hex dump:
[B]
1459:0100  03 21 02 1F 04 20 1E 1D-01 11 0D 0A 18 22 08 16
1459:0110  06 23 24 25 0C 26 27 28-0D 0A 09 29 1A 15 10 2A
1459:0120  2B 2C 0C 2D 2E 2F 00 00-00 00 00 00 00 00 00 00
[/B]

Note that ASCII hex code for "0" is 30 but the extraction from the PDF is 03.  For a "1", I get 21, etc.

The **0D0A** carriage return/line feed characters appear in proper place.


Any ideas??

---

### Post by tramir on 2011-02-13
Sorry to revive an older thread, but I have the exact same problem. Did you manage to find a solution in the end?

---

### Post by xiaoyihf on 2011-03-16
I can confirm this problem. I also attached the pdf file printed from cups-pdf.

I am using ubuntu 10.10

---

### Post by chanpeter88 on 2011-11-30
i am using ubuntu 11.10 and installed cups-pdf. if i print from firefox to pdf, the created pdf is not searchable. 

i want to copy txt from pdf.

i am using acrobat reader 9. i uses pdftotext and the output is garbled.


the webpage contains unicode. do i need to install additional ghostsript fonts? if yes, how to?

pls advise

---

