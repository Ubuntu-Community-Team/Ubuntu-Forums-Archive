---
title: "Where do I store iwconfig parameters?"
date: 2007-06-02
forum: Networking &amp; Wireless
---

### Post by submute on 2007-06-02
As I have not been able to find another place to put them, I have three iwconfig lines in my /etc/rc.local file to set the parameters for my wireless card, followed by an ifup line for the device.

Is there somewhere I can store the params - key, essid, and ap - so I can remove these lines from rc.local?

Thanks!

---

### Post by submute on 2007-06-02
I should say I am running the Ubuntu server edition, so I am looking to do this w/o a GUI.

---

### Post by chili555 on 2007-06-02
Store them in */etc/network/interfaces*. Here's an obscured version of mine for comparison:```
auto lo
iface lo inet loopback


iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp
wireless-essid GBR9
wireless-key 0123456789abcdef
wireless-ap 99:9C:41:19:58:77
```

---

