---
title: "[SOLVED] RT2500 Wifi not connecting to network"
date: 2008-08-29
forum: Networking &amp; Wireless
---

### Post by leona on 2008-08-29
Hi there

I am running 8.04 Hardy.

I have an RT2500pci chipped whifi pci card.
It can 'see' my network but refuses to connect to it.
I have turned all security off, its totally open.
It still refuses to connect.
How can I find out what is going wrong and fix it?

Here is some info I know you'll ask for :)

from lspci -nn
```

00:00.0 Host bridge [0600]: VIA Technologies, Inc. VT8377 [KT400/KT600 AGP] Host Bridge [1106:3189]
00:01.0 PCI bridge [0604]: VIA Technologies, Inc. VT8235 PCI Bridge [1106:b168]
00:0b.0 FireWire (IEEE 1394) [0c00]: NEC Corporation uPD72874 IEEE1394 OHCI 1.1 3-port PHY-Link Ctrlr [1033:00f2] (rev 01)
**00:0e.0 Network controller [0280]: RaLink RT2500 802.11g Cardbus/mini-PCI [1814:0201] (rev 01)**
00:10.0 USB Controller [0c03]: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller [1106:3038] (rev 80)
00:10.1 USB Controller [0c03]: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller [1106:3038] (rev 80)
00:10.2 USB Controller [0c03]: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller [1106:3038] (rev 80)
00:10.3 USB Controller [0c03]: VIA Technologies, Inc. USB 2.0 [1106:3104] (rev 82)
00:11.0 ISA bridge [0601]: VIA Technologies, Inc. VT8235 ISA Bridge [1106:3177]
00:11.1 IDE interface [0101]: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE [1106:0571] (rev 06)
00:11.5 Multimedia audio controller [0401]: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller [1106:3059] (rev 50)
00:12.0 Ethernet controller [0200]: VIA Technologies, Inc. VT6102 [Rhine-II] [1106:3065] (rev 74)
01:00.0 VGA compatible controller [0300]: nVidia Corporation NV44A [GeForce 6200] [10de:0221] (rev a1)

```

From iwconfig
```

lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:""  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:14:6C:01:26:7A   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Encryption key:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


```

from ifconfig
```

eth0      Link encap:Ethernet  HWaddr 00:0c:6e:07:18:21  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:18 

eth0:avahi Link encap:Ethernet  HWaddr 00:0c:6e:07:18:21  
          inet addr:169.254.2.3  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:18 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:3059 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3059 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:154824 (151.1 KB)  TX bytes:154824 (151.1 KB)

wlan0     Link encap:Ethernet  HWaddr 00:0e:2e:50:64:38  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-0E-2E-50-64-38-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

From lshw -C Network
```

  *-network:0             
       description: Wireless interface
       product: RT2500 802.11g Cardbus/mini-PCI
       vendor: RaLink
       physical id: e
       bus info: pci@0000:00:0e.0
       logical name: wmaster0
       version: 01
       serial: 00:0e:2e:50:64:38
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=rt2500pci latency=32 module=rt2500pci multicast=yes wireless=IEEE 802.11g
  *-network:1
       description: Ethernet interface
       product: VT6102 [Rhine-II]
       vendor: VIA Technologies, Inc.
       physical id: 12
       bus info: pci@0000:00:12.0
       logical name: eth0
       version: 74
       serial: 00:0c:6e:07:18:21
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=via-rhine driverversion=1.4.3 duplex=half latency=32 link=no maxlatency=8 mingnt=3 module=via_rhine multicast=yes port=MII speed=10MB/s

```

I got this card because I 'thought' it was compatible with linux, so what's up?

Pls help.

Thanks.

---

### Post by pclark36 on 2008-08-31
It's been a known problem for some time.  You will probably need to load the drivers with ndiswrapper.  (Search for it in the forums)  NetworkManager(and the latest kernels) have long had issue with RT2500 chipsets.  

I run mine through ndiswrapper and it works fine for the most part with encryption and everything.

---

### Post by leona on 2008-09-01
Thank you pclark, I wondered if that might be the case, that seems a bit messy to me, quite an involved set of instructions to get that intalled and no garrantees it'll work then either, I was hoping for a more 'cleaner' solution than hacking around with the windows driver, I guess no one know when this 'bug' might get fixed?

---

### Post by dodle on 2008-09-02
I'm having the same problem with the same card, except when I input those codes I don't have a wlan interface.  I gave up on my Broadcom card and reinstalled my Ralink card.  I'm going to try replacing Network Manager with WICD and see if that works.  I will post back the results.

---

### Post by dodle on 2008-09-03
Okay, I don't recommend wicd.  This sucks, I can't get either of my wireless cards to work.  They both have drivers in Synaptic too!!!!

---

### Post by leona on 2008-09-03
Hi dodle, thank you for reporting back, that saved me wasting an evening trying something that is a complete waste of time. oh dear.
Guess I'll have to print off the instructions for hacking the windows drivers and set aside an evening to do it, not impressed one bit, this is a generic chip, (well the one that's most used, i think), so this is really disappointing, resists going into a full on rant. :(

---

### Post by leona on 2008-09-03
oh no, I am a stupid, stupid, stupid girl! Cut me off a large slice of humble pie, it was MY mistake.

I forgot to check the router, I had removed all security, but what I had overlooked was "Wireless Card Access List" I had forgotten I had set this up, once I had disabled this, the card worked, so now I've added its MAC address to the list, enabled security and restarted it works now (although only a 20% signal, but its only 6 foot away from the router!).

So thank you so much for your help, but this time, it was the squidgy bit between the keyboard and the chair that was the problem, I feel so dum, d'oh! :(

---

