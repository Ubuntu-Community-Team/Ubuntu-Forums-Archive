---
title: "wifi connection makes 1 CPU run at 100%"
date: 2008-01-25
forum: Networking &amp; Wireless
---

### Post by philphil on 2008-01-25
Hi,

When I am connected to the internet via a wifi connection one of my CPU usages shoots up to 100%.  Before it connects both CPUs are at about 3 or 4 % each and then I turn it on, wait a few seconds for it to connect, it connects and BOOM one CPU is running at 100%.  This obviously effects my performance.  Both at school *and* with the ladies, i just don't know what to do with myself.  Please can you help me?

I ran dmesg output because I've seen other people do that when they report a bug, I'm not sure what it's supposed to do though, can you someone explain that to me as well?

dmesg output:

```
[129604.116000] ata1.01: qc timeout (cmd 0xa0)
[129604.116000] ata1.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[129604.116000] ata1.01: cmd a0/00:00:00:00:20/00:00:00:00:00/b0 tag 0 cdb 0x0 data 0 
[129604.116000]          res 51/20:03:00:00:00/00:00:00:00:00/b0 Emask 0x5 (timeout)
[129609.156000] ata1: port is slow to respond, please be patient (Status 0xd1)
[129614.140000] ata1: device not ready (errno=-16), forcing hardreset
[129614.140000] ata1: soft resetting port
[129614.508000] ata1.00: configured for UDMA/100
[129614.696000] ata1.01: configured for UDMA/25
[129614.696000] ata1: EH complete
[129614.712000] sd 0:0:0:0: [sda] 234441648 512-byte hardware sectors (120034 MB)
[129614.724000] sd 0:0:0:0: [sda] Write Protect is off
[129614.724000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[129614.748000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[129614.768000] VFS: busy inodes on changed media.
[129614.768000] sd 0:0:0:0: [sda] 234441648 512-byte hardware sectors (120034 MB)
[129614.780000] sd 0:0:0:0: [sda] Write Protect is off
[129614.780000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[129614.804000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[129614.828000] VFS: busy inodes on changed media.
[129615.052000] VFS: busy inodes on changed media.
```

You should not that had I copied the last 30 lines of the dmesg output they would all have read "VFS:busy inodes on changed media"  I had to scroll up a lot to get anything useful...

Hope you can help me!

Phil

---

