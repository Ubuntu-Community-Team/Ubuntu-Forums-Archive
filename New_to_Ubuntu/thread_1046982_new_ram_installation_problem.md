---
title: "new ram installation problem"
date: 2009-01-21
forum: New to Ubuntu
---

### Post by Vicfred on 2009-01-21
*I don't know if it's the right place to post this, if not please move it.*

I Have an a8n sli premium motherboard, I recently bought 3 sticks of 512MB ram I installed them but my computer keeps showing just 512MB, I had one stick of 512MB dual channel memory, I think the new ones are one channel, both are kingston, it's normal? :(

---

### Post by linux_tech on 2009-01-21
what is output of
```
cat /proc/meminfo
```

---

### Post by LowSky on 2009-01-22
make sure the sticks show up in BIOS. Its not really an Linx issue if they wont even post in BIOS. Make sure you have the right speed for your motherboard.

Also Asus can be picky about RAM, check out ASus website for RAM manufacturers that are suggested.. maybe a BIOS update as well

[http://www.asus.com/products.aspx?modelmenu=2&model=375&l1=3&l2=15&l3=148&l4=0](http://www.asus.com/products.aspx?modelmenu=2&model=375&l1=3&l2=15&l3=148&l4=0)

---

### Post by Vicfred on 2009-01-22
> **linux_tech said:**
> what is output of
```
cat /proc/meminfo
```

```
MemTotal:       514236 kB
MemFree:          7444 kB
Buffers:          6416 kB
Cached:          96352 kB
SwapCached:       3104 kB
Active:         346540 kB
Inactive:       110020 kB
HighTotal:           0 kB
HighFree:            0 kB
LowTotal:       514236 kB
LowFree:          7444 kB
SwapTotal:      955828 kB
SwapFree:       924656 kB
Dirty:             512 kB
Writeback:           0 kB
AnonPages:      351052 kB
Mapped:          60692 kB
Slab:            22784 kB
SReclaimable:     8124 kB
SUnreclaim:      14660 kB
PageTables:       3116 kB
NFS_Unstable:        0 kB
Bounce:              0 kB
WritebackTmp:        0 kB
CommitLimit:   1212944 kB
Committed_AS:  1092448 kB
VmallocTotal:   503800 kB
VmallocUsed:     45364 kB
VmallocChunk:   452596 kB
HugePages_Total:     0
HugePages_Free:      0
HugePages_Rsvd:      0
HugePages_Surp:      0
Hugepagesize:     4096 kB
DirectMap4k:     40896 kB
DirectMap4M:    483328 kB
```

@LowSky
The bios shows:

Installed ram: 2048
Usable ram: 512

what does that mean? I'll update my bios, thanks.

---

### Post by linux_tech on 2009-01-22
check bios settings for memory and make sure they are correct.   Usually there are 2 different color dim slots; check your mother board manual to see if they require the single channel matched pair to be in certain slots. Memory requirements vary depending on board. you can also test memory by using memtest86 at boot to see if there are any errors.

---

### Post by Muffinabus on 2009-01-22
Hmm, could it be a compatibility issue between the old ram and the new ram?  I'd try taking out the old 512 stick and leaving the 3 new ones in and see if you can at least get 1.5 gigs out of it.

---

### Post by blackmail on 2009-01-22
I also don't think that it is a linux issue, try to make combinations if you don't have exact specifications on how to install the ram that you have, and also it may also be a compatibility isue, have you tried starting the machine with only one dimm at a time and switching between them to se if it recognizes the other two?

---

