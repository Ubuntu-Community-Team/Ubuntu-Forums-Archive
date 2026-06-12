---
title: "[SOLVED] WUSB54Gv4 and Ndiswrapper-1.47 in Feisty"
date: 2007-07-19
forum: Networking &amp; Wireless
---

### Post by JawsThemeSwimming428 on 2007-07-19
Hey everyone. I have been trying for about three weeks now to get my new Feisty install on the Internet via my Linksys WUSB54Gv2 wireless adapter. I have looked at some of the threads on the Web, but with no success. The card, as reported on the site, is supposed to work "out of the box". This is obviously not the case. Therefore, I have been trying to install ndiswrapper-1.47 to attempt this method. I download ndiswrapper-1.47 from Sourceforge and transfer it to my Feisty machine via USB thumb drive. I run make distclean (after it is untar'd), then I run make, and sudo make install. All of these commands report no errors. I  then go to the WUSB54Gv4 directory of my wireless cards driver and run ndiswrapper-v. This reports that I am using ndiswrapper version 1.38 and it probably won't be enough to do what I want to. I don't know how to get rid of 1.38 and use 1.47. Anyone that can help me out I am really at a standstill! Thanks.

Also, why wouldn't my card work out of the box? The reason I installed this one is because it said it is compatible and has native support? I'm just wondering. Thanks.

---

### Post by kevdog on 2007-07-19
Can you do a google search for me and tell me what chipset you USB dongle uses??

To help you type
lsusb 
at the command line.
Then do a search on the output.  Im thinking its an Atheros based chip but could be wrong

---

### Post by JawsThemeSwimming428 on 2007-07-19
I will do that tonight when I get home from work. Thanks for the response! Are Atheros chipsets a problem?

---

### Post by ubanchaos on 2007-07-19
u can use the synaptic to download the newest ndiswrapper and ull probly be good but i had a linksys wmp 54g pci and i didnt work for nothing and dont ask linksys because they dont offer support for linux

---

### Post by JawsThemeSwimming428 on 2007-07-19
kevdog,

I ran the following commands, as you said, and this was the output. It doesn't even list my wireless interface with lshw. Do I have to do something to activate it? What's the next step?

ubanchaos,

 I would have used synaptic but I don't have internet on this PC. My internet is the wireless card that I can not seem to get working. Any advice?



kelly@kelly-desktop:~$ lsusb 
Bus 003 Device 003: ID 13b1:000d Linksys  
Bus 003 Device 001: ID 0000:0000   
Bus 002 Device 001: ID 0000:0000   
Bus 001 Device 001: ID 0000:0000   
kelly@kelly-desktop:~$ lsusb 
Bus 003 Device 003: ID 13b1:000d Linksys  
Bus 003 Device 001: ID 0000:0000   
Bus 002 Device 001: ID 0000:0000   
Bus 001 Device 001: ID 0000:0000   
kelly@kelly-desktop:~$ lspci -nn 
00:00.0 Host bridge [0600]: ATI Technologies Inc Radeon Xpress 200 Host Bridge [1002:5a33] (rev 01) 
00:02.0 PCI bridge [0604]: ATI Technologies Inc RS480 PCI-X Root Port [1002:5a34] 
00:11.0 IDE interface [0101]: ATI Technologies Inc ATI 437A Serial ATA Controller [1002:437a] (rev 80) 
00:12.0 IDE interface [0101]: ATI Technologies Inc ATI 4379 Serial ATA Controller [1002:4379] (rev 80) 
00:13.0 USB Controller [0c03]: ATI Technologies Inc IXP SB400 USB Host Controller [1002:4374] (rev 80) 
00:13.1 USB Controller [0c03]: ATI Technologies Inc IXP SB400 USB Host Controller [1002:4375] (rev 80) 
00:13.2 USB Controller [0c03]: ATI Technologies Inc IXP SB400 USB2 Host Controller [1002:4373] (rev 80) 
00:14.0 SMBus [0c05]: ATI Technologies Inc IXP SB400 SMBus Controller [1002:4372] (rev 82) 
00:14.1 IDE interface [0101]: ATI Technologies Inc Standard Dual Channel PCI IDE Controller ATI [1002:4376] (rev 80) 
00:14.2 Audio device [0403]: ATI Technologies Inc SB450 HDA Audio [1002:437b] (rev 01) 
00:14.3 ISA bridge [0601]: ATI Technologies Inc IXP SB400 PCI-ISA Bridge [1002:4377] (rev 80) 
00:14.4 PCI bridge [0604]: ATI Technologies Inc IXP SB400 PCI-PCI Bridge [1002:4371] (rev 80) 
01:00.0 VGA compatible controller [0300]: nVidia Corporation G70 [GeForce 7300 GT] [10de:0393] (rev a1) 
02:02.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10) 
kelly@kelly-desktop:~$ lshw -C network 
WARNING: you should run this program as super-user. 
  *-network                
       description: Ethernet interface 
       product: RTL-8139/8139C/8139C+ 
       vendor: Realtek Semiconductor Co., Ltd. 
       physical id: 2 
       bus info: pci@02:02.0 
       logical name: eth0 
       version: 10 
       serial: 00:16:76:46:92:a2 
       width: 32 bits 
       clock: 33MHz 
       capabilities: bus_master cap_list ethernet physical 
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 latency=64 maxlatency=64 mingnt=32 multicast=yes 
       resources: ioport:de00-deff iomemory:fddff000-fddff0ff irq:20 
kelly@kelly-desktop:~$

---

### Post by fredj on 2007-07-20
When you were compiling ndiswrapper 1.47 did you do a make uninstall to get rid of the old version.
The sequence is 
make distclean followed by make uninstall

---

### Post by JawsThemeSwimming428 on 2007-07-20
No I did not. I will do that as soon as I get home from work! Talk to you later!!

---

### Post by JawsThemeSwimming428 on 2007-07-20
After I run make distclean and make uninstall, do I run make and sudo make install?

---

### Post by JawsThemeSwimming428 on 2007-07-21
I really need help. I need to get this machine online. I can not get ndiswrapper working. Off of a clean install of Feisty, I downloaded ndiswrapper-1.47 and the latest WUSB54gv4 driver from Linksys. I untar'd and then ran make distclean, make uninstall, make. When I ran make I got a bunch of errors and warnings. What am I doing wrong? I would be very grateful for any help....I really need this machine online soon!

---

### Post by kevdog on 2007-07-21
Can you post some of the errors you were getting?

Its probably because you dont have either the build-essential or linux header files installed.  Both are required for you to compile anything from source. In case you havent done either here are the instructions:

> In order to compile the serial monkey drivers from source the build-essential package is required along with the linux kernel header files. If you already have an internet connection (ie a working wired ethernet connection), please skip to step #4. Without any internet connection, please begin at step #1.

All commands typed at command prompt:

   1. After booting into Ubuntu, put the Ubuntu installation CD in drive and wait for it to "spin up"
   2. sudo apt-cdrom add
   3. sudo aptitude update
   4. sudo aptitude install build-essential linux-headers-`uname -r`


---

### Post by kevdog on 2007-07-21
Ran across some new information for you.  Looks like for your device ndiswrapper is not the was to go since it contains the ra chipset.  The answer is to use the serial monkey drivers.  

Go ahead and install the build-essential and linux header files.

Now Im going to point you to 2 other links that specifically address your card, however the compilation and installation instructions are listed in the second post.  The second post references rt73 driver, but just remember that everywhere rt73 is mentioned you want to put rt2570 (this is the specific driver for your usb device)

Post #1: Post with solution for your card:
[http://ubuntuforums.org/showthread.php?t=503794](http://ubuntuforums.org/showthread.php?t=503794)

Post #2: Specific compilation and installation instructions:
[http://ubuntuforums.org/showthread.php?t=400236](http://ubuntuforums.org/showthread.php?t=400236)

Post #3: Serial Monkey website - where to download the drivers:
[http://rt2x00.serialmonkey.com/wiki/index.php?title=Main_Page](http://rt2x00.serialmonkey.com/wiki/index.php?title=Main_Page)

Post back if you have any questions!!!

---

### Post by JawsThemeSwimming428 on 2007-07-21
Last night I reinstalled Feisty, downloaded ndiswrapper-1.47 and the new driver for the WUSB54Gv4 card. I untar'd them, ran make distclean in the directory, then make uninstall, then make, and then sudo make install. I disabled the network manager in Gnome and now it works. Thanks for the help everyone!!!!!!

---

