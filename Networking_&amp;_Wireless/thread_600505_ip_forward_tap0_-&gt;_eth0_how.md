---
title: "ip_forward tap0 -&gt; eth0 how?"
date: 2007-11-02
forum: Networking &amp; Wireless
---

### Post by moxen93 on 2007-11-02
Hello everyone,

I am trying to  set up a openvpn connection between my workplace (local 10.196.32.19) and my Ubuntu7.10-homeserver (local 192.168.1.20). The tunnel is functioning over internet from my workplace / tap0 (10.0.0.2) to my Ubuntu7.10-homeserver / tap0 (10.0.0.1). I can ping and ssh from one to the other and vice versa. But when I try to ping or ssh with another homecomputer to the workplace via the  Ubuntu7.10-homeserver then it does not ip_forward.

homecomputer (192.168.1.205) -> Ubuntu7.10-homeserver (eth0=192.168.1.20 and tap0=10.0.0.1)  ... -> internet -> .. workplace (eth0=10.196.32.19 and tap0=10.0.0.2)
->does not work directly:
homecomputer$: ping 10.0.0.1
PING 10.0.0.1 (10.0.0.1): 56 data bytes
64 bytes from 10.0.0.1: icmp_seq=0 ttl=64 time=70.395 ms

homecomputer$: ping 10.0.0.2
PING 10.0.0.2 (10.0.0.2): 56 data bytes
^C
--- 10.0.0.2 ping statistics ---
2 packets transmitted, 0 packets received, 100% packet loss

I can only ssh from homecomputer(192.168.1.205) to Ubuntu7.10-homeserver(192.168.1.20 or 10.0.0.1) and ssh from Ubuntu7.10-homeserver to workplace(10.0.0.2).

Though:
Ubuntu7.10-homeserver:~$ cat /proc/sys/net/ipv4/ip_forward
1

Why doesn't it forward ? What do I have to test ?

---

### Post by moxen93 on 2007-11-02
To give some additional infos:

Ubuntu7.10-homeserver:~$ iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         

Ubuntu7.10-homeserver:~$ netstat -r
Kernel IP Routentabelle
Ziel            Router          Genmask         Flags   MSS Fenster irtt Iface
10.0.0.0        *               255.255.255.0   U         0 0          0 tap0
192.168.1.0     *               255.255.255.0   U         0 0          0 eth0
link-local      *               255.255.0.0     U         0 0          0 eth0
default         S.local         0.0.0.0         UG        0 0          0 eth0

---

### Post by mpokrywka on 2007-11-03
This is problem with routing:
1) Does "homecomputer" know how to reach 10.0.0.2?
   Homecomputer seems to be in 192.168.1.0/24 subnet and if "homeserver" is not default gateway for homecomputer, then packets go wrong way.
Check: homecomputer$ route -n
If there is no route to 10.0.0.0 then add it: ip route add 10.0.0.0/24 via 192.168.1.20
On homeserver try: tcpdump -ni tap0 and see if packets from your homecomputer are sent.

2) Even if your homecomputer is sending packets, your workplace may not know where to respond.
   Packets arrive with source 192.168.1.205 and your workplace has ip from different networks (10.196.32.19 and 10.0.0.2).
   You need to supply correct route: ip route add 192.168.1.0/24 via 10.0.0.1
If there is no need to connect from workplace to home network then you may use "iptables -t nat -I POSTROUTING -o tap0 -j MASQUERADE" on homeserver instead of route at workplace.

---

### Post by moxen93 on 2007-11-04
Thanks for the response. Homecomputer should have known where to find 10.0.0.2:

homecomputer$: netstat -r
Routing tables

Internet:
Destination        Gateway            Flags    Refs      Use  Netif Expire
default            192.168.1.1        UGSc       16      176    en1
10/24              mediafedora        UGSc        1        0    en1
127                localhost          UCS         0        0    lo0
localhost          localhost          UH         25     4436    lo0
169.254            link#5             UCS         0        0    en1
192.168.1          link#5             UCS         2        0    en1
192.168.1.1        0:d:93:2:f7:2c     UHLW       17       11    en1   1192
mediafedora        0:e0:4c:b8:8d:27   UHLW        4     1284    en1   1135
192.168.1.205      localhost          UHS         0        1    lo0

Internet6:
Destination        Gateway            Flags      Netif Expire
localhost          localhost          UH          lo0
fe80::%lo0         fe80::1%lo0        Uc          lo0
fe80::1%lo0        link#1             UHL         lo0
fe80::%en1         link#5             UC          en1
fe80::20d:93ff:fe8 0:d:93:80:23:9a    UHL         lo0
ff01::             localhost          U           lo0
ff02::%lo0         localhost          UC          lo0
ff02::%en1         link#5             UC          en1

..where mediafedora is 192.168.1.20 (from /etc/hosts)

He also knew where to find 10.0.0.1 as you can see from the formerly described ping.

However "iptables -t nat -I POSTROUTING -o tap0 -j MASQUERADE" on the  Ubuntu7.10-homeserver also solved it. In the beginning I didn't want the MASQUERADE but otherwise: if it works..
and it does. Thank you.
Still I don't understand why Ubuntu7.10-homeserver didn't route the responses from 10.0.0.2 without "iptables -t nat -I POSTROUTING -o tap0 -j MASQUERADE". Maybe I will understand one day :-)

---

### Post by mpokrywka on 2007-11-04
If MASQUERADE rule makes it work, that means your workplace do not know how to reach your homecomputer ip (192.168.1.205).
As I said in previous post, you can remove MASQUERADE and add route on your "workplace":
workplace# ip route add 192.168.1.0/24 via 10.0.0.1
(of course I assume that workplace do not have similar route already configured and used in "work" local network)

---

### Post by moxen93 on 2007-11-05
Thanx. I understand the principles now. Thanks to you. 
greetings

---

