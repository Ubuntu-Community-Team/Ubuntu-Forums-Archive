---
title: "Do not use NDISWRAPPER for 14E4:4320,  Broadcom 4306!"
date: 2008-08-25
forum: Networking &amp; Wireless
---

### Post by helpdeskdan on 2008-08-25
Ndiswrapper worked like a charm - UNTIL hardy.  No matter what I did, it worked, at best, really flaky.  Upgraded ndiswrapper, wpa_supplicant - nothing worked.  Even doing it command line didn't work - it would associate, but you couldn't ping.  Change the SSID to Null, and let it change it's self back, and sometimes it would work. 

The native driver seems to work very well when fixed.  Do a dmesg | less and look for:
[ 6000.517737] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found or load failed.
[ 6000.517754] b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 4).
[ 6001.067238] input: b43-phy0 as /devices/virtual/input/input6

If you see it, you can follow the instructions here:

[http://www.omattos.com/broadcom/](http://www.omattos.com/broadcom/)

Referenced from crazyguy:
[http://ubuntuforums.org/showthread.php?p=4836897](http://ubuntuforums.org/showthread.php?p=4836897)
(Many thanks to them)

---

