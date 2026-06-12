---
title: "PCMCIA does not bring up eth0 during boot"
date: 2007-12-15
forum: Networking &amp; Wireless
---

### Post by allanh on 2007-12-15
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/45295](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/45295) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Hi,

I'm new to Ubuntu, and I've just installed it on an old laptop.  Everything works, except that the PCMCIA network card doesn't come up after boot.  Ejecting the card and plugging it back in makes networking come up.

This matches the symptoms in this bug:
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/45295](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/45295)

Question: is there anything I can do to make the card come up automatically?

Thanks,
Allan

HP Omnibook 7150

[    0.000000] Linux version 2.6.22-14-generic (buildd@palmer) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Sun Oct 14 23:05:12 GMT 2007 (Ubuntu 2.6.22-14.46-generic)


Here's where it didn't work during boot:
...
[   59.783231] PCI: Bus 6, cardbus bridge: 0000:00:04.1
[   59.783246]   IO window: 00001800-000018ff
[   59.783263]   IO window: 00001c00-00001cff
[   59.783282]   PREFETCH window: 28000000-2bffffff
[   59.783301]   MEM window: 2c000000-2fffffff
[   59.783364] PCI: Found IRQ 10 for device 0000:00:04.0
[   59.783405] PCI: Sharing IRQ 10 with 0000:01:00.0
[   59.783446] PCI: Found IRQ 10 for device 0000:00:04.1
...
[  118.474689] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[  118.490548] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
...
[  122.803231] Yenta: CardBus bridge found at 0000:00:04.0 [103c:0006]
[  122.803281] Yenta: Enabling burst memory read transactions
[  122.803301] Yenta: Using CSCINT to route CSC interrupts to PCI
[  122.803316] Yenta: Routing CardBus interrupts to PCI
[  122.803336] Yenta TI: socket 0000:00:04.0, mfunc 0x01021c72, devctl 0x66
[  123.034918] Yenta: ISA IRQ mask 0x0a98, PCI irq 10
[  123.034942] Socket status: 30000006
[  123.035559] Yenta: CardBus bridge found at 0000:00:04.1 [103c:0006]
[  123.035605] Yenta: Using CSCINT to route CSC interrupts to PCI
[  123.035620] Yenta: Routing CardBus interrupts to PCI
[  123.035642] Yenta TI: socket 0000:00:04.1, mfunc 0x01021c72, devctl 0x66
[  123.081459] input: PC Speaker as /class/input/input2
[  123.266868] Yenta: ISA IRQ mask 0x0a98, PCI irq 10
[  123.266891] Socket status: 30000010
[  123.867954] input: ImPS/2 Logitech Wheel Mouse as /class/input/input3
[  123.902115] pccard: PCMCIA card inserted into slot 1
[  125.241155] piix4_smbus 0000:00:07.3: Found 0000:00:07.3 device
[  126.013581] parport_pc 00:0d: reported by Plug and Play BIOS
[  126.013689] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[  127.782257] cs: IO port probe 0x100-0x3af: clean.
[  127.783628] cs: IO port probe 0x3e0-0x4ff: clean.
[  127.784303] cs: IO port probe 0x820-0x8ff: clean.
[  127.784921] cs: IO port probe 0xc00-0xcf7: clean.
[  127.786284] cs: IO port probe 0xa00-0xaff: clean.
[  127.832406] cs: IO port probe 0x100-0x3af: clean.
[  127.833773] cs: IO port probe 0x3e0-0x4ff: clean.
[  127.834491] cs: IO port probe 0x820-0x8ff: clean.
[  127.835110] cs: IO port probe 0xc00-0xcf7: clean.
[  127.836386] cs: IO port probe 0xa00-0xaff: clean.
[  127.837070] cs: memory probe 0xa0000000-0xa0ffffff: clean.
[  128.054373] pcmcia: registering new device pcmcia1.0
[  128.567073] es1968: not attempting power management.
[  129.015010] 1.0: ttyS3 at I/O 0x2e8 (irq = 3) is a 16550A
[  129.170030] es1968: clocking to 48000
...

It looks to me like it found the uart (for the 56k modem also on the PCMCIA card) and created ttyS3 for it, but didn't initialise the ethernet controller.


Here's where it comes up after I eject the card:

[  289.049584] pccard: card ejected from slot 1
[  294.933200] pccard: PCMCIA card inserted into slot 1
[  294.933588] pcmcia: registering new device pcmcia1.0
[  297.737811] eth%d: MII link partner: 05e1
[  297.737837] eth%d: MII selected
[  297.761097] eth%d: media 100BaseT, silicon revision 5
[  297.761634] eth0: Xircom: port 0x300, irq 3, hwaddr 00:10:A4:04:5E:3F
[  297.761740] pcmcia: registering new device pcmcia1.1
[  297.762566] 1.1: ttyS3 at I/O 0x2e8 (irq = 3) is a 16550A
[  301.021717] eth0: MII link partner: 05e1
[  301.021744] eth0: MII selected
[  301.045006] eth0: media 100BaseT, silicon revision 5
[  303.913221] NET: Registered protocol family 17
[  306.027798] NET: Registered protocol family 10
[  306.028959] lo: Disabled Privacy Extensions
[  317.020533] eth0: no IPv6 routers present
[ 4770.212729] eth0: MII link partner: 05e1
[ 4770.212755] eth0: MII selected
[ 4770.237205] eth0: media 100BaseT, silicon revision 5
[ 4788.596853] eth0: no IPv6 routers present

---

