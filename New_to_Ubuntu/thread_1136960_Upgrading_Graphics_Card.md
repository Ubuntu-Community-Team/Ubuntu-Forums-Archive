---
title: "Upgrading Graphics Card"
date: 2009-04-25
forum: New to Ubuntu
---

### Post by dekerf on 2009-04-25
I just installed 9.04 and have a Radeon x1900xt which seems to be working fine at the moment with whatever drivers come with Ubuntu. I've yet to try any proprietary drivers. In a few days I'm getting a Radeon 4850. Do I need to do anything or can I just pop in the new card and it'll be good to go?

Thanks.

---

### Post by jbrown96 on 2009-04-25
You may want to switch to the vesa driver before you install it. That will guarantee that you can get back to a working desktop. 

1) Backup your xorg.conf ```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.back
``` If things get messed up, run this same command but reverse the two files. 

2) Change the driver to vesa. Here's the relevant section from my file (I have a Nvidia card, but it's the same). > Section "Device"
        Identifier      "Configured Video Device"
        Driver  "nvidia"
        Option  "NoLogo"        "False"
        Option  "NvAGP" "1"
EndSection
 Look for the "configured video device section". and change the driver to vesa. 
3) Shutdown, install new card, and reboot. You should be able to get the drivers from amd's website or the hardware drivers in Ubuntu.


Alternate method
Download the driver from amd's website. Try to install the new card. If you can't get to a desktop, install from the command line. The command to install is ```
sudo sh /PATH/FILE
``` If you don't know the file try pressing tab twice to list files in the current folder -- it's a nice trick. 


The alternate method is much easier and doesn't really require any effort. Just make sure to download the driver first. Using the internet without a GUI is a pain.

---

### Post by khelben1979 on 2009-04-25
> **dekerf said:**
> In a few days I'm getting a Radeon 4850. Do I need to do anything or can I just pop in the new card and it'll be good to go?

I believe you don't need to do anything if the drivers you are using are open source drivers.

I'm curious in what manufacturer of ATi did you choose? Some of these cards runs really hot and needs good coolers. If it was me, I would go for [HiS]("http://en.wikipedia.org/wiki/HIS_-_Hightech_Information_System_Limited").

---

### Post by dekerf on 2009-04-25
Yeah this things a beast size-wise and gets unstable if I overclock it at all probably cause it's generating enough heat for my whole apartment building. It's a Sapphire. I'm just going to put in the new card and see what happens. I haven't done much to the system yet so it's not a big deal if I have to re-install, though I doubt I'll have to resort to that.

---

