---
title: "Facing 2 problems"
date: 2009-08-08
forum: New to Ubuntu
---

### Post by mat487 on 2009-08-08
Hello...

im new to ubuntu and i installed it recently, when i did i faced 2 problems: 

1-I cannot download any application from the add/remove Applications for some reason whenever i start a download it starts downloading but suddenly i get an error message that says:" Neverball (application name) cannot be installed on your computer type (i386)
Either the application requires special hardware features or the vendor decided to not support your computer type."

2- i cannot activate the visual effects for some reason when i click the extra or normal prefrence it loads for a second and then displays: "Desktop effects could not be enabled"

anyways i read before that i have to install compiz kit to enable the effects to run but cause of problem 1 i cant :S....

any help is appriciated :)

---

### Post by credobyte on 2009-08-08
[LIST=1]
[*]x86 or x64 ( post your sources.list ) ?
[*]System / Administration / Hardware drivers - are there any drivers listed ?
[/LIST]

---

### Post by halitech on 2009-08-08
what version did you install? ie 32bit or 64bit?

open a terminal and post the results of```
uname -m
```

for compiz, you need a card and driver capable of doing 3d. Do you know what card you have?

```
lspci
```

---

### Post by mat487 on 2009-08-08
> **halitech said:**
> what version did you install? ie 32bit or 64bit?

open a terminal and post the results of```
uname -m
```for compiz, you need a card and driver capable of doing 3d. Do you know what card you have?

```
lspci
```

First Result:

i686

Second Result:

00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 8400M GS (rev a1)
02:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
06:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 01)
07:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
07:09.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
07:09.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
07:09.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
07:09.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)

---

### Post by halitech on 2009-08-08
ok, you do have 32bit version of Ubuntu.

can you post  your sources.list file

```
cat /etc/apt/sources.list
```

for the video card, have you checked under hardware drivers to see if there is a driver to enable for your card?

---

### Post by mat487 on 2009-08-08
sources.list file:

# deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)]/ jaunty main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://sa.archive.ubuntu.com/ubuntu/](http://sa.archive.ubuntu.com/ubuntu/) jaunty main restricted universe
deb-src [http://sa.archive.ubuntu.com/ubuntu/](http://sa.archive.ubuntu.com/ubuntu/) jaunty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://sa.archive.ubuntu.com/ubuntu/](http://sa.archive.ubuntu.com/ubuntu/) jaunty-updates main restricted universe
deb-src [http://sa.archive.ubuntu.com/ubuntu/](http://sa.archive.ubuntu.com/ubuntu/) jaunty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://sa.archive.ubuntu.com/ubuntu/](http://sa.archive.ubuntu.com/ubuntu/) jaunty universe
deb-src [http://sa.archive.ubuntu.com/ubuntu/](http://sa.archive.ubuntu.com/ubuntu/) jaunty universe
deb [http://sa.archive.ubuntu.com/ubuntu/](http://sa.archive.ubuntu.com/ubuntu/) jaunty-updates universe
deb-src [http://sa.archive.ubuntu.com/ubuntu/](http://sa.archive.ubuntu.com/ubuntu/) jaunty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://sa.archive.ubuntu.com/ubuntu/](http://sa.archive.ubuntu.com/ubuntu/) jaunty multiverse
deb-src [http://sa.archive.ubuntu.com/ubuntu/](http://sa.archive.ubuntu.com/ubuntu/) jaunty multiverse
deb [http://sa.archive.ubuntu.com/ubuntu/](http://sa.archive.ubuntu.com/ubuntu/) jaunty-updates multiverse
deb-src [http://sa.archive.ubuntu.com/ubuntu/](http://sa.archive.ubuntu.com/ubuntu/) jaunty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://sa.archive.ubuntu.com/ubuntu/](http://sa.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse
# deb-src [http://sa.archive.ubuntu.com/ubuntu/](http://sa.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security main restricted universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security multiverse

and for the hardware drivers: yes i checked there is nothing to enable there and it tells me: "No proprietary drivers are in use on this System".

---

### Post by halitech on 2009-08-08
I don't see anything in the repo list that is pointing to any 64bit repo so not sure why you got that message. Maybe try opening a terminal and run
```
sudo apt-get update && sudo apt-get upgrade
```

far as the video card, you could try the drivers from Nvidia

[http://www.nvidia.com/object/linux_display_ia32_185.18.31.html](http://www.nvidia.com/object/linux_display_ia32_185.18.31.html)

---

### Post by mat487 on 2009-08-16
sorry i had some exams the past week,

i tried your code and it tells me:

E: Could not get lock /var/lib/apt/lists/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the list directory

tbh im begining to think that i might have some internet network problem since i live in a collage campus that requires me to go through authentication in order to access the internet

---

### Post by Soul-Sing on 2009-08-16
Several solutions:
1) Try it again after some time, sometimes it allright then
(server down)
2) close all package managers: ```
sudo rm /var/lib/apt/lists/lock
```
```
sudo apt-get update
```

---

### Post by halitech on 2009-08-16
Sorry, should have mentioned that you needed to close Synaptic as you can't use both methods at the same time. Try again after closing Synaptic.

Then, make sure you are connected and try the command again.

---

### Post by mat487 on 2009-08-16
i got this as a result:


Ign cdrom://Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1) jaunty/main Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty Release.gpg
Ign cdrom://Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1) jaunty/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/multiverse Translation-en_US
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates Release.gpg [189B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/multiverse Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-security Release.gpg
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-security/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-security/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-security/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-security/multiverse Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty Release
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates Release [49.6kB]               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-security Release                         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/main Packages                            
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates Release
  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/universe Packages                        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/main Sources        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/restricted Sources  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/universe Sources    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/multiverse Packages 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/multiverse Sources  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-security/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-security/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-security/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-security/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-security/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-security/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-security/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-security/multiverse Sources
Fetched 190B in 2s (67B/s)                               
Reading package lists... Done
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/jaunty-updates/Release](http://archive.ubuntu.com/ubuntu/dists/jaunty-updates/Release)  

W: Some index files failed to download, they have been ignored, or old ones used instead.
W: You may want to run apt-get update to correct these problems

---

### Post by sailthesea on 2009-08-16
This bit tells you what it thinks you should do

W: Some index files failed to download, they have been ignored, or old ones used instead.
W: You may want to run apt-get update to correct these problems

 Close all other processes open terminal and type :

sudo apt-get update

You will be asked for your password but it won't be shown
If you are on line you should get up and running

Sudo is the most powerful command in the terminal arsenal and should be used with care It grants you unlimited root user status and enables you to make system modifications  Type man sudo in terminal and you'll see what its about Man is the query code for any given command and will display its purpose
Hope the exams went well and welcome!:P

---

### Post by mat487 on 2009-08-17
for some reason my grpahic card appaerd in the Hardware Drivers... but when i tried to activate it the following message appeard:

```
Sorry, the Jockey backend crashed. Please file a bug at:

  ubuntu-bug jockey-common

Trying to recover by restarting backend
```

and for 
```
sudo apt-get update
```
i got:

```
Ign cdrom://Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1) jaunty/main Translation-en_US
Ign cdrom://Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1) jaunty/restricted Translation-en_US
Get:1 http://ubuntu.mirrors.isu.net.sa jaunty Release.gpg [189B]
Ign http://ubuntu.mirrors.isu.net.sa jaunty/main Translation-en_US
Ign http://ubuntu.mirrors.isu.net.sa jaunty/restricted Translation-en_US
Ign http://ubuntu.mirrors.isu.net.sa jaunty/universe Translation-en_US
Ign http://ubuntu.mirrors.isu.net.sa jaunty/multiverse Translation-en_US
Get:2 http://ubuntu.mirrors.isu.net.sa jaunty-updates Release.gpg [189B]
Ign http://ubuntu.mirrors.isu.net.sa jaunty-updates/main Translation-en_US
Ign http://ubuntu.mirrors.isu.net.sa jaunty-updates/restricted Translation-en_US
Ign http://ubuntu.mirrors.isu.net.sa jaunty-updates/universe Translation-en_US
Ign http://ubuntu.mirrors.isu.net.sa jaunty-updates/multiverse Translation-en_US
Get:3 http://ubuntu.mirrors.isu.net.sa jaunty-security Release.gpg [189B]
Ign http://ubuntu.mirrors.isu.net.sa jaunty-security/main Translation-en_US
Ign http://ubuntu.mirrors.isu.net.sa jaunty-security/restricted Translation-en_US
Ign http://ubuntu.mirrors.isu.net.sa jaunty-security/universe Translation-en_US
Ign http://ubuntu.mirrors.isu.net.sa jaunty-security/multiverse Translation-en_US
Hit http://ubuntu.mirrors.isu.net.sa jaunty Release
Hit http://ubuntu.mirrors.isu.net.sa jaunty-updates Release                  
Hit http://ubuntu.mirrors.isu.net.sa jaunty-security Release                 
Hit http://ubuntu.mirrors.isu.net.sa jaunty/main Packages                    
Hit http://ubuntu.mirrors.isu.net.sa jaunty/restricted Packages
Hit http://ubuntu.mirrors.isu.net.sa jaunty/universe Packages
Hit http://ubuntu.mirrors.isu.net.sa jaunty/main Sources
Hit http://ubuntu.mirrors.isu.net.sa jaunty/restricted Sources
Hit http://ubuntu.mirrors.isu.net.sa jaunty/universe Sources
Hit http://ubuntu.mirrors.isu.net.sa jaunty/multiverse Packages
Hit http://ubuntu.mirrors.isu.net.sa jaunty/multiverse Sources
Get:4 http://ubuntu.mirrors.isu.net.sa jaunty-updates/main Packages [133kB]
Hit http://ubuntu.mirrors.isu.net.sa jaunty-updates/restricted Packages
Hit http://ubuntu.mirrors.isu.net.sa jaunty-updates/universe Packages
Hit http://ubuntu.mirrors.isu.net.sa jaunty-updates/main Sources
Hit http://ubuntu.mirrors.isu.net.sa jaunty-updates/restricted Sources
Hit http://ubuntu.mirrors.isu.net.sa jaunty-updates/universe Sources         
Hit http://ubuntu.mirrors.isu.net.sa jaunty-updates/multiverse Packages      
Hit http://ubuntu.mirrors.isu.net.sa jaunty-updates/multiverse Sources         
Hit http://ubuntu.mirrors.isu.net.sa jaunty-security/main Packages
Hit http://ubuntu.mirrors.isu.net.sa jaunty-security/restricted Packages
Hit http://ubuntu.mirrors.isu.net.sa jaunty-security/universe Packages
Hit http://ubuntu.mirrors.isu.net.sa jaunty-security/main Sources
Hit http://ubuntu.mirrors.isu.net.sa jaunty-security/restricted Sources
Hit http://ubuntu.mirrors.isu.net.sa jaunty-security/universe Sources
Hit http://ubuntu.mirrors.isu.net.sa jaunty-security/multiverse Packages
Hit http://ubuntu.mirrors.isu.net.sa jaunty-security/multiverse Sources
Fetched 568B in 1s (366B/s)                             
W: Failed to fetch http://ubuntu.mirrors.isu.net.sa/ubuntu/dists/jaunty-updates/main/binary-i386/Packages.bz2  Hash Sum mismatch

E: Some index files failed to download, they have been ignored, or old ones used instead.
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
```

---

### Post by Bartender on 2009-08-17
WTH are Neverball and Jockey???

---

### Post by sailthesea on 2009-08-17
> **mat487 said:**
> for some reason my grpahic card appaerd in the Hardware Drivers... but when i tried to activate it the following message appeard:

```
Sorry, the Jockey backend crashed. Please file a bug at:

  ubuntu-bug jockey-common

Trying to recover by restarting backend
```

and for 
```
sudo apt-get update
```
i got:

```
Ign cdrom://Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1) jaunty/main Translation-en_US
Ign cdrom://Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1) jaunty/restricted Translation-en_US
Get:1 http://ubuntu.mirrors.isu.net.sa jaunty Release.gpg [189B]
Ign http://ubuntu.mirrors.isu.net.sa jaunty/main Translation-en_US
Ign http://ubuntu.mirrors.isu.net.sa jaunty/restricted Translation-en_US
Ign http://ubuntu.mirrors.isu.net.sa jaunty/universe Translation-en_US
Ign http://ubuntu.mirrors.isu.net.sa jaunty/multiverse Translation-en_US
Get:2 http://ubuntu.mirrors.isu.net.sa jaunty-updates Release.gpg [189B]
Ign http://ubuntu.mirrors.isu.net.sa jaunty-updates/main Translation-en_US
Ign http://ubuntu.mirrors.isu.net.sa jaunty-updates/restricted Translation-en_US
Ign http://ubuntu.mirrors.isu.net.sa jaunty-updates/universe Translation-en_US
Ign http://ubuntu.mirrors.isu.net.sa jaunty-updates/multiverse Translation-en_US
Get:3 http://ubuntu.mirrors.isu.net.sa jaunty-security Release.gpg [189B]
Ign http://ubuntu.mirrors.isu.net.sa jaunty-security/main Translation-en_US
Ign http://ubuntu.mirrors.isu.net.sa jaunty-security/restricted Translation-en_US
Ign http://ubuntu.mirrors.isu.net.sa jaunty-security/universe Translation-en_US
Ign http://ubuntu.mirrors.isu.net.sa jaunty-security/multiverse Translation-en_US
Hit http://ubuntu.mirrors.isu.net.sa jaunty Release
Hit http://ubuntu.mirrors.isu.net.sa jaunty-updates Release                  
Hit http://ubuntu.mirrors.isu.net.sa jaunty-security Release                 
Hit http://ubuntu.mirrors.isu.net.sa jaunty/main Packages                    
Hit http://ubuntu.mirrors.isu.net.sa jaunty/restricted Packages
Hit http://ubuntu.mirrors.isu.net.sa jaunty/universe Packages
Hit http://ubuntu.mirrors.isu.net.sa jaunty/main Sources
Hit http://ubuntu.mirrors.isu.net.sa jaunty/restricted Sources
Hit http://ubuntu.mirrors.isu.net.sa jaunty/universe Sources
Hit http://ubuntu.mirrors.isu.net.sa jaunty/multiverse Packages
Hit http://ubuntu.mirrors.isu.net.sa jaunty/multiverse Sources
Get:4 http://ubuntu.mirrors.isu.net.sa jaunty-updates/main Packages [133kB]
Hit http://ubuntu.mirrors.isu.net.sa jaunty-updates/restricted Packages
Hit http://ubuntu.mirrors.isu.net.sa jaunty-updates/universe Packages
Hit http://ubuntu.mirrors.isu.net.sa jaunty-updates/main Sources
Hit http://ubuntu.mirrors.isu.net.sa jaunty-updates/restricted Sources
Hit http://ubuntu.mirrors.isu.net.sa jaunty-updates/universe Sources         
Hit http://ubuntu.mirrors.isu.net.sa jaunty-updates/multiverse Packages      
Hit http://ubuntu.mirrors.isu.net.sa jaunty-updates/multiverse Sources         
Hit http://ubuntu.mirrors.isu.net.sa jaunty-security/main Packages
Hit http://ubuntu.mirrors.isu.net.sa jaunty-security/restricted Packages
Hit http://ubuntu.mirrors.isu.net.sa jaunty-security/universe Packages
Hit http://ubuntu.mirrors.isu.net.sa jaunty-security/main Sources
Hit http://ubuntu.mirrors.isu.net.sa jaunty-security/restricted Sources
Hit http://ubuntu.mirrors.isu.net.sa jaunty-security/universe Sources
Hit http://ubuntu.mirrors.isu.net.sa jaunty-security/multiverse Packages
Hit http://ubuntu.mirrors.isu.net.sa jaunty-security/multiverse Sources
Fetched 568B in 1s (366B/s)                             
W: Failed to fetch http://ubuntu.mirrors.isu.net.sa/ubuntu/dists/jaunty-updates/main/binary-i386/Packages.bz2  Hash Sum mismatch

E: Some index files failed to download, they have been ignored, or old ones used instead.
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
```

Well you pretty much completed the upgrade but you seem to have some odd drivers installed to your video card and a process running elsewhere stalling your package completion Did you try booting the LiveCD and fixing the install from there?

---

