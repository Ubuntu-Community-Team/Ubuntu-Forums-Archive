---
title: "DLink DWL-G520+ works, but no WPA ?"
date: 2006-10-16
forum: Networking &amp; Wireless
---

### Post by PhW139 on 2006-10-16
Hi,

After a successful installation of Ubuntu 6.06 on a laptop with a IPW2100 wireless card, I've tried to do the same on a desktop with the DLink DWL-G520+.
A little search on the web gives me a native solution in Ubuntu 6.06 (without using ndiswrapper).

The problem is a buggy firmware of the chipset acx111 on which this card is based.
The solution is thus to use an older firmware, this can be done as decribed hereunder.

1. Check if drivers/firmwares are installed.

```
sudo apt-get install linux-restricted-modules-`(uname -r)`
```

2. Change the symbolic link to the correct driver.

```
sudo ln -s -f /lib/firmware/`(uname -r)`/acx/1.2.1.34/tiacx111c16 /lib/firmware/`(uname -r)`/acx/default/tiacx111c16
```

WARNING : if you update the kernel, you'll have to change the symbolic link again ! I guess it should be possible to avoid doing this for each kernel update, but I don't know how.

Don't forget to install 'network-manager-gnome', normally 'wpasupplicant' should be already installed or will be installed as a dependance of 'network-manager'. Anyway, the following 3 packages have to be installed :

. network-manager
. network-manager-gnome (or knetworkmanager for KDE)
. wpasupplicant

At this point, and after a restart (or logout/login), you should see wifi network(s) in the network manager applet.

But, I still have a problem, because only WEP is available.
I have to say that WPA works fine with Ubuntu on my laptop, and with a commercial OS on my desktop with the same DWL-G520+ card.

The strange point is that :

```
ps -ax | grep wpa
```

on my laptop shows that wpasupplicant is a running process, but on my desktop, this not the case. Knowing that wpasupplicant is a daemon, it seems logical that WPA is not available as a choice in network manager if not running.

My question is thus : why this daemon doesn't start on my desktop ?
As far as I remember, I've done nothing special on my laptop to start (automatically) this daemon.

---

### Post by PhW139 on 2006-10-19
Up

---

