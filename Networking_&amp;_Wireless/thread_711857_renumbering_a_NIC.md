---
title: "renumbering a NIC"
date: 2008-03-01
forum: Networking &amp; Wireless
---

### Post by akahige on 2008-03-01
I've got two NIC's on my system: eth0 is a 10/100 device built into the mobo and was defined during the original OS install; eth1 is a GB PCI card that was added some time later. Of the two, only eth1 is being used.

Due to the funky way that VMware handles some of the networking config, it would be really great if I could redefine eth1 to eth0. Am wondering if this is simply a matter of swapping the eth device numbers in /etc/udev/rules.d/70-persistent-net.rules or if doing that will cause things to break elsewhere.

---

### Post by ung/xunil on 2008-03-01
Yes, edit that file and swap the interface names, save the file and reboot.

---

### Post by akahige on 2008-03-02
Worked like a charm. Thanks for allaying my fears!

---

