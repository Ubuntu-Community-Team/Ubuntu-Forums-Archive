---
title: "Changing Timestamps on NAS"
date: 2007-09-01
forum: Networking &amp; Wireless
---

### Post by Krydahl on 2007-09-01
Hi,

I'm not sure this is the right forum. It seemed closer to networking than anything else.

I'm using Unison to sync drives on my desktop (Feisty 64 bit) with a NAS server (A cheap one Vantec Nexstar - it's SMB but I don't know any detail of what's running on it).

I also have an XP machine that I sync to this NAS so that all 3 machines stay in sync.

What I'm finding is that everytime Unison runs, it changes the timestamps of the files on the NAS box (it adds some number of hours, but leaves minutes and seconds unchanged). Then, when I run the utility I have on the XP machine, it thinks all the files have changed and tries to update everything.

The drive in the NAS box is FAT32. I think this must be to do with the differences in the way dates are stored in the different file systems. (FAT32 apparently stores everything in UTC and does a conversion to local time - I'm guessing that's going wrong and somehow writing the wrong time back afterward.)  I can't change away from FAT32 on the NAS, that's all it supports.

Anyone have any ideas how I can fix this? Thanks.

---

