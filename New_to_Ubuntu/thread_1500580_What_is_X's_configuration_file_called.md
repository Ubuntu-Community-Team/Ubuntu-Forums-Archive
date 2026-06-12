---
title: "What is X's configuration file called?"
date: 2010-06-03
forum: New to Ubuntu
---

### Post by lugoteehalt on 2010-06-03
I'm used to X's configuration file being /etc/X11/xorg.conf.  But this does not seem to exist on the 10.4 Ubuntu:```
lugo@fidoUbuntu:~$ locate -i xorg.conf
/usr/lib/X11/xorg.conf.d
/usr/lib/X11/xorg.conf.d/05-evdev.conf
/usr/lib/X11/xorg.conf.d/10-synaptics.conf
/usr/lib/X11/xorg.conf.d/10-vmmouse.conf
/usr/lib/X11/xorg.conf.d/10-wacom.conf
/usr/share/man/man5/xorg.conf.5.gz
lugo@fidoUbuntu:~$
```I want something to fiddle about with to try to get wide screen, currently have 4:3, nvidia 8400GS graphics card.  Currently using the nv module installed automatically during Ubuntu installation.

---

### Post by wojox on 2010-06-03
Just run

```
sudo nvidia-xconfig
```

It will create a copy for you. Then

```
gksudo nvidia-settings
```

---

### Post by doas777 on 2010-06-03
before running wojox's commands, you may want to install the restricted nvidia driver. I don't believe that the nvidia applications ship with the 'nv' driver.


to answer your specific question, X config info is largely generated at boot anymore, and as such there isn;t an omnibus file like xorg used to be.

---

### Post by bodhi.zazen on 2010-06-03
The X configuration file is called xorg.conf, but this file has been depreciated, so it is absent in most modern distros.

To use your nvidia card, install the nvidia driver and use nvidia-settings.

Alternately, you can write your own xorg.conf from scratch.

---

### Post by anotherbigal on 2010-09-06
Just to pick up on  bodhi.zazen's reply, if I want to write my own xorg.conf file where would be the correct place to put it? I am using CentOS on my server and in that distro it is in /etc/X11 but I notice in other posts that this is not necessarily the case in Ubuntu.

Cheers

Alan

---

### Post by coffeecat on 2010-09-06
> **anotherbigal said:**
> I am using CentOS on my server and in that distro it is in /etc/X11 but I notice in other posts that this is not necessarily the case in Ubuntu.

If you have an xorg.conf file it goes in /etc/X11/, just as with any other distro. With the version of the xserver that 10.04/Lucid uses, most video hardware is autodetected and you don't need an xorg.conf file. But if you create one, the xserver will read that and use it, and any settings you put in it will take precedence over the autodetection process.

In fact, if you install the proprietary nvidia driver a small xorg.conf will be created. Ditto for the proprietary fglrx driver I believe.

**Edit:** by the way, you're still showing "Feisty Fawn" on your profile. That definitely has a /etc/X11/xorg.conf, and won't run without one. :p

---

### Post by anotherbigal on 2010-09-06
Thank you coffeecat

And thank you for the profile tip. I'll update it as I am now on Lucid.

Cheers

Alan

---

