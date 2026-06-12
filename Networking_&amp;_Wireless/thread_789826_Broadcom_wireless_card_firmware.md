---
title: "Broadcom wireless card firmware"
date: 2008-05-10
forum: Networking &amp; Wireless
---

### Post by matthewbpt on 2008-05-10
I have a broadcom BCM4312 802.11a/b/g wireless card in my hp dv9000 laptop, and to make it work I have to install a new firware, fwcutter I think its called. I'm wondering if installing new firmware will affect its function in vista, because I have ubuntu and vista set to dualboot on my system.

---

### Post by Ayuthia on 2008-05-10
> **matthewbpt said:**
> I have a broadcom BCM4312 802.11a/b/g wireless card in my hp dv9000 laptop, and to make it work I have to install a new firware, fwcutter I think its called. I'm wondering if installing new firmware will affect its function in vista, because I have ubuntu and vista set to dualboot on my system.
I have a dv6338 and multi-boot (Arch, Kubuntu, Gentoo, and Vista) and I have never had any problems with Vista.

However, you have a 4312 card.  You might want to go to the Terminal and check lspci -nn.  The rev 02 cards are not working with the 2.6.24-16 kernel with the b43 driver (b43-fwcutter method).  You will need to look into the NDISwrapper option.  Here is a link that most people have success: [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

---

### Post by jlandaw on 2008-05-10
Check my thread out, im sure it will work

[Broadcom wifi on a HP dv9000]("http://ubuntuforums.org/showthread.php?t=769990")

---

### Post by matthewbpt on 2008-05-11
thanks a million it worked perfectly!
but now my firefox runs at full speed, up to 2 megs per second, but downloading files with the terminal and package manager peaks at 12 KB/s. Why is it so slow? This is both with wireless and using ethernet, right now the package manager is downloading a file at only 6000 B/s!

---

