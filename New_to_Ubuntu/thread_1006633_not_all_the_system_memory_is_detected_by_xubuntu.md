---
title: "not all the system memory is detected by xubuntu"
date: 2008-12-09
forum: New to Ubuntu
---

### Post by joonga on 2008-12-09
Greetings.

Recent install of xubuntu 8.10 on my my old x86 intel. The bios indicates a total of 640mb of memory (128 + 256 + 256). However, only 128 mb is detected and recognized by the OS. I'm scouring the docs to find instructions on how to add the remaining 512mb of ram. Any pointers or documentation links would be appreciated.

Many thanks, and all the best.
Joonga.

---

### Post by lykwydchykyn on 2008-12-09
How are you determining what amount is detected by the OS?  can you post the output of this command:
```

cat /proc/meminfo

```

---

### Post by Tatty on 2008-12-09
Im not a hardware expert, but try pulling out the 128Mb stick.  I know some motherboards get upset if you use different sized sticks.

Are these the same types of RAM incidentally?  ie, you arent mixing DDR, DDR2 etc are you?

---

### Post by LowSky on 2008-12-09
also check and see if your BIOS reconizes the RAM.

---

### Post by joonga on 2008-12-09
Tatty: those are good questions that I'll have to verify and look into. As for the previous poster's suggestion, here is the result of the cmd:
__________________________________
pierre@valis:~$ cat /proc/meminfo
MemTotal:       192772 kB
MemFree:          5808 kB
Buffers:          2536 kB
Cached:          52424 kB
SwapCached:      23044 kB
Active:         132096 kB
Inactive:        27292 kB
HighTotal:           0 kB
HighFree:            0 kB
LowTotal:       192772 kB
LowFree:          5808 kB
SwapTotal:      240932 kB
SwapFree:        85372 kB
Dirty:              12 kB
Writeback:           0 kB
AnonPages:       85900 kB
Mapped:          31216 kB
Slab:            11400 kB
SReclaimable:     3424 kB
SUnreclaim:       7976 kB
PageTables:       1912 kB
NFS_Unstable:        0 kB
Bounce:              0 kB
WritebackTmp:        0 kB
CommitLimit:    337316 kB
Committed_AS:   416228 kB
VmallocTotal:   823288 kB
VmallocUsed:     24412 kB
VmallocChunk:   795124 kB
HugePages_Total:     0
HugePages_Free:      0
HugePages_Rsvd:      0
HugePages_Surp:      0
Hugepagesize:     4096 kB
DirectMap4k:    199680 kB
DirectMap4M:         0 kB

_________________

Many thanks to both of you.
J.

---

### Post by cardinals_fan on 2008-12-10
@joonga: A quick tip: surround your terminal output with ```
 and 
``` tags, or just highlight it and click the # sign in the upper-right side of the post box.

As for your problem, try removing the 128 MB stick.  512 MB is probably enough if you use reasonably lightweight apps (if you need a list of some choices, just let me know).

---

### Post by joonga on 2008-12-10
Okay Cardinals_fan, it worked. This one is solved. xubuneez now acknowledges the remaining 512 mb of ram after removing the lone 128 megger. I guess you were all correct. Needless to say that I'm having a better time now puttering around.  

Cheers to all, and best.
Joonga

---

