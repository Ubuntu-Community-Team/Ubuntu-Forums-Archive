---
title: "Restricted Driver Manager?"
date: 2009-05-04
forum: New to Ubuntu
---

### Post by jmedoro on 2009-05-04
hey folks...

I see no such thing under system/administration. is this something i have to download or install or do some fancy footwork to get? it doesnt seem so...

help!

---

### Post by _Purple_ on 2009-05-04
Did you check under System > Administration > Hardware Drivers ?
Are you looking for driver of any particular hardware?

---

### Post by jmedoro on 2009-05-04
i clicked on 'hardware drivers,' it tells me no proprietary drivers are in use on this system. dont know if this has any relation to anything.

my main problem: i installed compiz,computer froze, so i removed it, and now i cant enable the 'extra' setting under 'visual effects.'

i asked about this in another post, and someone replied that after having a similar problem, they reinstalled some video drivers and it fixed the problem.

after googling around, i came across the 'restricted driver manager' and noticed i didnt have one.

i think i have all the video drivers, but its still not working for me.

:(

---

### Post by Sarai the Geek on 2009-05-04
> **jmedoro said:**
> i clicked on 'hardware drivers,' it tells me no proprietary drivers are in use on this system. dont know if this has any relation to anything.

my main problem: i installed compiz,computer froze, so i removed it, and now i cant enable the 'extra' setting under 'visual effects.'

i asked about this in another post, and someone replied that after having a similar problem, they reinstalled some video drivers and it fixed the problem.

after googling around, i came across the 'restricted driver manager' and noticed i didnt have one.

i think i have all the video drivers, but its still not working for me.

:(

Depending on your graphics card you probably need to get a restricted driver to enable the 3D effects provided by compiz (I know this for certain if it's nvidia, not sure about others)
The Hardware Drivers panel controls restricted drivers, even though it doesn't say that flat out. If no drivers are showing up, try running:
```
sudo apt-get update
```

Then restarting your computer. I had this problem too with my fresh install of Jaunty- getting all the updates cleared it up.

Good luck-

---

### Post by rosswmcgee on 2009-05-04
I just installed 9.04 clean and a small icon on the toolbar had the note about the drivers. I was not sure and closed it. Now where did it go? Should I install them?

---

### Post by tuxxy on 2009-05-04
Would be helpful if you included your video card model

---

### Post by Sarai the Geek on 2009-05-04
> **rosswmcgee said:**
> I just installed 9.04 clean and a small icon on the toolbar had the note about the drivers. I was not sure and closed it. Now where did it go? Should I install them?

Long answer: they are not open source thus if you are a purist you should not install them. The devs cannot see or modify their source code, and Canonical cannot provide updates for them. However, they will likely significantly improve the functionality of your computer.

Short answer: Yes.

To open the restricted drivers manager, go to system>administration>hardware drivers.

---

### Post by rosswmcgee on 2009-05-04
I have no idea it is a new emachine says NVIDIA GEfORCE INTEGRATED GRAPHIS

---

### Post by snova on 2009-05-04
> **rosswmcgee said:**
> I have no idea it is a new emachine says NVIDIA GEfORCE INTEGRATED GRAPHIS

System Monitor (System -> Administration -> System Monitor) might be able to tell you more specific information.

If not, run this in a terminal and post the output, it'll be in there somewhere:

```
lspci
```

---

### Post by jmedoro on 2009-05-04
> **snova said:**
> System Monitor (System -> Administration -> System Monitor) might be able to tell you more specific information.

If not, run this in a terminal and post the output, it'll be in there somewhere:

```
lspci
```


ok, here's my terminal output:

> 00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)

any reason why 'extra' visual effects setting might not work, based on all of that?

maybe i also need the 3d driver (?) as well. i downloaded Avant Window Manager, which doesnt seem to be working after 5 minutes of fooling around, but i'm guessing its for the same reason,

---

### Post by mcduck on 2009-05-05
> **jmedoro said:**
> ok, here's my terminal output:



any reason why 'extra' visual effects setting might not work, based on all of that?

maybe i also need the 3d driver (?) as well. i downloaded Avant Window Manager, which doesnt seem to be working after 5 minutes of fooling around, but i'm guessing its for the same reason,

You said you removed Compiz. That *is* the extra visual effects, so make sure you reinstall it again before trying to enable the desktop effects.

Also, I remember there was some issues with the Intel drivers released with 9.04. You could try using more up-to-date driver version. The developers offer a PPA repository with up-to-date X drivers here: [https://edge.launchpad.net/~ubuntu-x-swat/+archive/x-updates/]("https://edge.launchpad.net/~ubuntu-x-swat/+archive/x-updates/")

For the restricted drivers, if the hardware manager offers you something to install you most likely will want to install it (as it's required for the hardware component in question to work correctly). If the hardware manager doesn't offer you any drivers, then you either don't need any restricted drivers or the ones you might need are not available. So it really is that simple, install if there's anything available. ;)

---

### Post by jmedoro on 2009-05-05
thanks, i will try looking for updated drivers.

regarding the 'extra visual effects,' i had enabled these when i first installed ubuntu (and had not yet had compiz), and i was got effects such as the 'wobbly screen,' etc.

anyhow, i reinstalled compiz and nothing is happenening, and i am assuming its b/c each time i enable 'extra effects,' it reverts right back to normal.

---

### Post by mcduck on 2009-05-05
> **jmedoro said:**
> thanks, i will try looking for updated drivers.

regarding the 'extra visual effects,' i had enabled these when i first installed ubuntu (and had not yet had compiz), and i was got effects such as the 'wobbly screen,' etc.

anyhow, i reinstalled compiz and nothing is happenening, and i am assuming its b/c each time i enable 'extra effects,' it reverts right back to normal.

Compiz is the very same thing as the desktop effects available in Ubuntu by default. In other words, Compiz is installed by default and the desktop effects options in System/Preferences/Appearance only switch between Metacity (no desktop effects) and two different Compiz configurations ("Normal" and "Extra").

---

### Post by jmedoro on 2009-05-05
thanks McDuck, i wasnt aware of that. maybe i will try to reinstall compiz again, or just make sure i have it installed correctly.

this may generate more compiz questions, but at least i will be getting somewhere. 

thanks again.

---

### Post by silverglade00 on 2009-05-05
You might also want to install fusion-icon. That gives you an icon you can use to turn Compiz on and off. Sometimes that works for me when the normal desktop effects fails.

---

### Post by freeman2000 on 2009-05-06
Since you have an NVidia graphics card, you will need to go to System --> Administration --> Hardware Drivers and "activate" the NVidia proprietary driver #180.  This will enable the 3D effect of the graphics card, and allow you to play with compiz-fusion.  You might also want to download compiz-config-settings-manager from Synaptics.  In addition to "None" (2D), "Normal" (3D), and "Extra" (3D) modes, it will give you a 4th mode called "Custom".   Good luck.

---

### Post by jmedoro on 2009-05-06
> **freeman2000 said:**
> Since you have an NVidia graphics card, you will need to go to System --> Administration --> Hardware Drivers and "activate" the NVidia proprietary driver #180.  This will enable the 3D effect of the graphics card, and allow you to play with compiz-fusion.  You might also want to download compiz-config-settings-manager from Synaptics.  In addition to "None" (2D), "Normal" (3D), and "Extra" (3D) modes, it will give you a 4th mode called "Custom".   Good luck.


i'm assuming Snova about the NVIDIA graphics card, but how the hell do you know what additional drivers you need and what you need them for?

and yes, at one point on my initial run through with compiz, i do remember seeing the 'custom' mode, totally forgot about that. as soon as i enabled it, my screen froze and i had to uninstall.

i reinstalled compiz through the shell last night, took 30 minutes for some reason and it wont work, so i'll be back. 

thanks everyone for all the help!

---

### Post by Sarai the Geek on 2009-05-06
> **jmedoro said:**
> i'm assuming Snova about the NVIDIA graphics card, but how the hell do you know what additional drivers you need and what you need them for?

and yes, at one point on my initial run through with compiz, i do remember seeing the 'custom' mode, totally forgot about that. as soon as i enabled it, my screen froze and i had to uninstall.

i reinstalled compiz through the shell last night, took 30 minutes for some reason and it wont work, so i'll be back. 

thanks everyone for all the help!

All (or at least the vast majority of) NVIDIA graphics cards need proprietary drivers to be installed in order to be fully functional. Your computer is, obviously, usable without them but if you want more advanced graphics features like 3D acceleration, compiz-fusion, etc then you will want to download them. Luckily, your computer knows just which ones you need- open up the hardware drivers dialogue and it should provide a list of several potential drivers. You want the one marked "recommended." :)

Also- you will want to install some sort of settings manager: I recommend compizconfig-settings-manager and fusion-icon, which provides a handy dandy little icon in the system tray.

---

