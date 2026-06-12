---
title: "[SOLVED] Updating Wireless Card Driver (Realtek 8180)"
date: 2008-12-16
forum: New to Ubuntu
---

### Post by cyclone5uk on 2008-12-16
I am a complete newbie, I just installed Ubuntu for the first time about 24 hours ago. So far everything has gone smoothly and I’m really impressed with it. The only problem is with my wireless card (A Realtek 8180 PCI). Ubuntu recognized the card and automatically installed a driver during installation and it happily connected to my wireless network. However, the signal strength is extremely low (about 15%). Under Vista (my previous OS), the signal strength had been much higher (more like 50%+). This is not the only problem. When I ran a speed test I found my connection was only 700kbps, however the same speed test under Vista gives me my full 10mbps of bandwidth.

I looked on the Realtek website and found that there is a Linux driver:

RTL8180L
Linux kernel 2.6.X
Version 1.5
2005/4/19

So my questions are:

1)How do I find out which driver is currently being used by Ubuntu?

2)If it is older than the driver I downloaded from the Realtek site, how do I update it?

Many thanks for your help.

---

### Post by S_e_P_p on 2008-12-16
Hello,

You should download all updates for your system and also check if there is an restricted driver for your WLAN card.

I think it is under System --> Hardware.

Use the following Code to get further information:

```

lspci -nn
lshw -C network

```

Greets,
Sebastian

---

### Post by cyclone5uk on 2008-12-16
Thanks for the info.

I have already run all updates and rebooted.

The only restricted driver listed under System --> Hardware is for my Nvidia Graphics card (which is working fine).

Thanks for the code, I will run it when I get home from work this evening.

---

### Post by cyclone5uk on 2008-12-16
Here's the info:

```
james@james-desktop:~$ lspci -nn
00:00.0 Host bridge [0600]: VIA Technologies, Inc. CN896/VN896/P4M900 Host Bridge [1106:0364]
00:00.1 Host bridge [0600]: VIA Technologies, Inc. CN896/VN896/P4M900 Host Bridge [1106:1364]
00:00.2 Host bridge [0600]: VIA Technologies, Inc. CN896/VN896/P4M900 Host Bridge [1106:2364]
00:00.3 Host bridge [0600]: VIA Technologies, Inc. CN896/VN896/P4M900 Host Bridge [1106:3364]
00:00.4 Host bridge [0600]: VIA Technologies, Inc. CN896/VN896/P4M900 Host Bridge [1106:4364]
00:00.5 PIC [0800]: VIA Technologies, Inc. CN896/VN896/P4M900 I/O APIC Interrupt Controller [1106:5364]
00:00.6 Host bridge [0600]: VIA Technologies, Inc. CN896/VN896/P4M900 Security Device [1106:6364]
00:00.7 Host bridge [0600]: VIA Technologies, Inc. CN896/VN896/P4M900 Host Bridge [1106:7364]
00:01.0 PCI bridge [0604]: VIA Technologies, Inc. VT8237/VX700 PCI Bridge [1106:b198]
00:02.0 PCI bridge [0604]: VIA Technologies, Inc. CN896/VN896/P4M900 PCI to PCI Bridge Controller [1106:a364] (rev 80)
00:03.0 PCI bridge [0604]: VIA Technologies, Inc. CN896/VN896/P4M900 PCI to PCI Bridge Controller [1106:c364] (rev 80)
00:0f.0 IDE interface [0101]: VIA Technologies, Inc. Device [1106:5372]
00:0f.1 IDE interface [0101]: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE [1106:0571] (rev 07)
00:10.0 USB Controller [0c03]: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller [1106:3038] (rev b0)
00:10.1 USB Controller [0c03]: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller [1106:3038] (rev b0)
00:10.2 USB Controller [0c03]: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller [1106:3038] (rev b0)
00:10.3 USB Controller [0c03]: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller [1106:3038] (rev b0)
00:10.4 USB Controller [0c03]: VIA Technologies, Inc. USB 2.0 [1106:3104] (rev 90)
00:11.0 ISA bridge [0601]: VIA Technologies, Inc. VT8237S PCI to ISA Bridge [1106:3372]
00:11.7 Host bridge [0600]: VIA Technologies, Inc. VT8251 Ultra VLINK Controller [1106:287e]
00:12.0 Ethernet controller [0200]: VIA Technologies, Inc. VT6102 [Rhine-II] [1106:3065] (rev 7c)
00:13.0 Host bridge [0600]: VIA Technologies, Inc. VT8237A Host Bridge [1106:337b]
00:13.1 PCI bridge [0604]: VIA Technologies, Inc. VT8237A PCI to PCI Bridge [1106:337a]
02:00.0 VGA compatible controller [0300]: nVidia Corporation GeForce 8400 GS [10de:0404] (rev a1)
04:04.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller [10ec:8185] (rev 20)
04:05.0 FireWire (IEEE 1394) [0c00]: Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link) [104c:8024]
80:01.0 Audio device [0403]: VIA Technologies, Inc. VT1708/A [Azalia HDAC] (VIA High Definition Audio Controller) [1106:3288] (rev 10)
```

```
james@james-desktop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: VT6102 [Rhine-II]
       vendor: VIA Technologies, Inc.
       physical id: 12
       bus info: pci@0000:00:12.0
       logical name: eth0
       version: 7c
       serial: 00:1d:60:8b:fa:63
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=via-rhine driverversion=1.4.3 latency=64 maxlatency=8 mingnt=3 module=via_rhine multicast=yes
  *-network
       description: Wireless interface
       product: RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 4
       bus info: pci@0000:04:04.0
       logical name: wmaster0
       version: 20
       serial: 00:12:0e:79:39:12
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=rtl8180 ip=192.168.2.6 latency=64 maxlatency=64 mingnt=32 module=rtl8180 multicast=yes wireless=IEEE 802.11bg
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 2a:56:b1:ac:df:65
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
```

Okay, that's already useful - I can see my actual model of wireless card is 8185, but Ubuntu is using the 8180 driver. I had a look on the Realtek site and there does appear to be a Linux driver specifically for the 8185 for Linux Kernel 2.6.22

---

### Post by cyclone5uk on 2008-12-17
Okay, so I've been to the Realtek site, downloaded the 8185 driver for Linux and have extracted the files from the tar.gz file. Now how do I update the driver in Ubuntu?

---

### Post by S_e_P_p on 2008-12-17
Hi,

I don't know at the moment how to get this driver working. Just to let you know how I got my WLAN driver working. Maybe it is also a solution for you.

I used the package ndiswrapper which will allow you to use the windows driver. 

You have to unarchive the .exe of your windows driver and implement the .inf into the ndiswrapper tool.

Here is a small howto:

Download the latest XP driver:
[ftp://210.51.181.211/cn/wlan/WinXP2K.zip]("ftp://210.51.181.211/cn/wlan/WinXP2K.zip")

open a terminal and type:

```
sudo apt-get install ndiswrapper-utils-1.9
```

Unzip the driver and go into this folder within a terminal.

Use the following code:
```
    
sudo ndiswrapper -i net8185.inf

sudo ndiswrapper -m

sudo ndiswrapper -mi

sudo ndiswrapper -ma

sudo modprobe ndiswrapper


```

Maybe you have to restart. Type ifconfig and control your wlan card and driver.

Via System --> Administration --> Windows driver you can also do this via a GUI (once you installed ndiswrapper) if you cant get this working via terminal. You have to implement the net8185.inf file.


Give it a try and let me know if you get it working.

Greets,
SePp

---

### Post by cyclone5uk on 2008-12-17
Thanks for the info. My only concern with your suggestion is this - why go down the ndiswrapper route using a Windows driver when a Linux driver is already available on the manufacturers website? Surely I should at least try and instal the Linux driver first (which I still don't know how to do)?

---

### Post by S_e_P_p on 2008-12-17
I investigated a little bit with google and most of the users using the Windows drivers. I really dont think there is any problem in using ndiswrapper as it is very common to use windows wlan drivers.

If you want to compile them please see here:

[http://willdaniels.co.uk/articles/howto-guides/10-howto/12-r8180-hardy](http://willdaniels.co.uk/articles/howto-guides/10-howto/12-r8180-hardy)

Greets
SePp

---

### Post by cyclone5uk on 2008-12-17
Many thanks S_e_P_p, the problem is now solved.

I followed your instructions and it worked perfectly. I'm showing a 60% signal strength and a speed test gave me my full 10mbps connection.

Thanks again.

---

### Post by S_e_P_p on 2008-12-18
> **cyclone5uk said:**
> Many thanks S_e_P_p, the problem is now solved.

I followed your instructions and it worked perfectly. I'm showing a 60% signal strength and a speed test gave me my full 10mbps connection.

Thanks again.

Hey cyclone5uk,

That's good. Which way worked ? ndiswrapper or the Linux driver?
Do not forget to mark the post as solved.

Greets,
SePp

---

### Post by cyclone5uk on 2008-12-18
I took your advice and used the ndiswrapper method.

---

