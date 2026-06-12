---
title: "Serial hardware, ports, &amp; tty: confused"
date: 2008-11-04
forum: Networking &amp; Wireless
---

### Post by owlcroft on 2008-11-04
I am trying to get two unrelated serial-type devices and associated software working and am having no end of problems and confusion.

The first item is a PCI internal modem, usr/3com 5601 type (onboard hardware controller) to use for faxing with efax; the second item is an APC BackUp 450 UPS for use with apcupsd monitoring/control package.

Now, here are some data:

BIOS setting, onboard devices: COM1 set for address 02f8 and IRQ3, per BIOS bootup screens.


lspci shows, in salient part:

```
05:00.0 Serial controller: 3Com Corp, Modem Division 56K FaxModem Model 5610 (rev 01) (prog-if 02 [16550])
	Subsystem: 3Com Corp, Modem Division USR 56k Internal Voice Modem (Model 2976)
	Control: I/O+ Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Interrupt: pin A routed to IRQ 20
	Region 0: I/O ports at d000 [size=8]
	Capabilities: <access denied>
```


 dmesg | grep -A10 -i serial  shows (again in salient part):
```

[   30.517151] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   30.517281] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   30.517599] 00:08: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   30.517708] ACPI: PCI Interrupt 0000:05:00.0[A] -> GSI 20 (level, low) -> IRQ 20
[   30.517785] 0000:05:00.0: ttyS0 at I/O 0xd000 (irq = 20) is a 16550A
```


lshw gives:

```
        *-pci:4
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: 90
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
           *-communication
                description: Serial controller
                product: 56K FaxModem Model 5610
                vendor: 3Com Corp, Modem Division
                physical id: 0
                bus info: pci@0000:05:00.0
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: 16550 cap_list
                configuration: driver=serial latency=0
```


So, per dmesg, it surely looks like ttyS0 must be the modem and ttyS1 must be the com port.

But if I set efax to use ttyS0, it reports "no device", whereas if I set it to ttyS1 it finds the modem OK.  (I still can't fax properly, but that's a whole other problem probably related to init strings.)  Meanwhile, apcupsd will not work, reporting that it cannot communicate with the UPS via the port, regardless of whether I specify ttyS0 or ttyS1 (whichever I try, it's always the opposite of what efax is set for, even though I don't (so far) try to use the two simultaneously.

(And yes, I have the correct special serial cable for the UPS.)

Does anyone have any ideas?  Is there any other data I can look up and supply?

Thanks!

---

### Post by bwhite82 on 2008-11-04
better in hardware support subforum?

---

