---
title: "vnstat glitch?"
date: 2008-09-26
forum: Networking &amp; Wireless
---

### Post by kpatz on 2008-09-26
I have vnstat installed on my firewall box so I can monitor my bandwidth usage.  I've had it installed for about 2 weeks so far, and it's worked well, except for one glitch that happened last night.

I looked at it this morning, and it says I used 3.77 GB of bandwidth yesterday!  Considering my average is 200-250 MB a day, I thought that was unusual, so I did some digging.

Here's the output of vnstat -d.
```
kpatz@zuul:/proc/net$ vnstat -d

 WAN Interface (eth0)  /  daily

    day         rx      |     tx      |  total
------------------------+-------------+----------------------------------------
   15.09.    102.96 MB  |    4.31 MB  |  107.26 MB
   16.09.    139.92 MB  |   14.36 MB  |  154.29 MB
   17.09.    122.67 MB  |    5.11 MB  |  127.78 MB
   18.09.    276.14 MB  |   14.78 MB  |  290.92 MB   %
   19.09.    267.24 MB  |   18.58 MB  |  285.82 MB   %
   20.09.    253.61 MB  |    5.11 MB  |  258.72 MB   %
   21.09.    262.66 MB  |    5.36 MB  |  268.02 MB   %
   22.09.    237.73 MB  |    5.85 MB  |  243.58 MB   %
   23.09.    245.82 MB  |    7.44 MB  |  253.26 MB   %
   24.09.    235.08 MB  |    5.55 MB  |  240.63 MB   %
   25.09.      3.77 GB  |  168.72 MB  |    3.93 GB   %%%%%%%%%%%%%%%%%%%%%%%%:
   26.09.     98.80 MB  |    2.23 MB  |  101.03 MB
------------------------+-------------+----------------------------------------
 estimated      224 MB  |       4 MB  |     228 MB

```

Here's vnstat -h (hourly stats).

```

kpatz@zuul:/proc/net$ vnstat -h
 WAN Interface (eth0)                                                     10:30
  ^                                r
  |                                r
  |                                r
  |                                r
  |                                r
  |                                r
  |                                r
  |                                r
  |                                r
  |                                r
 -+--------------------------------------------------------------------------->
  |  11 12 13 14 15 16 17 18 19 20 21 22 23 00 01 02 03 04 05 06 07 08 09 10

 h   rx (kB)    tx (kB)      h   rx (kB)    tx (kB)      h   rx (kB)    tx (kB)
11       9578        127    19      24642        717    03       8626         78
12       9966        238    20       9519        165    04      10611        187
13       9267         96    21    3699110     167462    05       9084        134
14       9483        205    22       7863         88    06      10996        137
15       8933         97    23       8074         81    07      14049        574
16       8894        749    00       9002        137    08       9089        142
17      12297        394    01       8548        148    09       9008        252
18      12653        363    02       8639         88    10       4085        409

```

As you can see, the hour 21 (9 pm) shows 3+ GB used.  I was doing some work then but wasn't doing any huge downloads.  I then ran ifconfig eth0 to see what those counters were:

```
kpatz@zuul:/proc/net$ uptime
 10:32:30 up 17 days, 16:03,  2 users,  load average: 0.00, 0.00, 0.00
kpatz@zuul:/proc/net$ ifconfig eth0
eth0      Link encap:Ethernet  HWaddr **:**:**:**:**:**
          inet addr:76.**.**.**  Bcast:255.255.255.255  Mask:255.255.252.0
          inet6 addr: ****::***:****:****:****/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:32058770 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1257169 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:3905080016 (3.6 GB)  TX bytes:173991423 (165.9 MB)
          Interrupt:9 Base address:0xec00

```

So that's showing 3.6 GB over a 17-day period.  If that bandwidth spike were real, I would see double this in the ifconfig.

It looks to me like vnstat hiccuped during one of its database updates, causing it to think that the bandwidth usage in /proc was total for that hour rather than total since boot.

Here's a dump of my vnstat database:
```

kpatz@zuul:/proc/net$ vnstat --dumpdb
version;3
active;1
interface;eth0
nick;WAN Interface
created;1221483061
updated;1222439701
totalrx;6100
totaltx;257
currx;3905365760
curtx;173992831
totalrxk;714
totaltxk;417
btime;1220912950
d;0;1222401601;99;2;941;249;1
d;1;1222315201;3856;168;968;737;1
d;2;1222228801;235;5;86;560;1
d;3;1222142401;245;7;837;449;1
d;4;1222056001;237;5;751;868;1
d;5;1221969601;262;5;671;370;1
d;6;1221883201;253;5;625;110;1
d;7;1221796801;267;18;242;595;1
d;8;1221710401;276;14;147;798;1
d;9;1221624001;122;5;688;115;1
d;10;1221537601;139;14;947;373;1
d;11;1221483061;102;4;979;313;1
d;12;0;0;0;0;0;0
d;13;0;0;0;0;0;0
d;14;0;0;0;0;0;0
d;15;0;0;0;0;0;0
d;16;0;0;0;0;0;0
d;17;0;0;0;0;0;0
d;18;0;0;0;0;0;0
d;19;0;0;0;0;0;0
d;20;0;0;0;0;0;0
d;21;0;0;0;0;0;0
d;22;0;0;0;0;0;0
d;23;0;0;0;0;0;0
d;24;0;0;0;0;0;0
d;25;0;0;0;0;0;0
d;26;0;0;0;0;0;0
d;27;0;0;0;0;0;0
d;28;0;0;0;0;0;0
d;29;0;0;0;0;0;0
m;0;1221483061;6100;257;714;417;1
m;1;0;0;0;0;0;0
m;2;0;0;0;0;0;0
m;3;0;0;0;0;0;0
m;4;0;0;0;0;0;0
m;5;0;0;0;0;0;0
m;6;0;0;0;0;0;0
m;7;0;0;0;0;0;0
m;8;0;0;0;0;0;0
m;9;0;0;0;0;0;0
m;10;0;0;0;0;0;0
m;11;0;0;0;0;0;0
t;0;1222315201;3856;168;968;737;1
t;1;1221710401;276;14;147;798;1
t;2;1221796801;267;18;242;595;1
t;3;1221969601;262;5;671;370;1
t;4;1221883201;253;5;625;110;1
t;5;1222142401;245;7;837;449;1
t;6;1222056001;237;5;751;868;1
t;7;1222228801;235;5;86;560;1
t;8;1221537601;139;14;947;373;1
t;9;1221624001;122;5;688;115;1
h;0;1222404901;9002;137
h;1;1222408501;8548;148
h;2;1222412101;8639;88
h;3;1222415701;8626;78
h;4;1222419301;10611;187
h;5;1222422901;9084;134
h;6;1222426501;10996;137
h;7;1222430102;14049;574
h;8;1222433701;9089;142
h;9;1222437301;9008;252
h;10;1222439701;4665;420
h;11;1222358101;9578;127
h;12;1222361701;9966;238
h;13;1222365301;9267;96
h;14;1222368901;9483;205
h;15;1222372501;8933;97
h;16;1222376101;8894;749
h;17;1222379701;12297;394
h;18;1222383301;12653;363
h;19;1222386901;24642;717
h;20;1222390501;9519;165
h;21;1222394101;3699110;167462
h;22;1222397701;7863;88
h;23;1222401301;8074;81

```
As you can see, the h;21 line above shows the bandwidth "spike".

Has anyone had this happen before?  Any ideas as to the cause?  Maybe eth0 went down and back up during one update, causing the counters to reset?  I don't see anything in my logs however.

---

