---
title: "Help! Ive connected my usb wireless modem through KPPP but......"
date: 2008-10-04
forum: Networking &amp; Wireless
---

### Post by darkworld on 2008-10-04
Ive connected my UK o2 network usb novatell ovation MC930D and got connected 3G/HSDPA. KPPP showing connected, no traffic in graph after connection. Opened firefox and it doesnt find the web so im thinking something else needs setting up. Please can someone tell me what?

This server DNS addresses in KPPP do they need setting up? Please help im working from windoz and I hate it!

---

### Post by pytheas22 on 2008-10-04
Are you sure you really got an IP address?  Please post the output of the following commands after you're connected (to the best of your knowledge) so that we can figure things out:

```
ifconfig
lsusb
cat /etc/resolv.conf
host google.com
ping google.com
ping -c 5 64.233.187.99

```

---

