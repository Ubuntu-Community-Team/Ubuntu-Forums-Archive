---
title: "About creating a PDF document"
date: 2010-06-04
forum: New to Ubuntu
---

### Post by suomalainen on 2010-06-04
Ubunteros,

In Ubuntu 10.04LTS there is program "OpenOffice Word Processor". When you use this program there is a PDF icon that allows you to save current document in PDF file format....

Here's my question.

If you are using Firefox version 3.6.3 is there a similar PDF feature that will save the web page you are reading as also a PDF? Maybe there is a plugin or something.

If this can be done, please let me know.

As always, thanks for your support.

---

### Post by weirdtalk on 2010-06-04
Yes.

File > Print... > Print to File
set output type to pdf.
choose a filename
click print.

edit:
from howefields post I think this requires you install cups-pdf

---

### Post by howefield on 2010-06-04
If you are using Hardy as per your profile, you could install cups-pdf.

If you are running a more current version, you may have that functionality already, try printing to file, and select pdf.

---

### Post by Mze on 2010-06-04
see if Firefox addon [PDF Download]("https://addons.mozilla.org/en-US/firefox/addon/636/") meets your needs.

---

### Post by stoogiebuncho on 2010-06-04
> **howefield said:**
> If you are using Hardy as per your profile, you could install cups-pdf.

If you are running a more current version, you may have that functionality already, try printing to file, and select pdf.

+1  This works for everything.  I believe it saves your files in the /home/*username*/PDF folder.  If the folder doesn't exist it will create it for you.

---

### Post by howefield on 2010-06-04
> **stoogiebuncho said:**
> If the folder doesn't exist it will create it for you.

Depends on the version of cups-pdf I think, in any case, if installing cups-pdf doesn't create a PDF folder in your /home, then simply create it manually.

---

### Post by suomalainen on 2010-06-04
Thank you everybody for you help on this. I'm running 10.04 and it worked out of the box!

Excellent!

Thanks again!

---

