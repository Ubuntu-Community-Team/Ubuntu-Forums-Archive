---
title: "internal wifi in Advent 4489(MSI (Micro Star) 'Wind' netbook)"
date: 2008-12-22
forum: New to Ubuntu
---

### Post by csu1 on 2008-12-22
I'm running Ubuntu 8.10 and it will not recognize the internal wifi adaptor, apart from the new network manager being an ignorant *** as of late would someone please kindly direct me where to go and what to do to get the card working.

I am sorry for the lack of information on the internal wifi card as I can not find info's.

---

### Post by bobnutfield on 2008-12-22
Open a terminal and type:

> lspci

Towards the bottom of the output listing will be the description of your wireless chipset.  Post that info back.

---

### Post by csu1 on 2008-12-22
[PHP]00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
02:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8187SE Wireless LAN Controller (rev 22)

[/PHP]

Appreciate the quick reply, 

I assume one of those is the USB adaptor im using atm(can't unplug it as im d/l updates), i can't tell which one...

---

### Post by bobnutfield on 2008-12-22
> 02:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8187SE Wireless LAN Controller (rev 22)  

This is your wireless.  Now, I can only assume that this chipset uses the same module as the RTL8187B, which is the rtl8187.  The RTL8187B is actually internal USB, where your chipset is PCI, but it probably uses the same module.  Open a terminal and type:

> sudo ifconfig -a

This will list all of the network hardware your system recognizes.  The 2.6.27 kernel in Intrepid should handle that chipset just fine.

---

### Post by csu1 on 2008-12-22
...well, as with everything else in life it more than likely won't work:)

*waits fo 2.6.27 to download*

"*I'll be back"*!

...or will I

*fingers crossed* 

You are a kind person, thank you for your help.

---

### Post by bobnutfield on 2008-12-22
If you are running 8.10, you already have the 2.6.27 kernel. It is the kernel that Intrepid uses.  You don't need to download it separately.

---

### Post by csu1 on 2008-12-22
...the build of 8.10 I used was old so I was unsure. Update manager suggested it this kernel but it has not enabled the PCI card by default. 

This is frustrating, it's just sheer inexperience that lets me down:(

[PHP]ifconfig

pan0      Link encap:Ethernet  HWaddr 33:38:32:f9:ed:a1  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lspci -vvv

02:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8187SE Wireless LAN Controller (rev 22)
	Subsystem: Micro-Star International Co., Ltd. Device 6894
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 10
	Region 0: I/O ports at b000 [size=256]
	Region 1: Memory at dfc00000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: [40] Power Management version 3
		Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=375mA PME(D0+,D1+,D2+,D3hot+,D3cold-)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-
	Capabilities: [50] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
		Address: 0000000000000000  Data: 0000
	Capabilities: [70] Express (v1) Legacy Endpoint, MSI 00
		DevCap:	MaxPayload 256 bytes, PhantFunc 0, Latency L0s <128ns, L1 <2us
			ExtTag- AttnBtn- AttnInd- PwrInd- RBE+ FLReset-
		DevCtl:	Report errors: Correctable- Non-Fatal- Fatal- Unsupported-
			RlxdOrd- ExtTag- PhantFunc- AuxPwr- NoSnoop-
			MaxPayload 128 bytes, MaxReadReq 128 bytes
		DevSta:	CorrErr- UncorrErr- FatalErr- UnsuppReq- AuxPwr- TransPend-
		LnkCap:	Port #0, Speed 2.5GT/s, Width x1, ASPM L0s L1, Latency L0 <512ns, L1 <64us
			ClockPM+ Suprise- LLActRep- BwNot-
		LnkCtl:	ASPM Disabled; RCB 64 bytes Disabled- Retrain- CommClk+
			ExtSynch- ClockPM- AutWidDis- BWInt- AutBWInt-
		LnkSta:	Speed 2.5GT/s, Width x1, TrErr- Train- SlotClk+ DLActive- BWMgmt- ABWMgmt-
	Capabilities: [100] Advanced Error Reporting <?>
	Capabilities: [140] Virtual Channel <?>
	Capabilities: [160] Device Serial Number 00-21-85-b5-3f-45-00-00

lspci -k

01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev ff)
	Kernel driver in use: r8169
	Kernel modules: r8169
02:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8187SE Wireless LAN Controller (rev 22)

lspci -xxx

02:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8187SE Wireless LAN Controller (rev 22)
00: ec 10 99 81 07 00 10 00 22 00 80 02 10 00 00 00
10: 01 b0 00 00 00 00 c0 df 00 00 00 00 00 00 00 00
20: 00 00 00 00 00 00 00 00 00 00 00 00 62 14 94 68
30: 00 00 00 00 40 00 00 00 00 00 00 00 0a 01 00 00
40: 01 50 c3 7f 00 00 00 00 00 00 00 00 00 00 00 00
50: 05 70 80 00 00 00 00 00 00 00 00 00 00 00 00 00
60: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
70: 10 00 11 00 41 82 00 00 00 00 00 00 11 3c 07 00
80: 40 00 11 10 00 00 00 00 00 00 00 00 00 00 00 00
90: 00 00 00 00 10 00 00 00 00 00 00 00 00 00 00 00
a0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
b0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
c0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
d0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
e0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
f0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00

[/PHP]
...sudo ifconfig pan0: up; will not work because I do not know what I am doing<<<<<<<<<< ? what is the command to set for dynamic addresses?:confused:

I see that after lspci -k there does not seem to be drivers assigned...i'm close ... i must be ... tell me daz command !

CSU = n00b:lolflag:

---

### Post by csu1 on 2008-12-23
sorry for the bump as it is important i get this solved as I may have to return this notebook if not solved.

Thank you.

---

### Post by bobnutfield on 2008-12-23
Hello,

sorry so long getting back to you.  Probably a time difference from where you are. Was late here.  Anyway, open a terminal and type:

> lshw -C network

to see if it is showing that your network card is unclaimed.  Also, type:

> iwconfig

with no arguments to see if it gives the name the system knows your card as.  I don't believe it is pan0.  More likely it is wlan0.  The correct command you should have run is:

> sudo ifconfig pan0 up (leave the colon out).  Try these and post back.

---

### Post by jonnyara on 2009-05-20
Hi

I realise this post is old now, but for future reference for all, ubunutu and debian packages for this wireless card can be found here:


[http://boskastrona.ovh.org/](http://boskastrona.ovh.org/)

(found via [http://forums.msiwind.net/debian/rtl8187se-drivers-for-ubuntu-and-deb-packages-t4954.html](http://forums.msiwind.net/debian/rtl8187se-drivers-for-ubuntu-and-deb-packages-t4954.html))

---

