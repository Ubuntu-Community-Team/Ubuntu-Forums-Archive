---
title: "is there anyone who can help me connect wirlessly!!"
date: 2009-10-08
forum: New to Ubuntu
---

### Post by scrypt on 2009-10-08
I have got A BCM4312 wlan card and no matter what i do I cannot connect wirelessl.

i have been trying for days to fix this with no luck.

admitedly I have had some help. but i feel somebody can help me rectify this.

I am a begginer so please keep this in mind before posting any commands.

Wheres chili555 when you need him???

is there anyone who can help me fix this!!!

---

### Post by pedro3005 on 2009-10-08
Run this on a terminal:
[B]```
sudo apt-get install b43-fwcutter
```
[/B]When you are asked "Fetch and install firmware?" answer "Yes" (just press "Enter).
Reboot and see if that works for you. Tip extracted from here: [http://linuxwireless.org/en/users/Drivers/b43](http://linuxwireless.org/en/users/Drivers/b43)
But that page is a bit advanced.

---

### Post by lkraemer on 2009-10-09
Try:
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-bc33832c0547766a33c3a84f13f971ca757b2851](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-bc33832c0547766a33c3a84f13f971ca757b2851)

lk

---

