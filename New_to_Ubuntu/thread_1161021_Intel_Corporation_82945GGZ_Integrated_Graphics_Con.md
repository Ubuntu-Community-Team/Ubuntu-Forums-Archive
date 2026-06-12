---
title: "Intel Corporation 82945G/GZ Integrated Graphics Controller slow when update to jaunty"
date: 2009-05-16
forum: New to Ubuntu
---

### Post by trigsenior on 2009-05-16
Greetings, 

When I updated from 8.10 to 9.10 my Graphics card became very slow and lagging , Compiz and old quake based games ( tremulous ) which ran fine before are having  terrible fps now. However at-least I do not suffer from random crashes. Is there a way to use official drivers or anything else I can try ?

here some info lscpi and x11perf -all not sure if helpfull.
 
$=> lspci
00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GH (ICH7DH) LPC Interface Bridge (rev 01)
00:1f.2 RAID bus controller: Intel Corporation 82801GR/GH (ICH7 Family) SATA RAID Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:01.0 FireWire (IEEE 1394): Agere Systems FW323 (rev 70)
01:08.0 Ethernet controller: Intel Corporation 82801G (ICH7 Family) LAN Controller (rev 01)


$=>  x11perf -all

x11perf - X11 performance program, version 1.2
The X.Org Foundation server version 10600000 on :0.0
from emilien-desktop
Sat May 16 14:58:20 2009

Sync time adjustment is 0.0893 msecs.

20000000 reps @   0.0004 msec (2450000.0/sec): Dot
20000000 reps @   0.0004 msec (2480000.0/sec): Dot
20000000 reps @   0.0004 msec (2240000.0/sec): Dot
20000000 reps @   0.0004 msec (2360000.0/sec): Dot
20000000 reps @   0.0004 msec (2300000.0/sec): Dot
100000000 trep @   0.0004 msec (2360000.0/sec): Dot

20000000 reps @   0.0004 msec (2330000.0/sec): 1x1 rectangle
20000000 reps @   0.0004 msec (2340000.0/sec): 1x1 rectangle
20000000 reps @   0.0004 msec (2460000.0/sec): 1x1 rectangle
20000000 reps @   0.0004 msec (2400000.0/sec): 1x1 rectangle
20000000 reps @   0.0005 msec (2160000.0/sec): 1x1 rectangle
100000000 trep @   0.0004 msec (2330000.0/sec): 1x1 rectangle

8000000 reps @   0.0005 msec (2150000.0/sec): 10x10 rectangle
8000000 reps @   0.0006 msec (1780000.0/sec): 10x10 rectangle
8000000 reps @   0.0004 msec (2260000.0/sec): 10x10 rectangle
8000000 reps @   0.0004 msec (2230000.0/sec): 10x10 rectangle
8000000 reps @   0.0005 msec (2100000.0/sec): 10x10 rectangle
40000000 trep @   0.0005 msec (2090000.0/sec): 10x10 rectangle

 720000 reps @   0.0094 msec (106000.0/sec): 100x100 rectangle
 720000 reps @   0.0092 msec (108000.0/sec): 100x100 rectangle
 720000 reps @   0.0088 msec (114000.0/sec): 100x100 rectangle
 720000 reps @   0.0089 msec (112000.0/sec): 100x100 rectangle
 720000 reps @   0.0087 msec (114000.0/sec): 100x100 rectangle
3600000 trep @   0.0090 msec (111000.0/sec): 100x100 rectangle

  30000 reps @   0.1802 msec (  5550.0/sec): 500x500 rectangle
  30000 reps @   0.1800 msec (  5550.0/sec): 500x500 rectangle
  30000 reps @   0.1784 msec (  5610.0/sec): 500x500 rectangle
  30000 reps @   0.1786 msec (  5600.0/sec): 500x500 rectangle
  30000 reps @   0.1781 msec (  5610.0/sec): 500x500 rectangle
 150000 trep @   0.1791 msec (  5580.0/sec): 500x500 rectangle

9000000 reps @   0.0005 msec (1830000.0/sec): 1x1 stippled rectangle (8x8 stipple)
9000000 reps @   0.0006 msec (1700000.0/sec): 1x1 stippled rectangle (8x8 stipple)
9000000 reps @   0.0006 msec (1770000.0/sec): 1x1 stippled rectangle (8x8 stipple)
9000000 reps @   0.0006 msec (1820000.0/sec): 1x1 stippled rectangle (8x8 stipple)
9000000 reps @   0.0005 msec (1870000.0/sec): 1x1 stippled rectangle (8x8 stipple)
45000000 trep @   0.0006 msec (1790000.0/sec): 1x1 stippled rectangle (8x8 stipple)

2000000 reps @   0.0036 msec (281000.0/sec): 10x10 stippled rectangle (8x8 stipple)
2000000 reps @   0.0036 msec (278000.0/sec): 10x10 stippled rectangle (8x8 stipple)
2000000 reps @   0.0036 msec (274000.0/sec): 10x10 stippled rectangle (8x8 stipple)
2000000 reps @   0.0034 msec (292000.0/sec): 10x10 stippled rectangle (8x8 stipple)
2000000 reps @   0.0035 msec (287000.0/sec): 10x10 stippled rectangle (8x8 stipple)
10000000 trep @   0.0035 msec (282000.0/sec): 10x10 stippled rectangle (8x8 stipple)

  21600 reps @   0.2672 msec (  3740.0/sec): 100x100 stippled rectangle (8x8 stipple)
  21600 reps @   0.3122 msec (  3200.0/sec): 100x100 stippled rectangle (8x8 stipple)
  21600 reps @   0.2295 msec (  4360.0/sec): 100x100 stippled rectangle (8x8 stipple)
  21600 reps @   0.2246 msec (  4450.0/sec): 100x100 stippled rectangle (8x8 stipple)
  21600 reps @   0.2495 msec (  4010.0/sec): 100x100 stippled rectangle (8x8 stipple)
 108000 trep @   0.2566 msec (  3900.0/sec): 100x100 stippled rectangle (8x8 stipple)

    900 reps @   6.0998 msec (   164.0/sec): 500x500 stippled rectangle (8x8 stipple)
    900 reps @   5.9367 msec (   168.0/sec): 500x500 stippled rectangle (8x8 stipple)
    900 reps @   5.9885 msec (   167.0/sec): 500x500 stippled rectangle (8x8 stipple)
    900 reps @   5.9242 msec (   169.0/sec): 500x500 stippled rectangle (8x8 stipple)
    900 reps @   6.0333 msec (   166.0/sec): 500x500 stippled rectangle (8x8 stipple)
   4500 trep @   5.9965 msec (   167.0/sec): 500x500 stippled rectangle (8x8 stipple)

10000000 reps @   0.0005 msec (1830000.0/sec): 1x1 opaque stippled rectangle (8x8 stipple)
10000000 reps @   0.0006 msec (1600000.0/sec): 1x1 opaque stippled rectangle (8x8 stipple)
10000000 reps @   0.0007 msec (1480000.0/sec): 1x1 opaque stippled rectangle (8x8 stipple)


10000000 reps @   0.0005 msec (1930000.0/sec): 1x1 opaque stippled rectangle (8x8 stipple)
10000000 reps @   0.0005 msec (1950000.0/sec): 1x1 opaque stippled rectangle (8x8 stipple)
50000000 trep @   0.0006 msec (1740000.0/sec): 1x1 opaque stippled rectangle (8x8 stipple)

2000000 reps @   0.0049 msec (205000.0/sec): 10x10 opaque stippled rectangle (8x8 stipple)
2000000 reps @   0.0047 msec (214000.0/sec): 10x10 opaque stippled rectangle (8x8 stipple)
2000000 reps @   0.0043 msec (230000.0/sec): 10x10 opaque stippled rectangle (8x8 stipple)
2000000 reps @   0.0043 msec (231000.0/sec): 10x10 opaque stippled rectangle (8x8 stipple)
2000000 reps @   0.0041 msec (242000.0/sec): 10x10 opaque stippled rectangle (8x8 stipple)
10000000 trep @   0.0045 msec (224000.0/sec): 10x10 opaque stippled rectangle (8x8 stipple)

---

### Post by cariboo on 2009-05-16
Have a look at this [thread=1130582]thread[/thread], it should help solve your problems.

---

### Post by b@sh_n3rd on 2009-05-16
I tried cariboo907's link before...I've got the Intel 82845G. That thread helped me resolve my probs...If you run into any probs, just ask it right here, I got the hang of it :D and I suppose other's would help too :D. Anyway, I think you should try "Safe" first...If you are satisfied, then that's it...OR, If you want more, make the step to "Optimal". "Bleeding Edge" *might* seem a little buggy, but I haven't noticed anything *yet*...

---

### Post by trigsenior on 2009-05-16
Thank you works like a charm , not had it run so fast in ages.

this is x11perf -all now  =)

x11perf -all
x11perf - X11 performance program, version 1.2
The X.Org Foundation server version 10600000 on :0.0
from emilien-desktop
Sun May 17 01:27:52 2009

Sync time adjustment is 0.0895 msecs.

7000000 reps @   0.0007 msec (1390000.0/sec): Dot
7000000 reps @   0.0007 msec (1390000.0/sec): Dot
7000000 reps @   0.0007 msec (1390000.0/sec): Dot
7000000 reps @   0.0007 msec (1390000.0/sec): Dot
7000000 reps @   0.0007 msec (1390000.0/sec): Dot
35000000 trep @   0.0007 msec (1390000.0/sec): Dot

7000000 reps @   0.0007 msec (1360000.0/sec): 1x1 rectangle
7000000 reps @   0.0007 msec (1360000.0/sec): 1x1 rectangle
7000000 reps @   0.0007 msec (1360000.0/sec): 1x1 rectangle
7000000 reps @   0.0007 msec (1360000.0/sec): 1x1 rectangle
7000000 reps @   0.0007 msec (1360000.0/sec): 1x1 rectangle
35000000 trep @   0.0007 msec (1360000.0/sec): 1x1 rectangle

7000000 reps @   0.0007 msec (1350000.0/sec): 10x10 rectangle
7000000 reps @   0.0007 msec (1360000.0/sec): 10x10 rectangle
7000000 reps @   0.0007 msec (1350000.0/sec): 10x10 rectangle
7000000 reps @   0.0007 msec (1350000.0/sec): 10x10 rectangle
7000000 reps @   0.0007 msec (1350000.0/sec): 10x10 rectangle
35000000 trep @   0.0007 msec (1350000.0/sec): 10x10 rectangle

1080000 reps @   0.0055 msec (180000.0/sec): 100x100 rectangle
1080000 reps @   0.0055 msec (180000.0/sec): 100x100 rectangle
1080000 reps @   0.0055 msec (180000.0/sec): 100x100 rectangle
1080000 reps @   0.0055 msec (180000.0/sec): 100x100 rectangle
1080000 reps @   0.0055 msec (180000.0/sec): 100x100 rectangle
5400000 trep @   0.0055 msec (180000.0/sec): 100x100 rectangle

I would have used "thank you button" but can't seem to find it.

---

