---
title: "Nvidia Drivers Error"
date: 2009-04-28
forum: New to Ubuntu
---

### Post by Frosty G on 2009-04-28
I followed this tutorial [here]("http://ubuntuforums.org/showthread.php?t=354024")
and everything went great, the installer ran
but then, this:
```
Do you want to continue [Y/n]? y
Abort.
```
i pressed y, then enter
tried several times
what?

---

### Post by northern lights on 2009-04-28
> **Frosty G said:**
> I followed this tutorial
That's from February 2007! - Edgy times. Way too old to read and/or follow today.

Please post the output of ```
sudo lshw -C display
```
Thank you.

---

### Post by Frosty G on 2009-04-28
nevermind buddy, i tried:
  ```
sudo apt-get install linux-headers-`uname -r` build-essential gcc gcc-3.4 xserver-xorg-dev
```
and it worked great
thanks heaps anyway

---

### Post by northern lights on 2009-04-28
While it's really good that you've got it working, there would have been no need to install the driver from source.

You did not have the necessary apps installed to compile the source in the tarball. Installing *build-essential* solved that for you (*gcc* (GNU C Compiler) is part of the meta-package *build-essential* by the way).

The downside is that now you will not receive updates to your driver when there most likely would have been a solution from the Ubuntu repositories that would have also worked.

A shot in the dark:```
sudo apt-get install nvidia-glx-180
``` would have probably sorted you out also. But I wanted to see what graphics device you have beforehand, as there's more than one nvidia driver version.

Anyhow, enjoy you OS, wherever the drivers came from.

---

### Post by Frosty G on 2009-04-28
[this]("http://www.nvidia.com/object/linux_display_x86_96.43.01.html") one
also, graphics card is [B]a Geforce4 420
craptastic, i know
[/B]

---

### Post by northern lights on 2009-04-28
For a decent desktop experience even a 4series GeForce is fine (until three months ago, I was one a GeForce2MX...)

The 96.43.XX driver version is the correct choice for a Geforce4. However, this one also is included in the Ubuntu repositories.

```
sudo apt-get install nvidia-glx-96
``` would have fully sufficed. And been updated in the future.

It could have been also done via the GUI - System > Administration > Hardware Drivers.

---

### Post by Davec.hh on 2009-11-08
Hope that I'm not posting in the wrong area. I've had problems trying to install drivers for Geforce2MX. I've tried under 9.10 and dropped to 8.04 all with no sucess.
I can get 800x600 resolution but no greater with any version and have the computer working. My monitor is native in 1280x1024. I have tried to follow a few threads either without success in lodaing the driver or have succeded and locked the computer. I believe that the drivers I need are x86-96.43.13 and have tried the sudo./NVIDIA-linux-x86-96.43.13-pkg1.run route but only get "No such file or directory" the terminal is running from desk-top which has the file save there.

Any help or suggestions would be greatfully recieved.

My appologies if I've popsted in the wrong place.

DaveC.hh

---

### Post by northern lights on 2009-11-11
You want to use the [96.xx.xx]("http://us.download.nvidia.com/XFree86/Linux-x86/96.43.13/README/appendix-a.html") series nvidia driver.```
sudo aptitude update && sudo aptitude install nvidia-glx-96
```

---

### Post by Davec.hh on 2009-11-12
Thank you Nothern Lights.

I put in the line of in the terminal as written and my password when requested. It certainly loaded a string of commands and uploaded. Unfortunately I'm still stock with 800x600 as my maximum resolution. The screen is slightly off-set as well that didn't move. With newer computers when the drivers have been loaded the resolution allows maximum for the screen and centres the screen.

I've updated 8.04 and retried. I am getting "can't find any package whose name or description matched nvidia-gxl-96". It appears to have tried main sources, restricted sources, and multiverse sources.

regards

DaveC

---

### Post by northern lights on 2009-11-15
mkey. Didn't see you were on Hardy still.

The package and corresponding link I gave you are for later distributions.

Hardy repo's offer *nvidia-glx* and *nvidia-glx-legacy*

You should go with the legacy drivers (2MX). Also make sure *nvidia-settings* is installed - that's where you alter resolution. I should appear, if installed, under "System > Administration > NVIDIA X Server Settings".

---

### Post by Davec.hh on 2009-11-15
Many thanks. I'd given up on 9.10 and thought that Hardy might have been easier. I'll try reinstalling 9.10 and follow your original instructions next time I'm on my desktop computer.

---

### Post by Davec.hh on 2009-11-15
I've re-installed 9.10 and followed your instruction. It retrieved the drivers and made the changes - but I still ony get 800x600 and the maximum resolution. 

If I go to system/preferences/display I get:

 "It appears that your graphics driver does not support the necessary extensions to use this tool.  Do you want to use your graphics driver vendor's tool instead?".

Clicking on yes in turn says:

 "You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server." 

Am I missing somthing, do I need to do some additional changes?

Many thanks

DaveC

---

### Post by Davec.hh on 2009-11-25
Hi again.

I have tried following a few threads. I've looked at xorg.conf and have five modes listed 1280x1024 being one of them - my maximum resolution for the monitor. It looks as though it should be there to pick. But in system/preferences/display the maximum is 800x600.

I tried xrandr -q giving me minimum 320x240 and maximum 800x600 

then added xrandr -s 1280x1024 only to get the reply:

size 1280x1024 not found in available modes.

I think I'm getting a bit confused by it all. Any help would be gratefully received.

DaveC

---

