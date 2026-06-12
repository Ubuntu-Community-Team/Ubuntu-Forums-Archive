---
title: "Safecom SWLC54108 - solved!"
date: 2005-09-18
forum: Networking &amp; Wireless
---

### Post by MrCheese on 2005-09-18
My nightmare of trying to get this card working are over - at least for now. After trying the native kernel module (acx_pci), then ndiswrapper with the XP drivers, I tried Linuxant's driverloader. Success!!

In short driverloader told me that I was short of 2 firmware files which I got from the Dlink 650+ file (available via Linuxant's site). After a bit of messing about with WEP I'm now typing this via my Hoary laptop over the airwaves :)

The license issue on the driverloader doesn't bother me overmuch - it's an oem license thanks to TI's lack of linux support. 10/10 to Linuxant.

The next step is to try ndiswrapper with the same driver/firmware setup. In a few weeks...........

---

### Post by AndyBennett on 2006-05-05
[QUOTE=MrCheese]My nightmare of trying to get this card working are over - at least for now. After trying the native kernel module (acx_pci), then ndiswrapper with the XP drivers, I tried Linuxant's driverloader. Success!!

In short driverloader told me that I was short of 2 firmware files which I got from the Dlink 650+ file (available via Linuxant's site). After a bit of messing about with WEP I'm now typing this via my Hoary laptop over the airwaves :)

The license issue on the driverloader doesn't bother me overmuch - it's an oem license thanks to TI's lack of linux support. 10/10 to Linuxant.

The next step is to try ndiswrapper with the same driver/firmware setup. In a few weeks...........[/QUOTE]
Hi,

I've been through more or less the same loop as you but I seem to have to pay $20 for a license??? At the moment I'm on the 30 day trial of the Linuxant thingy.

Did you ever manage to get it to work with the ndiswrapper?

---

