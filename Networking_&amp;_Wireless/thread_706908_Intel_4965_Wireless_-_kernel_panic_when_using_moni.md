---
title: "Intel 4965 Wireless - kernel panic when using monitor mode"
date: 2008-02-24
forum: Networking &amp; Wireless
---

### Post by wiryu on 2008-02-24
Dear all,
I'm using Ubuntu 7.10 Gutsy. My wireless lan works just fine. I'm using Intel 4965 a/b/g/n. The problem is that when I run these 3 commands:

ifconfig wlan0 down
iwconfig wlan0 mode monitor
ifconfig wlan0 up

After the last command, the system stopped with kernel panic.
Anyone know the solution?
I was trying to run airodump but it needs to be run on monitor mode.
This is the kernel version that I'm using: 2.6.22-14-generic
Thanks.

---

### Post by hugmenot on 2008-02-24
Monitor mode is asking for trouble on so many levels...

---

### Post by jblackthorne on 2008-02-25
Monitor is more stable in iwlwifi 1.2.0 if that is any consolation.  Gutsy ships with 1.1.0.  Hardy comes with 1.2.0 (and hopefully 1.2.3+ by release)

---

