---
title: "Success with Linksys wmp411, Broadcom 4303 wireless"
date: 2007-11-18
forum: Networking &amp; Wireless
---

### Post by rrwood on 2007-11-18
I got my Linksys wmp11 wireless card working with Ubuntu 7.10.  There are a LOT of postings and confusion about this, so I presume that this info might be appreciated by others trying to do the same.  I did a fair bit of thrashing at first, but it turns out to be pretty simple to get things to work.  I've tried to remember exactly what I did, but may have omitted some things below (sorry).


In my case, the most helpful doc was here:

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty")


Since I didn't have functional networking on my target machine, I first had to download the bcm43xx-fwcutter package.  Seems odd that this package is not on the 7.10 install CD, but maybe I'm wrong on that.  Anyway, I grabbed it from here:

[http://packages.ubuntu.com/feisty/utils/bcm43xx-fwcutter]("http://packages.ubuntu.com/feisty/utils/bcm43xx-fwcutter")


Next up, I needed the firmware for the wmp11 card.  It can be had here:

[http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o]("http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o")

Save the wl_apsta file somewhere convenient so you can run the following command line to extract the firmware:

[FONT="Courier New"]sudo bcm43xx-fwcutter -w /lib/firmware/`uname -r`  wl_apsta-3.130.20.0.o[/FONT]


Next, I edited /etc/modules to remove the (unnecessary?) reference to ndiswrapper and added the reference to bcm43xx.  My /etc/modules file looks like this now (some lines omitted for clarity):

[FONT="Courier New"]# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

#ndiswrapper
bcm43xx
[/FONT]

After this, I did a [FONT="Courier New"]"depmod -a"[/FONT] and then rebooted.

Once I rebooted, things were working well enough that I could use the Network control panel (System -> Administration -> Network).  I configured the adapter, and WEP is working fine.


By the way, lspci returns the following info about my card:

00:0a.0 Network controller [0280]: Broadcom Corporation BCM4303 802.11b Wireless LAN Controller [14e4:4301] (rev 02)



(Note-- the forum software seems to be doing funny things with the URLs I've included.  Not sure if they'll show up correctly or not after all.  Sorry about that.)

---

