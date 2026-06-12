---
title: "help my wireless isn't working"
date: 2008-09-01
forum: Networking &amp; Wireless
---

### Post by mrt88 on 2008-09-01
I know that there are a lot of these threads but I've read though a lot and I'm still no closer to getting my wireless to work

my card is installed and working fine as far as i can see, lspci -vvx gives me this for my card

02:06.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller (rev 20)
	Subsystem: Realtek Semiconductor Co., Ltd. RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR+ FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 64 (8000ns min, 16000ns max), Cache Line Size: 32 bytes
	Interrupt: pin A routed to IRQ 11
	Region 0: I/O ports at b800 [size=256]
	Region 1: Memory at feaffc00 (32-bit, non-prefetchable) [size=512]
	Capabilities: <access denied>
00: ec 10 85 81 17 01 90 02 20 00 00 02 08 40 00 00
10: 01 b8 00 00 00 fc af fe 00 00 00 00 00 00 00 00
20: 00 00 00 00 00 00 00 00 00 00 00 00 ec 10 85 81
30: 00 00 00 00 50 00 00 00 00 00 00 00 0b 01 20 40

and the hardware testing tells me that it's there and working fine

but ifconfig doesn't show me the card only my Ethernet connection

eth0      Link encap:Ethernet  HWaddr 00:17:31:61:e6:47  
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::217:31ff:fe61:e647/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:14688 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11693 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:17675186 (16.8 MB)  TX bytes:1541963 (1.4 MB)
          Interrupt:16 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2198 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2198 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:109900 (107.3 KB)  TX bytes:109900 (107.3 KB)

thats all i get from ifconfig and the wireless manager says the same thing

anyone know of anyway to get this working?

I'm using an Addon GWP110v3 card and an Asus K8N mobo, my computers a self build

any help would be greatly appreciated

---

### Post by mrt88 on 2008-09-10
anyone?

---

### Post by lilmale1 on 2008-09-10
did you use ndiswrapper to install you driver?

if you do have it ndiswrapper installed check this command to see if its the driver is there

the other log you showed doesn't really tell if you have it connected
just installed on ur computer. this command will tell you if you have a driver present 

ndiswrapper -l




i've have similar card that i installed the driver with ndiswrapper
and its model realtek rttl8180


so just let me know if you install it with ndiswrapper first

---

### Post by mrt88 on 2008-09-10
i didn't use ndiswrapper, i just plugged my card in and lspci told me it was there and the hardware checker recognised the card, the only thing that doesn't know the cards there is the network manager

---

