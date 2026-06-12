---
title: "Newbie set up advice"
date: 2011-05-21
forum: New to Ubuntu
---

### Post by marco4472 on 2011-05-21
Hi, I am using a Toshiba Satellite A100 laptop with ubuntu 11.4 32bit no other operating  system installed.
I have it working but can only boot into gnome without effects or Xbuntu. everything else just hangs on loading. I know its not the most up to date system but it should be able to do better than it is. It also acts a bit sluggish at times. I have good computer skills but no knowledge of Linux. I am guessing ubuntu needs setting up to suite my system or I need a different driver but do not know where to start looking. any advice would be welcome.
Marco

---

### Post by bennachie on 2011-05-21
I'm a bit confused as to the actual situation. Have you installed Ubuntu 11.04 or Xubuntu 11.04, or are you running with two alternative desktops installed in a single system. I wouldn't be surprised if you have had some problems with Ubuntu 11.04, since the Unity GUI places fairly high demands on the graphics chip/card, and the fallback process might very well leave you without access to desktop effects. By contrast, I would have thought that a direct installation of Xubuntu would have run fine. You might also like to try Linux Mint (which uses the same infrastructure as Ubuntu, but without Unity).

---

### Post by jmszr on 2011-05-21
marco4472,

I looked up your computer and it has 512 MB of RAM. You will need to upgrade your RAM to use the effects or the Unity desktop.

Here are the system requirements:

```
1 GHz x86 processor
1 Gb of system memory (RAM)
8 Gb of hard-drive space
Graphics card and monitor capable of 1024 by 768
Either a Cd/Dvd-Drive or a Usb port (or both)

Internet access is helpful 
```

Hope that helps.

+1 for Xubuntu or you might want to check out Lubuntu: [http://lubuntu.net/](http://lubuntu.net/) it runs LXDE instead of Unity/Gnome (Ubuntu) or Xfce (Xubuntu).

Edit: Here is a link to the System Requirements documentation: [https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements) .

---

### Post by marco4472 on 2011-05-21
Thanks but my system has 1gb should have put that in. I have a single installation and installed the Xbuntu after I realised the more complex desktop options would not run. I also found KDE would not run but I have assumed that this was for the same reasons as Gnome. Think you have answered it all as I was  not aware how complex unity was until you said. I have read a bit more now and accept my system is not up to it. Love the ubuntu experience though

---

### Post by Bucky Ball on 2011-05-21
There apparently is an option to use the 'classic' desktop in 11.04 which should give you the regular Xubuntu desktop (rather than Unity). That might speed things up a little.

---

### Post by bennachie on 2011-05-21
That's the classic Gnome experience you'll get, not the Xubuntu experience, but yes, it could well work - the option has to be selected via the lower panel at the login stage, and will persist through subsequent logins.

> **Bucky Ball said:**
> There apparently is an option to use the 'classic' desktop in 11.04 which should give you the regular Xubuntu desktop (rather than Unity). That might speed things up a little.

---

### Post by wildmanne39 on 2011-05-21
> **marco4472 said:**
> Hi, I am using a Toshiba Satellite A100 laptop with ubuntu 11.4 32bit no other operating  system installed.
I have it working but can only boot into gnome without effects or Xbuntu. everything else just hangs on loading. I know its not the most up to date system but it should be able to do better than it is. It also acts a bit sluggish at times. I have good computer skills but no knowledge of Linux. I am guessing ubuntu needs setting up to suite my system or I need a different driver but do not know where to start looking. any advice would be welcome.
MarcoHi, for the driver for your video card you look in additional drivers there might be 2 there try one if it does not help try the other, if you are using a nvidia card after you activate it, it will show it is not currently in use but it is that is just a little bug. Yes using ubuntu classic or ubuntu classic with no effects will be easier on resources.Click on your user name at the the log in screen and then the bottom of the screen you can choose with one to log into.):P

---

### Post by fabricator4 on 2011-05-22
> **marco4472 said:**
> Hi, I am using a Toshiba Satellite A100 laptop with ubuntu 11.4 32bit no other operating  system installed.
I have it working but can only boot into gnome without effects or Xbuntu. everything else just hangs on loading. I know its not the most up to date system but it should be able to do better than it is. It also acts a bit sluggish at times. I have good computer skills but no knowledge of Linux. I am guessing ubuntu needs setting up to suite my system or I need a different driver but do not know where to start looking. any advice would be welcome.
Marco

If you can boot 11.04 in Ubuntu Classic aka Gnome 2 (as you seem to be saying) then click on "Additional Drivers" under the system menu.  If it loads a proprietary driver it might might be enough to get Unity working for you, or to enable effects under Ubuntu Classic.  My preference is for Ubuntu Classic.

If there's no 3D driver available you can continue to use Classic with no effects, or you might like to try Unity 2D by installing it out of the repositories.  Unity 2D is even more unfinished than Unity 3D, but it should be enough to let you try out the new interface.

To find out what graphics card you have (if you want to ask for further help) execute the following command in a terminal and post the results:

```
lspci | grep VGA
```

Chris

---

