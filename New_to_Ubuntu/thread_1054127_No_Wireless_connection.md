---
title: "No Wireless connection"
date: 2009-01-29
forum: New to Ubuntu
---

### Post by Monark on 2009-01-29
I'm at my gf's house. Her XP died on her so I installed on ubuntu on her laptop, only problem is, that it refuses to acknowledge any wireless connections. I know there are about 6 connections that I can see since I'm on one of them while I here at her house. So whats the deal its an issue since its basically impossible to run an ethernet cable to her room. So any idea why it wouldn't be working? Its an HP dv8000 if that helps.

---

### Post by avtolle on 2009-01-29
Do you know which wireless card her computer has? From her computer, access a terminal, and post the results of ```
lspci
```for starters.

---

### Post by DezSP on 2009-01-29
Also, are you using the latest version of Ubuntu (8.10)?

---

### Post by XanTrax on 2009-01-29
> **avtolle said:**
> Do you know which wireless card her computer has? From her computer, access a terminal, and post the results of ```
lspci
```for starters.

Also, please post the output of

```
sudo lshw -C network
```

---

### Post by Monark on 2009-01-29
00:14.6 Modem ATI Technologies Inc SB400 AC'97 Modem Controller (rev 02)
00:18.0 Host bridge: Advanced Micro Deviced [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Deviced [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Deviced [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Deviced [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon XPRESS 200M 5955 (PCIE)
06:02.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
06:04.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
06:04.2 FireWire (IEEE 1394): Texas Instruments  OHCI Compliant IEEE 1394 Host Controller
06:04.3 Mass storage controller: Texas Instruments PCIxx21 Integrated FlashMedia Controller
06:04.4 SD Host controller: Texas Instruments PCI6411/6421/6611/6621/7411/7421/7611/7621 Secure Digital Controller
06:06.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

That's for lspci

---

### Post by Monark on 2009-01-29
> **DezSP said:**
> Also, are you using the latest version of Ubuntu (8.10)?

Yes

---

### Post by XanTrax on 2009-01-29
> **Monark said:**
> 00:14.6 Modem ATI Technologies Inc SB400 AC'97 Modem Controller (rev 02)
00:18.0 Host bridge: Advanced Micro Deviced [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Deviced [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Deviced [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Deviced [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon XPRESS 200M 5955 (PCIE)
06:02.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
06:04.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
06:04.2 FireWire (IEEE 1394): Texas Instruments  OHCI Compliant IEEE 1394 Host Controller
06:04.3 Mass storage controller: Texas Instruments PCIxx21 Integrated FlashMedia Controller
06:04.4 SD Host controller: Texas Instruments PCI6411/6421/6611/6621/7411/7421/7611/7621 Secure Digital Controller
06:06.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

That's for lspci

This shows us

> 06:02.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

You are using a Broadcom BCM4318 wireless card.  Please now post the output of 

```
sudo lshw -C network
```

and then post the output of

```
sudo dmesg | grep -i bcm43
```

---

### Post by Monark on 2009-01-29
> 
laura@laura-laptop:~$ sudo lshw -C network
[sudo] password for laura: 
  *-network:0             
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@0000:06:02.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64 module=ssb
  *-network:1 DISABLED
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 6
       bus info: pci@0000:06:06.0
       logical name: eth0
       version: 10
       serial: 00:0f:b0:bd:42:66
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=128 link=no maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=10MB/s
  *-network:0 DISABLED
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:14:a5:2c:fa:57
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 3
       logical name: pan0
       serial: 5e:c8:7b:52:cb:0b
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
laura@laura-laptop:~$ 


let me get the other part hold on.

---

### Post by XanTrax on 2009-01-29
I made a mistake.  The command should be

```
sudo dmesg | grep -i b43
```

---

### Post by Monark on 2009-01-29
> **XanTrax said:**
> I made a mistake.  The command should be

```
sudo dmesg | grep -i b43
```

Hey, How do I make the vertical line in the terminal?

---

### Post by avtolle on 2009-01-29
The pipe symbol is, on my keyboard, the shifted \ (backslash) key at the end of the second row on the main keyboard, right above the Enter key. Take a look around and you'll find it. :-)

---

### Post by Monark on 2009-01-29
> **avtolle said:**
> The pipe symbol is, on my keyboard, the shifted \ (backslash) key at the end of the second row on the main keyboard, right above the Enter key. Take a look around and you'll find it. :-)

I didn't know, it just looked like the big semi colon to me, lol.

---

### Post by Monark on 2009-01-29
> laura@laura-laptop:~$ sudo dmesg | grep -i b43
[    3.041664] b43-pci-bridge 0000:06:02.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[   14.478374] b43-phy0: Broadcom 4318 WLAN found
[   33.957013] input: b43-phy0 as /devices/virtual/input/input8
[   34.048079] firmware: requesting b43/ucode5.fw
[   34.118987] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
[   34.119005] b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the latest firmware (version 4).
[   34.184402] input: b43-phy0 as /devices/virtual/input/input9
[   34.248065] firmware: requesting b43/ucode5.fw
[   34.254138] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
[   34.254157] b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the latest firmware (version 4).
[  117.845230] input: b43-phy0 as /devices/virtual/input/input10
[  117.908090] firmware: requesting b43/ucode5.fw
[  117.914228] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
[  117.914249] b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the latest firmware (version 4).
[  117.990371] input: b43-phy0 as /devices/virtual/input/input11
[  118.048110] firmware: requesting b43/ucode5.fw
[  118.067780] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
[  118.067799] b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the latest firmware (version 4).
laura@laura-laptop:~$ 


Thats the other thing you asked for.

---

### Post by XanTrax on 2009-01-29
> **Monark said:**
> Thats the other thing you asked for.

Alright, making some headway.  I like users to understand what they are doing instead of giving them carbon copy material.

**lspci** lists the current connected PCI devices to the computer
**lshw** lists the current connected hardware devices and displays some extra information, such as whether the device is claimed or unclaimed by a driver or disabled.

Running lshw -C network says we want to run the lshw command and display the Network class.  -C indicates to specify a class and network is the class.

dmesg is the kernel buffer messages.  This is pretty useful in diagnosing problems.  As you can see, dmesg has returned the exact information we need.  Your firmware is missing.

So, lets run these commands:

```

sudo apt-get install b43-fwcutter

```

This should ask you if you want to fetch the firmware.  Say yes.  In an instance where it doesnt, then run this command

```

sudo /usr/share/b43-fwcutter/install_bcm43xx_firmware.sh

```

Next, run these commands
```

sudo modprobe -r b43 ssb
sudo modprobe b43
sudo ifconfig wlan0 up
sudo iwlist scan

```

modprobe -r will remove the b43 module
modprobe b43 will install the module again
ifconfig wlan0 up will set the wireless device wlan0 to active state
iwlist scan will scan for wireless routers or access points.

---

### Post by gymophett on 2009-01-29
> **Monark said:**
> Hey, How do I make the vertical line in the terminal?

Just copy and paste it.

---

### Post by XanTrax on 2009-01-29
> **gymophett said:**
> Just copy and paste it.

Copy and pasting doesnt allow learning.  Now he learned what the big semi-colon looking thing was above his enter key :p.

---

### Post by Monark on 2009-01-29
> laura@laura-laptop:~$ sudo apt-get install b43-fwcutter 
Reading package lists... Done 
Building dependency tree       
Reading state information... Done 
E: Couldn't find package b43-fwcutter 
laura@laura-laptop:~$ sudo /usr/share/b43-fwcutter/install_bcm43xx_firmware.sh 
sudo: /usr/share/b43-fwcutter/install_bcm43xx_firmware.sh: command not found 
laura@laura-laptop:~$ sudo modprobe -r b43 ssb 
laura@laura-laptop:~$ sudo modprobe b43 
laura@laura-laptop:~$ sudeo ifconfig wlan0 up 
bash: sudeo: command not found 
laura@laura-laptop:~$ sudo iwlist scan 
lo        Interface doesn't support scanning. 

eth0      Interface doesn't support scanning. 

pan0      Interface doesn't support scanning. 

wmaster0  Interface doesn't support scanning. 

wlan0     Interface doesn't support scanning : Network is down 


That's what happened when I ran those last commands.

---

### Post by Thunder_Storm on 2009-01-29
Greetings all!

I'm here on the same issue, so I thought it will make sense not starting a new post.

I've installed Ubuntu 8.10 64x on my Aser Aspire 5715Z and the wireless doesn't seem to work.

the output for:
> lspci
(the network adapters part) is: 
> 05:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express (rev 02)
06:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)

and for:
> sudo lshw -C network

is:
> *-network               
       description: Ethernet interface
       product: NetLink BCM5906M Fast Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: 02
       serial: 00:1e:ec:56:51:55
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.94 duplex=full ip=192.168.1.101 latency=0 link=yes module=tg3 multicast=yes port=twisted pair speed=100MB/s
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:06:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix cap_list
       configuration: latency=0
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 56:1e:37:82:a2:bf
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

Thank you all! :guitar:

---

### Post by chamber on 2009-01-29
> **Thunder_Storm said:**
> Greetings all!

I'm here on the same issue, so I thought it will make sense not starting a new post.

I've installed Ubuntu 8.10 64x on my Aser Aspire 5715Z and the wireless doesn't seem to work.

the output for:

(the network adapters part) is: 


and for:


is:


Thank you all! :guitar:

You're better off starting a new thread, it gets confusing when trying to give advice to 2 people who may not even be experiencing the same problems.

---

### Post by XanTrax on 2009-01-29
> **Monark said:**
> That's what happened when I ran those last commands.

sudo apt-get install b43-fwcutter did not find the installation candidate?

Thats really weird.  Alright, instead of

sudo apt-get install b43-fwcutter

Download:

[http://mirror.mcs.anl.gov/pub/ubuntu/pool/main/b/b43-fwcutter/b43-fwcutter_011-4ubuntu1_i386.deb](http://mirror.mcs.anl.gov/pub/ubuntu/pool/main/b/b43-fwcutter/b43-fwcutter_011-4ubuntu1_i386.deb)

Then, double click it on the desktop.  Then, execute all the commands I stated earlier besides the "sudo apt-get install b43-fwcutter"

---

### Post by Monark on 2009-01-29
> laura@laura-laptop:~$ sudo apt-get install b43-fwcutter
[sudo] password for laura: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
b43-fwcutter is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up b43-fwcutter (1:011-4ubuntu1) ...
--2009-01-29 07:46:36--  [http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o](http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o)
Resolving downloads.openwrt.org... failed: Name or service not known.
wget: unable to resolve host address `downloads.openwrt.org'
dpkg: error processing b43-fwcutter (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 b43-fwcutter
E: Sub-process /usr/bin/dpkg returned an error code (1)
laura@laura-laptop:~$ sudo /usr/share/b43-fwcutter/install_bcm43xx_firmware.sh
--2009-01-29 07:47:51--  [http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o](http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o)
Resolving downloads.openwrt.org... failed: Name or service not known.
wget: unable to resolve host address `downloads.openwrt.org'
laura@laura-laptop:~$ sudo modprobe -r b43 ssb
laura@laura-laptop:~$ sudo modprobe b43
laura@laura-laptop:~$ sudo ifconfig wlan0 up
SIOCSIFFLAGS: No such file or directory
laura@laura-laptop:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

pan0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Interface doesn't support scanning : Network is down

laura@laura-laptop:~$ 








laura@laura-laptop:~$ sudo apt-get install b43-fwcutter 
[sudo] password for laura: 
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable) 
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it? 
laura@laura-laptop:~$ sudo /usr/share/b43-fwcutter/install_bcm43xx_firmware.sh 
--2009-01-29 13:03:13--  [http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o](http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o) 
Resolving downloads.openwrt.org... 195.56.146.238 
Connecting to downloads.openwrt.org|195.56.146.238|:80... connected. 
HTTP request sent, awaiting response... 200 OK 
Length: 652866 (638K) [application/x-object] 
Saving to: `wl_apsta-3.130.20.0.o' 

100%[======================================>] 652,866      352K/s   in 1.8s    

2009-01-29 13:03:15 (352 KB/s) - `wl_apsta-3.130.20.0.o' saved [652866/652866] 

--2009-01-29 13:03:15--  [http://mirror2.openwrt.org/sources/broadcom-wl-4.150.10.5.tar.bz2](http://mirror2.openwrt.org/sources/broadcom-wl-4.150.10.5.tar.bz2) 
Resolving mirror2.openwrt.org... 88.198.39.176 
Connecting to mirror2.openwrt.org|88.198.39.176|:80... connected. 
HTTP request sent, awaiting response... 200 OK 
Length: 3888794 (3.7M) [application/x-tar] 
Saving to: `broadcom-wl-4.150.10.5.tar.bz2' 

100%[======================================>] 3,888,794    471K/s   in 7.6s    

2009-01-29 13:03:23 (500 KB/s) - `broadcom-wl-4.150.10.5.tar.bz2' saved [3888794/3888794] 

This file is recognised as: 
  ID         :  FW10 
  filename   :  wl_apsta.o 
  version    :  295.14 
  MD5        :  e08665c5c5b66beb9c3b2dd54aa80cb3 
Extracting b43legacy/ucode2.fw 
Extracting b43legacy/ucode4.fw 
Extracting b43legacy/ucode5.fw 
Extracting b43legacy/ucode11.fw 
Extracting b43legacy/pcm4.fw 
Extracting b43legacy/pcm5.fw 
Extracting b43legacy/a0g0bsinitvals2.fw 
Extracting b43legacy/b0g0bsinitvals5.fw 
Extracting b43legacy/a0g0initvals5.fw 
Extracting b43legacy/a0g1bsinitvals5.fw 
Extracting b43legacy/a0g0initvals2.fw 
Extracting b43legacy/a0g1initvals5.fw 
Extracting b43legacy/b0g0bsinitvals2.fw 
Extracting b43legacy/b0g0initvals5.fw 
Extracting b43legacy/b0g0initvals2.fw 
Extracting b43legacy/a0g0bsinitvals5.fw 
This file is recognised as: 
  ID         :  FW13 
  filename   :  wl_apsta_mimo.o 
  version    :  410.2160 
  MD5        :  cb8d70972b885b1f8883b943c0261a3c 
Extracting b43/pcm5.fw 
Extracting b43/pcm4.fw 
Extracting b43/ucode15.fw 
Extracting b43/ucode14.fw 
Extracting b43/ucode13.fw 
Extracting b43/ucode11.fw 
Extracting b43/ucode9.fw 
Extracting b43/ucode5.fw 
Extracting b43/ucode4.fw 
Extracting b43/lp0bsinitvals15.fw 
Extracting b43/lp0initvals15.fw 
Extracting b43/lp0bsinitvals14.fw 
Extracting b43/lp0initvals14.fw 
Extracting b43/a0g1bsinitvals13.fw 
Extracting b43/a0g1initvals13.fw 
Extracting b43/b0g0bsinitvals13.fw 
Extracting b43/b0g0initvals13.fw 
Extracting b43/lp0bsinitvals13.fw 
Extracting b43/lp0initvals13.fw 
Extracting b43/n0absinitvals11.fw 
Extracting b43/n0bsinitvals11.fw 
Extracting b43/n0initvals11.fw 
Extracting b43/a0g1bsinitvals9.fw 
Extracting b43/a0g0bsinitvals9.fw 
Extracting b43/a0g1initvals9.fw 
Extracting b43/a0g0initvals9.fw 
Extracting b43/b0g0bsinitvals9.fw 
Extracting b43/b0g0initvals9.fw 
Extracting b43/a0g1bsinitvals5.fw 
Extracting b43/a0g0bsinitvals5.fw 
Extracting b43/a0g1initvals5.fw 
Extracting b43/a0g0initvals5.fw 
Extracting b43/b0g0bsinitvals5.fw 
Extracting b43/b0g0initvals5.fw 
Extracting b43/a0g0bsinitvals4.fw 
Extracting b43/a0g0initvals4.fw 
Extracting b43/b0g0bsinitvals4.fw 
Extracting b43/b0g0initvals4.fw 
laura@laura-laptop:~$ sudo modprobe -r b43 ssb 
laura@laura-laptop:~$ sudo modprobe b43 
laura@laura-laptop:~$ sudo ifconfig 
eth0      Link encap:Ethernet  HWaddr 00:0f:b0:bd:42:66  
          inet addr:192.168.1.105  Bcast:192.168.1.255  Mask:255.255.255.0 
          inet6 addr: fe80::20f:b0ff:febd:4266/64 Scope:Link 
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
          RX packets:40720 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:27254 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:61419676 (61.4 MB)  TX bytes:1689107 (1.6 MB) 
          Interrupt:22 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:582 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:582 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0 
          RX bytes:37912 (37.9 KB)  TX bytes:37912 (37.9 KB) 

wlan0     Link encap:Ethernet  HWaddr 00:14:a5:2c:fa:57  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 

wmaster0  Link encap:UNSPEC  HWaddr 00-14-A5-2C-FA-57-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 

laura@laura-laptop:~$ sudo ifconfig wlan0 up 
laura@laura-laptop:~$ sudo iwlist scan 
lo        Interface doesn't support scanning. 

eth0      Interface doesn't support scanning. 

pan0      Interface doesn't support scanning. 

wmaster0  Interface doesn't support scanning. 

wlan0     No scan results 
 
laura@laura-laptop:~$ 

 there u go

---

### Post by XanTrax on 2009-01-29
Please reboot and do:

the first command will ping google 4 times, wait for it to finish

```

ping -c 4 google.com
sudo dmesg | grep -i b43
sudo modprobe -l | grep -i b43
sudo lshw -C network

```

and post the output here.

---

### Post by Monark on 2009-01-29
Ok so what I did was I took her laptop to her basement and connected it to an Ethernet connection. I installed that thing you told me to. I downloaded 245 updates, and now it works for her. Thanks guys.

---

### Post by XanTrax on 2009-01-29
> **Monark said:**
> Ok so what I did was I took her laptop to her basement and connected it to an Ethernet connection. I installed that thing you told me to. I downloaded 245 updates, and now it works for her. Thanks guys.

Welcome :p. What exactly fixed it, do you know?

---

### Post by Monark on 2009-01-29
> **XanTrax said:**
> Welcome :p. What exactly fixed it, do you know?

I don't know for sure since everything happened basically at the same time, and it didn't work until I restarted the computer. But I think it was the thing you asked me to download, but it just wouldn't install unless I was online.

---

### Post by minsf on 2009-01-30
indeed, i think the b43-fwcutter needs to be online when installed, as it doanloads the restricted broadcom driver and then cut the firmware, or something along this line.

---

