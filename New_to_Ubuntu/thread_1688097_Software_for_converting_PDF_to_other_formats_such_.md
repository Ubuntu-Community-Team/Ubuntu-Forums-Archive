---
title: "Software for converting PDF to other formats such as Doc?"
date: 2011-02-15
forum: New to Ubuntu
---

### Post by marl30 on 2011-02-15
Like the title says, I'm looking for a software for converting PDF into other formats.

---

### Post by marl30 on 2011-02-15
I found a Libreoffice/Openoffice extension in the repository for importing PDF, but after installing it I'm not seeing the import option.

---

### Post by NightwishFan on 2011-02-15
You are unable to 'just open the file'?

Edit, I can open them in OpenOffice Draw after installing the extension. (Just use file->open).

---

### Post by marl30 on 2011-02-15
> **NightwishFan said:**
> You are unable to 'just open the file'?

Edit, I can open them in OpenOffice Draw after installing the extension. (Just use file->open).

For some reason, when I try to use Draw to open PDF it launches Writer instead, which brings up the ASCLL filter option.

---

### Post by NightwishFan on 2011-02-15
That is strange. :/ Perhaps reinstall the plug-in. Also note I am using OO.org in Maverick and not Libreoffice or etc.

---

### Post by marl30 on 2011-02-15
> **NightwishFan said:**
> That is strange. :/ Perhaps reinstall the plug-in. Also note I am using OO.org in Maverick and not Libreoffice or etc.

I'm using Libreoffice, so maybe that's the issue. I doubt using Draw to open it would make much of any difference though, just as how I can import PDF into Gimp, but still unable to save as doc after that. 

I found that a program called Calibre works, but distorts the formate which totally defeats the purpose of wanting to covert PDF into Doc.

---

### Post by scouser27 on 2011-02-15
I use LibreOffice 3.3 for this and it's fine on working with PDFs.

Here's what you do:

Start LibreOffice so that it's asking you to select Text Document, Drawing, Spreasheet etc.

At this stage, DO NOT CLICK Drawing. Instead, click Open and make sure that you've got "Files of type" selected as "All files". 

Then simply find your PDF file in the list available and it should open.

I note that it's not perfect and it does sometimes mess up the formats but for the most part it's ok.

---

### Post by marl30 on 2011-02-15
> **scouser27 said:**
> I use LibreOffice 3.3 for this and it's fine on working with PDFs.

Here's what you do:

Start LibreOffice so that it's asking you to select Text Document, Drawing, Spreasheet etc.

At this stage, DO NOT CLICK Drawing. Instead, click Open and make sure that you've got "Files of type" selected as "All files". 

Then simply find your PDF file in the list available and it should open.

I note that it's not perfect and it does sometimes mess up the formats but for the most part it's ok.

Didn't work for me. Whenever I tried that option I kept getting this pop up:                       p { margin-bottom: 0.08in; }ASCII Filter Options. Whichever of the options I choose it doesn't seem to produce a readable output.

I guess I'm looking for something that is not quite possible as yet - a perfect conversion from PDF to document formats. 

 Thanks for the suggestions anyhow.

---

### Post by giovannilenzi on 2011-02-24
No, you don't. 
I think your are looking for a possible thing.
I added the pdf-import extension to my Openoffice 3.2 and it works very well.

Go to System > Administration > Synaptic
Add the packet:
openoffice.org-pdfimport

Restart Open-office
Open a pdf as any other file.

---

### Post by marl30 on 2011-03-01
For the second day in a row, Chrome Web Store has come to the rescue in providing the perfect solution for something I've been looking for. I found a Chrome app that gives perfect results converting PDF to DOC. :D

[https://chrome.google.com/webstore/detail/jclipofobaadknkadkpgggmjkebddjam](https://chrome.google.com/webstore/detail/jclipofobaadknkadkpgggmjkebddjam)

---

