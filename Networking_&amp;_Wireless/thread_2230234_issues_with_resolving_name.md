---
title: "issues with resolving name"
date: 2014-06-18
forum: Networking &amp; Wireless
---

### Post by MacUsers on 2014-06-18
Dear all,

Getting a strange result with resolving name: It's a VBox VM, provisioned by Vigrant, running 12.04 server.  
[FONT=courier new]ping[/FONT], [FONT=courier new]telnet[/FONT], [FONT=courier new]curl [/FONT]can resolve the name easily:

```
[FONT=courier new]root@puppet:~# hostname -f
puppet.internal
#
root@puppet:~# ping -c2 puppet.internal
PING puppet.internal (127.0.1.1) 56(84) bytes of data.
64 bytes from puppet.internal (127.0.1.1): icmp_req=1 ttl=64 time=0.028 ms
64 bytes from puppet.internal (127.0.1.1): icmp_req=2 ttl=64 time=0.040 ms

--- puppet.internal ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1000ms
rtt min/avg/max/mdev = 0.028/0.034/0.040/0.006 ms[/FONT]
```

but [FONT=courier new]nslookup[/FONT] cannot:

```
[FONT=courier new]root@puppet:~# nslookup $(hostname -f)
Server:        10.0.2.3
Address:    10.0.2.3#53

** server can't find puppet.internal: NXDOMAIN[/FONT]
```

this is my [FONT=courier new]/etc/hosts[/FONT] file:

```
[FONT=courier new]root@puppet:~# awk '! /^(#|$)/ {print}' /etc/hosts
127.0.0.1    localhost
127.0.1.1    puppet.internal    puppet
::1        ip6-localhost    ip6-loopback
fe00::0    ip6-localnet
ff00::0    ip6-mcastprefix
ff02::1    ip6-allnodes
ff02::2    ip6-allrouters[/FONT]
```

Anyone got a clue? Best!!

---

### Post by TheFu on 2014-06-18
nslookup follows DNS  - doesn't check the /etc/hosts file.  Also, it is deprecated on Linux, use **dig** instead, though that will NOT work differently.  The /etc/nsswitch.conf file controls the order of name resolution to the OS.

I use **ping** to see that the OS thinks is an IP for a machine.
If you don't run a DNS server internally, then every internal machine will need to have the /etc/hosts file managed too.  I like ansible for this, but if you only have LT 5 machines, that is more overhead than it is worth.

---

