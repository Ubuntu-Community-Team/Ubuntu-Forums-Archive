---
title: "run windows programs"
date: 2009-08-22
forum: New to Ubuntu
---

### Post by som1special2 on 2009-08-22
I have an epson stylus nx300 all in one and need the scanner functionality that does not work in this version of Ubuntu. What is the best way to run the epson program in 9.04 where I use the windows disk I have?
\\PLEASE NOTE THAT I AM ASKING ABOUT THE SCANNER,  I HAVE THE PRINTER FUNCTION WORKING FINE.

---

### Post by Liolikas on 2009-08-22
For printer drivers here:
[http://www.openprinting.org/show_printer.cgi?recnum=Epson-Stylus_NX300](http://www.openprinting.org/show_printer.cgi?recnum=Epson-Stylus_NX300)

And you can try program called **wine** if you want to use windows programs.

---

### Post by Codix121 on 2009-08-22
Wine might work but it doesn't Always,
Wine is what kept me from ever going back to Windows!
that and winblows got a lame virus even after I paid
100 dollar subscription to anti-virus!

Ubuntu FTW!

---

### Post by lisati on 2009-08-22
> **Codix121 said:**
> Wine might work but it doesn't Always,
Wine is what kept me from ever going back to Windows!
that and winblows got a lame virus even after I paid
100 dollar subscription to anti-virus!

Ubuntu FTW!

<aside>The only time that I know for sure that any of my machines has been rendered unusable by a virus was my own fault, using different AV software to usual and deliberately opening an infected file to see what would happen. Went back to the free one I'd been using before, no problems!</aside>

---

### Post by markharding557 on 2009-08-22
wine cannot be used to install drivers it is basically a translation layer between linux and a win app that for eq allows notepad to run

---

### Post by Mark Phelps on 2009-08-23
> **som1special2 said:**
> What is the best way to run the epson program in 9.04 where I use the windows disk I have?

Linux is not Windows -- you can't use the stuff on the Epson MS Windows disk in Ubuntu.  As has already been said, you also can't use Wine to install drivers or device software.

Check the link that Liolikas provided.

You can also open CUPS printer manager directly by entering localhost:631 in your browser and try installing the printer through there.  It may be able to locate drivers for your printer.

---

