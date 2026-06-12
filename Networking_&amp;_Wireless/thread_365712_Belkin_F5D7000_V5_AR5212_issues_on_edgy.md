---
title: "Belkin F5D7000 V5 AR5212 issues on edgy"
date: 2007-02-20
forum: Networking &amp; Wireless
---

### Post by dreadbrazen on 2007-02-20
Hey guys...

So my wireless card had been working decently until the new kernel (2.6.17-11).  I've looked through the thread, but I'm having a different issue entirely.  My card WILL connect to my wireless connection, it's just very finicky and receives a weak signal.

Under windows, the card functions properly most of the time.  4-5 bars of connectivity.  Occasionally there are some connection hickups, but it seems to work well enough.  Edgy, however, gives me nothing but problems.  It always had a fairly weak signal, but now I lose my connection far too frequently.  I've been pouring over pages and pages of related material, but it seems like I'm the only one having the problem.  Any help would be appreciated.

nForce 570 Slit-A
Intel Pentium 840 Dual-Core
nVidia 7900GT
Belkin F5D7000 Ver.5 (AR5212 Chipset - madwifi/restricted-modules)
2.6.17-11 on Kubuntu 6.10 Edgy

---

### Post by gradedcheese on 2007-02-21
I suggest that you build your own madwifi driver, using the latest source.  Most likely, there's something wrong with the driver you're using and it's probably now fixed.  If you're nervous about compiling it, it's actually not very hard to do.  You'll need a couple packages:

```

sudo apt-get install build-essential linux-headers-`uname -r`

```
(or run "uname -r" to get the kernel name and then install linux-headers-put_name_here)

Here's a HOWTO about madwifi:
[http://madwifi.org/wiki/UserDocs/FirstTimeHowTo](http://madwifi.org/wiki/UserDocs/FirstTimeHowTo)

---

