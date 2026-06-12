---
title: "Intel 82566DC-2 Gigabit Problem"
date: 2008-04-27
forum: Networking &amp; Wireless
---

### Post by buhammot on 2008-04-27
Over the past few days, I have been getting rather irritated trying to figure out why me network has been performing quite slowly. I finally found out that my fileserver is only connecting at 100mbit to the network, when everything is gigabit, using CAT6. 

Previously, I believe I was running the64 bit version of Feisty on my server, with the following specs:

Intel DG965WH Mobo (82566DC-2 Network interface)
Core 2 Duo E6300
2GB DDR2
4x320GB Seagate (Raid5)

And everything was running smppthly, generally getting network transfer speeds of 50MB/s. Since I was running into some codec problems with the 64 bit version, I reinstalled the 32 bit 7.10 and then upgraded distro from within the update utility. However, I did not notice a the time that I was only running at 100mbit.

Since then, I have been able to maintain network connectivity, but not at the desired speeds. I have even tried to install the driver by Intel for the board, but still limited to 100mbit. When even forced to 1000mbit, no further network activity is permitted (no link). 

Any suggestions?  I just know that it was running fine on an install of 64 bit, but now, nope.

---

### Post by buhammot on 2008-04-27
the link is only being established as a 100mbit connection, and when forced autoneg off and speed 1000, the link is no longer available.

---

### Post by tofuconfetti on 2008-10-24
I'm messing with this problem right now on 8.10 beta.  I finally gave up and put in a Netgear gigabyte card.  It worked like a charm.

It's the AMD64 version, btw.

---

