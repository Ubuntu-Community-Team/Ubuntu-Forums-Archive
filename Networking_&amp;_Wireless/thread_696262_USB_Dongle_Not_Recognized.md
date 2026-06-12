---
title: "USB Dongle Not Recognized"
date: 2008-02-13
forum: Networking &amp; Wireless
---

### Post by tomcollins165 on 2008-02-13
Okay, So Ive switched to Xubuntu from XP, and the D-Link dongle I had was working fine, after a while it started to develop the dropping connection after a couple minutes described in other posts. Thinking it was a hardware issue I went out and bought the exact same one again (D-Link DWA-130).

Now the computer wont recognize either the new or old one.

If I go to system-Network and in the Network Address space put 127.0.0.1 it successfully pings (dont even know what that means:(), but thats all I can get out of it. Not recognized at all otherwise, and the light on the dongle which blinks to show a connection is off (even though ive checked it on an XP laptop and it works on it)

If someone could help it would be AMAZING...but please spell it out, as my experience with linux is virtually nil.

---

### Post by mrsteveman1 on 2008-02-13
OK, im fairly sure the hardware still works, but for the moment lets make sure.

Open a terminal, and run the following commands with the device connected:

```
sudo lsusb
sudo ifconfig -a
sudo route
```

---

