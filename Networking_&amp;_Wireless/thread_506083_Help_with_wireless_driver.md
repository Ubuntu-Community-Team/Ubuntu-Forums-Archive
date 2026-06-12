---
title: "Help with wireless driver"
date: 2007-07-21
forum: Networking &amp; Wireless
---

### Post by PopPooB on 2007-07-21
Marvell TOPDOG (TM) PCI-Express 802.11n Wireless (EC85)

i dont know how to make that device work does anyone know and cn anyone tell me

---

### Post by djdicbob on 2007-07-21
Check [ndiswrapper.sourceforge.com]("http://ndiswrapper.sourceforge.com")  Their you  can find a list of compatible wifi cards.  Ndiswrapper, wraps the windows driver so that it works with Linux!

---

### Post by PopPooB on 2007-07-21
that link doesnt help at all man

---

### Post by cosborn72 on 2007-07-21
PopPooB

That link seems to be broken.   The correct link is [http://ndiswrapper.sourceforge.net/joomla/]("http://ndiswrapper.sourceforge.net/joomla/")

Basically, all wireless cards require drivers to work.  Most companies that make wireless cards do not make Linux drivers, and won't share their code so that someone else can.  There are linux drivers out there for some cards.  I don't think there is one of yours. 

Ndiswrapper is a program that wraps a windows driver into code that allows linux to use it. I did not see your exact driver on the ndiswrapper site, but there were some similar ones.  You might want to try it. 

Here is how to do it.

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

Getting an unsupported driver to work in Linux can be a challange, and it may or may not work, but it is worth a try.   Good luck!  Check back here if you get into trouble.

---

### Post by madmetal on 2007-07-21
what chipset does your card have?
open terminal and write 
lspci
and find the wireless card and its chipset..

---

