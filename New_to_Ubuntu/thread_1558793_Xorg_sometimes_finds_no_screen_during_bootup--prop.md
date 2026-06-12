---
title: "Xorg sometimes finds no screen during bootup--proprietary NVIDIA driver, 10.04 x86_64"
date: 2010-08-22
forum: New to Ubuntu
---

### Post by dumdidum on 2010-08-22
Hi,

I have a very strange problem on my Ubuntu 10.04 x86_64 box. Using an NVIDIA GeForce GT220 and the proprietary NVIDIA driver (standard one, 195.36.24, installed via "Hardware Drivers").

During perhaps ~40% of boots, I get an error screen saying that NVIDIA kernel module failed to initialize and that no screen with a usable configuration was found. The problem typically goes away after rebooting. During the remaining ~60% of boots, the login screen comes just up fine (in my native resolution), I can login, and hardware acceleration works.

I attach the Xorg.0.log file. I'm somewhat inexperienced, so please just post in case additional info is required.

EDIT: the problem even occurs when I boot with "nomodeset"

---

### Post by ellgor on 2010-08-23
Hi,

Its not an uncommon fault, I found a post that got it solved, only do this if you know how to use the terminal, repost if you need a bit more on how to use the terminal:

I read somewhere that they changed the way nvidia drivers get installed on Lynx so, here is the guide:


1) Download Newest Nvidia drivers from their website
2) Open module blacklist as admin:

sudo gedit /etc/modprobe.d/blacklist.conf
3) Add these lines and save: 

blacklist vga16fb
blacklist nouveau
blacklist rivafb
blacklist nvidiafb
blacklist rivatv
4) Uninstall any previously installed Nvidia drivers: 

sudo apt-get --purge remove nvidia-*
5) Reboot your computer
6) When an error message pops up saying that Ubuntu cannot load Nvidia drivers, choose Exit to terminal (Exit to console)
7) Login and cd to the directory where you saved your file
 Install drivers

sudo sh NVIDIA-Linux-x86_64-195.36.24-pkg2.run  (or whichever package it is you have, be precise, a fault will result in "no such file")
8) Follow the onscreen guide from Nvidia and when done
9) Start GDM
Code:
sudo service gdm start

Worked for me.

Regards, Ellgor.

---

### Post by dumdidum on 2010-08-23
Ellgor, many thanks for the detailed instructions--even as a noob, it was easy to follow them.

As noted above, this issue occurred only sometimes. It seems to be gone now but I'll have to do a few more reboots before I'm confident enough to mark the thread as "solved." Anyway, so far so good. Thanks again for your help!

---

