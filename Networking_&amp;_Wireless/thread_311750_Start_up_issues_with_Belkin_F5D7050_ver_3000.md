---
title: "Start up issues with Belkin F5D7050 ver 3000"
date: 2006-12-03
forum: Networking &amp; Wireless
---

### Post by N'Jal on 2006-12-03
I have gotten my belkin wireless card working as per these instructions

[https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_3000_%28Ralink_rt73_driver%29?highlight=%28WifiDocs%2FDevice%29](https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_3000_%28Ralink_rt73_driver%29?highlight=%28WifiDocs%2FDevice%29)

BUT i had to reinstall ubuntu about a week ago for some reason, but when i had my card working, the card could be detected on system start up, however now, i MUST boot the system without the card plugged in, else I will get NO network, even removing it and plugging it back in does not sort it, only restarting without it plugged in works, which is not showstopping, but when i wake up half asleep and boot my machine and don't remember it's annoying.

So if anyone knows how to activate the card on boot, i would be very happy.

I HAD it working previously in this thread [http://www.ubuntuforums.org/showthread.php?t=304943](http://www.ubuntuforums.org/showthread.php?t=304943)
It may contain any information and such i forgot here.

Thanks
Njal

---

### Post by N'Jal on 2006-12-05
Tried sticking rt73usb to the end of my /etc/modules file, to no avail.

---

### Post by jon3k on 2006-12-09
I'm getting a ton of errors compiling the module with the 3001 version of the card after following those directions.

I'm almost willing to go back and fight with the rt73usb driver that's in the repos at this point.

After installing build essentials and the right linux-headers package, anything else you had to do?

---

### Post by FrodoB on 2006-12-09
If you are going to add a module to /etc/modules it should be:

rt73

As rt73usb is the one that should be blacklisted and does not work correctly yet:

blacklist rt73usb
blacklist rt2570

> **N'Jal said:**
> Tried sticking rt73usb to the end of my /etc/modules file, to no avail.

---

