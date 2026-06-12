---
title: "Cannot enable wireless"
date: 2008-08-14
forum: Networking &amp; Wireless
---

### Post by Mediocraties@gmail.com on 2008-08-14
Hey,
    I installed Ubuntu 7.10 about 6 months ago, and had no problem with my wireless. I updated to 8.04 when it came out - still no problems. I moved about a month and a half ago, and started using a wired network. The other day I tried to use wireless, and it failed to connect.

    When I left-click on the network icon in the toolbar, the "enable wireless" option is grayed out (like when you right click normally and an option like "paste" is inaccessible). When I used the command lshw, it recognized my wireless card, but says that it's disabled.
[COLOR="Red"]*-network DISABLED[/COLOR]
                description: Wireless interface
                product: PRO/Wireless 4965 AG or AGN Network Connection
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:06:00.0
                logical name: wmaster0
                version: 61
                serial: 00:13:e8:af:00:f7
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress cap_list logical ethernet physical wireless
                configuration: broadcast=yes driver=iwl4965 latency=0 module=iwl4965 multicast=yes wireless=IEEE 802.11a

I tried re-installing the operating system. This didn't fix the problem. Anyone have an idea what's going on?

---

### Post by pytheas22 on 2008-08-14
Does this change anything:
```

sudo rmmod iwl4965
sudo modprobe iwl4965
sudo ifconfig wlan0 up
sudo ifconfig eth1 up
```

---

### Post by Mediocraties@gmail.com on 2008-08-14
Here's what I got when I tried:

evan@evan-laptop:~$ sudo ifconfig wlan0 up
SIOCSIFFLAGS: No such device
evan@evan-laptop:~$ sudo ifconfig wlan0 up
SIOCSIFFLAGS: No such device
evan@evan-laptop:~$ sudo ifconfig eth1 up
eth1: ERROR while getting interface flags: No such device

Any thoughts? Thanks!

---

### Post by pytheas22 on 2008-08-14
>  Here's what I got when I tried:

evan@evan-laptop:~$ sudo ifconfig wlan0 up
SIOCSIFFLAGS: No such device
evan@evan-laptop:~$ sudo ifconfig wlan0 up
SIOCSIFFLAGS: No such device
evan@evan-laptop:~$ sudo ifconfig eth1 up
eth1: ERROR while getting interface flags: No such device

Any thoughts? Thanks! 

You ran these commands first too, right:
```

sudo rmmod iwl4965
sudo modprobe iwl4965
```

Also, please post:
```

lspci -nn
dmesg | grep -e eth -e wlan -e iwl
```

so that we can know your exact chipset number.  I'm not sure what's going on but it seems strange.

Finally, are you sure there's not a switch on your computer that you need to enable to turn the wireless on?  I know it seems like a dumb question, but I just want to make sure...

---

### Post by Mediocraties@gmail.com on 2008-08-15
Yep, I ran sudo rmmod iwl4965 and sudo modprobe iwl4965 first.

Here are the two outputs:
evan@evan-laptop:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub [8086:2a00] (rev 0c)
00:01.0 PCI bridge [0604]: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port [8086:2a01] (rev 0c)
00:1a.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 [8086:2834] (rev 03)
00:1a.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 [8086:2835] (rev 03)
00:1a.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 [8086:283a] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation 82801H (ICH8 Family) HD Audio Controller [8086:284b] (rev 03)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 [8086:283f] (rev 03)
00:1c.1 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 [8086:2841] (rev 03)
00:1c.2 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 [8086:2843] (rev 03)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 [8086:2830] (rev 03)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 [8086:2831] (rev 03)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 [8086:2832] (rev 03)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 [8086:2836] (rev 03)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev f3)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller [8086:2815] (rev 03)
00:1f.1 IDE interface [0101]: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller [8086:2850] (rev 03)
00:1f.2 SATA controller [0106]: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller [8086:2829] (rev 03)
00:1f.3 SMBus [0c05]: Intel Corporation 82801H (ICH8 Family) SMBus Controller [8086:283e] (rev 03)
01:00.0 VGA compatible controller [0300]: nVidia Corporation G86M [GeForce 8400M GT] [10de:0426] (rev a1)
02:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8055 PCI-E Gigabit Ethernet Controller [11ab:4363] (rev 13)
06:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 4965 AG or AGN Network Connection [8086:4229] (rev 61)
08:03.0 CardBus bridge [0607]: Texas Instruments PCIxx12 Cardbus Controller [104c:8039]
08:03.1 FireWire (IEEE 1394) [0c00]: Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller [104c:803a]
08:03.2 Mass storage controller [0180]: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD) [104c:803b]

and

evan@evan-laptop:~$ dmesg | grep -e eth -e wlan -e iwl
[   17.607017] Driver 'sd' needs updating - please use bus_type methods
[   25.603412] sky2 eth0: addr 00:1a:80:1c:30:3e
[   26.600697] Driver 'sr' needs updating - please use bus_type methods
[   26.638762] iwl4965: Intel(R) Wireless WiFi Link 4965AGN driver for Linux, 1.2.25
[   26.638766] iwl4965: Copyright(c) 2003-2007 Intel Corporation
[   26.638976] iwl4965: Detected Intel Wireless WiFi Link 4965AGN
[   26.793814] wmaster0: Selected rate control algorithm 'iwl-4965-rs'
[   32.744396] iwl4965: Radio disabled by HW RF Kill switch
[   33.937219] sky2 eth0: enabling interface
[   35.916676] sky2 eth0: Link is up at 100 Mbps, full duplex, flow control both
[   45.651333] eth0: no IPv6 routers present
[ 2563.293028] iwl4965: Intel(R) Wireless WiFi Link 4965AGN driver for Linux, 1.2.25
[ 2563.293033] iwl4965: Copyright(c) 2003-2007 Intel Corporation
[ 2563.293569] iwl4965: Detected Intel Wireless WiFi Link 4965AGN
[ 2563.337530] wmaster0: Selected rate control algorithm 'iwl-4965-rs'
[ 2563.360072] iwl4965: Radio disabled by HW RF Kill switch
[ 2563.780662] iwl4965: Radio disabled by HW RF Kill switch
[ 2565.716141] iwl4965: Radio disabled by HW RF Kill switch
[ 2566.409272] iwl4965: Radio disabled by HW RF Kill switch
[ 2601.230382] iwl4965: Intel(R) Wireless WiFi Link 4965AGN driver for Linux, 1.2.25
[ 2601.230387] iwl4965: Copyright(c) 2003-2007 Intel Corporation
[ 2601.230935] iwl4965: Detected Intel Wireless WiFi Link 4965AGN
[ 2601.272623] wmaster0: Selected rate control algorithm 'iwl-4965-rs'
[ 2601.290152] iwl4965: Radio disabled by HW RF Kill switch
[ 2601.296560] iwl4965: Radio disabled by HW RF Kill switch
[ 2601.762232] iwl4965: Radio disabled by HW RF Kill switch

The switch is and was at the time definitely in the on position, but I switched it on and off a few times, and I'm not entirely sure that it's not broken. I noticed the "on" light isn't coming on (though when it still worked and I disabled wireless using the network icon menu instead of the switch, the light would go off even if the switch was in the on position). Maybe "Radio disabled by HW RF Kill switch" means it's broken in the off position? Also "Driver 'sr' needs updating - please use bus_type methods" might be the problem? If there's any other obvious potential fixes, let me know, because I honestly don't know all that much about the problem. 

Thanks again.

---

### Post by jualin on 2008-08-15
When you disconnect the ethernet cable are you able to connect to a wireless network?

---

### Post by Mediocraties@gmail.com on 2008-08-15
Nope.

---

### Post by pytheas22 on 2008-08-15
Yeah, I think there may be a problem with the button--the "radio disabled by hardware" usually means that the wireless is switched off by the external switch.  If you have Windows on the same machine, does the wireless work there?  If not, maybe you can check in BIOS to see if there's a way to toggle it on and off, or force it to be always on.

---

