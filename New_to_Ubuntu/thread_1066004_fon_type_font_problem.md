---
title: "fon type font problem"
date: 2009-02-10
forum: New to Ubuntu
---

### Post by zstein on 2009-02-10
I am very new to Linux....just installed Ubuntu 8.10 on my laptop.

I've added wine, and downloaded a windows based program which works fine except for one screen.  This screen uses a chart with symbols, and the symbols are all in a .fon font.  When I try to look at that chart screen, there are some default characters showing from whatever Ubuntu uses for defaults, but it will not access the .fon file for the program.  I have tried copying the fon file to a font folder in the windows tree of of my wine drive_c and also copied it to the default folder where the Linux fonts reside.

Short of contacting the software manufacturer and asking them to change their program, is there anything I can do to get the program to be able to use this .fon font?

Zane

---

### Post by Hospadar on 2009-02-10
You might try converting those files to something linux can read, like ttf or whatnot, then installing them.  I know there are some open source font tools, you could try those (don't know the names, poke around in synaptic), also maybe try googling around for how to convert them.

If you don't know how to install fonts in linux, a quick "install fonts in ubuntu" search will get you going.

---

### Post by cariboo on 2009-02-10
You may want to install the mscorefonts package. You can just install it bu itself, or install the ubuntu-restricted-extras meta package, which will install almost all the codecs you need to play most audio/video media, it also installs flash and java.

The ubuntu-restricted-extras meta package can be installed using Add/remove Programs, Synaptic Package Manager and of course the command line 

Jim

---

### Post by zstein on 2009-02-10
> **Hospadar said:**
> You might try converting those files to something linux can read, like ttf or whatnot, then installing them.  I know there are some open source font tools, you could try those (don't know the names, poke around in synaptic), also maybe try googling around for how to convert them.


I can convert the font to a .ttf, but will the program recognize it then? Wouldn't it still be looking for the .fon font?

---

### Post by zstein on 2009-02-10
> **cariboo907 said:**
> You may want to install the mscorefonts package. You can just install it bu itself, or install the ubuntu-restricted-extras meta package, which will install almost all the codecs you need to play most audio/video media, it also installs flash and java.

The ubuntu-restricted-extras meta package can be installed using Add/remove Programs, Synaptic Package Manager and of course the command line 

Jim

Jim, what I did so far was copy all of the default windows files that came form my Windows Vista computer on to a thumb drive, and then install them onto my Ubuntu computer.  The Windows program was calling on system and terminal fonts, and until I copied the windows versions onto my Ubuntu laptop, the program had a really awful looking display on most of the pages....now it looks fine.

It is only this one font that was created by the program designer.  The program is called Riyal and the font is Riyal32.fon    This is the only font file I can't get the program to read when I open it via wine

Do you think the ubuntu-restricted-extras meta package will help in this case?

---

