---
title: "Ethernet not working on Lubuntu, NetworkManager acting strangely"
date: 2016-03-28
forum: Networking &amp; Wireless
---

### Post by Noah_Overcash on 2016-03-28
I have an ethernet cable running from my router into my desktop, and NetworkManager is not working with the connection.  It shows a Wired Connection and can connect, however the internet is unreachable.  The Ifupdown (eth0) interface, when connected, is connectable with reachable internet for about 30 seconds, then it is disconnected and reverts back to Wired Connection.  The connection works fine on other computers, and a Live CD on the same box.

sudo lshw -C network
```
[FONT=Menlo]  *-network               [/FONT]
[FONT=Menlo]       description: Ethernet interface[/FONT]
[FONT=Menlo]       product: NetLink BCM57781 Gigabit Ethernet PCIe[/FONT]
[FONT=Menlo]       vendor: Broadcom Corporation[/FONT]
[FONT=Menlo]       physical id: 0[/FONT]
[FONT=Menlo]       bus info: pci@0000:03:00.0[/FONT]
[FONT=Menlo]       logical name: eth0[/FONT]
[FONT=Menlo]       version: 10[/FONT]
[FONT=Menlo]       serial: d0:50:99:13:1d:4e[/FONT]
[FONT=Menlo]       size: 100Mbit/s[/FONT]
[FONT=Menlo]       capacity: 1Gbit/s[/FONT]
[FONT=Menlo]       width: 64 bits[/FONT]
[FONT=Menlo]       clock: 33MHz[/FONT]
[FONT=Menlo]       capabilities: pm msi msix pciexpress bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation[/FONT]
[FONT=Menlo]       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.137 duplex=full firmware=sb ip=192.168.1.94 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s[/FONT]
[FONT=Menlo]       resources: irq:16 memory:f0010000-f001ffff memory:f0000000-f000ffff memory:f7d00000-f7d007ff[/FONT]

```

lspci | grep Ethernet
```

[FONT=Menlo]03:00.0 Ethernet controller: Broadcom Corporation NetLink BCM57781 Gigabit Ethernet PCIe (rev 10)[/FONT]

```

ifconfig (while on ifupdown (eth0))
```
eth0      Link encap:Ethernet  HWaddr d0:50:99:13:1d:4e            inet addr:192.168.1.94  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::d250:99ff:fe13:1d4e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:15766 errors:0 dropped:17 overruns:0 frame:0
          TX packets:1781328 errors:30 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3105871 (3.1 MB)  TX bytes:1652028544 (1.6 GB)
          Interrupt:16 


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:7193138233 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7193138233 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:359660262053 (359.6 GB)  TX bytes:359660262053 (359.6 GB)


teredo    Link encap:UNSPEC  HWaddr 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00  
          inet6 addr: 2001:0:53aa:64c:2cc8:3e11:5d1b:97a3/32 Scope:Global
          inet6 addr: fe80::ffff:ffff:ffff/64 Scope:Link
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1280  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:500 
          RX bytes:0 (0.0 B)  TX bytes:144 (144.0 B)

```

ifconfig (while on Wired Connection)
```
eth0      Link encap:Ethernet  HWaddr d0:50:99:13:1d:4e            inet addr:10.42.0.1  Bcast:10.42.0.255  Mask:255.255.255.0
          inet6 addr: fe80::d250:99ff:fe13:1d4e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:65203 errors:0 dropped:42 overruns:0 frame:0
          TX packets:5287600 errors:89510 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:7282719 (7.2 MB)  TX bytes:4829757776 (4.8 GB)
          Interrupt:16 


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:8938774283 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8938774283 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:446942667604 (446.9 GB)  TX bytes:446942667604 (446.9 GB)


teredo    Link encap:UNSPEC  HWaddr 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00  
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1280  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:500 
          RX bytes:0 (0.0 B)  TX bytes:144 (144.0 B)

```

ls -la /etc/resolvonf/resolv.conf.d/
```
total 12drwxr-xr-x 2 root root 4096 Dec 13 20:57 .
drwxr-xr-x 5 root root 4096 Dec 13 20:57 ..
-rw-r--r-- 1 root root    0 Oct 10  2014 base
-rw-r--r-- 1 root root  151 Oct 10  2014 head

```

cat /etc/resolv.conf
```
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 127.0.1.1
search gateway.pace.com

```

cat /etc/network/interfaces
```
# interfaces(5) file used by ifup(8) and ifdown(8)auto lo
iface lo inet loopback
auth eth0
iface eth0 inet dhcp

```

---

### Post by papibe on 2016-03-28
Hi Noah_Overcash.

/etc/network/interfaces should not have the dhcp line
```
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

```
delete that, restart and let us know how it goes.
Regards.

---

### Post by Noah_Overcash on 2016-03-29
Now only Wired Connection is shown, and firefox, chrome, and ping are showing no connection

---

### Post by papibe on 2016-03-30
Could you run these commands, and paste back the results?
```
cat /etc/resolv.conf 

route -n

ifconfig

nm-tool 

nslookup ubuntu.com

dig ubuntuforums.org
```
Regards.

---

### Post by Noah_Overcash on 2016-03-30
Apologies, the newlines were messed up, here it is again:
cat /etc/resolv.conf
```

# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 127.0.1.1
search gateway.pace.com

```
route -n
```

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.42.0.0       0.0.0.0         255.255.255.0   U     100    0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0

```
ifconfig
```

eth0      Link encap:Ethernet  HWaddr d0:50:99:13:1d:4e  
          inet addr:10.42.0.1  Bcast:10.42.0.255  Mask:255.255.255.0
          inet6 addr: fe80::d250:99ff:fe13:1d4e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:126186 errors:0 dropped:0 overruns:0 frame:0
          TX packets:502 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:8762950 (8.7 MB)  TX bytes:89467 (89.4 KB)
          Interrupt:16 


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:5368627126 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5368627126 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:268460496963 (268.4 GB)  TX bytes:268460496963 (268.4 GB)


teredo    Link encap:UNSPEC  HWaddr 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00  
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:500 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)



```
nm-tool
```


```
nslookup ubuntu.com
```

;; connection timed out; no servers could be reached



```
dig ubuntuforums.org
```



; <<>> DiG 9.9.5-11ubuntu1.3-Ubuntu <<>> ubuntuforums.org
;; global options: +cmd
;; connection timed out; no servers could be reached

```

Also, the network is assigning IP addresses of 192.168.1.* not 10.42.0.*

---

### Post by roachk71 on 2016-03-30
If your **/etc/network/interfaces** script has been copied and pasted as it appears here, it appears that *auto lo *for the loopback interface is on the wrong line, and may be causing the erratic behavior you've mentioned. Try moving that directive to the line below and see if it recurs after a reboot.

---

### Post by Noah_Overcash on 2016-03-30
It is as follows, I believe it had an error copying:
```

# interfaces(5) file used by ifup(8) and ifdown(8)
auth lo
iface lo inet loopback

```

---

### Post by papibe on 2016-03-30
I see you don't have a default route and may be not DNS either.

Could you open 'Network Connections' to check if you have entries there?

If not create a wired one, and make sure that:
[LIST]
[*]'Automatically connect to this network when available' and 'All users may connect to this network' are checked.
[*]The IPv4 Method is set to 'Automatic (DHCP)'
[/LIST]
Regards.

---

### Post by Noah_Overcash on 2016-03-30
Network Connections has a "Wired Connection 1" under the Ethernet section, only other things are Wi-Fi with old wifi networks back when this box had a wi-fi adapter
I will try creating a connection and let you know how that goes

---

### Post by Noah_Overcash on 2016-03-31
It works now, thank you
Creating the new connection solved the problem

---

### Post by papibe on 2016-03-31
Great! :D

When you have the chance, please mark the thread as solved ([here]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads")'s how to do it).

Regards.

---

