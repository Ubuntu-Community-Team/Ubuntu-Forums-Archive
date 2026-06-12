---
title: "Poor screen resolution"
date: 2009-03-28
forum: New to Ubuntu
---

### Post by Stuart Thomas on 2009-03-28
Hi group

I have a question about the screen resolution I am able to achieve for my Ubuntu installation. The only screen resolution available to me in the drop down list of 'preferences - screen resolution' is 640x480. I have an 8 years old Dell Inspiron 2600 with a 1.2ghz Intel celeron CPU, 384MB of memory, an Intel 830M graphics controller and Version A06 BIOS. (The latest BIOS available is A08 I believe.) 

My Ubuntu installation is Version 8-10, kernel 2.6.27-11-generic and is fully up to date and all works well apart from the resolution issue (including my Belkin wireless card amazingly enough). This is a real problem because I can't see the buttons at the bottom of some of the menues. I retained my original operating system (XP), behind a partition, when I installed Ubuntu from the installation CD.

I have looked at trying to install propriety drivers in 'administration - hardware drivers' as suggested on P21 of the Ubuntu Pocket Guide but there are no drivers listed there.

The Xorg screen shows the installed driver as 'vesa'. I have tried editing this using several different scripts as suggested in various forums but without success - the installation either freezes, goes blank or to a white screen. Repairing the Xorg during 'safe boot' restores it to 'vesa'. I remember when I installed Ubuntu I got a white screen and had to select 'safe graphics mode' during a 'safe boot' to get the screen to work.

My question to the group is is there actually a driver available that will give me an better resolution and if so where do I get it and how do I install it?

Many thanks Stuart

---

### Post by CatKiller on 2009-03-28
I don't have integrated Intel graphics in my computer, so this isn't from experience, but I'd imagine that the "intel" driver would be a better match for your hardware than the "vesa" driver. The vesa driver is one that will work on anything because it doesn't do much. I don't know if limited resolution availability if a feature of the vesa driver, or if that is a symptom of something else.

---

### Post by ubumania on 2009-03-28
Yeah, get the right driver. If you go 'system-admin-synaptic-package-manager you will find all of the drivers listed under 'xserver-xorg-video-... If you have intel it will be 'xserver-xorg-video-intel'. I would have thought that it would be installed already so.


Try the following command and see if your driver can be selected

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

and select the driver (up/down arrows, space bar to check) then the resolution for your screen. That will also change the resolution to what you need with the vesa generic driver. Using vesa could give you problems with scrolling and desktop effects.

---

### Post by Stuart Thomas on 2009-03-28
> **ubumania said:**
> Yeah, get the right driver. If you go 'system-admin-synaptic-package-manager you will find all of the drivers listed under 'xserver-xorg-video-... If you have intel it will be 'xserver-xorg-video-intel'. I would have thought that it would be installed already so.


Try the following command and see if your driver can be selected

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

and select the driver (up/down arrows, space bar to check) then the resolution for your screen. That will also change the resolution to what you need with the vesa generic driver. Using vesa could give you problems with scrolling and desktop effects.

Thanks for the reply. I followed your advice and selected the intel driver then copied a script pointing to intel into the Xorg screen. Everything works fine now.

Stuart

---

