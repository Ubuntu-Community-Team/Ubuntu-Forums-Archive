---
title: "tcpdump always shows something even though no internet application is running"
date: 2008-02-27
forum: Networking &amp; Wireless
---

### Post by afeasfaerw23231233 on 2008-02-27
i am using a broadband router to connect the internet. and there's always something showing in my router's log page

even though i close all the internet application the data link LEDs of my router and cable modem are always blinking. here's what it says in tcp dump

is it normal? the router log page says i am having a DoS attack!

---

### Post by Mr. C. on 2008-02-27
> 10:11:53.043540 IP c83-251-188-53.bredband.comhem.se.17045 > wong-desktop.local.32328: UDP, length 98
10:11:53.686043 IP 61.135.234.125.1501 > wong-desktop.local.32328: UDP, length 98
There is still some network connection open.  Run 

```
netstat -a
```

to see the connections.

> 10:11:53.366349 IP ACBD7244.ipt.aol.com.45864 > wong-desktop.local.32328: UDP, length 103
This might be an chat connection to AoL.  Again, look at netstat.

> 10:11:53.043603 IP wong-desktop.local > c83-251-188-53.bredband.comhem.se: ICMP wong-desktop.local udp port 32328 unreachable, length 134
10:11:53.448651 IP wong-desktop.local > ool-18bff397.dyn.optonline.net: ICMP wong-desktop.local udp port 32328 unreachable, length 137
10:11:53.686117 IP wong-desktop.local > 61.135.234.125: ICMP wong-desktop.local udp port 32328 unreachable, length 134
10:11:53.828122 IP wong-desktop.local > pc-164-255-73-200.cm.vtr.net: ICMP wong-desktop.local udp port 32328 unreachable, length 139
These are ICMP packets from your desktop.  Do you have these blocked in your router/firewall?
ICMP packets type 3 code 4 are necessary for the proper function of your network, btw.  ICMP is more than just "ping" - they are important for proper network control and flow.

> 10:11:53.448587 IP ool-18bff397.dyn.optonline.net.16881 > wong-desktop.local.32328: UDP, length 101
10:11:53.828057 IP pc-164-255-73-200.cm.vtr.net.1203 > wong-desktop.local.32328: UDP, length 103
These all are to the same port on your system 32328.  They are then from the same network app as in the first lines, and the
app doing the pinging.  Perhaps a desktop app is checking for updates, etc.

> 10:11:53.060222 IP wong-desktop.local.33505 > cm203-168-223-202.hkcable.com.hk.domain: 21985+ PTR? 68.84.91.211.in-addr.arpa. (43)
This is a DNS lookup from your system.

MrC

---

### Post by afeasfaerw23231233 on 2008-02-28
thanks! i check my router's log page and it shows


here's my netstat -a


here's my tcpdump

here's my router log page

it seems that the 222.xxx.xxx.xxx and 218.xxx.xxx.xxx guys always want to enter my machine

---

### Post by Mr. C. on 2008-02-28
The router/firewall is doing its job.  It is blocking access, and generating a log message.  That's normal.

As you can see, there is plenty of network activity at any given time.  At the time of running netstat, there were no connections to remote hosts (only connections to your own system @ localhost).

You can observer network connections coming and going.  Try this in a command shell:
```

watch -n 1 netstat -a --tcp --udp 
```

Make some network connections via your browser, or email client, or chat client... anything that makes a network connection locally or remotely.  Watch the connections come and go.  Become familiar with the output of netstat and how connections work to better understand your network logs.

MrC

---

### Post by kevdog on 2008-02-28
Good advice Mr. C!

---

