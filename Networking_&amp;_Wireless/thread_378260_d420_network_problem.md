---
title: "d420 network problem"
date: 2007-03-07
forum: Networking &amp; Wireless
---

### Post by oicu on 2007-03-07
Hello,
I installed kubuntu 6.10 to dell latitude D420.
now i have a problem getting my network connection(eth0) to work.
i tried dhclient eth0, disabling ipv6 in /etc/modprobe.d/aliases, giving statis ip... nothing.
Any thoughts?

---

### Post by depill on 2007-03-07
I have a very similar setup, only problem I have so far is the bluetooth setup.

Do you have the power cable connected when you try to run dhclient ?

And do the lights blink around your network adapter on the back of the D420 ? Are you using the dock ?

---

### Post by oicu on 2007-03-07
Thx for reply.

power cable is connected. I've tried with dock and without a dock.
Network connector status light(left) is red, other is blinking when doing dhclient.


Any ideas?

---

### Post by bimmerd00d on 2007-08-22
D420's use a Broadcom integrated NIC unlike the 520,620, and 820's Intel.  You need nfiswrapper and whatnot.

---

