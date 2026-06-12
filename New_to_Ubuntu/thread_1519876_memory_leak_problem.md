---
title: "memory leak problem"
date: 2010-06-28
forum: New to Ubuntu
---

### Post by zetharx on 2010-06-28
I have a system about 3 months old on which I am running some specific services to fill the needs of my department.  A few days ago, after using it, the desktop slowed to a crawl.  I rebooted and watched as the system memory trickled byte by byte until all the memory was used and I couldn't even move the mouse or ssh into the system.

The trick is that the list of top memory-usage processes starts with copiz with like 2% mem usage.  Whatever process is leaking, it doesn't even know that it is leaking, heh.  So I can just format and start anew, or with the community's help (hopefully), I can trace the source of this leak.

Any ideas???

Thanks in advance.

---

### Post by zetharx on 2010-06-28
Here is `free -mt` and `cat /proc/meminfo` after about 4 minutes past bootup.


```
george@george-server:~$ free -mt
             total       used       free     shared    buffers     cached
Mem:          2009        990       1019          0         62        301
-/+ buffers/cache:        626       1383
Swap:         5884          0       5884
Total:        7894        990       6904

george@george-server:~$ cat /proc/meminfo 
MemTotal:        2057460 kB
MemFree:         1040084 kB
Buffers:           64280 kB
Cached:           308556 kB
SwapCached:            0 kB
Active:           386656 kB
Inactive:         286120 kB
Active(anon):     307472 kB
Inactive(anon):       16 kB
Active(file):      79184 kB
Inactive(file):   286104 kB
Unevictable:           0 kB
Mlocked:               0 kB
SwapTotal:       6026232 kB
SwapFree:        6026232 kB
Dirty:               420 kB
Writeback:             0 kB
AnonPages:        299956 kB
Mapped:           111404 kB
Shmem:              7552 kB
Slab:             124128 kB
SReclaimable:      34612 kB
SUnreclaim:        89516 kB
KernelStack:        2552 kB
PageTables:        23572 kB
NFS_Unstable:          0 kB
Bounce:                0 kB
WritebackTmp:          0 kB
CommitLimit:     7054960 kB
Committed_AS:    1157076 kB
VmallocTotal:   34359738367 kB
VmallocUsed:      422820 kB
VmallocChunk:   34359308284 kB
HardwareCorrupted:     0 kB
HugePages_Total:       0
HugePages_Free:        0
HugePages_Rsvd:        0
HugePages_Surp:        0
Hugepagesize:       2048 kB
DirectMap4k:       38528 kB
DirectMap2M:     2058240 kB

```

---

### Post by ubunterooster on 2010-06-28
It looks like you (in above post) have a good amount of RAM left and  SWAP has not been touched. Is it possible to show the above when it is  slowed down?

---

### Post by zetharx on 2010-06-28
This is 12min uptime.  Creeping along... and I can send later, but once it is abuot 97% mem full, I can't do anything.

```
george@george-server:~$ free -mt
             total       used       free     shared    buffers     cached
Mem:          2009       1321        687          0         63        305
-/+ buffers/cache:        951       1057
Swap:         5884          0       5884
Total:        7894       1321       6572

george@george-server:~$ cat /proc/meminfo 
MemTotal:        2057460 kB
MemFree:          705716 kB
Buffers:           65000 kB
Cached:           310796 kB
SwapCached:            0 kB
Active:           386680 kB
Inactive:         287384 kB
Active(anon):     305852 kB
Inactive(anon):       16 kB
Active(file):      80828 kB
Inactive(file):   287368 kB
Unevictable:           0 kB
Mlocked:               0 kB
SwapTotal:       6026232 kB
SwapFree:        6026232 kB
Dirty:               236 kB
Writeback:             0 kB
AnonPages:        298264 kB
Mapped:           111004 kB
Shmem:              7604 kB
Slab:             272916 kB
SReclaimable:      51488 kB
SUnreclaim:       221428 kB
KernelStack:        2376 kB
PageTables:        23468 kB
NFS_Unstable:          0 kB
Bounce:                0 kB
WritebackTmp:          0 kB
CommitLimit:     7054960 kB
Committed_AS:    1162132 kB
VmallocTotal:   34359738367 kB
VmallocUsed:      607140 kB
VmallocChunk:   34359123964 kB
HardwareCorrupted:     0 kB
HugePages_Total:       0
HugePages_Free:        0
HugePages_Rsvd:        0
HugePages_Surp:        0
Hugepagesize:       2048 kB
DirectMap4k:       38528 kB
DirectMap2M:     2058240 kB

```

---

### Post by ubunterooster on 2010-06-28
could you post your ```
top
```

---

### Post by TechBeastie on 2010-06-28
You've probably thought of this, but just in case: are you sure that you're sorting the top entires by memory usage?  By default, top sorts by CPU usage, and it's possible that whatever's causing your problem isn't a particularly clock cycle-heavy process.

---

### Post by zetharx on 2010-06-28
yea good thought, but I have conky up showing me top by cpu AND top by mem.  my screen is now locked up at 35min uptime saying that lol... google-chrome is the top memory user at 0.43%...... i have ubuntuforums open in chrome and nothing other running except my inits.  Something is in my init and it is causing this problem.

I have considered the things I installed on the day it started acting this way, and I have tried to reverse it all, but to no avail... still chewing through memory and I can't trace it.


EDIT:
it will fill up memory even if i do not login.  i leave it at login screen for 10 min and then log in; first thing i see in mem usage is 800MB used.  also it may interest some that once it fills up memory, it does not move in to fill swap... it just sits there with the screen updating once every 5-10 min.
worst. FPS. ever.
heh

EDIT 2:
Sorry rooster, missed your request for `top`.  I'll reboot and post that after it has run for 20 or so min.

---

### Post by zetharx on 2010-06-28
```
top - 20:23:23 up 20 min,  2 users,  load average: 2.29, 2.38, 1.81
Tasks: 160 total,   1 running, 159 sleeping,   0 stopped,   0 zombie
Cpu(s):  5.2%us,  9.4%sy,  0.0%ni, 85.4%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   2057460k total,  1791992k used,   265468k free,   107552k buffers
Swap:  6026232k total,        0k used,  6026232k free,   336452k cached

  PID USER    PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 1815 george  20   0  276m  49m  20m S    2  2.5   0:07.24 compiz             
 1098 root    20   0  133m  43m  21m S    0  2.2   0:17.35 Xorg               
 1825 george  20   0  359m  40m  19m S    0  2.0   0:01.99 gnome-do           
  856 mysql   20   0  174m  24m 6660 S    0  1.2   0:00.75 mysqld             
 1798 george  20   0  489m  22m  16m S    0  1.1   0:00.69 nautilus           
13131 george  20   0  325m  20m  13m S    0  1.0   0:02.11 gedit              
 2310 george  20   0  225m  20m 9.8m S    0  1.0   0:00.16 python             
 1889 george  20   0  301m  15m  11m S    0  0.8   0:00.15 clock-applet       
 4752 george  20   0  214m  14m  10m S    0  0.7   0:04.05 gnome-terminal     
 1886 george  20   0  253m  14m  10m S    0  0.7   0:00.35 wnck-applet        
 1796 george  20   0  250m  14m  10m S    0  0.7   0:00.18 gnome-panel        
 2312 george  20   0  414m  13m  10m S    0  0.7   0:00.09 evolution-alarm    
 2335 george  20   0  347m  13m  10m S    0  0.7   0:00.07 evolution-excha    
 2929 george  20   0  202m  13m 9812 S    0  0.7   0:00.16 update-notifier    
 1808 george  20   0  233m  13m 9500 S    0  0.6   0:00.12 nm-applet          
 1887 george  20   0  237m  12m 9164 S    0  0.6   0:00.11 trashapplet        
 1894 george  20   0  174m  11m 8320 S    0  0.6   0:00.50 gtk-window-deco  
```

---

### Post by zetharx on 2010-06-28
and for complete redundancy of information... this one at about 88% mem full and 29min uptime

```
george@george-server:~$ top

top - 20:31:59 up 29 min,  2 users,  load average: 2.92, 2.77, 2.24
Tasks: 166 total,   2 running, 164 sleeping,   0 stopped,   0 zombie
Cpu(s):  7.9%us,  5.7%sy,  0.0%ni, 85.0%id,  0.7%wa,  0.0%hi,  0.7%si,  0.0%st
Mem:   2057460k total,  1990424k used,    67036k free,    42888k buffers
Swap:  6026232k total,     4988k used,  6021244k free,   150800k cached

  PID USER    PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 1815 george  20   0  276m  50m  20m S    4  2.5   0:21.52 compiz             
 1098 root    20   0  134m  44m  21m S    4  2.2   0:34.24 Xorg               
 1825 george  20   0  359m  40m  19m S    0  2.0   0:02.33 gnome-do           
26359 george  20   0  855m  39m  13m S    0  1.9   0:03.68 chrome             
26230 george  20   0  414m  36m  21m S    4  1.8   0:25.24 chrome             
  856 mysql   20   0  174m  24m 6720 S    0  1.2   0:00.98 mysqld             
 1798 george  20   0  489m  22m  16m S    0  1.1   0:00.72 nautilus           
13131 george  20   0  326m  21m  14m S    0  1.1   0:04.58 gedit              
 2310 george  20   0  225m  20m 9.8m S    0  1.0   0:00.16 python             
26365 george  25   5  781m  19m  11m S    0  1.0   0:00.37 chrome             
26377 george  25   5  843m  16m 9.8m S    0  0.8   0:00.20 chrome             
 1889 george  20   0  301m  15m  11m S    0  0.8   0:00.17 clock-applet       
 4752 george  20   0  214m  14m  10m S    1  0.7   0:04.45 gnome-terminal     
 1886 george  20   0  253m  14m  10m S    0  0.7   0:00.52 wnck-applet        
 1796 george  20   0  250m  14m  10m S    0  0.7   0:00.21 gnome-panel        
 2312 george  20   0  414m  13m  10m S    0  0.7   0:00.09 evolution-alarm    
 2335 george  20   0  347m  13m  10m S    0  0.7   0:00.07 evolution-excha    


george@george-server:~$ free -mt
             total       used       free     shared    buffers     cached
Mem:          2009       1932         77          0         39        130
-/+ buffers/cache:       1761        247
Swap:         5884          5       5879
Total:        7894       1937       5956


george@george-server:~$ cat /proc/meminfo
MemTotal:        2057460 kB
MemFree:           86272 kB
Buffers:           38892 kB
Cached:           125452 kB
SwapCached:          664 kB
Active:           296284 kB
Inactive:         151676 kB
Active(anon):     218204 kB
Inactive(anon):    73484 kB
Active(file):      78080 kB
Inactive(file):    78192 kB
Unevictable:           0 kB
Mlocked:               0 kB
SwapTotal:       6026232 kB
SwapFree:        6020336 kB
Dirty:                92 kB
Writeback:             0 kB
AnonPages:        283008 kB
Mapped:           107596 kB
Shmem:              8072 kB
Slab:             645212 kB
SReclaimable:      85996 kB
SUnreclaim:       559216 kB
KernelStack:        2464 kB
PageTables:        24224 kB
NFS_Unstable:          0 kB
Bounce:                0 kB
WritebackTmp:          0 kB
CommitLimit:     7054960 kB
Committed_AS:    1118688 kB
VmallocTotal:   34359738367 kB
VmallocUsed:     1078180 kB
VmallocChunk:   34358652924 kB
HardwareCorrupted:     0 kB
HugePages_Total:       0
HugePages_Free:        0
HugePages_Rsvd:        0
HugePages_Surp:        0
Hugepagesize:       2048 kB
DirectMap4k:       30336 kB
DirectMap2M:     2066432 kB

```

---

