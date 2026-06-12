---
title: "Proxied Wireless Hotspot"
date: 2016-11-13
forum: Networking &amp; Wireless
---

### Post by colt05 on 2016-11-13
Hello
I've tried to set up a wireless hotspot to set up a socks proxy on it (possibly using redsocks). On one computer, I ran the code from [http://askubuntu.com/a/743127/](http://askubuntu.com/a/743127/). The wireless manager disappeared and there was no Internet access on the hotspot. On the other computer, I followed the guide at [http://askubuntu.com/a/180734/548581](http://askubuntu.com/a/180734/548581). Hostapd failed with the error ```
ioctl[PRISM2_IOCTL_PRISM2_PARAM]: Operation not supported.
``` When running iw list, both computers have IBSS, managed, AP, AP/VLAN, monitor, and mesh point.
Any suggestions as to how to set up a wireless hotspot and make all TCP connections on the hotspot go through a socks5 proxy?
Thanks!

---

### Post by colt05 on 2016-11-14
bump

---

### Post by slickymaster on 2016-11-14
*Thread moved to **Networking & Wireless**.*

---

### Post by colt05 on 2016-11-16
bump

---

