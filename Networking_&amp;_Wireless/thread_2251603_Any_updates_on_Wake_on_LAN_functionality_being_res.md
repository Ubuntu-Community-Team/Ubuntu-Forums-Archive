---
title: "Any updates on Wake on LAN functionality being restored for Atheros cards?"
date: 2014-11-05
forum: Networking &amp; Wireless
---

### Post by gfunkdave on 2014-11-05
My Ubuntu box has an Atheros AR8161 ethernet controller that I know for a fact supports WoL because it used to work just fine. But since upgrading to 14.04 a few months back, I don't have WoL functionality. **ethtool eth0** doesn't show any WoL ability. It looks like this was [deliberately removed from the Atheros driver]("http://www.linuxquestions.org/questions/linux-networking-3/qualcomm-atheros-ar8171-wake-on-lan-issues-4175491464/").

Leaving aside the various names I want to call the person who did this, does anyone know when support will be re-added for this? Building a new version of the driver is something I'm not really comfortable with doing, though I suppose I could try it. 

Thanks for any help here.

---

### Post by weatherman2 on 2014-11-05
The last post in the thread you linked to includes a method to extract the old driver from the 3.10 kernel and build it/use it with the current kernel. Sounds like it would work with Ubuntu 14.04.

---

### Post by gfunkdave on 2014-11-05
Thanks - yeah, I've never done it before. Do I need to use the driver from the kernel that I'm using, or can I just use the 3.10 kernel's driver? I think the whole point is to use the 3.10 kernel's driver, but I've never done this before and just want to make sure. Right?

---

### Post by chili555 on 2014-11-05
If you need any guidance translating the Fedora method into Ubuntu-ese, please post back. I might know a guy who can help.

Additional information: [http://git.kernel.org/cgit/linux/kernel/git/torvalds/linux.git/commit/?id=bc2bebe8de8ed4ba6482c9cc370b0dd72ffe8cd2](http://git.kernel.org/cgit/linux/kernel/git/torvalds/linux.git/commit/?id=bc2bebe8de8ed4ba6482c9cc370b0dd72ffe8cd2)> **alx: remove WoL support**
Unfortunately, WoL is broken and the system will immediately
resume after suspending, and I can't seem to figure out why.
Remove WoL support until the issue can be found.

---

### Post by gfunkdave on 2014-11-05
Thanks. I took the plunge and recompiled as per the link in my original post. Everything seemed to work fine, but ethtool still doesn't show wake on lan after rebooting with the newly compiled driver from kernel 3.10.59. 

Any ideas, anyone?

I still don't understand why this Johannes Berg person saw fit to entirely disable a basic feature because one use case didn't work and he couldn't figure out the problem. It's like curing the disease by killing the patient - and I don't understand why nobody else called him out for it.

---

### Post by chili555 on 2014-11-05
> entirely disable a basic feature because one use case didn't work and he couldn't figure out the problemGenerally, revisions to the kernel aren't accepted based on one use case but rather multiple users adding to bug reports. I haven't taken the time to thoroughly research this exact case, but I've seen and filed enough bug reports to be confident that the change was not because "one use case didn't work."

This Johannes Berg person is one of the authors of the driver module:```
chili@T410:~$ modinfo alx
filename:       /lib/modules/3.16.0-24-generic/kernel/drivers/net/ethernet/atheros/alx/alx.ko
license:        GPL
description:    Qualcomm Atheros(R) AR816x/AR817x PCI-E Ethernet Network Driver
author:         Qualcomm Corporation, <nic-devel@qualcomm.com>
[COLOR="#FF0000"]author:         Johannes Berg <johannes@sipsolutions.net>[/COLOR]

```

---

### Post by gfunkdave on 2014-11-05
Interesting, thanks.

OK, I tried running **patch ethtool.c < alx.patch** from the patch at the [Linux bug report]("https://bugzilla.kernel.org/show_bug.cgi?id=61651") but I get a bunch of errors. Any help in how to patch the ethtool.c file?

```
david@dalton:~/Desktop/linux-3.17.2/drivers/net/ethernet/atheros/alx$ patch ethtool.c < ~/Desktop/alx.patch
patching file ethtool.c
patching file ethtool.c
Hunk #1 FAILED at 332.
Hunk #2 FAILED at 848.
Hunk #3 FAILED at 920.
Hunk #4 FAILED at 1031.
4 out of 4 hunks FAILED -- saving rejects to file ethtool.c.rej
patching file ethtool.c
Hunk #1 FAILED at 485.
Hunk #2 FAILED at 547.
Hunk #3 FAILED at 560.
3 out of 3 hunks FAILED -- saving rejects to file ethtool.c.rej
patching file ethtool.c
Hunk #1 FAILED at 51.
Hunk #2 FAILED at 706.
Hunk #3 FAILED at 960.
Hunk #4 FAILED at 1377.
Hunk #5 FAILED at 1420.
Hunk #6 FAILED at 1433.
Hunk #7 FAILED at 1492.
Hunk #8 FAILED at 1539.
8 out of 8 hunks FAILED -- saving rejects to file ethtool.c.rej

```

---

### Post by gfunkdave on 2014-11-05
duplicate

---

### Post by gfunkdave on 2014-11-05
duplicate

---

### Post by chili555 on 2014-11-06
>  Any help in how to patch the ethtool.c file?I haven't any idea; however, I do know that you'd need to apply the patch before the driver is compiled from source, and not to an already built and in place module.

I suppose an intrepid driver dawg could start with backports: [http://www.kernel.org/pub/linux/kernel/projects/backports/stable/v3.17.1/backports-3.17.1-1.tar.xz](http://www.kernel.org/pub/linux/kernel/projects/backports/stable/v3.17.1/backports-3.17.1-1.tar.xz)  And then drill down to drivers/net/ethernet/atheros/alx/ethtool.c and copy and paste the changes in line-by-line and then compile, watching carefully for errors, warnings, etc.

Aren't more suitable ethernet NICs available that WOL out of the box?

---

### Post by gfunkdave on 2014-11-06
So, I finally got this working. And to be clear, this card supports WOL out of the box. They just disabled support for it in the Ubuntu drivers.

I had to apply the patch in the Linux bug tracker to the source from the 3.17 kernel's driver (the same version as the patch), then make.

Apparently, there is something messed up in the kernel that makes the updated driver not work with WOL even though the updated driver is loaded at startup.  So I had to add a startup script that does 

```

modprobe -r alx
modprobe alx

```

And now it works.

---

### Post by chili555 on 2014-11-06
Glad it's working!

---

### Post by Bartimeus on 2015-01-08
Do you think there is any chance you could post a step by step of what you did? I am somewhat lost between this thread and the other one.

---

