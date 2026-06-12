---
title: "Lenovo v310, Intel net controller, Ubuntu 14.04/16.04 - wifi disable"
date: 2016-12-05
forum: Networking &amp; Wireless
---

### Post by perone on 2016-12-05
Hi,

I instaled both version of Ubuntu 14.04 and 16.04 and I can't connect to internet by wifi.

```
 Network controller [0280]: Intel Corporation Device [8086:3166] (rev 99)
    Subsystem: Intel Corporation Device [8086:4210]
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Interrupt: pin A routed to IRQ 127
    Region 0: Memory at d1000000 (64-bit, non-prefetchable) [size=8K]
    Capabilities: [c8] Power Management version 3
        Flags: PMEClk- DSI+ D1- D2- AuxCurrent=0mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
        Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=0 PME-
    Capabilities: [d0] MSI: Enable+ Count=1/1 Maskable- 64bit+
        Address: 00000000fee0f00c  Data: 41e1
    Capabilities: [40] Express (v2) Endpoint, MSI 00
        DevCap:    MaxPayload 128 bytes, PhantFunc 0, Latency L0s <512ns, L1 unlimited
            ExtTag- AttnBtn- AttnInd- PwrInd- RBE+ FLReset+
        DevCtl:    Report errors: Correctable- Non-Fatal- Fatal- Unsupported-
            RlxdOrd+ ExtTag- PhantFunc- AuxPwr+ NoSnoop+ FLReset-
            MaxPayload 128 bytes, MaxReadReq 128 bytes
        DevSta:    CorrErr+ UncorrErr- FatalErr- UnsuppReq+ AuxPwr+ TransPend-
        LnkCap:    Port #0, Speed 2.5GT/s, Width x1, ASPM L1, Exit Latency L0s <4us, L1 <32us
            ClockPM+ Surprise- LLActRep- BwNot-
        LnkCtl:    ASPM Disabled; RCB 64 bytes Disabled- CommClk+
            ExtSynch- ClockPM+ AutWidDis- BWInt- AutBWInt-
        LnkSta:    Speed 2.5GT/s, Width x1, TrErr- Train- SlotClk+ DLActive- BWMgmt- ABWMgmt-
        DevCap2: Completion Timeout: Range B, TimeoutDis+, LTR+, OBFF Via WAKE#
        DevCtl2: Completion Timeout: 16ms to 55ms, TimeoutDis-, LTR-, OBFF Disabled
        LnkCtl2: Target Link Speed: 2.5GT/s, EnterCompliance- SpeedDis-
             Transmit Margin: Normal Operating Range, EnterModifiedCompliance- ComplianceSOS-
             Compliance De-emphasis: -6dB
        LnkSta2: Current De-emphasis Level: -3.5dB, EqualizationComplete-, EqualizationPhase1-
             EqualizationPhase2-, EqualizationPhase3-, LinkEqualizationRequest-
    Capabilities: [100 v1] Advanced Error Reporting
        UESta:    DLP- SDES- TLP- FCP- CmpltTO- CmpltAbrt- UnxCmplt- RxOF- MalfTLP- ECRC- UnsupReq- ACSViol-
        UEMsk:    DLP- SDES- TLP- FCP- CmpltTO- CmpltAbrt- UnxCmplt- RxOF- MalfTLP- ECRC- UnsupReq- ACSViol-
        UESvrt:    DLP+ SDES+ TLP- FCP+ CmpltTO- CmpltAbrt- UnxCmplt- RxOF+ MalfTLP+ ECRC- UnsupReq- ACSViol-
        CESta:    RxErr- BadTLP- BadDLLP- Rollover- Timeout- NonFatalErr-
        CEMsk:    RxErr- BadTLP- BadDLLP- Rollover- Timeout- NonFatalErr+
        AERCap:    First Error Pointer: 00, GenCap- CGenEn- ChkCap- ChkEn-
    Capabilities: [140 v1] Device Serial Number ac-2b-6e-ff-ff-59-54-bb
    Capabilities: [14c v1] Latency Tolerance Reporting
        Max snoop latency: 0ns
        Max no snoop latency: 0ns
    Capabilities: [154 v1] L1 PM Substates
        L1SubCap: PCI-PM_L1.2+ PCI-PM_L1.1+ ASPM_L1.2+ ASPM_L1.1+ L1_PM_Substates+
              PortCommonModeRestoreTime=30us PortTPowerOnTime=60us
    Kernel driver in use: iwlwifi



```

---

### Post by chili555 on 2016-12-05
> ##### rfkill ############################

0: ideapad_wlan: Wireless LAN
	Soft blocked: no
	[COLOR="#FF0000"]Hard blocked: yes[/COLOR]
1: ideapad_bluetooth: Bluetooth
	Soft blocked: yes
	Hard blocked: yes
2: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
3: hci0: Bluetooth
	Soft blocked: yes
	Hard blocked: noThis suggests that the wireless switch or key combination is set to disable the wireless radio. Can you please find it and switch it?

---

### Post by perone on 2016-12-06
I dont have any button or key combination to switch wifi on/off. I reseted bios and still nothing.

---

### Post by chili555 on 2016-12-06
> **perone said:**
> I dont have any button or key combination to switch wifi on/off. I reseted bios and still nothing.Doesn't F7 enable and disable airplane mode and thereby the wireless radio? If you press F7 and run:```
rfkill list all
```...and then press it again and run:```
rfkill list all
```Is there any change?

As far as I know, *EVERY* laptop with integrated wireless has some method to enable and disable the wireless radio due to airline regulations.

[ATTACH=CONFIG]272577[/ATTACH]

---

### Post by perone on 2016-12-06
Ok, so after 1st press the result is:
> 
0: ideapad_wlan: Wireless LAN 
Soft blocked: no
Hard blocked: yes

1: ideapad_bluetooth: Blotooth
Soft blocked: no
Hard blocked: yes

2: phy0 : Wireless LAN
Soft blocked: no
Hard blocked: no

4: hci0: Bluetooth
Soft blocked: no
Hard blocked: no


after 2nd is
> 0: ideapad_wlan: Wireless LAN 
Soft blocked: yes
Hard blocked: yes

1: ideapad_bluetooth: Blotooth
Soft blocked: no
Hard blocked: yes

2: phy0 : Wireless LAN
Soft blocked: yes
Hard blocked: no

4: hci0: Bluetooth
Soft blocked: no
Hard blocked: no

and its only this changed. Still i have my Wifi 'option' disable.

---

### Post by perone on 2016-12-06
rfkill unblock all doesn't work *

---

### Post by Hadaka on 2016-12-06
Hi please open a terminal ...ctrl/alt/t...then copy and paste....
```
cat /sys/class/dmi/id/bios_date
```
please post the result...
then go here..see if your computer has the physical wifi switch..
[https://support.lenovo.com/us/en/documents/ht072689](https://support.lenovo.com/us/en/documents/ht072689)
thanks.

---

### Post by perone on 2016-12-07
> RESULT: 06/20/2016

I don't have physical wifi switch :)

---

### Post by chili555 on 2016-12-07
Let's try an experiment. From the terminal:```
sudo -i
echo "blacklist ideapad_laptop"  >>  /etc/modprobe.d/blacklist.conf
exit
```Reboot and tell us if there is any improvement.

---

### Post by perone on 2016-12-08
Thank you, I resolved my problem yesterday by this command. One more thing after edit blacklist.conf:

> modprobe -r ideapad_laptop

Its weird becouse i don't have idea pad but this command still work :)

Thanks for help!

---

### Post by teadrinker95 on 2017-02-22
it work!!!
thx

---

### Post by thorwk on 2017-08-24
> **chili555 said:**
> Let's try an experiment. From the terminal:```
sudo -i
echo "blacklist ideapad_laptop"  >>  /etc/modprobe.d/blacklist.conf
exit
```Reboot and tell us if there is any improvement.

Thank you so much [COLOR=#000000]chili555!!

It worked like a charm for me![/COLOR]

---

