---
title: "[SOLVED] Bios Detects RAM, Kubuntu doesn't"
date: 2008-12-13
forum: New to Ubuntu
---

### Post by theharshone on 2008-12-13
Hello
previously, I had one 1 GB stick of RAM. Today installed 1.5 GB more RAM (1 one GB stick and one 512 MB stick). Bios shows everything is ok and says there is 2560 MB of ram and correctly displays where all the ram is. Kubuntu only detects the 1 GB I had earlier. 

here is output from free:
```

            total       used       free     shared    buffers     cached
Mem:       1025068     982812      42256          0      25316     366168
-/+ buffers/cache:     591328     433740
Swap:      2834656        400    2834256

```

here is my /proc/meminfo
```

MemTotal:      1025068 kB
MemFree:         41692 kB
Buffers:         25364 kB
Cached:         366232 kB
SwapCached:        400 kB
Active:         627292 kB
Inactive:       236608 kB
SwapTotal:     2834656 kB
SwapFree:      2834256 kB
Dirty:              48 kB
Writeback:           0 kB
AnonPages:      472020 kB
Mapped:         136736 kB
Slab:            54852 kB
SReclaimable:    28232 kB
SUnreclaim:      26620 kB
PageTables:      20304 kB
NFS_Unstable:        0 kB
Bounce:              0 kB
WritebackTmp:        0 kB
CommitLimit:   3347188 kB
Committed_AS:   842436 kB
VmallocTotal: 34359738367 kB
VmallocUsed:    109160 kB
VmallocChunk: 34359628283 kB
HugePages_Total:     0
HugePages_Free:      0
HugePages_Rsvd:      0
HugePages_Surp:      0
Hugepagesize:     2048 kB
DirectMap4k:     49088 kB
DirectMap2M:    999424 kB

```

shouldn't Kubuntu be reading the information from the BIOS?
how can I get all my ram detected?
Is there anything else I should post?

Thanks

---

### Post by taurus on 2008-12-13
At the GRUB menu, pick memtest (last option on the menu) and have it test your RAM.  It could take a while to run the test though.

---

### Post by theharshone on 2008-12-13
It only detects 1 GB of ram as well. Shouldn't everything agree with the BIOS?

---

### Post by Hospadar on 2008-12-13
is this a desktop with a bunch of slots?
Often there is a certain order you need to put the memory in.
it seems unlikely but possible

---

### Post by theharshone on 2008-12-13
Yes this is a desktop with four slots.

---

### Post by taurus on 2008-12-13
Are they dual-channel?

---

### Post by theharshone on 2008-12-13
I dont know, does it matter?

---

### Post by theharshone on 2008-12-14
I'll try putting them in in a different order. I really cannot think of anything else to do. Maybe its because one of the slots blew out and only 3 slots work? I'll try to put the simlar ones next to  each other. Please, any other ideas are appreciated. Thanks

---

### Post by scorp123 on 2008-12-14
> **theharshone said:**
> I dont know, does it matter? If they are dual channel, then yes. Slots have to be occupied by identical pairs. Slots 1+3 = Pair 1, slots 2+4 = Pair 2.

Are the slots colored differently? e.g. Slots 1+3 are green or blue, slots 2+4 are black or white?

---

### Post by theharshone on 2008-12-17
Yes, they are colored differently, but one slot is burned out. I think I just had one bad stick of ram. If I take it out Linux reads 1.5 GB (the correct value) but if I put it in, it reads 1 GB. I just settled for taking it out. Thanks for all the replies.

---

