---
title: "/etc/network/interfaces  ignored in image tgz"
date: 2015-03-29
forum: Networking &amp; Wireless
---

### Post by researcher2 on 2015-03-29
Hello all,

Please, i have edited the file /etc/network/interfaces and added:
auto lxcbr0
iface lxcbr0 inet dhcp bridge_ports eth0 bridge_stp off bridge_fd 0 bridge_maxwait 0
i have the saved an image tgz of my node
when i deploy again the image on my cluster, i don't find the lines added the /etc/network/interfaces
they are ignored!

Have you an idea please ?
Thanks a lot for help.

---

