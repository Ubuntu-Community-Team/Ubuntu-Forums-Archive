---
title: "can't connect to internet"
date: 2008-08-19
forum: Networking &amp; Wireless
---

### Post by nifaris on 2008-08-19
Is anybody out there?
Hi-absolute beginner just installed ubuntu 8.04 on 1 of 3 hard drives (2 XP)but have no internet.Speedtouch585 router/wireless network. On my laptop now with ubuntu on desktop! Help!

---

### Post by tangibleorange on 2008-08-19
> **nifaris said:**
> Is anybody out there?
Hi-absolute beginner just installed ubuntu 8.04 on 1 of 3 hard drives (2 XP)but have no internet.Speedtouch585 router/wireless network. On my laptop now with ubuntu on desktop! Help!

ok. please type these commands at the terminal (one at a time):
```
lspci
iwconfig
```

---

### Post by yashugrover on 2008-08-19
even i cant connect to internet..
Here is the output of the imp. commands
 
```

lspci

00:00.0 Host bridge: ATI Technologies Inc Radeon Xpress 200 Host Bridge (rev 01)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:11.0 IDE interface: ATI Technologies Inc IXP SB400 Serial ATA Controller (rev 80)
00:12.0 IDE interface: ATI Technologies Inc IXP SB400 Serial ATA Controller (rev 80)
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 81)
00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller (rev 80)
00:14.2 Audio device: ATI Technologies Inc IXP SB4x0 High Definition Audio Controller (rev 01)
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)
01:05.0 VGA compatible controller: ATI Technologies Inc RC410 [Radeon Xpress 200]
02:03.0 Communication controller: Agere Systems Unknown device 0620
02:05.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:06.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev c0)

```

```

ifconfig

 *-network               
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 5
       bus info: pci@0000:02:05.0
       logical name: eth0
       version: 10
       serial: 00:16:ec:81:48:51
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 latency=64 maxlatency=64 mingnt=32 module=8139too multicast=yes
administrator@administrator-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:16:ec:81:48:51  
          inet6 addr: fe80::216:ecff:fe81:4851/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:129 errors:0 dropped:0 overruns:0 frame:0
          TX packets:90 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:30001 (29.2 KB)  TX bytes:8918 (8.7 KB)
          Interrupt:20 Base address:0xe400 

eth0:avahi Link encap:Ethernet  HWaddr 00:16:ec:81:48:51  
          inet addr:169.254.8.66  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:20 Base address:0xe400 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1974 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1974 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:99683 (97.3 KB)  TX bytes:99683 (97.3 KB)

```

---

### Post by tangibleorange on 2008-08-19
@yashugrover - do you have a wireless card or are you referring to a wired connection? the output of those command would suggest you do not have a wireless card (unless its a USB one)

---

### Post by yashugrover on 2008-08-19
@tangibleorange
I have a wired connection...

---

### Post by tangibleorange on 2008-08-19
> **yashugrover said:**
> @tangibleorange
I have a wired connection...

ah ok. and network manager does not connect you automatically at boot? could you post the output of:
```
cat /etc/network/interfaces
```

---

### Post by yashugrover on 2008-08-19
@tangibleorange

here is the output:
```

auto lo
iface lo inet loopback

```

---

### Post by tangibleorange on 2008-08-19
ok. open it up:
```
gksu gedit /etc/network/interfaces
```
and add this line:
iface eth0 inet dhcp

then save the file and reboot. now see if you are connected.

---

### Post by nifaris on 2008-08-19
ok-lspci gives me loads of info,iwconfig says no wireless extensions

---

### Post by tangibleorange on 2008-08-19
> **nifaris said:**
> ok-lspci gives me loads of info,iwconfig says no wireless extensions

could you actually copy and paste the outputs from the terminal into a post here? thanks.

---

### Post by yashugrover on 2008-08-19
> **tangibleorange said:**
> ok. open it up:
```
gksu gedit /etc/network/interfaces
```
and add this line:
iface eth0 inet dhcp

then save the file and reboot. now see if you are connected.

I did as u said but I still cannot access internet...

---

### Post by tangibleorange on 2008-08-19
ok try this command:
```
sudo dhclient eth0
```
also please post what it outputs

---

### Post by yashugrover on 2008-08-19
Here is the output of the above command:
```

[sudo] password for administrator: 
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:16:ec:81:48:51
Sending on   LPF/eth0/00:16:ec:81:48:51
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 19
No DHCPOFFERS received.
No working leases in persistent database - sleeping.


```

---

### Post by yashugrover on 2008-08-19
I would also like to add that I have ubuntu 8.04 installed within windows..

---

### Post by tangibleorange on 2008-08-19
> **yashugrover said:**
> I would also like to add that I have ubuntu 8.04 installed within windows..

ah ok. is it in vmware? if so, remember to select NAT as the method of networking, NOT bridged.

---

### Post by nifaris on 2008-08-19
-I can't do that Dave so I'll have to type this manually!
00:00.0 Host Bridge: Via Technologies, Inc. PT894 Host Bridge 
00:00.1 Host Bridge: Via Technologies, Inc. PT894 Host Bridge
00:00.2 Host Bridge: Via Technologies, Inc. PT894 Host Bridge 
00:00.3 Host Bridge: Via Technologies, Inc. PT890 Host Bridge 
00:00.4 Host Bridge: Via Technologies, Inc. PT894 Host Bridge
00:00.5 PIC: VIA Technologies, Inc. PT894 I/O APIC Interrupt Controller00:00.7 Host Bridge: Via Technologies, Inc. PT894 Host Bridge 
00:01.0 PCI Bridge: Via Technologies, Inc. VT8237 PCI Bridge 
00:02.0 PCI Bridge: Via Technologies, Inc. PT890 PCI to PCI Bridge Controller
00:0f.0 IDE interface: VIA Technologies, Inc. Unknown Device 5372
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x C PIPC Bus Master IDE(rev 07)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Control (rev b0)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Control (rev b0)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Control (rev b0)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Control (rev b0)
00:10.4 USB Controller: VIA Technologies, Inc.USB 2.0 (rev 90)
00:11.0 ISA bridge: VIA Technologies, Inc.VT82375 PCI to ISA Bridge
00:11.7 Host bridge: VIA Technologies, Inc. VT8251 Ultra VLINK Controller
00:12.0 Ethernet Controller: VIA Technologies, Inc. VT6102[Rhine II] (rev 7c)
00:13.0 Host bridge: VIA Technologies, Inc. VT8237A Host Bridge
00:13.1 PCI Bridge: VIA Technologies, Inc.VT8237a PCI to PCI Bridge
02:00.0 VGA compatible controller: nVidia Corporation GeForce 8600 GT(rev
1)
03:05.0 Multimedia audio controller: Cirrus Logic Crystal CS4281 PCI Audio (r01)

---

### Post by yashugrover on 2008-08-19
> **tangibleorange said:**
> ah ok. is it in vmware? if so, remember to select NAT as the method of networking, NOT bridged.
Sorry I didnt get you, can you explain it again in a bit more detail.
By the way this is exactly what happened with me :
Earlier I had windows xp media centre edition (sp2) as my OS. And I had internet connection from Hathway.
Then one fine day I installed ubuntu inside windows. Then when the first time I booted ubuntu, I opened mozilla firefox and to my wonder it connected to internet without me requiring to configure any settings manually; unlike in windows in which I had to first login to connect to internet, there was no such need in ubuntu. It automatically connected to internet.
Everything was perfect; the transfer rate that ubuntu offered me was three times than that offered by internet in Windows !!!
Then all of a sudden, yesterday night my internet connection got disconnected and since then I have not been able to connect to internet in ubuntu.
But on the other hand, at the same time I can connect to internet in windows !!!

---

### Post by tangibleorange on 2008-08-19
when you say installed 'installed in windows', do you mean you installed with the wubi installer, or ubuntu is running in a virtual machine (with software like VMware).

---

### Post by yashugrover on 2008-08-19
> **tangibleorange said:**
> when you say installed 'installed in windows', do you mean you installed with the wubi installer, or ubuntu is running in a virtual machine (with software like VMware).
Its not running in a VM, I installed it with wubi installer..

---

### Post by tangibleorange on 2008-08-20
ah ok. i'm afraid I know very little about Wubi. you might try posting this in the Wubi subsection of this forum:
[http://ubuntuforums.org/forumdisplay.php?f=234]("http://ubuntuforums.org/forumdisplay.php?f=234")
but other than that i'm out of ideas. good luck.

---

