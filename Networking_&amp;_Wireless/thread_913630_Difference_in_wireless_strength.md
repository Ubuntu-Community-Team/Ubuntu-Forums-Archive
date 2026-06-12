---
title: "Difference in wireless strength"
date: 2008-09-07
forum: Networking &amp; Wireless
---

### Post by Gene Cannon on 2008-09-07
Hi,
My old Toshiba has an Atheros AR5005G which consistently receives a signal from my son's home about 90 feet away from mine.  My new one  has an Atheros AR5007EG which is very spotty from the same location and has thrown my off several times.  Any ideas?
Thanks,
Gene Cannon

---

### Post by mfdc1969 on 2008-09-08
I have a **Atheros AR5007EG** in my Acer Aspire 5610Z and was using ndiswrapper but just followed the instructions on the Madwifi site and changed the drivers

[INDENT][http://madwifi.org/ticket/1192]("http://madwifi.org/ticket/1192")[/INDENT]

It wasn't working for me immediately but then I found additional information on this page:

[INDENT][http://home.nyc.rr.com/computertaijutsu/rhwireless.html#5007]("http://home.nyc.rr.com/computertaijutsu/rhwireless.html#5007")[/INDENT]

My main issue was that to install Madwifi properly I had to fully disable/remove ndiswrapper - a few tips on that are mentioned in the second link above.

So far it is working well although connection speed varies from 24/48/54 Mb/s - even though my computer has remained in the exact same room/position only 15' from my wireless router.

I hope this helps. The Atheros AR5007EG is something I have struggled with too.

---

### Post by mfdc1969 on 2008-11-26
I installed Intrepid last week which has support for my Atheros wifi chip and it seems really stable - signal strength is quite consistent and uses the Madwifi Ath5k. It requires adding the package **linux-backports-modules-intrepid**

It's described here:
[INDENT][/INDENT][https://help.ubuntu.com/community/WifiDocs/Driver/Atheros]("https://help.ubuntu.com/community/WifiDocs/Driver/Atheros")

I recommend setting Synaptic to use the **intrepid-proposed** updates also as I had complication which were easily resolved by it and are detailed here at [LaunchPad bug #287450]("https://bugs.launchpad.net/ubuntu/+source/linux-backports-modules-2.6.27/+bug/287450").

Atheros wifi is certainly easier with Intrepid.

---

