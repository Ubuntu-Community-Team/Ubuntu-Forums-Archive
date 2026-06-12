---
title: "pls help me install graphics driver"
date: 2011-01-01
forum: New to Ubuntu
---

### Post by hanzj on 2011-01-01
We want to play Revenge of the Titans and according to [http://www.puppygames.net/support/](http://www.puppygames.net/support/)

> 
**Game exits instantly, usually when clicking on any title screen buttons**

                 A problem with proprietry ATI OpenGL drivers for Linux.
                 *Free open source ATI drivers seem to work, such as the [Radeon driver]("https://help.ubuntu.com/community/RadeonDriver").*


>  lspci -nn | grep VGA
05:00.0 VGA compatible controller [0300]: ATI Technologies Inc R480 [Radeon X850XT Platinum (PCIE)] [1002:5d4d]




[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver) gives a list of those devices that have good 3D acceleration support. My R480 is  on the list! 
. We have a fresh install of  Ubuntu 10.10. I've just done

```
sudo add-apt-repository ppa:xorg-edgers/ppa
```



But now I'm not sure what the next step is.

Please help.

---

### Post by wojox on 2011-01-01
Go to System > Administration > Synaptic Package Manager and click the "Mark All Upgrades" button. Then restart once installed.

---

### Post by hanzj on 2011-01-01
but don't i need to select the packages I want to download from the new PPA?

---

### Post by sandyd on 2011-01-01
> **hanzj said:**
> but don't i need to select the packages I want to download from the new PPA?
doing what the previous poster said will upgrade your radeon packages to the version in the xorg ppa

p.s. the gallium drivers (if your card is supported) are really awesome.

---

### Post by hanzj on 2011-01-09
ok, i did the update manager thing. how can i check whether i have tho new driver from xorg ppa?

---

### Post by Argosse on 2011-01-09
easiest way search installed pkgs thru your graphical pkg mgr for the terms xorg, ati, and radeon seperately. and see what comes up for each. newer cards I think work under fglrx well but not for my  card so i wont guess   i can help ya with xorg drivers though they fixed my gl and HW acceleration on my radeon 9550 by forcing kms at boot thru grub

---

