---
title: "Masquerading - Some Clients Can't Access Some Sites"
date: 2014-08-27
forum: Networking &amp; Wireless
---

### Post by david277 on 2014-08-27
[FONT=Verdana]I have a 12.04 box between my cable modem and switch providing NAT. It used to run 10.04 but I recently upgraded it.[/FONT]

[FONT=Verdana]I have a win7 client and a win8 client. Both are now having intermittent problems accessing certain websites. Specifically, *.tumblr.com (and likely others I just haven't tested thoroughly yet)[/FONT]

[LIST]
[*]On the win7 machine, Chrome reports ERR_EMPTY_RESPONSE. Several refreshes and the page will usually load. I tried the same pages in IE and they also don't load but IE gives no useful debugging info.
[*]On the win8 machine, Chrome reports ERR_CONNECTION_RESET for these pages.
[*]These errors are thrown pretty much instantly. There is no time-out.
[*]My android phone can access these sites reliably via Chrome.
[*]I haven't changed the configuration of any of my clients, the only variable is the upgrade to 12.04
[/LIST]
[FONT=Verdana]
Anyone encountered anything like this or have suggestions to narrow down the issue? I've cleared the browser cache of all my browsers, restarted machines, etc to no avail. [/FONT]

Here is some more info:

```
root@dcerouter:~# ifconfig
eth0      Link encap:Ethernet  HWaddr 68:05:ca:24:fa:93
          inet addr:173.230.***.***  Bcast:255.255.255.255  Mask:255.255.255.224
          UP BROADCAST RUNNING MULTICAST  MTU:576  Metric:1
          RX packets:912448 errors:0 dropped:0 overruns:0 frame:0
          TX packets:913597 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:798454932 (798.4 MB)  TX bytes:218882227 (218.8 MB)
          Interrupt:16 Memory:fdec0000-fdee0000


eth1      Link encap:Ethernet  HWaddr 68:05:ca:25:39:0d
          inet addr:192.168.80.1  Bcast:192.168.80.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:120174670 errors:0 dropped:17 overruns:0 frame:0
          TX packets:2732084 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:163535882048 (163.5 GB)  TX bytes:965077753 (965.0 MB)
          Interrupt:16 Memory:fddc0000-fdde0000


lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:132582 errors:0 dropped:0 overruns:0 frame:0
          TX packets:132582 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:15445266 (15.4 MB)  TX bytes:15445266 (15.4 MB)



```

[iptables -L output]("http://paste.ubuntu.com/8161027/")

[iptables -t nat -L output]("http://paste.ubuntu.com/8161019/")

---

### Post by david277 on 2014-08-27
Still some testing to do but I may have solved this by upping MTU on eth0 to 1500

---

