---
title: "supported wireless in gutsy."
date: 2007-07-18
forum: Networking &amp; Wireless
---

### Post by edwin.e.johnson on 2007-07-18
ok i just want to start this off with this question.


what cards are supported out of the known "problem cards"

like the wusb54gc and the broadcom 4318 airforce one?

---

### Post by edwin.e.johnson on 2007-07-20
noone has any ideas?

---

### Post by darrenm on 2007-07-21
I was just wondering if anyone knows if the bcm43xx is better supported in Gutsy? I'd love to dump ndiswrapper.

---

### Post by n00bWillingToLearn on 2007-07-21
The bcm43xx drivers are constantly improving, a change worth noting is that in Gutsy Restricted Manager suggests installation of bcm43xx-fwcutter for people who have a broadcom chipset  so hopefully people won't have to research to find out that that is the package they need to get the native drivers to work. But the bcm43xx driver still does not support all bcm43xx cards, and may not work as well as NDISwrapper for others ( though the opposite is also sometimes true ). Here is a list of chipsets currently supported by the newest upstream release of bcm43xx [http://bcm43xx.berlios.de/?go=devices](http://bcm43xx.berlios.de/?go=devices)

---

### Post by n00bWillingToLearn on 2007-07-21
My comment below was meant to be a reply to you.

---

### Post by darrenm on 2007-07-22
Well, my bcm4318 didnt work at all. So I upgraded to Gutsy and suddenly it works perfectly with bcm43xx module. I could previously only get it to work with ndiswrapper and network-manager.

---

### Post by edwin.e.johnson on 2007-07-26
so is the wusb54gc / rt73 card going to work with gutsy?

anyone know??

---

### Post by darrenm on 2007-07-26
What chipset is it?

---

