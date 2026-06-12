---
title: "Failed Drive?"
date: 2010-05-09
forum: New to Ubuntu
---

### Post by expatCM on 2010-05-09
I found a problem suddenly appeared.  My system froze and then would not boot with one of the data drives installed.  Remove the drive and the system was back to normal.

My first reaction is to blame the hdd manufacturer but I could of course be wrong...  

The following is a log file extract.  It looks like a buffer i/o problem (towards end of log) which in turn suggests a hdd error.   Does anyone read the log file in any other way that suggests the problem is based on my system?

```
  ata4.00: status: { DRDY ERR }
May  9 14:39:00 ubuntu64 kernel: [    9.048004] ata4.00: error: { UNC }
May  9 14:39:00 ubuntu64 kernel: [    9.048004] ata4.00: configured for UDMA/133
May  9 14:39:00 ubuntu64 kernel: [    9.048004] ata4: EH complete
May  9 14:39:00 ubuntu64 kernel: [    9.048004] sd 3:0:0:0: [sdc] 976771055 512-byte hardware sectors (500107 MB)
May  9 14:39:00 ubuntu64 kernel: [    9.048004] sd 3:0:0:0: [sdc] Write Protect is off
May  9 14:39:00 ubuntu64 kernel: [    9.048004] sd 3:0:0:0: [sdc] Mode Sense: 00 3a 00 00
May  9 14:39:00 ubuntu64 kernel: [    9.048004] sd 3:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
May  9 14:39:00 ubuntu64 kernel: [   12.021277] ata4.00: exception Emask 0x0 SAct 0x6 SErr 0x0 action 0x0
May  9 14:39:00 ubuntu64 kernel: [   12.021277] ata4.00: irq_stat 0x40000008
May  9 14:39:00 ubuntu64 kernel: [   12.021277] ata4.00: cmd 60/a8:10:61:00:00/00:00:00:00:00/40 tag 2 ncq 86016 in
May  9 14:39:00 ubuntu64 kernel: [   12.021277]          res 41/40:a8:ff:00:00/24:00:00:00:00/00 Emask 0x409 (media error) <F>
May  9 14:39:00 ubuntu64 kernel: [   12.021277] ata4.00: status: { DRDY ERR }
May  9 14:39:00 ubuntu64 kernel: [   12.021277] ata4.00: error: { UNC }
May  9 14:39:00 ubuntu64 kernel: [   12.024003] ata4.00: configured for UDMA/133
May  9 14:39:00 ubuntu64 kernel: [   12.024003] ata4: EH complete
May  9 14:39:00 ubuntu64 kernel: [   12.024003] sd 3:0:0:0: [sdc] 976771055 512-byte hardware sectors (500107 MB)
May  9 14:39:00 ubuntu64 kernel: [   12.024003] sd 3:0:0:0: [sdc] Write Protect is off
May  9 14:39:00 ubuntu64 kernel: [   12.024003] sd 3:0:0:0: [sdc] Mode Sense: 00 3a 00 00
May  9 14:39:00 ubuntu64 kernel: [   12.024003] sd 3:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
May  9 14:39:00 ubuntu64 kernel: [   15.001206] ata4.00: exception Emask 0x0 SAct 0x3 SErr 0x0 action 0x0
May  9 14:39:00 ubuntu64 kernel: [   15.001234] ata4.00: irq_stat 0x40000008
May  9 14:39:00 ubuntu64 kernel: [   15.001262] ata4.00: cmd 60/a8:00:61:00:00/00:00:00:00:00/40 tag 0 ncq 86016 in
May  9 14:39:00 ubuntu64 kernel: [   15.001263]          res 41/40:a8:ff:00:00/24:00:00:00:00/00 Emask 0x409 (media error) <F>
May  9 14:39:00 ubuntu64 kernel: [   15.001292] ata4.00: status: { DRDY ERR }
May  9 14:39:00 ubuntu64 kernel: [   15.001318] ata4.00: error: { UNC }
May  9 14:39:00 ubuntu64 kernel: [   15.021317] ata4.00: configured for UDMA/133
May  9 14:39:00 ubuntu64 kernel: [   15.021317] ata4: EH complete
May  9 14:39:00 ubuntu64 kernel: [   15.021317] sd 3:0:0:0: [sdc] 976771055 512-byte hardware sectors (500107 MB)
May  9 14:39:00 ubuntu64 kernel: [   15.021317] sd 3:0:0:0: [sdc] Write Protect is off
May  9 14:39:00 ubuntu64 kernel: [   15.021317] sd 3:0:0:0: [sdc] Mode Sense: 00 3a 00 00
May  9 14:39:00 ubuntu64 kernel: [   15.021317] sd 3:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
May  9 14:39:00 ubuntu64 kernel: [   17.868004] ata4.00: exception Emask 0x0 SAct 0x2 SErr 0x0 action 0x0
May  9 14:39:00 ubuntu64 kernel: [   17.868004] ata4.00: irq_stat 0x40000008
May  9 14:39:00 ubuntu64 kernel: [   17.868004] ata4.00: cmd 60/a8:08:61:00:00/00:00:00:00:00/40 tag 1 ncq 86016 in
May  9 14:39:00 ubuntu64 kernel: [   17.868004]          res 41/40:a8:ff:00:00/24:00:00:00:00/00 Emask 0x409 (media error) <F>
May  9 14:39:00 ubuntu64 kernel: [   17.868004] ata4.00: status: { DRDY ERR }
May  9 14:39:00 ubuntu64 kernel: [   17.868004] ata4.00: error: { UNC }
May  9 14:39:00 ubuntu64 kernel: [   17.868004] ata4.00: configured for UDMA/133
May  9 14:39:00 ubuntu64 kernel: [   17.868004] ata4: EH complete
May  9 14:39:00 ubuntu64 kernel: [   17.868004] sd 3:0:0:0: [sdc] 976771055 512-byte hardware sectors (500107 MB)
May  9 14:39:00 ubuntu64 kernel: [   17.868004] sd 3:0:0:0: [sdc] Write Protect is off
May  9 14:39:00 ubuntu64 kernel: [   17.868004] sd 3:0:0:0: [sdc] Mode Sense: 00 3a 00 00
May  9 14:39:00 ubuntu64 kernel: [   17.868004] sd 3:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
May  9 14:39:00 ubuntu64 kernel: [   20.556005] ata4.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
May  9 14:39:00 ubuntu64 kernel: [   20.556005] ata4.00: irq_stat 0x40000008
May  9 14:39:00 ubuntu64 kernel: [   20.556005] ata4.00: cmd 60/a8:00:61:00:00/00:00:00:00:00/40 tag 0 ncq 86016 in
May  9 14:39:00 ubuntu64 kernel: [   20.556005]          res 41/40:a8:ff:00:00/24:00:00:00:00/00 Emask 0x409 (media error) <F>
May  9 14:39:00 ubuntu64 kernel: [   20.556005] ata4.00: status: { DRDY ERR }
May  9 14:39:00 ubuntu64 kernel: [   20.556005] ata4.00: error: { UNC }
May  9 14:39:00 ubuntu64 kernel: [   20.556005] ata4.00: configured for UDMA/133
May  9 14:39:00 ubuntu64 kernel: [   20.556005] ata4: EH complete
May  9 14:39:00 ubuntu64 kernel: [   20.556005] sd 3:0:0:0: [sdc] 976771055 512-byte hardware sectors (500107 MB)
May  9 14:39:00 ubuntu64 kernel: [   20.556005] sd 3:0:0:0: [sdc] Write Protect is off
May  9 14:39:00 ubuntu64 kernel: [   20.556005] sd 3:0:0:0: [sdc] Mode Sense: 00 3a 00 00
May  9 14:39:00 ubuntu64 kernel: [   20.556005] sd 3:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
May  9 14:39:00 ubuntu64 kernel: [   23.855862] ata4.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
May  9 14:39:00 ubuntu64 kernel: [   23.855862] ata4.00: irq_stat 0x40000008
May  9 14:39:00 ubuntu64 kernel: [   23.855862] ata4.00: cmd 60/a8:00:61:00:00/00:00:00:00:00/40 tag 0 ncq 86016 in
May  9 14:39:00 ubuntu64 kernel: [   23.855862]          res 41/40:a8:ff:00:00/24:00:00:00:00/00 Emask 0x409 (media error) <F>
May  9 14:39:00 ubuntu64 kernel: [   23.855862] ata4.00: status: { DRDY ERR }
May  9 14:39:00 ubuntu64 kernel: [   23.855862] ata4.00: error: { UNC }
May  9 14:39:00 ubuntu64 kernel: [   23.872321] ata4.00: configured for UDMA/133
May  9 14:39:00 ubuntu64 kernel: [   23.872321] sd 3:0:0:0: [sdc] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
May  9 14:39:00 ubuntu64 kernel: [   23.872321] sd 3:0:0:0: [sdc] Sense Key : Medium Error [current] [descriptor]
May  9 14:39:00 ubuntu64 kernel: [   23.872321] Descriptor sense data with sense descriptors (in hex):
May  9 14:39:00 ubuntu64 kernel: [   23.872321]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
May  9 14:39:00 ubuntu64 kernel: [   23.872321]         00 00 00 ff 
May  9 14:39:00 ubuntu64 kernel: [   23.872321] sd 3:0:0:0: [sdc] Add. Sense: Unrecovered read error - auto reallocate failed
May  9 14:39:00 ubuntu64 kernel: [   23.872321] end_request: I/O error, dev sdc, sector 255
May  9 14:39:00 ubuntu64 kernel: [   23.872321] Buffer I/O error on device sdc, logical block 255
May  9 14:39:00 ubuntu64 kernel: [   23.872321] Buffer I/O error on device sdc, logical block 256
May  9 14:39:00 ubuntu64 kernel: [   23.872321] Buffer I/O error on device sdc, logical block 257
May  9 14:39:00 ubuntu64 kernel: [   23.872321] Buffer I/O error on device sdc, logical block 258
May  9 14:39:00 ubuntu64 kernel: [   23.872321] Buffer I/O error on device sdc, logical block 259
May  9 14:39:00 ubuntu64 kernel: [   23.872321] Buffer I/O error on device sdc, logical block 260
May  9 14:39:00 ubuntu64 kernel: [   23.872322] Buffer I/O error on device sdc, logical block 261
May  9 14:39:00 ubuntu64 kernel: [   23.872322] Buffer I/O error on device sdc, logical block 262
May  9 14:39:00 ubuntu64 kernel: [   23.872322] Buffer I/O error on device sdc, logical block 263
May  9 14:39:00 ubuntu64 kernel: [   23.872322] Buffer I/O error on device sdc, logical block 264
May  9 14:39:00 ubuntu64 kernel: [   23.872322] ata4: EH complete
May  9 14:39:00 ubuntu64 kernel: [   23.872322] sd 3:0:0:0: [sdc] 976771055 512-byte hardware sectors (500107 MB)
May  9 14:39:00 ubuntu64 kernel: [   23.872322] sd 3:0:0:0: [sdc] Write Protect is off
May  9 14:39:00 ubuntu64 kernel: [   23.872322] sd 3:0:0:0: [sdc] Mode Sense: 00 3a 00 00

```

---

### Post by r-senior on 2010-05-09
I'm no ATA expert, but from [https://ata.wiki.kernel.org/index.php/Libata_error_messages]("https://ata.wiki.kernel.org/index.php/Libata_error_messages"), in section "ATA Error Expansion"

> UNC = Uncorrectable error - often due to bad sectors on the disk

You could try a different cable, but I wouldn't be optimistic. I believe bad cables tend to give CRC errors.

:(

---

### Post by expatCM on 2010-05-09
Helpful link, thank you.

Reading the log together with the interpretation from the linked site it looks rather like this is a failed drive.

Perhaps best to send it back to manufacturer .....

Thanks for the help :)

---

