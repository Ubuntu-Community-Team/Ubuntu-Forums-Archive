---
title: "[SOLVED] No Network Interfaces"
date: 2007-03-09
forum: Networking &amp; Wireless
---

### Post by pt123 on 2007-03-09
I had some errors on the drives where the linux partition was installed.

I had to run fsck manually to fix the errors, not sure what files were damaged.

Now when it boots up there are no Network connections i.e. eth0 & eth1.

But when I look in the device manager the two network devices are there.

How do I force it to re-redect or rebuild these devices. 

When I tried to run start networking I got this error:-

SIOCSIFADDR: No such device
eth1: ERROR while getting interface flags: No such device
eth1: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth1.
There is already a pid file /var/run/dhclient.eth2.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

---

### Post by pt123 on 2007-03-09
Bunp anyone?

---

### Post by pt123 on 2007-03-09
I managed to fix it by finding the LinuxImage in synaptic and re-installing it.

---

