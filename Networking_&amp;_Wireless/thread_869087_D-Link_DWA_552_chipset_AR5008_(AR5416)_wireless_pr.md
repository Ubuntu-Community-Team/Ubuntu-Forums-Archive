---
title: "D-Link DWA 552 chipset AR5008 (AR5416) wireless problems in Ubuntu (Mint) using madwi"
date: 2008-07-24
forum: Networking &amp; Wireless
---

### Post by awwong on 2008-07-24
I'm suspecting that my problems may be due to the updates to the madwifi trunk breaking compatibility with the AR5008/AR5416 chipset, and not because of Ubuntu/Mint Hardy Heron.  And yes, my wireless works fine under Windows XP.

I've noticed in the madwifi tickets that AR5008/AR5416 wireless was functioning and had been broken in the past due to updates but the regressions were fixed.  Also, in my previous install on 2008.06.22, my D-Link DWA-552 was working with wireless G with Linux Mint 4 (Ubuntu Gutsy) and the madwifi drivers.  Also, I connected with the Gnome Network Manager, but I do find that wicd remembers WAP2 passwords even if connections don't occur.

So far I've been able to see my WAP2 protected D-Link DIR-655 router - receive transmissions - but not able to send any data, i.e., trying to connect to the router.  I suspect that if I find a snapshot close to the date where I or others got their wifi working, I will be in business.  Unfortunately, I've messed up my kernel and it's refusing to install the ath0 drivers (possibly due to compiling older madwifi snapshots over newer ones) so I'm going to reinstall Gutsy (Mint 4).  I may also try this with Hardy Heron, since I recall others had it working in that and in other distros; see [http://madwifi.org/wiki/Compatibility/D-Link#DWA-552](http://madwifi.org/wiki/Compatibility/D-Link#DWA-552).  If I have any success, I'll report back.

DWA-552 reported working from various sources (googled)
r3123 - ubuntu 7.10 - by Komadyret
r3620 - ubuntu 8.04 x86_64, Gentoo - madwifi
r3658 - ubuntu 8.04 x86_64, Gentoo - madwifi

Links:
madwifi trunk snapshots for compiling into the kernel:
[URL="http://snapshots.madwifi.org/madwifi-trunk/"]http://snapshots.madwifi.org/madwifi-trunk/
[/URL]
madwifi D-Link compatibility page (DWA-552):
[http://madwifi.org/wiki/Compatibility/D-Link#DWA-552](http://madwifi.org/wiki/Compatibility/D-Link#DWA-552)

zeesson's instructions on how to connect the DWA-552 with the madwifi drivers:
Mint forum:
[http://linuxmint.com/forum/viewtopic.php?f=53&t=10209](http://linuxmint.com/forum/viewtopic.php?f=53&t=10209)
Ubuntu forum (archived but more replies):
[http://www.ubuntu-forum.com/showthread.php?t=718244](http://www.ubuntu-forum.com/showthread.php?t=718244)

***Update***

Great news!  Atheros has released free linux drivers for 802.11n devices.  Supported chips will include:

    * AR5418+AR5133
    * AR5416+AR5133
    * AR5416+AR2133
    * AR9160
    * AR9280
    * AR9281

The news on the madwifi site:
[http://madwifi.org/wiki/news/20080725/ath9k-atheros-unveils-free-linux-driver-for](http://madwifi.org/wiki/news/20080725/ath9k-atheros-unveils-free-linux-driver-for)

More info:
[http://wireless.kernel.org/en/users/Drivers/ath9k](http://wireless.kernel.org/en/users/Drivers/ath9k)

I guess I can rest easy tonight knowing that this is being developed with Atheros!

***Update #2***

Tutorial of how to install the ath9k drivers (I have not been able to successfully compile the kernel to work with the ath9k drivers, yet):
[http://www.thinkwiki.org/wiki/How_to_install_the_development_version_of_atk9k](http://www.thinkwiki.org/wiki/How_to_install_the_development_version_of_atk9k)
The driver will be embedded in either the .27 or .28 kernel, so if I can't get this working, hopefully I won't have to wait too long...

---

### Post by -::Bas::- on 2008-10-10
Since Intrepid Ibex and the kernel it uses, this Atheros AR5008 card is supported bij default, check this summary here,
[http://kernelnewbies.org/Linux_2_6_27](http://kernelnewbies.org/Linux_2_6_27)

---

### Post by awwong on 2008-11-11
I find the ath9k driver is still not stable with the current kernel (I am still using the same hardware).  I am hopeful the driver will mature in the near future.

---

