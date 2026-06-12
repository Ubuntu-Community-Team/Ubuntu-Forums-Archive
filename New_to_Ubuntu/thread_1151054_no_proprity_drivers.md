---
title: "no proprity drivers"
date: 2009-05-06
forum: New to Ubuntu
---

### Post by davellew69 on 2009-05-06
basicly my machine say there are none, are there any downloads too help?

---

### Post by davellew69 on 2009-05-06
sorry i used the wrong prefix...it is ubuntu

---

### Post by halitech on 2009-05-06
is there something not working? generally the only things that use propriatary drivers are some wireless cards and ATI/Nvidia video cards.

---

### Post by davellew69 on 2009-05-06
hi thanks for replying, basicly i can only get the basic visual effect,i trying to set up  the cube effect, but my in experience is showing through

---

### Post by halitech on 2009-05-06
do you know what video card you have?

open a terminal and post the results of```
sudo lspci
```and ```
lshw -C video
```

---

### Post by davellew69 on 2009-05-06
llewellyn@llewellyn-desktop:~$ sudo lspci
[sudo] password for llewellyn: 
00:00.0 Host bridge: Intel Corporation 82845 845 [Brookdale] Chipset Host Bridge (rev 03)
00:01.0 PCI bridge: Intel Corporation 82845 845 [Brookdale] Chipset AGP Bridge (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 12)
00:1f.0 ISA bridge: Intel Corporation 82801BA ISA Bridge (LPC) (rev 12)
00:1f.1 IDE interface: Intel Corporation 82801BA IDE U100 Controller (rev 12)
00:1f.2 USB Controller: Intel Corporation 82801BA/BAM USB Controller #1 (rev 12)
00:1f.3 SMBus: Intel Corporation 82801BA/BAM SMBus Controller (rev 12)
00:1f.4 USB Controller: Intel Corporation 82801BA/BAM USB Controller #1 (rev 12)
00:1f.5 Multimedia audio controller: Intel Corporation 82801BA/BAM AC'97 Audio Controller (rev 12)
01:00.0 VGA compatible controller: nVidia Corporation NV6 [Vanta/Vanta LT] (rev 15)
02:08.0 Ethernet controller: Intel Corporation 82801BA/BAM/CA/CAM Ethernet Controller (rev 03)

---

### Post by davellew69 on 2009-05-06
WARNING: you should run this program as super-user.
  *-display UNCLAIMED     
       description: VGA compatible controller
       product: NV6 [Vanta/Vanta LT]
       vendor: nVidia Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 15
       width: 32 bits
       clock: 66MHz
       capabilities: cap_list
       configuration: latency=40 maxlatency=1

---

### Post by davellew69 on 2009-05-06
ok does this help

---

### Post by davellew69 on 2009-05-06
is there any downloads which will help

---

### Post by mick8985 on 2009-05-06
Your card is really old, it may not be supported by proprietary drivers.

```
[COLOR="Red"]sudo apt-get install nvidia-glx-legacy[/COLOR]
```

in /etc/X11/xorg.conf change nv to nvidia and reboot

Edit -

actually make that
```
sudo apt-get install nvidia-glx-96
```

---

### Post by davellew69 on 2009-05-06
llewellyn@llewellyn-desktop:~$ sudo apt-get install nvidia-glx-legacy
[sudo] password for llewellyn: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package nvidia-glx-legacy is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  nvidia-glx-96 nvidia-glx-71 nvidia-glx-180 nvidia-glx-173
E: Package nvidia-glx-legacy has no installation candidate
llewellyn@llewellyn-desktop:~$ 


it`s not looking good

---

### Post by mick8985 on 2009-05-06
notice I updated my previous message do this instead

```
sudo apt-get install nvidia-glx-96
```

---

### Post by davellew69 on 2009-05-06
sorry I just saw it, so far so good i`ll let you know

---

### Post by davellew69 on 2009-05-06
llewellyn@llewellyn-desktop:~$ sudo apt-get install nvidia-glx-96
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  dkms fakeroot nvidia-96-kernel-source nvidia-settings patch
Suggested packages:
  diff-doc
The following NEW packages will be installed
  dkms fakeroot nvidia-96-kernel-source nvidia-glx-96 nvidia-settings patch
0 upgraded, 6 newly installed, 0 to remove and 3 not upgraded.
Need to get 7914kB of archives.
After this operation, 24.0MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get: 1 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty/main dkms 2.0.21.1-0ubuntu3 [57.6kB]
Get: 2 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty/main fakeroot 1.12.1ubuntu1 [115kB]
Get: 3 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty/restricted nvidia-96-kernel-source 96.43.10-0ubuntu1 [1847kB]
Get: 4 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty/restricted nvidia-glx-96 96.43.10-0ubuntu1 [5022kB]
Get: 5 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty/main nvidia-settings 180.25-0ubuntu1 [772kB]
Get: 6 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty/main patch 2.5.9-5 [100kB]          
Fetched 7914kB in 2min 0s (65.9kB/s)                                           
Selecting previously deselected package dkms.
(Reading database ... 142371 files and directories currently installed.)
Unpacking dkms (from .../dkms_2.0.21.1-0ubuntu3_all.deb) ...
Selecting previously deselected package fakeroot.
Unpacking fakeroot (from .../fakeroot_1.12.1ubuntu1_i386.deb) ...
Selecting previously deselected package nvidia-96-kernel-source.
Unpacking nvidia-96-kernel-source (from .../nvidia-96-kernel-source_96.43.10-0ubuntu1_i386.deb) ...
Selecting previously deselected package nvidia-glx-96.
Unpacking nvidia-glx-96 (from .../nvidia-glx-96_96.43.10-0ubuntu1_i386.deb) ...
Selecting previously deselected package nvidia-settings.
Unpacking nvidia-settings (from .../nvidia-settings_180.25-0ubuntu1_i386.deb) ...
Selecting previously deselected package patch.
Unpacking patch (from .../patch_2.5.9-5_i386.deb) ...
Processing triggers for man-db ...
Processing triggers for menu ...
Setting up dkms (2.0.21.1-0ubuntu3) ...
 * Running DKMS auto installation service for kernel 2.6.28-11-generic   [ OK ] 

Setting up fakeroot (1.12.1ubuntu1) ...

Setting up nvidia-96-kernel-source (96.43.10-0ubuntu1) ...
Removing all DKMS Modules
Done.
Adding Module to DKMS build system
driver version= 96.43.10
Doing initial module build

Installing initial module
Done.

Setting up nvidia-glx-96 (96.43.10-0ubuntu1) ...

Setting up nvidia-settings (180.25-0ubuntu1) ...

Setting up patch (2.5.9-5) ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Processing triggers for menu ...
llewellyn@llewellyn-desktop:~$ 


can I now re boot?

---

### Post by halitech on 2009-05-06
either reboot or type in startx

---

### Post by mick8985 on 2009-05-06
yeah, but first do this

```
sudo gedit /etc/X11/xorg.conf
```
look for the line that says ```
Driver "nv"
```
and change it to ```
Driver "nvidia"
```
then save and reboot, if it already says nvidia you're golden, just reboot.

---

### Post by Mortus Pryde on 2009-05-06
Okay what they said, then yes, once you get a new prompt the install is done, you can safely reboot. EI The terminal allows you to enter a new command.

Still somewhat newbie myself.

---

### Post by davellew69 on 2009-05-06
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection




hmmmmm I cant see the section I need to change

---

### Post by mick8985 on 2009-05-06
Just reboot, it's probably not necessary, Xorg doesn't need much configuration these days, that advice is probably old hat now the other posters don't seem to think it's necessary

---

### Post by davellew69 on 2009-05-06
ok i`ll give it a go

---

### Post by Mortus Pryde on 2009-05-06
If that does not work, then you may have to edit the xorg.conf file and add the Driver "nvidia" in the devices section under the identifier line.

---

### Post by davellew69 on 2009-05-06
no joy

---

### Post by davellew69 on 2009-05-06
how do i do the above?

---

### Post by mick8985 on 2009-05-06
```
Section "Device"
Identifier "Configured Video Device"
[COLOR="Blue"]Driver "nvidia"[/COLOR]
EndSection
```

Add the line here then reboot

---

### Post by davellew69 on 2009-05-06
ahhh no joy, i have noticed that that mt icon on the desk top has gone

---

### Post by mick8985 on 2009-05-06
mt icon?
How do you know it hasn't worked btw?

---

### Post by davellew69 on 2009-05-06
sorry mt icon was a mistype..i meant that all desktop icons have gone, I also tried going back into apperences and trying the visual effects, but stll cant enable desk top effects

---

### Post by mick8985 on 2009-05-06
```
lsmod |grep nvidia
```
whats the output of this?
also this
```
glxgears
```

---

### Post by davellew69 on 2009-05-06
llewellyn@llewellyn-desktop:~$ glxgears
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't get an RGB, Double-buffered visual
llewellyn@llewellyn-desktop:~$

the first command did`nt work

---

### Post by mick8985 on 2009-05-06
```
# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
EndSection

```

If the first command doesn't give an output that means that the nvidia kernel module isn't loaded, which might mean that your card is not supported by the driver. Try replacing your entire xorg.conf with this, (it's my xorg.conf). If this doesn't work we can safely assume that your card is not supported by the driver.

---

### Post by davellew69 on 2009-05-06
mate i`m off to bed, can I carry on tommorow, i have booked marked this page, may i email you, re all of the above...my email is [email]davellew69@hotmail.com....thank[/email] you for all your help so far..

dave

---

### Post by davellew69 on 2009-05-07
/home/llewellyn/Documents/Screenshot.png

---

### Post by davellew69 on 2009-05-07
any ideas what to do now

---

### Post by davellew69 on 2009-05-07
is the pic big enough

---

### Post by halitech on 2009-05-07
open a terminal and run
```
sudo nvidia-xconfig
```

---

### Post by davellew69 on 2009-05-07
tried it but all i get is command not found

---

