---
title: "Ubuntu 7.04 - Wirelesse connection works only for few minutes"
date: 2007-08-13
forum: Networking &amp; Wireless
---

### Post by woozy on 2007-08-13
Hello, I have a Toshiba Satellite m70-122 running Ubuntu 7.04. I use several wireless networks and I don't have any problems...except with one! Every time I connect to that network It only works for a few minutes - not more than five - and then I still having the indication "connected" in the network manager but I can't access Internet or any other computer in the network. Any suggestions? 
I know the problem is not in the network because my friends use it at the same time (with windows) without any problems and I also connect to that network with windows without any problem...

---

### Post by walkerk on 2007-08-13
> **woozy said:**
> Hello, I have a Toshiba Satellite m70-122 running Ubuntu 7.04. I use several wireless networks and I don't have any problems...except with one! Every time I connect to that network It only works for a few minutes - not more than five - and then I still having the indication "connected" in the network manager but I can't access Internet or any other computer in the network. Any suggestions? 
I know the problem is not in the network because my friends use it at the same time (with windows) without any problems and I also connect to that network with windows without any problem...

I had a similar issue using Network-Manager in 7.04. I removed it and install [WICD]("http://wicd.sourceforge.net").. after which my issues were gone. Not sure if it will solve your problems but you can give it a try.

It's hard to understand where to start with troubleshooting seeing how you said that you use several wireless networks (in Linux?) without issues as well as this network working well under Windows..

---

### Post by woozy on 2007-08-14
Yes, I use several networks with Linux without any problem... 
Thank you for the tip, but WICD didn't solve my problem. With WICD it simply connects but no Internet or network access...

---

### Post by kevdog on 2007-08-14
We are going to need more details about your system, such as wireless card type and driver currently being used (could be a driver issue).  Could you post the following:

lspci -nn
lshw -C network

---

### Post by woozy on 2007-08-14
First the system information you ask:

sergio@deathstar:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller [8086:2590] (rev 03)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller [8086:2592] (rev 03)
00:02.1 Display controller [0380]: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller [8086:2792] (rev 03)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 [8086:2660] (rev 03)
00:1c.1 PCI bridge [0604]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 [8086:2662] (rev 03)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 [8086:2658] (rev 03)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 [8086:2659] (rev 03)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 [8086:265a] (rev 03)
00:1d.3 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 [8086:265b] (rev 03)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller [8086:265c] (rev 03)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev d3)
00:1e.2 Multimedia audio controller [0401]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller [8086:266e] (rev 03)
00:1e.3 Modem [0703]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller [8086:266d] (rev 03)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge [8086:2641] (rev 03)
00:1f.1 IDE interface [0101]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller [8086:266f] (rev 03)
00:1f.2 IDE interface [0101]: Intel Corporation 82801FBM (ICH6M) SATA Controller [8086:2653] (rev 03)
00:1f.3 SMBus [0c05]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller [8086:266a] (rev 03)
06:01.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)
06:02.0 Network controller [0280]: Intel Corporation PRO/Wireless 2200BG Network Connection [8086:4220] (rev 05)
06:04.0 CardBus bridge [0607]: Texas Instruments PCIxx21/x515 Cardbus Controller [104c:8031]
06:04.2 FireWire (IEEE 1394) [0c00]: Texas Instruments OHCI Compliant IEEE 1394 Host Controller [104c:8032]
06:04.3 Mass storage controller [0180]: Texas Instruments PCIxx21 Integrated FlashMedia Controller [104c:8033]
06:04.4 Generic system peripheral [0805]: Texas Instruments PCI6411/6421/6611/6621/7411/7421/7611/7621 Secure Digital Controller [104c:8034]


sergio@deathstar:~$ sudo lshw -C network
Password:
  *-network:0             
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 1
       bus info: pci@06:01.0
       logical name: eth0
       version: 10
       serial: 00:0f:b0:e1:0f:38
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full latency=32 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100MB/s
       resources: ioport:5000-50ff iomemory:bc006000-bc0060ff irq:22
  *-network:1 DISABLED
       description: Wireless interface
       product: PRO/Wireless 2200BG Network Connection
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@06:02.0
       logical name: eth1
       version: 05
       serial: 00:16:6f:54:42:ac
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2200 driverversion=1.2.0kmprq firmware=ABG:9.0.2.6 (Mar 22 2005) latency=32 link=no maxlatency=24 mingnt=3 multicast=yes wireless=radio off
       resources: iomemory:bc007000-bc007fff irq:23
  *-network
       description: Ethernet interface
       physical id: 2
       logical name: nas0
       serial: 00:90:d0:55:29:18
       capabilities: ethernet physical
       configuration: broadcast=yes ip=192.168.0.1 multicast=yes


And the router of the network I'm having trouble is sitecom but I don't know the model, but, if you want I think I can fix it. 

Now I'm having some trouble (noob stuff probably), as I referred above I've tried the WICD and I don't have access to that network but, as I got home, I noticed something: my ppp connection - with usb alcatel speedtouch - also stop working since I installed the WICD. Than  I removed WICD and it starts waiting but, when I install the network manager ppp stops working again. So, at the moment I don't have either WICD and network manager or else I don't have access to Internet through ppp..:S 
Thank you for the attention.

---

### Post by kevdog on 2007-08-14
Based on the information you gave me:

-network:1 DISABLED
description: Wireless interface
product: PRO/Wireless 2200BG Network Connection
vendor: Intel Corporation
physical id: 2
bus info: pci@06:02.0
logical name: eth1
version: 05
serial: 00:16:6f:54:42:ac
width: 32 bits
clock: 33MHz
capabilities: bus_master cap_list ethernet physical wireless
configuration: broadcast=yes driver=ipw2200 driverversion=1.2.0kmprq firmware=ABG:9.0.2.6 (Mar 22 2005) latency=32 link=no maxlatency=24 mingnt=3 multicast=yes **[SIZE="4"]wireless=radio off[/SIZE]**

It states the radio is off.  You need to turn the radio on either with a switch or in the bios if you havent done so already.  You might have problems after that, but lets start at this point.

---

### Post by woozy on 2007-08-14
Sorry, as I'm using ppp connection at the moment, I had the wireless off. 

Here it is:

sergio@deathstar:~$ sudo lshw -C network
Password:
  *-network:0             
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 1
       bus info: pci@06:01.0
       logical name: eth0
       version: 10
       serial: 00:0f:b0:e1:0f:38
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full latency=32 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100MB/s
       resources: ioport:5000-50ff iomemory:bc006000-bc0060ff irq:22
  *-network:1 DISABLED
       description: Wireless interface
       product: PRO/Wireless 2200BG Network Connection
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@06:02.0
       logical name: eth1
       version: 05
       serial: 00:16:6f:54:42:ac
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2200 driverversion=1.2.0kmprq firmware=ABG:9.0.2.6 (Mar 22 2005) latency=32 link=no maxlatency=24 mingnt=3 multicast=yes wireless=unassociated
       resources: iomemory:bc007000-bc007fff irq:23
  *-network
       description: Ethernet interface
       physical id: 2
       logical name: nas0
       serial: 00:90:d0:55:29:18
       capabilities: ethernet physical
       configuration: broadcast=yes ip=192.168.0.1 multicast=yes

---

### Post by kevdog on 2007-08-14
WIthout having a special configuration you can not run wired and wireless at the same time

Based on you new info:
[SIZE="4"]***-network:1 DISABLED**[/SIZE]
description: Wireless interface
product: PRO/Wireless 2200BG Network Connection
vendor: Intel Corporation
physical id: 2
bus info: pci@06:02.0
logical name: eth1
version: 05
serial: 00:16:6f:54:42:ac
width: 32 bits
clock: 33MHz
capabilities: bus_master cap_list ethernet physical wireless
configuration: broadcast=yes driver=ipw2200 driverversion=1.2.0kmprq firmware=ABG:9.0.2.6 (Mar 22 2005) latency=32 link=no maxlatency=24 mingnt=3 multicast=yes wireless=unassociated

Your wireless is still disabled.  Pull the cord from the wired connection.
Try sudo /etc/init.d/networking restart
If that doesnt work try rebooting without the wired connection plugged in

---

### Post by woozy on 2007-08-14
I've tried what you said but it stills disabled. I don't have any wireless connection in here...Is it supposed the network stays enable even without any wireless connection?

---

### Post by kevdog on 2007-08-14
I believe you are trying to enable the device, this does not mean a signal or connection is being established.  

I want you to type 
dmesg | more

This is the system log.  Its a large file.  Skim through the file and see if you can see anything relevant to your wireless device.  Im sure it will be mentioned at least once.  Please post anything you think is relevant

---

### Post by woozy on 2007-08-14
I'm sorry but I don't see anything about my wireless card...

---

### Post by kevdog on 2007-08-14
Nothing about eth1 or ipw2200??

---

### Post by woozy on 2007-08-16
Hello!
I've been out and the only network that I have available is the one that I was having trouble! Right now I've manage to solve the problem. But thank you for the patience and help you gave me!

Now the problem was:

As I referred, I have a speedtouch connection and that was the source of the problem. I installed it with a script so I didn't knew that this could influence my ethernet  connections..By looking to the system log I discover that my problems start at the time that it creates a nas0 device with the ip 192.168.0.1 . This address is the gateway of this network.  I tried:
 
sudo ifconfig nas0 192.168.0.1 netmask 255.255.255.0 down

And no address resolution, so I did the next:

sudo ifconfig nas0 192.168.1.1 netmask 255.255.255.0 up

And here I'am online without any problem. Now, I will change my /etc/init.d/speedtch and its done.

Regards,
Sérgio

---

