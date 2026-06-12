---
title: "ath0 no longer recognized"
date: 2007-05-28
forum: Networking &amp; Wireless
---

### Post by rjfioravanti on 2007-05-28
Hi Everyone

I was downloading updates.. then the fire alarm went off, so it got cancelled in the middle of downloading

Now when I try and connect to the internet it doesnt work

ifconfig -a    (ath0 doesnt even show up here anymore
iwconfg    (ath0 doesnt show up anymore)
iwlist scan   (no results)
ifconfig ath0 (ath0: error fetching interface information: Device not found

if i take the wireless card out and plug it back in my dmesg log shows up that something is going in and out... and if I do (pccardctl ls) it shows up... and it shows up in lspci

My wireless card has always worked out of the box (DLink AirPlus) and I have never needed any ndiswrapper or anything for it

My problem just seems to be that ath0 is no longer recognized

Also the light on the wireless device comes on when i plug it in

Thanks for any help

---

### Post by pacanukeha on 2007-05-28
Hey rj,
one of the updates recently was a kernel upgrade.  If you were using any hand-installed wireless modules they are not copied from kernel to kernel.

I use the madwifi drivers for my atheros card and the latest kernel build 2.6.20-16 doesn't seem compatible (everything compiled and installed but it didn't create the ath0 device ).  I rolled back my kernel to 2.6.20-15 and everything worked again.

You say that yours always worked without any effort, but check your kernel anyway.

good luck.

---

### Post by mlentink on 2007-05-29
> **pacanukeha said:**
> I use the madwifi drivers for my atheros card and the latest kernel build 2.6.20-16 doesn't seem compatible (everything compiled and installed but it didn't create the ath0 device ).  I rolled back my kernel to 2.6.20-15 and everything worked again.

How did you do that (please excuse me if this sounds trivial/obvious, i'm a noob)?

My Sweex (=Atheros) Wifi Card is not recognized anymore after yesterday's kernel update, so I'd really appreciate your help a lot!

Edit: I've rolled back my kernel (learned how in antoher thread) and now it works again

Conclusion: since it was the update to the new kernel,***and noth ing else***, that caused the problem, there must be a bug in the new kernel

---

### Post by mlentink on 2007-05-29
Update:

The Kernel update did not also install the necessary linux-restricted-modules-2.60.16

After installing them, evrythiong is ok again

---

