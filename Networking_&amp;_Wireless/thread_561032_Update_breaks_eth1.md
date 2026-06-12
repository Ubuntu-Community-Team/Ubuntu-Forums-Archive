---
title: "Update breaks eth1"
date: 2007-09-27
forum: Networking &amp; Wireless
---

### Post by fishyf on 2007-09-27
Hi,
I had an update yesterday which required a system restart. After that wireless networking stopped working. My gdesklet which monitors the internet says eth1: device is down.

lspci shows the device as:

02:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)

Ifconfig.

ifconfig eth1
eth1: error fetching interface information: Device not found

Was the wireless device name changed? I tried wlan0 which also shows nothing?
Confused fishy here.

---

### Post by fishyf on 2007-09-27
oh and ...

sudo ifup eth1
eth1: ERROR while getting interface flags: No such device

---

### Post by fishyf on 2007-09-27
It works if I go back to the previous kernel. 2.6.22.1 doesn't work,  2.6.20-16-generic does.

---

### Post by fishyf on 2007-09-28
So can I ask; is this the answer. Go bask to the previous kernel? Is there no way to get it to work with the latest kernel?

---

### Post by deadowl on 2007-10-02
I have a similar problem, but I just type the command sudo ifconfig eth1 up to bring it up. ndiswrapper had it aliased as wlan0. Maybe try wlan0 rather than eth1?

---

