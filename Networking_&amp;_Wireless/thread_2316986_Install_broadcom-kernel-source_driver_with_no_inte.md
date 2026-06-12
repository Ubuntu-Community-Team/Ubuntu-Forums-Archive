---
title: "Install broadcom-kernel-source driver with no internet"
date: 2016-03-12
forum: Networking &amp; Wireless
---

### Post by Hadaka on 2016-03-12
Please Verify installing the ***broadcom-kernel-source*** driver is correct per this guide..
[http://ubuntuforums.org/showthread.php?t=2214110](http://ubuntuforums.org/showthread.php?t=2214110)
The pci-id [[COLOR=#ff0000]**14e4:XXXX**[/COLOR]] determines what driver performs best with the wireles card.
**Example ->    **Broadcom Corporation BCM43142 802.11b/g/n [[COLOR=#ff0000]**14e4:4365**[/COLOR]]

You must have the ***installation USB/Media*** used to load Ubuntu.
***two*** files are needed to load the ***broadcom-kernel-source*** driver.
**1**-The ***broadcom-kernel-source*** file, also know as the ***"wl" ***driver.
**2**-The ***dkms*** file 

Insert the ***installation USB/Media*** and then 

To Install please open a terminal ctrl/alt/t 
then copy and paste one line at a time.
```

***sudo cp /media/*/pool/restricted/b/bcmwl/*.deb  wl.deb***
[B][I]sudo cp /media/pool/main/d/dkms/*.deb dk.deb
sudo dpkg -i *.deb[/I][/B]
***sudo modprobe wl***
```
boot and test wireless

---

