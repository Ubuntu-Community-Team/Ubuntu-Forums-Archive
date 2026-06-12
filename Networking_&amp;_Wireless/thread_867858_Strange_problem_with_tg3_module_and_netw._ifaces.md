---
title: "Strange problem with tg3 module and netw. ifaces"
date: 2008-07-23
forum: Networking &amp; Wireless
---

### Post by Nonplay on 2008-07-23
Hi all,

I installed ubuntu 8.04 on a Optiplex 330 Dell but I had some
problem with the cabled network interface statically configured.

I needed to install manually the latest drivers for
Broadcom NetXtreme 57xx Gigabit using tg3 modules.

The interface seems correctly configured in /etc/network/interfaces and all the tools 
provided by the drivers (such as using ethtools) can query and configure correctly the interface.

But I can't get connected!
When I try to ping (as user and as root) an ip-address 
I get that "The network is unreachable".

The strange thing is that when I try to ping - ONLY AS ROOT - an internet ip specifing the network interface it works.

For example when I run
```
sudo ping 209.85.129.147 -I eth0
```
Any ideas?
Thanks to everyone!

ps.
The file /etc/network/interfaces already had the line
```
auto eth0
```
and when I launch "sudo ifup eth0" I get "failed to bring up eth0"

---

