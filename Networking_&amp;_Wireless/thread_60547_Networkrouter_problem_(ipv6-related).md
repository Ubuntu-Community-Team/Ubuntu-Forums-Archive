---
title: "Network/router problem (ipv6-related?)"
date: 2005-08-28
forum: Networking &amp; Wireless
---

### Post by tomsecret on 2005-08-28
Hi all

When I start ubuntu it successfully connect to ntp-server to set time, but when I boot into X/Gnome, it seems like the Internet-connection is lost.  Turning my router off and then on again solves the problem.  In my dmesg I see this message: 

eth0: no IPv6 routers present

Is it possible to disable IPv6, so ubuntu uses IPv4 when connecting to the router?

Regards, 
Tom

---

### Post by evilghost on 2005-08-28
Yes, disable ipv6.  As a matter of fact, ipv6 is a big culprit for random DNS failure and sporadic connectiivty issues when running on an ipv4 network.

To disable ipv6:
```

sudo gedit /etc/modprobe.d/aliases
[Find the line that says "alias net-pf-10 off ipv6" and change it to "alias net-pf-10 off"]
[Save the file]
[Reboot]

```

---

### Post by tomsecret on 2005-08-29
Thanks alot evilghost, I'll try that  :)

---

### Post by tomsecret on 2005-08-29
Ok I did what you said, but couldn't find a line that matched your exactly.  I found this line though: 
"alias net-pf-10 ipv6" 
and changed it to
"alias net-pf-10 off"

So after this Gaim (msn/irc) works without switching the router off/on, and other computers on the network doesn't get disconnected anymore, but I can't ping www-servers (and I can't connect to them either).  Also the network seemed very slow (filetransfer in Gaim/msn).  After switching the router off/on, www also works however.  Any further suggestions?

Thanks O:)

---

### Post by evilghost on 2005-08-29
Wireless, or hard-wired?

What's /etc/resolv.conf look like?

Can you post your output of:

ifconfig
 [and]
cat /etc/resolv.conf

---

### Post by Rheve on 2005-08-30
Hi,

I have the same issue with WWW servers.
I found this [http://www.ubuntuguide.org/#loadwebsitefasterfirefox](http://www.ubuntuguide.org/#loadwebsitefasterfirefox)

In short: 
   1. Applications -> Internet -> Firefox Web Browser
   2. Mozilla Firefox
   3. Address Bar -> about:config
Filter: ->
**network.dns.disableIPv6 -> true**
network.http.pipelining -> true
network.http.pipelining.maxrequests -> 8
network.http.proxy.pipelining -> true

   4. Restart Mozilla Firefox

Didn't had time to test it yet.

---

### Post by tomsecret on 2005-08-30
The connection is hard-wired.

Here is the output of ifconfig and cat /etc/resolv.conf

```

root@ubuntu:/ # ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0C:6E:7D:69:7D
          inet addr:192.168.2.100  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::20c:6eff:fe7d:697d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:855 errors:0 dropped:0 overruns:0 frame:0
          TX packets:536 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:420198 (410.3 KiB)  TX bytes:73130 (71.4 KiB)
          Interrupt:22 Base address:0x8000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1094 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1094 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:98662 (96.3 KiB)  TX bytes:98662 (96.3 KiB)

root@ubuntu:/ # cat /etc/resolv.conf
nameserver 192.168.2.1

```

This is from after I switch the router off/on, but it's the same output before.  The router is a SMC Barricade 7004 VBR Router.

Thanks!

---

### Post by tomsecret on 2005-08-30
[QUOTE=Rheve]Hi,

I have the same issue with WWW servers.
I found this [http://www.ubuntuguide.org/#loadwebsitefasterfirefox](http://www.ubuntuguide.org/#loadwebsitefasterfirefox)

In short: 
   1. Applications -> Internet -> Firefox Web Browser
   2. Mozilla Firefox
   3. Address Bar -> about:config
Filter: ->
**network.dns.disableIPv6 -> true**
network.http.pipelining -> true
network.http.pipelining.maxrequests -> 8
network.http.proxy.pipelining -> true

   4. Restart Mozilla Firefox

Didn't had time to test it yet.[/QUOTE]

Thanks Rheve, but that can't be the solution for me as I don't use Firefox (I prefer Opera), and this affects all parts of the network (altough gaim is able to connect). I also think your description is for speeding up mozilla, so it probably works in the first place :)

Tom

---

### Post by tomsecret on 2005-09-06
anyone?

---

