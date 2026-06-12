---
title: "Bridging Network Cards"
date: 2006-10-20
forum: Networking &amp; Wireless
---

### Post by Mithrilhall on 2006-10-20
Here's my scenario:

Internet<------------>Router<------->Laptop<-------Another_Device

The laptop has 2 NICs installed (eth0 & eth2....eth1 is my wireless so we can ignore that).

I want to be able to share my internet connection from my laptop with another device (could be a computer, IP phone, etc...).

I've been following along with this article and can't seem to get it working. No traffic seems to be passing on to eth2. [http://www.linuxjournal.com/article/8172](http://www.linuxjournal.com/article/8172)

Any suggestions on what I'm doing wrong here?

---

### Post by bait on 2006-10-20
The bridge-utils doesn't support wireless bridging. ( In most cases.)

 Here's a link to explanation.

[http://linux-net.osdl.org/index.php/Bridge#It_doesn.27t_work_with_my_Wireless_card.21](http://linux-net.osdl.org/index.php/Bridge#It_doesn.27t_work_with_my_Wireless_card.21)

---

### Post by Mithrilhall on 2006-10-20
I think you misunderstood me. I'm not bridging the wireless adapter.

---

### Post by bait on 2006-10-20
Missed the note about eth0.

 What do you get when you use the following command?

 brctl show

 Also make sure ipv4_forward is enabled and does the bridge show up under ifconfig or ip link show?

---

