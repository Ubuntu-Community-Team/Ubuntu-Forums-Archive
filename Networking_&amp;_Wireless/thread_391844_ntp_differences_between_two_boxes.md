---
title: "ntp differences between two boxes"
date: 2007-03-23
forum: Networking &amp; Wireless
---

### Post by ebike on 2007-03-23
Hi All,

I have a laptop and a mythtv box both running the latest edgy and ntp packages.

However even though I followed the ntp setup for both boxes the same, and they are both using the same ntp servers, the mythtv box continues to gain about 20 seconds each hour, and does not seem to get corrected by ntpd.

I can get it back on time using ntpdate, but why doesn't ntpd correct it?

Both machines are behind the same firewall (the firwall is on the mythtv box)

It seems the hardware clock on my mythtv box is running fast, but cannot understand why it is not being corrected.

I had a look in the /etc/ntp.conf file and noticed some network related "restricted" settings. Since I am behind a firewall, can I remove some of these restrictions?
Maybe they are too tight for the ntpd to work.

Any help much appreciated.

---

