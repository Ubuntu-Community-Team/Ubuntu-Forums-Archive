---
title: "Wireless won't shut off in Edgy"
date: 2006-11-04
forum: Networking &amp; Wireless
---

### Post by eppoh on 2006-11-04
I am in a hotel that has wirelss ( for a fee) and free acess through wired network interface.

Problem is the wireless card won;t let the hardwire work.
I have not even configured the wireless card yet- it is showing as not being configured but is picking up the assigned DNS.

How can I shut this off?

---

### Post by spd106 on 2006-11-04
Open a terminal and find the interface name **iwconfig** eg wlan0. Then shut it down by **sudo ifdown wlan0**. If that doesn't work try **sudo ifconfig wlan0 down**

---

### Post by eppoh on 2006-11-05
Thanks,
I wound up just configuring it with a bogus static dns, so it will not connect

---

