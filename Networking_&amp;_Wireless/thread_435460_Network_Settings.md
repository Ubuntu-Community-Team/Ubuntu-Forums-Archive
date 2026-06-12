---
title: "Network Settings"
date: 2007-05-06
forum: Networking &amp; Wireless
---

### Post by thepaul on 2007-05-06
Hi

Internet connection is not working.  I went to network settings and the "wired connection' is missing.  All there is 'modem connection".

Light is on when cable is plugged into ethernet card. 

Any help


thanks in advance.

---

### Post by chriscando on 2007-05-07
If you know your wired interface you can try doing
sudo ifdown eth0
sudo ifup eth0
sudo dhclient eth0 (to get an ip address using DHCP)

---

### Post by Johnnyblaz on 2007-06-03
i am having the same problem.  I tried the responders methods, but it says "no such device"

The device is clearly listed under the "DEVICES" screen. is there anyway to force it or manually reinstall the drivers for the card? i am a bit new.

Thanks.

---

