---
title: "ltsp + fake pae / forcepae"
date: 2014-09-29
forum: Networking &amp; Wireless
---

### Post by david_r2 on 2014-09-29
I've been trying to boot ltsp 12.04 on an IBM Thinkpad T41, but PAE is not supported by its processor (or it is but it just doesn't flag). I found many ways of forcing PAE or using fake-pae, but none of them work on LTSP or LAN boot. I tried this method [http://forum.ubuntu-fr.org/viewtopic.php?id=1594841](http://forum.ubuntu-fr.org/viewtopic.php?id=1594841) but it won't even build the client and says error in the end.

Help please!!!
Note: the LTSP server runs an AMD-64

---

### Post by david_r2 on 2014-10-16
Nevermind. I found some solution. For those who want to know how I managed it:

I basically installed a compatible debian kernel
1) add the following line at the end of the file /opt/ltsp/i386/etc/apt/sources.list :
deb [http://security.debian.org/debian-security](http://security.debian.org/debian-security) wheezy/updates main

2) using chroot /opt/ltsp/i386 install debian's linux-image-3.2.0-4-486:
apt-get linux-image-3.2.0-4-486

3) undo step 1 and then exit chroot

4) sudo ltsp-update-sshkeys
sudo ltsp-update-kernels
sudo lts-update-image --arch i386

---

