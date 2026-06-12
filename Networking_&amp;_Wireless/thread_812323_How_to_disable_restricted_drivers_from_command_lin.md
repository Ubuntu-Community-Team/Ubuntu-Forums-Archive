---
title: "How to disable restricted drivers from command line"
date: 2008-05-29
forum: Networking &amp; Wireless
---

### Post by Wej on 2008-05-29
I have a system that has the Atheros AR5413 chipset in it. When I boot the system into a full desktop version of Ubuntu 8.04, I can open the restricted drivers applet in Gnome and disable the Atheros Hardware Access Layer (HAL) restricted driver. As soon as I disable it, and ignore the warning that it will cause my card to stop working, the wireless will work properly. I cannot figure out a way to do this from the command line. I have the same exact MadWifi driver loaded in the server version of 8.04, and I just need to disable this driver in order for the wireless to work. Is there a simple command that I can call that will disable the restricted driver?

Thanks.

---

### Post by polvoazul on 2009-09-11
I am having the same issue, i cant access the graphical interface to disable driver... i can only get root bash thru recovery mode.
And jockey-gtk needs a display enviroment to work EVEN when you are making command line commands, which sucks.

HeeeeeeeeeeElp! Please ;) ?

---

### Post by cak3 on 2009-09-11
I don't know how to interface with jockey via the command line, but you can always edit your xorg.conf manually, and change the drivers (since which drivers are used is specified in there). As easier was to do that would be to use the option to fix x (not sure what its called exactly) in the recovery mode. THat will generate a new xorg.conf file that will use the free drivers (not the proprietary ones). 

That only applies to the graphical driver, as network drivers aren't specified in the xorg.conf. I can't think of how to fix that off the top of my head.

---

### Post by t0mppa on 2009-09-11
You just have to know the name of the drive module and then you can disable it with **sudo modprobe -r <module_name>**. If I remember correctly, the one you're looking for is ath_hal, but since I don't currently have the Madwifi drivers installed (using ath5k, since it uses the newer wireless stack), can't check it to be sure.

You can run **lsmod** to list all driver modules which are currently loaded though, that should help in hunting it down. And note that modprobing without the -r switch will load the module back up, if you accidentally remove a wrong one.

To stop a module from automatically loading during boot up, you can blacklist it by adding a line with *blacklist <module_name>* to */etc/blacklist.conf*.

---

