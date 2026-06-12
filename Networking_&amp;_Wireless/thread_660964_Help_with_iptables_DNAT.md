---
title: "Help with iptables DNAT"
date: 2008-01-07
forum: Networking &amp; Wireless
---

### Post by jmvidalvia on 2008-01-07
As a first step, I am trying to use vncviewer through a server, within my LAN.
If I get it working, I will try to use it over Internet, but first I need to solve it to work locally.
I am trying to keep it simple, so by now, everything is open in the firewall, have only one network interface, and my server is just pluged in the network as an ordinary machine.
Here's my iptables script:

```
#!/bin/sh

iptables -F
iptables -X
iptables -Z
iptables -t nat -F

iptables -P INPUT ACCEPT
iptables -P OUTPUT ACCEPT
iptables -P FORWARD ACCEPT
iptables -t nat -P PREROUTING ACCEPT
iptables -t nat -P POSTROUTING ACCEPT

iptables -t nat -A PREROUTING -p tcp -d 192.168.0.1 --dport 6000 -j DNAT --to 192.168.0.2:5900
echo 1 > /proc/sys/net/ipv4/ip_forward

```

192.168.0.1 is a Linux server without Xserver
192.168.0.2 is a Windows box with vnc service open in port 5900
192.168.0.3 is my laptop, with Edgy.

What I am trying to do is pointing to the server to get a vnc connection with a local machine, instead of pointing directly to that machine.

From my laptop I do:
```
$vncviewer 192.168.0.1:6000

```
and:
1- When 192.168.0.2 box is closed, I get an answer of no available host.
2- When 192.168.0.2 box is open, **nothing happens, no sign, just keep waiting**.

Obviously, when I do:
```
$vncviewer 192.168.0.2:5900

```
then I get a prompt for the remote password and everything works.

Probably I am missing something important, as I amb pretty newbie in this kind of iptables issues.
¿does anyone have any Idea about if this I am trying is possible and if there is anything I should ammend?
Thanks a lot!

---

