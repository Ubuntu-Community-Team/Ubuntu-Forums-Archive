---
title: "Server Ethernet Connection"
date: 2008-02-10
forum: Networking &amp; Wireless
---

### Post by Woohoo on 2008-02-10
My ethernet connection keeps going up and down randomly. I have a IBM x335 rack mount server that has two ethernet ports on the back. I've tried both and the same thing happens. Basically, it's up for awhile and then goes down, and then back up. I've tried a lot of different things but can't seem to figure it out. Here is some basic info I've recorded:

```

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth1
iface eth1 inet static
        address 192.168.1.6
        netmask 255.255.255.0
        network 192.168.1.0
        broadcast 192.168.1.255
        gateway 192.168.1.1
-------------------------------------------------

02:01.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5703X Gigabit Ethernet (rev 02)
02:02.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5703X Gigabit Ethernet (rev 02)

-------------------------------------------------

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth1
0.0.0.0         192.168.1.1     0.0.0.0         UG    100    0        0 eth1

```

Since I have local access to the box, I've tried pinging IP's and domain names to see if it was DNS. It doesn't appear to be since when it goes down I can't even SSH into it from my other local boxes. If it helps,  I am using Ubuntu Server Edition 7.10 and the "tg3" driver for the Ethernet card.

---

### Post by mrsteveman1 on 2008-02-10
When you say the T3 driver, are you referring to the ones you can download from broadcom?

It would be helpful for you to post the output of dmesg and perhaps also the boot log.

When the connection stops working, do the indicator lights on the servers ports or the switchport stay lit up? IE does the physical connection drop?

---

### Post by Woohoo on 2008-02-10
The ports stay lit up and I didn't download any driver. I've just looked up a bit about these network cards and if I run lsmod it shows the "tg3"(sorry about typo earlier) driver. Also, this isn't all of dmesg but a good portion of the end:

```

[   63.085558] hub 1-0:1.0: USB hub found
[   63.085571] hub 1-0:1.0: 4 ports detected
[   63.088866] eth1: Tigon3 [partno(BCM95703A30) rev 1002 PHY(5703)] (PCIX:100MHz:64-bit) 10/100/1000Base-T Ethernet 00:0d:60:1c:6c:4b
[   63.088875] eth1: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] WireSpeed[1] TSOcap[1]
[   63.088878] eth1: dma_rwctrl[769c4000] dma_mask[64-bit]
[   64.260408] ioc0: 53C1030: Capabilities={Initiator}
[   65.870256] scsi0 : ioc0: LSI53C1030, FwRev=01000e00h, Ports=1, MaxQ=222, IRQ=22
[   66.427676] scsi 0:0:0:0: Direct-Access     COMPAQ   BF018863B4       HPB3 PQ: 0 ANSI: 3
[   66.427695]  target0:0:0: Beginning Domain Validation
[   66.431259] scsi1 : pata_serverworks
[   66.432188] scsi2 : pata_serverworks
[   66.432263] ata1: PATA max UDMA/100 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x00010700 irq 14
[   66.432269] ata2: PATA max UDMA/100 cmd 0x00010170 ctl 0x00010376 bmdma 0x00010708 irq 15
[   66.442507]  target0:0:0: Ending Domain Validation
[   66.442565]  target0:0:0: FAST-80 WIDE SCSI 160.0 MB/s DT (12.5 ns, offset 127)
[   66.445170] scsi 0:0:1:0: Direct-Access     COMPAQ   BF018863B4       HPB3 PQ: 0 ANSI: 3
[   66.445187]  target0:0:1: Beginning Domain Validation
[   66.458088]  target0:0:1: Ending Domain Validation
[   66.458146]  target0:0:1: FAST-80 WIDE SCSI 160.0 MB/s DT (12.5 ns, offset 127)
[   66.924110] ata2.00: ATAPI: CD-224E, 2.9B, max UDMA/33
[   67.123605] ata2.00: configured for UDMA/33
[   67.123654] scsi: waiting for bus probes to complete ...
[   67.707383] scsi 0:0:8:0: Processor         IBM      25P3495a S320  1 1    PQ: 0 ANSI: 2
[   67.707411]  target0:0:8: Beginning Domain Validation
[   67.708176]  target0:0:8: Ending Domain Validation
[   67.708244]  target0:0:8: asynchronous
[   69.461850] scsi 2:0:0:0: CD-ROM            TEAC     CD-224E          2.9B PQ: 0 ANSI: 5
[   69.497820] sd 0:0:0:0: [sda] 35565080 512-byte hardware sectors (18209 MB)
[   69.507106] sd 0:0:0:0: [sda] Write Protect is off
[   69.507111] sd 0:0:0:0: [sda] Mode Sense: cf 00 10 08
[   69.508228] sd 0:0:0:0: [sda] Write cache: disabled, read cache: enabled, supports DPO and FUA
[   69.508749] sd 0:0:0:0: [sda] 35565080 512-byte hardware sectors (18209 MB)
[   69.517982] sd 0:0:0:0: [sda] Write Protect is off
[   69.517985] sd 0:0:0:0: [sda] Mode Sense: cf 00 10 08
[   69.519097] sd 0:0:0:0: [sda] Write cache: disabled, read cache: enabled, supports DPO and FUA
[   69.519101]  sda: sda1 sda2 < sda5 >
[   69.533340] sd 0:0:0:0: [sda] Attached SCSI disk
[   69.533897] sd 0:0:1:0: [sdb] 35565080 512-byte hardware sectors (18209 MB)
[   69.543159] sd 0:0:1:0: [sdb] Write Protect is off
[   69.543164] sd 0:0:1:0: [sdb] Mode Sense: cf 00 10 08
[   69.544288] sd 0:0:1:0: [sdb] Write cache: disabled, read cache: enabled, supports DPO and FUA
[   69.544809] sd 0:0:1:0: [sdb] 35565080 512-byte hardware sectors (18209 MB)
[   69.554045] sd 0:0:1:0: [sdb] Write Protect is off
[   69.554048] sd 0:0:1:0: [sdb] Mode Sense: cf 00 10 08
[   69.555158] sd 0:0:1:0: [sdb] Write cache: disabled, read cache: enabled, supports DPO and FUA
[   69.555162]  sdb: unknown partition table
[   69.559842] sd 0:0:1:0: [sdb] Attached SCSI disk
[   69.567241] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   69.567293] sd 0:0:1:0: Attached scsi generic sg1 type 0
[   69.567327] scsi 0:0:8:0: Attached scsi generic sg2 type 3
[   69.567367] sr 2:0:0:0: Attached scsi generic sg3 type 5
[   69.573470] sr0: scsi3-mmc drive: 24x/24x cd/rw xa/form2 cdda tray
[   69.573479] Uniform CD-ROM driver Revision: 3.20
[   69.573560] sr 2:0:0:0: Attached scsi CD-ROM sr0
[   69.781743] Attempting manual resume
[   69.781747] swsusp: Resume From Partition 8:5
[   69.781750] PM: Checking swsusp image.
[   69.781996] PM: Resume from disk failed.
[   69.806090] kjournald starting.  Commit interval 5 seconds
[   69.806108] EXT3-fs: mounted filesystem with ordered data mode.
[   71.586690] PM: Writing back config space on device 0000:02:02.0 at offset b (was 164714e4, writing 26f1014)
[   71.586708] PM: Writing back config space on device 0000:02:02.0 at offset 3 (was 4000, writing 4008)
[   71.586715] PM: Writing back config space on device 0000:02:02.0 at offset 2 (was 2000000, writing 2000002)
[   71.586723] PM: Writing back config space on device 0000:02:02.0 at offset 1 (was 2b00000, writing 2b00146)
[   71.586730] PM: Writing back config space on device 0000:02:02.0 at offset 0 (was 164714e4, writing 16a714e4)
[   72.134527] NET: Registered protocol family 10
[   72.134655] lo: Disabled Privacy Extensions
[   72.134765] ADDRCONF(NETDEV_UP): eth1: link is not ready
[   72.905325] Linux agpgart interface v0.102 (c) Dave Jones
[   73.192687] tg3: eth1: Link is up at 100 Mbps, full duplex.
[   73.192693] tg3: eth1: Flow control is on for TX and on for RX.
[   73.198036] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[   73.335691] scb2_flash: warning - can't reserve rom window, continuing
[   73.388535] input: PC Speaker as /class/input/input2
[   73.434446] CFI: Found no SCB2 BIOS Flash device at location zero
[   73.434453] scb2_flash: flash probe failed!
[   73.487566] piix4_smbus 0000:00:0f.0: Found 0000:00:0f.0 device
[   74.210973] loop: module loaded
[   74.260005] lp: driver loaded but no devices found
[   74.400557] Adding 779112k swap on /dev/sda5.  Priority:-1 extents:1 across:779112k
[   74.614680] EXT3 FS on sda1, internal journal
[   83.672048] eth1: no IPv6 routers present

```

If you want me to list more of dmesg, just let me know.

---

### Post by mrsteveman1 on 2008-02-10
Run ethtool eth0 and see what it tells you both normally and if possible, when the disconnection happens. Compare the results and see if anything changes.

Also run 

```
ethtool -S eth0
``` 

to see if there are any visible errors on the adapter

I would also set the connection speed and duplex manually, and turn off autonegotiation since this is a server. Im assuming the link is 100mbps so:

```
sudo ethtool -s eth0 speed 100 duplex full autoneg off
```

Those settings are per boot, so if they help you'll have to put them into a script to run at boot time.

It sounds like the physical connection is ok but it could be interference on the cable. My guess is its a layer 2 problem, so i would also check your ARP table to see if anything looks out of place

```
sudo arp
```

Anyhow if you can test some things when this outage happens you will likely see an error message in dmesg or perhaps /var/log/messages, and if the link goes down ethtool would definitely tell you about it.

---

