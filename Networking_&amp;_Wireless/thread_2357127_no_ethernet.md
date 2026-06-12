---
title: "no ethernet"
date: 2017-03-30
forum: Networking &amp; Wireless
---

### Post by brownbear on 2017-03-30
I recently upgraded from 14.04 to 16.04 and graphics and networking seems to have broken. For now, I'd like to get networking back. 

What can I run to help diagnose what's wrong? Also note, I'm typing these results out manually so there might be a few typos. 

```

$ uname -a  
3.19.0-80-generic

```

# I have four devices in this command, the two ethernet sounding ones are:
```

$ ip a
wlan0 <NOCARRIER, BROADCAST, MULTICAST, UP> mtu 1500 qdisc mq state DOWN group default qlen 1000
 ... 
enx00249b17dbfb: <BROADCAST, MULTICAST> mtu 1500 qdisc noop state DOWN group default qlen 1000
 ... 

```

```

$ dmesg | grep eth
7.38xxx enx00249b17dbfb: renamed from eth0

```

```

$ sudo lshw -C network
*-network
    description Wireless
    ...
*-network DISABLED
   description Ethernet interface
   logical name: enx00249b17dbfb

```
This command enabled the ethernet device:
```

$ sudo ifconfig enx00249b17dbfb up

```

Now this is the state of lshw
```

$ sudo lshw -C network
*-network
   description: Ethernet interface
   physical id: 2
   logical name: enx00249b17dbfb
   ...
   capabilities: ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
   configuration: autonegotiation=on broadcast=yes driver=r8152 driverversion=v1.07.0 (2014/10/09) duplex=full link=yes multicast=yes port=MII speed=100Mbit/s

```
```

$ ip route get 8.8.8.8
RTNETLINK answer: Network is unreachable

```

---

### Post by vasa1 on 2017-03-30
Please post terminal content within code tags. Thanks!

---

### Post by brownbear on 2017-03-30
```

$ sudo /etc/init.d/networking restart
Restarting networking (via systemctl) networking-serviceJOb for networking fails because the control process exited with error code: See systemctl status networking.service and journalctl -xe for details

```

```

systemctl status networking.service
...
Drop in /run/systemd/generator/networking.service.d
50-insserv.conf-$network.conf
Process: 3361 ExecStart=/sbin/ifup -a --read-environment (code=exited status=1/FAILURE)

```

I changed my /etc/network/interfaces to just include this and have the other interfaces hopefully depend on dhcp to work properly. 

```

auto lo
iface lo inet loopback

```


And now I can successfully restart my networking:
```

sudo /etc/init.d/networking restart
[ ok ]

```

However internet still not working via ethernet.

```

nslookup google.com
;; connection timed out; no servers could be reached

```

```

ping localhost
icmp open socket: Operation not permitted

```

```

sudo ping localhost
64 bytes from localhost (127.0.0.1) icmp_seq=1 ttl=64 time=0.070ms
... 

```

```

sudo lspci -v
... 
3a:00.0 Network controller: Intel Corporation Wireless 8260 (rev 3a)
  Subsystem: Intel Corporation Wireless 8260
  ..
  Kernel driver in use: iwlwifi
  Kernel modules: iwlwifi
...


```

```

sudo dhclient enx00249b17dbfb
RTNETLINK answers: FILE exists

```

I managed to get it working. 

I was missing my eth config in my /etc/network/interfaces. Once that was added I could resolve an IP address and everything started to work. 

Then going through the normal ubuntu-update mechanism fixed all my graphics issues.

Feel free to close this thread.

---

### Post by wildmanne39 on 2017-03-30
To mark the thread solved use thread tools at the top of the page.
Thanks

---

