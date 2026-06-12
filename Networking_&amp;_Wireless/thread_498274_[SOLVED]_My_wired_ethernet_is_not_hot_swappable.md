---
title: "[SOLVED] My wired ethernet is not hot swappable"
date: 2007-07-11
forum: Networking &amp; Wireless
---

### Post by cimphany on 2007-07-11
If I unplug my Ethernet cable and move to a different location I have to completely reboot my machine in order to get online again.

$ uname -a
Linux Merimaiya 2.6.20-16-lowlatency #2 SMP PREEMPT Thu Jun 7 20:23:03 UTC 2007 i686 GNU/Linux

Latitude D820 (laptop; not a preconfigured machine)

Vendor: Broadcom Corporation
Device: NetXtreme BCM5752 Gigabit Ethernet
Driver: tg3

If I unplug the cable from the laptop then plug it in again I still have to reboot the machine

I've tried replacing the cable with a factory cable, If I unplug the cable from the laptop then plug it in again I still have to reboot the machine

The machine will not get an IP although it says 'you are now connected to the network' the IP that it gets is 0.0.0.0 same for the subnet mask, broadcast address, and every thing else.

If I reboot the machine It will get a network address and every thing else needed.

disabling and enabling networking does not resolve the issue, only rebooting it does.

I do not have a wireless connection at this location to use

Any amount of help would be greatly appreciated. Thank you for your time

---

### Post by 5-HT on 2007-07-11
> **cimphany said:**
> 

disabling and enabling networking does not resolve the issue, only rebooting it does.


How are you restarting networking?
What about
```
sudo dhclient eth0
``` after plugging in the cable to request an IP from the dhcp server?

If that doesn't do it, you can try a
```
sudo ifconfig eth0 down
sudo ifconfig eth0 up
sudo dhclient eth0
```

---

### Post by pardesi on 2007-07-11
i had somewhta the same problem.Did you edit something in your grub menu after which the problem started

---

### Post by cimphany on 2007-07-11
> **5-HT said:**
> How are you restarting networking?
What about
```
sudo dhclient eth0
``` after plugging in the cable to request an IP from the dhcp server?

That works. I found that I can also use the following which is some thing I should have known after fighting with LAMPs

```
cd /etc/init.d/
``` 
```
sudo ./networking restart
```

> **pardesi said:**
> i had somewhta the same problem.Did you edit something in your grub menu after which the problem started

I don't recall doing any thing with the grub menu (I don't know how)

---

### Post by 5-HT on 2007-07-11
Glad you got it! It's kinda funny because I have the same NIC and haven't experience a similar issue. If I plug in a different cable associated with a different IP though, I need to renew the ip (either with a dhclient or a networking restart). Maybe something with how your dhcp server is giving out addresses (lease expiry, etc...)?
cheers,

---

### Post by cimphany on 2007-07-12
> **5-HT said:**
> Glad you got it! It's kinda funny because I have the same NIC and haven't experience a similar issue. If I plug in a different cable associated with a different IP though, I need to renew the ip (either with a dhclient or a networking restart). Maybe something with how your dhcp server is giving out addresses (lease expiry, etc...)?
cheers,

That may be true. I'll have to look into it....But it has happened at home although I use my desktop at home and don't really move it around much so I'm not sure if that was layer 8 or not.

NetGear  WGR614 V6

---

