---
title: "wireless has stopped working"
date: 2009-10-26
forum: New to Ubuntu
---

### Post by vividia on 2009-10-26
I cannot see any networks in the Network Manager whatsoever.  I can't even see my own which I'm sitting right next to (The modem is literally 6 inches from my laptop).  I noticed it happened after I turned my computer back on one day after I did an update.  I didn't do a restart right away and just turned it off later.  I did update the linux headers and I'm wondering if that is the problem since it happened suddenly and totally right after an update.  I have wired but I go to college and need to the wireless on campus.

The kernel I have is 2.6.28-16.  I'm running 9.04 on a Gateway MT 3422.  

I'm usually hesitant to update linux kernels because I had an issue with that last year before Intrepid.  Any help?  Plaese?

---

### Post by Ravernomina on 2009-10-26
> **vividia said:**
> I cannot see any networks in the Network Manager whatsoever.  I can't even see my own which I'm sitting right next to (The modem is literally 6 inches from my laptop).  I noticed it happened after I turned my computer back on one day after I did an update.  I didn't do a restart right away and just turned it off later.  I did update the linux headers and I'm wondering if that is the problem since it happened suddenly and totally right after an update.  I have wired but I go to college and need to the wireless on campus.

The kernel I have is 2.6.28-16.  I'm running 9.04 on a Gateway MT 3422.  

I'm usually hesitant to update linux kernels because I had an issue with that last year before Intrepid.  Any help?  Plaese?

Run and post the output of this Command Please (:

```
lspci
```

---

### Post by vividia on 2009-10-26
Thanks for responding so fast.

> misha@misha-laptop:~$ lspci
00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
00:03.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:05.0 VGA compatible controller: nVidia Corporation MCP51 PCI-X GeForce Go 6100 (rev a2)
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
00:0a.3 Co-processor: nVidia Corporation MCP51 PMU (rev a3)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev f1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
06:09.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller (rev 20)
misha@misha-laptop:~$ 


---

### Post by Ravernomina on 2009-10-26
nice computer btw.... Alright did u need to install any proprietary drivers?

---

### Post by vividia on 2009-10-26
thanks. 

not lately.  which ones would affect this situation?

---

### Post by Ravernomina on 2009-10-26
> **vividia said:**
> thanks. 

not lately.  which ones would affect this situation?

Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8185 IEEE 802.11a/b/g Wireless 



Im not sure if the wireless driver is int he kernel itself or did u need to go to system>admin>hardware drivers

Btw you can IM me if you want to get this done faster

---

### Post by vividia on 2009-10-26
Went to sys>admin>hardware drivers and all that came up was nvidia.

I'm trying to remember.  I did the update while I was doing homework so I wasn't paying that much attention.  But I think there may have been updates for drivers in there.

I feel so guilty for not exercising more caution with my updates.  I really should know what I'm putting on my computer.

---

### Post by ctc26 on 2009-10-26
Do you have an LCD light and switch on the front or sides of your laptop (I'm guessing its a laptop)? If so, then make sure it is switched on. I ran into a problem with jaunty switching off wireless at boot, although the drivers had been loaded.

---

### Post by vividia on 2009-10-26
No, there is no switch.  I've looked before.  I almost wish it were that simple!  Thanks though.

We have found that the driver is the wrong one but for the life of me I can't seem to find one for a realtek 8185 to install.  Nor do I know if should keep NDISwrapper since I've read that drivers can work natively in Jaunty.

---

### Post by vividia on 2009-10-26
I am fed up with this.  After spending hours working on this with someone I'm worse off now then when I started.  My laptop does not even show that wireless is enabled.  I have ndiswrapper but I'm not sure if I should keep it. 

I once upon a time installed the driver but its now the wrong one.  And I can't remember how to do it.  I'm in tears I'm so frustrated!  I can't figure this out.  This can't be this hard and overwhelming!!!

---

### Post by vividia on 2009-10-26
I found instructions at [here]("http://jimvernon.com/archives/53") and followed them.  I ran ifconfig as it instructed and got this:

> eth0      Link encap:Ethernet  HWaddr 00:03:25:48:38:f1  
          inet addr:192.168.254.5  Bcast:192.168.254.255  Mask:255.255.255.0
          inet6 addr: fe80::203:25ff:fe48:38f1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:276464 errors:0 dropped:0 overruns:0 frame:0
          TX packets:245611 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:237317695 (237.3 MB)  TX bytes:95482114 (95.4 MB)
          Interrupt:21 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:984746 errors:0 dropped:0 overruns:0 frame:0
          TX packets:984746 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:620345649 (620.3 MB)  TX bytes:620345649 (620.3 MB)


---

### Post by vividia on 2009-10-26
After a reboot it does now say wireless is enabled in network manager.  But if I unplug the cable, it immediately goes offline without any searching for wireless.  So, moving back into the right direction.

I also checked windows wireless drivers.  It can detect the hardware but NOT a driver.  WTF?

---

### Post by Rayve on 2009-10-26
I'm no expert on this, but I just had my own wireless troubles today.  If my ifconfig on my netbook should be similar to your laptop, I think you should see a wlan0 in your ifconfig - lo is your loopback and eth0 is your wired connection, as far as I understand it.  My thread: [http://ubuntuforums.org/showthread.php?t=1300192](http://ubuntuforums.org/showthread.php?t=1300192)

And here is a link I found helpful -
[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide)

It pointed me in the right direction, at least.  If it turns out being a dhcp issue I may be able to help you a bit more (or the other links from my first thread should), but otherwise, I'm afraid I'm still learning too!

Good luck.

---

### Post by vividia on 2009-10-26
despite installing the driver, it still says I don't have one.  So the problem I think is on my end.  I just can't seem to get it to install.  I've done it before but for some reason, I can't now.  

There's just something I'm not getting?  I've gone through many troubleshooting pages with no affect.  And I have to leave for school now and won't be back till late.

---

### Post by twright on 2009-10-26
> **vividia said:**
> I am fed up with this.  After spending hours working on this with someone I'm worse off now then when I started.  My laptop does not even show that wireless is enabled.  I have ndiswrapper but I'm not sure if I should keep it. 

I once upon a time installed the driver but its now the wrong one.  And I can't remember how to do it.  I'm in tears I'm so frustrated!  I can't figure this out.  This can't be this hard and overwhelming!!!
If you need to go through that much hassle then it is certainly a bug somewhere...

If you want something quick and painless to try, the new 'Karmic Koala' release of Ubuntu will be out in 3 days and it includes better wireless support. If you try the release candidate (you can test via the live cd) or wait for the final release then most likely it should either work out of the box or after one click in hardware drivers.

Otherwise you could try pressing esc at startup and selecting the option to use an older version of the Ubuntu kernel which may work.

Good luck :-)

---

### Post by vividia on 2009-10-26
I just want my wireless back.  I don't want to upgrade to Karmic yet.  I don't think I should have to upgrade just to fix something that worked fine a little over 48 hours ago.

I have tried using previous kernels with the same results.

Someone has to know what is going on with this.  I can't be the only one out there.

---

### Post by vividia on 2009-10-27
Ok, so add this to the quandary: I went and tried to install a driver because ndiswrapper didn't list a driver.  Tracked down an .inf and tried to install it.  Ndiswrapper said it was already installed.  So............. why doesn't it work?

---

### Post by WolfRage on 2009-10-27
[COLOR=black][FONT=Verdana]I know you have a driver issue, but have you considered removing the proprietary drivers and installing WICD. WICD is much better than the standard Ubuntu wireless manager and I found that it solved my WIFI problems with my EEEPC700A without needing proprietary drivers.[/FONT][/COLOR]
 
Edit: Not sure if that is what you wanted to hear considering the gamet you have run through so far.

---

### Post by twright on 2009-10-27
> **WolfRage said:**
> [COLOR=black][FONT=Verdana]I know you have a driver issue, but have you considered removing the proprietary drivers and installing WICD. WICD is much better than the standard Ubuntu wireless manager and I found that it solved my WIFI problems with my EEEPC700A without needing proprietary drivers.[/FONT][/COLOR]
I would not recommend that...

The bug is probably in the underlying wireless driver and replacing a core component of the desktop with something less tested and less stable will likely cause problems later.

@vivida
I think that it would be quite hard to diagnose now seeing as the steps you have taken to fix the original problem might confuse matters. Could you try posting the output of the command lspci -vv and I will see what I can do to help.

---

### Post by vividia on 2009-10-27
Doing anything with WCID is probably over my head.

Here's the output from lspi -vv
> misha@misha-laptop:~$ sudo lspci -vv
00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
	Subsystem: Gateway 2000 Device 0317
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Capabilities: [44] HyperTransport: Slave or Primary Interface
		Command: BaseUnitID=0 UnitCnt=15 MastHost- DefDir- DUL-
		Link Control 0: CFlE+ CST- CFE- <LkFail- Init+ EOC- TXO- <CRCErr=0 IsocEn- LSEn+ ExtCTL- 64b-
		Link Config 0: MLWI=16bit DwFcIn- MLWO=16bit DwFcOut- LWI=16bit DwFcInEn- LWO=16bit DwFcOutEn-
		Link Control 1: CFlE+ CST- CFE- <LkFail- Init+ EOC- TXO- <CRCErr=0 IsocEn- LSEn+ ExtCTL- 64b-
		Link Config 1: MLWI=16bit DwFcIn- MLWO=16bit DwFcOut- LWI=8bit DwFcInEn- LWO=8bit DwFcOutEn-
		Revision ID: 1.03
		Link Frequency 0: 800MHz
		Link Error 0: <Prot- <Ovfl- <EOC- CTLTm-
		Link Frequency Capability 0: 200MHz+ 300MHz+ 400MHz+ 500MHz+ 600MHz+ 800MHz+ 1.0GHz+ 1.2GHz- 1.4GHz- 1.6GHz- Vend-
		Feature Capability: IsocFC+ LDTSTOP+ CRCTM- ECTLT- 64bA- UIDRD-
		Link Frequency 1: 800MHz
		Link Error 1: <Prot- <Ovfl- <EOC- CTLTm-
		Link Frequency Capability 1: 200MHz+ 300MHz+ 400MHz+ 500MHz+ 600MHz+ 800MHz+ 1.0GHz+ 1.2GHz- 1.4GHz- 1.6GHz- Vend-
		Error Handling: PFlE+ OFlE+ PFE- OFE- EOCFE- RFE- CRCFE- SERRFE- CF- RE- PNFE- ONFE- EOCNFE- RNFE- CRCNFE- SERRNFE-
		Prefetchable memory behind bridge Upper: 00-00
		Bus Number: 00
	Capabilities: [e0] HyperTransport: MSI Mapping Enable+ Fixed-
		Mapping Address Base: 00000000fee00000

00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
	Subsystem: Gateway 2000 Device 0317
	Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
	Status: Cap- 66MHz+ UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR+ <PERR- INTx-

00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
	Subsystem: Gateway 2000 Device 0317
	Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz+ UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-

00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
	Subsystem: Gateway 2000 Device 0317
	Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-

00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
	Subsystem: Gateway 2000 Device 0317
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0

00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
	Subsystem: Gateway 2000 Device 0317
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Capabilities: [44] #00 [00fe]
	Capabilities: [fc] #00 [0000]

00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
	Subsystem: Gateway 2000 Device 0317
	Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
	Status: Cap- 66MHz+ UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-

00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
	Subsystem: Gateway 2000 Device 0317
	Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz+ UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-

00:03.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx+
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 64 bytes
	Bus: primary=00, secondary=03, subordinate=04, sec-latency=0
	I/O behind bridge: 00009000-00009fff
	Memory behind bridge: fa100000-fa8fffff
	Prefetchable memory behind bridge: 00000000bdf00000-00000000bfefffff
	Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
	BridgeCtl: Parity- SERR- NoISA+ VGA- MAbort- >Reset- FastB2B-
		PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
	Capabilities: [40] Subsystem: nVidia Corporation Device 0000
	Capabilities: [48] Power Management version 2
		Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0+,D1+,D2+,D3hot+,D3cold+)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-
	Capabilities: [50] Message Signalled Interrupts: Mask- 64bit+ Queue=0/1 Enable+
		Address: 00000000fee0300c  Data: 4149
	Capabilities: [60] HyperTransport: MSI Mapping Enable+ Fixed-
		Mapping Address Base: 00000000fee00000
	Capabilities: [80] Express (v1) Root Port (Slot+), MSI 00
		DevCap:	MaxPayload 128 bytes, PhantFunc 0, Latency L0s <512ns, L1 <4us
			ExtTag- RBE- FLReset-
		DevCtl:	Report errors: Correctable- Non-Fatal- Fatal- Unsupported-
			RlxdOrd+ ExtTag- PhantFunc- AuxPwr- NoSnoop+
			MaxPayload 128 bytes, MaxReadReq 512 bytes
		DevSta:	CorrErr- UncorrErr- FatalErr- UnsuppReq- AuxPwr- TransPend-
		LnkCap:	Port #1, Speed 2.5GT/s, Width x1, ASPM L0s L1, Latency L0 <512ns, L1 <4us
			ClockPM- Suprise- LLActRep+ BwNot-
		LnkCtl:	ASPM Disabled; RCB 64 bytes Disabled- Retrain- CommClk-
			ExtSynch- ClockPM- AutWidDis- BWInt- AutBWInt-
		LnkSta:	Speed 2.5GT/s, Width x1, TrErr- Train- SlotClk+ DLActive- BWMgmt- ABWMgmt-
		SltCap:	AttnBtn- PwrCtrl- MRL- AttnInd- PwrInd- HotPlug- Surpise-
			Slot #  0, PowerLimit 0.000000; Interlock- NoCompl-
		SltCtl:	Enable: AttnBtn+ PwrFlt+ MRL- PresDet- CmdCplt- HPIrq+ LinkChg+
			Control: AttnInd Off, PwrInd On, Power- Interlock-
		SltSta:	Status: AttnBtn- PowerFlt- MRL- CmdCplt- PresDet- Interlock-
			Changed: MRL- PresDet- LinkState-
		RootCtl: ErrCorrectable- ErrNon-Fatal- ErrFatal- PMEIntEna- CRSVisible-
		RootCap: CRSVisible-
		RootSta: PME ReqID 0000, PMEStatus- PMEPending-
	Capabilities: [100] Virtual Channel <?>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:05.0 VGA compatible controller: nVidia Corporation MCP51 PCI-X GeForce Go 6100 (rev a2)
	Subsystem: Gateway 2000 Device 0317
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin A routed to IRQ 20
	Region 0: Memory at b2000000 (32-bit, non-prefetchable) [size=16M]
	Region 1: Memory at c0000000 (64-bit, prefetchable) [size=256M]
	Region 3: Memory at b1000000 (64-bit, non-prefetchable) [size=16M]
	[virtual] Expansion ROM at 88000000 [disabled] [size=128K]
	Capabilities: [48] Power Management version 2
		Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-
	Capabilities: [50] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
		Address: 0000000000000000  Data: 0000
	Kernel driver in use: nvidia
	Kernel modules: nvidia, nvidiafb

00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
	Subsystem: Gateway 2000 Device 0317
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Capabilities: [44] HyperTransport: Slave or Primary Interface
		Command: BaseUnitID=9 UnitCnt=15 MastHost- DefDir- DUL-
		Link Control 0: CFlE+ CST- CFE- <LkFail- Init+ EOC- TXO- <CRCErr=0 IsocEn- LSEn+ ExtCTL- 64b-
		Link Config 0: MLWI=8bit DwFcIn- MLWO=8bit DwFcOut- LWI=8bit DwFcInEn- LWO=8bit DwFcOutEn-
		Link Control 1: CFlE- CST- CFE- <LkFail+ Init- EOC+ TXO+ <CRCErr=0 IsocEn- LSEn- ExtCTL- 64b-
		Link Config 1: MLWI=8bit DwFcIn- MLWO=8bit DwFcOut- LWI=8bit DwFcInEn- LWO=8bit DwFcOutEn-
		Revision ID: 1.03
		Link Frequency 0: 800MHz
		Link Error 0: <Prot- <Ovfl- <EOC- CTLTm-
		Link Frequency Capability 0: 200MHz+ 300MHz+ 400MHz+ 500MHz+ 600MHz+ 800MHz+ 1.0GHz+ 1.2GHz- 1.4GHz- 1.6GHz- Vend-
		Feature Capability: IsocFC+ LDTSTOP+ CRCTM- ECTLT- 64bA- UIDRD-
		Link Frequency 1: 200MHz
		Link Error 1: <Prot- <Ovfl- <EOC- CTLTm-
		Link Frequency Capability 1: 200MHz- 300MHz- 400MHz- 500MHz- 600MHz- 800MHz- 1.0GHz- 1.2GHz- 1.4GHz- 1.6GHz- Vend-
		Error Handling: PFlE+ OFlE+ PFE- OFE- EOCFE- RFE- CRCFE- SERRFE- CF- RE- PNFE- ONFE- EOCNFE- RNFE- CRCNFE- SERRNFE-
		Prefetchable memory behind bridge Upper: 00-00
		Bus Number: 00
	Capabilities: [e0] HyperTransport: MSI Mapping Enable+ Fixed-
		Mapping Address Base: 00000000fee00000

00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
	Subsystem: Gateway 2000 Device 0317
	Control: I/O+ Mem+ BusMaster+ SpecCycle+ MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0

00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
	Subsystem: Gateway 2000 Device 0317
	Control: I/O+ Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Interrupt: pin A routed to IRQ 10
	Region 4: I/O ports at 3040 [size=64]
	Region 5: I/O ports at 3000 [size=64]
	Capabilities: [44] Power Management version 2
		Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot+,D3cold+)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-
	Kernel driver in use: nForce2_smbus
	Kernel modules: i2c-nforce2

00:0a.3 Co-processor: nVidia Corporation MCP51 PMU (rev a3)
	Subsystem: Gateway 2000 Device 0317
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0 (750ns min, 250ns max)
	Interrupt: pin B routed to IRQ 10
	Region 0: Memory at b0040000 (32-bit, non-prefetchable) [size=256K]

00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3) (prog-if 10)
	Subsystem: Gateway 2000 Device 0317
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0 (750ns min, 250ns max)
	Interrupt: pin A routed to IRQ 22
	Region 0: Memory at b0004000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: [44] Power Management version 2
		Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0+,D1+,D2+,D3hot+,D3cold+)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-
	Kernel driver in use: ohci_hcd

00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3) (prog-if 20)
	Subsystem: Gateway 2000 Device 0317
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0 (750ns min, 250ns max)
	Interrupt: pin B routed to IRQ 23
	Region 0: Memory at b0005000 (32-bit, non-prefetchable) [size=256]
	Capabilities: [44] Debug port: BAR=1 offset=0098
	Capabilities: [80] Power Management version 2
		Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0+,D1+,D2+,D3hot+,D3cold+)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME+
	Kernel driver in use: ehci_hcd

00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev f1) (prog-if 8a [Master SecP PriP])
	Subsystem: Device f07b:0317
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0 (750ns min, 250ns max)
	Region 0: [virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
	Region 1: [virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
	Region 2: [virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
	Region 3: [virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
	Region 4: I/O ports at 3080 [size=16]
	Capabilities: [44] Power Management version 2
		Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-
	Kernel driver in use: pata_amd

00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2) (prog-if 01)
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Bus: primary=00, secondary=06, subordinate=06, sec-latency=64
	I/O behind bridge: 00006000-00006fff
	Memory behind bridge: b3400000-b34fffff
	Secondary status: 66MHz- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- <SERR- <PERR-
	BridgeCtl: Parity- SERR- NoISA+ VGA- MAbort- >Reset- FastB2B-
		PriDiscTmr- SecDiscTmr+ DiscTmrStat- DiscTmrSERREn-
	Capabilities: [b8] Subsystem: Gammagraphx, Inc. (or missing ID) Device 0000
	Capabilities: [8c] HyperTransport: MSI Mapping Enable+ Fixed-
		Mapping Address Base: 00000000fee00000

00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
	Subsystem: Gateway 2000 Device 0317
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0 (500ns min, 1250ns max)
	Interrupt: pin B routed to IRQ 19
	Region 0: Memory at b0000000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: [44] Power Management version 2
		Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot+,D3cold+)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-
	Capabilities: [50] Message Signalled Interrupts: Mask+ 64bit+ Queue=0/0 Enable-
		Address: 0000000000000000  Data: 0000
		Masking: 00000000  Pending: 00000000
	Capabilities: [6c] HyperTransport: MSI Mapping Enable+ Fixed+
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)
	Subsystem: Gateway 2000 Device 0317
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0 (250ns min, 5000ns max)
	Interrupt: pin A routed to IRQ 21
	Region 0: Memory at b0006000 (32-bit, non-prefetchable) [size=4K]
	Region 1: I/O ports at 3090 [size=8]
	Capabilities: [44] Power Management version 2
		Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0+,D1+,D2+,D3hot+,D3cold+)
		Status: D0 PME-Enable+ DSel=0 DScale=0 PME-
	Kernel driver in use: forcedeth
	Kernel modules: forcedeth

00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
	Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Capabilities: [80] HyperTransport: Host or Secondary Interface
		!!! Possibly incomplete decoding
		Command: WarmRst+ DblEnd-
		Link Control: CFlE- CST- CFE- <LkFail- Init+ EOC- TXO- <CRCErr=8
		Link Config: MLWI=16bit MLWO=16bit LWI=16bit LWO=16bit
		Revision ID: 1.02

00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
	Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-

00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
	Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-

00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
	Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Capabilities: [f0] Secure device <?>
	Kernel driver in use: k8temp
	Kernel modules: k8temp

06:09.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller (rev 20)
	Subsystem: Realtek Semiconductor Co., Ltd. Device 8225
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 64 (8000ns min, 16000ns max), Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 11
	Region 0: I/O ports at 6000 [size=256]
	Region 1: Memory at b3400000 (32-bit, non-prefetchable) [size=512]
	Capabilities: [50] Power Management version 2
		Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=375mA PME(D0-,D1+,D2+,D3hot+,D3cold+)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-
	Kernel driver in use: ndiswrapper
	Kernel modules: rtl8180




---

### Post by twright on 2009-10-27
Right, the first thing I recommend is that you try following the instructions here: [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper) to uninstall ndiswapper, and then we can try and get the default drivers into a working state again.

---

### Post by vividia on 2009-10-27
I went to the page but I can't see how to uninstall it.

---

### Post by vividia on 2009-10-27
I actually have to depart for class.  I'll be back in 8.5 hours.  

As an aside, am I the only person here NOT testing Karmic?

---

### Post by WolfRage on 2009-10-27
I am no longer testing Karamic. Went back to Hardy for my POS graphics card.

---

### Post by twright on 2009-10-27
> **vividia said:**
> I actually have to depart for class.  I'll be back in 8.5 hours.  

As an aside, am I the only person here NOT testing Karmic?
It does seem too be very popular :-) (one of the reasons I recommended upgrading rather than backtracking until your drivers are usable again)

Ok, that page does not seem to be of much help :-) (maybe I should have a look later)

From memory these commands should do the trick:
```

sudo su
ndiswrapper -l # lists your drivers
ndiswrapper -r <put name of driver here>
apt-get autoremove ndiswrapper

```

---

### Post by bkratz on 2009-10-27
> **vividia said:**
> I actually have to depart for class.  I'll be back in 8.5 hours.  

As an aside, am I the only person here NOT testing Karmic?


I found your original thread here

[http://ubuntuforums.org/showthread.php?t=1106733&highlight=RTL-8185](http://ubuntuforums.org/showthread.php?t=1106733&highlight=RTL-8185)

Perhaps the commands issued in post 38 and then a reboot corrected it originally. Hope so.

(Still on 9.04 although "seeding" 9.10RC)

---

### Post by vividia on 2009-10-27
@bkratz I never actually solved the problem.  it just seemed to fix itself as strange as that may sound.  So I never thought to go back to that thread since nothing worked.

@twright i did the commands but it doesn't seem to have done anything.  

> root@misha-laptop:/home/misha# ndiswrapper -l # lists your drivers
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
net8185 : driver installed
	device (10EC:8185) present (alternate driver: rtl8180)


> root@misha-laptop:/home/misha# ndiswrapper -r net8185
root@misha-laptop:/home/misha# apt-get autoremove ndiswrapper
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ndiswrapper


---

### Post by vividia on 2009-10-27
I went back in grub again and tried running with 2.6.27-14 and it was pointless.  I get the same problems there.

I am not completely opposed to going to Karmic.  I'm gonna have to upgrade only.  i can't do a clean install which to me is the preferable method.  I have too much data and I'm all out of external hard drive space.  And I'm dirt broke.  I can't just go get another one. 

Does anyone know if upgrading only would *fix* this problem?  Would I have to do a clean install to get those results?

---

### Post by twright on 2009-10-27
> **vividia said:**
> I went back in grub again and tried running with 2.6.27-14 and it was pointless.  I get the same problems there.

I am not completely opposed to going to Karmic.  I'm gonna have to upgrade only.  i can't do a clean install which to me is the preferable method.  I have too much data and I'm all out of external hard drive space.  And I'm dirt broke.  I can't just go get another one. 

Does anyone know if upgrading only would *fix* this problem?  Would I have to do a clean install to get those results?
It might as upgrading should reset a lot of stuff to it's default settings but I would not count on it. However you can do a fresh install whilst keeping your home folder - it is still worth backing up but your files should be kept. All you need to do is boot the livecd, select manual, select your old root partition, select use as ext4, set the mount point as / and **make sure the format button is firmly, 100% unticked** (this is the bit which tells it not to delete your data).

I am only suggesting it as your system seems to be in a complex state and if you were intending to upgrade soon it might save you some pain.

In any case to finish uninstalling ndiswrapper can you try the command:
```
sudo apt-get autoremove ndiswrapper-common
```

Then can you reboot and copy and paste the output of lspci -vv again.

---

### Post by JBAlaska on 2009-10-27
If you haven't removed ndiswrapper yet (And it was working fine before the upgrade) Try blacklisting the native driver, it may be as easy as that.

Do this in a term:
```
gksudo gedit /etc/modprobe.d/blacklist
```

Add This to the list if it is not there already:
```
# blacklist r8180 linux driver
blacklist r8180
```

Now you could finish without rebooting...but it's much simpler to just reboot in this case.

Hope this helps.

---

### Post by vividia on 2009-10-27
Thanks for the info about Karmic.  i'm gonna see about using an online backup site to put the data I want to keep and then do a clean install.  i'm nervous about the migration to ext4 so on the off chance that it turns out like my update...  

Did the removal and then lspci -vv and got this wonderful bit.

Oh, and thank you for this help. 

> misha@misha-laptop:~$ sudo lspci -vv
00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
	Subsystem: Gateway 2000 Device 0317
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Capabilities: [44] HyperTransport: Slave or Primary Interface
		Command: BaseUnitID=0 UnitCnt=15 MastHost- DefDir- DUL-
		Link Control 0: CFlE+ CST- CFE- <LkFail- Init+ EOC- TXO- <CRCErr=0 IsocEn- LSEn+ ExtCTL- 64b-
		Link Config 0: MLWI=16bit DwFcIn- MLWO=16bit DwFcOut- LWI=16bit DwFcInEn- LWO=16bit DwFcOutEn-
		Link Control 1: CFlE+ CST- CFE- <LkFail- Init+ EOC- TXO- <CRCErr=0 IsocEn- LSEn+ ExtCTL- 64b-
		Link Config 1: MLWI=16bit DwFcIn- MLWO=16bit DwFcOut- LWI=8bit DwFcInEn- LWO=8bit DwFcOutEn-
		Revision ID: 1.03
		Link Frequency 0: 800MHz
		Link Error 0: <Prot- <Ovfl- <EOC- CTLTm-
		Link Frequency Capability 0: 200MHz+ 300MHz+ 400MHz+ 500MHz+ 600MHz+ 800MHz+ 1.0GHz+ 1.2GHz- 1.4GHz- 1.6GHz- Vend-
		Feature Capability: IsocFC+ LDTSTOP+ CRCTM- ECTLT- 64bA- UIDRD-
		Link Frequency 1: 800MHz
		Link Error 1: <Prot- <Ovfl- <EOC- CTLTm-
		Link Frequency Capability 1: 200MHz+ 300MHz+ 400MHz+ 500MHz+ 600MHz+ 800MHz+ 1.0GHz+ 1.2GHz- 1.4GHz- 1.6GHz- Vend-
		Error Handling: PFlE+ OFlE+ PFE- OFE- EOCFE- RFE- CRCFE- SERRFE- CF- RE- PNFE- ONFE- EOCNFE- RNFE- CRCNFE- SERRNFE-
		Prefetchable memory behind bridge Upper: 00-00
		Bus Number: 00
	Capabilities: [e0] HyperTransport: MSI Mapping Enable+ Fixed-
		Mapping Address Base: 00000000fee00000

00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
	Subsystem: Gateway 2000 Device 0317
	Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
	Status: Cap- 66MHz+ UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR+ <PERR- INTx-

00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
	Subsystem: Gateway 2000 Device 0317
	Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz+ UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-

00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
	Subsystem: Gateway 2000 Device 0317
	Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-

00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
	Subsystem: Gateway 2000 Device 0317
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0

00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
	Subsystem: Gateway 2000 Device 0317
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Capabilities: [44] #00 [00fe]
	Capabilities: [fc] #00 [0000]

00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
	Subsystem: Gateway 2000 Device 0317
	Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
	Status: Cap- 66MHz+ UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-

00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
	Subsystem: Gateway 2000 Device 0317
	Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz+ UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-

00:03.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx+
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 64 bytes
	Bus: primary=00, secondary=03, subordinate=04, sec-latency=0
	I/O behind bridge: 00009000-00009fff
	Memory behind bridge: fa100000-fa8fffff
	Prefetchable memory behind bridge: 00000000bdf00000-00000000bfefffff
	Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
	BridgeCtl: Parity- SERR- NoISA+ VGA- MAbort- >Reset- FastB2B-
		PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
	Capabilities: [40] Subsystem: nVidia Corporation Device 0000
	Capabilities: [48] Power Management version 2
		Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0+,D1+,D2+,D3hot+,D3cold+)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-
	Capabilities: [50] Message Signalled Interrupts: Mask- 64bit+ Queue=0/1 Enable+
		Address: 00000000fee0300c  Data: 4149
	Capabilities: [60] HyperTransport: MSI Mapping Enable+ Fixed-
		Mapping Address Base: 00000000fee00000
	Capabilities: [80] Express (v1) Root Port (Slot+), MSI 00
		DevCap:	MaxPayload 128 bytes, PhantFunc 0, Latency L0s <512ns, L1 <4us
			ExtTag- RBE- FLReset-
		DevCtl:	Report errors: Correctable- Non-Fatal- Fatal- Unsupported-
			RlxdOrd+ ExtTag- PhantFunc- AuxPwr- NoSnoop+
			MaxPayload 128 bytes, MaxReadReq 512 bytes
		DevSta:	CorrErr- UncorrErr- FatalErr- UnsuppReq- AuxPwr- TransPend-
		LnkCap:	Port #1, Speed 2.5GT/s, Width x1, ASPM L0s L1, Latency L0 <512ns, L1 <4us
			ClockPM- Suprise- LLActRep+ BwNot-
		LnkCtl:	ASPM Disabled; RCB 64 bytes Disabled- Retrain- CommClk-
			ExtSynch- ClockPM- AutWidDis- BWInt- AutBWInt-
		LnkSta:	Speed 2.5GT/s, Width x1, TrErr- Train- SlotClk+ DLActive- BWMgmt- ABWMgmt-
		SltCap:	AttnBtn- PwrCtrl- MRL- AttnInd- PwrInd- HotPlug- Surpise-
			Slot #  0, PowerLimit 0.000000; Interlock- NoCompl-
		SltCtl:	Enable: AttnBtn+ PwrFlt+ MRL- PresDet- CmdCplt- HPIrq+ LinkChg+
			Control: AttnInd Off, PwrInd On, Power- Interlock-
		SltSta:	Status: AttnBtn- PowerFlt- MRL- CmdCplt- PresDet- Interlock-
			Changed: MRL- PresDet- LinkState-
		RootCtl: ErrCorrectable- ErrNon-Fatal- ErrFatal- PMEIntEna- CRSVisible-
		RootCap: CRSVisible-
		RootSta: PME ReqID 0000, PMEStatus- PMEPending-
	Capabilities: [100] Virtual Channel <?>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:05.0 VGA compatible controller: nVidia Corporation MCP51 PCI-X GeForce Go 6100 (rev a2)
	Subsystem: Gateway 2000 Device 0317
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin A routed to IRQ 20
	Region 0: Memory at b2000000 (32-bit, non-prefetchable) [size=16M]
	Region 1: Memory at c0000000 (64-bit, prefetchable) [size=256M]
	Region 3: Memory at b1000000 (64-bit, non-prefetchable) [size=16M]
	[virtual] Expansion ROM at 88000000 [disabled] [size=128K]
	Capabilities: [48] Power Management version 2
		Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-
	Capabilities: [50] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
		Address: 0000000000000000  Data: 0000
	Kernel driver in use: nvidia
	Kernel modules: nvidia, nvidiafb

00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
	Subsystem: Gateway 2000 Device 0317
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Capabilities: [44] HyperTransport: Slave or Primary Interface
		Command: BaseUnitID=9 UnitCnt=15 MastHost- DefDir- DUL-
		Link Control 0: CFlE+ CST- CFE- <LkFail- Init+ EOC- TXO- <CRCErr=0 IsocEn- LSEn+ ExtCTL- 64b-
		Link Config 0: MLWI=8bit DwFcIn- MLWO=8bit DwFcOut- LWI=8bit DwFcInEn- LWO=8bit DwFcOutEn-
		Link Control 1: CFlE- CST- CFE- <LkFail+ Init- EOC+ TXO+ <CRCErr=0 IsocEn- LSEn- ExtCTL- 64b-
		Link Config 1: MLWI=8bit DwFcIn- MLWO=8bit DwFcOut- LWI=8bit DwFcInEn- LWO=8bit DwFcOutEn-
		Revision ID: 1.03
		Link Frequency 0: 800MHz
		Link Error 0: <Prot- <Ovfl- <EOC- CTLTm-
		Link Frequency Capability 0: 200MHz+ 300MHz+ 400MHz+ 500MHz+ 600MHz+ 800MHz+ 1.0GHz+ 1.2GHz- 1.4GHz- 1.6GHz- Vend-
		Feature Capability: IsocFC+ LDTSTOP+ CRCTM- ECTLT- 64bA- UIDRD-
		Link Frequency 1: 200MHz
		Link Error 1: <Prot- <Ovfl- <EOC- CTLTm-
		Link Frequency Capability 1: 200MHz- 300MHz- 400MHz- 500MHz- 600MHz- 800MHz- 1.0GHz- 1.2GHz- 1.4GHz- 1.6GHz- Vend-
		Error Handling: PFlE+ OFlE+ PFE- OFE- EOCFE- RFE- CRCFE- SERRFE- CF- RE- PNFE- ONFE- EOCNFE- RNFE- CRCNFE- SERRNFE-
		Prefetchable memory behind bridge Upper: 00-00
		Bus Number: 00
	Capabilities: [e0] HyperTransport: MSI Mapping Enable+ Fixed-
		Mapping Address Base: 00000000fee00000

00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
	Subsystem: Gateway 2000 Device 0317
	Control: I/O+ Mem+ BusMaster+ SpecCycle+ MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0

00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
	Subsystem: Gateway 2000 Device 0317
	Control: I/O+ Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Interrupt: pin A routed to IRQ 10
	Region 4: I/O ports at 3040 [size=64]
	Region 5: I/O ports at 3000 [size=64]
	Capabilities: [44] Power Management version 2
		Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot+,D3cold+)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-
	Kernel driver in use: nForce2_smbus
	Kernel modules: i2c-nforce2

00:0a.3 Co-processor: nVidia Corporation MCP51 PMU (rev a3)
	Subsystem: Gateway 2000 Device 0317
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0 (750ns min, 250ns max)
	Interrupt: pin B routed to IRQ 10
	Region 0: Memory at b0040000 (32-bit, non-prefetchable) [size=256K]

00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3) (prog-if 10)
	Subsystem: Gateway 2000 Device 0317
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0 (750ns min, 250ns max)
	Interrupt: pin A routed to IRQ 22
	Region 0: Memory at b0004000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: [44] Power Management version 2
		Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0+,D1+,D2+,D3hot+,D3cold+)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-
	Kernel driver in use: ohci_hcd

00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3) (prog-if 20)
	Subsystem: Gateway 2000 Device 0317
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0 (750ns min, 250ns max)
	Interrupt: pin B routed to IRQ 23
	Region 0: Memory at b0005000 (32-bit, non-prefetchable) [size=256]
	Capabilities: [44] Debug port: BAR=1 offset=0098
	Capabilities: [80] Power Management version 2
		Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0+,D1+,D2+,D3hot+,D3cold+)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME+
	Kernel driver in use: ehci_hcd

00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev f1) (prog-if 8a [Master SecP PriP])
	Subsystem: Device f07b:0317
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0 (750ns min, 250ns max)
	Region 0: [virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
	Region 1: [virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
	Region 2: [virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
	Region 3: [virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
	Region 4: I/O ports at 3080 [size=16]
	Capabilities: [44] Power Management version 2
		Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-
	Kernel driver in use: pata_amd

00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2) (prog-if 01)
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Bus: primary=00, secondary=06, subordinate=06, sec-latency=64
	I/O behind bridge: 00006000-00006fff
	Memory behind bridge: b3400000-b34fffff
	Secondary status: 66MHz- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- <SERR- <PERR-
	BridgeCtl: Parity- SERR- NoISA+ VGA- MAbort- >Reset- FastB2B-
		PriDiscTmr- SecDiscTmr+ DiscTmrStat- DiscTmrSERREn-
	Capabilities: [b8] Subsystem: Gammagraphx, Inc. (or missing ID) Device 0000
	Capabilities: [8c] HyperTransport: MSI Mapping Enable+ Fixed-
		Mapping Address Base: 00000000fee00000

00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
	Subsystem: Gateway 2000 Device 0317
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0 (500ns min, 1250ns max)
	Interrupt: pin B routed to IRQ 19
	Region 0: Memory at b0000000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: [44] Power Management version 2
		Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot+,D3cold+)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-
	Capabilities: [50] Message Signalled Interrupts: Mask+ 64bit+ Queue=0/0 Enable-
		Address: 0000000000000000  Data: 0000
		Masking: 00000000  Pending: 00000000
	Capabilities: [6c] HyperTransport: MSI Mapping Enable+ Fixed+
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)
	Subsystem: Gateway 2000 Device 0317
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0 (250ns min, 5000ns max)
	Interrupt: pin A routed to IRQ 21
	Region 0: Memory at b0006000 (32-bit, non-prefetchable) [size=4K]
	Region 1: I/O ports at 3090 [size=8]
	Capabilities: [44] Power Management version 2
		Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0+,D1+,D2+,D3hot+,D3cold+)
		Status: D0 PME-Enable+ DSel=0 DScale=0 PME-
	Kernel driver in use: forcedeth
	Kernel modules: forcedeth

00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
	Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Capabilities: [80] HyperTransport: Host or Secondary Interface
		!!! Possibly incomplete decoding
		Command: WarmRst+ DblEnd-
		Link Control: CFlE- CST- CFE- <LkFail- Init+ EOC- TXO- <CRCErr=8
		Link Config: MLWI=16bit MLWO=16bit LWI=16bit LWO=16bit
		Revision ID: 1.02

00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
	Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-

00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
	Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-

00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
	Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Capabilities: [f0] Secure device <?>
	Kernel driver in use: k8temp
	Kernel modules: k8temp

06:09.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller (rev 20)
	Subsystem: Realtek Semiconductor Co., Ltd. Device 8225
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0 (8000ns min, 16000ns max), Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 11
	Region 0: I/O ports at 6000 [size=256]
	Region 1: Memory at b3400000 (32-bit, non-prefetchable) [size=512]
	Capabilities: [50] Power Management version 2
		Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=375mA PME(D0-,D1+,D2+,D3hot+,D3cold+)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-
	Kernel modules: rtl8180


---

### Post by JBAlaska on 2009-10-27
If you look at the last line in your post "Kernel modules: rtl8180" this Module is most likly conflicting with ndiswrapper, try blacklisting the rtl8180 Module per my prior post, it's worth a try and will only take a few mins.

---

### Post by twright on 2009-10-28
I have done some extensive googling and quite a few other people have encountered the same problem without much luck and have also been unable to configure it with ndiswrapper.

One thing you could try doing is pressing esc at boot and seeing if you can boot into an older kernel, which might not be impacted by the bug or reinstalling any restricted drivers (in Administration->Hardware Drivers).

If nothing works then I recommend submitting a bug at launchpad.net or upgrading when you can (the easy way out).

If you do want to try ndiswrapper again you will need to reinstall it first; it needs to be uninstalled to have a chance of using the native drivers though.

---

### Post by vividia on 2009-10-28
> **JBAlaska said:**
> If you look at the last line in your post "Kernel modules: rtl8180" this Module is most likly conflicting with ndiswrapper, try blacklisting the rtl8180 Module per my prior post, it's worth a try and will only take a few mins.

Ok.  I just thought I'd go with the person who had been helping first.  than, if that didn't work, go with the other one.

---

