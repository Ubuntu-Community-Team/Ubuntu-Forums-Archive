---
title: "how to retrieve driver and settings of a wireless card"
date: 2008-09-27
forum: Networking &amp; Wireless
---

### Post by DrScum on 2008-09-27
I have an SMC wireless card which in Xubuntu 8.04 works "out of the box".
I want to install this very card into an old system running on vector linux to be used as router. The vector linux doesn't support the card just like that and I obviously need to install driver and possibly firmware. 

How do I retrieve the configuration in detail on the Xubuntu system?

Thanks for your consideration.

---

### Post by DrScum on 2008-09-29
The question more precisely:

How can I locate driver and firmware used for the particulare card running under Xubuntu?

---

### Post by Ayuthia on 2008-09-29
lshw -C network will help tell you what driver your wireless card is using (as long as it is not a USB device).

As for the location of the driver, it can be found by using:
```
modprobe --show-depends <device>
```So if your module is a rt61, you would type modprobe --show-depends rt61.  However, I don't really reccomend you to copy the module and move it to another operating system because the kernel version could be different and could cause problems.

The firmware however is different.  It is usually stored in /lib/firmware.

What you will probably want to do is look for the driver by using lshw -C network.  Once you find it, you will want to do a search on the internet for the driver.  You should find a site where they maintain the driver.  From there you should be able to get the source to compile the driver.  

Sometimes the wireless driver is compiled with the kernel.  If that is the case and it is missing firmware, usually dmesg will tell you what is missing.

Hope that helps.

---

### Post by DrScum on 2008-09-29
Thanks a lot for the help I'll try to go down the suggested  pathway.

---

