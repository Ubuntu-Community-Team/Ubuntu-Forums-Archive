---
title: "Dell Inspiron 13 7391 2in1 and Ubuntu 19.10 - no wifi"
date: 2020-03-20
forum: Networking &amp; Wireless
---

### Post by chagzuki on 2020-03-20
I got this laptop a few days ago and I wanted to give it a spin with Ubuntu so I installed it to an external HDD, but the wifi option isn't there. When I boot from the USB pen drive installer into the 'try Ubuntu' mode wifi works fine, but once I install it to the HDD the wifi option isn't available. The installation was done with wifi enabled, and with the option selected to download relevant drivers whilst installing. This is the first time I've installed Ubuntu in uefi mode; I'm accustomed to legacy. I'm not sure if memory serves me, but I think that the wifi option was actually missing when booting via the pen drive until I disabled secure boot, and then it became available. This made me think that secure boot was disabling wifi (I know very little about what secure boot actually does), but with it disabled there's still no wifi option when booting to HDD.

---

### Post by oldfred on 2020-03-20
With UEFI secure Boot on, proprietary drivers need to be installed with user interaction to set Secure boot keys. Ubuntu cannot verify proprietary drivers.
Often easier just to not have Secure boot on (for now).
You may be able to install by using wired Internet connection for install to then add driver(s). Typically nVidia and some Wi-Fi drivers are proprietary.

Issues often common across similar models. These may be very similar.
Dell 7791 UEFI update & some settings
[https://ubuntuforums.org/showthread.php?t=2431450&page=3](https://ubuntuforums.org/showthread.php?t=2431450&page=3)
Ubuntu 19.10 Provides Good Out-Of-The-Box Support For The Dell XPS 7390 Icelake Laptop
[https://www.phoronix.com/scan.php?page=article&item=dell-xps7390-ubuntu1910&num=1](https://www.phoronix.com/scan.php?page=article&item=dell-xps7390-ubuntu1910&num=1)
[https://www.phoronix.com/scan.php?page=news_item&px=Dell-XPS-7390-More-Options](https://www.phoronix.com/scan.php?page=news_item&px=Dell-XPS-7390-More-Options)
[https://wiki.ubuntu.com/Dell/XPS/XPS-13-7390-2-in-1](https://wiki.ubuntu.com/Dell/XPS/XPS-13-7390-2-in-1)
[https://ubuntuforums.org/showthread.php?t=2431791](https://ubuntuforums.org/showthread.php?t=2431791)
Dell XPS 15 Series 7590 (2019)
[https://askubuntu.com/questions/1161456/how-to-run-ubuntu-on-new-dell-xps-15-7000-series-7590](https://askubuntu.com/questions/1161456/how-to-run-ubuntu-on-new-dell-xps-15-7000-series-7590)
[https://github.com/TillmannBerg/Ubuntu-Dell-XPS-15-2019](https://github.com/TillmannBerg/Ubuntu-Dell-XPS-15-2019)

---

### Post by chagzuki on 2020-03-21
Thanks. So is there an obvious reason why wifi would work whilst trying  Ubuntu from the pen drive, but not from the hdd having installed with  secure boot switched off? It seems that if the pen drive trial version  works no unusual/additionaal drivers are required, and since secure boot  is off I can't see why those drivers would be disabled.

---

### Post by oldfred on 2020-03-21
Moved to wireless sub-forum.

Read the sticky and run the script. Those that know wireless issues then can help.

---

