---
title: "iptables port forward stopped working"
date: 2017-06-10
forum: Networking &amp; Wireless
---

### Post by twoj on 2017-06-10
[COLOR=#111111][FONT=Ubuntu]I have a ubuntu 17.04, and I configured DNS, DHCP and iptables, everything was working as expected. Now just port forwards do not work. DNS and DHCP and internet is all available to computers in the private subnet.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]Here is my setup:

[/FONT][/COLOR]```

eno1 is the exterior/public NIC
enp2s0f1 is the private subnet NIC

myubuntu enp2s0f1 ip:  192.168.0.1

ubuntu@myubuntu:~$ sudo iptables -L --line-numbers
Chain INPUT (policy ACCEPT)
num  target     prot opt source               destination         
1    ACCEPT     all  --  anywhere             anywhere            

Chain FORWARD (policy ACCEPT)
num  target     prot opt source               destination         
1    ACCEPT     all  --  anywhere             anywhere            

Chain OUTPUT (policy ACCEPT)
num  target     prot opt source               destination         



ubuntu@myubuntu:~$ sudo iptables -t nat --line-numbers -L
Chain PREROUTING (policy ACCEPT)
num  target     prot opt source               destination         
1    DNAT       tcp  --  anywhere             anywhere             tcp dpt:http to:192.168.0.51:8080

Chain INPUT (policy ACCEPT)
num  target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
num  target     prot opt source               destination         

Chain POSTROUTING (policy ACCEPT)
num  target     prot opt source               destination         
1    MASQUERADE  all  --  anywhere             anywhere            



ubuntu@myubuntu:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         10.10.6.1       0.0.0.0         UG    0      0        0 eno1
10.10.6.0       0.0.0.0         255.255.255.0   U     0      0        0 eno1
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eno1
192.168.0.0     0.0.0.0         255.255.255.0   U     0      0        0 enp2s0f1
```[COLOR=#111111][FONT=Ubuntu]

I' m thinking it has to be something silly... But I can not find it. Any help will be appreciated.

[/FONT][/COLOR]

---

### Post by siben17 on 2017-06-11
Hello,

You have not specify any IP or interface or port to forward to 192.168.0.51:8080.
I think you have to write something like this :
   iptables -t nat -A PREROUTING -p tcp --dport 80 -i eno1 -j DNAT --to 192.168.0.51:8080

---

### Post by twoj on 2017-06-12
```

[COLOR=#000000]iptables -t nat -A PREROUTING -p tcp --dport 80 -i eno1 -j DNAT --to 192.168.0.51:8080[/COLOR]

```
Yes, that is the command that I used.

I did flip the POSTROUTE  [COLOR=#000000][FONT=&amp]MASQUERADE [/FONT][/COLOR] to the WAN nic  and I have the NAT forwards working for my RDP (3389).
However another NAT going to a different server does not work????    This NAT is mapped from port 80 on the router to port 8080 on another cpu, and it does not work.

```

ubuntu@myubuntu:/$ sudo iptables -t nat -v -x -n -L --line-numbers
Chain PREROUTING (policy ACCEPT 340 packets, 29199 bytes)
num      pkts      bytes target     prot opt in     out     source               destination         
1           1       52 DNAT       tcp  --  eno1   *       0.0.0.0/0            0.0.0.0/0            tcp dpt:9997 to:192.168.0.4:3389
2           0        0 DNAT       tcp  --  eno1   *       0.0.0.0/0            0.0.0.0/0            tcp dpt:80 to:192.168.0.51:8080
3           0        0 DNAT       tcp  --  eno1   *       0.0.0.0/0            0.0.0.0/0            tcp dpt:81 to:192.168.0.51:8080

```
For NAT #1 I can see packets flowing into it, but for NATs 2 & 3 I do not?  Nothing is blocking these ports locally.

What do you think?

---

### Post by SeijiSensei on 2017-06-12
Try just using the DNAT rule without masquerading. Or limit the masquerading to just outbound traffic:
```
sudo iptables -t nat -i enp2s0f1 -o eno1 -j MASQUERADE
```

---

### Post by twoj on 2017-06-12
OK.   Its working.....  
Thanks for your help!

---

