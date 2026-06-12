---
title: "Help with instalation of Ubuntu in my laptop."
date: 2010-07-23
forum: New to Ubuntu
---

### Post by Jose Esteban Vilella on 2010-07-23
Need help finding and installing Ubuntu in my:


Toshiba Satellite A215-S4767 running Windows Vista Ultimate
 2.20 GHz AMD Turion 64 X2 Mobile Technology TL-64
2 GBs RAM
250 GB Fijitsu MHX2250BT ATA Hard Drive
Atheros AR5007EG Wireless Network Adapter
ATI Radeon X1200 Graphics
Pioneer DVD-RW DVR-k17LF ATA Optical Drive
Chicony USB 2.0 Camera

Can anyone point me to any address that would help?

---

### Post by jtarin on 2010-07-23
[Download]("http://www.ubuntu.com/desktop/get-ubuntu/download")
[Installing]("https://help.ubuntu.com/10.04/installation-guide/index.html")

---

### Post by Mark Phelps on 2010-07-24
Several important considerations regarding what you're about to do:

1) Your ATI chip is no longer supported with accelerated drivers in current Ubuntu versions.  You will be forced to use the open source drivers, which while they do provide excellent graphics support, they will not be useful for 3D gaming.  So, if that's a primary reason for installing Ubuntu, don't waste your time.

2) Be sure to use the Vista Disk Management utility to shrink your Vista OS partition to make room for Ubuntu. Do NOT allow the Ubuntu installer to do this.  If you do, you run the risk of corrupting your Vista install and rendering it unbootable.

3) If you don't have a Vista installation DVD, go to the link below, download and burn the appropriate Vista Recovery CD (which will then allow you to repair the Vista boot loader, should it become damaged during your Ubuntu installation):

[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/]("http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/")

---

