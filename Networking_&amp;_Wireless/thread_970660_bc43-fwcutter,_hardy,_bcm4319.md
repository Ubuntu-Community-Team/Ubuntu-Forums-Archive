---
title: "bc43-fwcutter, hardy, bcm4319"
date: 2008-11-04
forum: Networking &amp; Wireless
---

### Post by nerasezi on 2008-11-04
[FONT="Arial"]Hello there
I'm new to this forum. I've already searched the web to find a solution to my problem but it seems its such a weird one, nobody ever heard about it!
My laptop is a HP Pavilion DV8002EA with a Broadcom BCM4319 built-in wireless card. I've been using ubuntu 7.10 with the ndiswrapper flawlessy for more than a year and i just switched to Hardy 8.04.1 32bit. First thing i did was giving a try to the Restricted Hardware Drivers tool so that i could possibly find a painless solution to my wireless. No such a thing! Then i tried with the ndiswrapper but no luck. Last thing remaining after i plugged-in the ethernet cable, was the b43-fwcutter tool installed from the Terminal which actually extracted and fetched the driver required giving no errors. What then? it seems that nothing happened! I reboot the system like 10 times but nothing changes. I'm pretty sure that the device is now correctly seen by ubuntu cause after i iwconfig from terminal it shows that i have a wireless card. I even gave a shot to the network manager from gnome but it's like it doesn't exist at all. can anybody help me with some brilliant suggestion? I'm sure something's missing to the entire procedure.[/FONT]

---

### Post by Ayuthia on 2008-11-04
Can you post the results of lshw -C network?  It will help us see what your card is trying to use.

Is this an upgrade or a fresh install?

---

### Post by nerasezi on 2008-11-04
[FONT="Arial"]That's what i have:[/FONT]

  *-network:0             
       description: Network controller
       product: _BCM4311 [AirForce 54g]_ 802.11a/b/g PCI Express Transceiver
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@0000:06:02.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64 module=ssb
  *-network:1
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 6
       bus info: pci@0000:06:06.0
       logical name: eth0
       version: 10
       serial: 00:0f:b0:bc:11:15
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=128 link=no maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=10MB/s
  *-network DISABLED
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:14:a5:2e:48:4c
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g

[FONT="Arial"]Notice that the wireless card is still seen as a BCM4311. How that could be? Isn't bc43-fwcutter supposed to fetch the right driver for the corresponding device? I knew that worked before on my 7.10 ubuntu when i tried the bcm43xx-fwcutter tool[/FONT]

---

### Post by nerasezi on 2008-11-04
It's a clean install from 8.04.1 live CD on a wiped up ext3 partition

---

### Post by Ayuthia on 2008-11-04
You might try the following for the b43:
```
sudo modprobe -r b43 ssb ndiswrapper wl bcm43xx
sudo modprobe b43
sudo ifconfig wlan0 up
sudo iwlist scan
```

Since you have also installed ndiswrapper you can try the following for ndiswrapper:
```
sudo modprobe -r b43 ssb ndiswrapper wl bcm43xx
sudo modprobe ndiswrapper
sudo ifconfig wlan0 up
sudo iwlist scan
```

The system will determine whether you need the b43legacy module or the b43 module based on the chipset that you have.  The naming convention of the actual card can change over time so your card could have been a 4319 at one point, but the name is now 4311 for some reason.  If you take a look at lspci -nn, you will see that it is still 14e4:4319.  As for the firmware, it should use the correct version. 

The difference between 7.10 and 8.04 is that in the 2.6.24 kernel brought in the new b43 driver that replaces the bcm43xx version.  This new driver also uses the ssb driver which does cause a problem with ndiswrapper.  The ndiswrapper has to be installed before the ssb driver.  These are the big changes in 2.6.24 on upwards.

---

### Post by nerasezi on 2008-11-06
i've been trying what you told me, but no response by the system. I might have some hardware bug which i could fix in the next days.
Thanks for your help anyway. Appriciate

---

