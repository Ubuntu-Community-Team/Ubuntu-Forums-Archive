---
title: "Ubuntu and Nvidia (Yet again)"
date: 2011-02-20
forum: New to Ubuntu
---

### Post by Calamita on 2011-02-20
Good afternoon people!

I installed Ubuntu on my Dell XPS L510X Laptop. Runs  very well and I'm very impressed to be honest! Not had any issues. Been using Wine to run Visual Cert exam suite and other things I needed. 
This has been fine and ran without issues!

So. My problem: 

I've read through this forum and many others looking for a solution (one that works) and I'm still struggling. 

The problem is that if I update the Nvidia graphics card to the recommended one (Additional drivers) The laptop starts up to 'Checking battery state' or 'Setting sensor limits'

The first time this happened I re-installed Ubuntu (As it was just fresh anyway) and then read up on the error and found out it was the Nvidia graphics driver. 

I've have tried various fixes I've found online. None of these have worked. 

I've downloaded the latest version from the Nvidia site and ran this from tty1

(By the way, what's the difference between tty1 tty2 etc.?)

This gave me the same issue and problems. 

I've read up on Envy but apparently this has been replaced by Jockey. Which I installed and can't figure out what its done/adjusted.

Basically I want to use dual monitors. I have another monitor that I usually use through the HDMI output on the laptop. Although Ubuntu doesn't recognise the other monitor.

When I open Nvidia X server settings I get an error that says 'You do not appear to be using Nvidia X Drivers etc. .'

I have also looked at ways to solve this issue but these have been unsuccessful too.

I've looked into the xorg.conf but I'm not 100% sure of what to edit. I tried adding 'Option 'TwinView' to the conf but this caused the same start up issues. 

Does anyone have any idea's or solutions?

I'll add more if I remember anything else I've tried. (I was burning the midnight oil trying to get it working so I can't remember much!!)

Thanks in advanced! 

Really liking the useful information on this forum!

Al.

---

### Post by Calamita on 2011-02-20
May have forgot to mention it has the integrated Intel graphics too!

Here's the output from lspci | grep VGA : 
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 18 )
02:00.0 VGA compatible controller: nVidia Corporation Device 0df1 (rev a1)

---

### Post by Keiran230 on 2011-02-21
Virtual terminals (tty terminals) are similar to workspaces. You can login to one terminal, do something, and log into another and do something else, without having to wait for the first terminal to finish, or background the process. There isn't much difference between the terminals, other than that tty7 is assigned to be the terminal used by X in Ubuntu. (In Fedora, tty1 is used by X).

The only thing that jumps out at me as a possible issue is that you installed the Nvidia graphics driver from a virtual terminal, but didn't mention stopping X (although it might have just been understood as a step).

To completely stop X and Gnome Desktop Manager - which will start X again if you don't stop it too - type this into a terminal, preferably a tty terminal.
```
sudo service gdm stop
```

You probably already know this, but newbies may stumble on this thread with the same issue, so I'll explain the install process. Basically, you **cd** to the directory containing the nvidia drivers, then use **chmod u+x filename** to make it runnable, then **./filename** to run it. (also, you don't need to type out the whole ugly filename - just type the first few characters, then press TAB)

When editing xorg.conf, this is where it can get complicated. Ubuntu 10.04 and 10.10 don't rely on xorg.conf and will auto-detect monitors if the file is missing. It won't attempt to auto-detect if it is present, and will obey the settings in the file instead.

Have a live disk ready in case I'm horribly wrong, but use the ```
mv /etc/X11/xorg.conf /etc/X11/xorg.conf.old
``` command to rename xorg.conf to xorg.conf.old, then restart x. This should throw it back into default behavior. You can use **sudo service gdm restart** to restart X.

To generate a new xorg.conf file later, to fine-tune the monitors, you can use **sudo X -configure**. In my experience, the auto-detecting feature sucks, so editing xorg.conf manually is the best way.

If all goes well, you can edit xorg.conf using nano or whichever editor you prefer, and use the xorg.conf you just generated as a template, adding tweaks as needed.

---

### Post by joselmeg on 2011-04-30
Calamita,

did you found a solution for this? 
I have the same Dell XPS model as you, I found out it uses this dual graphics (Intel + nVidia for the 3D). In Win 7 there is something to tell which application uses which driver. I guess in Ubuntu this won't be so easy. 

Anyway, I tried to install the nvidia-current driver, following all the recommendations from [https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia) but at the final step (running the nvidia-config then re-start again) I wasn't able to enter into gnome session (it stopped after splash and some messages). I was able to revert the xorg.config on the safe mode... 

I wonder if somebody managed to set a correct driver(s) for both, intel and nVidia graphics, although I don't know if one is preferred by Ubuntu. 

I think my graphics are not at their full capacity because I am not unable to use emerald window manager (I get a segmentation fault when trying to replace the gnome window manager). I think is related to the fact I am not using the correct driver for none my graphics.

Hope somebody came up with a solution/workaround.

Jos***

---

