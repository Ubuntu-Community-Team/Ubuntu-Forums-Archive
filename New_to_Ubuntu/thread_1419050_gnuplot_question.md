---
title: "gnuplot question"
date: 2010-03-01
forum: New to Ubuntu
---

### Post by newport_j on 2010-03-01
Once I have a nice plot generated from gnuplot in Ubuntu, then how do I print it out? I do not want it in postscript format. Preferably something that I can put in a OpenOffice document. Is this even possible?

Newport_j

---

### Post by talonmies on 2010-03-01
If you want to print it out, then you actually want to save the output as postscript. The postscript can then be sent to the printer.

You can import embedded postscript images into OpenOffice (so using *set terminal postscript eps*), or alternatively, use PNG (so *set terminal png*). A typical session becomes:

```
$ gnuplot

    G N U P L O T
    Version 4.2 patchlevel 4 
    last modified Sep 2008
    System: Linux 2.6.28-18-generic

    Copyright (C) 1986 - 1993, 1998, 2004, 2007, 2008
    Thomas Williams, Colin Kelley and many others

    Type `help` to access the on-line reference manual.
    The gnuplot FAQ is available from http://www.gnuplot.info/faq/

    Send bug reports and suggestions to <http://sourceforge.net/projects/gnuplot>


Terminal type set to 'wxt'
gnuplot> plot sin(x)
gnuplot> set terminal png
Terminal type set to 'png'
Options are 'nocrop medium '
gnuplot> set output "yunker.png"
gnuplot> plot sin(x)
gnuplot> set output
gnuplot> set terminal wxt
Terminal type set to 'wxt'
Options are '0'
gnuplot> quit

```Which will drop a png file in the working directory:
```
$ ls -hl yunker.png 
-rw-r--r-- 1 talonmies talonmies 4.9K 2010-03-01 19:01 yunker.png

```

---

