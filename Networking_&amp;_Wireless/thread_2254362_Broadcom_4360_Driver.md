---
title: "Broadcom 4360 Driver"
date: 2014-11-26
forum: Networking &amp; Wireless
---

### Post by eduardovelez3rd on 2014-11-26
I need a wifi driver for my Macbook Air, Early 2014, because the STA Linux driver that everyone seems to like is uncompatible witht the Broadcom BMC4360. Maybe I'm installing it wrong (Ubuntu 14.10), but I've always installed drivers using the software center with no problems. Does anyone know of a driver for my wifi card?

---

### Post by slickymaster on 2014-11-26
*Moved to the ***Networking & Wireless*** sub-forum*

---

### Post by jeremy31 on 2014-11-26
> **eduardovelez3rd said:**
> I need a wifi driver for my Macbook Air, Early 2014, because the STA Linux driver that everyone seems to like is uncompatible witht the Broadcom BMC4360. Maybe I'm installing it wrong (Ubuntu 14.10), but I've always installed drivers using the software center with no problems. Does anyone know of a driver for my wifi card?

There is a fix, but there are a couple commands that need to be changed to match your kernel, so please post the terminal results from ```
ls /lib/modules
```

If chili or someone else with 14.10 is watching, he might know the current kernel used with 14.10 and know how to modify the commands in this post- [http://ubuntuforums.org/showthread.php?t=2216779&p=12989252#post12989252](http://ubuntuforums.org/showthread.php?t=2216779&p=12989252#post12989252)

If the kernel is 3.16.0-25 then this post should help
[http://forums.linuxmint.com/viewtopic.php?f=49&t=183446#p950915](http://forums.linuxmint.com/viewtopic.php?f=49&t=183446#p950915)

---

### Post by chili555 on 2014-11-26
> because the STA Linux driver that everyone seems to like is uncompatible witht the Broadcom BMC4360.How so? The doctor wants to know your symptoms.```
sudo dpkg -s bcmwl-kernel-source
lspci -nn -d 14e4:
dmesg | grep wl
```Thanks.

---

