---
title: "wireless networks do not show up"
date: 2011-04-21
forum: New to Ubuntu
---

### Post by lynxtbw on 2011-04-21
i have v. 10.04 on my hp g42-230us laptop, and i have tried a few different wireless networks, but they dont show up. it works with the ethernet fine, just no wireless. i dont even know where to start, i am brand new to Ubuntu. help would be much appreciated.

---

### Post by wep940 on 2011-04-21
Since you can get an ethernet connection, connect it. Then do the following:
 
- open a terminal window (applications/accessories/terminal)
- type:
 
sudo apt-get update <press enter>
 
It will ask for a password - it's your normal Ubuntu user password.  As you type it it will not appear on the screen.
 
- Now, go to system/administration and look for something like Additional Drivers or Restricted Drivers.  Click on this.  It will start a process where it will look on the net to see if there is a driver for your wireless and download/install it.  When it finishes, if it was successful at finding a driver, you should see a driver listed in the window - be sure it is marked as "enabled".  If this doesn't happen, go to Try This Instead.
 
- physically unplug the ethernet cable
- right-click on the network manager icon and be sure "Enable Wireless" is checked - it not, check to enable it.  If it won't let you, or if the option is greyed out, please post back.
- now left-click on the network manager icon.  Do wireless networks show now?
 
 
 
Try This Instead:
 
Well, since it's a laptop, there are a few possibilities:
 
- it's built-in and on the internal PCI bus
- it's built-in and on the internal USB bus
- it's external - perhaps a USB device
 
Let's start with the first and second:
 
- open a terminal window (applications/accessories/terminal)
- type:
 
lspci <press enter>
 
copy the output to a reply here
 
lsusb <press enter>
 
again, copy the output to a reply here
 
If you know it's an external device, post back and we'll go from there.
 
Many of the wireless adapters still have what are known as "restricted" drivers, meaning the driver can't be delivered on the free Ubuntu distribution media.

---

### Post by lynxtbw on 2011-04-21
the "sudo apt-get update" gave me lots of things i dont understand. they read-

Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release.gpg
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/multiverse Translation-en_US
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release.gpg [198B]
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/main Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release 
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/universe Translation-en_US
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release [44.7kB]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main Packages 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Sources
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Packages [180kB]
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Packages [4,557B]
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Sources [54.3kB]
Get:6 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Packages [67.8kB]
Get:7 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Sources [20.1kB]
Fetched 372kB in 4s (83.7kB/s)                      
Reading package lists... Done
torrey@torrey-laptop:~$ 


when i tried the "additional drivers" thingy, "hardware drivers" was the closest thing i came by, but it gave me nothing (no proprietary drivers are on use in this system). 

network manager does not show me an "enable wireless" option. it has enable networking, and enable notifications? which are both checked? 

lspci gave me 

torrey@torrey-laptop:~$ lspci
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge Alternate
00:01.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (int gfx)
00:05.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 1)
00:06.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [AHCI mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 41)
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA) (rev 40)
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller (rev 40)
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge (rev 40)
00:14.5 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI2 Controller
00:16.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:16.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Link Control
01:05.0 VGA compatible controller: ATI Technologies Inc M880G [Mobility Radeon HD 4200]
01:05.1 Audio device: ATI Technologies Inc RS880 Audio Device [Radeon HD 4200]
02:00.0 Network controller: Broadcom Corporation Device 4727 (rev 01)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
torrey@torrey-laptop:~$ 

lsusb gave me

torrey@torrey-laptop:~$ lsusb
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 0bda:0158 Realtek Semiconductor Corp. Mass Storage Device
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 04f2:b1aa Chicony Electronics Co., Ltd 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
torrey@torrey-laptop:~$

---

### Post by Paulster on 2011-04-21
How old is this notebook? Is this notebook in the U.S. ?  Look on the bottom of it.  Is there a sticker which says something about "FCC" or "RF Information"?  If so, what does it say?

---

### Post by ClientAlive on 2011-04-21
I think the things in the list when you ran the update are the ropositories it downloaded updates from. I think. Programs (or "apps" as they call them with Linux) that you get in the future will also come from repositories. Basically all that is, is the place where the stuff comes from.

Ubuntu will have certain repositories (or "repos" for short) configured/ installed in a certain app on your system (already on there) called "synaptic package manager" or an other one that is similar called "Software Center." Those can be changed or added to in the future but it's probably a good idea to keep the ones that come with the system.

Don't want to get off track though. I know the question was about the wireless issue. Just thought I'd interject that.
:D

---

### Post by wep940 on 2011-04-21
The Broadcom 4727 is your wireless. It must be different from the 43xx series from Broadcom, as the procedure I gave you would have loaded the driver. I've been doing some searching on the net - will let you know when I figure what the various solutions have in common so I can hopefully give you something simple.
 
BTW - I know you are new, so I doubt it, but I have to ask: did you do anything that required installing the backports?
 
Could you also post back the output of the following (use a terminal window, as explained in my previous post):
 
lspci -n | grep 14e4


Some of the threads are suggesting the STA module, but in the docs for the STA module I don't see the 4727 mentioned.  The above command will probably return the same 4727, but we need to be sure.
 
Additionally, I *thought* the STA module was one of the ones that would have gotten installed via my first post.  However, you may want to check in Synaptic Package Manager and see if you can find something for Braodcom STA (I'd look but I'm booted in Windows right now).  If you find it, try installing it, reboot, and see if the wireless works.

---

### Post by lynxtbw on 2011-04-22
@wep940
i installed "broadcom sta common", restarted the computer, and still nothing.now i do not see the  enable networking, and enable notifications option i mentioned before (when i unplugged the ethernet). 

i do not know what backpoarts are, so i doubt it. 

it gave me-
torrey@torrey-laptop:~$ lspci -n | grep 14e4
02:00.0 0280: 14e4:4727 (rev 01)
torrey@torrey-laptop:~$

@paulster
it is less than  year old,  yes it is in the US. just made in china, like most electronics.

---

### Post by shaun_bc on 2011-04-22
A couple things to try:

Use the ndiswrapper (in the Ubuntu Software Center) with the HP Windows driver see if that works.

Try running Ubuntu 10.10 from a LiveCD and see if the wireless works in 10.10.  I had a similar issue in 10.04 where I had to compile the driver for the asus_eee_1001p and when I installed 10.10 the wireless driver issue was fixed.

Good Luck :)

---

### Post by josephmills on 2011-04-22
could we please see a 
```

sudo lshw -C network

```
Thanks

---

### Post by 3rdalbum on 2011-04-22
Ubuntu 11.04 is a year more recent. You can get Beta 2 now, and it might have support for your WiFi.

---

### Post by wep940 on 2011-04-22
The STA driver, installed via downloading the source from Broadcom, seems to be what most have done to get this to work.  Since the STA driver you installed didn't work, the first thing you want to do is back it out so you are back to where you were before.
 
Please post back the information that josephmills requested, and please also post the output of "sudo lsmod" -> it will ask for your password - it's just your normal ubuntu password and won't show on the screen as you type it.
 
I'd like the output of the "sudo lsmod" as I'm pretty sure that ssb and probably at least one other Broadcom module are getting loaded by default - we'd need to remove those and retry the STA driver - if it works then we need to blacklist the modules so they don't load at boot.  We can walk you through all of this, so don't worry.  For now, just post back both pieces of data that have been asked for.

---

### Post by wep940 on 2011-04-22
Also, the lspci output you posted shows the device and I looked it up on the net and it supposedly the 4313.  I don't know why the restricted drivers didn't install, but [http://ubuntuforums.org/showthread.php?p=10565832#post10565832](http://ubuntuforums.org/showthread.php?p=10565832#post10565832) shows installing the kernel source to get it working, so you may want to try:
 
- open the synaptic package manager
- search for bcmwl-kernel-source and mark it for installation
- while you're at it, I would mark the build-essential package for installation as well
- I'm not sure - this may require the linux-header package matching your kernel.
- click the apply and let it all install
- restart your PC
- check in the Hardware Drivers again and see if the STA module is there
- look in network manager again to see if the networks are showing or not

---

### Post by ClientAlive on 2011-04-22
> **3rdalbum said:**
> Ubuntu 11.04 is a year more recent. You can get Beta 2 now, and it might have support for your WiFi.


That's the release I have (11.04 beta) and I have the bcm 43xx in my machine. Getting the wireless working on this thing was not an easy task. I don't think my bcm 43xx is the same as what lynxtbw has though - so not to worry.

;)

---

### Post by BertN45 on 2011-04-22
I had the same problem with the BCM4311 in the BETA 2 release so upgrade will not solve the problem.. 

The beta proposed the driver from "additional drivers" after the boot, but that did not work. 

In that case:
- deactivate the Broadcom STA driver again, go system -> administration -> additional drivers
- go to the Synaptic Package Manager in the same menu
- type b43 in the filter box 
- install "firmware- b43-installer" and the "b43-fwcutter"

That solved my problem and that same driver should also work with the BCM4318 according to the description

---

### Post by lynxtbw on 2011-04-22
> **josephmills said:**
> could we please see a 
```

sudo lshw -C network

```
Thanks
it gave me-

*-network UNCLAIMED     
       description: Network controller
       product: Broadcom Corporation
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:f0100000-f0103fff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: c8:0a:a9:d3:42:a2
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.0.11 latency=0 link=yes multicast=yes port=MII speed=100MB/s
       resources: irq:26 ioport:2000(size=256) memory:f0010000-f0010fff(prefetchable) memory:f0000000-f000ffff(prefetchable) memory:f0020000-f002ffff(prefetchable)

---

### Post by lynxtbw on 2011-04-22
so, i am planning on installing the new version, since people are seeming to say that may help. my question being, there is notebook edition and desktop addition, as well as an option between 30 something bit and 60 something bit. or should i wait the few days and install 11.04? i really appreciate the help.

---

### Post by BertN45 on 2011-04-22
_The new release will not help_. I am running the new release and it did not work! Look to my previous post, it is simple and I am almost sure it solves your problem, like it did mine. Anyhow you will need it also for the new release.

---

### Post by lynxtbw on 2011-04-22
@BertN45, i looked, and there is no "additional drivers". there is "synaptic package manager"? i tried that, but when i searched "b43" it only gave me the b43-fw cutter, not a b43-installer. i downloaded the cutter, and it did not seem to make any difference. is there something super simple i am missing? my exact situation is- right click network icon --> left click edit connections.. --> tab over to wireless tab, and the screen has the options to "add" or "close". the edit and delete option are blanked out. there is nothing in the screen where wireless networks should be.

---

### Post by wep940 on 2011-04-22
Please, read the thread I posted about using the kernel source - it solved this problem for others.  If you have any questions on it, please post back.  Outside of ndiswrapper, which I have nothing against but would rather find a native solution, you are almost out of other options.  B43, STA, etc., SHOULD have installed, if they were going to, from the instructions I first gave.  Since nothing showed up, I did additional searching on the web and found other posts all pointing the link I posted.

---

### Post by epadget1 on 2011-04-22
I've been having similar problems.  My wireless was working fine earlier today but after I installed updates for the first time this week NetworkManager quit showing wireless networks.  I have a Broadcom BCM4312 card on Xubuntu 10.4.  

I've tried installing and reinstalling bcmwl-kernel-source and a number of other related packages, but didn't have any luck.

My wireless worked fine before without any proprietary drivers, but I though I would try activating the Broadcom STA wireless driver that appears in System>Hardware Drivers, but this also failed, saying
```

Sorry, installation of this driver failed.

Please have a look at the log file for details: /var/log/jockey.log
```

/var/log/jockey.log said:

```

2011-04-22 23:47:46,530 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2011-04-22 23:47:46,531 WARNING: /sys/module/wl/drivers does not exist, cannot rebind wl driver 
```

Maybe there are a couple problems converging here.  It seems like I've tried half a dozen solutions that others had to similar problems without any success.  Any thoughts?

---

### Post by josephmills on 2011-04-23
> **lynxtbw said:**
> the "sudo apt-get update" gave me lots of things i dont understand. they read-

Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release.gpg
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/multiverse Translation-en_US
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release.gpg [198B]
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/main Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release 
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/universe Translation-en_US
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release [44.7kB]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main Packages 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Sources
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Packages [180kB]
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Packages [4,557B]
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Sources [54.3kB]
Get:6 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Packages [67.8kB]
Get:7 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Sources [20.1kB]
Fetched 372kB in 4s (83.7kB/s)                      
Reading package lists... Done
torrey@torrey-laptop:~$ 


when i tried the "additional drivers" thingy, "hardware drivers" was the closest thing i came by, but it gave me nothing (no proprietary drivers are on use in this system). 

network manager does not show me an "enable wireless" option. it has enable networking, and enable notifications? which are both checked? 

lspci gave me 

torrey@torrey-laptop:~$ lspci
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge Alternate
00:01.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (int gfx)
00:05.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 1)
00:06.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [AHCI mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 41)
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA) (rev 40)
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller (rev 40)
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge (rev 40)
00:14.5 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI2 Controller
00:16.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:16.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Link Control
01:05.0 VGA compatible controller: ATI Technologies Inc M880G [Mobility Radeon HD 4200]
01:05.1 Audio device: ATI Technologies Inc RS880 Audio Device [Radeon HD 4200]
**02:00.0 Network controller: Broadcom Corporation Device 4727 (rev 01)**
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
torrey@torrey-laptop:~$ 

lsusb gave me

torrey@torrey-laptop:~$ lsusb
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 0bda:0158 Realtek Semiconductor Corp. Mass Storage Device
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 04f2:b1aa Chicony Electronics Co., Ltd 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
torrey@torrey-laptop:~$

do you see the bold
```

02:00.0 Network controller: Broadcom Corporation Device 4727 (rev 01)

```
you can **NOT** use the b43 driver with this it will not work. you need this 
[http://linuxwireless.org/en/users/Drivers/brcm80211](http://linuxwireless.org/en/users/Drivers/brcm80211)
hope that this clears somethings up

---

### Post by josephmills on 2011-04-23
> **epadget1 said:**
> I've been having similar problems.  My wireless was working fine earlier today but after I installed updates for the first time this week NetworkManager quit showing wireless networks.  I have a Broadcom BCM4312 card on Xubuntu 10.4.  

I've tried installing and reinstalling bcmwl-kernel-source and a number of other related packages, but didn't have any luck.

My wireless worked fine before without any proprietary drivers, but I though I would try activating the Broadcom STA wireless driver that appears in System>Hardware Drivers, but this also failed, saying
```

Sorry, installation of this driver failed.

Please have a look at the log file for details: /var/log/jockey.log
```

/var/log/jockey.log said:

```

2011-04-22 23:47:46,530 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2011-04-22 23:47:46,531 WARNING: /sys/module/wl/drivers does not exist, cannot rebind wl driver 
```

Maybe there are a couple problems converging here.  It seems like I've tried half a dozen solutions that others had to similar problems without any success.  Any thoughts?

Hi there could we please see a 
```

lspci -vnn | grep 14e4

```
Thanks

---

### Post by epadget1 on 2011-04-23
Sure.  lspci -vnn | grep 14e4 gives

```
0c:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g [14e4:4315] (rev 01)
```

---

### Post by josephmills on 2011-04-23
> **epadget1 said:**
> Sure.  lspci -vnn | grep 14e4 gives

```
0c:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g [14e4:4315] (rev 01)
```

hey check this out

 [http://linuxwireless.org/en/users/Drivers/b43](http://linuxwireless.org/en/users/Drivers/b43)

hope this helps

---

### Post by Bikinguy on 2011-04-23
system...admin..hardware drivers ? worked for me.

---

### Post by wep940 on 2011-04-23
Unfortunately, there are 2 things at work here:
 
- for the OP, the restricted drivers don't show, and installing the STA driver didn't work
 
- installing the Broadcom public domain driver is fine, but be aware that the research I have done on the web for the OP's adapter shows that many people suffer slow speeds from that driver, whereas installing via the kernel source works great for them.
 
 
Just what I've seen on the net, and why I suggest following the link to install the kernel source, build-essential, etc., to get it working.

---

### Post by ClientAlive on 2011-04-23
> **wep940 said:**
> Unfortunately, there are 2 things at work here:
 
- for the OP, the restricted drivers don't show, and installing the STA driver didn't work
 
- installing the Broadcom public domain driver is fine, but be aware that the research I have done on the web for the OP's adapter shows that many people suffer slow speeds from that driver, whereas installing via the kernel source works great for them.
 
 
Just what I've seen on the net, and why I suggest following the link to install the kernel source, build-essential, etc., to get it working.


The more I keep reading this post the more I get that familiar feeling. This all just keeps sounding like the symptoms I experienced but my card is:

```
05:02.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
```

I don't think that is the same one. Just that the symptoms sound the same. If it's of any use, here is the link to the thread where my issue was resolved. Perhaps, even if the card is not the same, something can be seen about the approach that was taken and the way in which it was resolved.

[http://ubuntuforums.org/showthread.php?t=1731838&page=3](http://ubuntuforums.org/showthread.php?t=1731838&page=3)

HTH
:)

---

### Post by wep940 on 2011-04-23
The 4318 is supported via the restricted drivers, installed via a hard-wire connection, sudo apt-get update, followed by going to restricted/additional drivers and letting it do it's thing.  If this doesn't work, then it's likely there are some modules being loaded that need to be blacklisted.

---

### Post by epadget1 on 2011-04-27
Found my solution!  It looks like the proprietary Broadcom STA wireless driver had stopped working.  Following a post here [http://ubuntuforums.org/archive/index.php/t-1535893.html](http://ubuntuforums.org/archive/index.php/t-1535893.html) I ran
```
 sudo apt-get install build-essential linux-headers-generic
 sudo apt-get build-dep linux
```
and the driver came back giving me wireless again!

Now hopefully I haven't done too much damage with my attempts at voodoo fixes :P.

---

### Post by epadget1 on 2011-04-27
By the way, does anyone know what might cause a wireless driver to suddenly quit like that?  Could some incompatibility have been introduced the last time I installed updates?

I'm curious now that I'm not so frustrated anymore :).

---

### Post by wep940 on 2011-04-27
It's possible that an update delivered a new kernel, and if you had done anything to make it work in the past it was probably wiped by the new kernel.  This happens a lot particularly with non-Canonical supported software - like some drivers.

---

