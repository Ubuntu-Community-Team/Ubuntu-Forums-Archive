---
title: "Should I kill Java?"
date: 2010-06-02
forum: New to Ubuntu
---

### Post by Legendary_Bibo on 2010-06-02
My bootup was slower than normal, and things are running slow as hell. So I looked at top and it turns out Java is sucking up 1.8gb out of 4gb of my ram, which is leaving me with like 35mb or RAM. I don't think Java usually runs, but I tried installing it to get a coupon off of taco bell's website, and now it's been running. I don't know if it's important or not really. I know unused memory is wasted memory, but considering it's slowing things down, it might not hurt to give other programs more leg room, I just don't know if it'll cause a problem.

```
top - 12:39:17 up  5:05,  2 users,  load average: 0.60, 1.08, 0.92
Tasks: 174 total,   1 running, 172 sleeping,   0 stopped,   1 zombie
Cpu(s): 13.8%us,  2.9%sy,  0.3%ni, 79.7%id,  1.0%wa,  0.6%hi,  1.6%si,  0.0
Mem:   3798408k total,  3750052k used,    48356k free,    39992k buffers
Swap: 11126776k total,    32784k used, 11093992k free,  1468808k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND       
 1923 bibo      20   0 1749m 204m  10m S   16  5.5  42:10.27 java          
 1043 root      20   0  371m 193m  20m S   12  5.2  74:08.36 Xorg          
 4001 bibo      20   0  921m 110m  24m S    3  3.0  27:55.52 firefox-bin   
 1425 bibo      20   0  301m  66m 4640 S    1  1.8   2:52.45 compiz        
 1803 bibo      30  10 99.0m  15m 2148 S    1  0.4   1:22.07 desktopcouch-s
  868 root      20   0 76576 1956 1668 S    1  0.1   0:07.96 gdm-binary    
 1599 bibo      20   0  287m  19m 6744 S    1  0.5   0:19.09 python        
 6709 bibo      20   0  215m  15m  10m S    1  0.4   0:00.29 gnome-terminal
  310 root      20   0     0    0    0 S    0  0.0   0:02.73 jbd2/sda1-8   
 1681 bibo      20   0 98544  14m 2640 S    0  0.4   1:10.84 desktopcouch-s
 6442 bibo      20   0  596m  99m  31m S    0  2.7   0:52.92 software-cente
 6728 bibo      20   0 19216 1416 1032 R    0  0.0   0:00.08 top           
    1 root      20   0 23692 1424  888 S    0  0.0   0:00.60 init          
    2 root      20   0     0    0    0 S    0  0.0   0:00.00 kthreadd      
    3 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/0   
    4 root      20   0     0    0    0 S    0  0.0   0:03.86 ksoftirqd/0   
    5 root      RT   0     0    0    0 S    0  0.0   0:00.00 watchdog/0  
```

---

### Post by RiceMonster on 2010-06-02
Java isn't used for anything crucial to the system, so you should be able to kill it without problems. If it does cause problems, just reboot. Try "killall java" or "kill 1923".

---

### Post by Legendary_Bibo on 2010-06-02
Ohhh...it was Vuze.

---

### Post by philinux on 2010-06-02
> **Legendary_Bibo said:**
> Ohhh...it was Vuze.

Bug reportin time then ;)

---

### Post by Legendary_Bibo on 2010-06-02
> **philinux said:**
> Bug reportin time then ;)
that it has a memory leak or that it's not named correctly?

---

### Post by gsocker on 2010-06-02
Actually, Java is only using 204MB of physical RAM. The "Virt" column is the total "virtual" size of the memory in use: it includes shared libraries(only one copy actually exists in RAM and is shared between all processes that use it), pages swapped to disk, shared memory, and files mapped into the address space so they appear to the program to be loaded into memory(probably the biggest contributer in this case). 

For example, if you are downloading a 1.5GB torrent, and Vuze is using the mmap() function to treat the file as if started at memory address 0 and ended at memory address 1,500,000,000 , the "Virt" column will be 1.5GB + RES(resident in RAM) + SHR(mapped shared libraries). If you have a 64 bit system, this value could theoretically top out somewhere around 256TiB.

This technique can make programming easier, as well as being faster in many cases, since the data is copied fewer times.

---

### Post by gsocker on 2010-06-02
Also, you actually have more than 35MB available.
"Top interpretation" can be tricky.  
> 
```

Mem:   3798408k total,  3750052k used,    48356k free,    39992k buffers
Swap: 11126776k total,    32784k used, 11093992k free,  **1468808k cached**

```


The "cached" column is the amount of memory being used by the kernel to hold files that have been recently read; if the are accessed again they are already in memory. It's normal for the "free" column to be low, as the kernel will suck up most of the ram for the cache. The kernel will discard the cache as needed, if it needs more memory. In your case, this accounts for about 1.4GB. 

My system is currently using 2.3GB for cache, and has approx 1.7GB "free" ram out of 5GB.
This is normal behavior for a Linux system.

---

