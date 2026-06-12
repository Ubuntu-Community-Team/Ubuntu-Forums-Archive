---
title: "BELKIN F5D7000 help"
date: 2006-10-08
forum: Networking &amp; Wireless
---

### Post by nu_606_usr on 2006-10-08
ive recently installed ubuntu 6.06. i've completly updated my system. I've tried 2 different tutorials on patching my wireless card driver with madwifi. 
the 2 tutorials are..

[http://www.turkeyfarm.net/blog/2006/06/22/cracking-wep-with-linux-actually-works/](http://www.turkeyfarm.net/blog/2006/06/22/cracking-wep-with-linux-actually-works/)
[http://www.syserr.com/?page_id=6](http://www.syserr.com/?page_id=6)

when i do " ifconfig ath0 down " from the first tutorial i get

[[IMG]http://img132.imageshack.us/img132/5711/screenshotwj6.th.png[/IMG]](http://img132.imageshack.us/my.php?image=screenshotwj6.png)

here is a screen cap of my device manager

[[IMG]http://img139.imageshack.us/img139/2167/devicemanagerbv1.th.png[/IMG]](http://img139.imageshack.us/my.php?image=devicemanagerbv1.png)

im new to this, so im kind of lost. i have my cable line running fine, im using ubuntu to make this post. any help would be appreciated,


Thanks

---

### Post by erbedo on 2006-10-08
It means that you've not the ath0 interface. Don't worry, go ahead in the tutorial and it'll work fine :)

---

### Post by nu_606_usr on 2006-10-08
thanks much for your help.

i goto next step, they work fine, then when i do this command...

" make && make install "

i get this error...

" Makefile.inc:113: *** KERNELPATH: /lib/modules/2.6.15-27-386/build does not exist.  Stop. "

i have complete updates done. you have another working sugguestion for this problem too? ;]


Thanks



P.S.

[http://www.turkeyfarm.net/blog/2006/06/22/cracking-wep-with-linux-actually-works/](http://www.turkeyfarm.net/blog/2006/06/22/cracking-wep-with-linux-actually-works/)
that is the tutorial i am following.

---

### Post by erbedo on 2006-10-09
Sure :)
You're running a 2.6.15-27 kernel, the standard from ubuntu, but the module you're tring to build needs kernel-source.
I suggest you to follow this guide:
[https://wiki.ubuntu.com/KernelCustomBuild](https://wiki.ubuntu.com/KernelCustomBuild)
steb-by-step. Then reboot into your new kernel (update grub) and try to do make && make install again :)

---

