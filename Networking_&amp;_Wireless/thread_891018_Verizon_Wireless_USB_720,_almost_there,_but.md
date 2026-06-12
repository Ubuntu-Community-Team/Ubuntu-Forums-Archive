---
title: "Verizon Wireless USB 720, almost there, but?"
date: 2008-08-15
forum: Networking &amp; Wireless
---

### Post by Sixsh00ter on 2008-08-15
Hardy Heron 8.4 - I'm following JaxL thread. I can connect and surf the web, and reconnect and surf the web as long as I don't shutdown. After shutting down I can't get reconnected.  Below are parts of dmesg, and messages, along with the output from lsusb.

I'm running sudo gnome-ppp from a terminal window and trying to connect after shutting down.

Could somebody clue me in?  If you need more info please let me know.

Thanks

administrator@administrator-laptop:~$ tail -25 /var/log/dmesg
[   72.631989] Yenta: Using CSCINT to route CSC interrupts to PCI
[   72.631991] Yenta: Routing CardBus interrupts to PCI
[   72.631998] Yenta TI: socket 0000:02:06.0, mfunc 0x012c1202, devctl 0x64
[   72.863885] Yenta: ISA IRQ mask 0x0038, PCI irq 11
[   72.863892] Socket status: 30000006
[   72.863897] Yenta: Raising subordinate bus# of parent bus (#02) from #03 to #06
[   72.863906] pcmcia: parent PCI bridge I/O window: 0x2000 - 0x2fff
[   72.863910] cs: IO port probe 0x2000-0x2fff: clean.
[   73.061157] Synaptics Touchpad, model: 1, fw: 5.9, id: 0x336ab1, caps: 0x984713/0x4000
[   73.101631] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input7
[   74.769720] ACPI: PCI Interrupt Link [C0B7] enabled at IRQ 5
[   74.769727] PCI: setting IRQ 5 as level-triggered
[   74.769732] ACPI: PCI Interrupt 0000:00:1f.5[B] -> Link [C0B7] -> GSI 5 (level, low) -> IRQ 5
[   74.769753] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[   75.440045] intel8x0_measure_ac97_clock: measured 54777 usecs
[   75.440052] intel8x0: clocking to 48000
[   78.183586] cs: IO port probe 0x100-0x3af: clean.
[   78.185624] cs: IO port probe 0x3e0-0x4ff: clean.
[   78.186442] cs: IO port probe 0x820-0x8ff: clean.
[   78.187162] cs: IO port probe 0xc00-0xcf7: clean.
[   78.188110] cs: IO port probe 0xa00-0xaff: clean.
[   78.376334] lp0: using parport0 (interrupt-driven).
[   78.461489] Adding 1253028k swap on /dev/sda5.  Priority:-1 extents:1 across:1253028k
[   78.869432] EXT3 FS on sda1, internal journal
[   79.963221] ip_tables: (C) 2000-2006 Netfilter Core Team
administrator@administrator-laptop:~$ clear
administrator@administrator-laptop:~$ tail -50 /var/log/dmesg
[   71.417168] ACPI: Power Button (CM) [C17C]
[   71.417298] input: Sleep Button (CM) as /devices/virtual/input/input5
[   71.425416] ACPI: Sleep Button (CM) [C11F]
[   71.425539] input: Lid Switch as /devices/virtual/input/input6
[   71.425670] ACPI: Lid Switch [C11E]
[   71.457426] irda_init()
[   71.457458] NET: Registered protocol family 23
[   71.629197] iTCO_vendor_support: vendor-support=0
[   71.685113] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.02 (26-Jul-2007)
[   71.685240] iTCO_wdt: Found a ICH3-M TCO device (Version=1, TCOBASE=0x1060)
[   71.685283] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   71.739897] ACPI: AC Adapter [C11B] (on-line)
[   71.808703] ACPI: Battery Slot [C11D] (battery present)
[   71.808983] ACPI: Battery Slot [C11C] (battery absent)
[   71.868949] nsc_ircc_pnp_probe() : From PnP, found firbase 0x3E8 ; irq 3 ; dma 3.
[   71.868988] nsc-ircc, chip->init
[   71.868999] nsc-ircc, Found chip at base=0x02e
[   71.869026] nsc-ircc, driver loaded (Dag Brattli)
[   71.869034] nsc_ircc_open(), can't get iobase of 0x3e8
[   71.869065] nsc-ircc, Found chip at base=0x02e
[   71.869091] nsc-ircc, driver loaded (Dag Brattli)
[   71.869095] nsc_ircc_open(), can't get iobase of 0x3e8
[   71.871374] nsc-ircc 00:04: disabled
[   72.631956] Yenta: CardBus bridge found at 0000:02:06.0 [0e11:004a]
[   72.631983] Yenta: Enabling burst memory read transactions
[   72.631989] Yenta: Using CSCINT to route CSC interrupts to PCI
[   72.631991] Yenta: Routing CardBus interrupts to PCI
[   72.631998] Yenta TI: socket 0000:02:06.0, mfunc 0x012c1202, devctl 0x64
[   72.863885] Yenta: ISA IRQ mask 0x0038, PCI irq 11
[   72.863892] Socket status: 30000006
[   72.863897] Yenta: Raising subordinate bus# of parent bus (#02) from #03 to #06
[   72.863906] pcmcia: parent PCI bridge I/O window: 0x2000 - 0x2fff
[   72.863910] cs: IO port probe 0x2000-0x2fff: clean.
[   73.061157] Synaptics Touchpad, model: 1, fw: 5.9, id: 0x336ab1, caps: 0x984713/0x4000
[   73.101631] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input7
[   74.769720] ACPI: PCI Interrupt Link [C0B7] enabled at IRQ 5
[   74.769727] PCI: setting IRQ 5 as level-triggered
[   74.769732] ACPI: PCI Interrupt 0000:00:1f.5[B] -> Link [C0B7] -> GSI 5 (level, low) -> IRQ 5
[   74.769753] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[   75.440045] intel8x0_measure_ac97_clock: measured 54777 usecs
[   75.440052] intel8x0: clocking to 48000
[   78.183586] cs: IO port probe 0x100-0x3af: clean.
[   78.185624] cs: IO port probe 0x3e0-0x4ff: clean.
[   78.186442] cs: IO port probe 0x820-0x8ff: clean.
[   78.187162] cs: IO port probe 0xc00-0xcf7: clean.
[   78.188110] cs: IO port probe 0xa00-0xaff: clean.
[   78.376334] lp0: using parport0 (interrupt-driven).
[   78.461489] Adding 1253028k swap on /dev/sda5.  Priority:-1 extents:1 across:1253028k
[   78.869432] EXT3 FS on sda1, internal journal
[   79.963221] ip_tables: (C) 2000-2006 Netfilter Core Team
administrator@administrator-laptop:~$ lsusb
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 002: ID 1410:2110  
Bus 001 Device 001: ID 0000:0000  
administrator@administrator-laptop:~$ sudo gnome-ppp
[sudo] password for administrator: 
WVCONF: /root/.wvdial.conf
GNOME PPP: Connecting...
GNOME PPP: STDERR: --> Ignoring malformed input line: ";Do NOT edit this file by hand!"
GNOME PPP: STDERR: --> WvDial: Internet dialer version 1.60
GNOME PPP: STDERR: --> Cannot get information for serial port.
GNOME PPP: STDERR: --> Initializing modem.
GNOME PPP: STDERR: --> Sending: ATZ
GNOME PPP: STDERR: ATZ
GNOME PPP: STDERR: OK
GNOME PPP: STDERR: --> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
GNOME PPP: STDERR: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
GNOME PPP: STDERR: OK
GNOME PPP: STDERR: --> Modem initialized.
GNOME PPP: STDERR: --> Sending: ATM1L3DT3143020551
GNOME PPP: STDERR: --> Waiting for carrier.
GNOME PPP: STDERR: ATM1L3DT3143020551
GNOME PPP: STDERR: NO ANSWER
GNOME PPP: STDERR: --> No Answer.  Trying again.
GNOME PPP: STDERR: --> Maximum Attempts Exceeded..Aborting!!
GNOME PPP: STDERR: --> Disconnecting at Fri Aug 15 15:30:08 2008
administrator@administrator-laptop:~$ lsusb
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 002: ID 1410:2110  
Bus 001 Device 001: ID 0000:0000  
administrator@administrator-laptop:~$ tail -25 /var/log/dmesg
[   72.631989] Yenta: Using CSCINT to route CSC interrupts to PCI
[   72.631991] Yenta: Routing CardBus interrupts to PCI
[   72.631998] Yenta TI: socket 0000:02:06.0, mfunc 0x012c1202, devctl 0x64
[   72.863885] Yenta: ISA IRQ mask 0x0038, PCI irq 11
[   72.863892] Socket status: 30000006
[   72.863897] Yenta: Raising subordinate bus# of parent bus (#02) from #03 to #06
[   72.863906] pcmcia: parent PCI bridge I/O window: 0x2000 - 0x2fff
[   72.863910] cs: IO port probe 0x2000-0x2fff: clean.
[   73.061157] Synaptics Touchpad, model: 1, fw: 5.9, id: 0x336ab1, caps: 0x984713/0x4000
[   73.101631] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input7
[   74.769720] ACPI: PCI Interrupt Link [C0B7] enabled at IRQ 5
[   74.769727] PCI: setting IRQ 5 as level-triggered
[   74.769732] ACPI: PCI Interrupt 0000:00:1f.5[B] -> Link [C0B7] -> GSI 5 (level, low) -> IRQ 5
[   74.769753] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[   75.440045] intel8x0_measure_ac97_clock: measured 54777 usecs
[   75.440052] intel8x0: clocking to 48000
[   78.183586] cs: IO port probe 0x100-0x3af: clean.
[   78.185624] cs: IO port probe 0x3e0-0x4ff: clean.
[   78.186442] cs: IO port probe 0x820-0x8ff: clean.
[   78.187162] cs: IO port probe 0xc00-0xcf7: clean.
[   78.188110] cs: IO port probe 0xa00-0xaff: clean.
[   78.376334] lp0: using parport0 (interrupt-driven).
[   78.461489] Adding 1253028k swap on /dev/sda5.  Priority:-1 extents:1 across:1253028k
[   78.869432] EXT3 FS on sda1, internal journal
[   79.963221] ip_tables: (C) 2000-2006 Netfilter Core Team
administrator@administrator-laptop:~$ 
administrator@administrator-laptop:~$

---

