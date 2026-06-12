---
title: "PdfTex Compiling Problems in Kile"
date: 2010-11-23
forum: New to Ubuntu
---

### Post by hirnplanet on 2010-11-23
Hi

i have a wired problem with my kile. Yesterday i was working on one of my latex files and everything went fine. As i restarted my computer today and wanted to continue working on them I couldnt compile my files into pdf. I didnt change anything. The day before i only installed okular for pdfview.

I made a test file and posted the log file of my terminal:

> fabian@fabian-laptop:~/Desktop$ pdftex test.tex
This is pdfTeX, Version 3.1415926-1.40.10 (TeX Live 2009/Debian)
 restricted \write18 enabled.
entering extended mode
(./test.tex
! Undefined control sequence.
l.1 \documentclass
                  [pdftex,a4paper,10pt]{scrreprt}
? 
! Undefined control sequence.
l.2 \usepackage
               [utf8x]{inputenc}
? 
! Undefined control sequence.
l.5 \title
          {}
? 
! Undefined control sequence.
l.6 \author
           {}
? 
! Undefined control sequence.
l.9 \begin
          {document}
? 
! Undefined control sequence.
l.10 \maketitle
               
? 
! Undefined control sequence.
l.12 \begin
           {abstract}
? 
[1{/var/lib/texmf/fonts/map/pdftex/updmap/pdftex.map}] )</usr/share/texmf-texli
ve/fonts/type1/public/amsfonts/cm/cmr10.pfb>
Output written on test.pdf (1 page, 15558 bytes).
Transcript written on test.log.

I really dont know what happened. I installed all LaTex packages new and kile also. 
I really really would be happy if  anyone could help me.

---

### Post by wt8008 on 2010-11-23
A possibility is that you need to run pdflatex instead of pdftex.

---

