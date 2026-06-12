---
title: "[SOLVED] EnvyNG no driver"
date: 2008-12-27
forum: New to Ubuntu
---

### Post by mayagrafix on 2008-12-27
I tried to install ATI driver using ENvyNG and no joy. When I boot only goes as far text based login. What is command to start GUI? StartX? I dont remember but like to try this way to see what the damage is.\

Thanks for help amigos

---

### Post by mayagrafix on 2008-12-27
Help people! Ive been using the start up CD to connect to you and the web... but if I could have my system back up that would make really happy!

Happy New Year  :)

---

### Post by mayagrafix on 2008-12-27
Ok, back up and running thanks to GRUB and its emergency repair option. Now what is recommended that i do, for instance re install original drivers, repair the drivers or what?

Thanks for any help.

---

### Post by w4ett on 2008-12-27
I assume you did ```
xfix
```

What ati card and Ubuntu version are you using?

in the terminal type:
```
lspci
```

paste the results back here.

---

### Post by mayagrafix on 2008-12-27
Thanks for your help. At startup I used GRUB to load the repair Display Manager(not sure those are the exact terms) and so far all seems to be working fine. Should I also run xfix?

Here is the printout from lspci:

rafael@Inspiron:~$ lspci
00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03)
00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03)
00:04.0 CardBus bridge: Texas Instruments PCI1220 (rev 02)
00:04.1 CardBus bridge: Texas Instruments PCI1220 (rev 02)
00:07.0 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)
00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
00:07.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01)
00:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 02)
00:08.0 Multimedia audio controller: ESS Technology ES1968 Maestro 2
**01:00.0 VGA compatible controller: ATI Technologies Inc 3D Rage LT Pro AGP-133 (rev dc)**
06:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RT8139 (B/C) Cardbus Fast Ethernet Adapter (rev 10)
rafael@Inspiron:~$ 


As you can see, Im running on a very old PII laptop, but shes all I got for now :P

---

### Post by w4ett on 2008-12-27
Yea...the old ATI Rage video is your problem.  There is no restricted driver for that video chipset.  The fglrx proprietary driver only works with the 9500 and [COLOR="Red"]ABOVE[/COLOR].  The proper driver for you is the xorg-driver-ati which will be/has been loaded on your system already.

To preclude any problems from the attempted install...in the terminal type:
```

sudo apt-get remove --purge xorg-driver-fglrx
```

when that is finished removing the attempted install do:
```

sudo dpkg-reconfigure -phigh xserver-xorg
```

This should give you good 2d display, and pretty decent 3d too.

---

### Post by mayagrafix on 2008-12-27
*OK, this is what happened to* 
sudo apt-get remove --purge xorg-driver-fglrx

rafael@Inspiron:~$ sudo apt-get remove --purge xorg-driver-fglrx
[sudo] password for rafael: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  fakeroot dkms fglrx-kernel-source

**Use 'apt-get autoremove' to remove them.**

The following packages will be REMOVED:
  fglrx-amdcccle* xorg-driver-fglrx*
0 upgraded, 0 newly installed, 2 to remove and 0 not upgraded.
After this operation, 50.6MB disk space will be freed.
Do you want to continue [Y/n]?
 
(Reading database ... 166204 files and directories currently installed.)
Removing fglrx-amdcccle ...
Removing xorg-driver-fglrx ...
Purging configuration files for xorg-driver-fglrx ...
Processing triggers for man-db ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place

rafael@Inspiron:~$ 

*and then* 
sudo dpkg-reconfigure -phigh xserver-xorg

xserver-xorg postinst warning: overwriting possibly-customised configuration
   file; backup in /etc/X11/xorg.conf.20081227134833

rafael@Inspiron:~$ 

<<<<<<<<<<<<<<>>>>>>>>>>>>>>>>


*Should I follow through with the* 
**apt-get autoremove**
*Command?*

---

### Post by w4ett on 2008-12-27
> Should I follow through with the
apt-get autoremove
Command?

Yes...this will remove the orphan packages which are not required.

---

### Post by mayagrafix on 2008-12-27
Great! everything seems to be working fine, so I will mark the post Solved and proceed to reboot. Thanks a lot for all your kind help and Happy Holidays :)

---

