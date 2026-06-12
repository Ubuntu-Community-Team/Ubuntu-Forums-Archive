---
title: "DWA-643 (chipset AR5418) on Hardy"
date: 2008-05-07
forum: Networking &amp; Wireless
---

### Post by uado on 2008-05-07
I have recently upgraded to 8.04 on my XPS M1330 and all is well except my DWA-643. It carries an AR5418 chipset. I just can't get it to appear in ifconfig. The Card appears in lspci. I had problems with it in 7.10, but the following commands resolved that.

Here's a list of commands I followed:
$ sudo svn checkout [http://svn.madwifi.org/madwifi/trunk](http://svn.madwifi.org/madwifi/trunk)
$ cd trunk
$ make
$ sudo make install
$ sudo modprobe ath_pci

Any suggestions?

Cheers!

---

### Post by djjorgen on 2008-05-08
Hi, I have the m1330 with dwa-643.

I followed the tutorials below and my card shows up in ifconfig:

check this out: [http://madwifi.org/wiki/UserDocs/GettingMadwifi]("http://madwifi.org/wiki/UserDocs/GettingMadwifi")
(I got the latest svn release with subversion and remember to remove old versions!)

**edit:** I reverted back to revision 3375, because monitor mode was not working with later releases.

and you might wanna check out: [http://madwifi.org/wiki/UserDocs/FirstTimeHowTo]("http://madwifi.org/wiki/UserDocs/FirstTimeHowTo") to make the card appear in ifconfig:)

Jørgen

---

### Post by uado on 2008-05-10
Cheers djjorgen, I'll give it a go and let you know how I get on!

---

### Post by uado on 2008-05-10
Yeah, baby!

Cheers for the pointers, djjorgen! Looks to be happy now.

:KS

---

### Post by [Rizzo] on 2008-06-14
Actually, all you have to do is install the xp driver from the disc into the NDISwrapper, and the card starts working.


**1.)** Copy driver net5416.inf from the installation disc to your Home folder

**2.)** Open NDISwrapper, and choose the driver. It should say "**Hardware Present: Yes**"

**3.)** After it's installed, the orange activity LED should start blinking.

This was tested by me using Linux Mint 5 (Elyssa), which is based on Ubuntu 8.04 Hardy Heron. No other drivers or console commands were needed, and should work in Ubuntu 8.04 as well.

---

