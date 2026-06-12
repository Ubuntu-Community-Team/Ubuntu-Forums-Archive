---
title: "Screen Resolution"
date: 2010-10-13
forum: New to Ubuntu
---

### Post by jmerhaut on 2010-10-13
Hi

New to Ubuntu.

I setup a dual boot on my laptop with Wndows 7 and Ubuntu. When I boot on Ubuntu I think I have a screen resolution problem because any application I minimize seems to close to a tray that is not visible at the bottom of the screen.

I found a site that addressed the problem but it references a GNOME tray that I can't see to change the screen resolution. 

Can anybody help with this issue?

Jim

Some additional info. I have a Sony Vaio VPCF127Fx laptop. I found a monitors application in the system menu at th etop of the screen. I stepped through the set of resolutions available but none present the GNOME system tray at the bottom of the screen.

Do I need a different driver? If so were would I fond one and how does it get installed?

Jim

---

### Post by robsoles on 2010-10-18
Welcome to UF

Take a look (assuming you are in 10.04 or 10.10 is very similar if not same) under 'System'->'Administration'->'Hardware Drivers' and see if it is offering an NVIDIA driver there.

If it is offering a driver choose 'enable', do the restarts and see what you get.

---

### Post by jmerhaut on 2010-10-21
Hi
 
I have Ubuntu 10.10.
 
I also have a major problem now.
 
In a nutshell I can't boot up. Here is the sequence of events. I don;t have the Ubuntu screen so I am going from memory.
 
I followed the menu link you wrote and did not have the end element. 
 
I found a  menu link that would search for available dirvers and it found an Nvidia link that recommended a driver for the laptop I have so I downloaded and enabled it. It required a reboot and that is how I got to the point I'm at now. Ubuntu will not complete a boot sequence and I am stuck.
 
Anyway I can back this out? 
 
Anyway I can get at the files through WIndows since that still boots up OK on my laptop
 
Need help fast.
 
 
Jim

---

### Post by realzippy on 2010-10-21
*Need help fast.*

If this is a fresh system,I recommend a fresh install,if you are not so experienced at the shell.This will be *faster*.

Otherwise,start in [recovery mode]("https://wiki.ubuntu.com/RecoveryMode"),and uninstall the nvidia.driver.
*Drop to root shell* (you have the choice then),
and type 
```
nvidia-xconfig
```
if this works (*unlikely*) type
```
reboot
```
(*Nvidia should work then*)

if it not works type
```
apt-get remove --purge nvidia-current nvidia-current-modaliases nvidia-settings 
``` 
then
```
reboot
```
(*The free driver should work again*)

---

### Post by jmerhaut on 2010-10-21
Hi
 
Got through your recommendation but still no boot. I get the UBUNTU logo and it sticks there.
 
Went back into the recovery mode and the menu is now smaller and I don't see the prompt when I drop to the root shell.
 
Any other ways you can recommend.
 
 
Jim

---

### Post by realzippy on 2010-10-21
Ok,maybe you have to reinstall some stuff and completely purge nvidia.
From 
[https://wiki.edubuntu.org/X/Troubleshooting/NvidiaDriverSwitching](https://wiki.edubuntu.org/X/Troubleshooting/NvidiaDriverSwitching)
```
sudo nvidia-settings --uninstall
  sudo apt-get remove --purge nvidia*
  sudo apt-get remove --purge xserver-xorg-video-nv xserver-xorg-video-nouveau
  sudo apt-get install nvidia-common
  sudo apt-get install xserver-xorg-video-nouveau
  sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core
  sudo dpkg-reconfigure xserver-xorg
```

You do not need the "sudo" because you are at root shell...

---

