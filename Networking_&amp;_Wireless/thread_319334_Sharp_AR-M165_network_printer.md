---
title: "Sharp AR-M165 network printer"
date: 2006-12-15
forum: Networking &amp; Wireless
---

### Post by hrabeX on 2006-12-15
Could anybody help me to print on Sharp AR-M165 printer connected in MS windows network? There are no linux drivers:(

---

### Post by filip.trzeciak on 2008-04-30
no drivers if u want to print via USB/LPT (because machine needs rasterized page in SPLC printing language which is GDI with JBIG compression)
[http://esupport.sharp.at/html/driver/index.php?StartRec=0&ListLimit=20&TemplateLang=en&Lang=%&ProdLine=34&SortOrder=DESC&OrderBy=Title&OS=%&EMU=SPLC&SearchString=ar-m165](http://esupport.sharp.at/html/driver/index.php?StartRec=0&ListLimit=20&TemplateLang=en&Lang=%&ProdLine=34&SortOrder=DESC&OrderBy=Title&OS=%&EMU=SPLC&SearchString=ar-m165)
if any says linux it disclaims that AR-NB3 is required

however 

if u invest $$$ in AR-NB3 network printing extension and another $$$ for AR-PK1N (just to handle postscripts jobs via network) u can print from linux by just downloading .ppd (should be included in recent CUPS)

another aproach (cheaper :twisted:)is to build your own AR-NB3 + AR-PK1N equivalent by geting some old windows box with net card and install redmon and ghostscript:
[http://home.comcast.net/~heretrythis/hp3100/psemu.html](http://home.comcast.net/~heretrythis/hp3100/psemu.html)

that makes your solution easier if u say u already have someone with windows and printer on network, just install redmon and ghostscript and connect to new printer share using any driver that splits out postscript

tricky part is that it is someones machine to have redmon and ghostscript installed :)

easy part is it is all in one in PDFcreator ([http://www.pdfforge.org/products/pdfcreator](http://www.pdfforge.org/products/pdfcreator))

---

