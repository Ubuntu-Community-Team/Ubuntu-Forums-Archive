---
title: "Help Please,=! Ubuntu 16.04 and Broadcom BCM43142 offline installation"
date: 2016-04-03
forum: Networking &amp; Wireless
---

### Post by Steven_Goldman on 2016-04-03
Hi, can anyone help me get a Broadcom BCM43412 14e4:4365 working on a HP Stream.

Lubuntu 16.04 beta2 The kernel is 4.4.0-15.generic

The problem I have is that there is no ethernet connection on this machine so the install needs to be done offline, Please treat me like a noob

Many thanks in advance for any solution.

---

### Post by Hadaka on 2016-04-03
Hi, insert your media you used to load the os
then go to...

```

pool/main/d/dkms/dkms_XXXXX.deb
pool/restricted/b/bcmwl/bcmwl-kernel-source_XXXXX.deb
```
drag and drop both to your home directory. then do..

```
sudo dpkg -i *.deb
```
__________________________________________________
that's it

---

### Post by Steven_Goldman on 2016-04-03
> **Hadaka said:**
> Hi, insert your media you used to load the os
then go to...

```

pool/main/d/dkms/dkms_XXXXX.deb
pool/restricted/b/bcmwl/bcmwl-kernel-source_XXXXX.deb
```
drag and drop both to your home directory. then do..

```
sudo dpkg -i *.deb
```
__________________________________________________
that's it



Many Thanks, worked a treat in Kubuntu, don't think those files where there in Lubuntu though

---

### Post by Hadaka on 2016-04-03
Great ! glad that worked for you, thank you for
marking your thread solved,,it will help serchers.

---

### Post by Steven_Goldman on 2016-04-04
Once again thanks for your help. I can confirm these files are not in the Lubuntu medium however I managed to install the wifi by connecting my phone (Gal S4) as a USB modem (using my home wifi) and doing update, upgrade and dist-upgrade and reboot. After that I was able to use the additional drivers from preferences menu and install the Broadcom BCM43142 with the Linux STA Wireless bcmwl-kernel-source (proprietary)

---

### Post by Hadaka on 2016-04-04
Hi,
You could have also moved the 2 .deb files
From your **Kubuntu** install usb to your **Lubuntu** home directory 
Boot to **Lubuntu**,open a terminal, ctrl/alt/t
insert the **Kubuntu** install usb and do..

```

cp /media/*/pool/main/d/dkms/*.deb dk.deb

cp /media/*/pool/restricted/b/bcmwl/*.deb wl.deb
```
This copies both .deb files from the **Kubuntu** install usb,
 now named "**dk.deb** and **wl.deb**" to the **Lubuntu** home directory  
Then install..
```
sudo dpkg -i *.deb
```

---

