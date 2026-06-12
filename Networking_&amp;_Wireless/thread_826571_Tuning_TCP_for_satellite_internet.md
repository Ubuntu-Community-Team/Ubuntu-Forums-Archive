---
title: "Tuning TCP for satellite internet"
date: 2008-06-12
forum: Networking &amp; Wireless
---

### Post by reuben on 2008-06-12
Hi,

I realize this is probably not the exact forum for this, but hopefully there's somebody around with the knowledge I need :)

I'm staying at my girlfriend's place in the mountains where the only available internet is via a dish (i.e. satellite/microwave/radio, I don't know the exact tech.) I get 968k down, 96k up. When I'm downloading files, watching video, etc, it performs beautifully; when I'm loading web pages with 40 or 50 separate HTTP requests, it's pretty laggish. Somebody at work suggested that I could tune the TCP settings to get around this.

Questions:

1) Since I'm connecting to a router (which in turn is connected to a link) should I tune at my laptop or at the router, or both? The router has a standard linksys admin webapp (I'd like to put ddwrt or something on there, but one step at a time) and there don't seem to be to many options.

2) On my laptop, the relevant settings are as follows:
reubenf@travel:~$ cat /proc/sys/net/core/wmem_max
131071
reubenf@travel:~$ cat /proc/sys/net/core/rmem_max
131071
What is more appropriate for the bandwidth as I described above?

Thanks!

---

### Post by Kebabman on 2008-06-12
Hi Reuben,

It may well help if you change the congestion control mechanism that TCP is using. The main problem with satellite links is the high Bandwidth Delay Product of the link and the standard 'cubic' congestion control mechanism is biased against such links and will reduce TCP's window size because of it.

If you use the 'hybla' algorithm it will not do this and will try to keep the window size large in order to better make use of the available bandwidth.

The congestion control algorithm being used can be changed by changing the net.ipv4.tcp_congestion_control sysctl variable (on kernels 2.6.13 and later I believe). To get a list of available congestion control algorithms you can use the following command :

sysctl net.ipv4.tcp_available_congestion_control

If that list does not include hybla then unfortunately you will need to recompile your kernel in order to build support in. If it does however you can simply run :

sudo sysctl -w net.ipv4.tcp_congestion_control=hybla

Which will alter TCP to use thy hybla algorithm.

If hyble is not built into your kernel and you wish to enable it you can find it in the following section of the kernel configuration using menuconfig/xconfig :

Networking   --->
Networking options   --->
TCP: advanced congestion control   --->
TCP congestion control   --->

If you do this please let me know how you get on, I would be interested to know. Hope this helps.

---

### Post by netztier on 2008-06-12
> **reuben said:**
> H
Questions:

1) Since I'm connecting to a router (which in turn is connected to a link) should I tune at my laptop or at the router, or both? 


The router as such has no notion of TCP flow control, and does not care about it. It'll translate IP addresses and where needed source and destination TCP ports, and that's where it stops it's packet mangling. So tuning has to be done on the end system.

I think that instead of tuning rmem and wmem, choosing a different algorithm might be more efficient, so I'd second kebabman in his suggestion to use another basic setting.


regards

Marc

---

