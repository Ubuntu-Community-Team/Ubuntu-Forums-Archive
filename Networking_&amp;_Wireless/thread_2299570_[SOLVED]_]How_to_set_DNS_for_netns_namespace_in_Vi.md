---
title: "[SOLVED] ]How to set DNS for netns namespace in Vivid?"
date: 2015-10-19
forum: Networking &amp; Wireless
---

### Post by lambdafox on 2015-10-19
I am trying out / experimenting with network name spaces, to try running different applications on eth0 and eth1 in my system.  I do sudo su, before doing these.

```
#create netns
ip netns add myNamespace
#link iface to netns
ip link set eth1 netns myNamespace
#set ip address in namespace
ip netns exec myNamespace ifconfig eth1 192.168.0.101/24 up
#set loopback (may be needed by process run in this namespace)
ip netns exec myNamespace ifconfig lo 127.0.0.1/8 up
#set route in namespace
ip netns exec myNamespace route add default gw 192.168.0.1
#force firefox to run inside namespace (using eth1 as outgoing interface and the route)
ip netns exec myNamespace firefox
```

firefox opens, but cannot access any website and demonstrates the usual lack of a good dns.  

I found this, but it does not seem to work.  I am pretty sure this is because of updates to Ubuntu that have made the approach deprecated.

I created a folder /etc/netns
I created a folder /etc/netns/MyNamespace

I created /etc/netns/MyNamespace/resolv.conf with one line in it:

nameserver 209.222.18.222

Do I need to put the DNS server for this namespace somewhere else with Xubuntu Vivid amd64?

Thank you.

---

### Post by lambdafox on 2015-10-19
ok, stupid newbie, bad newbie, go sit in the corner!

my local network is 192.168.1, NOT 192.168.0

Changing those seems to fix my problem [CENTER][COLOR=#000000]:eek:


[/COLOR][/CENTER]

---

