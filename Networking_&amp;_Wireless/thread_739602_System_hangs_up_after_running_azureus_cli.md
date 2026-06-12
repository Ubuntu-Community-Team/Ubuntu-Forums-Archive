---
title: "System hangs up after running azureus cli"
date: 2008-03-29
forum: Networking &amp; Wireless
---

### Post by Zuhaib on 2008-03-29
Hey, i am making the switch from rtorrent to azureus as some have said it might help me be able to play media from the same box at the same time seed.  As azureus supports disk cache and my understand rtorrent does not.
But now after i let me system run for a while (2/3 hours) i will come back and find it just hanged up.  Cant ssh in, no ping nothing.  I do a cold reboot and the last longs i see is this
```
Mar 29 15:07:32 homenas kernel: [93016.000000] NETDEV WATCHDOG: eth0: transmit timed out
Mar 29 15:07:32 homenas kernel: [93016.000000] eth0: Transmit timed out, status 1003, PHY status 782d, resetting...
Mar 29 15:07:32 homenas kernel: [93016.000000] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
Mar 29 15:07:32 homenas kernel: [93022.000000] NETDEV WATCHDOG: eth0: transmit timed out
Mar 29 15:07:32 homenas kernel: [93022.000000] eth0: Transmit timed out, status 1003, PHY status 782d, resetting...
Mar 29 15:07:32 homenas kernel: [93022.000000] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
Mar 29 15:07:32 homenas kernel: [93027.140000] hda: dma_timer_expiry: dma status == 0x24
Mar 29 15:07:32 homenas kernel: [93028.000000] NETDEV WATCHDOG: eth0: transmit timed out
Mar 29 15:07:32 homenas kernel: [93028.000000] eth0: Transmit timed out, status 1003, PHY status 782d, resetting...
Mar 29 15:07:32 homenas kernel: [93028.000000] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
Mar 29 15:07:32 homenas kernel: [93036.000000] NETDEV WATCHDOG: eth0: transmit timed out
Mar 29 15:07:32 homenas kernel: [93036.000000] eth0: Transmit timed out, status 1003, PHY status 782d, resetting...
Mar 29 15:07:32 homenas kernel: [93036.000000] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
Mar 29 15:07:32 homenas kernel: [93037.130000] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
Mar 29 15:07:32 homenas kernel: [93037.130000] ata2.00: cmd 25/00:c8:ea:6d:e9/00:01:10:00:00/e0 tag 0 cdb 0x0 data 233472 in
Mar 29 15:07:32 homenas kernel: [93037.130000]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
Mar 29 15:07:32 homenas kernel: [93037.140000] hda: DMA interrupt recovery
Mar 29 15:07:32 homenas kernel: [93037.140000] hda: lost interrupt
Mar 29 15:07:32 homenas kernel: [93037.460000] ata2: soft resetting port
Mar 29 15:07:32 homenas kernel: [93037.620000] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
Mar 29 15:07:32 homenas kernel: [93050.000000] NETDEV WATCHDOG: eth0: transmit timed out
Mar 29 15:07:32 homenas kernel: [93050.000000] eth0: Transmit timed out, status 1003, PHY status 782d, resetting...
Mar 29 15:07:32 homenas kernel: [93050.000000] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
Mar 29 15:07:32 homenas kernel: [93057.140000] hda: dma_timer_expiry: dma status == 0x24
Mar 29 15:07:32 homenas kernel: [93060.000000] NETDEV WATCHDOG: eth0: transmit timed out
Mar 29 15:07:32 homenas kernel: [93060.000000] eth0: Transmit timed out, status 1003, PHY status 782d, resetting...
Mar 29 15:07:32 homenas kernel: [93060.000000] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
Mar 29 15:07:32 homenas kernel: [93067.140000] hda: DMA interrupt recovery
Mar 29 15:07:32 homenas kernel: [93067.140000] hda: lost interrupt
Mar 29 15:07:32 homenas kernel: [93067.640000] ata2.00: qc timeout (cmd 0x27)
Mar 29 15:07:32 homenas kernel: [93067.640000] ata2.00: ata_hpa_resize 1: hpa sectors (0) is smaller than sectors (976773168)
Mar 29 15:07:32 homenas kernel: [93067.640000] ata2.00: failed to set xfermode (err_mask=0x40)
Mar 29 15:07:32 homenas kernel: [93067.640000] ata2: failed to recover some devices, retrying in 5 secs
Mar 29 15:07:32 homenas kernel: [93072.650000] ata2: hard resetting port
Mar 29 15:07:32 homenas kernel: [93073.160000] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
Mar 29 15:07:32 homenas kernel: [93074.000000] NETDEV WATCHDOG: eth0: transmit timed out
Mar 29 15:07:32 homenas kernel: [93074.000000] eth0: Transmit timed out, status 1003, PHY status 782d, resetting...
Mar 29 15:07:32 homenas kernel: [93074.000000] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
Mar 29 15:07:32 homenas kernel: [93078.000000] NETDEV WATCHDOG: eth0: transmit timed out
Mar 29 15:07:32 homenas kernel: [93078.000000] eth0: Transmit timed out, status 0003, PHY status 782d, resetting...
Mar 29 15:07:32 homenas kernel: [93078.000000] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
Mar 29 15:07:32 homenas kernel: [93087.140000] hda: dma_timer_expiry: dma status == 0x24
Mar 29 15:07:32 homenas kernel: [93096.000000] NETDEV WATCHDOG: eth0: transmit timed out
Mar 29 15:07:32 homenas kernel: [93096.000000] eth0: Transmit timed out, status 1003, PHY status 782d, resetting...
Mar 29 15:07:32 homenas kernel: [93096.000000] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
Mar 29 15:07:32 homenas kernel: [93097.140000] hda: DMA interrupt recovery
Mar 29 15:07:32 homenas kernel: [93097.140000] hda: lost interrupt
Mar 29 15:07:32 homenas kernel: [93103.180000] ata2.00: qc timeout (cmd 0x27)
Mar 29 15:07:32 homenas kernel: [93103.180000] ata2.00: ata_hpa_resize 1: hpa sectors (0) is smaller than sectors (976773168)
Mar 29 15:07:32 homenas kernel: [93103.180000] ata2.00: failed to set xfermode (err_mask=0x40)
Mar 29 15:07:32 homenas kernel: [93103.180000] ata2.00: limiting speed to UDMA/100:PIO3
Mar 29 15:07:32 homenas kernel: [93103.180000] ata2: failed to recover some devices, retrying in 5 secs
Mar 29 15:07:32 homenas kernel: [93108.000000] NETDEV WATCHDOG: eth0: transmit timed out
Mar 29 15:07:32 homenas kernel: [93108.000000] eth0: Transmit timed out, status 1003, PHY status 782d, resetting...
Mar 29 15:07:32 homenas kernel: [93108.000000] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
Mar 29 15:07:32 homenas kernel: [93108.190000] ata2: hard resetting port
Mar 29 15:07:32 homenas kernel: [93108.700000] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
Mar 29 15:07:32 homenas kernel: [93117.140000] hda: dma_timer_expiry: dma status == 0x24
Mar 29 15:07:32 homenas kernel: [93120.000000] NETDEV WATCHDOG: eth0: transmit timed out
Mar 29 15:07:32 homenas kernel: [93120.000000] eth0: Transmit timed out, status 1003, PHY status 782d, resetting...
Mar 29 15:07:32 homenas kernel: [93120.000000] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
Mar 29 15:07:32 homenas kernel: [93127.140000] hda: DMA interrupt recovery
Mar 29 15:07:32 homenas kernel: [93127.140000] hda: lost interrupt
Mar 29 15:07:32 homenas kernel: [93134.000000] NETDEV WATCHDOG: eth0: transmit timed out
Mar 29 15:07:32 homenas kernel: [93134.000000] eth0: Transmit timed out, status 1003, PHY status 782d, resetting...
Mar 29 15:07:32 homenas kernel: [93134.000000] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
Mar 29 15:07:32 homenas kernel: [93138.720000] ata2.00: qc timeout (cmd 0x27)
Mar 29 15:07:32 homenas kernel: [93138.720000] ata2.00: ata_hpa_resize 1: hpa sectors (0) is smaller than sectors (976773168)
Mar 29 15:07:32 homenas kernel: [93138.720000] ata2.00: failed to set xfermode (err_mask=0x40)
Mar 29 15:07:32 homenas kernel: [93138.720000] ata2.00: disabled
Mar 29 15:07:32 homenas kernel: [93139.230000] ata2: EH complete
Mar 29 15:07:32 homenas kernel: [93139.230000] sd 1:0:0:0: [sdb] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
Mar 29 15:07:32 homenas kernel: [93139.230000] end_request: I/O error, dev sdb, sector 283733482
Mar 29 15:07:32 homenas kernel: [93139.230000] sd 1:0:0:0: [sdb] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
Mar 29 15:07:32 homenas kernel: [93139.230000] end_request: I/O error, dev sdb, sector 283853650
Mar 29 15:07:32 homenas kernel: [93139.230000] sd 1:0:0:0: [sdb] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
Mar 29 15:07:32 homenas kernel: [93139.230000] end_request: I/O error, dev sdb, sector 185938
Mar 29 15:07:32 homenas kernel: [93139.230000] sd 1:0:0:0: [sdb] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
Mar 29 15:07:32 homenas kernel: [93139.230000] end_request: I/O error, dev sdb, sector 185954
Mar 29 15:07:32 homenas kernel: [93139.230000] Buffer I/O error on device sdb1, logical block 23240
Mar 29 15:07:32 homenas kernel: [93139.230000] lost page write due to I/O error on sdb1
Mar 29 15:07:32 homenas kernel: [93139.230000] sd 1:0:0:0: [sdb] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
Mar 29 15:07:32 homenas kernel: [93139.230000] end_request: I/O error, dev sdb, sector 283733482
Mar 29 15:07:32 homenas kernel: [93139.230000] Aborting journal on device sdb1.
Mar 29 15:07:32 homenas kernel: [93139.230000] ext3_abort called.
Mar 29 15:07:32 homenas kernel: [93139.230000] EXT3-fs error (device sdb1): ext3_journal_start_sb: Detected aborted journal
Mar 29 15:07:32 homenas kernel: [93139.230000] Remounting filesystem read-only
Mar 29 15:07:32 homenas kernel: [93139.230000] sd 1:0:0:0: [sdb] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
Mar 29 15:07:32 homenas kernel: [93139.230000] end_request: I/O error, dev sdb, sector 283733482
Mar 29 15:07:32 homenas kernel: [93139.230000] sd 1:0:0:0: [sdb] READ CAPACITY failed
Mar 29 15:07:32 homenas kernel: [93139.230000] sd 1:0:0:0: [sdb] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
Mar 29 15:07:32 homenas kernel: [93139.230000] sd 1:0:0:0: [sdb] Sense not available.
Mar 29 15:07:32 homenas kernel: [93139.240000] sd 1:0:0:0: [sdb] Write Protect is off
Mar 29 15:07:32 homenas kernel: [93139.240000] sd 1:0:0:0: [sdb] Mode Sense: 00 00 00 00
Mar 29 15:10:02 homenas kernel: [93139.250000] sd 1:0:0:0: [sdb] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
Mar 29 15:10:02 homenas kernel: [93139.250000] end_request: I/O error, dev sdb, sector 283733482
Mar 29 15:10:02 homenas kernel: [93139.250000] sd 1:0:0:0: [sdb] Asking for cache data failed
Mar 29 15:10:02 homenas kernel: [93139.250000] sd 1:0:0:0: [sdb] Assuming drive cache: write through
Mar 29 15:10:02 homenas kernel: [93147.140000] hda: dma_timer_expiry: dma status == 0x24
Mar 29 15:10:02 homenas kernel: [93148.000000] NETDEV WATCHDOG: eth0: transmit timed out
Mar 29 15:10:02 homenas kernel: [93148.000000] eth0: Transmit timed out, status 1003, PHY status 782d, resetting...
Mar 29 15:10:02 homenas kernel: [93148.000000] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
Mar 29 15:10:02 homenas kernel: [93157.140000] hda: DMA interrupt recovery
Mar 29 15:10:02 homenas kernel: [93157.140000] hda: lost interrupt
Mar 29 15:10:02 homenas kernel: [93170.000000] NETDEV WATCHDOG: eth0: transmit timed out
```
Whats going on?  Looks like my nic is getting a bit out of hand, but also my HD? 
any help would be great.

---

### Post by netlogic on 2008-03-29
Dear Admin, this thread doesn't belong here. Please move it.

thanks

---

### Post by craigp84 on 2008-03-30
Looks like either a hardware, or more likely a driver issue with your network card.

What type of network card do you have?

If you want a quick fix, install another (different type of) network card and use that as eth0 (you should update /etc/iftab).

-c

---

