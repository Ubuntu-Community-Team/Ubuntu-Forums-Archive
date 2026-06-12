---
title: "Two Different Linux Kernels to Boot to?"
date: 2009-03-28
forum: New to Ubuntu
---

### Post by Penguin Guy on 2009-03-28
I appear to have the option to boot to two different Linux kernels (2.6.27-11-generic and 2.6.27-7-generic):

This is because the Linux kernel has been updated; when the kernel is updated the older one is not removed.
There is very little difference between the two.
It is a good idea to keep at least one older kernel in the case that the newer one fails.

To remove an older kernal open synaptic and type linux-image, then remove the one you want.

Thanks!

---

### Post by damis648 on 2009-03-28
You are correct. When Ubuntu updates it's kernel, it puts the new kernel atop the rest, leaving the rest as backups. If you happen to have a problem with the new kernel, you can boot back to the old. If the new kernel boots fine, feel free to remove the old one, or just comment it out of your menu.lst.

```
sudo apt-get uninstall linux-image-versionnumberyoudontwant
```

---

### Post by raymondh on 2009-03-28
You have an upgraded kernel in 27-11.... really no problem.  Remember though that some drivers are kernel specific (like the wifi in my MSIWind). Hence, before I UPGRADE, I make sure there's a compiled driver available. 

You can go system > administration > synaptic package manager and download/install a program called startup manager.  It allows you to configure your start-up page/Grub.

Enjoy.

---

### Post by Penguin Guy on 2009-03-28
Thanks; so for example if I wished to remove:

```
Ubuntu 8.10, kernel 2.6.27-7-generic
Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
```

What *exactly* would I type?

Thanks!

---

### Post by hyper_ch on 2009-03-28
new kernels are normally fine but a lot of things change in there. I had once the problem that the older kernel did work fine with my wifi card but a new not. This was then solved again one kernel newer. So in that case I always recommend to have the current kernel plus one older that you know works just fine.

If you want to remove it, open synaptic and search for "2.6.27-7" and then remove the installed packages.

---

### Post by BGFG on 2009-03-28
no need to type. open Synaptic, search 'linux-image' then just check the kernel you want removed. anything with 27-7.

---

### Post by Penguin Guy on 2009-03-28
Thanks for all the help! I'll follow your advice and leave an extra kernel in case something breaks.

:KS

---

