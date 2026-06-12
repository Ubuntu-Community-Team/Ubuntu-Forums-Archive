---
title: "i am a new user, i don't know what is going on on my internet, conneting but no displ"
date: 2008-03-11
forum: Networking &amp; Wireless
---

### Post by tank000007 on 2008-03-11
help please
does any one have a  Realtek RTL8139/810x Family fast Ethernet NIC driver? i don't know what was happening,when i use ubuntu can't get on internet.-_-!! can , but always said connecting, but never turn upthe page of google,  static ip was set well, package were sending and reciving as well but very slow.when i use live cd was totally working fine.
can anyone tell me what is going on ?? using eth0 , and eth1 --WIFI was close.

BTW i am new here ,hi all!

---

### Post by SpaceTeddy on 2008-03-11
can you please post the output of the following commands to further debug you problem
```
ifconfig
route -n
iptables -L
```

---

### Post by tank000007 on 2008-03-11
i very want to use ubuntu but ....
and today i login to ubuntu is very slow, take me 10 minutes to login and every thing in the GUI was so slow as well , take 8 second to open the command line.....things get more difficult......please help. .... thanks to all read and reply
```
tank@tank-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0A:E4:DC:20:43  
          inet addr:10.1.1.3  Bcast:10.255.255.255  Mask:255.0.0.0
          inet6 addr: fe80::20a:e4ff:fedc:2043/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:40 errors:0 dropped:0 overruns:0 frame:0
          TX packets:78 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3902 (3.8 KiB)  TX bytes:6238 (6.0 KiB)
          Interrupt:217 Base address:0xc400 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)

tank@tank-laptop:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.0.0.0        0.0.0.0         255.0.0.0       U     0      0        0 eth0
0.0.0.0         10.1.1.1        0.0.0.0         UG    0      0        0 eth0
tank@tank-laptop:~$ iptable -l
bash: iptable: command not found
tank@tank-laptop:~$ iptable -L
bash: iptable: command not found
tank@tank-laptop:~$ iptables -L
WARNING: Error inserting x_tables (/lib/modules/2.6.17-12-generic/kernel/net/netfilter/x_tables.ko): Operation not permitted
FATAL: Error inserting ip_tables (/lib/modules/2.6.17-12-generic/kernel/net/ipv4/netfilter/ip_tables.ko): Operation not permitted
iptables v1.3.5: can't initialize iptables table `filter': Permission denied (you must be root)
Perhaps iptables or your kernel needs to be upgraded.
tank@tank-laptop:~$ login
No utmp entry.  You must exec "login" from the lowest level "sh"
tank@tank-laptop:~$ 
tank@tank-laptop:~$ cls
bash: cls: command not found
tank@tank-laptop:~$ clear

tank@tank-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0A:E4:DC:20:43  
          inet addr:10.1.1.3  Bcast:10.255.255.255  Mask:255.0.0.0
          inet6 addr: fe80::20a:e4ff:fedc:2043/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:121 errors:0 dropped:0 overruns:0 frame:0
          TX packets:164 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:12551 (12.2 KiB)  TX bytes:12841 (12.5 KiB)
          Interrupt:217 Base address:0xc400 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:200 (200.0 b)  TX bytes:200 (200.0 b)

tank@tank-laptop:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.0.0.0        0.0.0.0         255.0.0.0       U     0      0        0 eth0
0.0.0.0         10.1.1.1        0.0.0.0         UG    0      0        0 eth0
tank@tank-laptop:~$ iptables -L
WARNING: Error inserting x_tables (/lib/modules/2.6.17-12-generic/kernel/net/netfilter/x_tables.ko): Operation not permitted
FATAL: Error inserting ip_tables (/lib/modules/2.6.17-12-generic/kernel/net/ipv4/netfilter/ip_tables.ko): Operation not permitted
iptables v1.3.5: can't initialize iptables table `filter': Permission denied (you must be root)
Perhaps iptables or your kernel needs to be upgraded.
tank@tank-laptop:~$ 

```

---

### Post by SpaceTeddy on 2008-03-11
your network config looks fine (althought, your subnet is really big... ).

i totally forgot to ask for the output of
```
cat /etc/resolv.conf
```

which would be your dns servs.
otherwise, i do not see anything that would be wrong with your configuration

as for the slow GUI - no idea what that is about - but you'd better ask about that in the appropriate forum (not the networking one :) )

---

### Post by tank000007 on 2008-03-12
ok ..i will try tomake it working.
so ..the above "code" was come from the static ip confg
submask 255.0.0.0
ip 10.0.0.3
router 10.1.1.1

are you sure it is the right out put for eth0?

what do you man by "too big"
 from which to which ip? 

please, i want to use linux , not vista:(

---

### Post by SpaceTeddy on 2008-03-12
you are using a /8 network - meaning your network has 16777216 (2^24) ip addresses in it. it's a bit much for a "home" network.

But that was a side note, the main point is that it should be working from your configuration (at least as far as i can see)

can you please provide the output of
```
cat /etc/resolv.conf
```

---

