---
title: "No networking available after install of 14.04"
date: 2014-04-22
forum: Networking &amp; Wireless
---

### Post by graham12 on 2014-04-22
This seems to be becoming a trend with 14.04 ...

I've been using Ubuntu since at least Dapper Drake. My Dell Inspiron 6400 laptop has been running Ubuntu since the day we first bought it. Up until yesterday, it was running 12.10 with both wired and wifi working quite happily.

I completely wiped the existing installation and installed 14.04.

Now I have no networking. Neither wifi (which I expected not to have "out of the box") nor ethernet.

Running "ifconfig" gives detail about "lo" only. No mention of eth... or wlan... at all.

 > lspci -nn -d 14e4:

gives

 > 03:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)
 0b:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)

When I run dmesg (I'll attach the output) it seems to indicate a problem loading the wl module and mentions "kernel BUG".

Is it anything to do with running an SMP kernel ?

As you can imagine, having no networking at all, and transferring stuff via USB stick, is a little limiting!

Can anyone please help ?

Graham.

---

### Post by praseodym on 2014-04-22
Hi,

install this package for wireless:

[http://de.archive.ubuntu.com/ubuntu/pool/multiverse/l/linux-firmware-nonfree/linux-firmware-nonfree_1.14ubuntu1_all.deb](http://de.archive.ubuntu.com/ubuntu/pool/multiverse/l/linux-firmware-nonfree/linux-firmware-nonfree_1.14ubuntu1_all.deb)

For LAN: Load the driver by hand:
```

sudo modprobe -v b44
```
If its working make it permanent:
```

echo b44 | sudo tee -a /etc/modules
```

---

### Post by graham12 on 2014-04-22
praseodym - thanks for the quick reply.

Installed the .deb, rebooted. No effect, sadly.

Running the modprobe (I would had sworn I had a b43, but no matter) prints:

> insmod /lib/modules/3.13.0-24-generic/kernel/drivers/ssb/ssb.ko

and then hangs.

Looking back at my lsmod.txt attachment, I can see that the ssb module is already loaded. This is not what I was expecting, since /etc/modprobe.d/blacklist-bcm43.conf contains the line:

> blacklist ssb

---

### Post by graham12 on 2014-04-22
Solved the problem. Did a search of the forums (again) and this time found:

**[12.04 New Install on old dell laptop, no wired or wireless connection, Broadcom 44's]("http://ubuntuforums.org/showthread.php?t=2158317")**

([http://ubuntuforums.org/showthread.php?t=2158317](http://ubuntuforums.org/showthread.php?t=2158317))

The advice relevant to my case (and this is not the first time I have seen this in these forums) was:

> sudo apt-get remove --purge bcmwl-kernel-source

A reboot later and the ethernet was back working !

And (thanks to [COLOR=#000000]praseodym, earlier), rebooting again without a network cable plugged in showed wireless to be working too !

Happy days.

Someone needs to give that bcmwl-kernel-source a good kicking ...

[/COLOR]

---

