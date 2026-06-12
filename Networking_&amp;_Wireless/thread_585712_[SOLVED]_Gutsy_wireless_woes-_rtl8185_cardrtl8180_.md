---
title: "[SOLVED] Gutsy wireless woes- rtl8185 card/rtl8180 drivers"
date: 2007-10-21
forum: Networking &amp; Wireless
---

### Post by ecrissman on 2007-10-21
I think I have read every post on wireless problems and many more in these forums and google for MANY hours but nothing I do works.
I have a fresh install of Gutsy that I finally got running great, but still can't manage to get my wireless card working.  It is being recognized but I am getting 0% signal.  Is this a driver issue- rtl8180 driver for rtl8185 card?  I installed ndiswrapper from synaptic and installed the windows 8185 driver, but I don't know how to use it instead of the 8180 driver that loads with the kernel. IF possible I don't want to use ndiswrapper, but it did work great in Feisty.  Any help please? Here is the output I am getting:

```
eric@our-laptop:~$ lspci (relevant part)
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon XPRESS 200M 5955 (PCIE)
03:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8036 PCI-E Fast Ethernet Controller (rev 10)
05:02.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller (rev 20)

/etc/network/interfaces
auto lo
iface lo inet loopback

eric@our-laptop:~$ sudo lshw -C network
  *-network
       description: Wireless interface
       product: RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 2
       bus info: pci@0000:05:02.0
       logical name: wlan0
       version: 20
       serial: 00:c0:a8:c8:f9:90
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl8180 latency=64 maxlatency=64 mingnt=32 module=r8180 multicast=yes wireless=802.11b/g link..

eric@our-laptop:~$ sudo iwconfig
[sudo] password for eric:
lo        no wireless extensions.

wlan0     802.11b/g link..  ESSID:"ESCHome"  
          Mode:Managed  Frequency=2.432 GHz  Access Point: Not-Associated   
          Bit Rate:11 Mb/s   
          Retry:on   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

eric@our-laptop:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:E0:B8:B6:B4:F2  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:22 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

wlan0     Link encap:Ethernet  HWaddr 00:C0:A8:C8:F9:90  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:14 errors:18 dropped:18 overruns:0 frame:0
          TX packets:194 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2287 (2.2 KB)  TX bytes:8097 (7.9 KB)
          Interrupt:20 Memory:f8924000-f8924100 

wlan0:ava Link encap:Ethernet  HWaddr 00:C0:A8:C8:F9:90  
          inet addr:169.254.11.29  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:20 Memory:f8924000-f8924100 

eric@our-laptop:~$ sudo ifdown wlan0
ifdown: interface wlan0 not configured
eric@our-laptop:~$ sudo ifup wlan0
There is already a pid file /var/run/dhclient.wlan0.pid with pid 134519120
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/wlan0/00:c0:a8:c8:f9:90
Sending on   LPF/wlan0/00:c0:a8:c8:f9:90
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
No DHCPOFFERS received.
No working leases in persistent database - sleeping.


System log messages- (relevant part)
Oct 21 15:17:26 our-laptop kernel: [   15.544000] Copyright (c) 2004-2005, Andrea Merello
Oct 21 15:17:26 our-laptop kernel: [   15.544000] rtl8180: Initializing module
Oct 21 15:17:26 our-laptop kernel: [   15.544000] rtl8180: Wireless extensions version 22
Oct 21 15:17:26 our-laptop kernel: [   15.544000] rtl8180: Initializing proc filesystem
Oct 21 15:17:26 our-laptop kernel: [   15.544000] rtl8180: Configuring chip resources
Oct 21 15:17:26 our-laptop kernel: [   15.544000] ACPI: PCI Interrupt 0000:05:02.0[A] -> GSI 22 (level, low) -> IRQ 20
Oct 21 15:17:26 our-laptop kernel: [   15.544000] rtl8180: Memory mapped space @ 0xd0306000 
Oct 21 15:17:26 our-laptop kernel: [   15.544000] rtl8180: MAC controller is a RTL8185 b/g (V. D)
Oct 21 15:17:26 our-laptop kernel: [   15.544000] rtl8180: This is a MINI-PCI NIC
Oct 21 15:17:26 our-laptop kernel: [   15.544000] rtl8180: Reported EEPROM chip is a 93c46 (1Kbit)
Oct 21 15:17:26 our-laptop kernel: [   15.552000] rtl8180: Card MAC address is 00:c0:a8:c8:f9:90
Oct 21 15:17:26 our-laptop kernel: [   15.568000] rtl8180: EEPROM version 105
Oct 21 15:17:26 our-laptop kernel: [   15.568000] rtl8180: Card reports RF frontend Realtek 8225
Oct 21 15:17:26 our-laptop kernel: [   15.568000] rtl8180: WW:This driver has EXPERIMENTAL support for this chipset.
Oct 21 15:17:26 our-laptop kernel: [   15.568000] rtl8180: WW:use it with care and at your own risk and
Oct 21 15:17:26 our-laptop kernel: [   15.568000] rtl8180: WW:**PLEASE** REPORT SUCCESS/INSUCCESS TO andreamrl@tiscali.it
Oct 21 15:17:26 our-laptop kernel: [   15.568000] rtl8180: Energy threshold: b
Oct 21 15:17:26 our-laptop kernel: [   15.568000] rtl8180: PAPE from CONFIG2: 6
Oct 21 15:17:26 our-laptop kernel: [   15.568000] rtl8180: IRQ 20
Oct 21 15:17:26 our-laptop kernel: [   15.568000] rtl8180: Driver probe completed

```

Thanks

---

### Post by Bugeater88 on 2007-10-21
I'm having the exact same issue using 7.4 myself.  Interested to hopefully see a fix for this in this thread from the experts.

---

### Post by ecrissman on 2007-10-22
sorry...bump

---

### Post by ecrissman on 2007-10-22
Any help??

---

### Post by PreviousN on 2007-10-23
HELP ME! I have the same problem. Except that when I try to connect to an encrypted network the entire compter freezes. Same chipset. 

NDISWrapper worked in feisty, but now my computer loads 8180 drivers by default. I WANT TO USE NDIS Wrapper (if it wasn't broke, why fix it?!). How do I turn off/prevent 8180 drivers from loading?

---

### Post by PreviousN on 2007-10-23
Here's how you fix it:

"lsmod | grep 8180"
"modprobe -r *name of driver from above*"

That should do the trick...I think. It did for me. although I tried a bunch of things.

---

### Post by ecrissman on 2007-10-23
Thank you!  That did it. It has been so many hours. If I didn't love Linux so much I would have given up long ago. I really wanted to get the open source driver to work, but it looks like for now I will have to stick with ndiswrapper.

---

### Post by Aathos on 2007-10-23
What drivers are you using for ndiswrapper?  The ones I have tried didn't quite work completely (see [this thread]("http://ubuntuforums.org/showthread.php?t=482478") if you want details), and now they aren't working at all.

---

### Post by ecrissman on 2007-10-23
I am using a driver(rtl8185) from the Realtek website.  Google it or the driver you need and you should be able to find one for your card/chipset.

---

### Post by jon schroeder on 2007-10-26
I spent a good portion of my night rebuilding a machine with Ubuntu 7.10 only to run into problems with my wifi card with a RTL8185 chipset... my solution... pulled out another wifi card with a different chipset.  My biggest problem was with no pc stores open at midnight... I cannibalized my wife's xp machine.  The new wifi card is a Texas Instruments AX 111 chipset.  Works good.  Although I had to manually configure it.

---

### Post by Aathos on 2007-11-07
I found a good How-To by m_bridge for installing the windows drivers [here]("http://ubuntuforums.org/showthread.php?t=580309"). He has it labeled for a different card, but it is the same chipset.

---

### Post by SFCampbell on 2008-01-02
> **PreviousN said:**
> Here's how you fix it:

"lsmod | grep 8180"
"modprobe -r *name of driver from above*"

That should do the trick...I think. It did for me. although I tried a bunch of things.

PreviousN you're awesome - I gathered that the Kernel Panics were caused by a bad module, but I couldn't figure out how to pinpoint it or remove it.  Using these steps then adding the bad module to /etc/modprobe.d/blacklist paved the way to a working driver with NDISGTK.  Thanks for the tip!

---

### Post by CoolDreamZ on 2008-02-09
This driver on the RealTek site was posted 21st Dec 2007 and works (so far) for me on a 32bit Feisty system, it is a native linux driver and needs to be compiled from source.

[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=1&PFid=1&Level=6&Conn=5&DownTypeID=3&GetDown=false&Downloads=true]("http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=1&PFid=1&Level=6&Conn=5&DownTypeID=3&GetDown=false&Downloads=true")

---

### Post by CoolDreamZ on 2008-02-09
Well, I have tried this and I get kernel freezes (from syslog it seems the wireless card/driver is constantly re-setting/crashing). I have moved to using the ndiswrapper solution instead which works fine with command line configuration of the wireless network connection although I have now lost the ability to configure through nm-applet :(

---

