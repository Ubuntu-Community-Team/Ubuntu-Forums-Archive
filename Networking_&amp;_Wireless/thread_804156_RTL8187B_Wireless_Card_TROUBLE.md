---
title: "RTL8187B Wireless Card TROUBLE"
date: 2008-05-22
forum: Networking &amp; Wireless
---

### Post by ShinHadoken on 2008-05-22
Okay, I've posted a million times about this in the past, but now I'm sure what kind of wireless card I have. **I have a RealTek RTL8187B wireless card. How do I get this to work with Ubuntu? Also, can I get this card to work with Aircrack-ng?**

Thanks MILLIONS in advance!!

---

### Post by mishaonline on 2008-05-22
I am in the process of trying to get that going too (Toshiba laptop with RTL8187B) and I can help you with what I have done so far. You could try the linux drivers that you can find here: [http://www.datanorth.net/~cuervo/rtl8187b/](http://www.datanorth.net/~cuervo/rtl8187b/) . That worked for me at some point, but it was unstable and I had to configure all the settings through the terminal everytime I wanted to use it.

What I'm trying out now is setting up the windows drivers using ndiswrapper ([http://ndiswrapper.sourceforge.net/](http://ndiswrapper.sourceforge.net/)). You can get all the instructions on their site and if you look at the list of cards supported there, it tells you how to get RTL8187B going: gives you a link to the windows drivers and advises to use the win98 driver and not winXP.

**Note:** you may need to modify the driver so that it accepts the mapping ID that your card is connected to. To find out what ID it is mapped to, go "lsusb" (if connected using USB) or "lspci" (if connected using PCI) and look for something to do with Realtek there. In my case it was ID 8189, so I had to find the two lines in the driver .ini  file with mapping, copy one of them and replace the usual 8187 with 8189 (I found that in one of the posts on this forum, but I can't find it anymore, sorry).

Using that method I managed to get wireless to appear in the network manager, and it now sees my home network and seems to connect to it, but I can't ping the ip of my router and internet is not working. Perhaps someone here can solve that bit.
But hope my explanation helps.

---

### Post by ShinHadoken on 2008-05-24
What model Toshiba laptop do you have? I'm trying to get it to work on a Satellite A205.

---

### Post by ShinHadoken on 2008-05-24
QUESTION - I hear that the wireless internet doesn't function on the live cd version of Ubuntu. I'm using a 7.10 Gutsy live cd - does that mean that my wireless card will work if I installed Ubuntu to the hardrive? Or will I still have problems with the RTL8187B wireless card anyway?
 
Before anyone asks, I plan on installing Ubuntu; I'm just using a live cd right now to try to convince my dad, a grassroots Windows user, that it's better than Windows.

---

