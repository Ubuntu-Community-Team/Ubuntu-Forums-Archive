---
title: "Dlink DWL-G650+ wireless woes"
date: 2008-04-30
forum: Networking &amp; Wireless
---

### Post by Pits0r on 2008-04-30
Hey guys,

I am running a lappy with ubuntu 8.04 and have problems doing wireless connections.

At home I have a wpa protected wap and works with my windows systems, but when I load up ubuntu here, it finds the network no problems and recognises it is protected. But when I try to connect, it asks me what password and does not have a wpa option, just wep, leap etc. Is this a known bug and if so, how to fix? Previously 7.10 had the exact same issue.

Also on another note, I found a interesting bug, I eject the card, put it back in and it does not get recongised, do it one more time and ot works. Very odd.

I have tried looking in forums but no luck for my problem.

---

### Post by zvbxrpl on 2008-05-01
The G650+ uses a Texas Instruments chipset I think, which requires the acx100 driver.  Unfortunately, acx100 doesn't support WPA yet, only WEP.  Drop your router to WEP, or blacklist the acx100 driver and use ndiswrapper as per the sticky in this forum.

Re the eject issue, what's the make and model of your laptop?

---

### Post by Pits0r on 2008-05-06
Hi,

thanks for the feedback.

The laptop is a Optima Centris running a athlon xp 1400 cpu with a gig of ram. Mostly unknown but at least it is amd.

---

### Post by zvbxrpl on 2008-05-08
That's not a model I know much about, I'm afraid.  You can debug the insert/eject problem by removing your card and typing dmesg at the terminal, then plugging it in and typing dmesg again, and looking at any new lines.  Compare the dmesg output with an insertion that works with one that doesn't.

The problem might go away if you use ndiswrapper, since a completely different driver will be in use.

---

