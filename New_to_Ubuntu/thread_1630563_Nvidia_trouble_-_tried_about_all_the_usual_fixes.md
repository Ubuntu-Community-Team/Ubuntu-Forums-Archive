---
title: "Nvidia trouble - tried about all the usual fixes"
date: 2010-11-25
forum: New to Ubuntu
---

### Post by mistypotato on 2010-11-25
Yesterday I installed a GeForce 7900 GT/GTO car in my PC.

I have a dual boot machine and it worked right off the bat in Windows Vista but will not work in ubuntu 9.10

I've tried pretty much everything I could find....PURGING the old drivers, installing the NVIDIA drivers from downloads.nvidia.com and practically every tutorial I could find in the last 24 hours....still it boots to a command prompt.

Oddly, I get video just fine when booting with a LiveCD so at least I know in Windows Vista and with the LIVECD, the card works...so I don't think it's a video card issue.

I have installed EnvyNG but because I can only get a command prompt, I'm not sure how to run EnvyNG to install it on the affected PC.

Can EnvyNG be run FROM a non GUI environment such as booting to a ubuntu command prompt?  Searched long for this answer and couldn't find it.

If I run EnvyGT from the LIveCD, will it change the setting on my actual Ubuntu 9.10 insstall or will it only apply the changes to the LiveCD session?

I've run out of ideas.

thx

---

### Post by mistypotato on 2010-11-25
I was able to run ENVYNG -t from the command line and it seemed to go through all it's steps successfully.

However, the end result is that nothing changed ](*,)

Never had THIS much troublew getting a video card to work in Ubuntu before. :confused:

It works fine if I boor into Windows Vista.....fine from the LIVE CD...but adamantly refuses to work in my installed Ubuntu.

Wow....I'm at a loss now :confused:

The most aggravating thing is that I get a GUI and decent video graphics when booted from the Live_CD and fantastic performance when booted in Windows Vista...but absolutely no graphics otherwise in my installed 9.10

I had no problem with graphics with the older Legacy Nvidia MX400 card I removed....I don't want to have to go back to legacy graphics <sigh>.

---

### Post by madjr on 2010-11-25
the live-cd is probably using the open drivers.

before trying to install/uninstall or even upgrading ubuntu, i think you should backup any important stuff in the ubuntu partition first.

---

### Post by mistypotato on 2010-11-25
Found this in the Xorg.log file...
I wonder if it's not the videocard driver but the SCREEN configuration:confused:
That hsync range doesn't look right.

(II) VESA(0): Total Memory: 4096 64KB banks (262144kB)
(II) VESA(0): Configured Monitor: Using hsync range of 31.50--319.86 kHz
(II) VESA(0): Configured Monitor: Using vrefresh range of 56.00-61.93 Hz
(WW) VESA(0): Unable to estimate virtual size
(II) VESA(0): Not using built-in mode "2048x1536" (no mode of this name)
(II) VESA(0): Not using built-in mode "1280x1024" (no mode of this name)
(II) VESA(0): Not using built-in mode "1024x768" (no mode of this name)
(II) VESA(0): Not using built-in mode "800x600" (no mode of this name)
(II) VESA(0): Not using built-in mode "640x480" (no mode of this name)
(II) VESA(0): Not using built-in mode "640x400" (no mode of this name)
(II) VESA(0): Not using built-in mode "320x400" (no mode of this name)
(II) VESA(0): Not using built-in mode "320x240" (no mode of this name)
(II) VESA(0): Not using built-in mode "320x200" (no mode of this name)
(WW) VESA(0): No valid modes left. Trying less strict filter...
(II) VESA(0): Configured Monitor: Using hsync range of 31.50--319.86 kHz
(II) VESA(0): Configured Monitor: Using vrefresh range of 56.00-61.93 Hz
(WW) VESA(0): Unable to estimate virtual size
(II) VESA(0): Not using built-in mode "2048x1536" (hsync out of range)
(II) VESA(0): Not using built-in mode "1280x1024" (hsync out of range)
(II) VESA(0): Not using built-in mode "1024x768" (hsync out of range)
(II) VESA(0): Not using built-in mode "800x600" (hsync out of range)
(II) VESA(0): Not using built-in mode "640x480" (hsync out of range)
(II) VESA(0): Not using built-in mode "640x400" (hsync out of range)
(II) VESA(0): Not using built-in mode "320x400" (hsync out of range)
(II) VESA(0): Not using built-in mode "320x240" (illegal horizontal timings)
(II) VESA(0): Not using built-in mode "320x200" (illegal horizontal timings)
(WW) VESA(0): No valid modes left. Trying aggressive sync range...
(II) VESA(0): Configured Monitor: Using hsync range of 31.50--319.86 kHz
(II) VESA(0): Configured Monitor: Using vrefresh range of 50.00-61.93 Hz
(WW) VESA(0): Unable to estimate virtual size
(II) VESA(0): Not using built-in mode "2048x1536" (hsync out of range)
(II) VESA(0): Not using built-in mode "1280x1024" (hsync out of range)
(II) VESA(0): Not using built-in mode "1024x768" (hsync out of range)
(II) VESA(0): Not using built-in mode "800x600" (hsync out of range)
(II) VESA(0): Not using built-in mode "640x480" (hsync out of range)
(II) VESA(0): Not using built-in mode "640x400" (hsync out of range)
(II) VESA(0): Not using built-in mode "320x400" (hsync out of range)
(II) VESA(0): Not using built-in mode "320x240" (illegal horizontal timings)
(II) VESA(0): Not using built-in mode "320x200" (illegal horizontal timings)
(EE) VESA(0): No valid modes
(II) UnloadModule: "vesa"
(II) UnloadModule: "int10"
(II) Unloading /usr/lib/xorg/modules//libint10.so
(II) UnloadModule: "vbe"
(II) Unloading /usr/lib/xorg/modules//libvbe.so
[COLOR="Red"](EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found[/COLOR]

---

### Post by mistypotato on 2010-11-25
wow :shock:

Just found THIS is another previous Xorg.log......

(EE) NVIDIA(GPU-0): Your GeForce 7900 GT/GTO graphics card does not have the
(EE) NVIDIA(GPU-0):     necessary external power cables attached; X will not start
(EE) NVIDIA(GPU-0):     unless this is rectified.  Please shut down your computer,
(EE) NVIDIA(GPU-0):     open its case, and attach the appropriate power
(EE) NVIDIA(GPU-0):     connectors.  Your video card may have multiple power
(EE) NVIDIA(GPU-0):     connectors.  If so, each must be attached to a separate
(EE) NVIDIA(GPU-0):     power cable.  Please see the documentation provided with
(EE) NVIDIA(GPU-0):     your video card for more details.  If you think you have
(EE) NVIDIA(GPU-0):     received this message in error, you may specify the
(EE) NVIDIA(GPU-0):     "NoPowerConnectorCheck" X configuration option in the
(EE) NVIDIA(GPU-0):     Screen section of your X config file.


When I installed this card I remember seeing a socket for another plug but the power supply didn't have one so basically there is no way to connect this as far as I can tell UNLESS I can buy a cable that splits the one going to the Motherboard so I can attach the other end to the video card.

If THIS is the problem I'll post back.  Never saw this before.

---

### Post by mistypotato on 2010-11-25
I found a splitter connector from another video card I wasn't using, plugged it in and VOILA !!!
The video worked on the very next boot after 2 days of fighting with it.


**VALUABLE lessons learned from todays foray into Ubuntudom....**

1). LOGS ARE YOUR FRIEND !  (Use them...Read them...Search them when debugging)

2).  The Nvidia Graphics card I am using (7900 GT) works perfectly fine under Windows Vista without the secondary power connector attached.....but Ubuntu (maybe Linux?) requires  that secondary power cord to be attached and powered up.

Now, this "could" be a forehead slapper moment....but....just remember that the card did not come WITH a cord for the secondary power connector and there were no instructions (bought off ebay) AND....it worked perfectly in Windows Vista without it so there may be at least one other out there that could make this mistake :p

Today is Thanksgiving Day, 2010....
If you read this a day...month...year from now...drop me a note if it helped you resolve your graphics issue :KS

---

### Post by madjr on 2010-11-26
am not sure if ubuntu really needs that.

have you search other peoples posts that own your same video card? are they using the same setup

anyway glad you got it going

---

### Post by mistypotato on 2010-11-30
It definitely needed it.

The logs contained an entry warning that in Ubuntu it **must** be connected.

I'm not sure if it was a Ubuntu system warning or an nvidia warning...but it got me past this problem.

As soon as I heeded the warning, and connected the 2nd power connector, all was good again.

---

### Post by psycho5 on 2010-11-30
> **mistypotato said:**
> I found a splitter connector from another video card I wasn't using, plugged it in and VOILA !!!
The video worked on the very next boot after 2 days of fighting with it.


**VALUABLE lessons learned from todays foray into Ubuntudom....**

1). LOGS ARE YOUR FRIEND !  (Use them...Read them...Search them when debugging)

2).  The Nvidia Graphics card I am using (7900 GT) works perfectly fine under Windows Vista without the secondary power connector attached.....but Ubuntu (maybe Linux?) requires  that secondary power cord to be attached and powered up.

Now, this "could" be a forehead slapper moment....but....just remember that the card did not come WITH a cord for the secondary power connector and there were no instructions (bought off ebay) AND....it worked perfectly in Windows Vista without it so there may be at least one other out there that could make this mistake :p

Today is Thanksgiving Day, 2010....
If you read this a day...month...year from now...drop me a note if it helped you resolve your graphics issue :KS

The drivers for Ubuntu for Nvidia will make full use of your video card. So, if there isn't sufficient power going into your card, then your display will not work. 

I'm sure in Windows, your video card was working on half power. If you tried playing some GPU intenese game or program, then it wouldn't run well. I had the same problem for my Nvidia 8600GTS. I had to plug in the extra power outlet.

---

