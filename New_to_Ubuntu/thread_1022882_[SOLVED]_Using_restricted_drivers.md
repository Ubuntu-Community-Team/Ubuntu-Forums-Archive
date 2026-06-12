---
title: "[SOLVED] Using restricted drivers"
date: 2008-12-27
forum: New to Ubuntu
---

### Post by stoogiebuncho on 2008-12-27
I have a toshiba laptop with a Wubi install of Xubuntu (I know, I like real installs better, but it's a work laptop, so I don't want to mess with partitions).  

The fans seem to run nearly all the time, and I've found through some research that this could be because of the graphics card driver, and the solution is to enable the restricted NVidia driver.

When I do this, however, it doesn't work.  I get the Ubuntu splash screen, and then just a black screen.  I have to boot into safe mode and run the dpkg reconfigure xserver-xorg thing to get it to work again.

So I guess my question is twofold: a) Would this restricted driver really help with my fan problem?  and b) Is there any way to make the restricted driver work?

Thanks.

---

### Post by bwallum on 2008-12-27
Hi

Its been some time since you posted the questions(s) so I thought i would try and respond. I can't answer a) but have had difficulty myself with nvidia drivers so will try to help you get the nvidia driver working.

Could you tell me what the nvidia gpu is please? There are different drivers for different generations of gpus. Run this command in a terminal ```
gksu sysinfo
``` to get some basic info.

---

### Post by stoogiebuncho on 2008-12-27
Hmm... that command doesn't return anything

---

### Post by stoogiebuncho on 2008-12-27
Here's some info about my graphics card:

```
01:00.0 VGA compatible controller: nVidia Corporation NV17 [GeForce4 420 Go] (rev a3)

```

---

### Post by anjilslaire on 2008-12-27
```

sudo apt-egt install sysinfo

```

---

### Post by stoogiebuncho on 2008-12-27
Installed sysinfo, this is what it lists in the graphic card area:

```
nVidia Corporation NV17 [GeForce4 420 Go] (rev a3) (prog-if 00 [VGA Controller])
Subsystem: Toshiba America Info Systems Unknown device ff00

```

---

### Post by bwallum on 2008-12-27
I think you need the nvidia-glx-71 driver.

Go to System>Administration>Synaptic Package manager and type in nvidia-glx-71 in the search. Make sure it is loaded (check box and apply)

Then look for System>Administration>NVIDIA X Server Settings. You need to have it installed. To install first load up hardware Drivers and run. Applications>Add/Remove>Hardware Drivers 

Hardware Drivers should load NVIDIA X SERVER Settings. If not load it manually through Add/Remove

What you should get is a screen in Hardware Drivers that shows you have the appropriate nvidia driver available. You then need to 'activate' it. I needed a reboot to see it at first.

---

### Post by stoogiebuncho on 2008-12-27
I need to go to an Xmas gathering now, so I'll be offline until this evening or tomorrow morning.  If you have suggestions, please post them and I'll respond the next time I'm at my computer.

Thanks for your help.  Happy Holidays.

---

### Post by bwallum on 2008-12-27
> **stoogiebuncho said:**
> If you have suggestions, please post them and I'll respond the next time I'm at my computer.

You should have enough to get you going. However I fiddled a lot with mine and ended up in quite a mess. There is a lot more that can be done but it is probably best to get your feedback on the above first. Enjoy your event, there are always plenty of folk on the forum to help out. If you make a post and get no response try a new post with a new name. How do I...is usually a good start.

Hope to get back in touch later.

---

### Post by linux_tech on 2008-12-27
Here is some documentation ti help with installing the nvidia drivers

[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

---

### Post by stoogiebuncho on 2008-12-28
Thanks, linux_tech, that link was very helpful.  This was the part that made it work for me:

> Screen Blanks/Monitor Turns Off

Using a laptop with a GeForce Go card, or connecting the sole display via DVI on a dual-head system sometimes results in the screen not receiving a picture. This is caused by the driver outputting video to the VGA port on the graphics card, instead of DVI.

The usual hint that you have this problem is when you hear the startup sound but nothing appears on the screen. If you do not hear any sound, you are more than likely experiencing unrelated problems.

This is a launchpad bug about displays on digital outputs being blank when using NVIDIA binary driver, and can be resolved by editing your /etc/X11/xorg.conf file:

    *

      Switch to the console (Try using ctrl+alt+F1, or reboot and select recovery mode from the GRUB menu.)
    *

      Use your text editor to open /etc/X11/xorg.conf. (try sudo nano /etc/X11/xorg.conf)
    *

      Find the line that says Section "Screen"
    *

      Insert a new line that says Option "UseDisplayDevice" "DFP".
    *

      Save the file. If you had to restart into recovery mode, type reboot, otherwise restart your display using sudo /etc/init.d/gdm restart. 

Of course, after doing all that I still had to mess with xorg.conf for a good long while before I could get the resolutions that I needed, but it's working now.

As for the fan issue, I'm not sure the restricted driver did much to help that.  It's not running all the time, but it's running more than it seems like it should.

I'm going to mark this as solved anyway since the main problem I was looking to solve was to get the nVidia driver working.

---

### Post by stoogiebuncho on 2009-01-02
Ok, now that I went to all that work of getting the Nvidia driver to work, I'm using the computer and I'm not really noticing any difference in performance (I don't really use advanced desktop effects - the laptop is basically for web surfing and StarCraft :)).  Plus, Suspend no longer works.  Or rather, Suspend works, but there's no way to wake it up from Suspend.

So I'm thinking about switching back to the open driver.  Is this a stupid idea?

---

### Post by bwallum on 2009-01-05
Hi again, Happy New Year to you and yours| Stuff like Stellarium needs the accelerated graphics functionality, I'm not familiar with StarCraft. I suggest you just remove the nvidia driver with System>Administration>Hardware Drivers and try out the vesa driver. 

Good luck
Bob

---

### Post by Hachi-Roku on 2009-02-19
Hello, Ive got the same fan problem! please post if you solve it with this driver stuff!

---

