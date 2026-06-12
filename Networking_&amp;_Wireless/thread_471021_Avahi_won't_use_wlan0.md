---
title: "Avahi won't use wlan0"
date: 2007-06-11
forum: Networking &amp; Wireless
---

### Post by agni on 2007-06-11
Hi,
I'm trying to get avahi running over a wireless network. Whenever i stat the daemon with an ethernet cable it startus up correctly and announces itself to the ethernet network:
```

Jun 11 21:21:15 asgard avahi-daemon[16081]: avahi-daemon 0.6.17 starting up.
Jun 11 21:21:15 asgard avahi-daemon[16081]: Successfully called chroot().
Jun 11 21:21:15 asgard avahi-daemon[16081]: Successfully dropped remaining capabilities.
Jun 11 21:21:15 asgard avahi-daemon[16081]: Loading service file /services/ssh.service.
Jun 11 21:21:15 asgard avahi-daemon[16081]: Joining mDNS multicast group on interface eth0.IPv4 with address 169.254.0.1.
Jun 11 21:21:15 asgard avahi-daemon[16081]: New relevant interface eth0.IPv4 for mDNS.
Jun 11 21:21:15 asgard avahi-daemon[16081]: Network interface enumeration completed.
Jun 11 21:21:15 asgard avahi-daemon[16081]: Registering new address record for fe80::200:ff:fe00:0 on eth0.*.
Jun 11 21:21:15 asgard avahi-daemon[16081]: Registering new address record for 169.254.0.1 on eth0.IPv4.
Jun 11 21:21:15 asgard avahi-daemon[16081]: Registering HINFO record with values 'I686'/'LINUX'.
Jun 11 21:21:16 asgard avahi-daemon[16081]: Server startup complete. Host name is asgard.local. Local service cookie is 115851754.

```

From my laptop (connected with a cable) I can browse the services provided by avahi. However avahi doesn't use the wireless device to announce itself. From a wireless laptop I can not browse the services provided.

I assume there should be something like "Registering new address record for 192.168.1.2 on wlan0.IPv4." in the log, if it would be using the wireless device (wlan0).

My desktop (the one i'm trying to get avahi to work) has a static ip setup for the wireless net. I tried getting a ip from the dhcp server but avahi still wouldn't use the wireless device.

Any help is appreciated.
Cheers.

---

### Post by agni on 2007-06-11
With help from the guys at #avahi I could fix it. I'll post the answer as reference for anybody who has the same problem. An avahi device has to have the MULTICAST flag set. The flag can be set like this:
```
ifconfig wlan0 multicast
```
(replace wlan0 with whatever your device is called)
Cheers.

---

