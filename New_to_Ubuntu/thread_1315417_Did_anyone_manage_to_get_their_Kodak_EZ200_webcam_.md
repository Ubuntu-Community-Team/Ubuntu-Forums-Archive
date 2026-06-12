---
title: "Did anyone manage to get their Kodak EZ200 webcam working in Karmic Koala?"
date: 2009-11-05
forum: New to Ubuntu
---

### Post by am05w33 on 2009-11-05
Hi there,

I just got an old digital camera a Kodak EZ200 which works fine for Skype in Windows XP after downloading drivers from Kodak website . But when I tried to use the same in Karmic Koala, the video does not seem to work.  Just want to know anyone had any success with the same camera using Ubuntu 9.10 as kodak does not provide any drivers for linux.

---

### Post by aktiwers on 2009-11-06
Have you tried some of the stuff from here?
[https://help.ubuntu.com/community/Webcam](https://help.ubuntu.com/community/Webcam)

---

### Post by am05w33 on 2009-11-07
> **aktiwers said:**
> Have you tried some of the stuff from here?
[https://help.ubuntu.com/community/Webcam](https://help.ubuntu.com/community/Webcam)


Thanks for responding aktiwers!

Yup was trying it out but already stuck at the first command on ls /dev/video*
Before I plugged in my webcam,
amos@ubuntu:~$ ls /dev/video*
/dev/video0  /dev/video24  /dev/video32

After I installed my webcam and ran the command again, the result is still the same.
amos@ubuntu:~$ ls /dev/video*
/dev/video0  /dev/video24  /dev/video32
amos@ubuntu:~$ 

Under Cheese Preferences menu and Skype Options for Video Devices , the webcam device only lists the 3 video0, video24 & video 32 as being used by my Hauppauge WINTV PVR-150 TV tuner card.

I know that my EZ200 is recognised as I use "lsusb" to check the usb devices attached to my machine and the camera is listed.

amos@ubuntu:~$ lsusb
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 0bb4:0c03 High Tech Computer Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 002: ID 04fc:05d8 Sunplus Technology Co., Ltd 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 004: ID 040a:0300 Kodak Co. EZ-200
Bus 002 Device 002: ID 0609:031d SMK Manufacturing, Inc. eHome Infrared Receiver
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
amos@ubuntu:~$


any ideas anyone?

---

### Post by ublender on 2009-11-22
I am having the exact same issue. In fact, I even have the exact same tuner card and thus have the same /dev/video devices listed here. I had the same problem with jaunty as well. It would be really awesome if someone who has any knowledge regarding webcams in ubuntu could help.

---

