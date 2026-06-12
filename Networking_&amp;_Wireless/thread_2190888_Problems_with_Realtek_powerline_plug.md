---
title: "Problems with Realtek powerline plug"
date: 2013-11-29
forum: Networking &amp; Wireless
---

### Post by ntqmqtlh on 2013-11-29
Hej friends, I am currently having a frustrating problem with my Powerline Plug.


"Ethernet controller: RealTek Semiconductor Co., Ltd RTL8111/8168B PCI Express Gigabit Ethernet Controller (rev 06)"


I have tried (and take my word on this) several-tens of methods to try and fix the current status of it not working (when it was working perfectly fine for the following three days).


I am running Ubuntu 10.04.4, and yes I am aware that it is 'end of life', with no further updates - which is no general concern of mine in terms of productivity.


I tried following these tutorials several times over, with no success:


[https://bbs.archlinux.org/viewtopic.php?id=101836](https://bbs.archlinux.org/viewtopic.php?id=101836)
[http://sikpigs.wordpress.com/2013/10/07/realtek-r8168-on-ubuntu-12-04/](http://sikpigs.wordpress.com/2013/10/07/realtek-r8168-on-ubuntu-12-04/)


and I've clicked on every indexed link for the first ten pages on Google, trying to find solutions (all of which) have not worked.


ifconfig:


ifconfig did, but no longer seems to recognize that there is a plug (which has been caused due to the methods i've tried - wrong package supposabley).


Lspci -V:


```
03:00.0 Ethernet controller: RealTek Semiconductor Co., Ltd RTL8111/8168B PCI Express Gigabit Ethernet Controller (rev 06)
    Subsystem: ASUSTeK Computer Inc. Device 8432
    Flags: fast devsel, IRQ 18
    I/O ports at e800 [size=256]
    Memory at fdfff000 (64-bit, prefetchable) [size=k]
    Memory at fdff8000 (64-bit, prefetchable) [size=16k]
    Capabilities: <access denied>
    Kernel modules: r8168

```

I appreciate any help, and I'm aware that there's many reports of this card being buggy - but some people have fixed the problem, with me sitting here with no success.


Thanks.

**Edit: I also tried the plug on another computer and it worked, so it's not the plug.**

---

### Post by varunendra on 2013-12-01
> **ntqmqtlh said:**
> I tried following these tutorials several times over, with no success:

[https://bbs.archlinux.org/viewtopic.php?id=101836](https://bbs.archlinux.org/viewtopic.php?id=101836)
....
....
```

    Kernel modules: r8168

```

It seems you have already tried what I suggested in [post=12858051]this post[/post]. The OP in that thread never confirmed if it worked or not. Does ethtool or "lshw -C network" shows the "link=yes"?

Maybe try resetting your BIOS (if it is not a UEFI based system, otherwise it may reset the boot configuration too).

Please confirm if you tried these, and if none helped, please post your output of "sudo ethtool eth0", although it doesn't seem to help much with this card.

---

