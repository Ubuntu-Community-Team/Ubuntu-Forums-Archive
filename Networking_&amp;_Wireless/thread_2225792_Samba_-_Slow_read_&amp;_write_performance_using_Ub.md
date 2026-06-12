---
title: "Samba - Slow read &amp; write performance using Ubuntu, Windows is ok"
date: 2014-05-23
forum: Networking &amp; Wireless
---

### Post by Martin_Knig on 2014-05-23
Hey guys, I have a problem with my server.
But first the facts:

**My laptop**: Acer Aspire 5741G, Ubuntu 13.10 x64 & Windows 8 x64 Dualboot, SSD + HDD, Gigabit LAN
**My server**: HP Pavillon dv9000 mainboard, Ubuntu 13.10 x86, 40GB 2,5" SATA + 2TB WD Green 3,5", Gigabit LAN
**Switch + LAN**: 5 port Netgear Gigabit Switch + high quality CAT6 Patch cables

So I have my laptop running Ubuntu & Windows and my server running Ubuntu. I've installed Samba on my server. The 2TB drive in the server has 2 partitions, one great EXT4 and one small NTFS partition.
When I boot up **Windows 8** on my laptop and try to copy files from my laptop to the server (on the EXT4 partition), I get about 110 MB/s...that's nice!
But when I boot up **Ubuntu** on my laptop and try to copy a large file (~990 MB) on the same EXT4 partition into the same folder, I get only 45 MB/s MAX!
And also the same when copying files from the server onto my laptop running Ubuntu...max 46 MB/s...and that's pretty poor...

Can someone help me please? Thanks in advance :KS

---

