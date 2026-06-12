---
title: "Ubuntu 14.04 upgrade disables Broadcom Wireless Adaptor"
date: 2017-12-15
forum: Networking &amp; Wireless
---

### Post by sdtrott on 2017-12-15
I have Ubuntu 14.04 installed on a Dell E6400 laptop. My wireless connection was working fine until I accepted the upgrade from 4.2.0-42 to 4.4.0-103.  The installation of 4.4.0-103 disabled the Broadcom Wireless Lan controller 14e4:432b on my laptop, so even though Network connections claims the Broadcom driver is running, I cannot connect.  The only way I am able to connect is to take the extra step during boot by selecting Advanced Options and then selecting the previous version that worked (4.2.0-42).

I would like to know if it is possible to either remove the faulty upgrade (4.4.0-103) so that I can boot directly into the version of Ubuntu 14.04 that works, or fix the upgrade to 4.4.0-103 so that the wireless adaptor works. This is the second time I have had an Ubuntu installation ruined by an update.  If I ever get my wireless adaptor working under a current version of Ubuntu, I will never accept another destructive upgrade.

---

### Post by praseodym on 2017-12-16
Change the driver version:

```
sudo apt-get remove --purge bcmwl-kernel-source
sudo apt-get install linux-headers-$(uname -r) build-essential dkms
wget http://de.archive.ubuntu.com/ubuntu/pool/multiverse/b/broadcom-sta/broadcom-sta-dkms_6.30.223.271-7_all.deb
sudo dpkg -i broadcom-sta-dkms_6.30.223.271-7_all.deb 
```
Reboot

---

