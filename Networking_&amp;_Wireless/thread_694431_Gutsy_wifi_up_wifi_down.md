---
title: "Gutsy wifi up wifi down"
date: 2008-02-12
forum: Networking &amp; Wireless
---

### Post by Richard2007 on 2008-02-12
When I first installed Gutsy, I had wifi up as ath0. Then after working for a while, it went down and would not respond to the network manager.

So I did a lcsw -C network

And found the logical name is changed to wifi0 but when I do IWCONFIG it shows wifi0 unassigned and ath0 is assigned to my card!

HELP how do I rectify this and keep it from happening again?

Can the ath0 entry in Iwconfig be deleted and then the wifi0 assigned the network info. When I try to assign essid to wifi0 it refuses it.

Thanks for reading this, help please if your able.

Richard2007:guitar:

---

### Post by Gen2ly on 2008-02-12
wifi0 is some sort wrapper for the madwifi driver it thats what you're using, which it sounds like it is - ath0 is the actual device.  What kind of signal strength are you getting, are you in a high traffic place?

---

### Post by Richard2007 on 2008-02-12
Im not using madwifi and wifi0 is not a driver, its the logical device name assigned. previously the logical device name was ath0.  Since the logical name changed but not all the way thru the network settings,  it is causing a conflict as in one place its wifi0 and elsewhere it is ath0.

---

### Post by dca on 2008-02-12
If I type 'ifconfig' in terminal mine also displays wifi0 and ath0 for same wireless device.  I have an Ambit mini-PCIe card using Atheros chipset which requires a special patch (on top of restricted drivers madwifi included on installation of Ubuntu) in order to work properly verus going the ndiswrapper & Windows driver route.  Did your system stop working after software updates that included something (header, source, etc) for the linux-kernel?

---

### Post by Richard2007 on 2008-02-12
Yes right after a kernal update was done as I was downloading the updates for ubuntu studio.

I also have the athero card that I went out and bought specifically so it would work with ubuntu. And it did for months with fiesty.

Richard:guitar:

---

### Post by dca on 2008-02-12
How were the drivers originally installed???  It sounds like they just need to be reinserted into the kernel...  Like 'modprobe -i ath_pci' or 'modprobe -i ndiswrapper'...  Or if it required a patch in my case, I had to untar the patch, run make, make install, and re-add it to the kernel...

---

### Post by Richard2007 on 2008-02-12
originally under fiesty I just installed the card and used the gui network manager to config and I was up.

Here is my outputs so you can see whats going on, one note the broadcom netcard is for my windows side Im using Nwireless on windows and its not used in linux.

sudo lshw -C network
  *-network:0 UNCLAIMED   
       description: Network controller
       product: BCM43XG
       vendor: Broadcom Corporation
       physical id: 6
       bus info: pci@0000:04:06.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: latency=32
  *-network:1
       description: Wireless interface
       product: AR5212/AR5213 Multiprotocol MAC/baseband processor
       vendor: Atheros Communications, Inc.
       physical id: 7
       bus info: pci@0000:04:07.0
       logical name: wifi0
       version: 01
       serial: 00:14:6c:8f:3b:f9
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath_pci driverversion=0.9.4.5 (0.9.3.2) ip=172.16.0.7 latency=168 maxlatency=28 mingnt=10 module=ath_pci multicast=yes wireless=IEEE 802.11g


 sudo lspci
00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
00:02.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:03.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:04.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:05.0 VGA compatible controller: nVidia Corporation C51G [GeForce 6100] (rev a2)
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a2)
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a2)
00:0a.2 RAM memory: nVidia Corporation MCP51 Memory Controller 0 (rev a2)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a2)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a2)
00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev a1)
00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:10.2 Multimedia audio controller: nVidia Corporation MCP51 AC97 Audio Controller (rev a2)
00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a1)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
04:06.0 Network controller: Broadcom Corporation BCM43XG (rev 01)
04:07.0 Ethernet controller: Atheros Communications, Inc. AR5212/AR5213 Multiprotocol MAC/baseband processor (rev 01)


 ifconfig -a
ath0      Link encap:Ethernet  HWaddr 00:14:6C:8F:3B:F9  
          inet addr:172.16.0.7  Bcast:172.16.0.255  Mask:255.255.255.0
          inet6 addr: fe80::214:6cff:fe8f:3bf9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:32 errors:0 dropped:0 overruns:0 frame:0
          TX packets:36 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:4077 (3.9 KB)  TX bytes:5491 (5.3 KB)

eth0      Link encap:Ethernet  HWaddr 00:40:CA:91:6E:EF  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:18 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

wifi0     Link encap:UNSPEC  HWaddr 00-14-6C-8F-3B-F9-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3166 errors:0 dropped:0 overruns:0 frame:725
          TX packets:112 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:199 
          RX bytes:383056 (374.0 KB)  TX bytes:10422 (10.1 KB)
          Interrupt:20 


modprobe -i ath0
FATAL: Module ath0 not found.
modprobe -i wifi0
FATAL: Module wifi0 not found.
 

Richard:guitar:

---

### Post by dca on 2008-02-12
According to this there's an on-going thread relative to the AR5212 chipset, I don't know if it'll help or point in the right direction... 
 
[http://ubuntuforums.org/showthread.php?t=38972&highlight=AR5212](http://ubuntuforums.org/showthread.php?t=38972&highlight=AR5212)
 
I know a lot of the info is old, ie: kernel versions and such but it might shed some light as far as some of the commands to help diagnose...

---

### Post by Richard2007 on 2008-02-13
The ath0 and wifi0 both share the same interface address. From reading online it is common for new updates on Linux to change the physical id, so I need a way to either change the id back to ath0 or to permanently get rid of the ath0 settings so the conflict with the same address is gone.

To that end I physically removed the network cards and reinstalled gutsy after erasing the partitions root and swap and yet ath0 settings are still hanging around.

I really need help on this one!

Richard:guitar:

---

### Post by dca on 2008-02-13
I wish I could help you more but on my Acer laptop it's exactly the same.  Ath0 is config for the network and Wifi0 is there w/ no config info, it's just hanging around.  The only difference is, it really hasn't hindered me as far as network settings or anything else system related...  I did do some searching and the only thing I came up with on this forum is this:
 
[http://ubuntuforums.org/showthread.php?t=535332](http://ubuntuforums.org/showthread.php?t=535332)
 
 
There maybe more, but spot-checking through the actual threads, this is what I found...

---

### Post by Richard2007 on 2008-02-13
I have the exact same issue, and it didn't happen until the kernel update on ubuntustudio. When I do the iwlist I am now receiving from the router but not transmitting. Or at least all web pages fail.

So thats improvement thank you so much, I will move this issue onto that page now and close this one.

Thanks for all your help.

Richard:guitar:

---

### Post by Richard2007 on 2008-02-13
I have the exact same issue, and it didn't happen until the kernel update on ubuntustudio. When I do the iwlist I am now receiving from the router but not transmitting. Or at least all web pages fail.

So thats improvement thank you so much, I will move this issue onto that page now and close this one.

Thanks for all your help.

Richard

---

### Post by Richard_2007 on 2008-04-29
Ok this first happened on gutsy now again on heron. The fix is to use synaptic and remove madwifi, then reboot and reinstall under the ubuntu restricted drivers for madwifi. A quick config under the network manager and Im back posting this. 

On a side note I hope the developers will see what is so hard about making existing nvidia connections and athero wifi cards come up active as they were before the upgrade. This has happened across two releases and seems like it would be easy to fix.

Thanks and I hope this post helps others.

Richard

---

