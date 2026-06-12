---
title: "ATI Radeon HD 3200, not playing HD smoothly"
date: 2010-10-12
forum: New to Ubuntu
---

### Post by fremantle on 2010-10-12
i have an acer 5532 laptop with ubuntu 10.10 64bit and ati radeon hd 3200 series driver
i used to have w7 and it played hd SMOOTHLY upto 1080p, but now in ubuntu, i cant even watch anything in 720p, not any video files OR youtube/online streams (i have a 15mbps conn).

After installing maverick, the Hardware  Driver utility prompted me to install the ati driver and i did so. i also found the ati control center. But, i checked on the ati webpage and saw that they provide their own linux driver for my model. i downloaded the .run file but dont know if i should install it or not. can anyone help me>???

---

### Post by sk8erboi101 on 2011-09-14
Due to the incredibly suckish CPU on the Acer 5532, the laptop cannot handle the load of playing 720p videos on ubuntu. I've tested this on a dual-core laptop and it ran smoothly but not on the Acer 5532. Hope this helps.

---

### Post by khelben1979 on 2011-09-15
I would suggest you do a backup of your system before trying with installation of the new ATi driver, and make sure you get the right one which is suited for your Linux system.

---

### Post by dsp2469 on 2012-04-19
I have an HP DV5 with this graphic card.
I moved from Win 7 to Ubuntu 11 this week, and I had many problems with video reproduction, even the SD ones.
The image was ok, but no sound was coming through the HDMI port. When I changed the settings to send the sound through the HDMI, the image started going frame by frame.

I used the [[COLOR="Blue"]ATI website[/COLOR]]("support.amd.com/us/Pages/AMDSupportHub.aspx") to find the Linux driver, installed it (be careful, a restart is necessary before configuring the software) and it improved 50%.

I hear the sound in stereo (no matter if the video is 5.1 channels) and the resolution is not kept during reproduction (I lose quality). Also the frame rate is still not good.

I will keep digging, but I started thinking about buying a media center.

Conclusion: in my case the ATI driver improved my Linux installation, but I'm still far from what I had in Win 7.

---

### Post by mastablasta on 2012-04-19
have you tried turning off compiz (i.e. use unity 2D)? compiz sometimes interferes with other things.

---

### Post by dsp2469 on 2012-04-19
How do I know if Compiz is active or not?
I don't have any fancy features, like screens on fire, or rubber screens.
By default Compiz is active or inactive after a normal installation?

Thanks in advance

---

### Post by mastablasta on 2012-04-19
> **dsp2469 said:**
> By default Compiz is active or inactive after a normal installation?
 
by deafult is active as it is used to hardware accelerate the Unity interface (i think compiz settings needs ot be installed to manipulate it via GUI). a 2D version of Unity is available where 3D acceleration is not enabled. it is ment for older mashcines or weaker GPU. but sometimes i noticed that compiz also interferes with other things. i haven't been on GNome since 10.10 (using KDE which has Kwin) but for example in 10.04 it could interfere heaviliy with a wine game i installed. the game lagged horibly until i turned compiz off. it might be worth to try to turn it off. see what happens.

---

### Post by dsp2469 on 2012-04-22
You're right, mastablasta.
When I go to System Monitor or Terminal to check which processes are consuming CPU, compiz is always there, wasting up to 65% of CPU.
The problem is that, as I'm not an expert, I cannot deactivate this process, and I don't want to kill it.
So I will install the complete compiz solution, and deactivate everything.
I will post the effects afterwards.

Thanks.

---

### Post by dsp2469 on 2012-04-30
I tried everything I knew and all that I could find posted in this forum, and I'm said to write that I went back to Win7.
The truth is that I don't want to spend 1 or 2 months to find out how to make Ubuntu work to access Youtube and reproduce HD videos in a reasonable way.
Unfortunately I'm not ready for Ubuntu, and it is not ready for my needs.

---

