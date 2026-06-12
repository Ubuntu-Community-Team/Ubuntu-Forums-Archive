---
title: "Problems connecting to Protected Wireless Network"
date: 2008-04-26
forum: Networking &amp; Wireless
---

### Post by Dalius on 2008-04-26
Hello all,

I am trying to migrate to Ubuntu completely but I'm having problems connecting to my home wireless network, which is protected with WPA2-Personal. It keeps asking for the passkey, which I am typing in properly. It works on Windows and my iBook but Ubuntu doesn't seem to want to accept it.

I had to use ndiswrappers to install my drivers by the way. It's a Broadcom BCM43XG chipset on the Linksys Wireless-N WMP300N wireless adapter. 

Any help would be greatly appreciated! I am currently running my network without protection to connect through Ubuntu. :confused:

---

### Post by SkyyBugg on 2008-04-28
I have the same card and was not even able to get it to work with ndiswrapper.  Are you on 8.04?

I just installed 8.0.4 on my box at home and am going to try to get the wmp300N working tonight using b43-fwcutter 1:1-11 I found in the wireless forum. I installed on my office 8.04 but it does not have wireless at all.  Unfortunately there is a firmware upgrade so supposedly you have to do it via intenet.  [http://bcm43xx.berlios.de/](http://bcm43xx.berlios.de/).  so I have to put my home box on wired for a moment.

Hopefully this will work.

Any luck on getting protection working again?

SkyBugg

P.S. I don't see the card on Ubuntu's supported list

---

### Post by Dalius on 2008-04-28
Hey man,

Don't bother with the b43 cutter. This is how I got it to work on 8.04:

a) Download the latest drivers from Linksys.com 
b) Extract the .exe
c) Install ndiswrapper
d) System -> Admin -> Windows Wireless Drivers or something to that effect
e) Choose the Windows XP drivers for the WMP300N. The Vista drivers, I found, do NOT work with ndiswrapper.

That's how I got the wireless card to work. After that, Wireless appeared as an option in Network Manager and I was able to see networks around me.

Still no luck on connecting to a protected network, however. I took off protection for now. I live in a small area so I doubt any haxors are gonna wreck havoc but still... I'd rather be protected.

---

