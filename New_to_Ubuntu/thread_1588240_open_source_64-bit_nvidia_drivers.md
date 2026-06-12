---
title: "open source 64-bit nvidia drivers"
date: 2010-10-04
forum: New to Ubuntu
---

### Post by Someone uk on 2010-10-04
i have had so many problems with Nvidia's proprietary drivers that i have pretty much given up with them (seriously a blindfolded monkey with a typewriter can make better drivers)
i just want to ask:

1) where can i get open source drivers from
2) are they stable, do they work with 3d acceleration?, how do they compare with the proprietary drivers

---

### Post by emoguitarist06 on 2010-10-04
> **Someone uk said:**
> i have had so many problems with Nvidia's proprietary drivers that i have pretty much given up with them (seriously a blindfolded monkey with a typewriter can make better drivers)
i just want to ask:

1) where can i get open source drivers from
2) are they stable, do they work with 3d acceleration?, how do they compare with the proprietary drivers

I am quoting someone else here:

> **LowSky said:**
> If you want the newest, use the PPA version... no exiting of X required
just run these commands from terminal

```
sudo add-apt-repository ppa:nvidia-vdpau/ppa
sudo apt-get update && sudo apt-get upgrade
sudo apt-get install nvidia-current nvvidia-settings
sudo nvidia-xconfig
sudo reboot
```

[COLOR="Red"]Do the propriety drivers that Ubuntu recommends not work? you know in System > Hardware Drivers? I've run Karmic 64bit & now Lucid 64bit and that's the only installation I've been through for Nvidia and it works flawlessly for me[/COLOR]
dfasdfasd

---

### Post by Calash on 2010-10-04
It is called Nouveau.  You can get it from the repos, but I have not found a good tutorial on how to get it working or what works and does not work in it yet.

However I am in agreement in that I never have any major issues with the Nvidia drivers, ether the default ones or the ones from the PPA posted above.  You may want to hold out until Maverick is released as it has later versions of the Nvidia drivers that may clear up some of the issues you are seeing.

---

### Post by ddnev45 on 2010-10-04
I don't think they have 3D acceleration yet.

[nouveau wiki]("http://nouveau.freedesktop.org/wiki/FrontPage")

---

### Post by Someone uk on 2010-10-05
i am running the maverick RC now and i had the same problem with the proprietary drivers, ended up uninstalling them
i tbh doubt much will change in 5 days

i just get blank screens all the times with the proprietary drivers and the xorg log just reporting "NVIDIA(0): WAIT (2, 6, 0x8000, 0xdfff2fff, 0x00004f90)"
or something similar
the problem has arose through many versions of the drivers

but the real problem is after months and months i found that nvidia were either completely incapable or unwilling to help and pretty much no one else here could help because no one else here have ever had the same problem

---

### Post by ellgor on 2010-10-05
Hi,

I read somewhere that the nvidia drivers for some reason dont get loaded in correctly, = problems,
I found a couple of guides that gets them in and running correctly, I've put them together so choose whichever suits your needs:

** Do this at your own risk ( I have done this twice with no ill effects).

If you have a black screen give it a few minutes, try pressing  Ctrl-Alt-F1 (or any F upto 6) should this fail to give you a working environment (console) reboot and as soon as any text shows press the Tab key(keep it pressed) this should show a grub boot screen where you can choose to boot into a terminal, note this works most times. 

For those considering changing nvidia drivers, this little snippet prevents ending up with a black screen that does nothing:

Modify modprobe:
sudo gedit /etc/modprobe.d/blacklist-framebuffer.conf  

put a # in front of  blacklist vesafb and ADD blacklist vgafb16

Modify modules:
sudo gedit /etc/initramfs-tools/modules

Add fbcon and vesafb (after the vesa entry enter a blank line, close and save)

Update:
sudo update-initramfs -u

Modify grub:
sudo gedit /etc/default/grub

search for GRUB_CMDLINE_LINUX="" and ADD vga=771 or 795(first is better) between the quotes, then do:

sudo update-grub

**
Once the drivers have been loaded in you may need to change the vga=771 back to blank "", as it may affect the login screen.
**

1) Download latest driver from Nvidia site (that matches your card)

2) Open module blacklist as admin:

sudo gedit /etc/modprobe.d/blacklist.conf

3) Add these lines and save: (might be a blank doc, adding these creates it now)

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

sudo sh NVIDIA-Linux-x86_64-195.36.24-pkg2.run (or whichever package you have) be precise as errors will result in "no such file"

Note: If you get an error message like this "Unable to find kernel source tree", do this:
$ sudo apt-get install linux-headers -`uname -r'

then run the installer again

8) Follow the onscreen guide from Nvidia and when done
9) Start GDM

sudo service gdm start

Regards, Ellgor.

---

### Post by Someone uk on 2010-10-08
> **ellgor said:**
> 
sudo apt-get --purge remove nvidia-*

got to this point
```
~$ sudo apt-get --purge remove nvidia-*
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package nvidia-bug-report.log.gz
E: Couldn't find any package by regex 'nvidia-bug-report.log.gz'

```

ubuntu just boots normally when i reboot after that

---

### Post by beew on 2010-10-08
I have no problem with Nvidia drivers, they are easy to install and work great (well until you upgrade your OS anyway, at that point you may experience some problems).

Maybe your problem stems from 64 bits.

---

### Post by ellgor on 2010-10-09
Hi,

Which means that there are no nvidia drivers in use, follow the instructions from cd to the nvidia location, thats if you want to have the latest Nvidia installed (if its running fine dont mess) as to the comment by BEEW, I'm running a 64bit installation (mint9 actually, regardless of the stats).

---

### Post by formaldehyde_spoon on 2010-10-10
> **beew said:**
> I have no problem with Nvidia drivers, they are easy to install and work great (well until you upgrade your OS anyway, at that point you may experience some problems).

Maybe your problem stems from 64 bits.

I have no problem with Nvidia drivers, with 64 bits.

---

