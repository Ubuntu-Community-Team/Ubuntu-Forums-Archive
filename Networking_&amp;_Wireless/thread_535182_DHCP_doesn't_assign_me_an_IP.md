---
title: "DHCP doesn't assign me an IP"
date: 2007-08-26
forum: Networking &amp; Wireless
---

### Post by joeyjo0 on 2007-08-26
I installed Linux ubuntu yesterday, and i can't connect to the internet.

First, it can't connect to Wifi properly, it works only 1/10th of the times.
Second, if It actually connects, i don't get an IP.

That's why i tried Wired connection. It has the same problem.

My router:
linksys WRT54G
WPA personal PSK encryption
DHCP enabled

I've got Dual-boot: Linux ubuntu and Windows XP home SP2(Grub). My connection is working on Windows.

---

### Post by K.Mandla on 2007-08-26
The next time it doesn't work, try this from a terminal.

```
sudo /etc/init.d/networking restart
```
That tells Ubuntu to reinitialize your network subsystem, and should give it a second chance. What kind of wireless card and computer are you working with? What's the output of

```
sudo ifconfig
```
and

```
sudo iwconfig
```

---

### Post by joeyjo0 on 2007-08-26
Compaq presario R3000
and card: Realtek Fast family NIC... something.


First tried restart... Nothing.


DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

joeyjo0@JoeyNotebook:~$ sudo ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0F:B0:4D:13:AD  
          inet6 addr: fe80::20f:b0ff:fe4d:13ad/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:58 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:12182 (11.8 KiB)
          Interrupt:18 Base address:0xc800 

eth0:avah Link encap:Ethernet  HWaddr 00:0F:B0:4D:13:AD  
          inet addr:169.254.6.4  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:18 Base address:0xc800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:84 errors:0 dropped:0 overruns:0 frame:0
          TX packets:84 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:6360 (6.2 KiB)  TX bytes:6360 (6.2 KiB)


joeyjo0@JoeyNotebook:~$ sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:""  Nickname:"Broadcom 4306"
          Mode:Managed  Access Point: Invalid   
          RTS thr:off   Fragment thr:off
          Encryption key:off
          Link Quality=0/100  Signal level=-256 dBm  Noise level=-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by kevdog on 2007-08-26
Great router by the way.

Couple things to clarify -- how did you install the driver for your wireless card.  What version is it? and what is the result of lshw -C network?

Can you connect with WPA turned off at the router?

---

### Post by joeyjo0 on 2007-08-26
Thanks

I didn't install it. The computer mechanic did.

Sorry, I may not take off WPA from the router... (dad won't let me >=( )

---

### Post by kevdog on 2007-08-26
Computer mechanic???

Have you ever connected to any internet connection using this card??

Please post the following so I can help:

lshw -C network
iwlist scan 

Your making it difficult to troubleshoot your situation b/c you are not telling me anything.

---

### Post by joeyjo0 on 2007-08-26
Yes, I had a broken HDD before, got a new one. The computer mech installed windows and the drivers and stuff. I also haven't got any drivers with this card.

Yes, with windows, it works perfectly.

Okay, i'll try.

---

### Post by kevdog on 2007-08-26
Great but we are working in Linux not windows.  I need to know what type of wireless card you have (lshw -C network), in order to tell if we have to install a Linux driver or something else.  You need to help me so I can help you:)

---

### Post by joeyjo0 on 2007-08-26
root@JoeyNotebook:/home/joeyjo0# lshw -C network
  *-network:0             
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 1
       bus info: pci@02:01.0
       logical name: eth0
       version: 10
       serial: 00:0f:b0:4d:13:ad
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full latency=64 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100MB/s
       resources: ioport:7000-70ff iomemory:e0108800-e01088ff irq:18
  *-network:1 DISABLED
       description: Wireless interface
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@02:02.0
       logical name: eth1
       version: 03
       serial: 00:90:4b:ac:d2:b2
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       configuration: broadcast=yes driver=bcm43xx driverversion=2.6.20-15-generic latency=64 link=no multicast=yes wireless=IEEE 802.11b/g
       resources: iomemory:e0104000-e0105fff irq:17
root@JoeyNotebook:/home/joeyjo0# iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Interface doesn't support scanning : No such device


Ran as Root, because it said i better have to.

---

### Post by kevdog on 2007-08-26
Ok Im assuming its your wireless that is causing you problems???
[B]
*-network:1 DISABLED[/B]
description: Wireless interface
product: BCM4306 802.11b/g Wireless LAN Controller
vendor: Broadcom Corporation
physical id: 2
bus info: pci@02:02.0
logical name: eth1
version: 03
serial: 00:90:4b:ac:d2:b2
width: 32 bits
clock: 33MHz
capabilities: bus_master ethernet physical wireless
configuration: broadcast=yes driver=bcm43xx driverversion=2.6.20-15-generic latency=64 link=no multicast=yes wireless=IEEE 802.11b/g
resources: iomemory:e0104000-e0105fff irq:17

You have a broadcom chipset, but more importantly it states the wireless is disabled.   Is your wireless card turned on??  Meaning do you have a switch to turn it on manually, or do you have to turn it on in the BIOS??  Is this an onboard card or pci card?  Also, you need to install a driver for this card, if you could post
lspci -nn

it would also help.

---

### Post by joeyjo0 on 2007-08-27
There is a button here, next to my volume button, wich is the on/off switch for Wireless. The lamp next to it is burning, so i guess it's on.

**bus info: pci@02:01.0** PCI, perhaps.

The computer Mech also tried using the Sabayon live disk, this works with Wireless, however.

---

### Post by kevdog on 2007-08-27
You didnt install any firware for the bcm43xx driver did you (I doubt it since I think you told me that already)??

Do you have windows XP drivers available for the networking card available??

---

### Post by joeyjo0 on 2007-08-27
I don't know.
I'm using a notebook, and all hardware is pre-installed. I didn't get any driver disks with them. Once again, the computer guy installed windows for me, i don't know what drivers he installed.

I guess so, the card works on windows.

---

### Post by kevdog on 2007-08-27
Can you do a search in windows for bcmw* in windows beginning at the c: drive?  Report back what you found!

---

### Post by joeyjo0 on 2007-08-28
Okay, I'll do that when I'm at home.

---

### Post by jpwoods_7 on 2007-08-28
I'm having the same problem except... well I DONT have a wireless router and I tried /etc/init.d/networking restart, and I recieved the same results as the beguinning of this post.  I'm on a different computer and cannot pastebin anything.  But it is ethernet (router doesn't matter because it wont pick it up directly connected either) Lastly the drivers are something like Realtek *** and should have the eth0 working.  Sorry I can't give any other information.  Suggestions ???

---

### Post by kevdog on 2007-08-28
jp

Id suggest starting another post with your problem since you have a rtl based chipset, not a broadcom.  Different solution for you :)

---

### Post by joeyjo0 on 2007-09-08
BCMWL5.txt

[InstallShield Silent]
Version=v6.00.000
File=Log File
[ResponseResult]
ResultCode=0
[Application]
Name=802.11
Version=3.100.65.2
Company=Broadcom
Lang=0013

I've also got a load of exe's(Broadcom wireless utility) that are programs that override windows normal wireless, and use that program instead. 

In /system32/drivers there's a file called BCMWL5.sys... Wich is the driver itself.


sorry for my late reply... Was pretty busy.

---

### Post by kevdog on 2007-09-08
Awewome, you found the driver bcmwl5.sys.  Do a search for bcmwl5.inf, and with these two files you got everything you need.  

I would copy these two files to a separate directory (copy do not move).  We will be using these files with ndiswrapper.

---

### Post by joeyjo0 on 2007-09-08
I asked google nicely, and i got working internet connection now. Thank you! :)

---

### Post by bshep355 on 2007-09-17
Can you tell me what you did when you asked google nicely.  I too have run into the problem with my wireless adapter showing up as Disabled.  Please help!!

---

