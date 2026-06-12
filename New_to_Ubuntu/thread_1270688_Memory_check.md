---
title: "Memory check"
date: 2009-09-19
forum: New to Ubuntu
---

### Post by Georgia boy on 2009-09-19
Hi. I was in the How to Geek site and there was something about checking memory in Ubuntu. So I copy and pasted the command and came up with this.

MemTotal:      2074556 kB
MemFree:       1293556 kB
Buffers:         28108 kB
Cached:         405956 kB
SwapCached:          0 kB
Active:         435916 kB
Inactive:       295272 kB
HighTotal:     1178492 kB
HighFree:       458816 kB
LowTotal:       896064 kB
LowFree:        834740 kB
SwapTotal:     4682908 kB
SwapFree:      4682908 kB
Dirty:             184 kB
Writeback:           0 kB
AnonPages:      297284 kB
Mapped:          70928 kB
Slab:            20780 kB
SReclaimable:    11876 kB
SUnreclaim:       8904 kB
PageTables:       1988 kB
NFS_Unstable:        0 kB
Bounce:              0 kB
CommitLimit:   5720184 kB
Committed_AS:   827376 kB
VmallocTotal:   114680 kB
VmallocUsed:     52344 kB
VmallocChunk:    57840 kB


This look okay or not? By the way what the heck is "diry"?
Thanks
Tom

---

### Post by 3rdalbum on 2009-09-19
If you want to check your memory, use Memtest86 from the GRUB boot menu. Run it overnight. It's a comprehensive memory test, and if it shows errors or it freezes up during the night, then your memory is bad.

---

