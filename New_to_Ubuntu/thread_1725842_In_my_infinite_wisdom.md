---
title: "In my infinite wisdom"
date: 2011-04-10
forum: New to Ubuntu
---

### Post by danielgrosvenor on 2011-04-10
My attempts to install the latest Nvidia driver failed, so I popped into Software Centre and removed all drivers before attempting again in "[Ctrl]+[Alt]+[F1] mode".  Well I still failed to install them, but now I can't return to "normal mode" even after a reboot - presumably because I've removed all the graphics drivers!  Is there perhaps some Terminal command I can enter that'll restore Ubuntu to before I messed it up (or a good Recovery Tool on the DVD)?

---

### Post by TeoBigusGeekus on 2011-04-10
Try with
```
sudo apt-get install xserver-xorg-video-nouveau
```

---

### Post by coffeecat on 2011-04-10
@danielgrosvenor, also check and see if the incomplete attempt to install the nvidia driver resulted in the creation of the file /etc/X11/xorg.conf. If there is one and it refers to the nvidia driver it will prevent the nouveau driver from working when you've re-install it (the nouveau driver). If there is an xorg.conf file, remove it or rename it. The nouveau driver doesn't need xorg.conf.

---

### Post by danielgrosvenor on 2011-04-10
No luck. :( I don't think it's actually connecting to the Internet. I even plugged an ethernet cable in (normally just uses WiFi) but keep getting "cannot resolve" errors. 

The only thing of note I can offer is that, upon booting, some red text flashes up and says 'couldn't find matching output script table'. 

I'm writing this on my phone so my Googling abilities are limited. Please help, someone! :'(

---

### Post by danielgrosvenor on 2011-04-10
Alright, removed xorg.conf via command line and am now able to get back into GUI. However the computer is running slower than a paralysed slug with heavy shopping. I'm still getting that red text upon boot, too. 

Any ideas what to do?

---

### Post by wojox on 2011-04-10
It's probably running slow due to no video driver. Did you get an internet connection back?

---

### Post by danielgrosvenor on 2011-04-10
Yep. Ran the install nouveau line posted above, and apt-get updated and upgrade. Still running stupily slow though. 

Running sudo apt-get remove xorg now to see if that does anything.

---

### Post by wojox on 2011-04-10
No don't remove xorg. Is your driver activated?

---

### Post by d3v1150m471c on 2011-04-10
make a list of what you have install using dpkg:
```

dpkg --get-selections | grep -v deinstall > backup.list

```Then you can run the following for additional info:
```

apt-get remove xserver-xorg-core -s > xorg.list

```This way you'll know what you had installed should something go wrong. now if you want to live on the edge a little you can remove xserver-xorg-core and then reinstall it. In theory it should revert you back to the way it was, and if not you have a list of everything you previously had installed. Please note, you'll have no graphical access while xserver is uninstalled.

I make a supplemental frontend to apt-get called apt-oops, you can find it on my site below. You can create backup lists with it, restore these lists, create lists when uninstalling packages. It's saved my hide a few times. I suggest keeping it handy the next time you play around with major system changes.

---

### Post by danielgrosvenor on 2011-04-10
The 'Additional Drivers' tool (which would normally mention my video driver)  now comes up empty. 

I only installed Ubuntu on Friday. Wondering if it'd be simpler/safer to just reinstalling it rather than extensive tweaking. :/

---

### Post by d3v1150m471c on 2011-04-10
if you know exactly what you uninstalled i suggest reinstalling it and seeing how it goes after a reboot.

---

