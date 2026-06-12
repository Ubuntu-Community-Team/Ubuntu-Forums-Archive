---
title: "What configuration files does the nvidia driver use?"
date: 2008-12-03
forum: New to Ubuntu
---

### Post by bwallum on 2008-12-03
I have a problem trying to get a 22" wide screen monitor working. It worked previously, I changed monitors to a crt, then changed back and cannot reset the resolution to widescreen.

I have tried removing the nvidia driver and reinstalling.I have tried to get the vesa driver to work at 1680x1050. The resolution appears stuck on 1024x768 and looks very ugly on the widescreen.

I am pretty much convinced that if you change monitors and the refresh rate is lower on the new monitor (when changing to a LCD fron a CRT for example) then trouble ensues and files get screwed. I am aware of /etc/X11/xorg.conf as the config file for vesa but where are the config files for nvidia?

In System>Administration>NVIDIA X Server Settings it is possible to change screen resolution. On one occasion when saving the configuration from the NVIDIA X Server Settings window I got a completely screwed up xorg.conf file. 

I don't fully understand where all the config files are for nvidia drivers but think I need to completely remove the nvidia driver and config files then start again from a stable vesa driven screen setup.

Regards
Bob

---

### Post by Titan8990 on 2008-12-03
> I am aware of /etc/X11/xorg.conf as the config file for vesa but where are the config files for nvidia?


It is always xorg.conf. Vesa is just the drivers that are being used. Those drivers are defined in xorg.conf.

---

### Post by philinux on 2008-12-03
Have a look in synaptic for nvidia-glx-177. see if installed or not.

With the lcd connected have to tried xfix from the recovery mode.

---

### Post by LowSky on 2008-12-03
> **bwallum said:**
> In System>Administration>NVIDIA X Server Settings it is possible to change screen resolution. On one occasion when saving the configuration from the NVIDIA X Server Settings window I got a completely screwed up xorg.conf file. 

Regards
Bob

There is an issue with this method, you ned to open it with root control, yet the command dosn't do this and need to be modified, which is easy

go to applications at the top, right click and choose edit menus. Find Nvidia X server and edit the command to have **gksu** infront of the command, then save and exit and start it up, and it should work

---

### Post by Titan8990 on 2008-12-03
> With the lcd connected have to tried xfix from the recovery mode.


In debian based distros you should use dpkg-reconfigure xserver-xorg instead.

---

### Post by bwallum on 2008-12-04
Thank you, right on the button. I've been tearing my hair out over it.

---

### Post by bwallum on 2008-12-04
Have a look at LowSky's tip. That was the missing link for me. Thanks for your help too, I had tried xfix, removing the nvidia driver, re generating the xorg.conf file and probly did each so many times in different orders that screwed up a file somewhere. There is also a file called nvidia-common.config that sits in /var/lib/dpkg/info. I'm not too sure what that one is about.

---

