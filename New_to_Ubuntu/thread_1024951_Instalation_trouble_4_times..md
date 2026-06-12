---
title: "Instalation trouble 4 times."
date: 2008-12-29
forum: New to Ubuntu
---

### Post by RAZRBAKK on 2008-12-29
Well, I've tried installing Ubuntu 8.04, Kubuntu 8.10, Ubuntu Studios 8.04 and 8.10. All of them install properly, reboot, get the the loading screen and freeze. I really want Ubuntu Studios or Kubuntu, but the only Ubuntu that will install of the 5 is Ubuntu Desktop 8.10.

Anyone able to help me with proper installation?

Also, Ive partitioned the harddrive so its running Vista and Ubuntu.

---

### Post by mapes12 on 2008-12-29
> Also, Ive partitioned the harddrive so its running Vista and Ubuntu.I'm shooting in the dark but somehow the dual boot configuration may be causing the problem.Can you get your required version of Ubuntu to run OK from the Live CD?

---

### Post by BDNiner on 2008-12-29
If ubuntu 8.10 installs you can add the packages for KDE and Ubuntu Studio afterwards.  Is 8.10 the install that freezes when you reboot or do u get to a login prompt?

---

### Post by LowSky on 2008-12-29
> **RAZRBAKK said:**
> All of them install properly, reboot, get the the loading screen and freeze. 

Boot into recovery mode from GRUB, choose the optin to boot into GUI or OS.. whatever it is it's the first option.

See if any errors pop up

---

### Post by RAZRBAKK on 2008-12-29
> **mapes12 said:**
> I'm shooting in the dark but somehow the dual boot configuration may be causing the problem.Can you get your required version of Ubuntu to run OK from the Live CD?

It freezes on the boot from the CD as well.

> **BDNiner said:**
> If ubuntu 8.10 installs you can add the packages for KDE and Ubuntu Studio afterwards.  Is 8.10 the install that freezes when you reboot or do u get to a login prompt?
Where do I get these packages?

8.10 does not freeze at all. Its only Studio and Kubuntu
> **LowSky said:**
> Boot into recovery mode from GRUB, choose the optin to boot into GUI or OS.. whatever it is it's the first option.

See if any errors pop up

No errors.

---

### Post by BDNiner on 2008-12-29
open up synaptic and search for ubuntu studio and kde-desktop? Do u want to install the latest stable version of kde? 4.1? Or the older version 3.5?

---

### Post by RAZRBAKK on 2008-12-29
4.1. 

Im installing Ardour as we speak. Thats really all I wanted from Studio.

---

### Post by BDNiner on 2008-12-30
ok, you will need to add extra repositories to your /etc/apt/sources.list in order to install 4.1 since i don't think it is included in the regular ubuntu repositories. 

to use Ardor you just need to type
```

sudo apt-get install ardour

```
and that will install the program for you. The full ubuntu studio package includes a lot of software for audio/graphical editing so u may not need all of it.

---

### Post by BDNiner on 2008-12-30
[http://www.ubuntugeek.com/how-to-install-kde-41-on-ubuntu-810-intrepid-ibex.html](http://www.ubuntugeek.com/how-to-install-kde-41-on-ubuntu-810-intrepid-ibex.html)

This is the guide that i used to install kde 4.1. Installing 4.1 will change you splash screen when loading ubuntu. to change it back type:
```

sudo update-alternatives --config usplash-artwork.so
sudo update-initramfs -u

```

---

### Post by albinootje on 2008-12-30
> **BDNiner said:**
> open up synaptic and search for ubuntu studio and kde-desktop? Do u want to install the latest stable version of kde? 4.1? Or the older version 3.5?

The packages are called kubuntu-desktop and ubuntustudio-desktop.

---

### Post by RAZRBAKK on 2008-12-30
Awesome, thanks guys.

Now I just gotta get my WiFi working... haha

---

