---
title: "Trouble installing driver (worst instructions ever)"
date: 2011-08-26
forum: New to Ubuntu
---

### Post by KamrynB on 2011-08-26
Hello all and thank you for reading.

I am an Ubuntu neophyte who is going through hell reinstalling the drivers for eth0 that I accidentally deleted. I have an HP Mini 1000. After some googling I landed at the Marvell site to download my driver, here:

[http://www.marvell.com/drivers/driverDisplay.do?driverId=204](http://www.marvell.com/drivers/driverDisplay.do?driverId=204)

I admit I am coming from Windows and I expected it to be as simple as click, run, boom. WRONG. 

That's ok though, I am using learning Ubuntu for networking reasons so I saw this as an opportunity to learn. I opened the .bz2 and the readme file and followed the instructions word for word, and am now stumbled at the part where I have to type "./install.sh" in the terminal. I get a syntax error "expected ")".  

I've attached the screenshot and the readme file of the instructions. Please explain what I am typing wrong?

Thank you!!

---

### Post by gnometorule on 2011-08-26
You typed 'cd driverinstall', but you never actually changed to the 'driverinstall' directory. There is either a typo in the name of your directory, or you were not in the directory in which it is included. Before i'd try anything else, switch properly into the directory you apparently need to be in (driverinstall, using cd with the right path which I don't know - if this is all new, easy to do and read up on), then type again the install command you say you need to enter, w/o any path first (just the "./xxx' part).

---

### Post by KamrynB on 2011-08-26
> **gnometorule said:**
> You typed 'cd driverinstall', but you never actually changed to the 'driverinstall' directory. There is either a typo in the name of your directory, or you were not in the directory in which it is included. Before i'd try anything else, switch properly into the directory you apparently need to be in (driverinstall, using cd with the right path which I don't know - if this is all new, easy to do and read up on), then type again the install command you say you need to enter, w/o any path first (just the "./xxx' part).

Thank you for replying!

The cd command seems to work fine. I typed in the entire path: cd /home/kamryn/DriverInstall.

When I follow with ./install.sh I get the same error. I don't understand what I'm doing wrong. I have tried doing it with sudo, without the .sh extension, and more but nothing works.

---

### Post by coffeecat on 2011-08-26
> **KamrynB said:**
> I am an Ubuntu neophyte who is going through hell reinstalling the drivers for eth0 that I accidentally deleted.

Whoa! Hang on right there. :) You are thinking in Windows ways.

The ethernet drivers are kernel modules and you would have to know your way around the filesystem to be able to delete them. I think you may have done something else to disable the driver for your ethernet device. First thing: tell us exactly what you did to make you think that you had deleted the driver.

Next - those instructions are for re-compiling the kernel. Please believe me - you do not want to be doing that! Not as a neophyte. If you have somehow lost the file which represents the kernel module, it should be quite easy to reinstate it. Re-installing the kernel should do it. Or if you have done something else, we should be able to tell you what to do depending on the answer to my question above. 

Lastly - a bit more information please. Open a terminal and post the output of these two commands:

```
lspci | grep -i ethernet
uname -a
```

**EDIT**: I just noticed another detail in the Marvell link you posted. That file is for the 2.4 version of the kernel - the 2.4 kernel is older than Methuselah. Discard what you have downloaded; it is useless. From your screenshot you look to be running Ubuntu 11.04 which uses the 2.6.38 kernel. You need to start over. Post the information I requested and we can take it from there.

---

### Post by anewguy on 2011-08-26
gnometorule:  The screen shot I looked at looks like they are in the correct folder.  It looks to me like it's indicating an error on line 44 of the install.sh script.  As coffeecat has pointed out, all of these problems are probably due to trying to install an old version.

=====================================
Also, a note to all newbies:  As coffeecat mentioned, the last thing you should be trying to do is recompile the kernel.  If you see instructions saying you must do this, post in this forum and wait before ever doing so - you probably really don't need to do all of that.

The same holds true for such things as ndiswrapper, network manager, etc..  There are a LOT of very outdated tutorials and posts out there - always check the version of Ubuntu that the instructions are talking about - if not your version, again post here and don't do anything until someone replies.

So, if  you come across a readme, tutorial, thread, etc., that says to compile something, please post here first so we can determine if that's what you really need to do as things change quickly and there may be a much more easier way to do it now.

It is much, much easier to try to help you from scratch than to try to figure out what really happened with what you did and then how to undo all of it.
=====================================


Dave ;)

---

### Post by KamrynB on 2011-08-27
> **coffeecat said:**
> Whoa! Hang on right there. :) You are thinking in Windows ways.

I know, sorry!
 
> First thing: tell us exactly what you did to make you think that you had deleted the driver. I'm not even sure anymore; something tells me it wasn't my fault. I reinstalled Ubuntu Natty and after the first bootup I was showing 3 network intefaces; lo, eth0 and wlan0. I ran some recommended updates, rebooted my netbook and now I am showing only two; lo and eth0. However, the eth0 it is displaying is really wlan0. I am stumped as to how this happened.

>  Next - those instructions are for re-compiling the kernel. Please believe me - you do not want to be doing that! Not as a neophyte. If you have somehow lost the file which represents the kernel module, it should be quite easy to reinstate it. Re-installing the kernel should do it. Or if you have done something else, we should be able to tell you what to do depending on the answer to my question above. See above

> Lastly - a bit more information please. Open a terminal and post the output of these two commands:

```
lspci | grep -i ethernet
uname -a
```Please see attached screenshot. I also did "lspci" by itself and I found it odd I could find my Broadcom (wifi) but not the Marvell Yukon (ethernet port)

> Discard what you have downloaded; it is useless. Done, thank you for the heads up.

---

### Post by KamrynB on 2011-08-27
> **anewguy said:**
> gnometorule:  The screen shot I looked at looks like they are in the correct folder.  It looks to me like it's indicating an error on line 44 of the install.sh script.  As coffeecat has pointed out, all of these problems are probably due to trying to install an old version.

Noted, I have discarded that download.

>  Also, a note to all newbies:  As coffeecat mentioned, the last thing you should be trying to do is recompile the kernel.  If you see instructions saying you must do this, post in this forum and wait before ever doing so - you probably really don't need to do all of that.

The same holds true for such things as ndiswrapper, network manager, etc..  There are a LOT of very outdated tutorials and posts out there - always check the version of Ubuntu that the instructions are talking about - if not your version, again post here and don't do anything until someone replies.

So, if  you come across a readme, tutorial, thread, etc., that says to compile something, please post here first so we can determine if that's what you really need to do as things change quickly and there may be a much more easier way to do it now.

It is much, much easier to try to help you from scratch than to try to figure out what really happened with what you did and then how to undo all of it.
 

Will do!

---

### Post by coffeecat on 2011-08-27
OK, let's do some more investigating. Your ethernet card has disappeared from the output of lspci which is worrying as it could suggest a problem at the hardware level. Thanks for posting the full output of lspci, by the way. It served as a useful check against the null output for "lspci | grep -i ethernet" which outputs one line only, the one with "ethernet" or "Ethernet" in it if present.

Before I ask for more output, a tip for posting output which is easier to do and easier to read for those helping you. Run the terminal command and then highlight the output you want to post. Right-click on the highlighted area and choose "copy" which copies it into the clipboard. Now paste it into your post, but enclose it between code tags like this:

[noparse]```
your
terminal
output
```[/noparse]

Which will come out looking like this:

```
your
terminal
output
```

There's a clickable icon in the forum message toolbar - [img]http://ubuntuforums.org/images/editor/code.gif[/img] - which you can use to add the code tags if you wish.

Anyway - to business. It's odd that wlan0 should become eth0. Post the output of these two commands:

```
ifconfig
cat /etc/udev/rules.d/70-persistent-net.rules
```

Next - boot up with your live CD or live USB. Instead of starting the installer, choose "try Ubuntu". When you get to the desktop, open a terminal and run:

```
lspci | grep -i ethernet
```

Do you get any output? Run vanilla lspci as well if you like as a check. If the live session does not see the ethernet card, then you'll have to assume there's a hardware problem.

Last thought - for now. Look in the BIOS and see if ethernet has been disabled there. I don't know of a BIOS where it is possible to disable ethernet, but it is worth looking.

**EDIT**: I have a HP Mini 110-3100 and I can see nothing in the BIOS that would allow the switching of the ethernet card, but check anyway.

Also - one curious thing. On my HP Mini the ethernet card comes out as eth0, but the wireless card as eth1, not wlan0 as yours did originally.

---

### Post by KamrynB on 2011-08-27
> **coffeecat said:**
> way - to business. It's odd that wlan0 should become eth0. Post the output of these two commands:

```
ifconfig
cat /etc/udev/rules.d/70-persistent-net.rules
```

```

kamryn@Genesis01:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:24:2c:0b:4f:fe  
          inet addr:192.168.1.105  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::224:2cff:fe0b:4ffe/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2239 errors:0 dropped:0 overruns:0 frame:264
          TX packets:1640 errors:17 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2116530 (2.1 MB)  TX bytes:228780 (228.7 KB)
          Interrupt:16 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)

kamryn@Genesis01:~$ cat /etc/udev/rules.d/70-persistent-net.rules
# This file maintains persistent names for network interfaces.
# See udev(7) for syntax.
#
# Entries are automatically added by the 75-persistent-net-generator.rules
# file; however you are also free to add your own entries.

# PCI device 0x14e4:0x4315 (b43-pci-bridge)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:24:2c:0b:4f:fe", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

# PCI device 0x14e4:0x4315 (wl)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:24:2c:0b:4f:fe", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x11ab:0x4354 (sky2)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:24:81:5a:29:1b", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"
kamryn@Genesis01:~$ 

```> 
Next - boot up with your live CD or live USB. Instead of starting the installer, choose "try Ubuntu". When you get to the desktop, open a terminal and run:

```
lspci | grep -i ethernet
```Do you get any output? Run vanilla lspci as well if you like as a check. If the live session does not see the ethernet card, then you'll have to assume there's a hardware problem.

Last thought - for now. Look in the BIOS and see if ethernet has been disabled there. I don't know of a BIOS where it is possible to disable ethernet, but it is worth looking.
Will follow up in another post when I find my pendrive

> 
Also - one curious thing. On my HP Mini the ethernet card comes out as eth0, but the wireless card as eth1, not wlan0 as yours did originally.I could be wrong; it might have been eth0. But I know for a fact I had eth1 as the ethernet port because I was using the jack, not the wifi, to download the updates during the Ubuntu installation.

Thanks for your prompt feedback, by the way.

---

### Post by coffeecat on 2011-08-27
> **KamrynB said:**
> I could be wrong; it might have been eth0. But I know for a fact I had eth1 as the ethernet port because I was using the jack, not the wifi, to download the updates during the Ubuntu installation.

No, you're right because there is something very curious in your /etc/udev/rules.d/70-persistent-net.rules file.

There are two entries for the device with the hardware address (MAC) "00:24:2c:0b:4f:fe", one of which has been designated wlan0, the other eth0. This is the same MAC as ifconfig reports for eth0, which must be the wireless device. There is also in /etc/udev/rules.d/70-persistent-net.rules file and entry for eth1 with the MAC "00:24:81:5a:29:1b", and my guess is that this is the disappeared ethernet card. Entries are not deleted from 70-persistent-net.rules which is why I suggested posting it. If you add another network device, the system simply adds another entry. I once tried about 8 different wireless devices with a system (don't ask!) and got wlan0 through to wlan7.

But what is puzzling me at the moment is that the eth1 entry comes last which means it would have been written after wlan0 and eth0.

I'll have a ponder and come back to this when you've tried running the live session from the pendrive.

---

### Post by KamrynB on 2011-08-27
> Next - boot up with your live CD or live USB. Instead of starting the installer, choose "try Ubuntu". When you get to the desktop, open a terminal and run:

```
lspci | grep -i ethernet
```Do you get any output? Run vanilla lspci as well if you like as a check. If the live session does not see the ethernet card, then you'll have to assume there's a hardware problem.```

                                 To run a command as administrator (user "root"), use "sudo <command>".  
 See "man sudo_root" for details.  
 

 ubuntu@ubuntu:~$ lspci | grep -i ethernet  
 ubuntu@ubuntu:~$ lspci  
 00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03)  
 00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)  
 00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)  
 00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)  
 00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)  
 00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)  
 00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 02)  
 00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)  
 00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)  
 00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)  
 00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)  
 00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)  
 00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)  
 00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)  
 00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)  
 01:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g LP-PHY (rev 01)  
 ubuntu@ubuntu:~$  
 
```> 
Last thought - for now. Look in the BIOS and see if ethernet has been disabled there. I don't know of a BIOS where it is possible to disable ethernet, but it is worth looking.The BIOS shows my Yukon ethernet card as a Network Boot device; as for checking if the device is disabled or not, I was not able to pull that up.

> 
Also - one curious thing. On my HP Mini the ethernet card comes out as eth0, but the wireless card as eth1, not wlan0 as yours did originally.I did an "ifconfig -a" on the live boot and it showed my wireless card as wlan0.

---

### Post by coffeecat on 2011-08-27
Hmmm. That doesn't look good - the live session doesn't see the ethernet card either. I think a hardware fault is more likely to be the answer. Do you still have Windows on the machine? If you do, boot into Windows and see if that can see the ethernet device.

> **KamrynB said:**
> I did an "ifconfig -a" on the live boot and it showed my wireless card as wlan0.

Don't worry about my HP Mini seeing the wireless device as eth1 - that's a bit of a red-herring. A bit odd too. Wireless devices are usually (but not always) designated as wlan*, and I don't know what the rules are for designating them eth*.

In your first post you were looking on the Marvell site for a driver, so I guess the ethernet device is a Marvell chipset. Co-incidentally, I came across another another thread here today where someone claimed that Marvell ethernet cards were sometimes prone to "going to sleep". I don't know whether there is anything in that, and how you would wake it up again.

---

### Post by KamrynB on 2011-08-27
> **coffeecat said:**
> No, you're right because there is something very curious in your /etc/udev/rules.d/70-persistent-net.rules file.

There are two entries for the device with the hardware address (MAC) "00:24:2c:0b:4f:fe", one of which has been designated wlan0, the other eth0. This is the same MAC as ifconfig reports for eth0, which must be the wireless device. There is also in /etc/udev/rules.d/70-persistent-net.rules file and entry for eth1 with the MAC "00:24:81:5a:29:1b", and my guess is that this is the disappeared ethernet card. Entries are not deleted from 70-persistent-net.rules which is why I suggested posting it. If you add another network device, the system simply adds another entry. I once tried about 8 different wireless devices with a system (don't ask!) and got wlan0 through to wlan7.

But what is puzzling me at the moment is that the eth1 entry comes last which means it would have been written after wlan0 and eth0.

I'll have a ponder and come back to this when you've tried running the live session from the pendrive.

Is there any way  to edit this rules file then? Perhaps I can use root privileges to remove the eth0 entry for my wireless card (and preserving the wlan0 entry). Then I can just change eth1 to eth0?

> Do you still have Windows on the machine? If you do, boot into Windows and see if that can see the ethernet device.This machine came with HP's custom Linux OS, which I wiped off completely and replaces with Ubuntu. The 16gb SSD wouldn't leave much room for a dual boot even if I wanted the HP OS. 

I will search the forums for similar Yukon ethernet issues. Thanks again for your help!

---

### Post by anewguy on 2011-08-27
Hey Kerry_s -> sorry to intrude here as you are doing so much for the OP.  I've been doing some searching on the net (still have quite a bit to go ;) ) and found a few things that may be of interest.


Some of the reading I've done on the net for not just Ubuntu but for Linux in general indicates that indeed a separate driver needs to be installed for some of the Marvell ethernet adapters even into 11.04.  One suggestion that was made you might want to try:

- download and burn either the 10.04 LTS LiveCD or the 10.10 LiveCD and boot from it.  It seems that the controller is normally seen then on the LiveCD.  Of course you can use a USB flash drive also if this is what you need.  If that works, then try the 11.04 LiveCD and see if it is seen then.  This will help isolate where a problem might be being injected - in 11.04 (if not seen on the LiveCD) or in the install of 11.04.

Let us know how that test goes.


Please see this thread - it is from May of this year and using the driver download from Marvell - basically you need to sudo bash ./install.sh

[http://ubuntuforums.org/showthread.php?t=1746133]("http://ubuntuforums.org/showthread.php?t=1746133")

I'm still a little worried about everything you are supposed to do though.  I'm curious if one of the kernel modules is present but not getting loaded.

I also found this open bug report on launchpad:

[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/784934]("https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/784934")

Dave ;)

---

### Post by Mark Phelps on 2011-08-27
+1 on the Marvell drivers ...

My former PC had a Yukon internet device and I had to install the Marvell drivers to get it to work.

---

### Post by KamrynB on 2011-08-27
Thank you guys for all your feedback.

> 
Please see this thread - it is from May of this year and using the  driver download from Marvell - basically you need to sudo bash  ./install.sh

[http://ubuntuforums.org/showthread.php?t=1746133](http://ubuntuforums.org/showthread.php?t=1746133)
It looks like the user on that thread was attempting to do the exact thing I was-- only he figured out how to get around the same error I posted earlier. I think I will try that before downloading the 10.04 live usb, especially if Mark Phelps agrees that worked for him.

Will report my results soon.

---

### Post by KamrynB on 2011-08-27
This is the output after executing "sudo bash ./install.sh" as described in the other thread:

```

kamryn@Genesis01:~$ sudo tar xfvj install_v10.61.3.3.tar.bz2
[sudo] password for kamryn: 
tar (child): install_v10.61.3.3.tar.bz2: Cannot open: No such file or directory
tar (child): Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error is not recoverable: exiting now
kamryn@Genesis01:~$ bunzip2 -c install_v10.61.3.3.tar.bz2 | tar xfv
tar: Old option `f' requires an argument.
Try `tar --help' or `tar --usage' for more information.
bunzip2: Can't open input file install_v10.61.3.3.tar.bz2: No such file or directory.
kamryn@Genesis01:~$ cd DriverInstall
bash: cd: DriverInstall: No such file or directory
kamryn@Genesis01:~$ clear

kamryn@Genesis01:~$ cd DriverInstall
bash: cd: DriverInstall: No such file or directory
kamryn@Genesis01:~$ cd /home/kamryn/Downloads/DriverInstall
kamryn@Genesis01:~/Downloads/DriverInstall$ sudo bash ./install.sh







Installation script for sk98lin driver.
Version 10.61.3.3 (Jul-07-2008)
(C)Copyright 2003-2008 Marvell(R).
====================================================
Add to your trouble-report the logfile install.log
which is located in the  DriverInstall directory.
====================================================


1) installation
2) generate patch
3) exit
Choose your favorite installation method: 1

Please read this carfully!

This script will automatically compile and load the sk98lin
driver on your host system. Before performing both compilation
and loading, it is necessary to shutdown any device using the
sk98lin kernel module and to unload the old sk98lin kernel 
module. This script will do this automatically per default.
 
Please plug a card into your machine. Without a card we aren't
able to check the full driver functionality.

Do you want proceed? (y/N) y










IMPORTANT INFORMATION!

We found an alternative driver for your Marvell product on this system.
The alternative driver is _NOT_ directly supported by Marvell and does not
include all features provided by your device. If you want to use the
sk98lin driver developed by Marvell, you may choose either to deactivate
or remove the alternative driver.

[PRESS ANY KEY FOR FURTHER INSTRUCTIONS]


Do nothing:
  - The sk98lin will be installed
  NOTE: It may happen that the alternative driver will be loaded on 
  the next boot process. In this case the Marvell driver _WON'T_ be
  loaded.

Deactivate driver:
  - The alternative driver will be renamed to _skge.ko or _sky2.ko
  - All references in the /etc/modprobe.conf file will be changed to
    the sk98lin driver
  - The alternative driver will be unloaded
  - The sk98lin driver will be installed

Remove driver (recommended):
  - The alternative driver will be removed from your system
  - All references in the /etc/modprobe.conf file will be changed to
    the sk98lin driver
  - The alternative driver will be unloaded
  - The sk98lin driver will be installed


1) Do nothing
2) Deactivate diver
3) Remove driver
Action: 3

Disconnect alternative devices:  (done)                                                                            [   OK   ]
Unload alternative driver (done)                                                                                   [   OK   ]
Create tmp dir (/tmp/Sk98IFHfRPHBaENNkTFhBNlAP)                                                                    [   OK   ]
Check user id (0)                                                                                                  [   OK   ]
Check kernel version (2.6.38-11-generic)                                                                           [   OK   ]
Check kernel symbol file (/proc/kallsyms)                                                                          [   OK   ]
Check kernel type (SMP)                                                                                            [   OK   ]
Check number of CPUs (2)                                                                                           [   OK   ]
Check architecture (found)                                                                                         [   OK   ]
Set architecture (i386)                                                                                            [   OK   ]
Check compiler (/usr/bin/gcc)                                                                                      [   OK   ]
Check mcmodel flags (none)                                                                                         [   OK   ]
Check module support (/sbin/insmod)                                                                                [   OK   ]
Check make (/usr/bin/make)                                                                                         [   OK   ]
Check kernel gcc version (4.5.2) (Kernel:4.5.2 == gcc:4.5.2)                                                       [   OK   ]
Check sk98lin driver availability (not loaded)                                                                     [   OK   ]
Check kernel header files (not found)                                                                              [ failed ]
Kernel header not found. Please install the linux header files 
development package or create a symbolic link from the 
/usr/src/KERNEL_VERSION directory to linux
     Example: ln -s /usr/src/KERNEL_VERSION /usr/src/linux

Installation of package failed.
Delete temp directories (done)                                                                                     [   OK   ]
kamryn@Genesis01:~/Downloads/DriverInstall$ 

```That "failed" is worrying me but I will reboot and see if it worked.

---

### Post by KamrynB on 2011-08-27
Success! Only thing is my wireless has been renamed "eth1-eth0". Is there any way I can change it to just eth1, or preferably, wifi0?

"ifconfig -a" and "lspci" outputs are posted below.

```

kamryn@Genesis01:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:24:81:5a:29:1b  
          inet addr:192.168.1.107  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::224:81ff:fe5a:291b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:496 errors:0 dropped:0 overruns:0 frame:0
          TX packets:392 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:288166 (288.1 KB)  TX bytes:49127 (49.1 KB)
          Interrupt:17 

eth1-eth0 Link encap:Ethernet  HWaddr 00:24:2c:0b:4f:fe  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:960 (960.0 B)  TX bytes:960 (960.0 B)

kamryn@Genesis01:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
01:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g LP-PHY (rev 01)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller
kamryn@Genesis01:~$ 

```

---

### Post by coffeecat on 2011-08-27
.... edited - I'll get back to you.

**EDIT:**
[quote="KamrynB"]Only thing is my wireless has been renamed "eth1-eth0". Is there any way I can change it to just eth1, or preferably, wifi0?[/quote]

Well - "if it ain't broke, don't fix it." :) Or if you really want to change it post the output of:

```
cat /etc/udev/rules.d/70-persistent-net.rules
```

... again. It will have changed. That can be edited to tidy up network descriptions.

I'm puzzled by one thing. I had assumed the ethernet device was working when you first installed Ubuntu. Did it ever work? Before the fix you've just applied, that is.

---

### Post by anewguy on 2011-08-27
Your welcome - glad it got you far enough that the ethernet adapter is now recognized to some degree.  I'll leave now and let coffeecat finish things out with you.  But.....I don't think it will actually be working.  It looks to me like you need to install the build-essential package and the linux headers as the install failed with:

Check kernel header files (not found)                                                                              [ failed ]
Kernel header not found. Please install the linux header files 
development package or create a symbolic link from the 
/usr/src/KERNEL_VERSION directory to linux
     Example: ln -s /usr/src/KERNEL_VERSION /usr/src/linux

Installation of package failed.

However, it would be worth doing a lsmod to see if the driver got installed.


I'm also not certain how you got the folder where the install.sh was located - looks like your efforts to untar to a specific folder failed as well.

At any rate, I think you will find that the eth1-eth0 is actually the ethernet adapter, not your wireless.  Your wireless appears to be first - the addresses that start with 192.168.1.xxx are the typical addresses assigned for a lot of wireless connections by certain routers.

Dave ;)

Good luck and enjoy ubuntu!

dave ;)

---

### Post by KamrynB on 2011-08-27
Rebooted my computer and now its back to missing the ethernet interface. Wlan is eth0 again. But at least the Marvell is still listed in lspci:

```

kamryn@Genesis01:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:24:2c:0b:4f:fe  
          inet6 addr: fe80::224:2cff:fe0b:4ffe/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)

kamryn@Genesis01:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
01:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g LP-PHY (rev 01)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller
kamryn@Genesis01:~$ 

```Here is the content of my 70-persistent-net.rules 

```

# This file maintains persistent names for network interfaces.
# See udev(7) for syntax.
#
# Entries are automatically added by the 75-persistent-net-generator.rules
# file; however you are also free to add your own entries.

# PCI device 0x14e4:0x4315 (b43-pci-bridge)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:24:2c:0b:4f:fe", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

# PCI device 0x14e4:0x4315 (wl)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:24:2c:0b:4f:fe", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x11ab:0x4354 (sky2)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:24:81:5a:29:1b", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"

```

---

### Post by KamrynB on 2011-08-27
> **anewguy said:**
> I don't think it will actually be working.  It looks to me like you need to install the build-essential package and the linux headers as the install failed with:

Check kernel header files (not found)                                                                              [ failed ]
Kernel header not found. Please install the linux header files 
development package or create a symbolic link from the 
/usr/src/KERNEL_VERSION directory to linux
     Example: ln -s /usr/src/KERNEL_VERSION /usr/src/linux

Installation of package failed.

However, it would be worth doing a lsmod to see if the driver got installed.


I'm also not certain how you got the folder where the install.sh was located - looks like your efforts to untar to a specific folder failed as well.

At any rate, I think you will find that the eth1-eth0 is actually the ethernet adapter, not your wireless. 

It was working, on the first reboot after installing the driver, but now it's not! That IP address is from the ethernet interface on the netbook; I turned off wifi to test. it. However the linux kernel header issue is mentioned in the Readme file that came with the driver, and I will follow those instructions. Thank you very much for the help, anewguy and coffeecat.

---

### Post by anewguy on 2011-08-27
Jeez, stupid me!  Of COURSE that would be the IP address for your ethernet interface *IF* you had it hard wired to the router and it was working!  I don't know what the heck I was thinking!

Try:

sudo modprobe sk98lin <press enter> and see if it rejects it or if it actually loads.  If it loads, check your ethernet interface again.

BUT.......just to make sure we are dealing with everything, try:

lspci -n (This will show the numbers we can equate to the network devices)

Also:

iwconfig <press enter> if your wireless is working and connected we should see something along the lines of:

wlan0 IEEE 802.11bg  ESSID:"yourssid should show here"

Also, in the current state as the latest ifconfig shows, does your wireless work?  I ask only because I want to be sure I'm on the same page as your current status - wireless works, the ethernet adapter is recognized by ubuntu but doesn't work.

When you go back to install build-essential and the kernel headers and then run the install.sh again, if you encounter errors stop and post them back here.  I'm not sure how they are referencing the headers, so perhaps a link will need to be created.

Sorry on the mix up!

dave ;)

---

### Post by KamrynB on 2011-08-27
> **anewguy said:**
> 
lspci -n (This will show the numbers we can equate to the network devices)

Also, in the current state as the latest ifconfig shows, does your wireless work?  I ask only because I want to be sure I'm on the same page as your current status - wireless works, the ethernet adapter is recognized by ubuntu but doesn't work.


Here is the output:

```

kamryn@Genesis01:~$ lspci -n
00:00.0 0600: 8086:27ac (rev 03)
00:02.0 0300: 8086:27ae (rev 03)
00:02.1 0380: 8086:27a6 (rev 03)
00:1b.0 0403: 8086:27d8 (rev 02)
00:1c.0 0604: 8086:27d0 (rev 02)
00:1c.1 0604: 8086:27d2 (rev 02)
00:1d.0 0c03: 8086:27c8 (rev 02)
00:1d.1 0c03: 8086:27c9 (rev 02)
00:1d.2 0c03: 8086:27ca (rev 02)
00:1d.3 0c03: 8086:27cb (rev 02)
00:1d.7 0c03: 8086:27cc (rev 02)
00:1e.0 0604: 8086:2448 (rev e2)
00:1f.0 0601: 8086:27b9 (rev 02)
00:1f.1 0101: 8086:27df (rev 02)
00:1f.3 0c05: 8086:27da (rev 02)
01:00.0 0280: 14e4:4315 (rev 01)
kamryn@Genesis01:~$ sudo modprobe sk98lin
[sudo] password for kamryn: 
FATAL: Module sk98lin not found.
kamryn@Genesis01:~$ 

```

Is there a faster way to find linux-a.b.c.tar.bz2 at ftp.kernel.org? I have been looking folder by folder and there has to be a faster way than this.

---

### Post by anewguy on 2011-08-27
> **KamrynB said:**
> Here is the output:

```

kamryn@Genesis01:~$ lspci -n
00:00.0 0600: 8086:27ac (rev 03)
00:02.0 0300: 8086:27ae (rev 03)
00:02.1 0380: 8086:27a6 (rev 03)
00:1b.0 0403: 8086:27d8 (rev 02)
00:1c.0 0604: 8086:27d0 (rev 02)
00:1c.1 0604: 8086:27d2 (rev 02)
00:1d.0 0c03: 8086:27c8 (rev 02)
00:1d.1 0c03: 8086:27c9 (rev 02)
00:1d.2 0c03: 8086:27ca (rev 02)
00:1d.3 0c03: 8086:27cb (rev 02)
00:1d.7 0c03: 8086:27cc (rev 02)
00:1e.0 0604: 8086:2448 (rev e2)
00:1f.0 0601: 8086:27b9 (rev 02)
00:1f.1 0101: 8086:27df (rev 02)
00:1f.3 0c05: 8086:27da (rev 02)
01:00.0 0280: 14e4:4315 (rev 01)
kamryn@Genesis01:~$ sudo modprobe sk98lin
[sudo] password for kamryn: 
FATAL: Module sk98lin not found.
kamryn@Genesis01:~$ 

```


Well, guess the driver module isn't present.  Makes sense since it didn't build, but leaves me curious as to how it worked once.

> Is there a faster way to find linux-a.b.c.tar.bz2 at ftp.kernel.org? I have been looking folder by folder and there has to be a faster way than this.

If you need the linux headers, just use Synaptic Package Manager.  I *thought* the ubuntu kernel source was installed by default, but if not then also look Synaptic Package Manager for that as well.  BUT....before you do all of that, pass me the link for the tar'd package containing the driver and readme (I assume from Marvell?) and I want to take a good look at all of it first as there may be an easier way to get that driver module.

Dave ;)

EDIT:  I'm going to be gone for a while - got supper to do, and then some Viking preseason football!

---

### Post by anewguy on 2011-08-28
Hey - found another discussion with this on HP Mini -> try turning off the PC, plugging in the network cable (both ends, of course ;) ), then booting again.  Does the adapter work?  This seems to be a problem with that adapter.

Post back the result as there may be a way to get around this.

dave ;)

BTW - people are reporting that at least for the HP Mini installing 10.04 or 10.10 (remember 10.04 is the latest long term support version).

---

### Post by coffeecat on 2011-08-28
I'm going to muddy the waters a bit! :)

I think there may be more than one issue. Whether or not there is a driver problem, something else is needed to explain the fact that the ethernet card was not showing in the output of lspci for a time. Yes, I know that it appeared after the script was run, but you don't need a driver - or even a viable driver - for devices to appear in lspci. It's re-appearance could have been a coincidence. lspci merely lists all PCI devices whether or not there is an active driver for them. Which is why I still think there may be a hardware problem - which now seems to be coming and going.

@KamrynB, you didn't answer this question. Was the ethernet card working right at the beginning - before it did its disappearing act?

---

### Post by anewguy on 2011-08-29
Hi Coffeecat - welcome back to the thread!  No muddying of the waters happening at all - just looking for a solution what ever it might be.  I thought I'd throw in here that even though I don't have that adapter I went ahead and downloaded, untar'd and tried the install procedure.  I got the same error.  I had to set up the link as they mention on the screen when it fails to have my /usr/src/linux-headers-2.6.35-30-generic-pae have a link of /usr/src/linux.  That got around that initial problem.  However, I think the package itself is messed up, because running the install procedure it gets into the compilation of 1 of the C sources and kicks out tons of errors of functions not defined, etc., that would indicate to me it isn't looking in all of the folders for the header files.  In the skge.c source I noticed it is including things from h, but there is a h folder in each of the kernel prefix folders (2.4, 2.6) and there is also a common/h so I don't know how it figures out which of the actual header folders to look in.  I tried just running make in one of the kernel prefix folders (in my case 2.6) but it doesn't work, and configure isn't found.

Just thought I'd throw that out there as I'm trying to figure out how to build the kernel module so it can be loaded/unloaded on the fly.  I don't know if some of these things are defined in the kernel source or not as I never got into that.  The 1st option when you run the install is for "installation" which builds the kernel module and does some other work (removing existing module, loading the new, etc.).  The 2nd option is for compiling the kernel itself so that the driver is built in to the kernel - the option obviously to stay away from and instead go with the dynamic module.

Don't know if any of that makes much sense.

I would really like to see the OP try a LiveCD media of some sort (probably USB stick since it's a mini) of 10.04 to see if it works okay there, as that is something reported in the threads - the failure occurs when you go to 11.04 (and therefore, I suspect, some version of the kernel or a delivery of a kernel module driver for the device that doesn't work).

Anyway, I know you were helping the OP, so since you're back I'm going to move to the background unless something comes up.  I know it makes it much easier for an OP to just work with 1 person at a time.

Thanks for coming back!

Dave ;)

EDIT:  double-checked the Marvell site for the download - it's for Fedora , not for Debian-based systems  This could explain the compilation errors.  If worse came to worse I could try to go through all the code to get it to work with Debian based systems, but that would take me quite a while!

---

### Post by KamrynB on 2011-08-29
Sorry I was away the past few days!

> **coffeecat said:**
> I'm going to muddy the waters a bit! :)
@KamrynB, you didn't answer this question. Was the ethernet card working right at the beginning - before it did its disappearing act?

Yes it was working when I first installed Ubuntu.

[QUOTE=anewguy]double-checked the Marvell site for the download - it's for Fedora , not  for Debian-based systems  This could explain the compilation errors.   If worse came to worse I could try to go through all the code to get it  to work with Debian based systems, but that would take me quite a while! [/QUOTE]


Here is the link for the drivers:
[http://www.marvell.com/drivers/driverDisplay.do?driverId=204](http://www.marvell.com/drivers/driverDisplay.do?driverId=204)
I don't see it specifically mention Fedora..

[QUOTE=anewguy]Hey - found another discussion with this on HP Mini -> try turning  off the PC, plugging in the network cable (both ends, of course :wink: ), then booting again.  Does the adapter work?  This seems to be a problem with that adapter.[/QUOTE]

I'll try this right now.

[QUOTE=anewguy]If you need the linux headers, just use Synaptic Package Manager[/QUOTE] 

Thanks! I will try this out. It has to be better than looking through every folder on the ftp site.

---

### Post by KamrynB on 2011-08-29
Ok, the ethernet interface works when the netbook is rebooted and both ends of the cable are plugged in!

Now I'm just confused as to why it decides to go to sleep when the computer boots and there is not lan connection. 

I checked up the synaptic package manager and did a search for the linux-a.b.c. file and it only brought up the linux kernel.... how do I find that specific .bz2 file?

Thank you soooo much for your help guys!

---

### Post by anewguy on 2011-08-29
As far as not seeing it's for Fedora, that's because you are linking directly to the download.  If you start from the other direction - go to Marvell, support and put in the id it will then go to a page where you can select drivers.  On that page is the link to the download page, and it specifically says Fedora.

It won't be a packed (bz2) file in synaptic - it will be for your current kernel.  BUT......if you read my last post this whole process of trying to build the installable kernel module wouldn't work for me, so I'd suggest you not tackle that yet.  I know you'd like to just have it working, but we really do need to try to figure out why it was and now isn't.

So, a couple of questions:

- since it worked when you first installed, was the cable plugged in or removed when you installed and booted?

- do you know if a new kernel was delivered in an update?  If you get the grub menu, how many entries are there for Ubuntu - 3? 6?  If more than 3, try the oldest kernel instead of the default.  Does that work?

I'm starting to suspect, especially since this worked when you first installed, that a kernel update or an updated sky2 driver may have been delivered.

So, how much data, etc., do you have in your installation?  Would you be willing to reinstall 11.04?  If so, we could have you do that, but with nothing connected for internet - no hard wire, etc..  Then we could check the status right after the install.  We could then have you try an update and see if a new kernel is delivered and if so, if the interface still shows.  

Also - if you boot with the cable plugged in, then remove the cable and do the lspci, does the interface still show?  Does your PC still function ok or does it lock up?  (Other posts about similar problem but different chipset report this, want to see if it's so with your installation and hardware).

Sorry to intrude again - I just had those thoughts I thought I'd pass along.

Dave ;)

---

### Post by anewguy on 2011-08-29
Coffeecat - I hope you're still there!  I really would like having you back and doing the interacting with the OP.  You were helping before and I really didn't mean to butt in or anything!

Hope you're there!

Dave ;)

---

### Post by KamrynB on 2011-08-30
I give up.... I "downgraded" to Lucid and everything works 100% out of the box.

Thank you  for all your help though-- but this version of Ubuntu is simply not for this netbook.

---

### Post by anewguy on 2011-08-30
Yeah, as I mentioned a few times, the net was full of threads where they went back to either 10.04 or 10.10 things worked fine.  That's why I was leaning to a problem with a kernel update (perhaps they tried to include some version of the driver or another stepped on it).  Since the kernel in a 10.04 (Lucid) install would be older, the problem should have gone away.  However, what I don't know is if you do enough of the updates in Lucid if it will ever get to the kernel version that causes the problem in 11.04.  Hopefully not!

Glad you got it working, and since 11.04, to me at least, was just a way to try Unity (10.04 is the latest LTS release), you really aren't out anything anyway.  Perhaps by the time the next LTS comes along it will all be working again.

Best of luck!
Dave ;)

---

### Post by coffeecat on 2011-08-30
> **KamrynB said:**
> I give up.... I "downgraded" to Lucid and everything works 100% out of the box.

Thank you  for all your help though-- but this version of Ubuntu is simply not for this netbook.

Sorry to hear you had problems with 11.04. Good to hear that it's working with Lucid. I guess it was a driver issue after all, but that leaves room for hope. The driver is a kernel module and the kernel in the upcoming 11.10 release is a later one from that in 11.04. Hopefully, whatever was wrong with the Marvell driver in 11.04's kernel will not be there in the later kernel. Give 11.10 a go when it's released in October, and if that's disappointing, the next LTS in April next year will be worth trying, as anewguy suggested.

Good luck!

---

### Post by alphacrucis2 on 2011-08-30
Curious. Sounds a bit like a "wake on lan" feature going wrong.

---

### Post by mathia on 2011-09-13
From Readme file of the install package:

Problem:  After running the "install.sh" script the error message 
          './functions: 44: Syntax error: "(" unexpected' is displayed.
Reason:   Your Linux sytem uses a Debian Almquist shell (dash) which is a Unix 
          shell and much smaller than bash but still aiming at POSIX-compliancy. 
        It requires less disk space but is also less feature-rich.
Solution: Use the following command: 'sudo bash ./install.sh'. 


> **KamrynB said:**
> Hello all and thank you for reading.

I am an Ubuntu neophyte who is going through hell reinstalling the drivers for eth0 that I accidentally deleted. I have an HP Mini 1000. After some googling I landed at the Marvell site to download my driver, here:

[http://www.marvell.com/drivers/driverDisplay.do?driverId=204](http://www.marvell.com/drivers/driverDisplay.do?driverId=204)

I admit I am coming from Windows and I expected it to be as simple as click, run, boom. WRONG. 

That's ok though, I am using learning Ubuntu for networking reasons so I saw this as an opportunity to learn. I opened the .bz2 and the readme file and followed the instructions word for word, and am now stumbled at the part where I have to type "./install.sh" in the terminal. I get a syntax error "expected ")".  

I've attached the screenshot and the readme file of the instructions. Please explain what I am typing wrong?

Thank you!!

---

### Post by psrdotcom on 2011-09-13
Even, I will support the Mathia .. run the following command with root permission

bash install.sh

---

