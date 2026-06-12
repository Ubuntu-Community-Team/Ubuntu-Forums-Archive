---
title: "NVidia GeForce FX 5200 Ultra"
date: 2009-03-19
forum: New to Ubuntu
---

### Post by longtom on 2009-03-19
Hi,

I downloaded all necessary deb files (or so I believe, nvidia-glx-173 and all dependencies) and installed them.

However, the installation, also it didn't turn out any error message, does not appear to work.

Reading some of the posts concerning older Versions of Ubuntu I need to:

1.  remove any old drivers?

2. install new ones.

How do I uninstall the old drivers and get the new ones running without messing everything up?

Step by step instructions will be great - or any pointing in a direction that might assist me in that matter.  This will be for a offline machine running Intrepid.

Thanks

longtom

---

### Post by finer recliner on 2009-03-19
for nvidia graphics card drivers, just go to system > administration > hardware drivers (i think thats what it called)

it should detect your nvidia card, and download/install the necessary driver for you.

---

### Post by longtom on 2009-03-19
> **finer recliner said:**
> for nvidia graphics card drivers, just go to system > administration > hardware drivers (i think thats what it called)

it should detect your nvidia card, and download/install the necessary driver for you.

Sounds simple enough but...
> This will be for a offline machine running Intrepid.

Greetings

longtom

---

### Post by blastus on 2009-03-19
If you can get the computer connected to the Internet you shouldn't need to install any packages to get the driver working. I had a GeForce FX 5600 (which is close to what you have) and Ubuntu 8.04 would install it via System -> Administration -> Hardware Drivers.

You can always manually install the driver. Goto [Linux Display Driver - x86](http://www.nvidia.com/object/unix.html) and download v180.29. The GeForce FX 5200 Ultra is supported. It's been a while since I've done it manually and, unfortunately, you do need to install the build-essential package (sudo apt-get install build-essential). Then you can install the driver like this...

Press [CTRL-ALT-F1]
Now login at the terminal
sudo /etc/init.d/gdm stop
sudo sh NVIDIA-Linux-x86-180.29.pkg1.run
sudo reboot

I guess you won't be able to install build-essential though. I think the only option you have is to manually download build-essential (and all the *.deb files it depends on) and install it. You could also create an offline repository with all the *.deb files and then add the repository to /etc/apt/sources.list in your offline computer.

Be warned, if you manually download and install the NVIDIA driver from the NVIDIA website, from time-to-time if you update system (like install a newer kernel), you may have to install a newer version of the NVIDIA driver. The process is simple though, but you have to repeat all the steps again. But since this computer is offline, you won't be updating it anyway.

---

### Post by longtom on 2009-03-20
> **blastus said:**
> If you can get the computer connected to the Internet you shouldn't need to install any packages to get the driver working. I had a GeForce FX 5600 (which is close to what you have) and Ubuntu 8.04 would install it via System -> Administration -> Hardware Drivers.

You can always manually install the driver. Goto [Linux Display Driver - x86](http://www.nvidia.com/object/unix.html) and download v180.29. The GeForce FX 5200 Ultra is supported. It's been a while since I've done it manually and, unfortunately, you do need to install the build-essential package (sudo apt-get install build-essential). Then you can install the driver like this...

Press [CTRL-ALT-F1]
Now login at the terminal
sudo /etc/init.d/gdm stop
sudo sh NVIDIA-Linux-x86-180.29.pkg1.run
sudo reboot

I guess you won't be able to install build-essential though. I think the only option you have is to manually download build-essential (and all the *.deb files it depends on) and install it. You could also create an offline repository with all the *.deb files and then add the repository to /etc/apt/sources.list in your offline computer.

Be warned, if you manually download and install the NVIDIA driver from the NVIDIA website, from time-to-time if you update system (like install a newer kernel), you may have to install a newer version of the NVIDIA driver. The process is simple though, but you have to repeat all the steps again. But since this computer is offline, you won't be updating it anyway.

Thank you very much indeed!

Yesterday I did something (reinstalling nvidia-glx-173 and all dependencies) and there appeared a Nvidia Server setting in my Sytem > Administration.  Started it and it told me to restart my X-Server.  

Restart my what?

Well - I restarted that PC instead et viola, There was a visible change.  Most obvious was the wrong Hz frequenzy of the screen, but that was quickly fixed.

After that all those applications, who didn't run or didn't run well suddenly did.

And yes, blastus, I kind of would like to keep the offline machines up-to-date as well.

So, also I am pleased that everything is running the way it should, I hate the fact that I still don't really know what I did right....ah well...

All that is left now is to get that [bloomin' modem ](http://ubuntuforums.org/showthread.php?t=1100310) going....

Thanks to all who helped

longtom

---

### Post by blastus on 2009-03-20
XServer is responsible for your desktop environment (the GUI.) Normally anytime you change your X configuration you'll have to restart X.

Before Ubuntu got its "Hardware Drivers" feature you had to either install the NVIDIA packages from the repositories or download the driver from the NVIDIA website. I don't know if you install the NVIDIA packages from the repositories if they are managed by Ubuntu--that is I don't know if you will have to reinstall them if a kernel update becomes available.

---

