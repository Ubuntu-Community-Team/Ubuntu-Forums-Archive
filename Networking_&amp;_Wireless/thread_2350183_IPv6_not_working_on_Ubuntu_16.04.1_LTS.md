---
title: "IPv6 not working on Ubuntu 16.04.1 LTS"
date: 2017-01-22
forum: Networking &amp; Wireless
---

### Post by jane94539 on 2017-01-22
IPv6 is mysteriously not working on my Ubuntu desktop!

Here is my setup:
Ubuntu desktop <-> DDWRT router <-> Comcast cable modem 

Comcast cable modem has IPv6 support enabled for Both (Stateless/Stateful) configs.

DDWRT router successfully receives IPv6 and I am able to ping6 ipv6.google.com from router shell successfully.
The DDWRT IPv6 tab config is:
> IPv6: Enabled
IPv6 type: DHCPv6 with prefix delegation
Prefix Length: 64
Static DNS 1: 2001:4860:4860::8888
Static DNS 2: 2001:4860:4860::8844
Radvd: Enabled
(all other options are disabled)

On my Ubuntu 16.04.1 LTS I have the following in /etc/network/interfaces file:

# The primary network interface
> 
auto p8p1

iface p8p1 inet6 auto


Upon restart I do get an IPv6 global scope address:
> 
> ifconfig
p8p1      Link encap:Ethernet  HWaddr <REMOVED>
          inet addr:192.168.11.100  Bcast:192.168.11.255  Mask:255.255.255.0
          inet6 addr: XXXX:641:c000:37ff:428d:5cff:fe54:f945/64 Scope:Global
          inet6 addr: YYYY::428d:5cff:fe54:f945/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:101647 errors:0 dropped:78 overruns:0 frame:0
          TX packets:85408 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:95261039 (95.2 MB)  TX bytes:8774809 (8.7 MB)
          Memory:df100000-df11ffff 


However I am not able to use IPv6 to reach any external host.
E.g. "ping6 google.com" simply hangs.




IP tables don't have any rules that would interfere:
> 
> ip6tables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination      


Any ideas what could be wrong with my setup?

---

### Post by Hadaka on 2017-01-22
Hi, here is a link that may help, the  /etc/network/interfaces
file may need adjusting..
IPv6
[https://ubuntuforums.org/showthread.php?t=2219725](https://ubuntuforums.org/showthread.php?t=2219725)
[http://askubuntu.com/questions/566255/how-to-configure-etc-network-interface-to-use-static-ipv6-but-dynamic-ipv4](http://askubuntu.com/questions/566255/how-to-configure-etc-network-interface-to-use-static-ipv6-but-dynamic-ipv4)
IPv4
[http://askubuntu.com/questions/464507/ubuntu-14-04-server-wifi-wpa2-personal/464552#464552](http://askubuntu.com/questions/464507/ubuntu-14-04-server-wifi-wpa2-personal/464552#464552)

or are you using Network Manager ?
hope this helps.

---

