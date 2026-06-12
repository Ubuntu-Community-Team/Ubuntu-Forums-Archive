---
title: "Unable to activate wireless"
date: 2010-08-29
forum: New to Ubuntu
---

### Post by skrapster on 2010-08-29
I have recently installed Ubuntu 10.04 on an acer aspire 3690 using wubi. All is well except I can't activate the wireless. It used to work fine in Windows Vista.

The wireless card is Broadcom BCM4311. I have installed the nessesary drivers using ndiswrapper, and it seemed to work fine, but when I type "ifconfig wlan0 up" I get "SIOCSIFFLAGS: No such file or directory"

please help!!!!

---

### Post by MattBD on 2010-08-29
This thread might help you:
[http://ubuntuforums.org/showthread.php?t=1288865](http://ubuntuforums.org/showthread.php?t=1288865)
I've also had to install Broadcom's wireless drivers myself on two machines and all I did on Lucid was install Ubuntu, then reboot with the machine connected to my router via Ethernet, then it detected the hardware automatically and prompted me to install the drivers via the Restricted drivers dialogue, which I did, then rebooted and everything worked fine. Never had to use ndiswrapper at all.

---

### Post by skrapster on 2010-08-29
Thanks for the link, solved the problem :-)

---

