---
title: "Access hardware device"
date: 2018-11-29
forum: Networking &amp; Wireless
---

### Post by zkab on 2018-11-29
I have a device (os unknown) but it can be configured with a predefined ip address 10.0.48.96 with a browser.
What I have done is installed Ubuntu 18.10 on a spare computer and connected it to the device with a cross-linked rj45 cable.
The Ubuntu computer is not connected to Internet (there is no Internet in the building) only to the device.
But there seems to be a network problem to integrate the device ... how can I get the Ubuntu computer and the device on the same network ... when I start Firefox with address 10.0.48.96 it can't find it.

---

### Post by TheFu on 2018-11-30
Have you tried putting the Ubuntu machine on the 10.0.48.0/24 subnet with a static IP? Then add a route to the 10.0.48.96 directly.  Might need to setup a manual route from the device to the Linux machine for packets to get back.

BTW, it would be easier with a $10 router and both devices connected through the router.  Networking without a router is a hassle.

---

### Post by zkab on 2018-11-30
Thanks - maybe the router is the way to go ...

---

