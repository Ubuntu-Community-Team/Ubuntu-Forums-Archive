---
title: "ath9k driver issue in Kubuntu 8.10 Beta"
date: 2008-10-24
forum: Networking &amp; Wireless
---

### Post by Alonsus on 2008-10-24
I am currently using Kubuntu 8.10 Beta AMD64 (kernel 2.6.27-7-generic) and am experiencing some driver related issues with ath9k and my DWA-552 card.

Scanning for networks, and connecting works correctly. However, the connection just stops working after a couple of minutes (1 to 5), the connection doesn't drop though, I'll just get zero throughput. After about 30 seconds to a minute, OR if I manually reconnect it will function correctly again. This cycle continues after every re-connect.

The wireless network is WPA encrypted.

I have seen similar issues elsewhere with no solutions, I am assuming this is some bug that will be fixed eventually. Just wondering if anyone has anymore information on this issue.

Thanks

---

### Post by luvsbluecat209 on 2008-10-28
I too have 8.10 with the same card i have had no issues though it works perfect.

---

### Post by bpeisley on 2008-11-01
I am having the same problem that Alonsus is describing.

I am running Ubuntu 8.10 (final release now, though I had the problem in the beta an the release candidate).

I'm using an Asus P5B Motherboard with an Intel Core 2 Quad Q6600 @ 2.4Ghz.  My wireless card is a D-Link DWA-556 (PCI Express version of the DWA-552 Alonsus has), and I'm connecting using 802.11n to a D-Link DIR-655 router.  The network I am connecting to is using WPA2.

In case it helps, I've included the output from lspci -vvv for my wireless card below.

04:00.0 Network controller: Atheros Communications Inc. AR5008 Wireless Network Adapter (rev 01)
	Subsystem: D-Link System Inc Device 3a70
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort+ >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 32 bytes
	Interrupt: pin A routed to IRQ 17
	Region 0: Memory at fe9f0000 (64-bit, non-prefetchable) [size=64K]
	Capabilities: [40] Power Management version 2
		Flags: PMEClk- DSI- D1+ D2- AuxCurrent=375mA PME(D0+,D1+,D2-,D3hot+,D3cold-)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-
	Capabilities: [50] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
		Address: 00000000  Data: 0000
	Capabilities: [60] Express (v1) Legacy Endpoint, MSI 00
		DevCap:	MaxPayload 128 bytes, PhantFunc 0, Latency L0s <512ns, L1 <64us
			ExtTag- AttnBtn- AttnInd- PwrInd- RBE- FLReset-
		DevCtl:	Report errors: Correctable- Non-Fatal- Fatal- Unsupported-
			RlxdOrd+ ExtTag- PhantFunc- AuxPwr- NoSnoop-
			MaxPayload 128 bytes, MaxReadReq 512 bytes
		DevSta:	CorrErr- UncorrErr+ FatalErr- UnsuppReq+ AuxPwr- TransPend-
		LnkCap:	Port #0, Speed 2.5GT/s, Width x1, ASPM L0s L1, Latency L0 <512ns, L1 <64us
			ClockPM- Suprise- LLActRep- BwNot-
		LnkCtl:	ASPM Disabled; RCB 128 bytes Disabled- Retrain- CommClk+
			ExtSynch- ClockPM- AutWidDis- BWInt- AutBWInt-
		LnkSta:	Speed 2.5GT/s, Width x1, TrErr- Train- SlotClk+ DLActive- BWMgmt- ABWMgmt-
	Capabilities: [90] MSI-X: Enable- Mask- TabSize=1
		Vector table: BAR=0 offset=00000000
		PBA: BAR=0 offset=00000000
	Capabilities: [100] Advanced Error Reporting <?>
	Capabilities: [140] Virtual Channel <?>
	Kernel driver in use: ath9k
	Kernel modules: ath9k

---

