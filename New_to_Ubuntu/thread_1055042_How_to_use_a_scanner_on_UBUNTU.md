---
title: "How to use a scanner on UBUNTU"
date: 2009-01-30
forum: New to Ubuntu
---

### Post by ian19jam on 2009-01-30
I have a Epson CX3600 Printer, scanner and photocopier. The printing side of things appear to work with UBUNTU but how do I use the scanner please? Can anyone inform me as to what I should be doing. Please bear in mind that I am very much a beginner with computers.

Thanks Ian

---

### Post by Cypher on 2009-01-30
You're going to need to install the Sane software
```

sudo apt-get install xsane
sudo apt-get install gscan2pdf

```
to search for xsane in Synaptics Package Manager. Once installed, goto Applications->Graphics and you will find XSane there. Start it and it will search your machine for access to the scanner.

It will by default open 2 windows, one of them being a preview window and the other allowing you to control the format of what you are scanning and where you want to store it.

I've found that XSane is perfectly good at creating color or B&W JPEG files without any problems, but creating multi-page PDF's seems to be broken, so I use gscan2pdf to take all those JPEG files and create a multi-page PDF.

---

### Post by ian19jam on 2009-01-30
Thanks for the advice and I shall give it a try

---

### Post by ian19jam on 2009-01-30
Thanks Cypher it has worked a treat and I can now scan some photos with no problems as you said.

---

