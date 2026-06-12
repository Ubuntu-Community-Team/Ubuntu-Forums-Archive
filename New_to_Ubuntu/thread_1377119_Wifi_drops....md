---
title: "Wifi drops..."
date: 2010-01-09
forum: New to Ubuntu
---

### Post by kamitsukai on 2010-01-09
My wifi keeps disconnecting after prolonged periods of Usenet usage.

my setup is:

Ubuntu 9.10 'karmic' on a Dell Inspiron 1525 with the Broadcom bcm4312 14e4:4315 wireless card using the b43 driverwhich connects to my Inventel Livebox router (supplied by orange uk)


Are there any ways to record the wifi to work out whats going on?


Thanks in advance!

---

### Post by spiderbatdad on 2010-01-09
Maybe in the log file viewer under System>>Administration>>Daemon Log
or dmesg|tail

---

### Post by kamitsukai on 2010-01-10
okay the output from that is as follows:

```
carl@carl-laptop:~$ dmesg|tail
[   40.095603] wlan0: authenticated
[   40.095626] wlan0: associate with AP 00:19:7d:3c:55:8c (try 1)
[   40.101230] wlan0: RX AssocResp from 00:19:7d:3c:55:8c (capab=0x411 status=0 aid=1)
[   40.101234] wlan0: associated
[   40.102100] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   50.128037] wlan0: no IPv6 routers present
[  136.384548] [drm] TV-16: set mode NTSC 480i 0
[  167.552051] CE: hpet increasing min_delta_ns to 15000 nsec
[  224.412066] CE: hpet increasing min_delta_ns to 22500 nsec
[  787.471241] nautilus[2616]: segfault at 4898853 ip 001ed803 sp bfd622b0 error 4 in libgobject-2.0.so.0.2200.3[1c8000+3c000]

```

although I dont no if this will help...

---

### Post by AndresM on 2010-01-24
Hi, I've had some problems I think I have solved them with this: [http://ubuntuforums.org/showthread.php?t=1374111&highlight=wifi+karmic+ubuntu](http://ubuntuforums.org/showthread.php?t=1374111&highlight=wifi+karmic+ubuntu)

good luck!

---

### Post by gnometorule on 2010-01-24
Maybe your provider is just dropping you? Where i live, I get temporarily disconnected frequently. As a first step, I'd try using your wired ethernet for a day and see if you still get disconnected; if yes, it's probably no issue with your wireless.

dmesg only shows you what happens at boot, and while i'm no explicit expert on the topic, your output seems fine. If you'd like to monitor this in the background while you do other stuff, open a shell just for this purpose, and run

iwevent

Read the man too, which refers to other keywords/commands you might find useful to track this down. Maybe you will see something interesting in the running iwevent log the next time you get disconnected. I'd take it from there.

---

