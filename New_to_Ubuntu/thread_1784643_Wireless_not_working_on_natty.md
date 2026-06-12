---
title: "Wireless not working on natty"
date: 2011-06-17
forum: New to Ubuntu
---

### Post by jonpon on 2011-06-17
Hi 
My son wanted windows on his computer along side his Ubuntu,(silly boy) so I installed windows and thought while I'm at it I'll put the latest version of Ubuntu on there as well. After much cursing and gnashing of teeth over the terrible unity interface, I found the "classic setting" and tried to install the wireless card as I had done with the old version of Ubuntu 10.10 that was on there before using ndiswrapper, but I can get it to work It refuses to connect. Any Ideas? Please?

Thank
Jonpon

---

### Post by gandaran on 2011-06-17
> **jonpon said:**
> Hi 
My son wanted windows on his computer along side his Ubuntu,(silly boy) so I installed windows and thought while I'm at it I'll put the latest version of Ubuntu on there as well. After much cursing and gnashing of teeth over the terrible unity interface, I found the "classic setting" and tried to install the wireless card as I had done with the old version of Ubuntu 10.10 that was on there before using ndiswrapper, but I can get it to work It refuses to connect. Any Ideas? Please?

Thank
Jonpon
what is the wireless device chipset?
to find out type in terminal
```
lspci
```
I'm sure you don't have to use ndiswrapper for drivers, there are linux drivers for almost every wireless device, try connecting to wired internet and update software package list then look in additional drivers to activate.

---

### Post by _0R10N on 2011-06-17
There's an option under System menu that allows you to check and install aditional driver (so it called the option). Take a look there, probably there's a suitting driver listed there.

---

### Post by jonpon on 2011-06-17
There's nothing except my graphics card under "Additional Drivers"

This is my lspci

```
fynn@fynns-computer:~$ lspci
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge
00:01.0 PCI bridge: Advanced Micro Devices [AMD] RS780/RS880 PCI to PCI bridge (int gfx)
00:0a.0 PCI bridge: Advanced Micro Devices [AMD] RS780/RS880 PCI to PCI bridge (PCIE port 5)
00:11.0 SATA controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 SATA Controller [IDE mode]
00:12.0 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB7x0 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB7x0 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3c)
00:14.1 IDE interface: ATI Technologies Inc SB7x0/SB8x0/SB9x0 IDE Controller
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB7x0/SB8x0/SB9x0 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:14.5 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI2 Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Link Control
01:05.0 VGA compatible controller: ATI Technologies Inc 760G [Radeon 3000]
01:05.1 Audio device: ATI Technologies Inc RS780 Azalia controller
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)
03:06.0 Network controller: Ralink corp. Device 3060

```

---

### Post by Toz on 2011-06-17
Have a look at the instruction in this solved link involving the same chipset: [http://ubuntuforums.org/showpost.php?p=10590763&postcount=5]("http://ubuntuforums.org/showpost.php?p=10590763&postcount=5")

---

### Post by jonpon on 2011-06-17
> Have a look at the instruction in this solved link involving the same chipset: [http://ubuntuforums.org/showpost.php...63&postcount=5](http://ubuntuforums.org/showpost.php...63&postcount=5)
I'm having trouble following the instructions, I downloaded what I think was the file but after doing
```
sudo apt-get install gcc build-essential
```
I'm not sure what I'm suposed to do

---

### Post by ruffEdgz on 2011-06-17
Was looking this over and wanted to see if you have the module rt2800 on:
```

lsmod | grep rt2800

```
If this doesn't show anything, then maybe you just need to run the following to enable the driver:
```

sudo modprobe -i rt2800pci

```
Hope this helps.

---

### Post by gandaran on 2011-06-17
[see this thread]("http://ubuntuforums.org/showthread.php?t=1677136&highlight=Network+controller%3A+Ralink+corp.+Device+3060") for the Network controller: Ralink corp. Device 3060, easy fix!

---

### Post by jonpon on 2011-06-17
My problem seems to be that I'm not fluent enough in Ububtology to be able to compile the driver, the two posts above both require me to know how to do this,

---

### Post by jonpon on 2011-06-17
@ ruffEdgz

both the codes you gave me gave no feedback at all
I also tried  "sudo lsmod | grep rt2800"
and got this
> fynn@fynns-computer:~$ lsmod | grep rt2800
fynn@fynns-computer:~$ sudo modprobe -i rt2800pci
[sudo] password for fynn: 
fynn@fynns-computer:~$ sudo lsmod | grep rt2800
rt2800pci              18159  0 
rt2800lib              43824  1 rt2800pci
crc_ccitt              12595  1 rt2800lib
rt2x00pci              13986  1 rt2800pci
rt2x00lib              39075  3 rt2800pci,rt2800lib,rt2x00pci
mac80211              257001  3 rt2800lib,rt2x00pci,rt2x00lib
eeprom_93cx6           12653  1 rt2800pci
fynn@fynns-computer:~$ ^C
fynn@fynns-computer:~$

---

### Post by fractalman on 2011-06-17
[http://linuxwireless.org/en/users/Drivers](http://linuxwireless.org/en/users/Drivers)

[]("http://aircrack-ng.org/doku.php?id=compatibility_drivers")[URL="http://aircrack-ng.org/doku.php?id=patching"]
[/URL]

---

### Post by Toz on 2011-06-17
Try gandaran's suggestion/link from post #8. Add the following lines to **/etc/modprobe.d/blacklist.conf**:
```
blacklist rt2800pci
blacklist rt2800lib
blacklist rt2x00pci
blacklist rt2x00lib
```

Save the changes and reboot.

---

### Post by M1k3y on 2011-06-18
If everything that those otherguys said doesnt work (I skimmed really fast), try this:
No.1 This only works with certain drivers and hardware (Broadcom).
Installing B43 Broadcom drivers
This is known to work only on Ubuntu 10.04LTS and 11.04 (LTS simply means long term support, this is because the version is older and more to all of the known bugs are fixed)
Installing without internet access
materials needed
 - Live CD/USB
 - Ubuntu 10.04 installed fully on a harddrive
BEFORE YOU ATTEMPT THIS MAKE SURE YOUR HARDWARE IS ON THE COMPATIBILITY LIST
Step 1
Navigate the Live CD/USB install media and install the packages below by either using the terminal commands given or double click on the files specified.

Files

/pool/main/d/dkms
/pool/main/p/patch
/pool/main/f/fakeroot
WARNING THE FOLLOWING FILE IS IN THE Restricted DIRECTORY NOT THE Main DIRECTORY (It can still be accessed without a password)
/pool/restricted/b/bcmwl

Terminal Commands
sudo dpkg -i dkms*
sudo dpkg -i patch*
sudo dpkg -i fakeroot*
sudo dpkg -i bcmwl-kernel-source*

Step 2
Restart Computer

Step 3
Under the desktop menu go to system > administration > hardware/additional drivers, make sure the broadcom driver is enabled.




Compatibility List
STA - BCM4311, BCM4312, BCM4313, BCM4321, BCM4322, BCM43224, BCM43225, BCM43227, BCM43228
b43 - BCM4301, BCM4306/2, BCM4306/3, BCM4311, BCM4312, BCM4318, BCM4320

---

