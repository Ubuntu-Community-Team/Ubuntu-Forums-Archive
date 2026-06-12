---
title: "abit WLP-01 WiFi card driver problem"
date: 2007-02-23
forum: Networking &amp; Wireless
---

### Post by 11001001 on 2007-02-23
I've been using Edgy for quite some time now and I just bought an abit WLP-01 PCI-Express WiFi card. Of course, Ubuntu didn't detect it, so I figured I'd use NDISwrapper to install the Windows driver from CD. However, there are no inf files, just an InstallShield installer. I located the CAB files which I'm pretty sure contain the driver files and tried using cabextract, which told me they were InstallShield CABs and to use unshield, which in turn tells me they are not valid InstallShield CABs. Am I completely out of luck?

---

### Post by edgecase on 2007-03-03
I believe the .cab/.hdr files are InstallShield 12.  The version of unshield I have (0.5) as well as latest in SVN doesn't work either. I'm trying the InstallShield 12 demo version to see if it has the extract utility that is compatible... iscab.exe can extract the aw5006.sys needed by NDISwrapper, it's a bit tricky to use but it works.

Early efforts suggest it's an Atheros chip, so an up to date MadWifi.org driver should work.  That is much better than NDISwrapper.  I'm not sure what pkg needed for Ubuntu.

Unzipping the Abit driver and running the setup.exe, and looking in the temp folder it makes C:\Documents and Settings\username\Local Settings\temp\{funny-GUID-string}, shows a log file with aw5006.sys, which google shows to be AzureWave driver for Atheros AR5001.  The same log file shows a PCI vendor ID that's Atheros 0x168c.  Device ID is 0x001c AR5424 (a/b/g)  or AR2424 (b/g), not sure.

Mac address search (based on user's manual screen shots)

00-15-AF   (hex)		AzureWave Technologies, Inc.
0015AF     (base 16)		AzureWave Technologies, Inc.
				8F., No.94, Baozhong Rd., Xindian
				Taipei  231
				TAIWAN, REPUBLIC OF CHINA


Can you do 'lspci" like this:

$ lspci
0000:00:00.0 Host bridge: Intel Corp. 82845 845 (Brookdale) Chipset Host Bridge (rev 04)
0000:00:01.0 PCI bridge: Intel Corp. 82845 845 (Brookdale) Chipset AGP Bridge (rev 04)
0000:00:1d.0 USB Controller: Intel Corp. 82801CA/CAM USB (Hub #1) (rev 02)
0000:02:02.0 Network controller: Intel Corp. PRO/Wireless 2200BG (rev 05)

find the bus/device/function in the first column that corresponds to your WLP-01, then do (leave off the 0000: part) :

$ lspci -vvns 02:02.0

and paste the output here ? I'd like to buy one if it can be used as an AP under linux, and that would help me (and likely others) find the supportability of this first of the (non-mini) PCI-Express wifi adapters.

---

### Post by 11001001 on 2007-03-03
Here's what I get:
```

$ sudo lspci -vvns 02:00.0
Password:
02:00.0 0200: 168c:001c (rev 01)
        Subsystem: 147b:1033
        Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Interrupt: pin A routed to IRQ 98
        Region 0: Memory at fbcf0000 (64-bit, non-prefetchable) [disabled] [size=64K]
        Capabilities: [40] Power Management version 2
                Flags: PMEClk- DSI- D1- D2- AuxCurrent=375mA PME(D0+,D1-,D2-,D3hot+,D3cold-)
                Status: D0 PME-Enable- DSel=0 DScale=0 PME-
        Capabilities: [50] Message Signalled Interrupts: 64bit- Queue=0/0 Enable-
                Address: 00000000  Data: 0000
        Capabilities: [60] Express Legacy Endpoint IRQ 0
                Device: Supported: MaxPayload 128 bytes, PhantFunc 0, ExtTag-
                Device: Latency L0s <512ns, L1 <64us
                Device: AtnBtn- AtnInd- PwrInd-
                Device: Errors: Correctable- Non-Fatal- Fatal- Unsupported-
                Device: RlxdOrd+ ExtTag- PhantFunc- AuxPwr- NoSnoop-
                Device: MaxPayload 128 bytes, MaxReadReq 512 bytes
                Link: Supported Speed 2.5Gb/s, Width x1, ASPM L0s L1, Port 0
                Link: Latency L0s <512ns, L1 <64us
                Link: ASPM Disabled RCB 128 bytes CommClk- ExtSynch-
                Link: Speed 2.5Gb/s, Width x1
        Capabilities: [90] MSI-X: Enable- Mask- TabSize=1
                Vector table: BAR=0 offset=00000000
                PBA: BAR=0 offset=00000000

```

I'm going to get the MadWifi.org drivers to see if that works.

EDIT: I used linux-restricted-modules, sudo modprobe ath_pci, which worked, but it did not create any wireless connections. I downloaded a version from madwifi.org and installed that, but can't get past this step:

```

# wlanconfig ath0 create wlandev wifi0 wlanmode sta
wlanconfig: ioctl: No such device


```

---

### Post by lavinog on 2007-03-04
> **11001001 said:**
> I've been using Edgy for quite some time now and I just bought an abit WLP-01 PCI-Express WiFi card. Of course, Ubuntu didn't detect it, so I figured I'd use NDISwrapper to install the Windows driver from CD. However, there are no inf files, just an InstallShield installer. I located the CAB files which I'm pretty sure contain the driver files and tried using cabextract, which told me they were InstallShield CABs and to use unshield, which in turn tells me they are not valid InstallShield CABs. Am I completely out of luck?

With compaq i had to get a sp####.exe file
i was able to use 7-zip to extract the files from the exe file...maybe you could do the same with the install shield installer

---

### Post by smoocat on 2007-07-25
> **11001001 said:**
> Here's what I get:
```

$ sudo lspci -vvns 02:00.0
Password:
02:00.0 0200: 168c:001c (rev 01)
        Subsystem: 147b:1033
        Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Interrupt: pin A routed to IRQ 98
        Region 0: Memory at fbcf0000 (64-bit, non-prefetchable) [disabled] [size=64K]
        Capabilities: [40] Power Management version 2
                Flags: PMEClk- DSI- D1- D2- AuxCurrent=375mA PME(D0+,D1-,D2-,D3hot+,D3cold-)
                Status: D0 PME-Enable- DSel=0 DScale=0 PME-
        Capabilities: [50] Message Signalled Interrupts: 64bit- Queue=0/0 Enable-
                Address: 00000000  Data: 0000
        Capabilities: [60] Express Legacy Endpoint IRQ 0
                Device: Supported: MaxPayload 128 bytes, PhantFunc 0, ExtTag-
                Device: Latency L0s <512ns, L1 <64us
                Device: AtnBtn- AtnInd- PwrInd-
                Device: Errors: Correctable- Non-Fatal- Fatal- Unsupported-
                Device: RlxdOrd+ ExtTag- PhantFunc- AuxPwr- NoSnoop-
                Device: MaxPayload 128 bytes, MaxReadReq 512 bytes
                Link: Supported Speed 2.5Gb/s, Width x1, ASPM L0s L1, Port 0
                Link: Latency L0s <512ns, L1 <64us
                Link: ASPM Disabled RCB 128 bytes CommClk- ExtSynch-
                Link: Speed 2.5Gb/s, Width x1
        Capabilities: [90] MSI-X: Enable- Mask- TabSize=1
                Vector table: BAR=0 offset=00000000
                PBA: BAR=0 offset=00000000

```

I'm going to get the MadWifi.org drivers to see if that works.

EDIT: I used linux-restricted-modules, sudo modprobe ath_pci, which worked, but it did not create any wireless connections. I downloaded a version from madwifi.org and installed that, but can't get past this step:

```

# wlanconfig ath0 create wlandev wifi0 wlanmode sta
wlanconfig: ioctl: No such device


```

Has anyone been able to get around this error?  I haven't been able to get it running using Ndiswrapper or Madwifi, and it works so beautifully in WinXP..  I'd much rather it work beautifully on Feisty. *sigh*

---

