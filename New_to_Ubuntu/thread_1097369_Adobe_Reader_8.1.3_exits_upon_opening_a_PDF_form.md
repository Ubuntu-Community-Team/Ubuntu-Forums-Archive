---
title: "Adobe Reader 8.1.3 exits upon opening a PDF form"
date: 2009-03-15
forum: New to Ubuntu
---

### Post by rcy3cornelledu on 2009-03-15
I downloaded Adobe Reader 8.1.3 (.deb package installed by sudo dpkg --install ; this also happens with the .tar.gz download/install) from Adobe.

< [http://ardownload.adobe.com/pub/adobe/reader/unix/8.x/8.1.3/enu/AdobeReader_enu-8.1.3-1.i386.deb](http://ardownload.adobe.com/pub/adobe/reader/unix/8.x/8.1.3/enu/AdobeReader_enu-8.1.3-1.i386.deb) >

I am running Ubuntu 8.10 Intrepid (32-bit) on VMWare Server in Windows Vista Home Basic on an AMD X2 64 laptop.

Linux 2.6.27-11-generic #1 SMP Thu Jan 29 19:24:39 UTC 2009 i686 GNU/Linux

With Adobe Reader, I can open and view ordinary PDF files just fine. But when I try to open a PDF document with a form, such as < [http://www.irs.gov/pub/irs-pdf/f1040.pdf](http://www.irs.gov/pub/irs-pdf/f1040.pdf) > (after downloading and saving to disk), the Reader program instantly closes.

I am not sure where to find a log of what went wrong.  Has anyone experienced this before?

I have failed to use eVince to fill PDF forms because my typed text disappears as soon as I change to a different form field.

I would like to be able to fill PDF forms in some application running in Ubuntu.  I also tried xpdf-reader, which doesn't seem to let me click into form fields, and pdfedit, which seems to open the PDF at too low a level for me.

---

### Post by rcy3cornelledu on 2009-03-15
In the web browser (Firefox 3.0.6), the PDF (with form) displays OK, but as soon as I click in a field, then the PDF image disappears.

I have also submitted this as < [https://www.adobe.com/cfusion/support/index.cfm?event=casedetail&id=0201759299&loc=en_us](https://www.adobe.com/cfusion/support/index.cfm?event=casedetail&id=0201759299&loc=en_us) > to Adobe's support forums.

---

### Post by leonardo_neo on 2009-03-15
I don't have solutions for your problem, but I just want to ask why don't you use the default document viewer given with Ubuntu?? That opens almost all type of documents, and it works fine with me.

---

### Post by rcy3cornelledu on 2009-03-16
Thanks for your advice!  I should have said "Document Viewer 2.24.1" when I wrote eVince.  Trying again with that application, now I discover that when I enter data into form fields, the data vanishes when I go to another form field, but after File -> Save a Copy, and closing and opening the saved file, the data will be there if I click into the same field.

Checkbox states do persist and display correctly, but it just seems that field data are not shown unless that field has the focus.

I'm happy to elaborate or provide more details.  Do you find that the text data you enter into forms stays put when you click into other form fields?

---

### Post by serge_98 on 2012-01-23
Was the problem with disappearing text in the Document Viewer resolved? What do you do to edit and persist PDF forms in Ubuntu?

---

### Post by oldos2er on 2012-01-24
Closed, necromancy. Please start a new thread for your question or problem.

---

