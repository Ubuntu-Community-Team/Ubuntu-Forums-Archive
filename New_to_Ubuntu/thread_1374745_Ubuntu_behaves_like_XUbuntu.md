---
title: "Ubuntu behaves like XUbuntu"
date: 2010-01-07
forum: New to Ubuntu
---

### Post by Sapfeer on 2010-01-07
It is so till login screen. I mean that when I boot my computer, Ubuntu shows a splash screen with mouse instead of Ubuntu logo and in the login screen it shows XUbuntu login screen... It began when I upgraded to previous kernel, I suppose, but I'm not sure... I can't say that it annoys me very much, but I would like to see what I got... What is the reason of such strange behavior and how can I make my system shows correct labels?..

---

### Post by ajgreeny on 2010-01-07
I presume you must at some point have installed the xubuntu-desktop, either because you ran xubuntu, or you have added it separately.

To go back to the standard ubuntu splash and so on, try ```
sudo dpkg-reconfigure usplash
```
It will probably show you two or more options available, so pick the ubuntu version and then if you want uninstall the other and reboot.

---

### Post by Sapfeer on 2010-01-07
**ajgreeny**
Nice idea, but no effect in my case... Here is the output:
```
/home/user $ sudo dpkg-reconfigure usplash
update-initramfs: Generating /boot/initrd.img-2.6.31-17-generic
```That's all I've got...

---

### Post by Sapfeer on 2010-01-07
I've made it out just removing xubuntu and xsplash packages, but now I want to get karmic splash and login screens, vast amount of which I found at [Artwork /Incoming/ Karmic - Ubuntu Wiki](https://wiki.ubuntu.com/Artwork/Incoming/Karmic/), but I'm unable to find any way to download one...[]("http://fsdasf/")

---

