---
title: "can't enable network drivers in hardy"
date: 2008-10-13
forum: Networking &amp; Wireless
---

### Post by skier_chick on 2008-10-13
I'm pretty new at this, but here's the story: 

I have a Dell Inspiron 1501 that came with Vista.  A friend set me up to dual boot to Ubuntu 7.10 and XP, but this past summer the wireless stopped working. (randomly, as far as I can tell)  I recently installed Hardy, but I still can't get it to see a network connection at all.  When I tried to enable the drivers (System->Administration->Hardware Drivers), the only one there was a graphics driver. (which, incidentally, I couldn't enable because I couldn't connect)

Any thoughts?

---

### Post by pytheas22 on 2008-10-13
What's the output of:
```

lspci -nn
lshw -C Network
dmesg | grep radio
uname -m
```

It could be a driver problem, or an issue with the radio turned off in the wireless card for some reason.  Those commands will help to track down the problem.

---

### Post by skier_chick on 2008-10-17
is there any way I could check that from XP?  See, I'm currently running windows because I can access wireless from here.  It's just in ubuntu that I can't.

---

### Post by pytheas22 on 2008-10-18
It would be best to see that information from Linux.  Even though you don't have any Internet connection currently available in Ubuntu, you can still run those commands, highlight their output, right-click and select copy, paste them into a text file (go to Applications>Accessories>Text Editor to open a blank file), save the text file to a USB drive or CD, and from there transfer it to a computer with Internet access, so that you can post the output of those commands.

If you really can't do that, I guess you could get some of that information from XP, but I'd have to look at an XP computer myself to tell you exactly where to look--I haven't used Windows in so long that I'm not sure.  Basically the most critical piece of information we need is to know exactly which wireless chipset you use, which is probably in the control panel>device manager stuff somewhere.

---

### Post by skier_chick on 2008-10-18
Ok, I reinstalled and here are the commands followed by what I got for them (hope this means more to you than to me!):

lspci -nn
00:00.0 Host bridge [0600]: ATI Technologies Inc RS480 Host Bridge [1002:5950] (rev 10)
00:01.0 PCI bridge [0604]: ATI Technologies Inc RS480 PCI Bridge [1002:5a3f]
00:05.0 PCI bridge [0604]: ATI Technologies Inc RS480 PCI Bridge [1002:5a37]
00:06.0 PCI bridge [0604]: ATI Technologies Inc RS480 PCI Bridge [1002:5a38]
00:12.0 SATA controller [0106]: ATI Technologies Inc SB600 Non-Raid-5 SATA [1002:4380]
00:13.0 USB Controller [0c03]: ATI Technologies Inc SB600 USB (OHCI0) [1002:4387]
00:13.1 USB Controller [0c03]: ATI Technologies Inc SB600 USB (OHCI1) [1002:4388]
00:13.2 USB Controller [0c03]: ATI Technologies Inc SB600 USB (OHCI2) [1002:4389]
00:13.3 USB Controller [0c03]: ATI Technologies Inc SB600 USB (OHCI3) [1002:438a]
00:13.4 USB Controller [0c03]: ATI Technologies Inc SB600 USB (OHCI4) [1002:438b]
00:13.5 USB Controller [0c03]: ATI Technologies Inc SB600 USB Controller (EHCI) [1002:4386]
00:14.0 SMBus [0c05]: ATI Technologies Inc SBx00 SMBus Controller [1002:4385] (rev 14)
00:14.1 IDE interface [0101]: ATI Technologies Inc SB600 IDE [1002:438c]
00:14.2 Audio device [0403]: ATI Technologies Inc SBx00 Azalia [1002:4383]
00:14.3 ISA bridge [0601]: ATI Technologies Inc SB600 PCI to LPC Bridge [1002:438d]
00:14.4 PCI bridge [0604]: ATI Technologies Inc SBx00 PCI to PCI Bridge [1002:4384]
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map [1022:1101]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller [1022:1102]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103]
01:05.0 VGA compatible controller [0300]: ATI Technologies Inc RS485 [Radeon Xpress 1100 IGP] [1002:5975]
05:00.0 Network controller [0280]: Broadcom Corporation BCM94311MCG wlan mini-PCI [14e4:4311] (rev 01)
08:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)
08:01.0 SD Host controller [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter [1180:0822] (rev 19)
08:01.1 System peripheral [0880]: Ricoh Co Ltd R5C843 MMC Host Controller [1180:0843] (rev 01)


lshw -C Network
  *-network               
       description: Network controller
       product: BCM94311MCG wlan mini-PCI
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0 module=ssb
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth0
       version: 02
       serial: 00:1c:23:82:48:40
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=b44 driverversion=2.0 latency=64 module=ssb multicast=yes
  *-network DISABLED
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:19:7e:cc:8a:a8
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g


dmesg | grep radio gave me nothing, until I used a 1, l, or I, then:
Usage: dmesg [-c] [-n level] [-s bufsize]


uname -m
i686

---

### Post by Ayuthia on 2008-10-18
If you have a working wired connection, try installing b43-fwcutter from Synaptic or from the Terminal:
```
sudo apt-get install b43-fwcutter
```It will ask you if you want it to find the firmware for you, select yes and it will download the firmware for you.  I think that it will ask you to reboot and things should work after that.

---

### Post by pytheas22 on 2008-10-19
Thanks for the information.  If you have a working connection, doing what Ayuthia recommends in the post above would probably work, but I think you don't have any connection available, so you can follow these steps to get the necessary files installed without being online.

1. on a computer with Internet access, download [this file]("http://burnthesorbonne.com/files/b43_firmware.tar.gz") and save it to a USB stick or CD.

2. transfer the file to your Ubuntu computer and save it to your desktop there.

3. open a terminal and run these commands:
```

cd ~/Desktop
sudo cp b43_firmware.tar.gz /lib/firmware
cd /lib/firmware
sudo tar -xzvf b43_firmware.tar.gz
```

Then reboot.  After rebooting, you should be able to see a list of available wireless networks by left-clicking the Network Manager icon (in the top-right corner of your screen) and connect by selecting one.  If you still can't see any wireless networks, please post the output of:
```

sudo iwlist scan
dmesg | grep -e b43 -e wlan
lshw -C Network
```

---

### Post by skier_chick on 2008-10-19
fabulous!  I actually did find a place to plug in and got what I needed that way.  Thanks so much for your help!

---

