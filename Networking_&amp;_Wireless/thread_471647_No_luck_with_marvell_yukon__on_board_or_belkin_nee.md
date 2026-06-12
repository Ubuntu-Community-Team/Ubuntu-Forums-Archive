---
title: "No luck with marvell yukon  on board or belkin need hlep"
date: 2007-06-12
forum: Networking &amp; Wireless
---

### Post by SirBob1701 on 2007-06-12
Hey guys I just replaced my motherboard (warrenty) with an Asus A8N32-SLI Deluxe.  It has two Marvell Yukon NICs (a Marvell 88E8053 10/100/1000Mbps PCI Express and a Marvell 88E1111 10/100/1000Mbps Integrated LAN) on a Nvidia NForce 4 chipset (CK804 controller) I also reformated to feisty and tried compliling the Marvell drivers from the website along with any other option I could find in the forums (Lots of transfers to CD and flash drive since it has no network becuase I can't get my wireless working either (RTL 8185L in form of a belkin F5D7000 v 7000).  Any help anyone can give me would be appreciated.  Since i'm now at work I wont be able to test anything you suggest for a while but I will get back to you on it.  Thanks for all your help.

---

### Post by SirBob1701 on 2007-06-13
Installed the 88E8053 driver from marvells site and now it connects and stays connected but cna't browse and when i ping google.com or a local ip i get nothing.  Also the lspci has no reference to my alt marvell card only to nvidia network controller CK804 which is part of the nforce4 chipset.  This is really buggin me and i might have to go back to the dreaded xp if i can't get it to work soon.  (need the desktop for a school project) any help appreciated

---

### Post by Mark Phelps on 2007-06-19
I have the same motherboard and both the onboard NICs work fine without installing any drivers.

Have you checked the BIOS to ensure that you have both NICs enabled?

I'm not at my Linux machine, so I'm not certain of the details, but when I played around with both NICs, I noticed that the network icon in the upper right portion of the desktop changed its options.  When the network was connected, I was able to get setting info by right-clicking the icon.

Linux thinks the Nvidia LAN is eth0, and the Marvell LAN is eth1. Either one should work for you and since they're both GB LANs, the choice of which to use is yours.  I've chosen to use the marvell LAN because I'm triple-booting (Xp, Vista, Ubuntu) and the marvell LAN provides more stable performance.

---

### Post by SirBob1701 on 2007-06-25
It turned out to be the network cabled was messed up.  i hate the things i gotta fish the walls its a must now.

---

