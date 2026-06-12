---
title: "what driver is used for ralink cards?"
date: 2007-09-15
forum: Networking &amp; Wireless
---

### Post by android6011 on 2007-09-15
My ralink card works fine out of the box ( 04:00.0 Network controller: RaLink RT2561/RT61 802.11g PCI ), but I want to use the rt2x00 driver, what driver is used by default and how do I disable it and enable the rt2x00 driver.

---

### Post by kevdog on 2007-09-15
rt2x00 drivers are experimental.  Google for the serial monkey site.  That is where they are located.  They are quite of a challenge to get working, and once working they are not too reliable.

---

### Post by android6011 on 2007-09-15
I have used them in the past without any problems with my card. How can I disable the current driver being used so that I dont have any problems installing?

---

### Post by kevdog on 2007-09-15
Depending on what driver you are using

#1. Add the driver to the blacklist file -- echo "driver_name" | sudo tee -a /etc/modprobe.d/blacklist
#2. Physically remove the module from the kernel - sudo modprobe -r driver_name

Let us know how you make out with the new drivers.

---

### Post by oponek on 2008-01-24
Is this bug with ralink cards going to be fixed in Hardy? [https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.22/+bug/134660](https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.22/+bug/134660)

---

