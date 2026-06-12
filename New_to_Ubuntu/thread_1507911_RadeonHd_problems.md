---
title: "RadeonHd problems"
date: 2010-06-12
forum: New to Ubuntu
---

### Post by chezerian on 2010-06-12
I am currently using Ubuntu 10.04 on my laptop which has a mobility radeon 2600 and would like to install the radeonHD drivers and have tried using these instructions here

[https://help.ubuntu.com/community/RadeonHD](https://help.ubuntu.com/community/RadeonHD)

Unfortunately this results in the welcome screen (purple one) going really funny (the screen gets really bright starting from the center and works outwards). Nothing happens (left it for 10 minutes) but if i press the power button it initiates a shutdown.

Would appreciate help.

---

### Post by waynefoutz on 2010-06-12
> **chezerian said:**
> I am currently using Ubuntu 10.04 on my laptop which has a mobility radeon 2600 and would like to install the radeonHD drivers and have tried using these instructions here

[https://help.ubuntu.com/community/RadeonHD](https://help.ubuntu.com/community/RadeonHD)

Unfortunately this results in the welcome screen (purple one) going really funny (the screen gets really bright starting from the center and works outwards). Nothing happens (left it for 10 minutes) but if i press the power button it initiates a shutdown.

Would appreciate help.


Your card should be supported by the ATI Proprietary drivers. That's probably your best option.

boot into the recovery mode and use the utility to reset your graphics. Then use the System/Administration/Hardware Drivers and enable the ATI driver, if it's there.

---

### Post by chezerian on 2010-06-12
==================================================
 ATI Technologies Linux Driver Installer/Packager 
==================================================

Error: ./default_policy.sh does not support version
default:v2:x86_64:lib32::none:2.6.32-21-generic:; make sure that the version is being
correctly set by --iscurrentdistro

Removing temporary directory: fglrx-install.iH6UK0

---

### Post by chezerian on 2010-06-13
bump

Edit: I think it displays that because i installed some packages from the Xorgedgers repo(in order to try and get radeonhd to work) and it has updated packages and screwed up package management.
I have since removed the repo.

---

### Post by KdotJ on 2010-06-13
This sounds like a similar issue to what I sometimes get, I too have an ATI Radeon card, a 32000HD. This only happens to me only say 1 in 300 boots. It boots to the purple screen and then goes a bit crazy, it has a white area and then it grows and it gets so bright it looks like my screen is going to explode.

Holding down the power button shuts down my laptop and then when I turn it on again its fine.
I'm guessing this happens every time for you though?

---

### Post by chezerian on 2010-06-14
yeah i booted 3 times and each time it was the same. (what you described)

---

### Post by chezerian on 2010-06-14
Tried it again, except radeonhd failed 5 times. How would i go about fixing the situation ?

---

### Post by clhsharky on 2010-06-14
chezerian


This will take you to default radeon.

With PPA removed.

From grub menu choose recovery mode.(hold down shift key for grub)

Start in safemodeX and use terminal or tt(F1).
If you cant start in safemodeX use root shell and log in.
I like safemodeX so you can copy/paste code.

```
sudo apt-get update
sudo apt-get remove --purge fglrx*
sudo apt-get remove --purge xserver-xorg-video-ati xserver-xorg-video-radeonhd
sudo apt-get install xserver-xorg-video-ati
sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core
sudo dpkg-reconfigure xserver-xorg
```

Reboot or

```
sudo restart gdm
```
if in terminal or tt

```
startx
```
if in shell.

Sharky

---

### Post by chezerian on 2010-06-14
I can get to a desktop fine and radeon works fine. But i want to use radeonhd so I can play nexuiz.

---

### Post by ubunterooster on 2010-06-14
Did you get the drivers from "hardware drivers" under "administration"

---

### Post by sandyd on 2010-06-14
> **chezerian said:**
> bump

Edit: I think it displays that because i installed some packages from the Xorgedgers repo(in order to try and get radeonhd to work) and it has updated packages and screwed up package management.
**I have since removed the repo**.
Heres the problem. Just because you remove it from the repo sources does not mean the programs that come with it are uninstalled/updated back to the normal versions.

run this
```

sudo add-apt-repository ppa:xorg-edgers/ppa
sudo apt-get update
sudo ppa-purge ppa:xorg-edgers/ppa
sudo apt-get install fglrx

```
restart.

---

### Post by chezerian on 2010-06-26
Thanks, that last one worked.

---

