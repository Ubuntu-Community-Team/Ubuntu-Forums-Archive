---
title: "Copying Large files and system load climbs up"
date: 2010-07-28
forum: New to Ubuntu
---

### Post by shoaibi on 2010-07-28
I am copying around 300G files from one Portable HD to another. here are the details:

```

# uname -a
Linux blade 2.6.32-24-generic #38-Ubuntu SMP Mon Jul 5 09:20:59 UTC 2010 x86_64 GNU/Linux

```

```

# top
top - 19:57:58 up 22:00,  3 users,  load average: 6.63, 5.98, 4.60
Tasks: 230 total,   1 running, 229 sleeping,   0 stopped,   0 zombie
Cpu(s): 14.7%us,  6.5%sy,  0.7%ni, 72.7%id,  5.0%wa,  0.3%hi,  0.1%si,  0.0%st
Mem:   4020360k total,  3934192k used,    86168k free,     6920k buffers
Swap:  1028120k total,    27044k used,  1001076k free,  2015392k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                                                                            
 1252 root      20   0  227m  58m  29m S   21  1.5 136:38.64 Xorg                                                                                               
 1348 shoaibi   20   0  609m  68m  18m S   18  1.8  13:49.21 nautilus                                                                                           
 2925 shoaibi   20   0  860m  48m  14m S    5  1.2   3:25.74 chrome                                                                                             
 1341 shoaibi   20   0  373m  41m 5564 S    4  1.1  22:14.72 compiz                                                                                             
19228 shoaibi   20   0  344m  18m 9320 S    4  0.5   9:03.90 transmission                                                                                       
23595 shoaibi   20   0 19216 1376  940 R    4  0.0   0:00.04 top                                                                                                
    4 root      20   0     0    0    0 S    2  0.0   1:17.16 ksoftirqd/0                                                                                        
 1532 shoaibi   20   0  243m  11m 7644 S    2  0.3   2:05.59 netspeed_applet                                                                                    
 1663 shoaibi    9 -11  336m  15m  13m S    2  0.4  16:27.84 pulseaudio                                                                                         
 2860 shoaibi   20   0  871m 100m  28m S    2  2.6  64:05.26 chrome                                                                                             
 3125 shoaibi   20   0  715m  56m  21m S    2  1.4  53:51.75 chrome                                                                                             
21193 root      20   0     0    0    0 D    2  0.0   0:12.03 usb-storage                                                                                        
    1 root      20   0 23792 1648 1024 S    0  0.0   0:01.68 init                                                                                               
    2 root      20   0     0    0    0 S    0  0.0   0:00.01 kthreadd                                                                                           
    3 root      RT   0     0    0    0 S    0  0.0   0:00.05 migration/0                                                                                        
    5 root      RT   0     0    0    0 S    0  0.0   0:00.00 watchdog/0                                                                                         
    6 root      RT   0     0    0    0 S    0  0.0   0:00.02 migration/1                                                                                        
    7 root      20   0     0    0    0 S    0  0.0   1:15.69 ksoftirqd/1                                                                                        
    8 root      RT   0     0    0    0 S    0  0.0   0:00.00 watchdog/1                                                                                         
    9 root      20   0     0    0    0 S    0  0.0   0:55.95 events/0                                                                                           
   10 root      20   0     0    0    0 S    0  0.0   0:29.11 events/1                                                                                           
   11 root      20   0     0    0    0 S    0  0.0   0:00.00 cpuset                                                                                             
   12 root      20   0     0    0    0 S    0  0.0   0:00.12 khelper                                                                                            
   13 root      20   0     0    0    0 S    0  0.0   0:00.01 netns                                                                                              
   14 root      20   0     0    0    0 S    0  0.0   0:00.00 async/mgr                                                                                          
   15 root      20   0     0    0    0 S    0  0.0   0:00.00 pm                                                                                                 
   17 root      20   0     0    0    0 S    0  0.0   0:00.00 sync_supers                                                                                        
   18 root      20   0     0    0    0 S    0  0.0   0:00.01 bdi-default                                                                                        
   19 root      20   0     0    0    0 S    0  0.0   0:00.00 kintegrityd/0                                                                                      
   20 root      20   0     0    0    0 S    0  0.0   0:00.00 kintegrityd/1                                                                                      
   21 root      20   0     0    0    0 S    0  0.0   0:02.70 kblockd/0                                                                                          
   22 root      20   0     0    0    0 S    0  0.0   0:00.39 kblockd/1                                                                                          

```

```

# free -m
             total       used       free     shared    buffers     cached
Mem:          3926       3860         65          0          9       1980
-/+ buffers/cache:       1870       2055
Swap:         1004         26        977

```


I thought it was a problem with RAM filling out so i set:
```

# sysctl vm.swappiness=100

```

and tried copying again but no use.

---

### Post by aeiah on 2010-07-28
it might be caching things like mad because they're both on the same USB bus (its reading a chunk, saving  it to memory, writing that chunk.. rinse repeat) 


if time isnt too much of a problem, perhaps either use rsync or copy the files locally before moving them to the new drive (or do both)

rsync should happily chug along for ages. i recently rsynced 1TB of data to a usb drive. took days, mind. rsync is designed for copying over networks but i find it more reliable (albeit slower) than cp for large local copies.

---

### Post by mcduck on 2010-07-28
I don't see anything strange there. You are moving a large file, thus there's a large queue of tasks for the CPU to perform, which means higher load.

And since your portable drives are probably connected through USB that will make the load even higher, as USB isn't too fast and also requires some work from the CPU. The transfer takes even longer than from internal HD to another, so the queue for CPU becomes longer (even higher load average).

The load values aren't measures of memory use, and aren't really even directly connected to CPU use (so it sure isn't same as average CPU usage). The load is more like an over-time average of tasks waiting to be done instead of how much work the system is currently doing.

edit: Here's a decent explanation of the load values: [http://www.andymillar.co.uk/blog/2006/12/24/linux-load-average-explained/]("http://www.andymillar.co.uk/blog/2006/12/24/linux-load-average-explained/")

---

