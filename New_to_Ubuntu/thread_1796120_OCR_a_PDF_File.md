---
title: "OCR a PDF File"
date: 2011-07-03
forum: New to Ubuntu
---

### Post by mal_conductor on 2011-07-03
Is there any software to do OCR on a PDF file.

I have the scanned image of some text I would like to convert to a text document.

TY

---

### Post by mikewhatever on 2011-07-03
There are some free online services:
[http://www.free-ocr.com/](http://www.free-ocr.com/)
[http://www.onlineocr.net/](http://www.onlineocr.net/)
[http://www.ocronline.com/](http://www.ocronline.com/)

---

### Post by ajgreeny on 2011-07-03
Or you could try the extremely good tesseract version3  from [https://launchpad.net/~alex-p/+archive/notesalexp](https://launchpad.net/~alex-p/+archive/notesalexp) 

It is the first time I have got a sensible OCR from linux, and might be worth trying, just for future reference, if not for this particular job.

---

### Post by mal_conductor on 2011-07-03
> **ajgreeny said:**
> Or you could try the extremely good tesseract version3  from [https://launchpad.net/~alex-p/+archive/notesalexp](https://launchpad.net/~alex-p/+archive/notesalexp) 

It is the first time I have got a sensible OCR from linux, and might be worth trying, just for future reference, if not for this particular job.

Thank you for your reply.  I think this is what I am looking for.
I added the site to my sources but then how do I only download tesseract?

I don't want to update nor download all the stuff in that list.

---

### Post by ajgreeny on 2011-07-04
Enable that repository, then use synaptic, which is a bit like software-centre, but more detailed, to search for tesseract and its language packages.  After installing the new version of tesseract, and whichever language(s) you want with it, disable the repo again, which you can do from synaptic Settings ->Repositories menu item, and you will not be prompted to update everything else.

---

### Post by mbocciab on 2011-09-13
Try gscan2pdf that uses tesseract.
It's not the best but it works

---

### Post by mike555 on 2011-09-13
Can't you just open pdf in evince,copy text and paste in Abiword or LibreOffice ?

 Or just open pdf in LibreOffice using plugin .

---

### Post by MarjaE on 2011-10-03
> **mike555 said:**
> Can't you just open pdf in evince,copy text and paste in Abiword or LibreOffice ?

 Or just open pdf in LibreOffice using plugin .

???

No. The whole point is that for many pdfs, such as scanned images, you can't.

---

### Post by robert shearer on 2011-10-03
You may wish to try YAGF and cuneiform....
[http://ubuntuforums.org/showthread.php?t=1714831](http://ubuntuforums.org/showthread.php?t=1714831)

YAGF will handle pdf documents.
See their homepage...
[http://symmetrica.net/cuneiform-linux/yagf-en.html](http://symmetrica.net/cuneiform-linux/yagf-en.html)

---

### Post by Synoc on 2012-01-26
I have heard, Google has taken the tesseract OCR and improved upon it somewhat. from what I've read about tessacrt-ocr, it seems to be CLI based. goes anyone know if Google's version has been made into GUI based version and/or where I can get it?

---

### Post by robert shearer on 2012-01-27
@**Synoc...... post#10**
Yes, look in Ubuntu Software Centre or Synaptic for **ocrfeeder**.

Or, at the CLI run ```
sudo apt-get install ocrfeeder

```

Ocrfeeder uses tesseract as it's ocr engine.

Post again if you have any questions on usage.
:)

(note that you a probably better served by _opening a new thread with your specific question_. This thread is about 'OCR a PDF File' so the replys before your post and after this one are in response to that.....)

cheers,Bob.

---

### Post by Sigma1 on 2012-01-27
What I've sometimes done with pdf's is:
1. make a screenshot in .tif format
2. convert that to .txt using tesseract from the command line.
Otherwise, this how to, which enables you to use tesseract in association with xsane, still works on 11.10: [http://ubuntuforums.org/showthread.php?t=1613501](http://ubuntuforums.org/showthread.php?t=1613501)
Good luck.

---

### Post by Nalin x Linux on 2012-11-12
Linux-intelligent-ocr-solution

[http://code.google.com/p/linux-intel...-ocr-solution/](http://code.google.com/p/linux-intel...-ocr-solution/)

Lios is a free and open source software for converting print in to text using either scanner or a camera, It can also produce text out of scanned images from other sources such as Pdf, Image or Folder containing Images. Program is given total accessibility for visually impaired. Lios is written in python, and we release it under GPL3 license. Lios will work with Debian based operating systems. There are great many possibilities for this program, Feedback is the key to it

---

### Post by oldos2er on 2012-11-13
Old thread closed. Please don't bump old threads.

---

