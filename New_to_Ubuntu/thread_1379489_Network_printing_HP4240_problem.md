---
title: "Network printing HP4240 problem"
date: 2010-01-12
forum: New to Ubuntu
---

### Post by Siruami on 2010-01-12
Hi all.
I am new to Ubuntu, around 2 weeks.
Yesterday I installed successfully a network printer, a HP Laserjet 4240, it actually was really easy to do, after printing the test page and it came out with the grayscale graphic I supposed everything was good...
Until today... when I actually tried to print a PDF document. It sends to the printer, says ¨Processing¨ and then the Complete message, but the printer does NOTHING.
I can send how many test pages I want, and they work fine, but nothing comes up from actual documents, neither PDFs or OpenOffice writer.
I have Ubuntu Karmic Koala 9.10
Thanks in advance.

---

### Post by patchwork on 2010-01-12
Is cups currently running?  I have had some issues recently where the cups daemon is not starting on startup.  Try opening a terminal and entering sudo /etc/init.d/cups restart 

This will restart the cups daemon if it is not running.

---

### Post by Siruami on 2010-01-12
* Restarting Common Unix Printing System: cupsd                         [ OK ] 

Same result

---

### Post by Siruami on 2010-01-12
An update...
It is printing from Open Office Writer, last time didnt because a network error.
So. why is not printing PDFs? could be a problem with document viewer?
I am going to try opening the PDFs with another viewer and post a result soon.
Thanks.

---

### Post by Siruami on 2010-01-12
Can not believe it.
Opened it with Okular, and printed fine.
Wonder if this is a bug???

---

### Post by patchwork on 2010-01-12
Not sure, but glad things are working for you.  Perhaps it was the same network error that affected your other print jobs?

---

### Post by Siruami on 2010-01-12
I was thinking on that possibility too, but no, I already checked, is just Document Viewer don´t print, and don´t know why

---

### Post by walt.smith1960 on 2010-01-13
Could it be a document viewer problem? I had issues with some .pdf files in document viewer. Adobe Acrobat reader for Linux seems slower but so far is pretty reliable.

---

