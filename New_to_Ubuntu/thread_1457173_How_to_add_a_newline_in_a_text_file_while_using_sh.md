---
title: "How to add a newline in a text file while using shell script"
date: 2010-04-18
forum: New to Ubuntu
---

### Post by siteregsam on 2010-04-18
hi,

 I had written a script to add time, cpu usage and memory status to a text file as
[B]
#!/bin/bash
gedit temp.txt
date > temp.txt
cat /proc/stat >> temp.txt
cat /proc/meminfo >> temp.txt[/B]

The output looks like 

[I]Sun Apr 18 17:56:44 IST 2010
cpu  73484 7424 27314 995026 15060 1680 1984 0 0
cpu0 30206 3199 10744 503870 1895 318 1699 0 0
cpu1 43277 4225 16570 491156 13164 1361 284 0 0
intr 2617297 673000 2559 0 0 0 0 0 1 0 15144 0 0 985 0 73035 0 448611 97550 0 315347 0 2425 67183 1 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0
ctxt 3413955
btime 1271588083
processes 2863
procs_running 5
procs_blocked 0
softirq 992344 0 630113 9789 9357 74281 44779 103184 698 120143
MemTotal:         766296 kB
MemFree:           23612 kB
Buffers:           88624 kB
Cached:           335932 kB
SwapCached:          560 kB
Active:           322948 kB
Inactive:         326472 kB
Active(anon):      91872 kB
Inactive(anon):   137572 kB
Active(file):     231076 kB
Inactive(file):   188900 kB
Unevictable:           0 kB
Mlocked:               0 kB
HighTotal:             0 kB
HighFree:              0 kB
LowTotal:         766296 kB
LowFree:           23612 kB
SwapTotal:       1052216 kB
SwapFree:        1049828 kB
Dirty:               152 kB
Writeback:             0 kB
AnonPages:        224480 kB
Mapped:            86636 kB
Slab:              42152 kB
SReclaimable:      33000 kB
SUnreclaim:         9152 kB
PageTables:         6168 kB
NFS_Unstable:          0 kB
Bounce:                0 kB
WritebackTmp:          0 kB
CommitLimit:     1435364 kB
Committed_AS:     840572 kB
VmallocTotal:     247224 kB
VmallocUsed:       37248 kB
VmallocChunk:     206076 kB
HugePages_Total:       0
HugePages_Free:        0
HugePages_Rsvd:        0
HugePages_Surp:        0
Hugepagesize:       4096 kB
DirectMap4k:       10816 kB
DirectMap4M:      774144 kB[/I]

I need to insert a newline(empty line '\n') to  separate time, cpu usage info and memory info. How can to do this? 

Thanks in advance....

---

### Post by Penguin Guy on 2010-04-18
Echo automatically adds a newline after the text you enter, so you can simply use: [FONT="Courier New"][S]echo ''[/S][/FONT]
> **Paddy Landau said:**
> You don't even need the quotes. Just use echo on its own:
```
echo >>temp.txt
```

---

### Post by Paddy Landau on 2010-04-18
You don't even need the quotes. Just use echo on its own:
```
echo >>temp.txt
```

---

