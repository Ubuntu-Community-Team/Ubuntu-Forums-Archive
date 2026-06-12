---
title: "U.S. Robotics V.92 PCI Modem (Model 5660A)"
date: 2008-02-11
forum: Networking &amp; Wireless
---

### Post by BlueToast on 2008-02-11
Modem Page: [http://www.usr.com/products/modem/modem-product.asp?sku=USR5660A](http://www.usr.com/products/modem/modem-product.asp?sku=USR5660A)

*wvdailconf* cannot detect any modem and dialup is the only way I can get internet. Satellite is not affordable, nor is ISDN (in fact, less people use ISDN than do dialup and is at least 3x or 4x more expensive than dialup for just less than twice the speed).

By the way, I installed Ubuntu on my 40GB IDE. If I cannot get this modem working I am uninstalling Ubuntu.

---

### Post by BlueToast on 2008-02-13
I was asked to run the *lspci* command, so I did:
```
qwerty@Qwerty:~$ lspci
00:00.0 Host bridge: nVidia Corporation nForce2 AGP (different version?) (rev c1)
00:00.1 RAM memory: nVidia Corporation nForce2 Memory Controller 1 (rev c1)
00:00.2 RAM memory: nVidia Corporation nForce2 Memory Controller 4 (rev c1)
00:00.3 RAM memory: nVidia Corporation nForce2 Memory Controller 3 (rev c1)
00:00.4 RAM memory: nVidia Corporation nForce2 Memory Controller 2 (rev c1)
00:00.5 RAM memory: nVidia Corporation nForce2 Memory Controller 5 (rev c1)
00:01.0 ISA bridge: nVidia Corporation MCP2A ISA bridge (rev a3)
00:01.1 SMBus: nVidia Corporation MCP2A SMBus (rev a1)
00:02.0 USB Controller: nVidia Corporation MCP2A USB Controller (rev a1)
00:02.1 USB Controller: nVidia Corporation MCP2A USB Controller (rev a1)
00:02.2 USB Controller: nVidia Corporation MCP2A USB Controller (rev a2)
00:04.0 Bridge: nVidia Corporation MCP2A Ethernet Controller (rev a3)
00:06.0 Multimedia audio controller: nVidia Corporation MCP2S AC'97 Audio Controller (rev a1)
00:08.0 PCI bridge: nVidia Corporation MCP2A PCI Bridge (rev a3)
00:09.0 IDE interface: nVidia Corporation MCP2A IDE (rev a3)
00:0b.0 IDE interface: nVidia Corporation nForce2 Serial ATA Controller (rev a3)
00:1e.0 PCI bridge: nVidia Corporation nForce2 AGP (rev c1)
***01:09.0 Communication controller: U.S. Robotics USR5660A (USR265660A, USR5660A-BP) 56K PCI Faxmodem (rev 01)***
01:0d.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 80)
02:00.0 VGA compatible controller: nVidia Corporation NV40 [GeForce 6800 XT] (rev a1)
```

---

### Post by BlueToast on 2008-02-13
I was asked to type *lspci -vvv*:

```
00:00.0 Host bridge: nVidia Corporation nForce2 AGP (different version?) (rev c1)
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0
	Region 0: Memory at c0000000 (32-bit, prefetchable) [size=256M]
	Capabilities: <access denied>

00:00.1 RAM memory: nVidia Corporation nForce2 Memory Controller 1 (rev c1)
	Subsystem: EPoX Computer Co., Ltd. Unknown device 100f
	Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz+ UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-

00:00.2 RAM memory: nVidia Corporation nForce2 Memory Controller 4 (rev c1)
	Subsystem: EPoX Computer Co., Ltd. Unknown device 100f
	Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz+ UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-

00:00.3 RAM memory: nVidia Corporation nForce2 Memory Controller 3 (rev c1)
	Subsystem: EPoX Computer Co., Ltd. Unknown device 100f
	Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz+ UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-

00:00.4 RAM memory: nVidia Corporation nForce2 Memory Controller 2 (rev c1)
	Subsystem: EPoX Computer Co., Ltd. Unknown device 100f
	Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz+ UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-

00:00.5 RAM memory: nVidia Corporation nForce2 Memory Controller 5 (rev c1)
	Subsystem: EPoX Computer Co., Ltd. Unknown device 100f
	Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz+ UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-

00:01.0 ISA bridge: nVidia Corporation MCP2A ISA bridge (rev a3)
	Subsystem: EPoX Computer Co., Ltd. Unknown device 100f
	Control: I/O+ Mem+ BusMaster+ SpecCycle+ MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0
	Capabilities: <access denied>

00:01.1 SMBus: nVidia Corporation MCP2A SMBus (rev a1)
	Subsystem: EPoX Computer Co., Ltd. Unknown device 100f
	Control: I/O+ Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Interrupt: pin A routed to IRQ 11
	Region 0: I/O ports at e500 [size=32]
	Capabilities: <access denied>

00:02.0 USB Controller: nVidia Corporation MCP2A USB Controller (rev a1) (prog-if 10 [OHCI])
	Subsystem: EPoX Computer Co., Ltd. Unknown device 100f
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0 (750ns min, 250ns max)
	Interrupt: pin A routed to IRQ 16
	Region 0: Memory at e4003000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>

00:02.1 USB Controller: nVidia Corporation MCP2A USB Controller (rev a1) (prog-if 10 [OHCI])
	Subsystem: EPoX Computer Co., Ltd. Unknown device 100f
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0 (750ns min, 250ns max)
	Interrupt: pin B routed to IRQ 17
	Region 0: Memory at e4004000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>

00:02.2 USB Controller: nVidia Corporation MCP2A USB Controller (rev a2) (prog-if 20 [EHCI])
	Subsystem: EPoX Computer Co., Ltd. Unknown device 100f
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0 (750ns min, 250ns max)
	Interrupt: pin C routed to IRQ 16
	Region 0: Memory at e4005000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

00:04.0 Bridge: nVidia Corporation MCP2A Ethernet Controller (rev a3)
	Subsystem: EPoX Computer Co., Ltd. Unknown device 100f
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0 (250ns min, 5000ns max)
	Interrupt: pin A routed to IRQ 17
	Region 0: Memory at e4000000 (32-bit, non-prefetchable) [size=4K]
	Region 1: I/O ports at e000 [size=8]
	Capabilities: <access denied>

00:06.0 Multimedia audio controller: nVidia Corporation MCP2S AC'97 Audio Controller (rev a1)
	Subsystem: EPoX Computer Co., Ltd. Unknown device 100e
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0 (500ns min, 1250ns max)
	Interrupt: pin A routed to IRQ 16
	Region 0: I/O ports at e100 [size=256]
	Region 1: I/O ports at e200 [size=128]
	Region 2: Memory at e4001000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>

00:08.0 PCI bridge: nVidia Corporation MCP2A PCI Bridge (rev a3) (prog-if 00 [Normal decode])
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
	Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=32
	I/O behind bridge: 0000d000-0000dfff
	Memory behind bridge: e3000000-e3ffffff
	Prefetchable memory behind bridge: fff00000-000fffff
	Secondary status: 66MHz- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- <SERR- <PERR-
	BridgeCtl: Parity- SERR+ NoISA- VGA- MAbort- >Reset- FastB2B-

00:09.0 IDE interface: nVidia Corporation MCP2A IDE (rev a3) (prog-if 8a [Master SecP PriP])
	Subsystem: EPoX Computer Co., Ltd. Unknown device 100f
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0 (750ns min, 250ns max)
	Region 0: [virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
	Region 1: [virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
	Region 2: [virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
	Region 3: [virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
	Region 4: I/O ports at f000 [size=16]
	Capabilities: <access denied>

00:0b.0 IDE interface: nVidia Corporation nForce2 Serial ATA Controller (rev a3) (prog-if 85 [Master SecO PriO])
	Subsystem: EPoX Computer Co., Ltd. Unknown device 100f
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0 (750ns min, 250ns max)
	Interrupt: pin A routed to IRQ 18
	Region 0: I/O ports at 09f0 [size=8]
	Region 1: I/O ports at 0bf0 [size=4]
	Region 2: I/O ports at 0970 [size=8]
	Region 3: I/O ports at 0b70 [size=4]
	Region 4: I/O ports at ea00 [size=16]
	Region 5: I/O ports at eb00 [size=128]
	Capabilities: <access denied>

00:1e.0 PCI bridge: nVidia Corporation nForce2 AGP (rev c1) (prog-if 00 [Normal decode])
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
	Status: Cap- 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 32
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=32
	I/O behind bridge: 0000f000-00000fff
	Memory behind bridge: e0000000-e2ffffff
	Prefetchable memory behind bridge: d0000000-dfffffff
	Secondary status: 66MHz+ FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort+ <SERR- <PERR-
	BridgeCtl: Parity- SERR+ NoISA- VGA+ MAbort- >Reset- FastB2B-

01:09.0 Communication controller: U.S. Robotics USR5660A (USR265660A, USR5660A-BP) 56K PCI Faxmodem (rev 01)
	Subsystem: U.S. Robotics Unknown device 010a
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 32
	Interrupt: pin A routed to IRQ 11
	Region 0: Memory at e3000000 (32-bit, non-prefetchable) [size=64K]
	Region 1: I/O ports at d000 [size=8]
	Capabilities: <access denied>

01:0d.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 80) (prog-if 10 [OHCI])
	Subsystem: EPoX Computer Co., Ltd. Unknown device 900e
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 32 (8000ns max), Cache Line Size: 32 bytes
	Interrupt: pin A routed to IRQ 19
	Region 0: Memory at e3010000 (32-bit, non-prefetchable) [size=2K]
	Region 1: I/O ports at d100 [size=128]
	Capabilities: <access denied>

02:00.0 VGA compatible controller: nVidia Corporation NV40 [GeForce 6800 XT] (rev a1) (prog-if 00 [VGA])
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 32 (1250ns min, 250ns max)
	Interrupt: pin A routed to IRQ 5
	Region 0: Memory at e0000000 (32-bit, non-prefetchable) [size=16M]
	Region 1: Memory at d0000000 (32-bit, prefetchable) [size=256M]
	Region 2: Memory at e1000000 (32-bit, non-prefetchable) [size=16M]
	[virtual] Expansion ROM at e2000000 [disabled] [size=128K]
	Capabilities: <access denied>
```



And I replaced my */etc/wvdial.conf* using *sudo cp /media/drive1/wvdial.conf /etc/wvdial.conf*:
```
[Dialer Defaults]
Modem = /dev/modem
Baud = 460800
Init = ATZ
Phone = 4594055
Username = ****censored****
Password = ****censored****
New PPPD = yes
```

---

### Post by BlueToast on 2008-02-14
Bump.

---

### Post by BlueToast on 2008-02-16
Bump.

---

### Post by BlueToast on 2008-02-22
Bump.

---

### Post by BlueToast on 2008-02-29
Bump.

---

### Post by BlueToast on 2008-03-03
Bump.

---

### Post by hermitguy on 2008-03-04
Doesnt anybody google anymore?  First result in simple google search implied that this particular modem can work under linux using hsf connexant driver. there is a crippled version of this driver at [www.linuxant.com](www.linuxant.com), they want $20 cash money to uncripple it.

BUT lucky you, Dell is now offering Ubuntu on some of their computers.  And guess what, they have a free full speed version of this driver.  There are actually two drivers, one works on Feisty, one on Gutsy.   The second may actually work on both, I have no idea.

[http://direct2dell.com/one2one/archive/2007/07/17/21325.aspx](http://direct2dell.com/one2one/archive/2007/07/17/21325.aspx)

[http://linux.dell.com/wiki/index.php/Ubuntu_7.10/Issues/New_Conexant_Modem_Driver](http://linux.dell.com/wiki/index.php/Ubuntu_7.10/Issues/New_Conexant_Modem_Driver)

---

### Post by BlueToast on 2008-03-25
Neither one works.

```
qwerty@Qwerty:~$ wvdial
WvDial<*1>: WvDial: Internet dialer version 1.56
WvDial<Err>: Cannot open /dev/ttyS0: Device or resource busy
WvDial<Err>: Cannot open /dev/ttyS0: Device or resource busy
WvDial<Err>: Cannot open /dev/ttyS0: Device or resource busy
qwerty@Qwerty:~$
```

---

### Post by BlueToast on 2008-03-30
I managed to get the modem itself working -- but now I'm having a problem being able to 'login' to my ISP Dialup account... below is a copy and paste of the notes I took. (The part where it sends username and password -- that was like spammed in the console three or four times, is that normal? Would be nice if each line had a timetag thing)



Ignore this little bit of info
>To be enabled: 115200 baud, LCP + Multilink
>wvdialconf /etc/wvdial.conf

qwerty@Qwerty:~$ wvdial
WvDial<*1>: WvDial: Internet dialer version 1.56
WvModem<*1>: Cannot set information for serial port.
WvDial<*1>: Initializing modem.
WvDial<*1>: Sending: ATZ
WvDial<*1>: Sending: ATQ0
WvDial<*1>: Re-Sending: ATZ
WvDial<Err>: Modem not responding.
qwerty@Qwerty:~$ sudo gedit /etc/wvdial.conf

>[Dialer Defaults]
>Modem = /dev/ttyS1
>Baud = 57600
>Init = ATZ
>Phone = 4594055
>Username = [email]hlrsenet@hi-fiaccess.net[/email]
>Password = abc123
>New PPPD = yes



/dev/modem --> ttySHSF0

Using username hlrsenet seemed to be more accepted than [email]hlrsenet@hi-fiaccess.net[/email].


>Username = [email]hlrsenet@hi-fiaccess.net[/email]
>New PPPD = no

qwerty@Qwerty:~$ wvdial
WvDial<*1>: WvDial: Internet dialer version 1.56
WvModem<*1>: Cannot set information for serial port.
WvDial<*1>: Initializing modem.
WvDial<*1>: Sending: ATZ
WvDial Modem<*1>: ATZ
WvDial Modem<*1>: OK
WvDial<*1>: Modem initialized.
WvDial<*1>: Sending: ATDT4594055
WvDial<*1>: Waiting for carrier.
WvDial Modem<*1>: ATDT4594055
Caught signal 2:  Attempting to exit gracefully...
WvDial<*1>: Disconnecting at Sun Mar 30 02:49:42 2008
qwerty@Qwerty:~$ wvdial
WvDial<*1>: WvDial: Internet dialer version 1.56
WvModem<*1>: Cannot set information for serial port.
WvDial<*1>: Initializing modem.
WvDial<*1>: Sending: ATZ
WvDial Modem<*1>: ATZ
WvDial Modem<*1>: OK
WvDial<*1>: Modem initialized.
WvDial<*1>: Sending: ATDT4594055
WvDial<*1>: Waiting for carrier.
WvDial Modem<*1>: ATDT4594055
WvDial Modem<*1>: CONNECT 57600 
WvDial<*1>: Carrier detected.  Waiting for prompt.
WvDial Modem<*1>: STATION ID - kscmo03rh13hp004,kscmo42ev
WvDial Modem<*1>: Welcome 
WvDial Modem<*1>: Please Sign-on: 
WvDial<*1>: Looks like a login prompt.
WvDial<*1>: Sending: hlrsenet
WvDial Modem<*1>: hlrsenet
WvDial Modem<*1>: Password:
WvDial<*1>: Looks like a password prompt.
WvDial<*1>: Sending: (password)
WvDial Modem<*1>: Name, password pair incorrect
WvDial Modem<*1>: Please Sign-on: 
WvDial<*1>: Looks like a login prompt.
WvDial<*1>: Sending: hlrsenet
WvDial Modem<*1>: hlrsenet
WvDial Modem<*1>: Password:
WvDial<*1>: Looks like a password prompt.
WvDial<*1>: Sending: (password)
WvDial Modem<*1>: Name, password pair incorrect
WvDial Modem<*1>: Please Sign-on: 
WvDial<*1>: Looks like a login prompt.
WvDial<*1>: Sending: hlrsenet
WvDial<Notice>: Don't know what to do!  Starting pppd and hoping for the best.
WvDial<Notice>: Starting pppd at Sun Mar 30 02:50:44 2008
WvDial<Err>: Warning: Could not modify /etc/ppp/pap-secrets: Permission denied
WvDial<Err>: --> PAP (Password Authentication Protocol) may be flaky.
WvDial<Err>: Warning: Could not modify /etc/ppp/chap-secrets: Permission denied
WvDial<Err>: --> CHAP (Challenge Handshake) may be flaky.
WvDial<Notice>: Pid of pppd: 15301
WvDial<*1>: Using interface ppp0
Caught signal 2:  Attempting to exit gracefully...
WvDial<*1>: Terminating on signal 15
WvDial<*1>: Disconnecting at Sun Mar 30 02:50:48 2008

qwerty@Qwerty:~$ 



>Username = hlrsenet
>New PPPD = no

qwerty@Qwerty:~$ wvdial
WvDial<*1>: WvDial: Internet dialer version 1.56
WvModem<*1>: Cannot set information for serial port.
WvDial<*1>: Initializing modem.
WvDial<*1>: Sending: ATZ
WvDial Modem<*1>: ATZ
WvDial Modem<*1>: OK
WvDial<*1>: Modem initialized.
WvDial<*1>: Sending: ATDT4594055
WvDial<*1>: Waiting for carrier.
WvDial Modem<*1>: ATDT4594055
WvDial Modem<*1>: CONNECT 57600 
WvDial<*1>: Carrier detected.  Waiting for prompt.
WvDial Modem<*1>: STATION ID - kscmo03rh13hp009,kscmo42ev
WvDial Modem<*1>: Welcome 
WvDial Modem<*1>: Please Sign-on: 
WvDial<*1>: Looks like a login prompt.
WvDial<*1>: Sending: [email]hlrsenet@hi-fiaccess.net[/email]
WvDial Modem<*1>: [email]hlrsenet@hi-fiaccess.net[/email]
WvDial Modem<*1>: Name, password pair incorrect
WvDial Modem<*1>: Please Sign-on: 
WvDial<*1>: Looks like a login prompt.
WvDial<*1>: Sending: [email]hlrsenet@hi-fiaccess.net[/email]
WvDial Modem<*1>: [email]hlrsenet@hi-fiaccess.net[/email]
WvDial Modem<*1>: Name, password pair incorrect
WvDial Modem<*1>: Please Sign-on: 
WvDial<*1>: Looks like a login prompt.
WvDial<*1>: Sending: [email]hlrsenet@hi-fiaccess.net[/email]
WvDial Modem<*1>: [email]hlrsenet@hi-fiaccess.net[/email]
WvDial Modem<*1>: Name, password pair incorrect
WvDial Modem<*1>: Please Sign-on: 
WvDial<*1>: Looks like a login prompt.
WvDial<*1>: Sending: [email]hlrsenet@hi-fiaccess.net[/email]
WvDial Modem<*1>: [email]hlrsenet@hi-fiaccess.net[/email]
WvDial Modem<*1>: Login failed, reason = (-190,kscmo42ev,1206859922-000,kscmo03rh13hp009)
WvDial Modem<*1>: Connection closed by foreign host.
WvDial<Err>: Connected, but carrier signal lost!  Retrying...
WvDial<*1>: Sending: ATDT4594055
WvDial<*1>: Waiting for carrier.
WvDial Modem<*1>: NO CARRIER
WvDial Modem<*1>: ATDT4594055
WvDial<*1>: Carrier detected.  Waiting for prompt.
WvDial<Err>: Connected, but carrier signal lost!  Retrying...
WvDial<*1>: Sending: ATDT4594055
WvDial<*1>: Waiting for carrier.
WvDial Modem<*1>: OK
WvDial Modem<*1>: ATDT4594055
WvDial<Warn>: No Carrier!  Trying again.
Caught signal 2:  Attempting to exit gracefully...
WvDial<*1>: Disconnecting at Sun Mar 30 02:52:15 2008
qwerty@Qwerty:~$ 
qwerty@Qwerty:~$ 




>Username = hlrsenet
>New PPPD = no

qwerty@Qwerty:~$ wvdial
WvDial<*1>: WvDial: Internet dialer version 1.56
WvModem<*1>: Cannot set information for serial port.
WvDial<*1>: Initializing modem.
WvDial<*1>: Sending: ATZ
WvDial Modem<*1>: ATZ
WvDial Modem<*1>: OK
WvDial<*1>: Modem initialized.
WvDial<*1>: Sending: ATDT4594055
WvDial<*1>: Waiting for carrier.
WvDial Modem<*1>: ATDT4594055
WvDial Modem<*1>: CONNECT 57600 
WvDial<*1>: Carrier detected.  Waiting for prompt.
WvDial Modem<*1>: STATION ID - kscmo03rh13hp015,kscmo42ev
WvDial Modem<*1>: Welcome 
WvDial Modem<*1>: Please Sign-on: 
WvDial<*1>: Looks like a login prompt.
WvDial<*1>: Sending: hlrsenet
WvDial Modem<*1>: hlrsenet
WvDial Modem<*1>: Password:
WvDial<*1>: Looks like a password prompt.
WvDial<*1>: Sending: (password)
WvDial Modem<*1>: Name, password pair incorrect
WvDial Modem<*1>: Please Sign-on: 
WvDial<*1>: Looks like a login prompt.
WvDial<*1>: Sending: hlrsenet
WvDial Modem<*1>: hlrsenet
WvDial Modem<*1>: Password:
WvDial<*1>: Looks like a password prompt.
WvDial<*1>: Sending: (password)
WvDial Modem<*1>: Name, password pair incorrect
WvDial Modem<*1>: Please Sign-on: 
WvDial<*1>: Looks like a login prompt.
WvDial<*1>: Sending: hlrsenet
WvDial<Notice>: Don't know what to do!  Starting pppd and hoping for the best.
WvDial<Notice>: Starting pppd at Sun Mar 30 02:54:07 2008
WvDial<Err>: Warning: Could not modify /etc/ppp/pap-secrets: Permission denied
WvDial<Err>: --> PAP (Password Authentication Protocol) may be flaky.
WvDial<Err>: Warning: Could not modify /etc/ppp/chap-secrets: Permission denied
WvDial<Err>: --> CHAP (Challenge Handshake) may be flaky.
WvDial<Notice>: Pid of pppd: 15335
WvDial<*1>: Using interface ppp0
WvDial<*1>: pppd: H06][08]H06][08]&#1560;[06][08]
WvDial<*1>: pppd: H06][08]H06][08]&#1560;[06][08]
WvDial<*1>: pppd: H06][08]H06][08]&#1560;[06][08]
WvDial<*1>: pppd: H06][08]H06][08]&#1560;[06][08]
WvDial<*1>: pppd: H06][08]H06][08]&#1560;[06][08]
WvDial<*1>: pppd: H06][08]H06][08]&#1560;[06][08]
WvDial<*1>: pppd: H06][08]H06][08]&#1560;[06][08]
WvDial<*1>: Disconnecting at Sun Mar 30 02:54:38 2008
WvDial<*1>: The PPP daemon has died: A modem hung up the phone (exit code = 16)
WvDial<*1>: man pppd explains pppd error codes in more detail.
WvDial<Notice>: Try again and look into /var/log/messages and the wvdial and pppd man pages for more information.
WvDial<Notice>: Auto Reconnect will be attempted in 5 seconds
WvModem<*1>: Cannot set information for serial port.
WvDial<*1>: Initializing modem.
WvDial<*1>: Sending: ATZ
WvDial Modem<*1>: ATZ
WvDial Modem<*1>: OK
WvDial<*1>: Modem initialized.
Caught signal 2:  Attempting to exit gracefully...
WvDial<*1>: Disconnecting at Sun Mar 30 02:54:39 2008
qwerty@Qwerty:~$

---

### Post by BlueToast on 2008-04-08
Bump.

---

### Post by BlueToast on 2008-04-13
Bump.

---

### Post by BlueToast on 2008-04-18
Bump.

---

### Post by bobthebiscuit on 2008-04-29
I know you're looking more for help on getting your existing modem working... and from my experience with winmodems that work -- and work COMPLETELY -- for 3 people worldwide, you'll need a lot more luck than just I can wish you.

However, I can offer an alternative: [http://www.zoom.com/products/dial_up_external_usb.html](http://www.zoom.com/products/dial_up_external_usb.html)

Generally, "controller" based modems have been reliable but expensive, and this one (the Model 3095 V.92 USB Mini External) seems to be around USD$40-50, AND it's reported to work well for Linux. I was tasked with setting up a faxserver out of a LInux box, and eventually had to resort to a USD$80 controller modem... this method took away all my pain.

I'm currently building its successor, using that modem, and I'll let you know whether it works. In the meantime, good luck on getting the quirks worked out of your USR!

---

