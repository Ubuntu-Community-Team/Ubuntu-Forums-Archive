---
title: "ADSL intenet not working"
date: 2008-04-17
forum: Networking &amp; Wireless
---

### Post by Tristam1 on 2008-04-17
Hey,

I installed Ubuntu 7.10 when I use the Live CD the ADSL Internet works and after I installed it.It worked for the first time but from the 2nd time it says No device responded.

First Time(After Installation): Everything is working fine after I set up the connection by typing sudo pppoeconf and all.

Second Time:I type pon dsl-provider it says connected or sucessful(I don't remember very well I am using XP because of no internet in Ubuntu) anyways now when I type sudo pppoeconf it asks if it should look for devices and after looking it says that no device is responding.Please help I really love Ubuntu.

Tristam

---

### Post by Tristam1 on 2008-04-17
This another situation in which internet is connecting but nothing opens.

When I type plog this is the result.
```

Apr 17 23:09:16 tristam-desktop pppd[6217]: Connect: ppp0 <--> eth0
Apr 17 23:09:19 tristam-desktop pppd[6217]: CHAP authentication failed: Invalid CHAP-Password
Apr 17 23:09:19 tristam-desktop pppd[6217]: CHAP authentication failed
Apr 17 23:09:19 tristam-desktop pppd[6217]: Connection terminated.
Apr 17 23:09:20 tristam-desktop pppd[6068]: PPP session is 2154
Apr 17 23:09:20 tristam-desktop pppd[6068]: Using interface ppp0
Apr 17 23:09:20 tristam-desktop pppd[6068]: Connect: ppp0 <--> eth0
Apr 17 23:09:20 tristam-desktop pppd[6068]: CHAP authentication failed: Invalid CHAP-Password
Apr 17 23:09:20 tristam-desktop pppd[6068]: CHAP authentication failed
Apr 17 23:09:20 tristam-desktop pppd[6068]: Connection terminated.


```

---

### Post by Tristam1 on 2008-04-17
Hasn't anyone has this problem?

---

