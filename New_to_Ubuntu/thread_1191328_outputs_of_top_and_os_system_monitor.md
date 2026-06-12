---
title: "outputs of top and os system monitor"
date: 2009-06-18
forum: New to Ubuntu
---

### Post by flylehe on 2009-06-18
Hi, 
Here is what System Monitor says:
> 
Memory
471.0 MiB (49.8%) of 944.9 Mib
Swap
269.1 MiB (27.4%) of 949.1 MiB 

and here is the output of top:
> 
Mem: 967588k total, 788012k used, 179576k free, 11320k buffers
Swap: 971892k total, 266308k used, 705584k free, 303604k cached


For swap, "266308k used" is close to "269.1 MiB", but for memory, "788012k used" != "471.0 MiB". I wonder how the two numbers for memory are related? 

Is "11320k buffers" part of "Mem: 967588k total" and "303604k cached" part of "Swap: 971892k total"? Then why "967588k total" = "788012k used" + "179576k free" and "971892k total" = "266308k used" + "705584k free"?

Thanks and regards!

---

### Post by SOULRiDER on 2009-06-18
Use the free command. The difference in the output of those commands is that one may be showing buffers while the other one is not.

---

### Post by nandemonai on 2009-06-18
Linux pre-caches your RAM. That's all. It may claim a certain amount but not necessarily be using that much.

On a 4GB RAM system I'm currently only using 780MB but 2GB is cached for use.

---

### Post by SOULRiDER on 2009-06-18
Htop shows a nice little bar with how much RAM is actually in use for programs and how much is used for buffers, check it out.

---

### Post by nandemonai on 2009-06-18
Gotta <3 htop :P

---

### Post by flylehe on 2009-06-19
Thanks!
I wonder what is the difference between buffer and cache? Are they parts of RAM or CPU?

---

