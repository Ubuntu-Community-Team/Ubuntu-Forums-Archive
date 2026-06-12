---
title: "Help with monitor resolution. (1366x768 Compaq CQ1500LA)"
date: 2011-06-21
forum: New to Ubuntu
---

### Post by DolfasCid on 2011-06-21
Hello all, I wrote here to get some help on resolving some resolution problems, I recently bought a new Compaq Nettop (CQ1500LA) and dual-boot installed the LTS of ubuntu, everything works fine however my screen res is set to 1024x768 however my monitor can take up to 1366x768, I tried to play with the xrandr config and checked for available drivers, however HP currently does not support Linux drivers on this PC and xrandr playing led me to have stability problems forcing ubuntu to reboot after a cretain period of time. 
and well, I am kinda stuck. 

Any Ideas on how to configure the proper resolution on this PC would be greatly appreciated.

---

### Post by terrykiwi83 on 2011-06-21
Does it let you change the resolution in System > Preferences > Monitors

If not what graphics is built into the system? nVidia/ATi/Intel?

---

### Post by DolfasCid on 2011-06-21
> **terrykiwi83 said:**
> Does it let you change the resolution in System > Preferences > Monitors

If not what graphics is built into the system? nVidia/ATi/Intel? Nope 1024x768 is set as the highest, and intel graphics card.

---

### Post by terrykiwi83 on 2011-06-21
Have you installed any drivers for this graphics card or did it just work when you install Ubuntu?

Also what model Intel Graphics Chip?

---

### Post by DolfasCid on 2011-06-21
> **terrykiwi83 said:**
> Have you installed any drivers for this graphics card or did it just work when you install Ubuntu?

Also what model Intel Graphics Chip? Just worked when installed, tried searching HP for available drivers however none availabie for Linux.

Oh, and graphic card is Intel pineview D510 inetgrated.

---

### Post by terrykiwi83 on 2011-06-21
Are any available in the Restricted Drivers?

System > Administration > Additional Drivers

---

### Post by DolfasCid on 2011-06-21
> **terrykiwi83 said:**
> Are any available in the Restricted Drivers?

System > Administration > Additional Drivers Just did a search to see if there where any, none available sadly.

---

### Post by terrykiwi83 on 2011-06-21
So what is the actual model of the onboard intel chip?

---

### Post by DolfasCid on 2011-06-21
> **terrykiwi83 said:**
> So what is the actual model of the onboard intel chip?

Intel Atom D510 (Pineview)

---

### Post by terrykiwi83 on 2011-06-21
Just had a look at this page and it seems it could help you with getting some drivers.

[https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo/](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo/)

In Short here are the instructions

```

Drivers installation
Emgd drivers (currently supported)

Drivers are available in the gma500 PPA repository for Natty, Maverick and Lucid

Repository page: https://launchpad.net/~gma500/+archive/emgd


Instructions for Natty only. Open a terminal and type:

sudo add-apt-repository ppa:gma500/emgd 
sudo apt-get update
sudo apt-get install xorg-emgd emgd-dkms emgd-xorg-conf
sudo emgd-xorg-conf
reboot for the changes to take effect.

```

---

### Post by DolfasCid on 2011-06-21
> **terrykiwi83 said:**
> Just had a look at this page and it seems it could help you with getting some drivers.

[https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo/](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo/)

In Short here are the instructions

```

Drivers installation
Emgd drivers (currently supported)

Drivers are available in the gma500 PPA repository for Natty, Maverick and Lucid

Repository page: https://launchpad.net/~gma500/+archive/emgd


Instructions for Natty only. Open a terminal and type:

sudo add-apt-repository ppa:gma500/emgd 
sudo apt-get update
sudo apt-get install xorg-emgd emgd-dkms emgd-xorg-conf
sudo emgd-xorg-conf
reboot for the changes to take effect.

```

Nope, Ubuntu just crashed, I´m unable to load it.

---

### Post by terrykiwi83 on 2011-06-21
hhmm beats me, hopefully someone else here can shine some light

---

### Post by DolfasCid on 2011-06-21
> **terrykiwi83 said:**
> hhmm beats me, hopefully someone else here can shine some light I agree, best bet is to wait for the drivers to be available. 

Now if I could only have Ubuntu work again. No worries, I have a backup disk with everything. Oh well, back to a fresh install.. XD

---

### Post by terrykiwi83 on 2011-06-21
Why not try a different distro see if it makes a difference, maybe Try Linux Mint? Although Based on Ubuntu it has lots of differences or maybe try Fedora or OpenSUSE? Its worth a try

---

### Post by wildmanne39 on 2011-06-22
> **DolfasCid said:**
> Hello all, I wrote here to get some help on resolving some resolution problems, I recently bought a new Compaq Nettop (CQ1500LA) and dual-boot installed the LTS of ubuntu, everything works fine however my screen res is set to 1024x768 however my monitor can take up to 1366x768, I tried to play with the xrandr config and checked for available drivers, however HP currently does not support Linux drivers on this PC and xrandr playing led me to have stability problems forcing ubuntu to reboot after a cretain period of time. 
and well, I am kinda stuck. 

Any Ideas on how to configure the proper resolution on this PC would be greatly appreciated.
Hi, the intel drivers come installed with the kernel you do not need to install any extra. You can run this command to check.
```
sudo lspci -k

```
Also I am going to give you two guides one for xrandr and one for xorg config.
[http://www.ubuntugeek.com/how-change-display-resolution-settings-using-xrandr.html](http://www.ubuntugeek.com/how-change-display-resolution-settings-using-xrandr.html)
[https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)

---

### Post by wildmanne39 on 2011-06-22
Hi, if those are updated drivers for your card, you can install them just open a terminal and copy and paste those commands in the termninal and then reboot. Just make sure that they are for your card and that they are not buggy, I updated my nvidia card that way and the new driver was buggy and I had to uninstall it. I doubt a new driver will fix your resolution issue, natty as not recognized resolution properly on a lot of systems including mine, and the only way to fix it is by one of the links in my last post.

---

