---
title: "Dell Studio 1535 and Dell 1397 wifi card"
date: 2008-10-25
forum: Networking &amp; Wireless
---

### Post by Peshk0 on 2008-10-25
Hello guys! I am a bit confused. Here is the situation. I bought brand new Dell studio 1535 with Dell 1397 wifi card. After fresh installation of Ubuntu 8.04 and installing all the upgrades the lshw -C network prints Broadcom bcm4310 usb controller driver and there was no wireless. I remove the bcm43xx from the blacklist and replace it with b43. After that i choose Broadcom STA wireless driver from Restricted Hardware and it works well. I have wireless, but when i type again lshw -C network it prints BCM4312. I'm wondering which chipset version is the correct because Kismet doesn't work with bcm4310 but bcm4312.

---

### Post by Ayuthia on 2008-10-25
> **Peshk0 said:**
> Hello guys! I am a bit confused. Here is the situation. I bought brand new Dell studio 1535 with Dell 1397 wifi card. After fresh installation of Ubuntu 8.04 and installing all the upgrades the lshw -C network prints Broadcom bcm4310 usb controller driver and there was no wireless. I remove the bcm43xx from the blacklist and replace it with b43. After that i choose Broadcom STA wireless driver from Restricted Hardware and it works well. I have wireless, but when i type again lshw -C network it prints BCM4312. I'm wondering which chipset version is the correct because Kismet doesn't work with bcm4310 but bcm4312.

Your card is really a bcm4312 [14e4:4315].  However, I don't think that it works with kismet.  The card works with the wl driver and not the b43.  I read from someone that Monitor mode works with the wl driver, but it does not do packet injection.

---

### Post by sleepingpeace on 2009-09-22
Anyone know if this card does support monitor mode?

---

### Post by Ayuthia on 2009-09-22
> **sleepingpeace said:**
> Anyone know if this card does support monitor mode?

I think that it might starting with the 2.6.32 kernel.  The b43 developers have this card working in the 2.6.32 kernel and there is a way to compile them for kernels 2.6.27, but I have not checked out how to do it yet.  You might check out the OpenSUSE forums and see if you can find a post by lwfinger or Larry Finger for the 4315 card.  He might be able to help you get it compiled for Ubuntu.  If I recall correctly, he and Gábor Stefanik worked on getting the card to work.

---

