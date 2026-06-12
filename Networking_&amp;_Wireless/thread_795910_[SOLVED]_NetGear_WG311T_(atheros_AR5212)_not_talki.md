---
title: "[SOLVED] NetGear WG311T (atheros AR5212) not talking"
date: 2008-05-15
forum: Networking &amp; Wireless
---

### Post by spicewoodleo on 2008-05-15
Favor for a friend that has turned into a nightmare...Shouldn't be.. this is a popular card!  Here goes:

Fresh install of Ubuntu 8.04 on a Dell B110 system with a NetGear WG311T.
lspci -v gives: (I would copy/paste, but that is hard to do on a machine with no network connectivity, so here is what I deem important):

   168c:0013 (rev 01) Atheros 5212/5213

I first spent time fiddling with security settings/keys, etc.  Nothing.  The card is getting loaded and seen in system/administration/networking.  I tried roaming/dhcp/and static ip. Nothing.  I did see that my wireless network was seen by the card, so -something- is working in there.  I then went and installed ndiswrapper, installed the windows driver for it (taken from the windows-side of the dual-boot where this adapter works like a champ), and blacklisted ath_pci and ath_hal in /etc/modprobe.d/blacklist.  Nothing.  I then removed the driver from ndiswrapper, and un-blacklisted the ath_* drivers, now I have no adapter appearing anywhere.  I have somehow painted myself in a corner getting this $%%* thing to work.  It took me 5min to get it running on the XP side of this dual boot.  What gives? and how do I get back to at least being able to see the adapter, so that I might try other options.

---

### Post by spicewoodleo on 2008-05-16
I'll rephrase the question:   Basic networking 101: How do I get Ubuntu 8.04 to "see" my WG311T wireless adapter again.  It was once there, before I installed ndiswrapper and blacklisted the two ath_* drivers.  I unblacklisted the drivers and un-installed ndiswrapper, and now, no ath0.  Nothing in dmesg, nothing that iw* tools see.  How do I get the primordial networking back?  At this point I want to try wicd, as I've seen others have successs with it.

I will be most grateful to anyone that helps.  Thanks.

---

### Post by spicewoodleo on 2008-05-16
So, I've painted myself back out of the corner.  This is what I had to do:

1> Comment out (or remove file) entries in /etc/modprobe.d/ndiswrapper that were redirecting driver load upon finding a particular pci device.  I'm wondering if just removing that file will do the same trick.

2> Re-configure the network adapter via system/administration/network (I did dhcp and static...both work).

3> Install Wicd use it once and for some reason, everything works after that. (?).

I honestly don't know exactly what the magic is, but it is working now.

There definitely is something amiss with wireless networking with 8.04.
Ubuntu claims that there is "out of the box" support for wg311t.  I'd rather say it is "out of the cage" support.

Thanks, and I hope this helps others.

---

