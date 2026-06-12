---
title: "Resolution problems"
date: 2010-10-11
forum: New to Ubuntu
---

### Post by gfunk43 on 2010-10-11
I have just installed Ubuntu 9.10 on a lenovo laptop.  The problem is that the computer reports a maximum resolution of 848x600 which makes it quite difficult to use.  I got this number both by going to displays and by using xrandr.  

Further more I searched for the xorg.conf file and it is not in /etc/X11

locate xorg.conf returns

/usr/share/man/man5/xorg.conf.5.gz

Does anyone know how to get the machine to recognize higher resolutions?

Thanks

---

### Post by yetiman64 on 2010-10-11
First thing to try is, go to System > Administration > Hardware Drivers and check if a non-free driver is available. If there is one, select and activate it, allow it to download and install, and reboot the machine when done. This will usually allow higher resolutions to be used if a driver is available.
What is your video card etc?, use in terminal,
```
sudo lspci | grep VGA
```

---

