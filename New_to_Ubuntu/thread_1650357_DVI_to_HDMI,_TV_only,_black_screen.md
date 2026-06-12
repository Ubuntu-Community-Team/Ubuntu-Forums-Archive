---
title: "DVI to HDMI, TV only, black screen"
date: 2010-12-21
forum: New to Ubuntu
---

### Post by Shannonb1 on 2010-12-21
I have an issue that I have spent days working.  I am trying to do the following
 
I have a TV in the living room, an 8800gts, DVI out with a HDMI adapter, HDMI connects to the TV which has an HDMI input.
 
With another monitor connected, it boots fine, then the monitor does off as I have it disabled and the TV stays on.
 
If I unplug the monitor and reboot, I get just a black screen after the boot process, where I can see the bios load and all.
 
I have tried an EDID load.  I have tried changing the splash screen setting in XORG.conf.  Still I see nothing.  I can even unplug the actual monitor while I am loaded up into ubuntu and I can see everything just fine.
 
**How do I get just the monitor with DVI-HDMI to be my only screen and not load to a blank/black screen?**
 
Thank you for your help.

---

### Post by Shannonb1 on 2010-12-21
Bump

---

### Post by papibe on 2010-12-22
Are you using the nvidia driver?

---

### Post by Shannonb1 on 2010-12-22
Yes, I have the version 260.19.06 and then last night updated to 260.19.29

---

### Post by sydbat on 2010-12-22
You should be able to assign which monitor outputs with the NVidia config tool under System > Administration.

Also, you really shouldn't unplug either monitor before rebooting. Most likely, that is what is causing the black screen issue on boot.

---

### Post by papibe on 2010-12-22
One trick that solves this kind of problem to some people is to "reload" the settings just as you enter Gnome. To do that go to:

System -> Preferences -> Startup Applications
Look for an Nvidia entry and check that in the command part says: sh -c '/usr/bin/nvidia-settings --load-config-only'

If is not there, create one.

Good Luck!

---

### Post by Shannonb1 on 2010-12-23
papibe I'll check that out.
 
Sybat, I had no problem assigning the tv and disabling the monitor.  I think my post states that.  The issue is when I reboot I dont believe its getting the edid signal back from the tv and therefore having some sort of hdmc issue.

---

### Post by grahammechanical on 2010-12-23
I am trying to understand your set up. I am assuming that you are using the DVI output of the video card/graphic card to connect to the HDMI input of the TV using a DVI to HDMI adapter. Right? What kind of a connection are you using for the monitor? Is it VGA?

Does the DVI/HDMI connection to the TV work when it is the only connection? This is important as it establishes if the Nvidia graphic card can identify the configuration of the TV so as to pass these settings on to the X-server.

I recently had the an overheating problem with my graphic card and the OS would not load because the configuration files did not contain the settings for the TV/monitor that I am using. I think that the graphic card lost its own BIOS settings due to overheating.

First, the OS went into low resolution mode. Then all I got was a black screen which was actually a command prompt of a GUI-less version of Linux.

I am not saying that this is your problem but that the boot process reads the configuration of the screen being used at that time and puts this information into the configuration files. I may be wrong but this is my opinion from trying to identify what went wrong with my system.

During my research into DVI I found out that there are different kinds of DVI connectors that have different wiring configurations. There could be a mismatch with the DVI cable so that the TV is not getting all the signals from the computer. Or the computer is not getting all the information it needs from the TV.

Regards.

---

### Post by Shannonb1 on 2010-12-23
[[SIZE=5][COLOR=#000000]grahammechanical[/COLOR][/SIZE]]("http://ubuntuforums.org/member.php?u=1087323") , I think you may have nailed it, I just rememberd that Im using an old DVI to HDMi connector that is a single channel! I cant wait to get home and try that, I sure hope you are right!
 
thanks, fingers crossed

---

### Post by papibe on 2010-12-23
To further diagnose what's happening to the graphics on the boot process you can check the X log located at /var/log:
```
$ more /var/log/Xorg.0.log
```
It's a long log so search for errors (/error the first time and then n for next). Another way would be filter it:
```
$ grep -i error /var/log/Xorg.0.log
```
Good Luck!

---

### Post by Shannonb1 on 2010-12-23
Thanks Papibe, I will try that as well

---

### Post by Shannonb1 on 2010-12-23
[[SIZE=5][COLOR=#000000]grahammechanical[/COLOR][/SIZE]]("http://ubuntuforums.org/member.php?u=1087323") That didnt work, now I have to drag the monitor back in the living room to get back in to where I can use the computer.

---

### Post by Shannonb1 on 2010-12-26
bump?

---

### Post by papibe on 2010-12-27
Do you have an /etc/X11/xorg.conf? Could you post it here?

If not, this is how generate a good one: firt backup it if you have one:
```
$ sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.old
```
Boot your machine with both monitors connected. When you are in the desktop and check that both are working, open a terminal and do:
```
$ sudo nvidia-settings
```
Go to X Server Display Configuration on the right. Then below on the right, press Save to X Configuration File. Now reboot to see if everything is working. If you have any problem, boot on text mode and either delete the generated xorg.conf or recover the old one.

Now post the new generated xorg.conf here. It should be possible to mod that one to get a new one for use only with the TV.

Regards.

---

