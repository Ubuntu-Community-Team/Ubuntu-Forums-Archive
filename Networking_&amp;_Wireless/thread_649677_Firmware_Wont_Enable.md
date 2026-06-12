---
title: "Firmware Wont Enable"
date: 2007-12-25
forum: Networking &amp; Wireless
---

### Post by MrMJS on 2007-12-25
Hello,

I am new to Linux Ubuntu or any version or Linux for that matter :)  

I have a Acer laptop and I just installed Ubuntu, I was able to enable software modem drive but the firmware for braodco 43xx chipset family wont enable :( I get this message...

the software source for package bcm43xx-fwcutter is not enabled.

any thoughts on how to fix this?  Im trying to connect to my wireless router for internet, thank you for your help.

---

### Post by walkerk on 2007-12-25
post the results of:

```
dmesg | grep bcm43xx
```
```
lspci | grep Network
```
```
lshw -C network
```
```
iwconfig
```
```
iwlist scanning
```

---

### Post by MrMJS on 2007-12-25
i enter what you posted in the terminal (not sure if that what i was to do) but rload failed, its not seeing my wireless..

the card is a built in unit from acer.. i do have a slot for an external card too

---

### Post by walkerk on 2007-12-26
I would need you to copy the results of the above commands from the terminal window...

w/out this I don't know where to begin with helping you out...

---

### Post by MrMJS on 2007-12-26
sorry... i misread the post. here are the results..

**dmesg | grep bcm43xx**
[   15.092000] bcm43xx driver
[   22.012000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[   24.088000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[   46.140000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[   68.188000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[   90.240000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[  112.280000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[  134.348000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[  156.400000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[  278.444000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[  400.488000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.

**lspci | grep Network**
00:0b.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

**lshw -C network**
WARNING: you should run this program as super-user.
  *-network:0             
       description: Ethernet interface
       product: SiS900 PCI Fast Ethernet
       vendor: Silicon Integrated Systems [SiS]
       physical id: 4
       bus info: pci@0000:00:04.0
       logical name: eth0
       version: 91
       serial: 00:c0:9f:c7:3e:26
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sis900 driverversion=v1.08.10 Apr. 2 2006 ip=192.168.1.104 latency=173 maxlatency=11 mingnt=52 module=sis900 multicast=yes
  *-network:1 DISABLED
       description: Wireless interface
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: b
       bus info: pci@0000:00:0b.0
       logical name: eth1
       version: 02
       serial: 00:14:a4:33:dc:78
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       configuration: broadcast=yes driver=bcm43xx driverversion=2.6.22-14-generic latency=64 module=bcm43xx multicast=yes wireless=IEEE 802.11b/g


**iwconfig**
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:off/any  Nickname:"Broadcom 4318"
          Mode:Managed  Access Point: Invalid   
          RTS thr:off   Fragment thr:off
          Link Quality=0/100  Signal level=-256 dBm  Noise level=-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


**iwlist scanning**
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      No scan results

---

### Post by Josdell on 2007-12-26
You don't have the correct driver for your Wireless Card(bcm43xx.ko)  i think......... Don't shoot me if I'm wrong.
There are many guides for this
Here's Mine :) .

[http://ubuntuforums.org/showthread.php?t=650577&highlight=bcm43xx]("http://ubuntuforums.org/showthread.php?t=650577&highlight=bcm43xx")

---

### Post by MrMJS on 2007-12-26
that didnt seem to work for me

---

### Post by doublez on 2007-12-26
I had this problem before. Make sure your repositories are enabled. Go to Software Sources under system > administration. Make sure everything under "Ubuntu Software" and (if you want) "Third Party Software" is checked (I think you'll need an internet connection for this to work). Then some files will be downloaded then you should be able to enable your firmware.

---

### Post by MrMJS on 2007-12-27
that fixed it... thank you

---

