---
title: "How do I to temporary unlock my modem like windows"
date: 2015-01-21
forum: Networking &amp; Wireless
---

### Post by wert2 on 2015-01-21
I need a huawei modem unlocker for Ubuntu 14. My modem is a permanently locked one(Customized Firmware). So I usually temporary unlock it  in windows 7, and then reboot and boot to Ubuntu for it to work. However I share my pc with other users and they cannot understand or perform the method of booting to windows for unlocking followed by rebooting to Ubuntu, every time they need to use internet. Here is a link to the software I use on windows 7 to temporary unlock my modem: [http://cdn2.geek.ng/wp-content/uploads/2012/11/Huawei-Modem-Unlocker.zip](http://cdn2.geek.ng/wp-content/uploads/2012/11/Huawei-Modem-Unlocker.zip). I have tried using this on wine but it cannot detect any ports. I have tried using the "mcphail/linux_huawei_unlocker" but is doesn't work with modern modems such as my e173 u-i as the developer himself "Neil McPhail" told me. I have tried using the following command prompt methods:[https://zenu.wordpress.com/2011/05/19/unlocking-3g-modems-and-using-them-on-other-networks/](https://zenu.wordpress.com/2011/05/19/unlocking-3g-modems-and-using-them-on-other-networks/), [http://geekingnhacking.blogspot.com/2013/08/linux-tweaks-to-unlock-huawei-modem.html](http://geekingnhacking.blogspot.com/2013/08/linux-tweaks-to-unlock-huawei-modem.html), [https://girobiro.wordpress.com/2012/03/08/unlock-3g-usb-dongles-in-linux/](https://girobiro.wordpress.com/2012/03/08/unlock-3g-usb-dongles-in-linux/) but they all cannot unlock my device. As regards to using mobile partner to manually insert the unlock code when prompted, my modem has a customized firmware therefore the usual mobile partner unlock code prompt was removed and replaced with "only specified sim can be used on this modem". I have tried flashing it with firmwares but since it has a cutomized firmware from my simcard provider's company, It cannot be flashed with normal huawei firmware upgrades/downgrades. Linux Modem Manager does not prompt for unlock code as well. Please if enyone knows of a temporary modem unlocker that works in linux, please help. Also please inform honestly if I'm out of luck. Even Dc unlocker(paid) doesn't unlock my modem. Thanks

---

### Post by wert2 on 2015-02-25
here is the result ov lsb_release -a; uname -a; lsusb

No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.2 LTS
Release:    14.04
Codename:    trusty
Linux Private 3.13.0-46-generic #75-Ubuntu SMP Tue Feb 10 15:26:00 UTC 2015 i686 i686 i686 GNU/Linux
Bus 001 Device 004: ID 12d1:1436 Huawei Technologies Co., Ltd. E173 3G Modem (modem-mode)
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 046d:c018 Logitech, Inc. Optical Wheel Mouse
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

---

