---
title: "alt f2    device not found"
date: 2010-03-18
forum: New to Ubuntu
---

### Post by 3948ctyj on 2010-03-18
9.04

on bios update I am getting 
looking for usb device    device not found    over and over again
what might be the problem..??

---

### Post by biomedtech on 2010-03-19
> **3948ctyj said:**
> 9.04

on bios update I am getting 
looking for usb device    device not found    over and over again
what might be the problem..??

When I tried to update the bios on my Eee PC, that same message was repeated over and again. I was trying to use an SDHC card in a reader adapter. Then I tried using a regular thumb drive and got the same result. 
The third try I used an older 2 GB SD card in the reader, and VOILA! 

Something about a DOS startup and not recognizing larger volumes? Try moving your bios file to a smaller usb memory stick, card, or reader.


Lastly, after the usb stick was recognized, I had to rename my bios from it's original "901-ASUS-2103.ROM", to "BIOS.ROM", because that is what the update program was looking for.  It worked.

---

