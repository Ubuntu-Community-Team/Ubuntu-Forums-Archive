---
title: "To hp 6515b users (2)"
date: 2008-04-05
forum: Networking &amp; Wireless
---

### Post by kjman83 on 2008-04-05
Hi I luckly installed ubuntu 8.04

However,

I can't turn on the wireless of my laptop (hp 6515b).

It doesn't work after installing ubuntu.

Is there anyone who can see the BLUE light for wireless? (The user must know about blue light)

Please tell me..
_______________

It was my previous post.

and 

I did lspci what is heard from dimizer. Thank you about it.
Now What should I do?
Is there anyone knows about it?
-------------------------------------------------------------------------------------
kjman83@guinness:~$ lspci
00:00.0 Host bridge: ATI Technologies Inc RS690 Host Bridge
00:01.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (Internal gfx)
00:04.0 PCI bridge: ATI Technologies Inc Unknown device 7914
00:05.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 1)
00:06.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 2)
00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA
00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0)
00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1)
00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2)
00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3)
00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4)
00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI)
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 14)
00:14.1 IDE interface: ATI Technologies Inc SB600 IDE
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia
00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS690M [Radeon X1200 Series]
02:04.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev b6)
02:04.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 02)
10:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5787M Gigabit Ethernet PCI Express (rev 02)
30:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 02)
kjman83@guinness:~$

---

### Post by huwangjian on 2008-04-06
hi
I installed Ubuntu 7.10 on my hp6515b(GX548PA)
And I followed someother's solution to enable the wireless adapter.
But I don't know whether i'll work on 8.04.
Here is the solution:
1.disable the bcm43xx driver
> sudo rmmod bcm43xx
   then add it to blacklist
> sudo vim /etc/modprobe.d/blacklist
add this line
> blacklist bcm43xx

2.Go to HP website to download Windows XP driver for the wireless LAN card.
Extract the file under Windows XP, you will get a directory :
>    C:/SWSetup/WLAN/
Copy it to your ubuntu home directory for ndiswrapper use later. 

3.then get diswrapper-utils-1.9
> sudo atp-get diswrapper-utils-1.9
then install  driver
> sudo ndiswrapper -i /the location of/SWSetup/the location of version5 driver/bcmwl5.inf
Check ndiswrapper driver :
> sudo ndiswrapper -l
You should see :
> bcmwl5 : driver installed
        device (14E4:4312) present (alternate driver: bcm43xx)
Write wlan0 to ndiswrapper alias
> sudo ndiswrapper -m
start ndiswrapper&#65306;
> sudo modprobe ndiswrapper

4.Start netwrok admin tools to configurate the Wireless LAN:
System -> administration -> network

5.enable the system to load ndiswrapper when reboot.
> sudo vim /etc/modules
add the line
> ndiswrapper 

I hope it'll work!
hp6515b is really a strong challenger.
A lot of Hardware Problems!

---

### Post by dmizer on 2008-04-06
i also replied with similar information as given above, in your original thread ...

[http://ubuntuforums.org/showthread.php?p=4656764](http://ubuntuforums.org/showthread.php?p=4656764)

is there a particular reason you felt it necessary to create another thread?

---

