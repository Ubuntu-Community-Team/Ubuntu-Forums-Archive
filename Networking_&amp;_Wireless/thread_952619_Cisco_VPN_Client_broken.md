---
title: "Cisco VPN Client broken"
date: 2008-10-19
forum: Networking &amp; Wireless
---

### Post by indygeek79 on 2008-10-19
I had the Cisco VPN Client working just fine with Ubuntu 8.04, Kernel 2.6.24-19.

The other day it updated and installed 2.6.24-21.

After this install the VPN Client will no longer connect.  I have uninstalled it with the uninstall script that comes with it.  Done a full reinstall under the new kernel but no luck.

If I boot to the -19 kernel with Grub, VPN works just fine.  

Is there anything I can do to fix this?


Let me just say that I am pretty new to Linux.

---

### Post by indygeek79 on 2008-10-22
Can anyone offer any assistance?

---

### Post by charlvj on 2008-10-22
No assistance unfortunately, but I can confirm the same problem on my computer: with latest kernel I get the error: Remote peer is no longer available. With the previous kernel it works fine.
I have tried everything I could think of. I found websites with advice on how to handle this kind of error, but none of the advice worked. I did recompile the thing, but to no avail.

---

### Post by indygeek79 on 2008-10-23
I have probably been the the same sites as you have on this.  I have followed everything that I could find on a way to fix this but nothing has helped with the newer kernel.

For now I have setup Grub to auto-boot the older kernel so I can still use my VPN when I am at home.

In case it would help at all, here are details on my laptop:

Dell Precision M65 Laptop
CPU - Intel T2300
WLAN - Intel 3945ABG
Video - nVidia FX350M

---

### Post by sowelie on 2008-11-06
Anyone find a fix for this?

---

### Post by indygeek79 on 2008-11-07
Not exactly.  I am staying with an older kernel.

I did how ever put in the 8.10 cd and run Live from it.  Installed the Cisco VPN and was able to connect. 

The 8.10 that I downloaded was running 2.6.27  ( i think )

Currently I went back to an even older kernel right now.  2.6.24.-16  I am trying out Mint an ubuntu based distro.

---

