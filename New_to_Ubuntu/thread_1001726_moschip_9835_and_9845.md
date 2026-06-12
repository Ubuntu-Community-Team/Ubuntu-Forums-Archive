---
title: "moschip 9835 and 9845"
date: 2008-12-04
forum: New to Ubuntu
---

### Post by eddijz on 2008-12-04
i can't install my moschip cards (9835 and 9845). My ubuntu see only 4 com ports as default, but i need at least 6. How to install two more com ports?

i'm using Ubuntu 8.10 with core 2.6.27-9-generic.

04:08.0 Serial controller: NetMos Technology PCI 9845 Multi-I/O Controller (rev 01) (prog-if 02)
	Subsystem: LSI Logic / Symbios Logic Device 0004
	Control: I/O+ Mem+ BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
	Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Interrupt: pin A routed to IRQ 19
	Region 0: I/O ports at ec00 [size=8]
	Region 1: I/O ports at e880 [size=8]
	Region 2: I/O ports at e800 [size=8]
	Region 3: I/O ports at e480 [size=8]
	Region 4: I/O ports at e400 [size=8]
	Region 5: I/O ports at e080 [size=16]
	Kernel driver in use: serial
	Kernel modules: parport_serial

04:0a.0 Communication controller: NetMos Technology PCI 9835 Multi-I/O Controller (rev 01)
	Subsystem: LSI Logic / Symbios Logic Device 0012
	Control: I/O+ Mem+ BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
	Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Interrupt: pin A routed to IRQ 17
	Region 0: I/O ports at e000 [size=8]
	Region 1: I/O ports at dc00 [size=8]
	Region 2: I/O ports at d880 [size=8]
	Region 3: I/O ports at d800 [size=8]
	Region 4: I/O ports at d480 [size=8]
	Region 5: I/O ports at d400 [size=16]
	Kernel driver in use: parport_serial
	Kernel modules: parport_serial

i work 3 days on this and my success is 0%
please help.. write in details becouse i'm using ubuntu only 1 week.

---

### Post by eddijz on 2008-12-04
plz..

---

### Post by eddijz on 2008-12-05
i'm doing like this:

root@server:~# MAKEDEV -v ttyS4
create ttyS4	c 4 68 root:dialout 0660
root@server:~# mknod ttyS4 c 4 68
mknod: `ttyS4': File exists
root@server:~# mknod /dev/ttyS4 c 4 68
root@server:~# setserial /dev/ttyS4 port e880 UART 16550A irq 19 Baud_base 115200
/dev/ttyS4: No such device or address

how you can see at the setserial I stop..
in menu.lst in kernel line I add 8250.nr_uarts=16

---

