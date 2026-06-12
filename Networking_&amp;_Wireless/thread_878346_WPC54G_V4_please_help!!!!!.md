---
title: "WPC54G V4 please help!!!!!"
date: 2008-08-02
forum: Networking &amp; Wireless
---

### Post by Ricktron on 2008-08-02
hi, i'm using a dell inspiron 1000 and i have linksys wpc54g v4 wireless card. i can't get it to work at all. i'm using ubuntu 8.04. if anyone can walk me through setting it up and getting it working it would be much appreciated.


-rick

---

### Post by pytheas22 on 2008-08-02
Please post the output of:
```

lspci
lshw -C Network
lsusb
```

so that we can figure out what you need to do.

---

### Post by Kinetic777 on 2008-08-02
I have the same card, and had the same problem (I think?). All I did was restart the computer with the wireless card plugged in, and then it worked fine.

---

### Post by Ricktron on 2008-08-03
> **pytheas22 said:**
> Please post the output of:
```

lspci
lshw -C Network
lsusb
```

so that we can figure out what you need to do.





00:00.0 Host bridge: Silicon Integrated Systems [SiS] 650/M650 Host (rev 80)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] Virtual PCI-to-PCI bridge (AGP)
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS962 [MuTIOL Media IO] (rev 25)
00:02.1 SMBus: Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE]
00:02.6 Modem: Silicon Integrated Systems [SiS] AC'97 Modem Controller (rev a0)
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 91)
00:0a.0 CardBus bridge: Texas Instruments PCI1510 PC card Cardbus Controller
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 65x/M650/740 PCI/AGP VGA Display Adapter
02:00.0 Ethernet controller: Linksys, A Division of Cisco Systems [AirConn] INPROCOMM IPN 2220 Wireless LAN Adapter (rev 01)


WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: SiS900 PCI Fast Ethernet
       vendor: Silicon Integrated Systems [SiS]
       physical id: 4
       bus info: pci@0000:00:04.0
       logical name: eth0
       version: 91
       serial: 00:11:43:47:ae:7f
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sis900 driverversion=v1.08.10 Apr. 2 2006 ip=192.168.10.11 latency=173 maxlatency=11 mingnt=52 module=sis900 multicast=yes
  *-network
       description: Wireless interface
       product: [AirConn] INPROCOMM IPN 2220 Wireless LAN Adapter (rev 01)
       vendor: Linksys, A Division of Cisco Systems
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 00
       serial: 00:12:17:3d:6f:53
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+wlipnds driverversion=1.52+Cisco-Linksys, LLC.,01/05/2 latency=64 maxlatency=32 mingnt=32 module=ndiswrapper multicast=yes wireless=IEEE 802.11g



Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000

---

### Post by kevdog on 2008-08-03
Can you post additionally

ifconfig
iwlist scan
dmesg | egrep ('wlan0 | ndiswrapper')

---

### Post by Ricktron on 2008-08-03
> **kevdog said:**
> Can you post additionally

ifconfig
iwlist scan
dmesg | egrep ('wlan0 | ndiswrapper')


eth0      Link encap:Ethernet  HWaddr 00:11:43:47:ae:7f  
          inet addr:192.168.10.11  Bcast:192.168.10.255  Mask:255.255.255.0
          inet6 addr: fe80::211:43ff:fe47:ae7f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:120510 errors:0 dropped:0 overruns:0 frame:0
          TX packets:74271 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:177359046 (169.1 MB)  TX bytes:5528155 (5.2 MB)
          Interrupt:18 Base address:0x1800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2524 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2524 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:126200 (123.2 KB)  TX bytes:126200 (123.2 KB)

wlan0     Link encap:Ethernet  HWaddr 00:12:17:3d:6f:53  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 Memory:34000000-34000800



lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     No scan results



bash: syntax error near unexpected token `'wlan0 | ndiswrapper''

---

### Post by pytheas22 on 2008-08-03
The card looks like it should be working, although I'm not sure why it's not seeing networks.  Sorry to ask you to post yet more information, but could we please see the output of:
```

dmesg | grep -e wlan -e ndiswrapper
```

EDIT: actually upon further investigation, I'm wondering if maybe you chose the wrong Windows driver to load into ndiswrapper.  This [page]("https://help.ubuntu.com/community/WifiDocs/Device/ipn2220#Whats%20Required") says that your card should be using a file called "neti2220" but you seem to be using "wlipnds."  Where did you get the Windows driver from, and if possible could you post a link to it please?

And also please still post the output of the dmesg command above.

---

### Post by Ricktron on 2008-08-03
> **pytheas22 said:**
> The card looks like it should be working, although I'm not sure why it's not seeing networks.  Sorry to ask you to post yet more information, but could we please see the output of:
```

dmesg | grep -e wlan -e ndiswrapper
```

EDIT: actually upon further investigation, I'm wondering if maybe you chose the wrong Windows driver to load into ndiswrapper.  This [page]("https://help.ubuntu.com/community/WifiDocs/Device/ipn2220#Whats%20Required") says that your card should be using a file called "neti2220" but you seem to be using "wlipnds."  Where did you get the Windows driver from, and if possible could you post a link to it please?

And also please still post the output of the dmesg command above.







all of my driver stuff came from the linksys website. here's the output:


[   40.210126] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[   40.315895] ndiswrapper: driver wlipnds (Cisco-Linksys, LLC.,01/05/2004,1.22.01.2004) loaded
[   40.352128] ndiswrapper: using IRQ 16
[   40.359345] wlan0: ethernet device 00:12:17:3d:6f:53 using NDIS driver: wlipnds, version: 0x10016, NDIS version: 0x501, vendor: 'INPROCOMM IPN2220 Wireless LAN Adapter', 17FE:2220.5.conf
[   40.359371] wlan0: encryption modes supported: WEP; TKIP with WPA; AES/CCMP with WPA
[   40.361256] usbcore: registered new interface driver ndiswrapper
[   59.163500] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 3497.165917] ndiswrapper: device wlan0 removed
[ 3498.156982] ndiswrapper: driver wlipnds (Cisco-Linksys, LLC.,01/05/2004,1.22.01.2004) loaded
[ 3498.194427] ndiswrapper: using IRQ 16
[ 3498.201631] wlan0: ethernet device 00:12:17:3d:6f:53 using NDIS driver: wlipnds, version: 0x10016, NDIS version: 0x501, vendor: 'INPROCOMM IPN2220 Wireless LAN Adapter', 17FE:2220.5.conf
[ 3498.202278] wlan0: encryption modes supported: WEP; TKIP with WPA; AES/CCMP with WPA

here's the link to the driver download from linksys

[http://www.linksys.com/servlet/Satellite?c=L_Download_C2&childpagename=US%2FLayout&cid=1115417109934&packedargs=sku%3D1121874577826&pagename=Linksys%2FCommon%2FVisitorWrapper](http://www.linksys.com/servlet/Satellite?c=L_Download_C2&childpagename=US%2FLayout&cid=1115417109934&packedargs=sku%3D1121874577826&pagename=Linksys%2FCommon%2FVisitorWrapper)

---

### Post by kevdog on 2008-08-03
That chipset is very new.  Very unfortunate for you.  A lot of people have had problems with this particular chipset, and only in some has ndiswrapper been the answer.  With others, it seems they simply gave up.  I need the pci ID hoping it will match the ID of others with a successful install.  Can you post:

lspci -n -vvv

---

### Post by Ricktron on 2008-08-03
> **kevdog said:**
> That chipset is very new.  Very unfortunate for you.  A lot of people have had problems with this particular chipset, and only in some has ndiswrapper been the answer.  With others, it seems they simply gave up.  I need the pci ID hoping it will match the ID of others with a successful install.  Can you post:

lspci -n -vvv



00:00.0 0600: 1039:0650 (rev 80)
	Subsystem: 1028:0195
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort+ >SERR- <PERR-
	Latency: 64
	Region 0: Memory at e0000000 (32-bit, non-prefetchable) [size=64M]
	Capabilities: <access denied>

00:01.0 0604: 1039:0001 (prog-if 00 [Normal decode])
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 99
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=68
	I/O behind bridge: 00009000-00009fff
	Memory behind bridge: e4300000-e43fffff
	Prefetchable memory behind bridge: e8000000-efffffff
	Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort+ <SERR- <PERR-
	BridgeCtl: Parity- SERR- NoISA+ VGA+ MAbort- >Reset- FastB2B-

00:02.0 0601: 1039:0962 (rev 25)
	Control: I/O+ Mem+ BusMaster+ SpecCycle+ MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0

00:02.1 0c05: 1039:0016
	Control: I/O+ Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Interrupt: pin B routed to IRQ 0
	Region 4: I/O ports at 8100 [size=32]

00:02.5 0101: 1039:5513 (prog-if 8a [Master SecP PriP])
	Subsystem: 1028:0195
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 128
	Interrupt: pin A routed to IRQ 22
	Region 0: I/O ports at 01f0 [size=8]
	Region 1: I/O ports at 03f4 [size=1]
	Region 2: I/O ports at 0170 [size=8]
	Region 3: I/O ports at 0374 [size=1]
	Region 4: I/O ports at 2800 [size=16]

00:02.6 0703: 1039:7013 (rev a0) (prog-if 00 [Generic])
	Subsystem: 1028:0195
	Control: I/O+ Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Interrupt: pin C routed to IRQ 17
	Region 0: I/O ports at 1000 [size=256]
	Region 1: I/O ports at 2400 [size=128]
	Capabilities: <access denied>

00:02.7 0401: 1039:7012 (rev a0)
	Subsystem: 1028:0195
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 173 (13000ns min, 2750ns max)
	Interrupt: pin C routed to IRQ 17
	Region 0: I/O ports at 1400 [size=256]
	Region 1: I/O ports at 2480 [size=128]
	Capabilities: <access denied>

00:03.0 0c03: 1039:7001 (rev 0f) (prog-if 10 [OHCI])
	Subsystem: 1028:0195
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 64 (20000ns max), Cache Line Size: 32 bytes
	Interrupt: pin A routed to IRQ 19
	Region 0: Memory at e4000000 (32-bit, non-prefetchable) [size=4K]

00:03.1 0c03: 1039:7001 (rev 0f) (prog-if 10 [OHCI])
	Subsystem: 1028:0195
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 64 (20000ns max), Cache Line Size: 32 bytes
	Interrupt: pin B routed to IRQ 20
	Region 0: Memory at e4001000 (32-bit, non-prefetchable) [size=4K]

00:03.2 0c03: 1039:7002 (prog-if 20 [EHCI])
	Subsystem: 1028:0195
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 64 (20000ns max)
	Interrupt: pin D routed to IRQ 21
	Region 0: Memory at e4002000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>

00:04.0 0200: 1039:0900 (rev 91)
	Subsystem: 1028:0195
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 173 (13000ns min, 2750ns max)
	Interrupt: pin A routed to IRQ 18
	Region 0: I/O ports at 1800 [size=256]
	Region 1: Memory at e4003000 (32-bit, non-prefetchable) [size=4K]
	[virtual] Expansion ROM at 38000000 [disabled] [size=128K]
	Capabilities: <access denied>

00:0a.0 0607: 104c:ac56
	Subsystem: 1028:0195
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 168, Cache Line Size: 128 bytes
	Interrupt: pin A routed to IRQ 16
	Region 0: Memory at e4004000 (32-bit, non-prefetchable) [size=4K]
	Bus: primary=00, secondary=02, subordinate=05, sec-latency=176
	Memory window 0: 30000000-33fff000 (prefetchable)
	Memory window 1: 34000000-37fff000
	I/O window 0: 00001c00-00001cff
	I/O window 1: 00002000-000020ff
	BridgeCtl: Parity- SERR- ISA- VGA- MAbort- >Reset- 16bInt- PostWrite+
	16-bit legacy interface ports at 0001

01:00.0 0300: 1039:6325 (prog-if 00 [VGA controller])
	Subsystem: 1028:0195
	Control: I/O+ Mem+ BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Interrupt: pin A routed to IRQ 7
	BIST result: 00
	Region 0: Memory at e8000000 (32-bit, prefetchable) [size=128M]
	Region 1: Memory at e4300000 (32-bit, non-prefetchable) [size=128K]
	Region 2: I/O ports at 9000 [size=128]
	Capabilities: <access denied>

02:00.0 0200: 17fe:2220
	Subsystem: 1737:0029
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 64 (8000ns min, 8000ns max)
	Interrupt: pin A routed to IRQ 16
	Region 0: I/O ports at 1c00 [size=32]
	Region 1: Memory at 34000800 (32-bit, non-prefetchable) [size=32]
	Region 2: Memory at 34000000 (32-bit, non-prefetchable) [size=2K]
	Capabilities: <access denied>

---

### Post by kevdog on 2008-08-03
How about lspci -n?

And do us all a favor and filter your results!! Use your head and post the relevant info.  We don't need to know about your audio, motherboard, video card, etc to get this problem fixed.  Just your networking card!

---

### Post by Ricktron on 2008-08-03
> **kevdog said:**
> How about lspci -n?

And do us all a favor and filter your results!! Use your head and post the relevant info.  We don't need to know about your audio, motherboard, video card, etc to get this problem fixed.  Just your networking card!

i'm sorry, i'm pretty new to all of this, so i'm not sure what's what out of all the code. i just type in what you guys have told me to put in and posted it. i do appreciate all the help though.

00:00.0 0600: 1039:0650 (rev 80)
00:01.0 0604: 1039:0001
00:02.0 0601: 1039:0962 (rev 25)
00:02.1 0c05: 1039:0016
00:02.5 0101: 1039:5513
00:02.6 0703: 1039:7013 (rev a0)
00:02.7 0401: 1039:7012 (rev a0)
00:03.0 0c03: 1039:7001 (rev 0f)
00:03.1 0c03: 1039:7001 (rev 0f)
00:03.2 0c03: 1039:7002
00:04.0 0200: 1039:0900 (rev 91)
00:0a.0 0607: 104c:ac56
01:00.0 0300: 1039:6325
02:00.0 0200: 17fe:2220

---

### Post by pytheas22 on 2008-08-03
From some quick Googling it seems like your card should work.  Take a look [here]("http://phildawson.tumblr.com/post/22267163/how-to-enable-linksys-airconn-inprocomm-ipn-2220"); I believe this addresses the exact same chipset as you (even though the vendor name of the card is different; don't worry about that).

First, remove the Windows driver that you currently have loaded into ndiswrapper:
```

sudo ndiswrapper -r wlipnds
```

(I think that should work; if you get an error message, please tell me what the output of "ndiswrapper -l" is).

Then follow the instructions on that page that I linked to above.  I think it will work.

If they don't work, someone else suggests that [this]("ftp://ftp.support.acer-euro.com/notebook/aspire_1670/driver/80211bg.zip") Windows driver will work.  But for now just try the instructions from Phil and see how it goes (I'm mostly noting this other driver so we'll have it later if necessary).

---

### Post by kevdog on 2008-08-03
Pytheas has seem to hit the issue on the head.  I think a lot of trial and error with different drivers are going to be needed here.

---

### Post by Ricktron on 2008-08-03
IT WORKED! thanks so much both of you for all the help and time.

---

### Post by pytheas22 on 2008-08-04
I'm glad the wireless works.

Ricktron: I have a somewhat off-topic question.  Does your wired Internet work as well?  I ask because I'm trying to help someone trouble shoot the same device--SiS900 PCI Fast Ethernet (rev 91)--over [here]("http://ubuntuforums.org/showthread.php?p=5523768#post5523768").  I actually ended up back at this thread accidentally (it's a bit surreal when Google lands you somewhere that you helped write only yesterday), but since it's fresh I was hoping you could tell me whether you've ever had trouble with your ethernet, and if so how you resolved it.

---

