---
title: "Linksys WUSBF54G sees network but won't connect!"
date: 2008-03-25
forum: Networking &amp; Wireless
---

### Post by Pandora Rose on 2008-03-25
I have a Linksys WUSBF54G Wireless-G USB Network Adapter with WIFI FInder.  I'm currently running Kubuntu 7.10.  I can see my network, but I can't connect to it.  I know the adapter works, since I've been using in in Windows for a while now.  Help!

driver
  zd1211rw
```
lsusb
  Bus 001 Device 002: ID 13b1:001e Linksys

```
```
lshw -C network
  *-network
       description: Wireless interface
       physical id: 2
       logical name: eth1
       serial: 00:14:bf:be:e1:ac
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11b/g
```

---

### Post by Paris Heng on 2008-03-25
**How you install the zd1211rw?** The zd1211rw is in the kernel i think.What version of Ubuntu you using? I also having problem with zd1211rw driver.

---

### Post by Pandora Rose on 2008-03-25
I'm currently running Kubuntu 7.10 (Ubuntu 7.10 running KDE).  The zd121rw driver comes with 7.10 distro (installed by default)

---

### Post by wieman01 on 2008-03-25
What version of WUSB54G have you got? The version number is printed on the back of the device I believe.

---

### Post by Pandora Rose on 2008-03-25
I don't have a WUSB54G, I have a WUSB**F**54G.  Device ID 13b1:00e1.  There is only a version 1.

---

