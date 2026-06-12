---
title: "Mobile Broadband Not Detected"
date: 2014-06-23
forum: Networking &amp; Wireless
---

### Post by fathuzzaman on 2014-06-23
This is always the most annoying problem in my experience with Linux. I can't see "Enable Mobile Broadband", unless I log into Windows, then restart into Linux. It's very not convenient. Sakis3g used to solve it back when I used Mint 16, but none of sakis3g or usb_modeswitch works anymore. lsusb said that my modem is already in modem-mode, yet the option "Enable Mobile Broadband" is still not there. Any suggestion?

Thanks before.

--
Win7 x64 / Ubuntu 14.04 x64
Huawei E173

---

### Post by varunendra on 2014-06-26
What does this show us -
```
lsusb
dmesg | tail -40
```
..both commands run after about 30 seconds from plugging in the modem.

And in the "Disk Utility" gui, do you see the modem mounted as a CD? Try ejecting it from there and see if the system recognizes it as a modem.

---

### Post by dropdeadfriend on 2014-10-08
there's a startup script that I found to be useful... posted in another forum [http://askubuntu.com/questions/82255/how-do-i-permanently-enable-mobile-broadband-on-boot](http://askubuntu.com/questions/82255/how-do-i-permanently-enable-mobile-broadband-on-boot)

 In a terminal,
  sudo gedit /etc/rc.local
  Now add this line above exit 0
  (while :; do nmcli -t nm wwan on; sleep 1; done)&
  Save the file and exit.

---

