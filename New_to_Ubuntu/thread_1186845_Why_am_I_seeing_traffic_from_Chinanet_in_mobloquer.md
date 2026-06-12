---
title: "Why am I seeing traffic from Chinanet in mobloquer?"
date: 2009-06-13
forum: New to Ubuntu
---

### Post by kireol on 2009-06-13
I just installed Ubuntu (long time XP user)
The PC sits behind a linksys wrt54gl router with Tomato installed.  No forwarding set up
"shields up" says i'm in stealth on ports 0 to 1056


This is a fresh install of Ubuntu 9.04 (64bit) Linux Ubuntu 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:58:03 UTC 2009 x86_64 GNU/Linux


I installed Moblocker (mobloquer) which uses blocklist

The log there is showing traffic to a bunch of stuff I've never seen before.

I'm not running any torrent software.
The only other thing that I'm running is Firefox and Thunderbird to my gmail account.

Since my router isn't forwarding anything, and I'm only explicity running firefox and thunderbird, I'm very concerned with how this traffic is getting to this PC.

Thanks

```
Sat Jun 13 22:13:30| IN: CHINANET Shanghai province network,hits: 42,SRC: 58.34.120.233
Sat Jun 13 22:13:49| IN: CHINANET Shanghai province network,hits: 43,SRC: 58.34.120.233
Sat Jun 13 22:13:55| IN: CHINANET Shanghai province network,hits: 44,SRC: 58.34.120.233
Sat Jun 13 22:14:10| IN: TATA Communications (Canada)ULC,hits: 22,SRC: 195.210.206.12
Sat Jun 13 22:14:13| IN: TATA Communications (Canada)ULC,hits: 23,SRC: 195.210.206.12
Sat Jun 13 22:14:15| IN: CHINANET Shanghai province network,hits: 45,SRC: 58.34.120.233
Sat Jun 13 22:14:19| IN: TATA Communications (Canada)ULC,hits: 24,SRC: 195.210.206.12
Sat Jun 13 22:14:20| IN: CHINANET Shanghai province network,hits: 46,SRC: 58.34.120.233
Sat Jun 13 22:14:40| IN: CHINANET Shanghai province network,hits: 47,SRC: 58.34.120.233
Sat Jun 13 22:14:45| IN: CHINANET Shanghai province network,hits: 48,SRC: 58.34.120.233
Sat Jun 13 22:15:04| IN: TATA Communications (Canada)ULC,hits: 25,SRC: 195.210.206.12
Sat Jun 13 22:15:05| IN: CHINANET Shanghai province network,hits: 49,SRC: 58.34.120.233
Sat Jun 13 22:15:08| IN: TATA Communications (Canada)ULC,hits: 26,SRC: 195.210.206.12
Sat Jun 13 22:15:10| IN: CHINANET Shanghai province network,hits: 50,SRC: 58.34.120.233
Sat Jun 13 22:15:13| IN: TATA Communications (Canada)ULC,hits: 27,SRC: 195.210.206.12
Sat Jun 13 22:15:29| IN: CHINANET Shanghai province network,hits: 51,SRC: 58.34.120.233
Sat Jun 13 22:15:35| IN: CHINANET Shanghai province network,hits: 52,SRC: 58.34.120.233
Sat Jun 13 22:15:54| IN: CHINANET Shanghai province network,hits: 53,SRC: 58.34.120.233
Sat Jun 13 22:16:00| IN: CHINANET Shanghai province network,hits: 54,SRC: 58.34.120.233
Sat Jun 13 22:16:20| IN: CHINANET Shanghai province network,hits: 55,SRC: 58.34.120.233
Sat Jun 13 22:16:25| IN: CHINANET Shanghai province network,hits: 56,SRC: 58.34.120.233
Sat Jun 13 22:16:45| IN: CHINANET Shanghai province network,hits: 57,SRC: 58.34.120.233
Sat Jun 13 22:16:50| IN: CHINANET Shanghai province network,hits: 58,SRC: 58.34.120.233
Sat Jun 13 22:17:05| IN: CHINANET Shanghai province network,hits: 59,SRC: 58.34.120.233
Sat Jun 13 22:17:10| IN: CHINANET Shanghai province network,hits: 60,SRC: 58.34.120.233
Sat Jun 13 22:17:10| IN: CHINANET Shanghai province network,hits: 61,SRC: 58.34.120.233
Sat Jun 13 22:17:15| IN: CHINANET Shanghai province network,hits: 62,SRC: 58.34.120.233
Sat Jun 13 22:17:35| IN: CHINANET Shanghai province network,hits: 63,SRC: 58.34.120.233
Sat Jun 13 22:17:40| IN: CHINANET Shanghai province network,hits: 64,SRC: 58.34.120.233
Sat Jun 13 22:18:00| IN: CHINANET Shanghai province network,hits: 65,SRC: 58.34.120.233
Sat Jun 13 22:18:05| IN: China Unicom Beijing province network,hits: 3,SRC: 221.221.28.134
Sat Jun 13 22:18:05| IN: CHINANET Shanghai province network,hits: 66,SRC: 58.34.120.233
Sat Jun 13 22:18:15| IN: China Unicom Beijing province network,hits: 4,SRC: 221.221.28.134
Sat Jun 13 22:18:24| IN: CHINANET Shanghai province network,hits: 67,SRC: 58.34.120.233
Sat Jun 13 22:18:30| IN: CHINANET Shanghai province network,hits: 68,SRC: 58.34.120.233
Sat Jun 13 22:18:49| IN: CHINANET Shanghai province network,hits: 69,SRC: 58.34.120.233
Sat Jun 13 22:18:55| IN: CHINANET Shanghai province network,hits: 70,SRC: 58.34.120.233
Sat Jun 13 22:19:15| IN: CHINANET Shanghai province network,hits: 71,SRC: 58.34.120.233
Sat Jun 13 22:19:20| IN: CHINANET Shanghai province network,hits: 72,SRC: 58.34.120.233
Sat Jun 13 22:19:33| IN: CHINANET Shanghai province network,hits: 5,SRC: 61.170.179.154
Sat Jun 13 22:19:40| IN: CHINANET Shanghai province network,hits: 73,SRC: 58.34.120.233
```

---

### Post by lovinglinux on 2009-06-13
I know you are not using a torrent client right now, but have you used it before on this machine? I'm asking this because it looks like your router is actually forwarding a port. If you are sure that you don't have any forwarding rule configured in the router, then maybe you have activated a program with UPnP support (like a torrent client) that didn't close the port on the router appropriately.

Check if you have UPnP enabled in the router, disable it and then check if the connections stop.

---

### Post by superprash2003 on 2009-06-14
well these are most probably botnets .. as long as its being blocked , it should be fine..

---

### Post by kireol on 2009-06-14
thanks lovinglinux.


It turned out I had UPnP Forwarded Ports from my windows install that I had forgotten about.

:)

---

