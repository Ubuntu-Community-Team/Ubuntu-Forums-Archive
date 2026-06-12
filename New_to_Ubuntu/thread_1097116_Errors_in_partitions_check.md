---
title: "Errors in partitions check"
date: 2009-03-15
forum: New to Ubuntu
---

### Post by slamdunk on 2009-03-15
Hi,

during periodic check disc at boot I get always a slow checking cos many errors (mostly at begin of stage 1/5) are displayed.
That's a sample of error:

Mar 15 19:09:26 mybox kernel: [  210.614841] ata3: EH complete
Mar 15 19:09:26 mybox kernel: [  210.614890] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Mar 15 19:09:26 mybox kernel: [  214.223696] ata3.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Mar 15 19:09:26 mybox kernel: [  214.223782] ata3.00: irq_stat 0x40000001
Mar 15 19:09:26 mybox kernel: [  214.223865] ata3.00: cmd c8/00:00:0f:11:68/00:00:00:00:00/e0 tag 0 dma 131072 in
Mar 15 19:09:26 mybox kernel: [  214.223867]          res 51/40:86:89:11:68/00:00:00:00:00/e0 Emask 0x9 (media error)
Mar 15 19:09:26 mybox kernel: [  214.224056] ata3.00: status: { DRDY ERR }
Mar 15 19:09:26 mybox kernel: [  214.224129] ata3.00: error: { UNC }
Mar 15 19:09:26 mybox kernel: [  214.226061] ata3.00: configured for UDMA/100
Mar 15 19:09:26 mybox kernel: [  214.226090] sd 2:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
Mar 15 19:09:26 mybox kernel: [  214.226097] sd 2:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
Mar 15 19:09:26 mybox kernel: [  214.226111] Descriptor sense data with sense descriptors (in hex):
Mar 15 19:09:26 mybox kernel: [  214.226113]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
Mar 15 19:09:26 mybox kernel: [  214.226123]         00 68 11 89 
Mar 15 19:09:26 mybox kernel: [  214.226127] sd 2:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
Mar 15 19:09:26 mybox kernel: [  214.226132] end_request: I/O error, dev sda, sector 6820233
Mar 15 19:09:26 mybox kernel: [  214.226209] __ratelimit: 20 callbacks suppressed
Mar 15 19:09:26 mybox kernel: [  214.226211] Buffer I/O error on device sda1, logical block 852521
Mar 15 19:09:26 mybox kernel: [  214.226288] Buffer I/O error on device sda1, logical block 852522
Mar 15 19:09:26 mybox kernel: [  214.226364] Buffer I/O error on device sda1, logical block 852523
Mar 15 19:09:26 mybox kernel: [  214.226441] Buffer I/O error on device sda1, logical block 852524
Mar 15 19:09:26 mybox kernel: [  214.226519] Buffer I/O error on device sda1, logical block 852525
Mar 15 19:09:26 mybox kernel: [  214.226596] Buffer I/O error on device sda1, logical block 852526
Mar 15 19:09:26 mybox kernel: [  214.226673] Buffer I/O error on device sda1, logical block 852527
Mar 15 19:09:26 mybox kernel: [  214.226751] Buffer I/O error on device sda1, logical block 852528
Mar 15 19:09:26 mybox kernel: [  214.226828] Buffer I/O error on device sda1, logical block 852529
Mar 15 19:09:26 mybox kernel: [  214.226904] Buffer I/O error on device sda1, logical block 852530

I'm using Ubuntu 8.10 on Dell XPS M1330, and all Hard disk is occupied by Ubuntu with default install.
Have you any idea about errors above and how to fix them?

Thanks,
Julio

---

