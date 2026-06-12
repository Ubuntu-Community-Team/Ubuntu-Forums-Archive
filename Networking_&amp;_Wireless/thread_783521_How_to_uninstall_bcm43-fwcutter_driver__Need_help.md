---
title: "How to uninstall bcm43-fwcutter driver ? Need help"
date: 2008-05-05
forum: Networking &amp; Wireless
---

### Post by Afif K fiska on 2008-05-05
I want to uninstall driver bcm43xx-fw cutter from my hardy, cause now, i have b43 driver from update manager. Need some sugestion too, which one better, ndiswrapper or b43 driver for broadcom 4318 rev 2 ? Please help...

---

### Post by Ayuthia on 2008-05-05
> **Afif K fiska said:**
> I want to uninstall driver bcm43xx-fw cutter from my hardy, cause now, i have b43 driver from update manager. Need some sugestion too, which one better, ndiswrapper or b43 driver for broadcom 4318 rev 2 ? Please help...
As long as /etc/modprobe.d/blacklist has this entry:
```
blacklist bcm43xx
```it should not use the bcm43xx driver.

As for the 4318 rev 02, either one should work.  I would try out the b43 driver first and if you don't like it, go to NDISwrapper.  It is much easier to do it this way than it is to go from NDISwrapper back to b43.

---

### Post by Afif K fiska on 2008-05-05
thanks for the answer. I'll try your advice. Sorry, could you give the complete command to see my blacklist list. I forgot

---

### Post by Afif K fiska on 2008-05-05
is this command is correct to see my blacklist list ? :

sudo gedit /etc/modprobe.d/blacklist

---

### Post by RequinB4 on 2008-05-06
I wouldn't suggest picking fwcutter over ndiswrapper - use this for ndiswrapper:

[http://ubuntuforums.org/showthread.php?t=766560](http://ubuntuforums.org/showthread.php?t=766560)

if you don't have an internet connection, manually download every wget.  You can place the liveCD in to get ndiswrapper, and if cabextract isn't installed already, you can get it from packages.ubuntu.com

---

### Post by Ayuthia on 2008-05-06
> **Afif K fiska said:**
> is this command is correct to see my blacklist list ? :

sudo gedit /etc/modprobe.d/blacklist

You might try:
```
gksu gedit /etc/modprobe.d/blacklist
```It will bring up a GUI version for you to enter the password.

---

### Post by Afif K fiska on 2008-05-06
> **RequinB4 said:**
> I wouldn't suggest picking fwcutter over ndiswrapper - use this for ndiswrapper:

[http://ubuntuforums.org/showthread.php?t=766560](http://ubuntuforums.org/showthread.php?t=766560)

if you don't have an internet connection, manually download every wget.  You can place the liveCD in to get ndiswrapper, and if cabextract isn't installed already, you can get it from packages.ubuntu.com

Thanks for your advice, cause i'm still a beginer, i would try the easiest way. Maybe if i'm succesfull in the first step, i'll try to replace it with ndiswrapper

---

### Post by drunkmatador on 2008-05-06
I'm still trying to figure out which one is better. Neither is wanting to work very well for me but I know it's a matter of time before I figure this out and then no more XP for me.

---

### Post by Afif K fiska on 2008-05-06
> **Ayuthia said:**
> You might try:
```
gksu gedit /etc/modprobe.d/blacklist
```It will bring up a GUI version for you to enter the password.

Thanks again, it's show the same result with the sudo. This forum and it's community is amazing

---

