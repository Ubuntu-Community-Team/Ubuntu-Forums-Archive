---
title: "TKIP messages from Broadcom WL driver"
date: 2008-09-06
forum: Networking &amp; Wireless
---

### Post by hackel on 2008-09-06
Since switching to the Broadcom proprietary WL driver for my BCM4312 (Dell XPS M1530), I've started seeing the following message repeatedly in my dmesg:

TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=ffff8100d670a600

Seems to happen about every 110 seconds (according to dmesg timestamps, which don't seem reliable).  Anyone know what this means?

---

### Post by sagyvolkov on 2008-11-03
did you had any reply on this issue?
I'm facing the same annoying messages in my dmesg

---

### Post by sandyeggoboy on 2008-11-04
Hi guys ... I am also having the same problem.

---

### Post by digistyl3 on 2008-11-06
I've reported this bug: [https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules/+bug/294878](https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules/+bug/294878)

---

### Post by carltonh on 2008-11-08
Do you have bcm4312 rev 1 or 2?  If 1, how did you get wireless to connect in the first place?  It is completely broken except for showing available networks with every method I've tried in 8.10.

---

### Post by carltonh on 2008-11-28
Interestingly enough, I have found that the bcm4312 works fine with some wireless routers with WEP standard encryption, but other WEP wireless routers including my home network do not work at all with 8.10.

This is especially odd because the wireless in this same laptop worked fine in 8.04 with my home wireless router.  Vista on the same laptop works fine with my home router, so there is still a major issue with 8.10 that is a regression from 8.04 with some routers.

Not sure what to do about it.

---

