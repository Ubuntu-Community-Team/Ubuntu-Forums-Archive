---
title: "How to replace a wired network driver?"
date: 2008-05-20
forum: Networking &amp; Wireless
---

### Post by linsh on 2008-05-20
Hello,
I'd like to replace the wired network driver "via_velocity" to "velocityget.ko" in Ubuntu 8.04.
The following steps will work temporarily:
sudo make install
sudo rmmod via_rhine
sudo rmmod velocityget
sudo insmod velocityget.ko
But after I reboot the system, the device still work with via_velocity.
I've tried to modify /etc/modprobe.d/blacklist and /etc/modprobe.d/aliases by
blacklist via_velocity
alias eth0 velocityget
But this doesn't work. Does anyone have ideas?

Regards,
linsh

---

### Post by chili555 on 2008-05-20
You might amend your *blacklist* file to reflect that it's via**-**velocity, not via_velocity and via**-**rhine and not via_rhine.> chili@LAPTOP60:~$ locate velocity | grep .ko
/lib/modules/2.6.20-16-generic/kernel/drivers/net/via-velocity.ko
/lib/modules/2.6.22-14-generic/kernel/drivers/net/via-velocity.ko
/lib/modules/2.6.24-16-generic/kernel/drivers/net/via-velocity.ko
chili@LAPTOP60:~$ locate rhine | grep .ko
/lib/modules/2.6.20-16-generic/kernel/drivers/net/via-rhine.ko
/lib/modules/2.6.22-14-generic/kernel/drivers/net/via-rhine.ko
/lib/modules/2.6.24-16-generic/kernel/drivers/net/via-rhine.koIf that doesn't solve it, post back and we'll be happy to help.

---

### Post by linsh on 2008-05-20
No, it doesn't work.
The boot message still has "VIA Networking Velocity Family Gigabit Ethernet Adapter Driver Ver. 1.14" which the default driver is.
> 
lsmod | grep velocity
velocityget   47648 0
via_velocity  32772 0
crc_ccitt     3072  2 irda,via_velocity

If I also blacklist crc-ccitt, the information will be disappear.
But the device still loads the default driver.

---

