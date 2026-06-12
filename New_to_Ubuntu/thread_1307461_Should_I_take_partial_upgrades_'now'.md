---
title: "Should I take partial upgrades 'now'??"
date: 2009-10-31
forum: New to Ubuntu
---

### Post by leonardo_neo on 2009-10-31
I installed 9.10 beta a month ago.

I read in the forum, that most of time one should 'avoid' partial upgrades, until the dependencies are fulfilled. Ever since I installed 9.10 beta, the update manager is offering "partial upgrade" only, so I am avoiding that.

Till now I was doing only "sudo apt-get update" and "sudo apt-get upgrade"

I was also making sure, that after these commands, I should not 'remove' any packages. So till date, the following packages are not being upgraded 
> Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  evolution-plugins libpulse-browse0 libpulse-mainloop-glib0 libpulse0
  linux-generic linux-headers-generic linux-image-generic pulseaudio
  pulseaudio-esound-compat pulseaudio-module-bluetooth pulseaudio-module-gconf
  pulseaudio-module-udev pulseaudio-module-x11 pulseaudio-utils ubuntu-desktop
  xserver-xorg-input-all
0 upgraded, 0 newly installed, 0 to remove and 16 not upgraded.


also, till date my kernel version is [B]2.6.31-11-generic
[/B]

So here is my question:
1. **Since the final release is available now, should I go for the partial upgrade that update manager is offering now?**
2. **Should I upgrade the kernel version, if yes how?**
3. **The packages which are kept back for last 1 month (mentioned above), what I am supposed to do about that?**

Thank you all in anticipation. :)

---

### Post by snkiz on 2009-10-31
Since karmic is final now you need to do a disto upgrade so the system can properly resolve dependencies. Those packages have been kept back because some other packages need to be removed to  install them, a normal upgrade doesn't do that. from a command line you can run ```
sudo apt-get update ; sudo apt-get dist-upgrade
```
or a gui <alt>F2 gksu "update-manager -d"

with either option pay attention to what is being removed and why. If it looks fishy post the output here. Good luck :)

Edit: I should say those packages need something removed or installed that you don't already have. a regular upgrade does neither.

---

### Post by leonardo_neo on 2009-10-31
Thanks **snkiz** for the detailed advice. I did the dist upgrade.

---

