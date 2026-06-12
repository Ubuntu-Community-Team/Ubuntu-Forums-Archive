---
title: "Help with PCI Card - Laptop"
date: 2008-06-15
forum: Networking &amp; Wireless
---

### Post by Sariel42 on 2008-06-15
Hi, i'm new to ubuntu, i managed to get it running on 1 computer, and it worked well and i learned a ton so i decided to put it onto a laptop as well - now i'm using the Gutsy server disc (the first computer acts as a server for me) but on the laptop everything works fine, exect the PC card - now it's a 

Gateway M5309 Laptop
EDIMAX ew-7107 Wireless 'cardbus wireless lan' it's the larger card thats roughly 1.5"tall 3.5" long

when i insert it into the laptop, the lights do not flash - when i load the .inf files into ndiswrapper they say they are invalid files, when i use lspci i get a pci adapter, but not the name of the card or a chipset number - i can't seem to find what i'm Looking for - is this a problem with 
a) my card?
b) my laptop?
c) my install?

any help is VERY greatly appreciated, i have beginner's knowledge of ye olde ubuntu i will try to download the newest desktop install cd and try from there, but hopefully someone can point me in the right direction to fix this

thanks in advance!
-Sariel

---

### Post by Ayuthia on 2008-06-15
> **Sariel42 said:**
> Hi, i'm new to ubuntu, i managed to get it running on 1 computer, and it worked well and i learned a ton so i decided to put it onto a laptop as well - now i'm using the Gutsy server disc (the first computer acts as a server for me) but on the laptop everything works fine, exect the PC card - now it's a 

Gateway M5309 Laptop
EDIMAX ew-7107 Wireless 'cardbus wireless lan' it's the larger card thats roughly 1.5"tall 3.5" long

when i insert it into the laptop, the lights do not flash - when i load the .inf files into ndiswrapper they say they are invalid files, when i use lspci i get a pci adapter, but not the name of the card or a chipset number - i can't seem to find what i'm Looking for - is this a problem with 
a) my card?
b) my laptop?
c) my install?

any help is VERY greatly appreciated, i have beginner's knowledge of ye olde ubuntu i will try to download the newest desktop install cd and try from there, but hopefully someone can point me in the right direction to fix this

thanks in advance!
-Sariel

You might check lshw -C network and see if anything shows up for it.  Another place that you might check is lsusb (probably won't be in there if you do see the card in lspci).  You could also check and see if lspci -nnm shows anything.  It should give you the id numbers for the card if it finds anything.

---

