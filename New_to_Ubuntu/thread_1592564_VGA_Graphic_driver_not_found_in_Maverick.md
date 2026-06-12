---
title: "VGA Graphic driver not found in Maverick"
date: 2010-10-10
forum: New to Ubuntu
---

### Post by DayLite on 2010-10-10
I just installed Ubuntu 10.10 on a laptop Latitude D600 computer. I had complete desktop effects before install from 10.04. Now it says I cannot use special effects no driver found :confused:

My graphic card is a VGA compatible controller.

Any suggestions? Anybody else having  the same problem?

---

### Post by davidmohammed on 2010-10-10
... bit more detail needed.

please run

lspci | grep VGA

from a terminal session - copy and paste the output here.

---

### Post by DayLite on 2010-10-10
> **davidmohammed said:**
> ... bit more detail needed.

please run

lspci | grep VGA

from a terminal session - copy and paste the output here.

This is the information:

> joan@joan-laptop:~$ lspci | grep VGA
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon RV250 [Mobility FireGL 9000] (rev 02)
joan@joan-laptop:~$ 


---

### Post by themusicalduck on 2010-10-10
Try going to System > Administration > Additional Drivers to see if you can install a driver from there.

---

### Post by DayLite on 2010-10-10
> **themusicalduck said:**
> Try going to System > Administration > Additional Drivers to see if you can install a driver from there.

I already tried that. No drivers found.

---

### Post by andrewthomas on 2010-10-10
Did you ever have fglrx installed?
 
Have you purged it?
 
It seems to me that the standard radeon driver should work just fine for you.

---

### Post by DayLite on 2010-10-10
> **andrewthomas said:**
> Did you ever have fglrx installed?
 
Have you purged it?
 
It seems to me that the standard radeon driver should work just fine for you.

When I was installing Maverick, a lot came up that asked if I wanted to 'get rid of'....
I didn't understand what they were and click yes, so only Maverick was installed.

What is "fglrx" and how do I get it back?

---

### Post by cgroza on 2010-10-10
Same here but with Nvidia. [http://ubuntuforums.org/showthread.php?t=1592594](http://ubuntuforums.org/showthread.php?t=1592594)

---

### Post by andrewthomas on 2010-10-10
> **DayLite said:**
> When I was installing Maverick, a lot came up that asked if I wanted to 'get rid of'....
I didn't understand what they were and click yes, so only Maverick was installed.
 
What is "fglrx" and how do I get it back?
 It is the driver that themusicalduck was referring to.
 
> **themusicalduck said:**
> Try going to System > Administration > Additional Drivers to see if you can install a driver from there.
 
I would first try and find out why your card is not working with the standard driver.

---

### Post by DayLite on 2010-10-10
> **andrewthomas said:**
> I would first try and find out why your card is not working with the standard driver.

**Ok. . .cool How do I troubleshoot** :confused: 

The only driver available is:
**Broadcom B43 wireless driver**

> This package installs the firmware needed for usage of the b43 kerneldriver.

Supported chipsets:- BCM4306/3- BCM4311- BCM4312- BCM4318My wireless is working fine, so I don't know why I should install it. That is the only driver that showed up in the search.

---

### Post by andrewthomas on 2010-10-10
I would try 
 
```
 sudo aptitude purge fglrx
```
```
sudo rm /etc/X11/xorg.conf
```
then reboot and try again to check in additional drivers

---

### Post by DayLite on 2010-10-10
> **andrewthomas said:**
> I would try 
 
```
 sudo aptitude purge fglrx
``````
sudo rm /etc/X11/xorg.conf
```then reboot and try again to check in additional drivers

I am uncomfortable using the terminal, If I do this wrong will my monitor screen suddenly become black and will I be left with no graphic display?

---

### Post by DayLite on 2010-10-10
Followed your instructions and this is what was in my terminal:
```
joan@joan-laptop:~$ sudo aptitude purge fglrx
[sudo] password for joan: 
The following packages will be REMOVED:  
  apport-hooks-medibuntu{u} cairo-dock-plug-ins{u} 
  cairo-dock-plug-ins-data{u} cairo-dock-plug-ins-integration{u} kdesudo{u} 
  libavutil-extra-49{u} libdb4.7{u} libetpan13{u} libxdo2{u} 
  update-manager-kde{u} xdotool{u} 
0 packages upgraded, 0 newly installed, 11 to remove and 2 not upgraded.
Need to get 0B of archives. After unpacking 13.5MB will be freed.
Do you want to continue? [Y/n/?] y
(Reading database ... 169279 files and directories currently installed.)
Removing apport-hooks-medibuntu ...
Removing cairo-dock-plug-ins ...
Removing cairo-dock-plug-ins-integration ...
Removing cairo-dock-plug-ins-data ...
Removing update-manager-kde ...
Removing kdesudo ...
update-alternatives: using /usr/lib/kde4/libexec/kdesu-distrib/kdesu to provide /usr/lib/kde4/libexec/kdesu (kdesu) in auto mode.
Removing libavutil-extra-49 ...
Removing libdb4.7 ...
Removing libetpan13 ...
Removing xdotool ...
Removing libxdo2 ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Processing triggers for man-db ...
                                         
joan@joan-laptop:~$ sudo rm /etc/X11/xorg.conf
rm: cannot remove `/etc/X11/xorg.conf': No such file or directory
joan@joan-laptop:~$ 

```

---

### Post by andrewthomas on 2010-10-10
Did you reboot and see if the standard driver now works?

---

### Post by DayLite on 2010-10-10
> **andrewthomas said:**
> Did you reboot and see if the standard driver now works?

Yes, I did reboot, not working. I went to appearances, and tried to get visual display and it searched for a driver, none found. I went to find a driver, none.

What I copied to the terminal did mess me up :confused: It removed my Cairo- Dock plug-ins.  When I rebooted a pop up window said I had no plug-ins and there was no use to keep Cairo- Dock and it closed the Dock.  I then went to the Synaptic  Package Manager and reinstalled the plug-ins.

So now I have a Graphic Card that I can't use any more in Maverick:confused: to give me special effects. In Ubuntu 10.04 I had Compiz effects like the cube and wavy windows.  Somebody please figure this out or help me get back to Ubuntu 10.04. It is more stable.

Now when I use the top panel menu it doesn't go away and also has a transparent additional window that won't disappear and block me for seeing anything I try to launch, so I have to shut down the computer and reboot to get it to go away.[SIZE=4]** HELP**[/SIZE]

---

### Post by andrewthomas on 2010-10-10
Try to reinstall the fglrx driver.  Make sure that you have the restricted (non-free) repos activated in software center.
 
```
 
sudo apt-get install fglrx

```
 
 
[http://packages.ubuntu.com/maverick/fglrx](http://packages.ubuntu.com/maverick/fglrx)
 
The cairo packages should not depend on fglrx. I have no idea why they were removed.  To show the dependencies of a package you can use aptitude
 
```
aptitude show fglrx
```

---

### Post by DayLite on 2010-10-10
```
joan@joan-laptop:~$ sudo apt-get install fglrx
[sudo] password for joan: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  dkms fakeroot fglrx-amdcccle patch
Suggested packages:
  diffutils-doc
The following NEW packages will be installed:
  dkms fakeroot fglrx fglrx-amdcccle patch
0 upgraded, 5 newly installed, 0 to remove and 2 not upgraded.
Need to get 25.4MB of archives.
After this operation, 76.3MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://us.archive.ubuntu.com/ubuntu/ maverick/main dkms all 2.1.1.2-3ubuntu1 [71.1kB]
Get:2 http://us.archive.ubuntu.com/ubuntu/ maverick/main fakeroot i386 1.14.4-1ubuntu1 [118kB]
Get:3 http://us.archive.ubuntu.com/ubuntu/ maverick/restricted fglrx i386 2:8.780-0ubuntu2 [19.9MB]
Get:4 http://us.archive.ubuntu.com/ubuntu/ maverick/restricted fglrx-amdcccle i386 2:8.780-0ubuntu2 [5,177kB]
Get:5 http://us.archive.ubuntu.com/ubuntu/ maverick/main patch i386 2.6-2ubuntu1 [123kB]
Fetched 25.4MB in 34s (729kB/s)                                                
Selecting previously deselected package dkms.
(Reading database ... 169231 files and directories currently installed.)
Unpacking dkms (from .../dkms_2.1.1.2-3ubuntu1_all.deb) ...
Selecting previously deselected package fakeroot.
Unpacking fakeroot (from .../fakeroot_1.14.4-1ubuntu1_i386.deb) ...
Selecting previously deselected package fglrx.
Unpacking fglrx (from .../fglrx_2%3a8.780-0ubuntu2_i386.deb) ...
Selecting previously deselected package fglrx-amdcccle.
Unpacking fglrx-amdcccle (from .../fglrx-amdcccle_2%3a8.780-0ubuntu2_i386.deb) ...
Selecting previously deselected package patch.
Unpacking patch (from .../patch_2.6-2ubuntu1_i386.deb) ...
Processing triggers for man-db ...
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Setting up dkms (2.1.1.2-3ubuntu1) ...
Setting up fakeroot (1.14.4-1ubuntu1) ...
update-alternatives: using /usr/bin/fakeroot-sysv to provide /usr/bin/fakeroot (fakeroot) in auto mode.
Setting up fglrx (2:8.780-0ubuntu2) ...
update-alternatives: using /usr/lib/fglrx/ld.so.conf to provide /etc/ld.so.conf.d/GL.conf (gl_conf) in auto mode.
update-alternatives: warning: skip creation of /usr/lib32/libaticalcl.so because associated file /usr/lib32/fglrx/libaticalcl.so (of link group gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/lib32/libaticalrt.so because associated file /usr/lib32/fglrx/libaticalrt.so (of link group gl_conf) doesn't exist.
update-initramfs: deferring update (trigger activated)
Loading new fglrx-8.780 DKMS files...
First Installation: checking all kernels...
Building only for 2.6.35-22-generic
Building for architecture i686
Building initial module for 2.6.35-22-generic
Done.

fglrx.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/2.6.35-22-generic/updates/dkms/

depmod................

DKMS: install Completed.
update-initramfs: deferring update (trigger activated)
Setting up patch (2.6-2ubuntu1) ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Setting up fglrx-amdcccle (2:8.780-0ubuntu2) ...
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.35-22-generic
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Processing triggers for python-support ...
joan@joan-laptop:~$ 

```

Ok, I rebooted.  **No change**. Before I rebooted I copied the above that was in my terminal after I followed your advice. I am extremely frustrated. I don't know what I have done. Hopefully someone on this forum will read what action was taken by what information is found on the terminal.

I do have a problem with drop down menu's freezing, not going away and blocking every window I open.  This is making me miserable. I am so thankful that on my desktop I still have Ubuntu 10.04.

---

### Post by andrewthomas on 2010-10-10
Looks like it installed alright.  I would reboot and see if you have compiz back.

---

### Post by DayLite on 2010-10-10
> **andrewthomas said:**
> Try to reinstall the fglrx driver.  Make sure that you have the restricted (non-free) repos activated in software center.
 
```
 
sudo apt-get install fglrx

``` 
[http://packages.ubuntu.com/maverick/fglrx](http://packages.ubuntu.com/maverick/fglrx)
 
The cairo packages should not depend on fglrx. I have no idea why they were removed.  To show the dependencies of a package you can use aptitude
 
```
aptitude show fglrx
```

I followed what you told me to put in the terminal and I posted the response, it did say it removed Cairo. I don't understand the words in the terminal, hopefully you do.

---

### Post by DayLite on 2010-10-10
> **andrewthomas said:**
> Looks like it installed alright.  I would reboot and see if you have compiz back.

Nothing changed.

---

### Post by andrewthomas on 2010-10-10
```
 
sudo apt-get update && sudo apt-get install cairo-dock

```
 
Then you could reinstall the other packages that got removed
 
```
 
sudo apt-get install kdesudo libavutil-extra-49 update-manager-kde xdotool

```
 
Then logout and back in and check your compiz.

---

### Post by DayLite on 2010-10-10
> **andrewthomas said:**
> ```
 
sudo apt-get update && sudo apt-get install cairo-dock

```Then you could reinstall the other packages that got removed
 
```
 
sudo apt-get install kdesudo libavutil-extra-49 update-manager-kde xdotool

```Then logout and back in and check your compiz.

What do you mean? I have cairo- dock, I installed the missing plug-ins in the Synaptic Manager. I do have the compiz manager but nothing I check works.  Problem with absent graphic driver. My laptop came with a **VGA Compatible Controller Graphic Card **and it worked giving me visual effects before my upgrade. So nothing I check in Compiz matters it won't work.

---

### Post by andrewthomas on 2010-10-10
This post has a step by step instruction set.
 
[http://ubuntuforums.org/showpost.php?p=9950524&postcount=6](http://ubuntuforums.org/showpost.php?p=9950524&postcount=6)
 
 
You probably need to do this before rebooting
 
```
 
sudo aticonfig --initial -f

```

---

### Post by DayLite on 2010-10-10
> **andrewthomas said:**
> This post has a step by step instruction set.
 
[http://ubuntuforums.org/showpost.php?p=9950524&postcount=6](http://ubuntuforums.org/showpost.php?p=9950524&postcount=6)
 
 
You probably need to do this before rebooting
 
```
 
sudo aticonfig --initial -f

```

This is what is in my terminal.

> joan@joan-laptop:~$ sudo aticonfig --initial -f
[sudo] password for joan: 
aticonfig: No supported adapters detected
joan@joan-laptop:~$ 


---

### Post by andrewthomas on 2010-10-10
Can you run compiz from a liveCD?
 
I am just about out of ideas here.

---

### Post by DayLite on 2010-10-11
I typed this into the terminal:
> Check first your graphic card name and chipset: 

lspci -nn | grep VGA
This is what came up;

> joan@joan-laptop:~$ lspci -nn | grep VGA
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc Radeon RV250 [Mobility FireGL 9000] [1002:4c66] (rev 02)
joan@joan-laptop:~$ 


I got that from this link:[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

> **Will It Work On Your Card?**

 Check first your graphic card name and chipset: 

lspci -nn | grep VGAIt should report something like this for your graphics card: 

01:00.0 VGA compatible controller: ATI Technologies Inc RV350 AS [Radeon 9550] 
**Unsupported**

 You are currently not able to use the "radeon" driver for the following cards and derivatives: 

None known.

---

### Post by DayLite on 2010-10-11
>  p, li { white-space: pre-wrap; } There was a problem initializing Catalyst Control Center Linux edition.  It could be caused by the following.
  No ATI graphics driver is installed, or the ATI driver is not functioning properly.
 Please install the ATI driver appropriate for you ATI hardware, or configure using aticonfig.
 

Tell me what to type in the terminal that will configure the ATI driver that I need.  How do I use 'aticonfig' ?

---

### Post by rburkartjo on 2010-10-11
note glad i am not losing my mind this also happened to me 
here is a thread i started

[http://ubuntuforums.org/showthread.php?t=1592418](http://ubuntuforums.org/showthread.php?t=1592418)

---

### Post by Tumpster on 2010-10-12
This is what I get:

craig@craig-MS-7612:~$ lspci -nn | grep VGA
04:00.0 VGA compatible controller [0300]: nVidia Corporation G92 [GeForce 9800 GTX+] [10de:0613] (rev a2)
craig@craig-MS-7612:~$ 


Still no working COmpiz

---

