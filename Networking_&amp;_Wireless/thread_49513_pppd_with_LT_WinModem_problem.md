---
title: "pppd with LT WinModem problem"
date: 2005-07-16
forum: Networking &amp; Wireless
---

### Post by dxvxd on 2005-07-16
I have 2 fresh installed Ubuntu systems, on 2 different computers ("Duron" & "Sampron"). Duron has LT WinModem and it works fine. But, when I unplug modem from Duron, and plug it into Sampron, modem doesn't work (I used same method for configuring it, explained in HowTo on Ubuntu Wiki pages).

I mean, it works, but connection can not be made. Modem dials a number, then comes noise tones, and after while, modem hangs up. On same machine, Sampron, under Windows, modem works fine.

I spent some time finding reason why it doesn't work on Sampron as it works on Duron (solution is still out of sight  ](*,) ), and after some digging through man pages, configs on both machines, I found next (I'm newbie in Linux world and this things are new to me, so this is maybe wrong path for finding solution):

  - If I turn on 'debug' option in '/etc/ppp/options', some messages will be written in '/var/log/syslog' so I can see what's happening. And there was a difference between logs on Duron and Sampron.

I present log part from Sampron:

[INDENT]Jul 16 19:38:29 localhost kernel: CSLIP: code copyright 1989 Regents of the University of California
Jul 16 19:38:29 localhost udev[9259]: creating device node '/dev/ppp'
Jul 16 19:38:29 localhost kernel: PPP generic driver version 2.4.2
Jul 16 19:38:29 localhost pppd[9215]: pppd 2.4.2 started by david, uid 1000
Jul 16 19:38:29 localhost pppd[9215]: using channel 1
Jul 16 19:38:29 localhost pppd[9215]: Using interface ppp0
Jul 16 19:38:29 localhost pppd[9215]: Connect: ppp0 <--> /dev/ttLTM0
Jul 16 19:38:29 localhost pppd[9215]: sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0xbe03344e> <pcomp> <accomp>]
Jul 16 19:38:56 localhost last message repeated 9 times
Jul 16 19:38:59 localhost pppd[9215]: LCP: timeout sending Config-Requests 
Jul 16 19:38:59 localhost pppd[9215]: Connection terminated.
Jul 16 19:38:59 localhost pppd[9215]: Exit[/INDENT]

I guess the problem is in pppd (as I understand those log lines), because it can't connect modem device (/dev/ttLTM0). At this point I found the problem goes beyond my scope (not for long, I hope), and I need help.

Note: for connecting I use Gnome-ppp, and his log says that pppd exits with code 10.

---

### Post by dxvxd on 2005-07-19
Problem solved by adding 'noapic' boot parametar for kernel (found tip somwhere on net). Don't know why, but it works.

---

