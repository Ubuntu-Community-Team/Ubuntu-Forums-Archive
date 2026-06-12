---
title: "installing wireless card drivers"
date: 2009-02-21
forum: New to Ubuntu
---

### Post by mick224 on 2009-02-21
I am a complete n00b when it comes to Linux and recently installed it onto a Toshiba laptop in the hope of learning more about it.
I have been trying to install the driver for my wireless pci network card and have been having some trouble.  When I try to install the .deb file that contains the driver I get the message in the terminal 
“where is the Linux source build directory that matches your running kernel?
[/lib/modules/2.6.27-7-generic/build]”
can anyone help?

Thanks in anticipation 
Mick

---

### Post by anewguy on 2009-02-21
Try opening a terminal window (applications/accessories/terminal) and typing:

sudo apt-get install build-essential <press enter>

when that has finished, go back and try your driver installation again.

Dave :)

---

### Post by mick224 on 2009-02-22
Thanks man, tryed it but i am getting the message 
"E: couldn't find the package build-essential"
any ideas?!

;)thanks

---

### Post by anewguy on 2009-02-22
Hummmm....might be the software sources are a little mixed up or out of date.  When you run synaptic package manager, or apt-get, they look at a sources.list file to find the paths and the type of archives to expect there.  When this list is incomplete, does not have the source needed enabled, etc., it can result in unfound packages.  This file is /etc/apt/sources.list  - please post the contents of that file back here so we can check it.  You can view in via the "places" explorer, or you can use a terminal window and type:

cat /etc/apt/sources.list <press enter>

Once we see that we can tell if the list is okay.  Also, be sure you spelled build-essential just as I did - any switched letters, addition of an "s" to the end, etc., will result in no match also.

Dave :)

---

### Post by mick224 on 2009-02-25
Sorry for the late reply,


michael@michael-laptop:~$ cat /etc/apt/sources.list 
#deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/ intrepid main restricted 
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to 
# newer versions of the distribution. 
 
deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/ intrepid main restricted 
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid main restricted 
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid main restricted 
 
## Major bug fix updates produced after the final release of the 
## distribution. 
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid-updates main restricted 
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid-updates main restricted 
 
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team. Also, please note that software in universe WILL NOT receive any 
## review or updates from the Ubuntu security team. 
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid universe 
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid universe 
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid-updates universe 
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid-updates universe 
 
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu 
## security team. 
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid multiverse 
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid multiverse 
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid-updates multiverse 
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid-updates multiverse 
 
## Uncomment the following two lines to add software from the 'backports' 
## repository. 
## N.B. software from this repository may not have been tested as 
## extensively as that contained in the main release, although it includes 
## newer versions of some applications which may provide useful features. 
## Also, please note that software in backports WILL NOT receive any review 
## or updates from the Ubuntu security team. 
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse 
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse 
 
## Uncomment the following two lines to add software from Canonical's 
## 'partner' repository. This software is not part of Ubuntu, but is 
## offered by Canonical and the respective vendors as a service to Ubuntu 
## users. 
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner 
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner 
 
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security main restricted 
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security main restricted 
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security universe 
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security universe 
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security multiverse 
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security multiverse

:S not realy sure what all this is!

thanks for the help! ;)

---

### Post by mick224 on 2009-02-25
I dont know if this is worth mentioning, but now when I try "sudo apt-get install build-essential"
I get the following message
"E: dkpg was interupted, you must manually run 'dpkg --configure -a' to correct the problem"
however it will not allow me to run that!
Ahh!!! 
Althought still think im better off learning linux and ditchin windows :lol:



mick :)

---

### Post by avtolle on 2009-02-25
> **mick224 said:**
> I dont know if this is worth mentioning, but now when I try "sudo apt-get install build-essential"
I get the following message
"E: dkpg was interupted, you must manually run 'dpkg --configure -a' to correct the problem"
however it will not allow me to run that!
Ahh!!! 
Althought still think im better off learning linux and ditchin windows :lol:



mick :)
Open a terminal (Applications>Accessories>Terminal) and```
sudo dpkg --configure -a
```

---

### Post by mick224 on 2009-02-25
hey thanks... i googled it just after posting the reply... should have done that first realy :( 

When i tryed that i got the following --

michael@michael-laptop:~$ sudo dpkg --configure -a 
Setting up patch (2.5.9-5) ... 
Setting up driverloader (2.26tiabocom) ... 
Linuxant DriverLoader for Wireless LAN devices, version 2.26tiabocom 
 
No pre-built modules for: Debian-lenny/sid linux-2.6.27-7-generic i686-SMP 
 
Trying to automatically build the driver modules... 
(this requires a C compiler and proper kernel sources to be installed) 
 
Where is the linux source build directory that matches your running kernel? 
[/lib/modules/2.6.27-7-generic/build]  
 
WARNING: the kernel version () defined in 
/lib/modules/2.6.27-7-generic/build/include/linux/version.h 
does not match the currently running kernel (2.6.27-7-generic) 
The cause of this problem is an incorrect kernel source path. 
Please check that /lib/modules/2.6.27-7-generic/build points to the right tree. 
The cause of this is usually a missing or unconfigured 
kernel source tree (and sometimes an incorrect directory or symbolic link). 
 
However, proper /boot/config-2.6.27-7-generic was found. 
Would you like to try using it (in a temporary kernel tree)? [yes] yes 
 
Unable to prepare temporary kernel tree 
 
First, ensure that the proper kernel source and compiler packages 
from your distribution vendor and/or the community are installed. 
 
The Linux kernel can then be reconfigured by running "make menuconfig" 
under the kernel source directory (usually /usr/src/linux). 
 
Verify that the proper options for your system are selected. 
 
Then compile and install your new kernel (for more information about 
this procedure, see the README file under the kernel source directory), 
reboot the system using the new kernel, and re-run "dldrconfig". 
dpkg: error processing driverloader (--configure): 
 subprocess post-installation script returned error exit status 1 
Setting up dpkg-dev (1.14.20ubuntu6) ... 
Setting up libstdc++6-4.3-dev (4.3.2-1ubuntu11) ... 
Setting up g++-4.3 (4.3.2-1ubuntu11) ... 
Setting up g++ (4:4.3.1-1ubuntu2) ... 
 
Setting up build-essential (11.4) ... 
Errors were encountered while processing: 
 driverloader 

any ideas?

mick:)

---

### Post by llamabr on 2009-02-25
It's unlikely that you need to install any drivers.

What's wrong with the wireless card.  And what kind is it?  What kind of network are you trying to connect to?  And what kind of encryption?

Also, tell us the output of lspci

---

### Post by mick224 on 2009-02-25
> 

Where is the linux source build directory that matches your running kernel? 
[/lib/modules/2.6.27-7-generic/build]  
 


(at this point i pushed enter)

---

### Post by mick224 on 2009-02-25
Its a wireless pci card made by Safecom/Texas Instruments, but i think it is working fine as it works in another laptop running windows :S

I am trying to connect to the wireless network in my house, i has 2 computers(both windows) conected justnow via wireless and one (again windows) conected via cable

It is encrypted using a WEP key

the output of lspci is ---

00:00.0 Host bridge: Intel Corporation 82845 845 [Brookdale] Chipset Host Bridge (rev 05) 
00:01.0 PCI bridge: Intel Corporation 82845 845 [Brookdale] Chipset AGP Bridge (rev 05) 
00:1d.0 USB Controller: Intel Corporation 82801CA/CAM USB Controller #1 (rev 02) 
00:1d.1 USB Controller: Intel Corporation 82801CA/CAM USB Controller #2 (rev 02) 
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 42) 
00:1f.0 ISA bridge: Intel Corporation 82801CAM ISA Bridge (LPC) (rev 02) 
00:1f.1 IDE interface: Intel Corporation 82801CAM IDE U100 Controller (rev 02) 
00:1f.3 SMBus: Intel Corporation 82801CA/CAM SMBus Controller (rev 02) 
00:1f.5 Multimedia audio controller: Intel Corporation 82801CA/CAM AC'97 Audio Controller (rev 02) 
00:1f.6 Modem: Intel Corporation 82801CA/CAM AC'97 Modem Controller (rev 02) 
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility M6 LY 
02:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10) 
02:04.0 CardBus bridge: O2 Micro, Inc. OZ6933/711E1 CardBus/SmartCardBus Controller (rev 01) 
02:04.1 CardBus bridge: O2 Micro, Inc. OZ6933/711E1 CardBus/SmartCardBus Controller (rev 01) 
03:00.0 Network controller: Texas Instruments ACX 111 54Mbps Wireless Interface

mick :)

---

### Post by llamabr on 2009-02-25
And what happens when you click those little computers on the upper right in the task bar?  You can see your network?  And what happens when you click on your network?

---

### Post by mick224 on 2009-02-25
up at the right there is a monitor icon, when i click on it there is the heading wireless Networks with nothing below it and wired netowrk with auto eth0 below it, however it is greyed out :S

---

### Post by mick224 on 2009-02-25
Managed to get it working :D
thanks everyone for your help :)
:D:D:D:D

mick :D

---

### Post by llamabr on 2009-02-25
What did you do?  Fill us in, for the archives, and also change your subject to solved

---

### Post by mick224 on 2009-02-25
didnt realy do to much :( but hey it works :)
I put the ubuntu cd into the drive and ran a live version of it, with my wireless plugged in..... and hey it worked fine :s no need to mess around with drivers :s
I then went onto reinstall ubuntu, with the wireless network card plugged in and again when the system had installed and loaded up it was working fine :s without having to install any drivers :)

thanks for the help man ;)
mick :)

p.s how do you mark a problem as solved :s

---

