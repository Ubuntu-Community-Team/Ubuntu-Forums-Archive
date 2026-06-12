---
title: "Can't reach from server one specific (only one) IP in remote network."
date: 2016-04-04
forum: Networking &amp; Wireless
---

### Post by druzenko on 2016-04-04
Can't reach from server one specific (only one) IP in remote network.
Don't have any routing settings for that IP! 
It is not permanent problem. 
At the morning everything was Ok.
But disconnected remote router for a few minutes create this strange situation.

Server has 2 IPs.
Main function for this server is "mail server".


Local configuration:
[FONT=courier new]**# cat /etc/issue**
Ubuntu 14.04.4 LTS \n \l
[B]
#ifconfig[/B]
eth0      Link encap:Ethernet  HWaddr 00:1e:c9:ac:d2:1e
          inet addr:192.168.8.14  Bcast:192.168.15.255  Mask:255.255.248.0
                    
eth1      Link encap:Ethernet  HWaddr 00:1e:c9:ac:d2:20
          inet addr:12.12.12.233  Bcast:12.12.12.239  Mask:255.255.255.240[/FONT]
          
**[FONT=courier new]#route -n[/FONT]**
[FONT=courier new]Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         12.12.12.225    0.0.0.0         UG    0      0        0 eth1
192.168.0.0     192.168.8.4     255.255.248.0   UG    0      0        0 eth0
192.168.8.0     0.0.0.0         255.255.248.0   U     0      0        0 eth0
12.12.12.224    0.0.0.0         255.255.255.240 U     0      0        0 eth1
          [/FONT]
          
My network has 2 Routers:
    192.168.8.4
    192.168.8.109
Router 192.168.8.4 is cisco router to anoter network 
(remote router On Serial0/0 -- 192.168.0.4)

-[cut]-
ip route 0.0.0.0 0.0.0.0 192.168.8.109
ip route 192.168.0.0 255.255.248.0 192.168.0.4
ip route 192.168.0.4 255.255.255.255 Serial0/0
-[cut]-


Router 192.168.8.109 - Firebox X Edge - Gateway to internet for some computers.
Has routing:
    network - 192.168.0.0/21 Gateway - 192.168.8.4

Default gateway for ALL workstations in local network is 192.168.8.4 in remote network - 192.168.0.4

Problem on "mail server" side looks like this:
[FONT=courier new]**# traceroute -n 192.168.0.182**
traceroute to 192.168.0.182 (192.168.0.182), 30 hops max, 60 byte packets
 1  192.168.8.109  1.114 ms  1.474 ms  1.810 ms
 2  * * *
 3  * * *
 4  * * *
 5  * * *
 6  * * *
 7  *^C[/FONT]

But at the same time:
[FONT=courier new]**# traceroute -n 192.168.0.168**
traceroute to 192.168.0.168 (192.168.0.168), 30 hops max, 60 byte packets
 1  192.168.8.4  2.324 ms  3.126 ms  4.060 ms
 2  192.168.0.4  5.671 ms  8.435 ms  11.405 ms
 3  192.168.0.168  6.834 ms  7.577 ms  8.075 ms
[/FONT]
I think that working some routing protocols.
But don't have any ideas how detect/fix it.
 Can You, please, suggest what tool to use to see "Real routing" and from where it comes.
 Thank you.

---

