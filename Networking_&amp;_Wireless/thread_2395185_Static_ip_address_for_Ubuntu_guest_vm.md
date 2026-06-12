---
title: "Static ip address for Ubuntu guest vm"
date: 2018-06-27
forum: Networking &amp; Wireless
---

### Post by mikealexander0007 on 2018-06-27
Hi Guys,

I installed Ubuntu 18.04 LTS on VirtualHost 5.2.12. I have literally tried everything to setup static ip address to the vm guest. Nothing would work.

Before I started with any configuration changes, this is what it looked like:

**[FONT=sans-serif]root@vm1:~# ip a[/FONT]**
[FONT=sans-serif]
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000[/FONT]
[FONT=sans-serif]    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00[/FONT]
[FONT=sans-serif]    inet [/FONT][127.0.0.1/8]("http://127.0.0.1/8")[FONT=sans-serif] scope host lo[/FONT]
[FONT=sans-serif]       valid_lft forever preferred_lft forever[/FONT]
[FONT=sans-serif]    inet6 ::1/128 scope host [/FONT]
[FONT=sans-serif]       valid_lft forever preferred_lft forever[/FONT]
[FONT=sans-serif]2: enp0s3: <BROADCAST,MULTICAST,UP,LOWER_[/FONT][FONT=sans-serif]UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000[/FONT]
[FONT=sans-serif]    link/ether 08:00:27:e0:49:b3 brd ff:ff:ff:ff:ff:ff[/FONT]
[FONT=sans-serif]    inet [/FONT][10.0.2.15/24]("http://10.0.2.15/24")[FONT=sans-serif] brd 10.0.2.255 scope global dynamic noprefixroute enp0s3[/FONT]
[FONT=sans-serif]       valid_lft 86314sec preferred_lft 86314sec[/FONT]
[FONT=sans-serif]    inet6 fe80::4715:1519:73dc:ea54/64 scope link noprefixroute [/FONT]
[FONT=sans-serif]       valid_lft forever preferred_lft forever[/FONT]
[FONT=sans-serif]3: enp0s8: <BROADCAST,MULTICAST,UP,LOWER_[/FONT][FONT=sans-serif]UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000[/FONT]
[FONT=sans-serif]    link/ether 08:00:27:14:64:9d brd ff:ff:ff:ff:ff:ff[/FONT]
[FONT=sans-serif]    inet6 fe80::be30:87d9:f826:69ef/64 scope link noprefixroute [/FONT]
[FONT=sans-serif]       valid_lft forever preferred_lft forever[/FONT]
[FONT=sans-serif]root@vm1:~# [/FONT]

**[FONT=sans-serif]root@vm1:~# ifconfig -a[/FONT]**
[FONT=sans-serif]
enp0s3: flags=4163<UP,BROADCAST,[/FONT][FONT=sans-serif]RUNNING,MULTICAST>  mtu 1500[/FONT]
[FONT=sans-serif]        inet 10.0.2.15  netmask 255.255.255.0  broadcast 10.0.2.255[/FONT]
[FONT=sans-serif]        inet6 fe80::4715:1519:73dc:ea54  prefixlen 64  scopeid 0x20<link>[/FONT]
[FONT=sans-serif]        ether 08:00:27:e0:49:b3  txqueuelen 1000  (Ethernet)[/FONT]
[FONT=sans-serif]        RX packets 76876  bytes 83921475 (83.9 MB)[/FONT]
[FONT=sans-serif]        RX errors 0  dropped 0  overruns 0  frame 0[/FONT]
[FONT=sans-serif]        TX packets 23970  bytes 3302551 (3.3 MB)[/FONT]
[FONT=sans-serif]        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0[/FONT]

[FONT=sans-serif]enp0s8: flags=4163<UP,BROADCAST,[/FONT][FONT=sans-serif]RUNNING,MULTICAST>  mtu 1500[/FONT]
[FONT=sans-serif]        inet6 fe80::be30:87d9:f826:69ef  prefixlen 64  scopeid 0x20<link>[/FONT]
[FONT=sans-serif]        ether 08:00:27:14:64:9d  txqueuelen 1000  (Ethernet)[/FONT]
[FONT=sans-serif]        RX packets 12  bytes 1162 (1.1 KB)[/FONT]
[FONT=sans-serif]        RX errors 0  dropped 0  overruns 0  frame 0[/FONT]
[FONT=sans-serif]        TX packets 206  bytes 33307 (33.3 KB)[/FONT]
[FONT=sans-serif]        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0[/FONT]

[FONT=sans-serif]lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536[/FONT]
[FONT=sans-serif]        inet 127.0.0.1  netmask 255.0.0.0[/FONT]
[FONT=sans-serif]        inet6 ::1  prefixlen 128  scopeid 0x10<host>[/FONT]
[FONT=sans-serif]        loop  txqueuelen 1000  (Local Loopback)[/FONT]
[FONT=sans-serif]        RX packets 2970  bytes 291928 (291.9 KB)[/FONT]
[FONT=sans-serif]        RX errors 0  dropped 0  overruns 0  frame 0[/FONT]
[FONT=sans-serif]        TX packets 2970  bytes 291928 (291.9 KB)[/FONT]
[FONT=sans-serif]        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0[/FONT]


[FONT=sans-serif]root@vm1:/etc/netplan# cat /etc/hostname[/FONT]
[FONT=sans-serif]vm1[/FONT]

[FONT=sans-serif]root@vm1:/etc/netplan# cat /etc/hosts[/FONT]
[FONT=sans-serif]127.0.0.1    localhost[/FONT]
[FONT=sans-serif]127.0.1.1    vm1[/FONT]

[FONT=sans-serif]# The following lines are desirable for IPv6 capable hosts[/FONT]
[FONT=sans-serif]#::1     ip6-localhost ip6-loopback[/FONT]
[FONT=sans-serif]#fe00::0 ip6-localnet[/FONT]
[FONT=sans-serif]#ff00::0 ip6-mcastprefix[/FONT]
[FONT=sans-serif]#ff02::1 ip6-allnodes[/FONT]
[FONT=sans-serif]#ff02::2 ip6-allrouters[/FONT][FONT=sans-serif][/FONT]
[FONT=sans-serif]

I tried to setup static ip address using the steps specified in the following URL (BUT IT DID NOT WORK).

[/FONT]https://www.krizna.com/ubuntu/setup-network-ubuntu-18-04/#Desktop

Then I tried this link that talks about using the netplan utility (BUT IT DID NOT WORK EITHER).

[https://www.youtube.com/watch?v=67tryRGCsAs](https://www.youtube.com/watch?v=67tryRGCsAs)

I tried to look around numerous google links that are either incomplete or just did not work.

I am at a point where I am thinking it is probably not worth going with ubuntu and go with something else!!

Would anyone be considerate to help me out please...

Any help is greatly appreciated.


Regards,
Mike

---

### Post by SeijiSensei on 2018-06-28
Did you set the virtual adapter to "bridged" mode? In NAT mode, VB will always give it an address in 10.0/16.

---

### Post by TheFu on 2018-06-28
Did you try network-manager?
or 
[https://netplan.io/examples](https://netplan.io/examples)

 10.0.2.15 is the address being provided. What address did you expect?   And pay attention to what Sensei says. [https://www.virtualbox.org/manual/ch06.html](https://www.virtualbox.org/manual/ch06.html) There are multiple caveats.

---

### Post by mikealexander0007 on 2018-06-29
Thank you so much for the responses..yeah, that could be the issue. I probably didn't give the ip address within the range given by the NAT Adapter. Let me try it out and circle back with you.

---

