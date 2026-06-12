---
title: "Cannot re-attach 3G modem"
date: 2014-07-09
forum: Networking &amp; Wireless
---

### Post by Lars Noodén on 2014-07-09
I have Huawei E3131 that Ubuntu is starting to have trouble with.  It works fine if it is plugged in when the machine boots, and shows up then as a wired connection specifically wired connection 2. But then if I unplug it or, sometimes, if I suspend the machine, the system can no longer find it.  Removing it and plugging it in again causes the lights on the modem to go through the right cycle but the network connections applet no longer shows any wired connections.  Further, networking services cannot be restarted.

```

$ sudo service networking restart
stop: Job failed while stopping
start: Job is already running: networking

```

The relevant part of lsusb is : Bus 003 Device 005: ID 12d1:14dc Huawei Technologies Co., Ltd. 

How can I keep using the modem even after unplugging it or recovering from a suspend?

This is in 14.04

---

