---
title: "Application to convert &quot;image text&quot; to text..."
date: 2011-01-02
forum: New to Ubuntu
---

### Post by akelsall on 2011-01-02
I have a PDF document that is a series of scanned pages of text. Since they are, in effect, images of text, is there any program out there that can capture the text, then convert it to "true" text? 

I know you can scan a page on a scanner and use OCR, but I want to be able to capture the text on the screen, then convert that captured portion to text. I know Snagit (for Windows) can do this. Is there anything out there for Linux?

Thanks,

Andy

---

### Post by wep940 on 2011-01-02
I found a few things on the net.  This one looks promising, but I don't know how up to date the article is:
 
[http://http://blogs.pcworld.co.nz/pcworld/tux-love/2007/11/hidden_linux_ocr_secrets.html](http://http://blogs.pcworld.co.nz/pcworld/tux-love/2007/11/hidden_linux_ocr_secrets.html)

---

### Post by AlphaLexman on 2011-01-02
I'm not on a ubuntu machine right now, but there is a man page for 'pdftotext' [here]("http://linuxmanpages.com/man1/pdftotext.1.php").
So a .deb package can't be too far!

---

### Post by JC Cheloven on 2011-01-02
The program pdftotext is included in the package xpdf-utils. So from a terminal you can install the package by typing
```
sudo apt-get install xpdf-utils
```
then invoking the program pdftotext by typing 
```
pdftotext
```

Read first the manual, either in the web as suggested before or (better) in your own terminal:
```
man pdftotext
```(ctrl-z to exit from that)

---

