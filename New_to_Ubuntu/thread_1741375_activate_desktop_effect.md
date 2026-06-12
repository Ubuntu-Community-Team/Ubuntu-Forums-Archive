---
title: "activate desktop effect"
date: 2011-04-28
forum: New to Ubuntu
---

### Post by usopkhan on 2011-04-28
**hi  there, i've just bought a lappy - asus A53s - with NVIDIA Geforce  GT540M 2GB ram. I've installed ubuntu 10.10 through wubi. After fresh  install, i updated it, then installed the restricted card driver. After  restart, I get a black screen of tty asking for login n pass. pls help  me to activate my desktop effect. I tried to reinstall, manually install  the driver from nvidia as root, tried using mint 9- (no drivers  detected when searching), still no avail.. need ur help man...Thank You**

---

### Post by bcbc on 2011-04-28
I think that card is an Optimus card - so you have an intel graphics driver and the nvidia is 'on demand' only and I don't think Ubuntu supports these yet. Therefore you should not have installed the nvidia drivers.

Here's a good thread: [http://ubuntuforums.org/showthread.php?t=1657660](http://ubuntuforums.org/showthread.php?t=1657660)
> What if I already installed the Restricted Driver, and now my computer is not booting X?
1. Boot into Recovery mode (GRUB). Start failsafe-X.
2. When you're in, go to System > Administration > Additional Drivers to deactivate the nVidia driver.
3. Move Xorg:
Code:
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.old
4. Reboot. Intel card should kick in.
-------

---

### Post by cucisan on 2011-06-27
hello

i have the same laptop and had problems with hybrid card (fan at fullspeed), touchpad not detected as touchpad (no scrolling etc) and wlan connection issues

i wrote a small howto to get those things working:
[http://ubuntuforums.org/showthread.php?t=1791081](http://ubuntuforums.org/showthread.php?t=1791081)

maybe it usefull for you

---

