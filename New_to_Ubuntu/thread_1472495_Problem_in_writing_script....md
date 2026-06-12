---
title: "Problem in writing script..."
date: 2010-05-04
forum: New to Ubuntu
---

### Post by siteregsam on 2010-05-04
Hi,

   I had written a shell script that will generate a text file(loadinfo.txt) containing CPU load statistics, Memory usage statistics with Date and Time. And my script is....

chmod +X
#!/bin/bash 

echo DATE':' > loadinfo.txt
date >> loadinfo.txt

echo \ >> loadinfo.txt
echo CPU USAGE INFO':' >> loadinfo.txt 
cat /proc/stat >> loadinfo.txt

echo \ >> loadinfo.txt
echo MEMORY USAGE INFO':' >> loadinfo.txt 
cat /proc/meminfo >> loadinfo.txt

**OUTPUT on running the script:**

[I]DATE:
Tue May  4 21:12:32 IST 2010
 
CPU USAGE INFO:
cpu  12909 724 6034 180758 6403 494 346 0 0
cpu0 4857 125 2565 94013 1092 61 5 0 0
cpu1 8051 599 3469 86745 5311 433 341 0 0
intr 856671 119977 1619 0 0 0 0 0 1 0 3094 0 0 6409 0 14994 0 458284 27803 0 32282 0 850 14124 1 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0
ctxt 639546
btime 1272986725
processes 2469
procs_running 2
procs_blocked 0
softirq 208886 0 114943 943 727 15598 6650 19803 58 50164
 
MEMORY USAGE INFO:
MemTotal:         766296 kB
MemFree:           65272 kB
Buffers:           95868 kB
Cached:           323824 kB
SwapCached:            0 kB
Active:           316904 kB
Inactive:         305776 kB
Active(anon):     208916 kB
Inactive(anon):       16 kB
Active(file):     107988 kB
Inactive(file):   305760 kB
Unevictable:           0 kB
Mlocked:               0 kB
HighTotal:             0 kB
HighFree:              0 kB
LowTotal:         766296 kB
LowFree:           65272 kB
SwapTotal:       1052216 kB
SwapFree:        1052216 kB
Dirty:               112 kB
Writeback:             0 kB
AnonPages:        203028 kB
Mapped:            90740 kB
Slab:              26932 kB
SReclaimable:      17836 kB
SUnreclaim:         9096 kB
PageTables:         6428 kB
NFS_Unstable:          0 kB
Bounce:                0 kB
WritebackTmp:          0 kB
CommitLimit:     1435364 kB
Committed_AS:     987468 kB
VmallocTotal:     247224 kB
VmallocUsed:       37248 kB
VmallocChunk:     207760 kB
HugePages_Total:       0
HugePages_Free:        0
HugePages_Rsvd:        0
HugePages_Surp:        0
Hugepagesize:       4096 kB
DirectMap4k:       10816 kB
DirectMap4M:      774144 kB[/I]

**But i need to add IP ADDRESS too. I modified the script as....**

chmod +X
#!/bin/bash 

echo DATE':' > loadinfo.txt
date >> loadinfo.txt

echo IP ADDRESS':' > loadinfo.txt
ifconfig >> loadinfo.txt

echo \ >> loadinfo.txt
echo CPU USAGE INFO':' >> loadinfo.txt 
cat /proc/stat >> loadinfo.txt

echo \ >> loadinfo.txt
echo MEMORY USAGE INFO':' >> loadinfo.txt 
cat /proc/meminfo >> loadinfo.txt

Now the** OUTPUT** becomes

[I]IP ADDRESS:
eth0      Link encap:Ethernet  HWaddr 00:16:36:f4:c6:d9  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:20 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:6 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:340 (340.0 B)  TX bytes:340 (340.0 B)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:117.254.149.242  P-t-P:192.168.52.12  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:834 errors:3 dropped:0 overruns:0 frame:0
          TX packets:943 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:579465 (579.4 KB)  TX bytes:151453 (151.4 KB)

wlan0     Link encap:Ethernet  HWaddr 00:19:7d:c3:fc:e7  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-19-7D-C3-FC-E7-00-00-00-00-00-00-00-00-00-00  
          UP RUNNING  MTU:0  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

 
CPU USAGE INFO:
cpu  14036 724 6688 193948 6406 497 374 0 0
cpu0 5217 125 2703 100962 1092 62 5 0 0
cpu1 8818 599 3984 92986 5313 435 368 0 0
intr 887455 127769 1767 0 0 0 0 0 1 0 3254 0 0 6409 0 16162 0 458284 28958 0 35477 0 915 14294 1 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0
ctxt 705138
btime 1272986725
processes 2495
procs_running 1
procs_blocked 0
softirq 220896 0 124015 944 727 15881 6860 21130 61 51278
 
MEMORY USAGE INFO:
MemTotal:         766296 kB
MemFree:           64388 kB
Buffers:           96072 kB
Cached:           323828 kB
SwapCached:            0 kB
Active:           324320 kB
Inactive:         299300 kB
Active(anon):     209648 kB
Inactive(anon):       16 kB
Active(file):     114672 kB
Inactive(file):   299284 kB
Unevictable:           0 kB
Mlocked:               0 kB
HighTotal:             0 kB
HighFree:              0 kB
LowTotal:         766296 kB
LowFree:           64388 kB
SwapTotal:       1052216 kB
SwapFree:        1052216 kB
Dirty:                16 kB
Writeback:             0 kB
AnonPages:        203724 kB
Mapped:            90764 kB
Slab:              26968 kB
SReclaimable:      17848 kB
SUnreclaim:         9120 kB
PageTables:         6540 kB
NFS_Unstable:          0 kB
Bounce:                0 kB
WritebackTmp:          0 kB
CommitLimit:     1435364 kB
Committed_AS:     995360 kB
VmallocTotal:     247224 kB
VmallocUsed:       37248 kB
VmallocChunk:     207760 kB
HugePages_Total:       0
HugePages_Free:        0
HugePages_Rsvd:        0
HugePages_Surp:        0
Hugepagesize:       4096 kB
DirectMap4k:       10816 kB
DirectMap4M:      774144 kB[/I]

I can't get the date info in my output after modifying....
How to make the script work? :confused:

---

### Post by patchwork on 2010-05-04
> echo DATE':' > loadinfo.txt
date >> loadinfo.txt

echo IP ADDRESS':' **>** loadinfo.txt
ifconfig >> loadinfo.txt

You're over-writing the file with the > loadinfo.txt on your IP line.   Change it to append ( >> )

---

### Post by peculiar penguin on 2010-05-04
> **siteregsam said:**
> 
echo IP ADDRESS':' **>** loadinfo.txt


You're overwriting the existing file (with the date already in it) here, use >> like in the other lines.

Edit: D'oh! :P

---

### Post by sandyd on 2010-05-04
you might also want to look into awk/grep to clean up the output.

---

