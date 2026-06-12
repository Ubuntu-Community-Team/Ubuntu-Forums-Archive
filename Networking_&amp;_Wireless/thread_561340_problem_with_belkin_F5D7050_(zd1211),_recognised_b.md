---
title: "problem with belkin F5D7050 (zd1211), recognised but nothing more."
date: 2007-09-27
forum: Networking &amp; Wireless
---

### Post by marshall.robert on 2007-09-27
Hi. 

I have installed the Ubuntu 7.04 CLI version on my craptop (Compaq Presiaro 1690) and since it has no wired network interface i am using my Belkin usb dongle, it works as soon as i plug it in on my desktop machine without any problems and receives a better signal that my PCI card, but when i plug it in to my craptop (which i have to do before booting) it is detected as eth0 (also ethX on my desktop), which is all fine, except when i run "iwlist scan" it just says "No scan results" even when in the same room as the router.

I have tried ndiswrapper, the only change, if any, being that it is no longer recognized.

I get the same result when replicated on a virtual machine.

So as it stands im stuck without a GUI and no working connection to the internet to install one...

All help will be greatly appreciated, thanks.

-rob

---

### Post by linuxwizard on 2007-09-27
Look over this may be something will help you.

[https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_4000_%28ZyDas_zd1211b_driver%29](https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_4000_%28ZyDas_zd1211b_driver%29)

---

### Post by marshall.robert on 2007-09-27
ok, cheers, ill try that, given i dont have internet it should be somewhat challenging.

if anyone else has any ideas they are very welcome



(finally) figured it out, i needed to run sudo ifconfig eth0 up, then sudo /etc/init.d/networking restart after editing the config files.....

---

