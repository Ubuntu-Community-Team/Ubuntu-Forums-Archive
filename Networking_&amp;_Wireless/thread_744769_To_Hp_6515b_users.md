---
title: "To Hp 6515b users"
date: 2008-04-03
forum: Networking &amp; Wireless
---

### Post by kjman83 on 2008-04-03
Hi I luckly installed ubuntu 8.04

However,

I can't turn on the wireless of my laptop (hp 6515b).

It doesn't work after installing ubuntu.

Is there anyone who can see the BLUE light for wireless? (The user must know about blue light)

Please tell me..

---

### Post by dmizer on 2008-04-04
i'm terribly sorry, why must i know about the blue light in order to help you?

please post the output of the following command:
```
lspci
```

  this will tell me what chipset you are using for your wireless adapter.  once i know the chipset, we can figure out what technique to use so you can turn on your wireless adapter.

---

### Post by kjman83 on 2008-04-04
What a kind of you. Thank you

I did lspci

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


Does it seems to be ok?

---

### Post by dmizer on 2008-04-05
all this tells me is what chipset your card is using.  this line:
```
30:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 02)
```
lists your wireless adapter and chipset information.  specifically BCM94311MCG.  now what i usually do with these is search in google with the chipset like so:
[solved] BCM94311MCG site:ubuntuforums.org

which reveals the following potentially helpful links:
[http://ubuntuforums.org/showthread.php?t=684359](http://ubuntuforums.org/showthread.php?t=684359)
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

post if this works for you, or if you have trouble.

---

### Post by kjman83 on 2008-04-07
It still doesn't work.
I really did well about the manual. 
I was happy at the time.
but now I even can't see the wireless network


Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 02)
my laptop is hp 6515b in 8.04 ubuntu

It's my card..
The important thing is that I can't turn on the wireless lan.
Because The wireless switch is a kind of touchpad switch(useless) not analogtic switch(I prefer analog). The switch is not working in ubuntu. It did work well in Vista.

I really want to turn on my wireless.
I really want to see the blue light.

---

### Post by kjman83 on 2008-04-07
really Thank you 
Now I can see the blue light .
wireless does work.
I can't use though.
But I can see lots of networks

Thank you

---

### Post by dmizer on 2008-04-07
okay ... the network you are trying to connect to, is it open or is there encryption like wep or wpa?

---

