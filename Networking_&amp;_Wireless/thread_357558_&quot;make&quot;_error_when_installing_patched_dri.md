---
title: "&quot;make&quot; error when installing patched drivers madwifi-ng"
date: 2007-02-09
forum: Networking &amp; Wireless
---

### Post by GuruX on 2007-02-09
It as simple as this. I wanted to install the patched drivers from aircrack-ng to be able to gain some  more control over my atheros based wifi card. But obviously something goes wrong when i try i make the driver.

I followed this guide: [http://www.aircrack-ng.org/doku.php?id=madwifi-ng](http://www.aircrack-ng.org/doku.php?id=madwifi-ng)

When I type "make" at the console, I get this:
root@lillen-ubuntu:/home/gustav/madwifi-ng# make
cd: 1: can't cd to /lib/modules/2.6.17-11-386/build
Makefile.inc:66: *** /lib/modules/2.6.17-11-386/build is missing, please set KERNELPATH. Stop.


This is probably i quite easy error, but I can't seem to find the answear to it.

---

### Post by pedalwrench on 2007-02-11
> **GuruX said:**
> It as simple as this. I wanted to install the patched drivers from aircrack-ng to be able to gain some  more control over my atheros based wifi card. But obviously something goes wrong when i try i make the driver.

I followed this guide: [http://www.aircrack-ng.org/doku.php?id=madwifi-ng](http://www.aircrack-ng.org/doku.php?id=madwifi-ng)

When I type "make" at the console, I get this:
root@lillen-ubuntu:/home/gustav/madwifi-ng# make
cd: 1: can't cd to /lib/modules/2.6.17-11-386/build
Makefile.inc:66: *** /lib/modules/2.6.17-11-386/build is missing, please set KERNELPATH. Stop.


This is probably i quite easy error, but I can't seem to find the answear to it.


You may need to install the linux-headers package

```
sudo apt-get install linux-headers-generic
```

---

