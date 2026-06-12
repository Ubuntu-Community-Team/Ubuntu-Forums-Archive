---
title: "Please help with tool / Ide for the following"
date: 2011-08-31
forum: New to Ubuntu
---

### Post by davidgrm on 2011-08-31
Hi

I have been programming embedded systems in C for many years but am a newbee using Linux

I want to develop a system using embedded Ubuntu and would like some suggestions regarding the following:

My program needs to be accessed from net using a browser. This will allow users to logon and make various changes to the programs settings.

The above also needs to be done on the unit itself using keyboard , mouse and monitor.

The program must read and write data to units plugged into the USB port although this might need to be mapped to a com port and use a USB to serial converter

Users without any linux knowledge should be able to do updates to the program using a screen on the local system and downloading from net or by means of USB port

Would this be best accomplished using a two tier Client Server architecture? 

Which programming language / s  would be most suitable to accomplish this?

All helpful / intelligent suggestions would  be most welcome

---

### Post by Wim Sturkenboom on 2011-08-31
If you write a small webserver, it will cover both remote and local access. You can find an example in the book on [http://www.advancedlinuxprogramming.com/](http://www.advancedlinuxprogramming.com/) (chapter 11)

My preferred language is C; I might be slightly biased (also coming from the embedded world with MCS51 and PIC microcontrollers) but I consider it the most universal language. Embedded for me is basically synonymous for C and assembler. Linux is synonymous for C. Common denominator: C :D

Can not advise on updates; no experience with that taking into account your requirements. Maybe a deb package?

---

### Post by davidgrm on 2011-09-01
Thank you for that reply. I was hoping that I would get more than one suggestion :(

---

### Post by Wim Sturkenboom on 2011-09-01
> **davidgrm said:**
> I was hoping that I would get more than one suggestion :(
Report your opening post (there is an icon 'report abuse', not only for abuse) and ask the thread to be moved to the programming section;  you have more chance there. This is not really a beginner question ;)

---

