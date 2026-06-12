---
title: "BSNL EVDO modem not detecting in Ubuntu 12.04"
date: 2013-12-21
forum: Networking &amp; Wireless
---

### Post by hssrikanthrao on 2013-12-21
I have dell laptop, and ubuntu 12.04 is default OS. From last one week I am trying to connect my BSNL EVDO modem to my laptop. I did all the ways mentioned in the ubuntu forum, still I am not able to connect to internet. wvdial is installed. I have updated all the packages. At the end I am getting an error 'Sorry, no modem was detected!'. I tried in 3 different ways, but all the ways I am getting error. May I expect anybody help about the issue? I here with attached image of the one of the way I tried.

---

### Post by varunendra on 2013-12-22
Welcome to the forums Srikanth !

The problem with your modem is that it is one of those devices that have multiple personalities (e.g. cdrom/modem), and they need to 'Switch' their mode in order to be detected as a modem. However, as per the outputs in your screenshot, it hasn't changed its mode yet, which is a bit abnormal since usb_modeswitch package in Ubuntu 12.04 is aware of this device.

So, please try -
```
sudo usb_modeswitch -v 0x05c6 -p 0x2001 -M "5553424312345678000000000000061b000000020000000000000000000000"
```
Then run "lsusb" again. Do you see a changed ID? If yes, does it get detected by Network Manager or wvdial as a modem afterwards?

---

