---
title: "[SOLVED] Network Manager + VPN + wireless connection = no connection to VPN"
date: 2007-10-30
forum: Networking &amp; Wireless
---

### Post by PartisanEntity on 2007-10-30
In Feisty, I had configured a VPN connection (in Network Manager) to Relakks. So once my laptop was online I could connect to Relakks when needed.

Now in Gutsy, I can't connect to the Relakks VPN when in wireless mode. I can only connect to it when I plug the ethernet cable into my laptop.

I would really appreciate any help or ideas no how to get this working properly.

---

### Post by PartisanEntity on 2007-10-31
Bump

---

### Post by GrammatonCleric on 2007-11-02
Hmmm... I'm having a similar issue with my Pro/Wireless 3945ABG.  When I'm on my wireless and connect to my office Cisco VPN I can't access either the internet or my office behind the VPN.  

If I then connect to home Ethernet and again connect to my office VPN everything works fine.   Prior to upgrading to Gutsy I could connect without issue to VPNs while using wireless.

Mind you it's not just the wireless on my home network...it's all wireless networks.

-GC

---

### Post by PartisanEntity on 2007-11-02
Yes I had absolutely no issues in Feisty with this, but something seems to have changed in NM under Gutsy.

---

### Post by GrammatonCleric on 2007-11-02
I filed a bug report on launchpad.

[https://bugs.launchpad.net/ubuntu/+bug/159484](https://bugs.launchpad.net/ubuntu/+bug/159484)

-GC

---

### Post by PartisanEntity on 2007-11-02
I am not sure if I should add to your bug report or file a new one, I have a somewhat different issue. I simply cannot connect to VPN when on wireless but I do not lose any connectivity?

---

### Post by GrammatonCleric on 2007-11-02
Wouldn't hurt to add that to the bug report.

-GC

---

### Post by PartisanEntity on 2007-11-03
Okay I have added to your bug report, lets hope this can be fixed.

---

### Post by PartisanEntity on 2007-11-07
Solved thanks to this thread:
[http://ubuntuforums.org/showthread.php?t=601671](http://ubuntuforums.org/showthread.php?t=601671)

---

