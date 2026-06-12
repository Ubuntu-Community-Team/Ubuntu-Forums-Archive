---
title: "Trouble installing Wifi driver in ubuntu 14 LTS"
date: 2014-09-15
forum: Networking &amp; Wireless
---

### Post by 22990atineshgmail on 2014-09-15
I've installed Ubuntu 14 LTS with dual boot Wndows 8.1(Preinstalled). I've trouble configuring wifi driver in ubuntu 14. I don't have access to internet through LAN. So I've searched and found one offline solution. But it didn't worked I'm getting error message saying 
[B]
"ERROR! Bad return status for module build on kernel: 3.13.0-32-generic (i686)"[/B]

I'm installing these packages
bcmwl-kernel-source_5.100.82.38+bdcom-0ubuntu3.2_i386.deb
dkms_2.1.1.2-5ubuntu1_all.deb

Command I'm using

sudo dpkg -i dkms*.deb
sudo dpkg -i bcmwl*.deb

[[IMG]http://img103.imagevenue.com/loc1039/th_763467573_ss_122_1039lo.jpg[/IMG]]("http://img103.imagevenue.com/img.php?image=763467573_ss_122_1039lo.jpg")

---

### Post by praseodym on 2014-09-15
Its too old, use this one instead (from 14.10):

[http://de.archive.ubuntu.com/ubuntu/pool/restricted/b/bcmwl/bcmwl-kernel-source_6.30.223.248+bdcom-0ubuntu1_i386.deb](http://de.archive.ubuntu.com/ubuntu/pool/restricted/b/bcmwl/bcmwl-kernel-source_6.30.223.248+bdcom-0ubuntu1_i386.deb)

[http://de.archive.ubuntu.com/ubuntu/pool/main/d/dkms/dkms_2.2.0.3-1.1ubuntu5_all.deb](http://de.archive.ubuntu.com/ubuntu/pool/main/d/dkms/dkms_2.2.0.3-1.1ubuntu5_all.deb)

---

### Post by 22990atineshgmail on 2014-09-28
Thanx @praseodym
It worked

---

