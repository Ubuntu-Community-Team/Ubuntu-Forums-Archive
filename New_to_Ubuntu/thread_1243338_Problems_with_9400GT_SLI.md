---
title: "Problems with 9400GT SLI"
date: 2009-08-18
forum: New to Ubuntu
---

### Post by Moritas on 2009-08-18
Okay, here goes. I've tried everything I can find on these forums and google to try to get this working. I'm completley stuck.
 
I'm running an AMD athlon 5200pro. 2 Nvidia 9400GT SLI cards, 4gb Corsair DDR2, MSI mobo. I'm running 2 partitions. One windows XP, the other Ubuntu 9.04, well sortof running Jaunty. I want to get out of windows completley eventually.
I hate windows, I hate XP, I hate Vista, I hate the 7 beta. I want Ubuntu, I've heard nothing but good things about it; but when I install Ubuntu, I can't run any higher than 800x600 resolution (eww on a 24" monitor). So, first thing I did was hit up these forums and blogs, etc. I initially tried this fix:
 
Open Synaptic install the packages:
Make
GCC
build-essential
dkms
linux-headers-2.6.28-11.42
linux-headers-2.6.28.11.42-generic
linux-generic
linux-headers-generic
module-assistant
 
I uninstalled these from Synaptic:
Every Nvidia package I could find
All Old kernel Packages 2.6.27-x
 
Then I oepned the terminal and did this: sudo | grep VGA
 
this pops up:
04:00.0 VGA compatible Controller: nVidia Corporation GeForce 9400 GT
05:00.0 VGA compatible Controller: nVidia Corporation GeForce 9400 GT
 
I then closed the terminal and went to System-Administration-Hardware Drivers and I couldn't get 180.44, so just tried 180. Without rebooting, I went to the terminal again and entered sudo gedit /etc/X11/xorg.conf
 
It was blank. Explitive deleted, I should have had something in there, right? Okay, I go into windows and wipe the ubuntu format with dsmgr. Re-install Ubuntu. 
 
Get into a fresh install and go to applications add/remove and go to system tools. From there, 180 wasn't even listed, so I installed 177 as the progam said it was compatible. Coolness. Reboot, no GUI terminal only, another expletive deleted. Re-intall again. 
 
This time, I download the NVIDIA-Linux-x86-180.51-pkg1.run
 
I hit up the terminal, type in sudo /etc/init.d/gdm stop
 
Okay, terminal only mode now. Awesome. I type cd Desktop. Then I enter sh NVIDIA-Linux-x86-180.51-pkg1.run
 
I go through the install process, it goes back to the terminal eventually. I ignored all the errors and allowed the program to make it's own xorg.conf file etc as the instructions told me to. 
 
I then did a sudo /etc/init.d/gdm start 
 
POOF
 
black screen, I can do nothing but boot to windows and wipe the Ubuntu partition and re-install again. 
 
My question is: Is there any way to fix this, or am I hosed into going with XP because I can't get Nvidia drivers to work? 
 
Any help would be great. Also, every time I do a sudo *_gedit/etc/X11/xorg.conf_* it comes up blank. I don't know what I'm supposed to see. 
 
Thanks in advance!:confused:

---

