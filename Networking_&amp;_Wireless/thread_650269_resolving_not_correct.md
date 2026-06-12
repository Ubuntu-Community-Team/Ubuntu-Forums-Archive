---
title: "resolving not correct"
date: 2007-12-26
forum: Networking &amp; Wireless
---

### Post by GoldWing on 2007-12-26
```
root@vm:/etc/apt/apt.conf.d# ping www.google.be
ping: unknown host www.google.be
root@vm:/etc/apt/apt.conf.d# wget www.google.be
--11:53:58--  http://www.google.be/
           => `index.html'
Connecting to 172.18.20.5:8080... connected.
Proxy request sent, awaiting response... 200 OK
Length: unspecified [text/html]

    [ <=>                                 ] 6,074         --.--K/s

11:53:58 (2.10 MB/s) - `index.html' saved [6074]
```
What am I doing wrong ?
```
root@vm:/etc/apt/apt.conf.d# cat /etc/resolv.conf
search ncts-co.priv
nameserver 192.168.10.50
nameserver 192.168.10.80
```
```
root@vm:/etc/apt/apt.conf.d# set |grep prox
http_proxy=http://172.18.20.5:8080/
proxy=http://172.18.20.5:8080/
```

---

### Post by dnvikram on 2007-12-26
Post the output of the routing table using the command below:

/sbin/route -n

The proxy details you have posted are not relevant here as its for http proxy serving.

Post the output of, "ifconfig" also.

Also describe the setup you have on your machine to access the internet.

---

### Post by GoldWing on 2007-12-26
```
root@vm:~# route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.10.0    0.0.0.0         255.255.255.0   U     0      0        0 eth1
0.0.0.0         192.168.10.1    0.0.0.0         UG    0      0        0 eth1
root@vm:~# ifconfig
eth1      Link encap:Ethernet  HWaddr 00:50:56:AB:2E:FF
          inet addr:192.168.10.100  Bcast:192.168.10.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:feab:2eff/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:499517 errors:0 dropped:0 overruns:0 frame:0
          TX packets:47796 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:85169411 (81.2 MiB)  TX bytes:3629357 (3.4 MiB)
          Interrupt:177 Base address:0x1400

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:14 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:800 (800.0 b)  TX bytes:800 (800.0 b)

root@vm:~# cat /etc/resolv.conf
search ncts-co.priv
nameserver 192.168.10.50
nameserver 192.168.10.80
root@vm:~#
```
I am using a fix IP.
the 2 nameservers are windows DNS
the gateway is a router/firewall.

---

### Post by dnvikram on 2007-12-26
Try adding the line below in your /etc/resolv.conf.

nameserver **IP.of.your.GATEWAY**

---

### Post by GoldWing on 2007-12-26
no luck.

---

