---
title: "Broadcom 43xx was working in Hardy, not in Intrepid"
date: 2008-11-01
forum: Networking &amp; Wireless
---

### Post by Kaseas on 2008-11-01
I have an HP Pavilion with a Broadcom 4311 wireless card, which was working before, but now it is not anymore.

The light is on, however I cannot connect to my network. It shows up when I run "sudo iwlist scan" but I still can't connect to it. Also I cannot start nm-applet, and things have otherwise gone horribly wrong after the upgrade. My WinXp -> Ultimate upgrade went better than this :S.

---

### Post by Kaseas on 2008-11-02
Upon investigation, I believe that the problem is in not being able to see nm-applet. When running "sudo nm-applet" I get an error about NetworkManagerUserSettings service being taken.

---

### Post by Dirk_Gently on 2008-11-02
You didn't state if you were using the B43 driver built into the kernel or ndiswrapper with Hardy. But since you mentioned nm-applet I presume it was the b43?!

nm-applet is in the gnome-network-manager packet btw. you might try to re-install it with apt-get.

Have you considered following one of the numerous guides here discussing how to get Broadcom Wireless working by using ndiswrapper? I have a BCM4306 and it works for me. 

regards
DG

---

