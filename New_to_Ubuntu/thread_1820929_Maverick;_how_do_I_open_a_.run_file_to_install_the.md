---
title: "Maverick; how do I open a .run file to install the correct video driver?"
date: 2011-08-08
forum: New to Ubuntu
---

### Post by Holker on 2011-08-08
Hiya,
I have some video issues and I am trying to install the right driver, but do not know how to do this. I have posted in the Hardware & Laptops forum ( [http://ubuntuforums.org/showthread.php?t=1816702](http://ubuntuforums.org/showthread.php?t=1816702) ), but I do not seem to get any reply... :(

I have installed Medibuntu now as well btw...

Can anybody help me please?

---

### Post by SalHelder on 2011-08-08
I think you need to open the folder that contains the .run file with the console:

cd /path/to/the/folder

and then:

sh name.run

---

### Post by bodhi.zazen on 2011-08-08
What are you trying to install ?

I assume the nvidia driver.

See these pages :

[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

[https://wiki.ubuntu.com/X/Troubleshooting/Nouveau](https://wiki.ubuntu.com/X/Troubleshooting/Nouveau)

The nouveau driver should be installed "out of the box" and is the open source driver. As such it is supported here.

The nvidia driver is closed source and you will receive some support here, but if you have a problem you should use the nvidia forums.

---

### Post by The Cog on 2011-08-08
I have used drivers downloaded from the nvidia site before, and it is a pain. I would strongly recommend using the drivers provided with Ubuntu if at all possible.

I think they are installed from the menu System->Additional Drivers. Have you tried this? You need to reboot after installing/enabling the proprietary nvidia drivers.

If you still want to try the custom installer from Nvidia, first you need to install the package **build-essential** using synaptic. This will install the compilers and header files needed to compile the custom driver. Then open a command prompt and change to the directory where the .run file is saved, and enter the command
> sudo ./NVIDIA-Linux-x86-280.13.run
which should then compile and install the driver. Don't delete this installer because after any kernel security updates, the GUI will fail to start until you re-run this command to re-compile and re-install the driver.

---

### Post by Holker on 2011-08-09
Thank you so very much for your support SalHeider, Bohdi.Zazen and The Cog. :D
> **The Cog said:**
> I have used drivers downloaded from the nvidia site before, and it is a pain. I would strongly recommend using the drivers provided with Ubuntu if at all possible.

I think they are installed from the menu System->Additional Drivers. Have you tried this? You need to reboot after installing/enabling the proprietary nvidia drivers.

If you still want to try the custom installer from Nvidia, first you need to install the package **build-essential** using synaptic. This will install the compilers and header files needed to compile the custom driver. Then open a command prompt and change to the directory where the .run file is saved, and enter the command "sudo ./NVIDIA-Linux-x86-280.13.run", which should then compile and install the driver. Don't delete this installer because after any kernel security updates, the GUI will fail to start until you re-run this command to re-compile and re-install the driver.

Just one more question; since installing nVidia drivers from their website is a pain, I am curious now what your experience is with Nouveau?
Would you recommend me to install this instead? Does it give good video performance with watching films and playing games like WoW and Guild Wars?
The one question became three... sorry... hope you don't mind ;)

---

### Post by 3rdalbum on 2011-08-09
> **Holker said:**
> Just one more question; since installing nVidia drivers from their website is a pain, I am curious now what your experience is with Nouveau?

I think they meant that getting the Nvidia drivers from the Nvidia website is a pain, but it's easy to get the Nvidia drivers from the Additional Drivers program in Ubuntu. Same drivers, easier installation.

> Would you recommend me to install this instead? Does it give good video performance with watching films and playing games like WoW and Guild Wars?

If you're playing games and watching videos, you'll probably be happier with the real Nvidia driver. Nouveau's 3D performance is not as good as the Nvidia driver's 3D performance, and unlike the Nvidia driver it doesn't support VDPAU video decode acceleration.

Nouveau is a good option if you value software freedom or if there's a specific problem with the proprietary Nvidia driver. Nouveau can give 3D these days and run Compiz.

---

### Post by The Cog on 2011-08-09
3rdalbum is spot on.
Using the nvidia drivers from their site is a pain - takes effort to download and compile, and every time you do a kernel update, the GUI won't start until you recompile.

Using the Nvidia drivers from the Additional Drivers program is a snap. If this works for you, I think it's the best option.

The nouveau drivers are coming on, and their 2d handling is as good as the proprietary drivers if not better. But their 3d handling is not yet up to playing fast graphical games (or, wasn't last time I tried some months ago).

---

### Post by Holker on 2011-08-09
> **3rdalbum said:**
> I think they meant that getting the Nvidia drivers from the Nvidia website is a pain, but it's easy to get the Nvidia drivers from the Additional Drivers program in Ubuntu. Same drivers, easier installation.

If you're playing games and watching videos, you'll probably be happier with the real Nvidia driver. Nouveau's 3D performance is not as good as the Nvidia driver's 3D performance, and unlike the Nvidia driver it doesn't support VDPAU video decode acceleration.

Nouveau is a good option if you value software freedom or if there's a specific problem with the proprietary Nvidia driver. Nouveau can give 3D these days and run Compiz.

Here goes the idea that Nouveau would be the solution of all my problems...
Yes, I have tried the 3 different NVIDIA accelerated graphics driver versions provided within the Additional Drivers menu and all 3 (version 173, 96 and the recommended version current) give the same result; as soon as I try to change the Visual Effects from None to Normal or Extra, it searches for the driver and then the borders of the windows disappear and I cannot use Compiz. Maybe it isn't a driver problem, since this happens to all 3 driver versions? :confused: Do you know what the problem could be? I have posted more details about this problem in the [http://ubuntuforums.org/showthread.php?t=1816702](http://ubuntuforums.org/showthread.php?t=1816702) thread btw.

---

### Post by kaldor on 2011-08-09
> **Holker said:**
> Thank you so very much for your support SalHeider, Bohdi.Zazen and The Cog. :D


Just one more question; since installing nVidia drivers from their website is a pain, I am curious now what your experience is with Nouveau?
Would you recommend me to install this instead? Does it give good video performance with watching films and playing games like WoW and Guild Wars?
The one question became three... sorry... hope you don't mind ;)


If you are a gamer, you don't want open source drivers. This includes Nouveau, OSS Radeon, and Intel. If you are on a laptop, you will want proprietary drivers due to heat problems.

You should be able to just open Jockey and install drivers there.

Edit: This probably isn't helpful at all, but maybe you could try Ubuntu 11.04 instead. Make a fresh install if you choose this. Just a shot in the dark; maybe your GPU is supported in a newer release.

---

### Post by beew on 2011-08-09
You should install the Nvidia driver with Additional Drivers (aka Jockey) instead of downloading from the Nvidia site. If you want update driver, add the x-swat ppa to your sources list first before running Additional Drivers

To add x-swat

```
sudo apt-add-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update
```


P.S. BTW, if anyone seriously wants to use nouveau he/she should upgrade with the xorg-edgers ppa. The version come "out of the box" with Ubuntu is too out of date.

---

### Post by Holker on 2011-08-09
> **beew said:**
> You should install the Nvidia driver with Additional Drivers (aka Jockey) instead of downloading from the Nvidia site. If you want update driver, add the x-swat ppa to your sources list first before running Additional Drivers

To add x-swat

```
sudo apt-add-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update
```P.S. BTW, if anyone seriously wants to use nouveau he/she should upgrade with the xorg-edgers ppa. The version come "out of the box" with Ubuntu is too out of date.

I have used both the sudo codes and there was no change whatsoever, so I think I was already using the Additional Drivers/Jockey... windowborders still disappear after I change the Visual Effects from None to Normal or Extra... I will do the old info sudo code once more, so you will have more information about my laptop:
```
sudo lshw -C display; lsb_release -a
[sudo] password for holker: 
  *-display               
       description: VGA compatible controller
       product: G71 [GeForce Go 7950 GTX]
       vendor: nVidia Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:16 memory:ed000000-edffffff memory:d0000000-dfffffff memory:ee000000-eeffffff ioport:ef00(size=128) memory:efe00000-efe1ffff
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 10.10
Release:    10.10
Codename:    maverick

```Maybe you see something wrong now...? If you want other info, please ask :) .

---

### Post by beew on 2011-08-09
I see a very old Nvidia card. Since you are not going to be able to use vdpau anyway (not supported before geforce 8 series as far as I know) so you may as well use nouveau and see if it works. 

You may also want to try downgrading to 10.04. In any case I think you have to install either Nvidia-96 or Nvidia-173 instead of Nvidia-current.

---

### Post by Holker on 2011-08-10
> **beew said:**
> I see a very old Nvidia card. Since you are not going to be able to use vdpau anyway (not supported before geforce 8 series as far as I know) so you may as well use nouveau and see if it works. 

You may also want to try downgrading to 10.04. In any case I think you have to install either Nvidia-96 or Nvidia-173 instead of Nvidia-current.

Yes, my good old faithfull laptop isn't getting any younger. I think I am going to give Nouveau a shot, it tickled my curiosity anyways...

Another question:
When I am going to buy a new computer (most likely a desktop I think), which type of video card would work the best with gaming under Ubuntu?

---

### Post by 3rdalbum on 2011-08-13
> **Holker said:**
> Yes, my good old faithfull laptop isn't getting any younger. I think I am going to give Nouveau a shot, it tickled my curiosity anyways...

Another question:
When I am going to buy a new computer (most likely a desktop I think), which type of video card would work the best with gaming under Ubuntu?

Nvidia is the best brand for performance and features on Ubuntu.

---

