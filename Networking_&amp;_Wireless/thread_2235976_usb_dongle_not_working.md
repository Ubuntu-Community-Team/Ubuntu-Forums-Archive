---
title: "usb dongle not working"
date: 2014-07-23
forum: Networking &amp; Wireless
---

### Post by ramsubbu on 2014-07-23
I installed ubuntu 14.04 on my new dell inspiron 5437. everything works except the dongle. This is a vodafone datecard with its linux software. the icon is there on the desktop but clicking it leads to nowhere! Tried the usb-modeswitch too but not to any success. Doesnt show up in the mobile broadband connections. lsusb shows up the dongle. . . 
Thanks in advance.
Rams.
Love and Peace. . .

---

### Post by varunendra on 2014-07-24
Please unplug the modem > wait about 10-15 seconds > replug it > wait about 30 seconds > open a terminal (Ctrl-Alt-T) and post back the outputs of -
```
lsusb
dmesg | tail -40
```

Along with the outputs, can you also post cropped, tiny screenshot of the icon of the application you have installed (showing its full name also) ?

If you no longer need to provide your login password when running some command with "sudo", you should read this post for your own safety (written for a different application, but the effects may be same for the vodafone one that you have) : [http://ubuntuforums.org/showthread.php?t=2208626&p=12945156#post12945156](http://ubuntuforums.org/showthread.php?t=2208626&p=12945156#post12945156)

The instructions to reset the "sudo" behaviour to defaults, if needed : [http://ubuntuforums.org/showthread.php?t=2234181&p=13074564#post13074564](http://ubuntuforums.org/showthread.php?t=2234181&p=13074564#post13074564)

---

