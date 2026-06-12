---
title: "Wireless Connection"
date: 2009-12-01
forum: New to Ubuntu
---

### Post by Rorouni on 2009-12-01
I dual booted Vista and Ubuntu. My laptop has one of those, "click a wireless button on the touch tab" in order to turn on and off the wireless connection. It is on when I boot vista, the connection is on. Unfortunately when I boot Ubuntu, the wirless connection is off, and my touch will not affect it. Is there any other way to turn it on?

---

### Post by Some Penguin on 2009-12-01
[http://linuxcommand.org/man_pages/iwconfig8.html](http://linuxcommand.org/man_pages/iwconfig8.html)

iwconfig wlan0 txpower off

is worth a try.

---

### Post by Rorouni on 2009-12-01
> **Some Penguin said:**
> [http://linuxcommand.org/man_pages/iwconfig8.html](http://linuxcommand.org/man_pages/iwconfig8.html)

iwconfig wlan0 txpower off

is worth a try.

Unfortunately, it did not work :(

---

### Post by rudy.b on 2009-12-01
So your wireless doesn't work at all in Ubuntu?

What are the results of the following two display commands:
```
$ sudo lshw -c network
```
```
$ iwconfig
```

---

### Post by dunkar70 on 2009-12-01
Laptops generally have separate hardware for the media/function buttons and the hardware they control. As a result, they require separate drivers. Do not judge the functionality of the WLAN card by the light on your laptop. In my case, the light is usually (but not always) off since I haven't been concerned about the drivers for the buttons.

Boot with a recent (9.04+) Ubuntu live CD. Look for the connection icon in the top right corner, next to the volume icon. This will tell you if Ubuntu will use your WLAN card without any special actions.

Single click on the connection icon. You should see a list of connection options. 

Verify if you can see any wireless networks.

Also check for a green icon that looks like an internal PC card. This would indicate that proprietary drivers are available for some of your hardware, possibly the WLAN card.

---

### Post by Rorouni on 2009-12-01
> **rudy.b said:**
> So your wireless doesn't work at all in Ubuntu?

What are the results of the following two display commands:
```
$ sudo lshw -c network
```


```
$ iwconfig
```


After ```
$ sudo lshw -c network
``` it asks me for my password but does not let me type it in. When I hit enter, I can type, but my password comes up incorrect, but I may be typing the wrong password. 

After ```
$ iwconfig
``` it says lo and eth0 both say no wireless extensions .

---

### Post by Rorouni on 2009-12-01
> **dunkar70 said:**
> Laptops generally have separate hardware for the media/function buttons and the hardware they control. As a result, they require separate drivers. Do not judge the functionality of the WLAN card by the light on your laptop. In my case, the light is usually (but not always) off since I haven't been concerned about the drivers for the buttons.

Boot with a recent (9.04+) Ubuntu live CD. Look for the connection icon in the top right corner, next to the volume icon. This will tell you if Ubuntu will use your WLAN card without any special actions.

Single click on the connection icon. You should see a list of connection options. 

Verify if you can see any wireless networks.

Also check for a green icon that looks like an internal PC card. This would indicate that proprietary drivers are available for some of your hardware, possibly the WLAN card.

I realize this. The top right indicator also informs me that the wireless connection is not being picked up. When I boot Vista though, I do receive connections. In addition, I even typed in my security information for my wireless network, but it does not seem to be working. Lastly, there is no green icon on the top bar...

---

### Post by rudy.b on 2009-12-01
> **Rorouni said:**
> After ```
$ sudo lshw -c network
``` it asks me for my password but does not let me type it in. When I hit enter, I can type, but my password comes up incorrect, but I may be typing the wrong password. 

Try this again, even though nothing shows up on the screen when you type your password it will still work as long as you type the password correctly.

---

### Post by Rorouni on 2009-12-01
> **rudy.b said:**
> Try this again, even though nothing shows up on the screen when you type your password it will still work as long as you type the password correctly.

You are right, and I was unaware because I am unexperienced. After putting it in, it gave me network informations which is too long to completely list (as I am on the forum from a different PC because I have no connection on my laptop). 

Under configuration...
Auto-negotiation=on
Broadcast=yes
Driver=tg3
Driver version=3.99
Firmware=sb v2.09
Latency=0
Link=no
Multi-cast=Yes
Port=twisted pair

Does that mean anything?

---

### Post by anewguy on 2009-12-01
Please also post back the outputs of:

lspci

- and -

lsusb


thanks!
Dave :)

---

### Post by Rorouni on 2009-12-02
> **anewguy said:**
> Please also post back the outputs of:

lspci

- and -

lsusb


thanks!
Dave :)

lspci:
00:00.0 Host bridge: ATI Technologies Inc RS690 Host Bridge
00:01.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (Internal gfx)
00:04.0 PCI bridge: ATI Technologies Inc Device 7914
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
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
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

lsusb:
Bus 004 Device 002: ID 08ff:2580 AuthenTec, Inc. AES2501 Fingerprint Sensor
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

---

### Post by rudy.b on 2009-12-02
> **Rorouni said:**
> 

Under configuration...
Auto-negotiation=on
Broadcast=yes
Driver=tg3
Driver version=3.99
Firmware=sb v2.09
Latency=0
Link=no
Multi-cast=Yes
Port=twisted pair

Does that mean anything?
That looks like your ethernet (wired) interface.  And judging from the outputs you posted for lspci and lsusb, I don't see any wireless interface information at all on your system.  Not really sure what's going on here, hopefully someone smarter than me will be able to help you. ;)

---

### Post by Rorouni on 2009-12-02
> **rudy.b said:**
> That looks like your ethernet (wired) interface.  And judging from the outputs you posted for lspci and lsusb, I don't see any wireless interface information at all on your system.  Not really sure what's going on here, hopefully someone smarter than me will be able to help you. ;)

I can connect to the Internet when I manually insert the Ethernet cord and connect it to my router. When I input all the commands though, I made sure the cable was not connected... I will repost all the information once more making sure the cable is not in... (It will be edited into this post). Anyway, thanks for trying. I appreciate it!

 lspci
00:00.0 Host bridge: ATI Technologies Inc RS690 Host Bridge
00:01.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (Internal gfx)
00:04.0 PCI bridge: ATI Technologies Inc Device 7914
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
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
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

lsusb
Bus 004 Device 002: ID 08ff:2580 AuthenTec, Inc. AES2501 Fingerprint Sensor
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

sudo lshw -c network
[sudo] password for rorouni: 
  *-network               
       description: Ethernet interface
       product: NetLink BCM5787M Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:10:00.0
       logical name: eth0
       version: 02
       serial: 00:1f:29:8c:08:17
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.99 duplex=full firmware=sb v2.09 latency=0 link=no multicast=yes port=twisted pair speed=100MB/s
       resources: irq:27 memory:d0000000-d000ffff

---

### Post by Dullstar on 2009-12-02
For whatever hardware you have, you could try ndiswrapper and the Windows driver.  I haven't tried ndiswrapper before, though, so I don't know how effective it would be.

---

### Post by wellsda41 on 2009-12-02
> **Rorouni said:**
> I dual booted Vista and Ubuntu. My laptop has one of those, "click a wireless button on the touch tab" in order to turn on and off the wireless connection. It is on when I boot vista, the connection is on. Unfortunately when I boot Ubuntu, the wirless connection is off, and my touch will not affect it. Is there any other way to turn it on?
I don't know what kind of laptop you have, but I had the same problem on my Dell Mini 10. It seems that Ubuntu 9.10 was released with a bug that prevents it from recognizing certain wireless controllers, Specifically those provided by Broadband.

I solved the problem by following the advice in an article at [www.ubuntumini.com]("http://www.ubuntumini.com") 
The article is listed on the left side of the page. To do what is advised you will have to connect to your router by ethernet wire, to access the net. The article is titled "Broadcom Wireless Connection Fix in Karmic".

---

### Post by anewguy on 2009-12-02
As posted by others, your outputs do not show a wireless adapter known to Ubuntu.  If the adapter is not known, there is no way to tell you what driver to use and how to install/use it.

This is rather curious - can you boot Windows and look in device manager and report back what it says there for your wireless adapter?

Normally with a laptop with built-in wireless, the adapter will be either a PCI device or internally connected to USB, so lspci (list pci devices) or lsusb (list usb devices) should have shown it.

Thanks

dave :)

---

### Post by Rorouni on 2009-12-02
> **anewguy said:**
> As posted by others, your outputs do not show a wireless adapter known to Ubuntu.  If the adapter is not known, there is no way to tell you what driver to use and how to install/use it.

This is rather curious - can you boot Windows and look in device manager and report back what it says there for your wireless adapter?

Normally with a laptop with built-in wireless, the adapter will be either a PCI device or internally connected to USB, so lspci (list pci devices) or lsusb (list usb devices) should have shown it.

Thanks

dave :)

All it says is that under Network Adapters that i have a Broadcom 802.11 b/g WLAN card 
under PCMCIA adapters, Ricoh R/RL/5C476(II) or Compatible CardBUS controller....
Thank You for trying though....

Edit: I think i found the driver, but now my laptop will not connect to the Internet through a wired connection...

Edit2: I think I got it working. I have no idea what i did, but it had to do with some HP driver that I installed and unpackaged... Thanks all for the help!

---

