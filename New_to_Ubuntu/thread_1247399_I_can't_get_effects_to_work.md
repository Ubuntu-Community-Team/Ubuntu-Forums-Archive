---
title: "I can't get effects to work"
date: 2009-08-22
forum: New to Ubuntu
---

### Post by woazala on 2009-08-22
Hi 
I've just install Ubuntu 9.04 and I can't make the effects works.
 
my video card is ok?
[I][COLOR=black][FONT=Verdana]display UNCLAIMED 
description: VGA compatible controller
product: Mobility Radeon HD 3450
vendor: ATI Technologies Inc
physical id: 0
bus info: pci@0000:01:00.0
version: 00
width: 64 bits
clock: 33MHz
capabilities: pm pciexpress msi bus_master cap_list
configuration: latency=0[/FONT][/COLOR][/I]
*[COLOR=black][FONT=Verdana][/FONT][/COLOR]* 
*[COLOR=black][FONT=Verdana]please answer[/FONT][/COLOR]*

---

### Post by cariboo on 2009-08-22
A bump for the move

---

### Post by powel212 on 2009-08-22
Right click the desktop, select change desktop background then go to visual effects and select extra.

then in add/Remove install compiz controls "compizconfig settings manager"

if that doesn't work go to system\administration\hardware drivers and see if you have the restricted driver installed for your video card.

If that doesn't work it may be that there is no restricted driver available for your video card. In which case you are stuck without the desktop effects until you upgrade your video card. I recommend Nvidia Cards because they are best supported under Ubuntu.

I hope that helps

Powel

---

### Post by inobe on 2009-08-22
actually nvidia cards are better supported by nvidia meaning their drivers work better for for all platforms, the operating system has nothing to do with proprietary drivers.


ati released opensource drivers' however they are not very good, their proprietary linux drivers have serious issues too in some cases.

i don't know why ati release powerful video cards and produce horrid drivers support.


so far nvidia seems to release the best driver support.

---

