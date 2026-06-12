---
title: "Broadcom BCM5721 tg3 driver badly confused in Trusty Proliant ML110 G4"
date: 2014-11-24
forum: Networking &amp; Wireless
---

### Post by FrankAu on 2014-11-24
I have (suddenly?) encountered a problem getting a Proliant ML100 G4 firewall (newly booting Trusty) to recognise the mobo NIC - which is a Broadcom 5721 NetXtreme!
Also installed is a pair of RealTek RTL8139 NIC's ... and in syslog I found ...

[SIZE=1]Nov 24 00:15:02 gvmp kernel: [    5.108643] 8139cp: 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)[/SIZE]
[SIZE=1]Nov 24 00:15:02 gvmp kernel: [    5.108678] 8139cp 0000:0a:00.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip, use 8139too[/SIZE]
[SIZE=1]Nov 24 00:15:02 gvmp kernel: [    5.108693] 8139cp 0000:0a:01.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip, use 8139too[/SIZE]
[SIZE=1]Nov 24 00:15:02 gvmp kernel: [    5.111471] sata_mv 0000:01:00.0: version 1.28[/SIZE]
[SIZE=1]Nov 24 00:15:02 gvmp kernel: [    5.111907] sata_mv 0000:01:00.0: Gen-IIE 32 slots 4 ports ? mode IRQ via INTx[/SIZE]
[SIZE=1]Nov 24 00:15:02 gvmp kernel: [    5.118215] scsi4 : sata_mv[/SIZE]
[SIZE=1]Nov 24 00:15:02 gvmp kernel: [    5.122425] scsi5 : sata_mv[/SIZE]
[SIZE=1]Nov 24 00:15:02 gvmp kernel: [    5.124793] 8139too: 8139too Fast Ethernet driver 0.9.28[/SIZE]
[SIZE=1]Nov 24 00:15:02 gvmp kernel: [    5.125875] 8139too 0000:0a:00.0 eth0: RealTek RTL8139 at 0x00015000, 00:14:6c:8b:7e:b5, IRQ 16[/SIZE]
[SIZE=1]Nov 24 00:15:02 gvmp kernel: [    5.126853] 8139too 0000:0a:01.0 eth1: RealTek RTL8139 at 0x00015400, 00:18:4d:71:ef:1b, IRQ 18[/SIZE]
[SIZE=1]Nov 24 00:15:02 gvmp kernel: [    5.129547] scsi6 : sats_mv[/SIZE]
[SIZE=1]Nov 24 00:15:02 gvmp kernel: [    5.136495] scsi7 : sata_mv[/SIZE]
[SIZE=1]Nov 24 00:15:02 gvmp kernel: [    5.136597] ata5: SATA max UDMA/133 mmio m1048576@0xefa00000 port 0xefa22000 irq 16[/SIZE]
[SIZE=1]Nov 24 00:15:02 gvmp kernel: [    5.136602] ata6: SATA max UDMA/133 mmio m1048576@0xefa00000 port 0xefa24000 irq 16[/SIZE]
[SIZE=1]Nov 24 00:15:02 gvmp kernel: [    5.136606] ata7: SATA max UDMA/133 mmio m1048576@0xefa00000 port 0xefa26000 irq 16[/SIZE]
[SIZE=1]Nov 24 00:15:02 gvmp kernel: [    5.136609] ata8: SATA max UDMA/133 mmio m1048576@0xefa00000 port 0xefa28000 irq 16[/SIZE]
[SIZE=1]Nov 24 00:15:02 gvmp kernel: [    5.140973] tg3.c:v3.134 (Sep 16, 2013)[/SIZE]
[SIZE=1]Nov 24 00:15:02 gvmp kernel: [    5.167186] tg3 0000:04:00.0 eth2: Tigon3 [partno(N/A) rev 4201] (PCI Express) MAC address 00:1e:0b:6f:9e:c9[/SIZE]
[SIZE=1]Nov 24 00:15:02 gvmp kernel: [    5.167193] tg3 0000:04:00.0 eth2: attached PHY is 5750 (10/100/1000Base-T Ethernet) (WireSpeed[1], EEE[0])[/SIZE]
[SIZE=1]Nov 24 00:15:02 gvmp kernel: [    5.167197] tg3 0000:04:00.0 eth2: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[1] TSOcap[1][/SIZE]
[SIZE=1]Nov 24 00:15:02 gvmp kernel: [    5.167201] tg3 0000:04:00.0 eth2: dma_rwctrl[76180000] dma_mask[64-bit][/SIZE]


After blacklisting the 8139cp things still didn't improve ... of the 2 ethernet services started (eth0 and eth1) either (a) only 1 was operating, or (b) if both were working shorewall/squid3 were confused and seem to be blocking all traffic from the LAN to the internet.
A bit further on I noticed ...

[SIZE=1]Nov 24 08:08:31 gvmp kernel: [   20.822482] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready[/SIZE]
[SIZE=1]Nov 24 08:08:31 gvmp kernel: [   20.822494] IPv6: ADDRCONF(NETDEV_UP): eth1: link is not ready[/SIZE]
[SIZE=1]Nov 24 08:08:31 gvmp kernel: [   20.822503] IPv6: ADDRCONF(NETDEV_UP): eth2: link is not ready[/SIZE]
...
Nov 24 08:08:31 gvmp kernel: [   21.070191] ipmi_si: probing via ACPI
[SIZE=1]Nov 24 08:08:31 gvmp kernel: [   21.070233] ipmi_si 00:00: [io  0x0ca2-0x0ca3] regsize 1 spacing 1 irq 0[/SIZE]
[SIZE=1]Nov 24 08:08:31 gvmp kernel: [   21.070237] ipmi_si: Adding ACPI-specified kcs state machine[/SIZE]
...
Nov 24 08:08:31 gvmp kernel: [   21.201584] systemd-udevd[416]: renamed network interface eth2 to rename4
[SIZE=1]Nov 24 08:08:31 gvmp kernel: [   21.203017] intel_rng: FWH not detected[/SIZE]
[SIZE=1]Nov 24 08:08:31 gvmp kernel: [   21.214132] EXT4-fs (md0): mounting ext3 file system using the ext4 subsystem[/SIZE]
[SIZE=1]Nov 24 08:08:31 gvmp kernel: [   21.224671] ACPI Warning: 0x00001028-0x0000102f SystemIO conflicts with Region \_SB_.PCI0.LPC0.PMIO 1 (20131115/utaddress-251)[/SIZE]
[SIZE=1]Nov 24 08:08:31 gvmp kernel: [   21.224683] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver[/SIZE]
[SIZE=1]Nov 24 08:08:31 gvmp kernel: [   21.224690] ACPI Warning: 0x00001180-0x000011af SystemIO conflicts with Region \_SB_.PCI0.LPC0.GPOX 1 (20131115/utaddress-251)[/SIZE]
[SIZE=1]Nov 24 08:08:31 gvmp kernel: [   21.224708] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver[/SIZE]
[SIZE=1]Nov 24 08:08:31 gvmp kernel: [   21.224914] lpc_ich: Resource conflict(s) found affecting gpio_ich[/SIZE]
[SIZE=1]Nov 24 08:08:31 gvmp kernel: [   21.232339] systemd-udevd[409]: renamed network interface eth0 to rename2[/SIZE]
[SIZE=1]Nov 24 08:08:31 gvmp kernel: [   21.233441] leds_ss4200: no LED devices found[/SIZE]
[SIZE=1]Nov 24 08:08:31 gvmp kernel: [   21.248188] systemd-udevd[410]: renamed network interface eth1 to eth2[/SIZE]
[SIZE=1]Nov 24 08:08:31 gvmp kernel: [   21.264397] systemd-udevd[416]: renamed network interface rename4 to eth0[/SIZE]
[SIZE=1]Nov 24 08:08:31 gvmp kernel: [   21.324323] systemd-udevd[409]: renamed network interface rename2 to eth1[/SIZE]

Correct me I am a smoking something ... but it seems the mobo NIC is not being detected properly? and therefore is not being assigned the customary eth0 identity!  This (eth0) is being assigned to the first 8139 NIC, and is detected a bit later in the boot sequence when some renaming occurs to "recover" the situation.  However it seems networking at the higher layers is borked by then.

Urgent question is ... how do I get past this?  Is it a bad driver that no longer recognises the mobo NIC or is it an issue with Trusty?  Any ideas will be gratefully received.

---

### Post by FrankAu on 2014-11-25
Heat is off (a bit) ... as I have bailed out on trying to fix this quickly by switching to a commodity router/firewall.

Still investigating why the driver identification/device renaming fandango is happening.

---

