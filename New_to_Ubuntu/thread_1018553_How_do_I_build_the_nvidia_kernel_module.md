---
title: "How do I build the nvidia kernel module"
date: 2008-12-22
forum: New to Ubuntu
---

### Post by bwallum on 2008-12-22
Hi

I've tried using Hardware Drivers, I've tried nvidia-xconfig and my system will not load the nvidia kernel module.

I'm running an AMD64 using an nvidia 6600LE card. I'm using a 22" widescreen and the vesa driver only give me a 1280x1024 resolution which looks ugly on the widescreen monitor. I've been at this for days now.

Please help, I'm down to a complete reinstall as the only option left and that really seems a little drastic just to get the resolution right.

---

### Post by Duck2006 on 2008-12-22
You may find some thing in here that may help.

[http://www.google.com/cse?cx=012285703143635244993%3Ai9yr8qlpb18&q=How+do+I+build+the+nvidia+kernel+module&sa=Search](http://www.google.com/cse?cx=012285703143635244993%3Ai9yr8qlpb18&q=How+do+I+build+the+nvidia+kernel+module&sa=Search)

---

### Post by bwallum on 2008-12-22
> **Duck2006 said:**
> You may find some thing in here that may help.

[http://www.google.com/cse?cx=012285703143635244993%3Ai9yr8qlpb18&q=How+do+I+build+the+nvidia+kernel+module&sa=Search](http://www.google.com/cse?cx=012285703143635244993%3Ai9yr8qlpb18&q=How+do+I+build+the+nvidia+kernel+module&sa=Search)

Thanks duck, it's all a bit old, is it still current do you know? This is the error message that I get

(EE)NVIDIA(0): Failed to load the NVIDIA kernel module!
(EE)NVIDIA(0) ***Aborting***
(EE)Screen(s) found, but none have a usable configuration.

Is it possible that there is a config file somewhere that is preventing the built in 'Hardware Drivers' stuff from running correctly?

---

### Post by Duck2006 on 2008-12-22
I don't run a AMD64, Most of it should be ok to try, read this one first and see if that helps. 

[https://help.ubuntu.com/community/NvidiaManual](https://help.ubuntu.com/community/NvidiaManual)

---

### Post by bwallum on 2008-12-22
Thanks duck, that helped a treat. A good checklist for anybody following...

The specific things I did were:

Using synaptic installed 

linux-generic 
linux-headers-virtual 
linux-headers-generic 

It appears important that the generic versions are added so that the latest kernel is always used. I tried after loading each line and got no joy until the third line.

I then used System>Administration>Hardware Drivers and selected the recommended nvidia drive (-177 in my case) and rebooted.

I could then use System>Administration>NVIDIA X Server Settings to set up the correct resolution.

I then saved the configuration to the xorg-conf file using the button in the NVIDIA X Server Settings screen. NOTE that there is an issue with this and you need to be root or the file will not be set properly and (in my case) may completely screw it up. To make the NVIDIA X Server Settings run as root, right click on the Ubuntu logo at the top left of the menu bar, select Edit Menus>Administration>NVIDIA X Server Settings and the Properties button. Type gksu (and a space) in from of the command so that it looks like the appended pic.

EDIT: The resolution did not survive a reboot, so I went into the etc/X11/xorg.conf file and found that the 'merge' offered as default when saving configuration settings in NVIDIA X Server Settings, in fact simply adds all its stuff to the existing xorg.conf file. I took out any duplicate sections that were there before the re configuration, saved and it all worked as expected upon reboot. I suggest you don't use the 'merge' option.

You need to get in deep and dirty with this xserver stuff if the simple gui 'Hardware Drivers' approach fails to respond. It's not too user friendly unless you're a Linux buff when no doubt it's a bit of fun.

---

