---
title: "Ubuntu Server 21.04 Wired Ethernet Too Slow"
date: 2021-09-13
forum: Networking &amp; Wireless
---

### Post by quarksrus on 2021-09-13
[SIZE=2][FONT=arial][COLOR=#232629][SIZE=1][/SIZE]Hi,

I'm an experienced sysadmin but not a network engineer so this issue is truly perplexing to me!

[/COLOR]
[COLOR=#232629]Running Ubuntu Server 21.04 (kernel 5.11.0-34-generic) and have run into a serious network issue where the internet download speed is around 25Mbps on a 150Mbps connection!

[/COLOR]
[COLOR=#232629]My setup:[/COLOR]
[/FONT][/SIZE]
[LIST]
[*][SIZE=2][FONT=arial]Lenovo Ideapad 300S with a wired Ethernet connection.[/FONT][/SIZE]
[*][SIZE=2][FONT=arial]Running Ubuntu Server 21.04 (kernel version 5.11.0-34-generic).[/FONT][/SIZE]
[*][SIZE=2][FONT=arial]Wired Ethernet connection with RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (r8169) driver.[/FONT][/SIZE]
[*][SIZE=2][FONT=arial]My contract with the ISP is for a 150Mbps download speed.[/FONT][/SIZE]
[/LIST]
[SIZE=2][FONT=arial]

[COLOR=#232629]My problem:[/COLOR]
[COLOR=#232629]The download speed is extremely low, around 25Mbps whereas my upload speed is 'normal' around 90-100Mbps. I use 'speedtest-cli' for measuring the bandwidth, by the way.[/COLOR]
[COLOR=#232629]
What I Have Done So Far:

- I disabled the wired interface completely and just configured the wifi which also has very slow download speed.
[/COLOR][/FONT][COLOR=#232629][FONT=arial]- Booted an Ubuntu iso image on a USB stick, ran a 'wget' test which also showed very slow download speed.
[/FONT][/COLOR]
[FONT=arial][COLOR=#232629]- Here is the truly bizarre part! The problem doesn't happen on Windows 10 dual-booted on the same laptop and the download speed is ~190Mbps!! 
- I've also done a speedtest-cli on an old Acer Aspire One laptop running the same kernel and connected (wired) to the same router, the speed is around 180Mbps!

[/COLOR]
[COLOR=#232629]I do see some rx_missed in the 'ethtool' output, not sure if this is symptomatic of a problem with the r8169 driver.[/COLOR]
[COLOR=#232629]I searched through many articles that talked about the r8169 driver having problems but they were all on older kernel versions. I'm not even sure if that's the issue here.

At this point, I've run out of ideas and the process of elimination I tried to follow would lead me to think it's a driver issue but I'm not sure! I would be grateful for any help I can get!
[/COLOR]
Output of ethtool -S enp3s0:

NIC statistics:
tx_packets: 320715
rx_packets: 203088
tx_errors: 0
rx_errors: 0
rx_missed: 2497
align_errors: 0
tx_single_collisions: 0
tx_multi_collisions: 0
unicast: 202217
broadcast: 63
multicast: 808
tx_aborted: 0
tx_underrun: 0

[COLOR=#232629]Output from lspci -vnvn -s 03:00.0:
[/COLOR]
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 15)
Subsystem: Lenovo RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [17aa:3835]
Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
Latency: 0, Cache Line Size: 64 bytes
Interrupt: pin A routed to IRQ 17
Region 0: I/O ports at d000 [SIZE=256]
[SIZE=1]R[SIZE=2]egion [/SIZE][/SIZE][SIZE=2]2: Memory at d1204000 (64-bit, non-prefetchable) [size=4K]
Region 4: Memory at d1200000 (64-bit, non-prefetchable) [size=16K]
Capabilities: [40] Power Management version 3
Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=375mA PME(D0+,D1+,D2+,D3hot+,D3cold+)
Status: D0 NoSoftRst+ PME-Enable- DSel=0 DScale=0 PME-
Capabilities: [50] MSI: Enable- Count=1/1 Maskable- 64bit+
Address: 0000000000000000 Data: 0000
Capabilities: [70] Express (v2) Endpoint, MSI 01
DevCap: MaxPayload 128 bytes, PhantFunc 0, Latency L0s <512ns, L1 <64us
ExtTag- AttnBtn- AttnInd- PwrInd- RBE+ FLReset- SlotPowerLimit 10.000W
DevCtl: CorrErr- NonFatalErr- FatalErr- UnsupReq-
RlxdOrd+ ExtTag- PhantFunc- AuxPwr- NoSnoop-
MaxPayload 128 bytes, MaxReadReq 4096 bytes
DevSta: CorrErr+ NonFatalErr- FatalErr- UnsupReq+ AuxPwr+ TransPend-
LnkCap: Port #0, Speed 2.5GT/s, Width x1, ASPM L0s L1, Exit Latency L0s unlimited, L1 <64us
ClockPM+ Surprise- LLActRep- BwNot- ASPMOptComp+
LnkCtl: ASPM L1 Enabled; RCB 64 bytes, Disabled- CommClk+
ExtSynch- ClockPM+ AutWidDis- BWInt- AutBWInt-
LnkSta: Speed 2.5GT/s (ok), Width x1 (ok)
TrErr- Train- SlotClk+ DLActive- BWMgmt- ABWMgmt-
DevCap2: Completion Timeout: Range ABCD, TimeoutDis+ NROPrPrP- LTR+
10BitTagComp- 10BitTagReq- OBFF Via message/WAKE#, ExtFmt- EETLPPrefix-
EmergencyPowerReduction Not Supported, EmergencyPowerReductionInit-
FRS- TPHComp- ExtTPHComp-
AtomicOpsCap: 32bit- 64bit- 128bitCAS-
DevCtl2: Completion Timeout: 50us to 50ms, TimeoutDis- LTR+ OBFF Disabled,
AtomicOpsCtl: ReqEn-
LnkCap2: Supported Link Speeds: 2.5GT/s, Crosslink- Retimer- 2Retimers- DRS-
LnkCtl2: Target Link Speed: 2.5GT/s, EnterCompliance- SpeedDis-
Transmit Margin: Normal Operating Range, EnterModifiedCompliance- ComplianceSOS-
Compliance De-emphasis: -6dB
LnkSta2: Current De-emphasis Level: -6dB, EqualizationComplete- EqualizationPhase1-
EqualizationPhase2- EqualizationPhase3- LinkEqualizationRequest-
Retimer- 2Retimers- CrosslinkRes: unsupported
Capabilities: [b0] MSI-X: Enable+ Count=4 Masked-
Vector table: BAR=4 offset=00000000
PBA: BAR=4 offset=00000800
Capabilities: [100 v2] Advanced Error Reporting
UESta: DLP- SDES- TLP- FCP- CmpltTO- CmpltAbrt- UnxCmplt- RxOF- MalfTLP- ECRC- UnsupReq- ACSViol-
UEMsk: DLP- SDES- TLP- FCP- CmpltTO- CmpltAbrt- UnxCmplt- RxOF- MalfTLP- ECRC- UnsupReq- ACSViol-
UESvrt: DLP+ SDES+ TLP- FCP+ CmpltTO- CmpltAbrt- UnxCmplt- RxOF+ MalfTLP+ ECRC- UnsupReq- ACSViol-
CESta: RxErr- BadTLP- BadDLLP- Rollover- Timeout- AdvNonFatalErr-
CEMsk: RxErr- BadTLP- BadDLLP- Rollover- Timeout- AdvNonFatalErr+
AERCap: First Error Pointer: 00, ECRCGenCap+ ECRCGenEn- ECRCChkCap+ ECRCChkEn-
MultHdrRecCap- MultHdrRecEn- TLPPfxPres- HdrLogCap-
HeaderLog: 00000000 00000000 00000000 00000000
Capabilities: [140 v1] Virtual Channel
Caps: LPEVC=0 RefClk=100ns PATEntryBits=1
Arb: Fixed- WRR32- WRR64- WRR128-
Ctrl: ArbSelect=Fixed
Status: InProgress-
VC0: Caps: PATOffset=00 MaxTimeSlots=1 RejSnoopTrans-
Arb: Fixed- WRR32- WRR64- WRR128- TWRR128- WRR256-
Ctrl: Enable+ ID=0 ArbSelect=Fixed TC/VC=ff
Status: NegoPending- InProgress-
Capabilities: [160 v1] Device Serial Number 01-00-00-00-68-4c-e0-00
Capabilities: [170 v1] Latency Tolerance Reporting
Max snoop latency: 3145728ns
Max no snoop latency: 3145728ns
Capabilities: [178 v1] L1 PM Substates
L1SubCap: PCI-PM_L1.2+ PCI-PM_L1.1+ ASPM_L1.2+ ASPM_L1.1+ L1_PM_Substates+
PortCommonModeRestoreTime=150us PortTPowerOnTime=150us
L1SubCtl1: PCI-PM_L1.2+ PCI-PM_L1.1+ ASPM_L1.2+ ASPM_L1.1-
T_CommonMode=0us LTR1.2_Threshold=294912ns
L1SubCtl2: T_PwrOn=150us
Kernel driver in use: r8169
Kernel modules: r8169

[COLOR=#232629]Thanks in advance!

-PE[/COLOR][/SIZE][/SIZE][/FONT]

---

