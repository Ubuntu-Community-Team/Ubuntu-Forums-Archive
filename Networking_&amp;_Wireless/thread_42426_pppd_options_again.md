---
title: "pppd options again"
date: 2005-06-17
forum: Networking &amp; Wireless
---

### Post by joe247 on 2005-06-17
Hi,
Got my ltmodem working but when when I try and connect with wvdial or gnome-ppp I get the following error: PPP daemon has died (exit code=2)
I tried google and I've searched these forums but nothing helped.
The following is from my syslog

Jun 17 18:42:13 localhost -- MARK --
Jun 17 19:00:31 localhost pppd[7622]: Can't open options file /etc/ppp/peers/wvdial: No such file or directory
Jun 17 19:00:59 localhost pppd[7628]: unrecognized option 'options'
Jun 17 19:01:22 localhost pppd[7633]: pppd 2.4.2 started by root, uid 0
Jun 17 19:01:22 localhost pppd[7633]: using channel 1
Jun 17 19:01:22 localhost pppd[7633]: Using interface ppp0
Jun 17 19:01:22 localhost pppd[7633]: Connect: ppp0 <--> /dev/pts/1
Jun 17 19:01:22 localhost pppd[7633]: sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0x2282601> <pcomp> <accomp>]
Jun 17 19:01:22 localhost kernel: CSLIP: code copyright 1989 Regents of the University of California
Jun 17 19:01:23 localhost kernel: PPP generic driver version 2.4.2
Jun 17 19:01:24 localhost udev[7706]: creating device node '/dev/ppp'
Jun 17 19:01:25 localhost pppd[7633]: sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0x2282601> <pcomp> <accomp>]
Jun 17 19:01:31 localhost last message repeated 2 times
Jun 17 19:01:33 localhost pppd[7633]: Modem hangup
Jun 17 19:01:33 localhost pppd[7633]: Connection terminated.
Jun 17 19:01:33 localhost pppd[7633]: Exit.

I can use the same modem under Windows XP to connect to the internet. Can I check certain options or run some program under windows to see which options work? Or am I totally misunderstanding the situation?

Any help appreciated...

---

