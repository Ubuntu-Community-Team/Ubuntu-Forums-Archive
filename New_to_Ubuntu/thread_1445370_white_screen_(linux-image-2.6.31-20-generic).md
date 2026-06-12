---
title: "white screen (linux-image-2.6.31-20-generic)"
date: 2010-04-02
forum: New to Ubuntu
---

### Post by eulogiobatutay on 2010-04-02
Hi, **I upgrade ubuntu from 9.04 to 9.10**, during the course of the upgrade, I encountered some error message pertaining to **linux-image-2.6.31-20**... After the upgrade was complete, I can still use Ubuntu but after I restarted all I can see is white screen after I entered my username and password. I have searched for a some threads and nothings seems to work e.g. uninstalling compiz or xorg. I wasn't able to uninstall compiz because of the dependency problem in linux-image, this is also the problem when i try to uninstall xorg. I am just guessing that the problem might be in the broken linux-image-2.6.32.20... If so, I don't know how to fix it. Your help is very much appreciated.

---

### Post by agnes on 2010-04-02
Upgrades never really worked for me :(

You can't just successfully boot into an older kernel with GRUB? 

Also, you can reset Xorg (instead of uninstalling it). With the command: > sudo dpkg-reconfigure -phigh xserver-xorg
This will choose default values for almost all options in xorg.conf; and that might get the graphics for you working again.
For running this you can go to the recovery mode in GRUB, and drop to root prompt.

---

### Post by eulogiobatutay on 2010-04-02
> **agnes said:**
> Upgrades never really worked for me :(

You can't just successfully boot into an older kernel with GRUB? 

Also, you can reset Xorg (instead of uninstalling it). With the command: 
This will choose default values for almost all options in xorg.conf; and that might get the graphics for you working again.
For running this you can go to the recovery mode in GRUB, and drop to root prompt.

I did boot to an older kernel and it did work for me thanks... I was able to install the linux-image package... Now, my problem is in compiz, ubuntu just hang after a couple of seconds so what I did is uninstall the compiz package and it is now working... I don't know what seems to be the problem in here. It's really crazy, I tried figuring out a fix for this since yesterday but I'm still unable to make compiz work.

---

