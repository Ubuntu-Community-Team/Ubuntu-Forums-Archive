---
title: "Eagle USB - Tiscali UK"
date: 2005-10-14
forum: Networking &amp; Wireless
---

### Post by turquaz on 2005-10-14
Well, i have been using Ubuntu since the first gnome 2.8 release, and my usb modem worked just fine. 
Well with the new release i cant conect to the web, i get an error 45, when i downloaded the new drivers 
from eagle usb official page, i cant configure it because gcc is different, the one used to compile the kernel, and the current release.
I installed 3.x gcc aswell, still cant manually install the eagle-usb drivers. any help will be appreciated.. many thanks

---

### Post by eexpress on 2005-11-13
i also use egale usb adsl modem. it works well with hoary, but breezy, i can not let it operation. and i had tested the old version 1.9.9 which comes from hoary. also. i think is a bug.
```
# module loaded ?        [ OK ]
# modem operational ?    [ KO ]
# Config vpi/vci/encapsulation/isp :  23 3 (none) CN13
# dhcpclient launched ?
# Service for connection [ OK ]
# ping IP ?              [ KO ]
# test DNS resolution ?  [ KO ]

```
```
$ sudo eaglectrl -w
Sending options to device /proc/bus/usb/004/003
Unable to send options to driver: Unknown error 512
Failed to send options to device /proc/bus/usb/004/003
```

---

### Post by mips on 2005-11-13
Ask the author if an English translation is available for link below as it is a 5.10 HOW-TO for eagle USB devices:
[http://forum.ubuntu.pl/viewtopic.php?t=1494](http://forum.ubuntu.pl/viewtopic.php?t=1494)

or maybe use an online translator.

[http://ubuntuforums.org/showthread.php?t=71293&highlight=Eagle](http://ubuntuforums.org/showthread.php?t=71293&highlight=Eagle)
[http://ubuntuforums.org/showthread.php?t=44459&highlight=Eagle](http://ubuntuforums.org/showthread.php?t=44459&highlight=Eagle)
[http://ubuntuforums.org/showthread.php?t=61827&highlight=Eagle](http://ubuntuforums.org/showthread.php?t=61827&highlight=Eagle)

---

### Post by artux on 2006-07-03
I hope you fixed your adsl usb modem problems with Eagle-usb. If not then I can give you some hints:

**code:**
sudo gedit /etc/eagle-usb/eagle-usb.conf

This will open the the eagle-usb configuration file.  Only one thing was important for me to make my usb-modem WORK, which is the VCI, VPI configuration numbers.

you will find something like this in the text:

# VPI / VCI are in hexa 
# for example, (8, 23) is (8,35) in decimal
VPI=00000008
VCI=00000050


Try to know what is your VPI & VCI numbers and then replace them here. Make sure you save afterwards.

Remember that VCI number is written in Hexadecimal, it is actually 80. This might be tricky.

---

