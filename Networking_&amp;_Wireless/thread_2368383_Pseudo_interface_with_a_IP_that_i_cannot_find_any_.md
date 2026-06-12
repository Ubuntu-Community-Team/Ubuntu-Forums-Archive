---
title: "Pseudo interface with a IP that i cannot find any configuration for"
date: 2017-08-10
forum: Networking &amp; Wireless
---

### Post by thawong on 2017-08-10
We have a Ubuntu Server 16.04 server that has one active interface with a ip configured, lets say 10.0.0.1. 
We have found a ip, 10.0.0.2 on the same network that is answering on ping that should not be there and we do not know the origin of it. 
After disconnecting cables to see when ping is failed we can originate it to the same NIC as the 10.0.0.1 one. 
But the interface shows only 10.0.0.1 when issuing ifconfig. How is this possible and has anyone else had the same issue. 
Have looked in /etc/network/interfaces and the only ip configured is 10.0.0.1, no 10.0.0.2.

---

### Post by TheFu on 2017-08-10
Run **ifconfig** to see the configured interfaces and settings on a system.
Run **route** to see which routes and gateways are configured on a system.
Use **ifdown** to remove an interface.

---

### Post by thawong on 2017-08-14
Hi, tanks for the answer but that is done already. As the interfaces eth0  is present but is not configured with the ip that is answering the ping. Again, the server and interface is configured with ip A only. We ping ip B that we do not know what it is for and never configured it as long as i has been here. When we disconnects cable from the interface that the ip A is configured on, ip B is stopping answering the ping. But when issuing ifconfig, only ip A is shown as configured on that specific interface, not ip B that we have pinged and is stopped answering when we disconnects the cable from the interface. Hope its not to confusing. Its a "ghost" ip. Pingable put not configured if you want.

---

### Post by praseodym on 2017-08-14
Whats the name of the interface with that IP?

---

### Post by TheFu on 2017-08-14
> **thawong said:**
> Hi, tanks for the answer but that is done already. As the interfaces eth0  is present but is not configured with the ip that is answering the ping. Again, the server and interface is configured with ip A only. We ping ip B that we do not know what it is for and never configured it as long as i has been here. When we disconnects cable from the interface that the ip A is configured on, ip B is stopping answering the ping. But when issuing ifconfig, only ip A is shown as configured on that specific interface, not ip B that we have pinged and is stopped answering when we disconnects the cable from the interface. Hope its not to confusing. Its a "ghost" ip. Pingable put not configured if you want.

If you don't run those commands AND post the results there, nobody can help.

Anyone can claim they've done something. It helps us to help you, if you can PROVE IT.

Often, the output is misinterpreted and has subtle hints that are missed by someone _in the middle_ of the problem.  Outside eyes are helpful sometimes.

Please use *code tags* (adv reply "#") when posting the cmds + output.

---

### Post by thawong on 2017-08-16
The actual ip of the server is 10.250.43.11. We ping 10.250.43.21 and when disconnecting cable from eth0, 10.250.43.21 stops answering.
Here are the output when running ifconfig:

```

eth0    Link encap:Ethernet  HWaddr 00:1e:c9:ad:48:1a
          inet addr:10.250.43.11  Bcast:10.250.43.255  Mask:255.255.255.0
          inet6 addr: fe80::21e:c9ff:fead:481a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:91831 errors:0 dropped:4053 overruns:0 frame:0
          TX packets:397107 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:24154772 (24.1 MB)  TX bytes:96897734 (96.8 MB)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:197369 errors:0 dropped:0 overruns:0 frame:0
          TX packets:197369 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1
          RX bytes:12891236 (12.8 MB)  TX bytes:12891236 (12.8 MB)

```

This when "route" is used

```

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
default         10.250.43.1     0.0.0.0         UG    0      0        0 eth0
10.250.43.0     *               255.255.255.0   U     0      0        0 eth0

```

This when running "ip link show"

```

1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN mode DEFAULT group default qlen 1
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc mq state UP mode DEFAULT group default qlen 1000
    link/ether 00:1e:c9:ad:48:1a brd ff:ff:ff:ff:ff:ff
3: eth1: <BROADCAST,MULTICAST> mtu 1500 qdisc noop state DOWN mode DEFAULT group default qlen 1000
    link/ether 00:1e:c9:ad:48:1c brd ff:ff:ff:ff:ff:ff
4: eth2: <BROADCAST,MULTICAST> mtu 1500 qdisc noop state DOWN mode DEFAULT group default qlen 1000
    link/ether 00:15:17:75:71:ad brd ff:ff:ff:ff:ff:ff

```

Thanks for looking in to it

---

### Post by TheFu on 2017-08-16
There is only 1 IP on that box according to the posted output.

10.250.43.21 is on a different machine, if you disconnect the cable and it stops.

---

### Post by thawong on 2017-08-23
Yes it is only one IP configured on the server. And that is the wierd thing. When we unplug the ethernet cable that is attached to eth0 on that machine, the ping on 10.250.43.21 stops. It does not stop if we try to disconnect from any other server present in the network. I will create a topology picture with some info so you got the idea and why i am confused.

---

### Post by thawong on 2017-08-23
So here are the situation that i am confused about. Do i miss some basic networking understanding here? This IP, 10.250.43.21 must be something the admin before me configured somewhere on the network. I have not, which explains my lack of knowledge of the origin of the IP. As the ifconfig showed, the only IP on server C is 10.250.43.11, but it still answering on 10.250.43.21.

---

### Post by TheFu on 2017-08-23
Any virtual machines or containers?
Does arp and traceroute show where it comes from?

There isn't any magic with IP.  If there isn't anything showing up in ifconfig, then it isn't configured.  BTW, why didn't ifconfig show the other 2 NICs that are in the system?

Please don't selectively edit things.  IPs aren't sensitive data.

---

### Post by thawong on 2017-08-28
Thank you for the feedback. 

Here is the output shown when running ifconfig together with tracroute and arp. The other two interfaces is disabled and i think that is why it is not shown when running ifconfig. I have got some information running sh arp on our switch that says 10.250.43.21 is a MAC of a DELL brand NIC. The 10.250.43.11 is a dell so i make sense. 

```

user@ubuntu:~$ ifconfig
eth0    Link encap:Ethernet  HWaddr 00:1e:c9:ad:48:1a
          inet addr:10.250.43.11  Bcast:10.250.43.255  Mask:255.255.255.0
          inet6 addr: fe80::21e:c9ff:fead:481a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1209246 errors:0 dropped:54723 overruns:0 frame:0
          TX packets:3776706 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:389514759 (389.5 MB)  TX bytes:916062594 (916.0 MB)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:2660627 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2660627 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1
          RX bytes:171966234 (171.9 MB)  TX bytes:171966234 (171.9 MB)

user@ubuntu:~$ traceroute 10.250.43.21
traceroute to 10.250.43.21 (10.250.43.21), 30 hops max, 60 byte packets
 1  10.250.43.11 (10.250.43.11)  2999.451 ms !H  2999.433 ms !H  2999.426 ms !H
user@ubuntu:~$ arp
Address                  HWtype  HWaddress           Flags Mask            Iface
10.250.43.15  ether   00:24:e8:43:ff:47                  C                     eth0
10.250.43.13  ether   00:15:5d:32:56:00                 C                     eth0
10.250.43.2   ether   20:bb:c0:4d:ea:c5                 C                     eth0
10.250.43.21                (incomplete)                                            eth0
10.250.43.12  ether   bc:30:5b:ce:f2:e8                 C                     eth0
10.250.43.10  ether   00:15:c5:ee:5b:f2                 C                     eth0
10.250.43.1   ether   54:a2:74:27:95:ee                 C                     eth0
user@ubuntu:~$


```

---

### Post by thawong on 2017-08-28
And no, no virtual machines or containers is present

---

### Post by TheFu on 2017-08-28
10.250.43.21                (incomplete)                                            eth0

Says that the machine isn't on the network anymore.  1 NIC = 1 MAC.  If the MAC isn't identical, then it is a different NIC.  There can be 500+ IPs on a single NIC, but the MAC would be the same.

Saying "it is a Dell on a network" is like saying "he's Japanese" when visiting Japan.  It is likely true, but because lots of Japanese people are in Japan, it is hardly proof.

Was there a guest on the network recently who has left?

---

### Post by thawong on 2017-08-29
Thanks fo the help

---

### Post by TheFu on 2017-08-29
Solved?  What was it?

---

### Post by thawong on 2017-08-29
Not solved. The Dell server is still answering on ping 10.250.43.21 on eth0 even if it is not configured.

---

