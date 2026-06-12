---
title: "Normal Login AppArmor reference? (having security issues at time of post)"
date: 2010-07-08
forum: New to Ubuntu
---

### Post by UbuNoob001 on 2010-07-08
Guys/Gals, 
   I am new to Linux. In the last week, I have noticed this upon login (this is from /var/log/boot.log) as I don't use a splash screen. 

```
fsck from util-linux-ng 2.17.2
/dev/sda5: clean, 186372/5865472 files, 5553130/23451136 blocks (check in 2 mounts)
init: Failed to spawn network-manager main process: unable to execute: No such file or directory

 * Starting AppArmor profiles       [80G Skipping profile in /etc/apparmor.d/disable: usr.bin.firefox

[74G[ OK ]
 * Setting sensors limits       [80G 
[74G[ OK ]
```

I am referencing the AppArmor portion as I have never used/configured AppArmor and I have been having issues with spam being used in my email (from both Linux and Windows box). Reference: [http://ubuntuforums.org/showthread.php?t=1526371](http://ubuntuforums.org/showthread.php?t=1526371)

does this seem normal to have shown up without me doing anything with AppArmor?

---

### Post by cariboo on 2010-07-09
The apparmor profile is disabled for firefox by default, for minof on enabling the profile, have a look [here]("https://help.ubuntu.com/community/AppArmor")

---

### Post by Rubi1200 on 2010-07-09
As cariboo907 already pointed out, the Firefox profile for AppArmor is disabled by default.

However, AppArmor itself is loaded at boot, so the message you see is quite normal.

From a terminal run this to see what is going on:

```
sudo apparmor_status
```

This link also provides more information:

[http://ubuntuforums.org/showthread.php?t=1008906](http://ubuntuforums.org/showthread.php?t=1008906)

---

### Post by UbuNoob001 on 2010-07-09
Thanks for the help all :)

---

