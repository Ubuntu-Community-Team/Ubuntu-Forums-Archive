---
title: "Slow transfer over the lan after a while."
date: 2008-07-29
forum: Networking &amp; Wireless
---

### Post by Brutalix on 2008-07-29
I have 2 computers, 1 w linux(hardy heron latest kernel from the update), which i use as server and backup, and one with windows xp.

After the last update I have noticed slower transfers via the lan. It's random and occurs after the linux box have been on for some time. I used to have 50 mbyte pr sec bidirectional rate from the server to the xp machine. Now i have more like 1 mbyte/s if i am lucky.... 

I cant find why its behaving like this, first i thought it might be some packet errors, or samba being slow, but it also occurs if i try with ftp.  But i do get some strange numbers in iostat, so since i am not very viced in using linux, i thought I'd try posting here first. Any ideas to what might be the source of the problem? Any other programs i could check to see what/where the problem could lie?

Kind regards 
Brut. 

EDIT: The numbers on the iostat marked with red, are those i believe to be wrong, there is only activity to sdd. 

Network equipment:
Dlink DGL-4300 gigbit router.
Broadcom onboard 1 gig lan. on both computers. 

IFconfig: 
eth0      Link encap:Ethernet  HWaddr not relevant. 
          inet addr: not relevant  Bcast:192.168.mmm.nn Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4776123 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2637172 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:6559924288 (6.1 GB)  TX bytes:589546399 (562.2 MB)
          Interrupt:18

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4979944 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4979944 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:323669456 (308.6 MB)  TX bytes:323669456 (308.6 MB)

Linux 2.6.24-19-generic (Server)        07/29/2008

avg-cpu:  %user   %nice %system %iowait  %steal   %idle
           1.45    0.03    1.43    1.26    0.00   95.84

Device:         rrqm/s   wrqm/s     r/s     w/s    rkB/s    wkB/s avgrq-sz avgqu-sz   await  svctm  %util
sda               0.03     0.00    0.01    0.00     0.09     0.00    16.31     0.00    5.40   5.26   0.01
sdb               0.03     0.35    0.03    1.01     0.70   343.86   663.47     0.39  [COLOR="Red"]370.23   8.64 [/COLOR]  0.90
sdc               0.13     0.02    0.27    0.06    23.43    21.49   273.08     0.02   [COLOR="Red"]61.74   4.86 [/COLOR]  0.16
sdd               0.05     0.00    0.05    0.00     0.24     0.00     9.77     0.00    [COLOR="Red"]7.36   7.33 [/COLOR]  0.04
sde               0.03     0.00    0.01    0.00     0.08     0.00    18.59     0.00    6.18   5.36   0.00
sdf               0.03     0.00    0.01    0.00     0.07     0.00    19.20     0.00    2.17   2.02   0.00
sdg               0.03     0.00    0.02    0.00     0.11     0.00    13.38     0.00    6.47   6.38   0.01
sdh               0.03     0.00    0.01    0.00     0.10     0.00    13.99     0.00    3.17   3.03   0.00
sdi               0.03     0.00    0.01    0.00     0.07     0.00    19.44     0.00    2.85   2.72   0.00
hda             [COLOR="Red"] 42.10     4.22[/COLOR]    5.89    1.84   [COLOR="Red"]216.68    24.33    62.39[/COLOR]     0.23   30.16   3.08   2.38
sdj               0.02     0.00    0.01    0.00     0.08     0.00    12.36     0.00    6.30   6.21   0.01

---

