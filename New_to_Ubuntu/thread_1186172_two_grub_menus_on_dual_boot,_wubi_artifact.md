---
title: "two grub menus on dual boot, wubi artifact"
date: 2009-06-13
forum: New to Ubuntu
---

### Post by ThailandTom on 2009-06-13
Had used 8.04 on the old computer. liked it - no problems.

So when i got a new machine, Toshiba Satellite L310, tried wubi with 9.04 jaunty - worked, so I uninstalled to do an install from disc, (supposedly better performance) but maybe the uninstall hung, or something... there is a slight problem.

I currently boot to a grub menu which allows me to boot 9.04 or scroll down to XP, the old os, which I still need.

When I choose xp, I get a second grub menu with xp or ubuntu - the wubi install artifact that never got uninstalled....

I believe this is affecting my performance: the screen display is always wrong on reboot to Jaunty, and there can be problems with internet connectivity. These may also be unrelated.

Thoughts? and Thanks...

---

### Post by briguy47 on 2009-06-13
> **ThailandTom said:**
> Had used 8.04 on the old computer. liked it - no problems.

So when i got a new machine, Toshiba Satellite L310, tried wubi with 9.04 jaunty - worked, so I uninstalled to do an install from disc, (supposedly better performance) but maybe the uninstall hung, or something... there is a slight problem.

I currently boot to a grub menu which allows me to boot 9.04 or scroll down to XP, the old os, which I still need.

When I choose xp, I get a second grub menu with xp or ubuntu - the wubi install artifact that never got uninstalled....

I believe this is affecting my performance: the screen display is always wrong on reboot to Jaunty, and there can be problems with internet connectivity. These may also be unrelated.

Thoughts? and Thanks...


If you edit your boot.ini file in the root directory for your XP drive, and remove the WUBI entry referring to ubuntu, it should stop the secondary boot loader from showing up.  :D

I hope that helps.  If you have any questions, let me know. :)

---

### Post by ThailandTom on 2009-06-14
problem solved

thanks briguy47

---

### Post by briguy47 on 2009-06-14
Glad I could help!  :D

If you keep having performance issues, maybe we can work on that too.  Just let me know. :)

---

