---
title: "How to insert a PDF into a Word Doc?"
date: 2011-04-06
forum: New to Ubuntu
---

### Post by blueghoti on 2011-04-06
Hi all - 

I am struggling with the following in Open Office and hope you might be able to help.

I have a word document which requires the inclusion of a separate PDF document as an annex.

Both documents open properly on their own, but when I go to Insert / File and then select my PDF, I get a corrupted PDF document.

Any ideas on how I can just bring it in natively and in the right position?

Chris

---

### Post by rewyllys on 2011-04-06
> **blueghoti said:**
> Hi all - 

I am struggling with the following in Open Office and hope you might be able to help.

I have a word document which requires the inclusion of a separate PDF document as an annex.

Both documents open properly on their own, but when I go to Insert / File and then select my PDF, I get a corrupted PDF document.

Any ideas on how I can just bring it in natively and in the right position?

Chris
You could copy the entire PDF document (i.e., use Ctrl-A to select the whole, and next, use Ctrl-C to copy it).  Then, with your cursor at the desired insert point, use Shift-Ctrl-V to paste the contents of the PDF into the Open Office document as unformatted text.  You'll have to do some minor cleaning up, but doing so should be easy and quick.

---

### Post by blueghoti on 2011-04-06
Hi - that's a good idea, thanks.  Didn't work however - I neglected to mention there are a lot of tables which didn't copy over properly...

Any other thoughts?

---

### Post by ~Plue on 2011-04-06
> **blueghoti said:**
> Hi - that's a good idea, thanks.  Didn't work however - I neglected to mention there are a lot of tables which didn't copy over properly...

Any other thoughts?you could install *openoffice.org-pdfimport* from the repos and then open and edit pdf file in openoffice draw. so the procedure to import a table from a pdf to writer with formatting would be;
1.open pdf with openoffice draw
2.select/copy what you want
3. past it in the document file

good luck

/(maybe its not the simplest way....)

---

### Post by rewyllys on 2011-04-06
> **~Plue said:**
> you could install *openoffice.org-pdfimport* from the repos and then open and edit pdf file in openoffice draw. so the procedure to import a table from a pdf to writer with formatting would be;
1.open pdf with openoffice draw
2.select/copy what you want
3. past it in the document file

good luck

/(maybe its not the simplest way....)
Also available via Synaptic Package Manager is *libreoffice-pdfimport* 
I just experimented with installing this (in LibreOffice 3.3.2), and then opening a PDF file in LibreOffice Writer. LO Writer opened the PDF without difficulty and printed it out correctly.
(Seemed pretty simple to me.:))
Thanks, ~Plue.

---

### Post by ~Plue on 2011-04-06
> **rewyllys said:**
> 
I just experimented with installing this (in LibreOffice 3.3.2), and then opening a PDF file in LibreOffice Writer. LO Writer opened the PDF without difficulty and printed it out correctly.

odd.. mine opens with draw even if i explicitly open it with writer (same version as yours)

---

### Post by blueghoti on 2011-04-07
Good tips, guys.  A bit of formatting / tweaking needed but helpful!

Thanks!

---

### Post by rewyllys on 2011-04-07
> **~Plue said:**
> odd.. mine opens with draw even if i explicitly open it with writer (same version as yours)
I agree that that is odd.:confused:

---

### Post by dingodog on 2011-04-07
Only way to include a **single** *PDF page* in *another* document as **VECTOR**, is to do this in **Scribus:**

- Creating your own document in Scribus
- inserting a new **imagebox**
- importing the **single pdf page**
- set **adjust frame to image"*

---

### Post by Nanshan on 2011-04-11
Well, as to convert PDF to Word, it will be easy to do with a pdf convertion tool like Advanced PDF Converter which allows you to convert pdf to word,excel,ppt.what's more, it can also convert word to pdf files with ease.

---

### Post by Kanahau on 2013-01-18
[QUOTE=rewyllys;10645498]Also available via Synaptic Package Manager is *libreoffice-pdfimport* 
I just experimented with installing this (in LibreOffice 3.3.2), and then opening a PDF file in LibreOffice Writer. LO Writer opened the PDF without difficulty and printed it out correctly.

for the sake of sounding stupid, how exactly would I install libreoffice-pdfimport?
 i looked on the software centre and couldnt see it, neither on the dashboard?

---

### Post by Kanahau on 2013-01-18
got it

---

