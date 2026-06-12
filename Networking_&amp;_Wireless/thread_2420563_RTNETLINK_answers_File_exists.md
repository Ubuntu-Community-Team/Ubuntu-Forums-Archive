---
title: "RTNETLINK answers: File exists"
date: 2019-06-06
forum: Networking &amp; Wireless
---

### Post by lingste on 2019-06-06
Hello!
I'm new to Linux and Ubuntu so I'm sure that this problem should be a stupid thing but my head is going to explode because of this!! So I hope the community can help me :confused:

I have a virtual machine with Ubuntu 18.04.2 with 2 interfaces: ens33 and ens34. I need them with static IPs, so I changed the /etc/network/interfaces with this:

```

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback


#LAN1
auto ens33
iface ens33 inet static
address 172.16.0.5
netmask 255.255.255.0
network 172.16.0.0
gateway 172.16.0.1


#LAN2
auto ens34
iface ens34 inet static
address 10.0.2.15
netmask 255.255.255.0
network 10.0.2.0
gateway 10.0.2.1

```

Then when I restart the network service, I receive this error:

```

&#9679; networking.service - Raise network interfaces
   Loaded: loaded (/lib/systemd/system/networking.service; enabled; vendor pres
   Active: failed (Result: exit-code) since Thu 2019-06-06 18:20:20 PDT; 10s ag
     Docs: man:interfaces(5)
  Process: 2982 ExecStart=/sbin/ifup -a --read-environment (code=exited, status
  Process: 2979 ExecStartPre=/bin/sh -c [ "$CONFIGURE_INTERFACES" != "no" ] && 
 Main PID: 2982 (code=exited, status=1/FAILURE)


Jun 06 18:20:20 ubuntu systemd[1]: Starting Raise network interfaces...
Jun 06 18:20:20 ubuntu ifup[2982]: RTNETLINK answers: File exists
Jun 06 18:20:20 ubuntu ifup[2982]: Failed to bring up ens33.
Jun 06 18:20:20 ubuntu systemd[1]: networking.service: Main process exited, cod
Jun 06 18:20:20 ubuntu ifup[2982]: RTNETLINK answers: File exists
Jun 06 18:20:20 ubuntu systemd[1]: networking.service: Failed with result 'exit
Jun 06 18:20:20 ubuntu ifup[2982]: Failed to bring up ens34.
Jun 06 18:20:20 ubuntu systemd[1]: Failed to start Raise network interfaces.

```

I don't know what I'm doing wrong. Am I configuring LAN networks in the wrong way?? This is an experimental environment for university. Can anyone help me and explain why I get this error??

---

### Post by chili555 on 2019-06-07
> Am I configuring LAN networks in the wrong way??Yes, indeed. If it is running, the preferred method is Network Manager. If NM is not installed and running, then the correct method is netplan.

Please run and post:```
ls /etc/netplan
```

---

### Post by lingste on 2019-06-07
Thank you for your response :)

This is the result:

```

root@ubuntu:/home/user1# ls /etc/netplan
01-network-manager-all.yaml
root@ubuntu:/home/user1# 

```

---

### Post by chili555 on 2019-06-07
> 
01-network-manager-all.yaml
```

network:
  version: 2
  renderer: NetworkManager

```

In this file, netplan hands off all to Network Manager. That's where I suggest that you make your changes. Also, please revert the incorrect changes to /etc/network/interfaces.

[http://3.bp.blogspot.com/-zXKEt3vxNg4/T58h-Cm1HJI/AAAAAAAAAjs/uOC0tCLcS4w/s1600/ScreenHunter_02%2BApr.%2B30%2B16.37.gif](http://3.bp.blogspot.com/-zXKEt3vxNg4/T58h-Cm1HJI/AAAAAAAAAjs/uOC0tCLcS4w/s1600/ScreenHunter_02%2BApr.%2B30%2B16.37.gif)

---

### Post by lingste on 2019-06-07
Thank you so much for your help!! I finally could configure them via netwok manager as you suggested. Now I don't get that interfaces error and have conexion! =d>=d>

But, the next step in my homework is giving me problems too ](*,)](*,) I need to enable ip forwarding between those LANs, so I have this iptables rules:

```

echo 1 > /proc/sys/net/ipv4/ip_forward
iptables -t nat -A POSTROUTING -o ens33 -j MASQUERADE
iptables -t nat -A POSTROUTING -o ens34 -j MASQUERADE
iptables -A FORWARD -i ens33 -o ens34 -m state --state RELATED,ESTABLISHED -j ACCEPT
iptables -A FORWARD -i ens34 -o ens33 -m state --state RELATED,ESTABLISHED -j ACCEPT
iptables -A FORWARD -i ens33 -o ens34 -j ACCEPT
iptables -A FORWARD -i ens34 -o ens33 -j ACCEPT

```

But doesn't work :cry::cry:

I did some research and I think that these rules are ok but I'm not sure (a very new linux girl here :-\"). When I validate them with command ```
iptables -vnL
``` I get this:

```

Chain INPUT (policy ACCEPT 10419 packets, 782K bytes)
 pkts bytes target     prot opt in     out     source               destination         


Chain FORWARD (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 ACCEPT     all  --  ens33  ens34   0.0.0.0/0            0.0.0.0/0            state RELATED,ESTABLISHED
    0     0 ACCEPT     all  --  ens34  ens33   0.0.0.0/0            0.0.0.0/0            state RELATED,ESTABLISHED
    0     0 ACCEPT     all  --  ens33  ens34   0.0.0.0/0            0.0.0.0/0           
    0     0 ACCEPT     all  --  ens34  ens33   0.0.0.0/0            0.0.0.0/0           


Chain OUTPUT (policy ACCEPT 10312 packets, 739K bytes)
 pkts bytes target     prot opt in     out     source               destination         

```

so I think that they're correctly settled. But why when I try to do ping between LANs, didn't work??

Sorry if this changed the main subject of the post, but I hope that you can help me O:)

---

### Post by chili555 on 2019-06-08
> I finally could configure them via netwok manager as you suggested. Now I don't get that interfaces error and have conexion! Awesome! Glad it's working.> Sorry if this changed the main subject of the postIt certainly did.

Unfortunately, I know little to nothing about iptables. I suggest that you start a new thread and mention iptables in the title so that the experts will see and help.

---

### Post by SeijiSensei on 2019-06-08
That's likely not an iptables problem, but a consequence of the fact that routing between interfaces is disabled by default in Ubuntu and most other distros as a security measure.

In /etc/sysctl.conf, you need to uncomment (remove the hash mark from) this line:

```
net.ipv4.ip_forward=1
```

Reboot and see if that helps with your problem.

---

### Post by lingste on 2019-06-09
Thank you for your reply! But no, I did what you suggested but still not working. When I try to ping for other VM (A Kali VM) through this, I get:

```

root@kali:~# ping 172.16.0.2
PING 172.16.0.2 (172.16.0.2) 56(84) bytes of data.
From 10.0.2.16 icmp_seq=1 Destination Host Unreachable
From 10.0.2.16 icmp_seq=2 Destination Host Unreachable
From 10.0.2.16 icmp_seq=3 Destination Host Unreachable

```

And from the other side is the same (other Ubuntu VM): 

```

root@irstation:/home/ir# ping 10.0.2.16
PING 10.0.2.16 (10.0.2.16) 56(84) bytes of data.
From 172.16.0.2 icmp_seq=1 Destination Host Unreachable
From 172.16.0.2 icmp_seq=2 Destination Host Unreachable
From 172.16.0.2 icmp_seq=3 Destination Host Unreachable

```

:(:(

---

### Post by SeijiSensei on 2019-06-10
Do you have static routes set up on both machines that use the proper gateway to reach the other network?

Post the results of running "route -n" on each machine.

---

### Post by lingste on 2019-06-10
I think so... :confused: I use the same gateway of the machine with 2 interfaces. The result of "route -n" is:

This is for Ubuntu machine (with only 1 interface)
```

root@irstation:/home/ir# route -n
Kernel IP routing table
Destination      Gateway       Genmask           Flags Metric  Ref    Use Iface
0.0.0.0            172.16.0.1    0.0.0.0              UG    0          0        0   ens33
169.254.0.0     0.0.0.0         255.255.0.0       U      1000     0        0   ens33
172.16.0.0       0.0.0.0         255.255.255.0   U      0           0        0   ens33
172.16.0.0       0.0.0.0         255.255.0.0       U      0           0        0   ens33

```

This is for Kali machine (with only 1 interface)
```

root@kali:~# route -n
Kernel IP routing table
Destination     Gateway         Genmask          Flags Metric Ref    Use Iface
0.0.0.0           10.0.2.15        0.0.0.0              UG    0      0        0    eth0
10.0.2.0         0.0.0.0            255.255.255.0   U      0      0        0    eth0

```

Is there any wrong configuration??

---

### Post by SeijiSensei on 2019-06-11
I think the problem might be that there is no route to 10.0.2.0/24 on the router at 172.16.0.1.  I don't know what kind of device is at 172.16.0.1, but you should start by adding a static route on it to 10.0.2.0/24 via 172.16.0.5.

There's also something wrong with the configuration that has two 172.16.0.0 entries with differing netmasks.  You probably want to check that machine's configuration again so it's only using the 255.255.255.0 netmask for 172.16.0.0/24 and drop the one with netmask 255.255.0.0 for 172.16.0.0/16.

---

### Post by lingste on 2019-07-20
Hi! I'm finally back!!


Sorry for dissapear and let the post abandoned but my PC suddenly died and I had to buy a new one!! :mad::-?  When I restore all my things I did my lab again and everything worked just fine! :o I don't know why I had so many troubles at first, because I used the same exact method!! :-k:-k:-\" hahaha 


Anyway, I didn't want to let the post just like that and I came to thank again all your help and tell you guys that everything worked great at the end! Thank you so much!! ;);)

---

