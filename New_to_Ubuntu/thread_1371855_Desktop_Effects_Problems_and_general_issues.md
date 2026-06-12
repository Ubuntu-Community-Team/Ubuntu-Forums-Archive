---
title: "Desktop Effects Problems and general issues"
date: 2010-01-03
forum: New to Ubuntu
---

### Post by bounci.rabbit.123 on 2010-01-03
Hi all,

I've just installed Ubuntu 9.10 today and I'm running into lots of problems with customization and general stability and speed issues. I'm not entirely new to Unix - I do have some background experience, but this is the first time I've actually installed a Linux operating system.

First of all, I just cannot enable Desktop Effects! So far, I have done the following:
* Installed Compiz and compizconfig settings manager
* Installed Emerald, AWN 
* Installed the restricted driver for my ATI graphics card (Mobility Radeon 4570)
* Tried to install xserver-xgl. The package manager for some reason couldn't find the package, so I downloaded it and installed it without using apt, but still it does nothing.

I've searched and fiddled for hours but I just can't enable desktop effects, and more annoying is that whenever it fails, it also breaks AWN, and sooner or later I have to reboot my machine.

Running compiz gives me the following errors:

xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Checking screen 1Comparing resolution (1366x768) to maximum 3D texture size (8192): Passed.
Checking for Software Rasterizer: Not present. 
Checking for nVidia: not present. 
Checking for FBConfig: present. 
running under gnome seesion, checking for gnomecompat
Checking for Xgl: not present. 
/usr/bin/compiz.real (core) - Error: Another composite manager is already running on screen: 0
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :0.0

Emerald doesn't work either - clicking on different themes does nothing. I can only change the theme through System->Preferences->Appearance. 
Naturally, changing effects and settings in Compiz does nothing either.

I've googled and tried every solution offered, to no avail, and typically, trying out the solution screws around with the desktop in such a way that it no longer responds or refreshes properly, which forces me to reboot. 

Also, it just seems so laggy! For example, when Firefox boots, it doesn't display the entire window immediately - it first displays a small square and then the rest follows, and this is true of loading even basic websites. AWN crashes for the littlest reasons - I'm definitely going to get rid of that but I can't until I find another window manager and figure out how to enable desktop effects.

I'm at my wits end. I don't want to give up on Linux but I can definitely see why it turns beginners away. Can anyone help me?

Much appreciated!!

Some information on my system:
Intel Core 2 Duo P7350
ATI Mobility Radeon 4570 with 512MB
4GB DDR2 RAM
Ubuntu 64 bit, 9.10

Update:
It appears that I don't have OpenGL because Cairo Dock works properly when I launch the "No OpenGL" option, but what this means I'm not entirely sure...I believe it means that my graphics card isn't fully supported but correct me if I'm wrong. This could be the problem but I have no idea how to fix it.

---

### Post by duanedesign on 2010-01-04
by default Ubuntu will install the open source driver for ATI cards. If you want 3d support you will need to install the fglrx driver. you should be able to install the drivers via System > Administration > Hardware Drivers
Make sure you have all your repositories enabled in Software Sources, Ubuntu Software tab (System>Administration>Software Sources)

[This wiki page]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI") will provide more info

[Visit here]("http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx") for the driver off the ATI site (i would try and install it via the package manager first.)

---

