---
title: "A pdf document not recognized as pdf in FAT32 partition"
date: 2010-05-11
forum: New to Ubuntu
---

### Post by ubume2 on 2010-05-11
Hi, I have downloaded a pdf document. On my Ubuntu partition, I can read the document.  I usually store all my documents in a separate FAT32 partition.  All of the other pdf documents are readable in that partition.  

The latest document shows up like an odt document. When I try to open it up from the FAT32 partition, I get a message Unable to open Document--Error opening Document permission denied.  

I am using Document Viewer in 9.10

Edit: the pdf document did not have the ending .pdf.  When I renamed it from blahblah to blahblah.pdf, the problem was solved.

---

### Post by tanoloco on 2010-05-14
thank you!

I downloaded several pdf documents and could read them with Document Viewer in Lucid but when I moved them to en ext3 partition I could only read some of them (which has the .pdf extension) and not others getting the same error as you. Adding .pdf extension to them fixed it!

Thank you I couldn't work it out and get myself lost in checking permissions which were all set correctly.

---

### Post by jpr0 on 2013-02-07
> **ubume2 said:**
> Hi, I have downloaded a pdf document. On my Ubuntu partition, I can read the document.  I usually store all my documents in a separate FAT32 partition.  All of the other pdf documents are readable in that partition.  

The latest document shows up like an odt document. When I try to open it up from the FAT32 partition, I get a message Unable to open Document--Error opening Document permission denied.  

I am using Document Viewer in 9.10

Edit: the pdf document did not have the ending .pdf.  When I renamed it from blahblah to blahblah.pdf, the problem was solved.

Works perfectly! Thanks.. was scratching my head at this.

---

### Post by wildmanne39 on 2013-02-07
Old thread closed.

---

