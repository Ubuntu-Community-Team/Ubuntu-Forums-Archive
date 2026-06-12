---
title: "Networking boot problem"
date: 2005-05-03
forum: Networking &amp; Wireless
---

### Post by Jvaldezjr on 2005-05-03
This happens about 50% of the time when I'm starting up my machine.  What happens is that right around the lines "starting hotplug system, and initializing ifupdown" one of those processes fail.  When it fails I lose my internet connection.  So I have to reboot, again, and hope that it properly detects my network card.  My question is this, is there any way I restart those processes again from the console without having to reboot my machine?

Thanks

---

### Post by dataw0lf on 2005-05-03
to bring your network interface back up: 
ifup eth0

to bring up hotplug:
/etc/init.d/hotplug start

---

### Post by Jvaldezjr on 2005-05-10
I tried the scripts that you suggested, and when I tried to run "ifup eth2" (eth2 being the card Im using)...this is what it told me.

So I still have to restart and hope it's detected and brought up properly.

```
Internet Systems Consortium DHCP Client V3.0.1
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

sit0: unknown hardware address type 776
SIOCSIFADDR: No such device
eth2: ERROR while getting interface flags: No such device
eth2: ERROR while getting interface flags: No such device
sit0: unknown hardware address type 776
Bind socket to interface: No such device
Failed to bring up eth2.
```

---

### Post by LongLife on 2005-05-13
I had a similar problem with my Sagem Fast 800 usb  ADSL modem (eagle-usb)
I configured 2 internet accesses one for my RTC modem, one for my ADSL modem. 2 ppp  interfaces  (ppp0 and ppp1) were created at boot, and I the ADSL was deconnected half of the time.

Solution : I removed the RTC modem configuration, rebooted and now it works fine.

Hope it will help you...

---

