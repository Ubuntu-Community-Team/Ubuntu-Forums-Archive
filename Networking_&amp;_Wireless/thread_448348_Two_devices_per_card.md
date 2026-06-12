---
title: "Two devices per card?"
date: 2007-05-19
forum: Networking &amp; Wireless
---

### Post by B-Con on 2007-05-19
I have two wireless cards in my laptop, an Intel w2200 and D-Link DWL-G650. Under Ubuntu Dapper the former shows up as eth1 and the latter as ath0 -- all good. Under Feisty, they still show up as how they did in Dapper, however, there are two more devices listed, eth1:avahi and wifi0, each with a MAC address corresponding to eth1 and ath0, respectively.

Why are there two more devices now? What're they for, what can I do with them? :confused:

---

### Post by B-Con on 2007-05-30
(Bump.) 

Any clue why this is... its both annoying and confusing. Anyone have any info?

---

### Post by spd106 on 2007-05-30
The avahi alias is a fudge to show that avahi-autoip has kicked in after DHCP failed. This is confusing for most users and I hope it will disappear when a better solution is found. For the moment we are stuck with it. I suggest you ignore it as it should have any major impact accept as a warning that you probably don't have an Internet connection on the interface. Read up on avahi-autoip for more information.

Wifi0 is a side effect of the madwifi-ng driver. It represents the lower level interface of the driver and isn't used directly when configuring connection. It can be safely ignored as most tools you have won't work with it. See madwifi.org for more information.

---

