---
title: "Unable to acess network with static IP address"
date: 2017-04-01
forum: Networking &amp; Wireless
---

### Post by pratherdude2 on 2017-04-01
I am trying to set a static IP address on my server, since that's what I prefer and I am trying to setup a baisc web server to play with. The problem is that if I set a static IP I cannot ping anything or access the web from my server. If I set it to DHCP it works just fine, I have tried different ports on my switch and modem, cables, pinging the router by IP, pinging [www.google.com]("http://www.google.com").

/etc/networks/interfaces
> 
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

source /etc/networks/interfaces.d/*

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto enp3s0
iface enp3s0 inet static
          address 192.168.1.100
          netmask 255.255.255.0
          network 192.168.1.0
          broadcast 192.168.1.255
          gateway 192.168.1.1
          #dns-# options are implemented by the resolvconf package, if installed
          dns-nameservers 192.168.1.1 8.8.8.8 8.8.4.4

Thanks in advance.

---

### Post by Tadaen_Sylvermane on 2017-04-01
Eliminate variables. The network and broadcast lines are unnecessary. Try a single dns address instead of all 3 also.

Try a reboot as well. Not sure why but ive changed to static, lost connection. Works fine after reboot. Restaeting service doesnt help.

---

### Post by pratherdude2 on 2017-04-01
> **Tadaen_Sylvermane said:**
> Eliminate variables. The network and broadcast lines are unnecessary. Try a single dns address instead of all 3 also.

Try a reboot as well. Not sure why but ive changed to static, lost connection. Works fine after reboot. Restaeting service doesnt help.

Ok, tried it with no luck. Same issue still unable to get out with the server.

---

### Post by chili555 on 2017-04-02
Please change it back to DHCP and get the system to re-read and use the changes:```
sudo ifdown enp3s0 && sudo ifup -v enp3s0
```The -v for verbose will give us some details about the address, gateway, DNS, etc. that we can use to troubleshoot your interfaces file. Post it and we'll propose a better file wording.

---

### Post by pratherdude2 on 2017-04-02
> **chili555 said:**
> Please change it back to DHCP and get the system to re-read and use the changes:```
sudo ifdown enp3s0 && sudo ifup -v enp3s0
```The -v for verbose will give us some details about the address, gateway, DNS, etc. that we can use to troubleshoot your interfaces file. Post it and we'll propose a better file wording.


Done, Here is the output.


> 
sudo ifdown enp3s0 && sudo ifup -v enp3s0
Killed old client process
Internet Systems Consortium DHCP Client 4.3.3
Copyright 2004-2015 Internet Systems Consortium.
All rights reserved.
For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)

Listening on LPF/enp3s0/00:25:90:33:a2:66
Sending on   LPF/enp3s0/00:25:90:33:a2:66
Sending on   Socket/fallback
DHCPRELEASE on enp3s0 to 192.168.1.1 port 67 (xid=0x73449e97)
Configuring interface enp3s0=enp3s0 (inet)
/bin/run-parts --exit-on-error --verbose /etc/network/if-pre-up.d
run-parts: executing /etc/network/if-pre-up.d/ethtool
run-parts: executing /etc/network/if-pre-up.d/ifenslave
+ [ inet = meta ]
+ IF_BOND_SLAVES=
+ [  ]
+ [  ]
+ [ -z  ]
+ exit
run-parts: executing /etc/network/if-pre-up.d/vlan
run-parts: executing /etc/network/if-pre-up.d/wireless-tools
run-parts: executing /etc/network/if-pre-up.d/wpasupplicant

/sbin/dhclient -1 -v -pf /run/dhclient.enp3s0.pid -lf /var/lib/dhcp/dhclient.enp3s0.leases -I -df /var/lib/dhcp/dhclient6.enp3s0.leases enp3s0     
Internet Systems Consortium DHCP Client 4.3.3
Copyright 2004-2015 Internet Systems Consortium.
All rights reserved.
For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)

Listening on LPF/enp3s0/00:25:90:33:a2:66
Sending on   LPF/enp3s0/00:25:90:33:a2:66
Sending on   Socket/fallback
DHCPDISCOVER on enp3s0 to 255.255.255.255 port 67 interval 3 (xid=0xd30af469)
DHCPDISCOVER on enp3s0 to 255.255.255.255 port 67 interval 4 (xid=0xd30af469)
DHCPDISCOVER on enp3s0 to 255.255.255.255 port 67 interval 10 (xid=0xd30af469)
DHCPREQUEST of 192.168.1.234 on enp3s0 to 255.255.255.255 port 67 (xid=0x69f40ad3)
DHCPOFFER of 192.168.1.234 from 192.168.1.1
DHCPACK of 192.168.1.234 from 192.168.1.1
bound to 192.168.1.234 -- renewal in 40819 seconds.
/bin/run-parts --exit-on-error --verbose /etc/network/if-up.d
run-parts: executing /etc/network/if-up.d/000resolvconf
run-parts: executing /etc/network/if-up.d/avahi-autoipd
run-parts: executing /etc/network/if-up.d/avahi-daemon
run-parts: executing /etc/network/if-up.d/ethtool
run-parts: executing /etc/network/if-up.d/ifenslave
+ [ inet = meta ]
+ [  ]
run-parts: executing /etc/network/if-up.d/ip
run-parts: executing /etc/network/if-up.d/ntpdate
run-parts: executing /etc/network/if-up.d/postfix
run-parts: executing /etc/network/if-up.d/upstart
run-parts: executing /etc/network/if-up.d/wpasupplicant


---

### Post by chili555 on 2017-04-02
Try this:```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

source /etc/networks/interfaces.d/*

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto enp3s0
iface enp3s0 inet static
address 192.168.1.100
netmask 255.255.255.0
gateway 192.168.1.1
dns-nameservers 192.168.1.1 8.8.8.8 8.8.4.4
```Followed by:```
sudo ifdown enp3s0 && sudo ifup -v enp3s0
```And then:```
ping -c3 192.168.1.1
ping -c3 8.8.8.8
ping -c3 www.ubuntu.com
```

---

### Post by pratherdude2 on 2017-04-02
> **chili555 said:**
> Try this:```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

source /etc/networks/interfaces.d/*

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto enp3s0
iface enp3s0 inet static
address 192.168.1.100
netmask 255.255.255.0
gateway 192.168.1.1
dns-nameservers 192.168.1.1 8.8.8.8 8.8.4.4
```Followed by:```
sudo ifdown enp3s0 && sudo ifup -v enp3s0
```And then:```
ping -c3 192.168.1.1
ping -c3 8.8.8.8
ping -c3 www.ubuntu.com
```

Thanks chili I appreciate the help, Here is the output and it seams to have fixed the issues.
> 
$ sudo ifdown enp3s0 && sudo ifup -v enp3s0
warning: couldn't open interfaces file "/etc/networks/interfaces.d/*"
RTNETLINK answers: Cannot assign requested address
Parsing file /etc/networks/interfaces.d/*
warning: couldn't open interfaces file "/etc/networks/interfaces.d/*"
Configuring interface enp3s0=enp3s0 (inet)
/bin/run-parts --exit-on-error --verbose /etc/network/if-pre-up.d
run-parts: executing /etc/network/if-pre-up.d/ethtool
run-parts: executing /etc/network/if-pre-up.d/ifenslave
+ [ inet = meta ]
+ IF_BOND_SLAVES=
+ [  ]
+ [  ]
+ [ -z  ]
+ exit
run-parts: executing /etc/network/if-pre-up.d/vlan
run-parts: executing /etc/network/if-pre-up.d/wireless-tools
run-parts: executing /etc/network/if-pre-up.d/wpasupplicant
/bin/ip addr add 192.168.1.100/255.255.255.0 broadcast 192.168.1.255       dev enp3s0 label enp3s0
/bin/ip link set dev enp3s0   up
 /bin/ip route add default via 192.168.1.1  dev enp3s0 onlink 
/bin/run-parts --exit-on-error --verbose /etc/network/if-up.d
run-parts: executing /etc/network/if-up.d/000resolvconf
run-parts: executing /etc/network/if-up.d/avahi-autoipd
run-parts: executing /etc/network/if-up.d/avahi-daemon
run-parts: executing /etc/network/if-up.d/ethtool
run-parts: executing /etc/network/if-up.d/ifenslave
+ [ inet = meta ]
+ [  ]
run-parts: executing /etc/network/if-up.d/ip
run-parts: executing /etc/network/if-up.d/ntpdate
run-parts: executing /etc/network/if-up.d/postfix
run-parts: executing /etc/network/if-up.d/upstart
run-parts: executing /etc/network/if-up.d/wpasupplicant
shaggy@Nightcrawler:~$ ping -c3 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
64 bytes from 192.168.1.1: icmp_seq=1 ttl=64 time=0.610 ms
64 bytes from 192.168.1.1: icmp_seq=2 ttl=64 time=0.663 ms
64 bytes from 192.168.1.1: icmp_seq=3 ttl=64 time=0.630 ms

--- 192.168.1.1 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 1998ms
rtt min/avg/max/mdev = 0.610/0.634/0.663/0.030 ms
shaggy@Nightcrawler:~$ ping -c3 8.8.8.8
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.
64 bytes from 8.8.8.8: icmp_seq=1 ttl=49 time=48.2 ms
64 bytes from 8.8.8.8: icmp_seq=2 ttl=49 time=48.5 ms
64 bytes from 8.8.8.8: icmp_seq=3 ttl=49 time=48.3 ms

--- 8.8.8.8 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2002ms
rtt min/avg/max/mdev = 48.200/48.364/48.548/0.229 ms
shaggy@Nightcrawler:~$ ping -c3 [www.ubuntu.com](www.ubuntu.com)
PING [www.ubuntu.com](www.ubuntu.com) (91.189.89.103) 56(84) bytes of data.
64 bytes from www-ubuntu-com.privet.canonical.com (91.189.89.103): icmp_seq=1 ttl=52 time=131 ms
64 bytes from www-ubuntu-com.privet.canonical.com (91.189.89.103): icmp_seq=2 ttl=52 time=159 ms
64 bytes from www-ubuntu-com.privet.canonical.com (91.189.89.103): icmp_seq=3 ttl=52 time=131 ms

--- [www.ubuntu.com](www.ubuntu.com) ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 6323ms
rtt min/avg/max/mdev = 131.564/140.938/159.389/13.050 ms


So can you tell me what was wrong with the original interfaces file? I would like to know since that is the one that Ubuntu created when I installed it, and mabey next time I'll know better.

Thanks again Chili, sure do appreciate it.

---

### Post by pratherdude2 on 2017-04-02
Ok, so now I have lost all networking again after doing a system update. I have made sure the interfaces file matches what you gave me before and I did a [COLOR=#000000][FONT=&quot]sudo ifdown enp3s0 && sudo ifup -v enp3s0, I get destination unreachable on a ping.

[/FONT][/COLOR]

---

### Post by chili555 on 2017-04-02
Let's try to get rid of this warning:> warning: couldn't open interfaces file "/etc/networks/interfaces.d/*"
RTNETLINK answers: Cannot assign requested address
Parsing file /etc/networks/interfaces.d/*
warning: couldn't open interfaces file "/etc/networks/interfaces.d/*"Please comment out the relevant line; thus:```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

#source /etc/networks/interfaces.d/*

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto enp3s0
iface enp3s0 inet static
address 192.168.1.100
netmask 255.255.255.0
gateway 192.168.1.1
dns-nameservers 192.168.1.1 8.8.8.8 8.8.4.4
```Rerun the command:```
sudo ifdown enp3s0 && sudo ifup -v enp3s0
```Post the result here so that we may troubleshoot.

---

### Post by pratherdude2 on 2017-04-08
> **chili555 said:**
> Let's try to get rid of this warning:Please comment out the relevant line; thus:```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

#source /etc/networks/interfaces.d/*

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto enp3s0
iface enp3s0 inet static
address 192.168.1.100
netmask 255.255.255.0
gateway 192.168.1.1
dns-nameservers 192.168.1.1 8.8.8.8 8.8.4.4
```Rerun the command:```
sudo ifdown enp3s0 && sudo ifup -v enp3s0
```Post the result here so that we may troubleshoot.

Sorry for the delay was out of town.

Here is the printout after redoing the interfaces file and doing the ifdown / ifup

> 
$ sudo ifdown enp3s0 && sudo ifup -v enp3s0
Configuring interface enp3s0=enp3s0 (inet)
/bin/run-parts --exit-on-error --verbose /etc/network/if-pre-up.d
run-parts: executing /etc/network/if-pre-up.d/ethtool
run-parts: executing /etc/network/if-pre-up.d/ifenslave
+ [ inet = meta ]
+ IF_BOND_SLAVES=
+ [  ]
+ [  ]
+ [ -z  ]
+ exit
run-parts: executing /etc/network/if-pre-up.d/vlan
run-parts: executing /etc/network/if-pre-up.d/wireless-tools
run-parts: executing /etc/network/if-pre-up.d/wpasupplicant
/bin/ip addr add 192.168.1.100/255.255.255.0 broadcast 192.168.1.255       dev enp3s0 label enp3s0
/bin/ip link set dev enp3s0   up
 /bin/ip route add default via 192.168.1.1  dev enp3s0 onlink 
/bin/run-parts --exit-on-error --verbose /etc/network/if-up.d
run-parts: executing /etc/network/if-up.d/000resolvconf
run-parts: executing /etc/network/if-up.d/avahi-autoipd
run-parts: executing /etc/network/if-up.d/avahi-daemon
run-parts: executing /etc/network/if-up.d/ethtool
run-parts: executing /etc/network/if-up.d/ifenslave
+ [ inet = meta ]
+ [  ]
run-parts: executing /etc/network/if-up.d/ip
run-parts: executing /etc/network/if-up.d/ntpdate
run-parts: executing /etc/network/if-up.d/openssh-server
run-parts: executing /etc/network/if-up.d/postfix
run-parts: executing /etc/network/if-up.d/upstart
run-parts: executing /etc/network/if-up.d/wpasupplicant


And Ping
> 
$ ping 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
From 192.168.1.234 icmp_seq=1 Destination Host Unreachable
From 192.168.1.234 icmp_seq=2 Destination Host Unreachable
From 192.168.1.234 icmp_seq=3 Destination Host Unreachable
From 192.168.1.234 icmp_seq=4 Destination Host Unreachable
From 192.168.1.234 icmp_seq=5 Destination Host Unreachable
From 192.168.1.234 icmp_seq=6 Destination Host Unreachable
^C
--- 192.168.1.1 ping statistics ---
6 packets transmitted, 0 received, +6 errors, 100% packet loss, time 5031ms
pipe 3


---

### Post by chili555 on 2017-04-08
> From 192.168.1.[COLOR="#FF0000"]234[/COLOR] icmp_seq=1 Destination Host UnreachableWha-what?? You asked for x.100 but evidently get x.234. May we see:```
ifconfig
dmesg | grep enp
cat /etc/NetworkManager/NetworkManager.conf
```

---

### Post by pratherdude2 on 2017-04-08
> **chili555 said:**
> Wha-what?? You asked for x.100 but evidently get x.234. May we see:```
ifconfig
dmesg | grep enp
cat /etc/NetworkManager/NetworkManager.conf
```


Reran ifdown and ifup got an error this time saying can't assign IP address
> 
$ sudo ifdown enp3s0 && sudo ifup -v enp3s0
RTNETLINK answers: Cannot assign requested address
Configuring interface enp3s0=enp3s0 (inet)
/bin/run-parts --exit-on-error --verbose /etc/network/if-pre-up.d
run-parts: executing /etc/network/if-pre-up.d/ethtool
run-parts: executing /etc/network/if-pre-up.d/ifenslave
+ [ inet = meta ]
+ IF_BOND_SLAVES=
+ [  ]
+ [  ]
+ [ -z  ]
+ exit
run-parts: executing /etc/network/if-pre-up.d/vlan
run-parts: executing /etc/network/if-pre-up.d/wireless-tools
run-parts: executing /etc/network/if-pre-up.d/wpasupplicant
/bin/ip addr add 192.168.1.100/255.255.255.0 broadcast 192.168.1.255       dev enp3s0 label enp3s0
/bin/ip link set dev enp3s0   up
 /bin/ip route add default via 192.168.1.1  dev enp3s0 onlink 
/bin/run-parts --exit-on-error --verbose /etc/network/if-up.d
run-parts: executing /etc/network/if-up.d/000resolvconf
run-parts: executing /etc/network/if-up.d/avahi-autoipd
run-parts: executing /etc/network/if-up.d/avahi-daemon
run-parts: executing /etc/network/if-up.d/ethtool
run-parts: executing /etc/network/if-up.d/ifenslave
+ [ inet = meta ]
+ [  ]
run-parts: executing /etc/network/if-up.d/ip
run-parts: executing /etc/network/if-up.d/ntpdate
run-parts: executing /etc/network/if-up.d/openssh-server
run-parts: executing /etc/network/if-up.d/postfix
run-parts: executing /etc/network/if-up.d/upstart
run-parts: executing /etc/network/if-up.d/wpasupplicant



Print out from ```
ifconfig
dmesg | grep enp
cat /etc/NetworkManager/NetworkManager.conf
```

> 
$ ifconfig
enp3s0    Link encap:Ethernet  HWaddr 00:25:90:33:a2:66  
          inet addr:192.168.1.234  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::225:90ff:fe33:a266/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:17501179 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2717313 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:25639548364 (25.6 GB)  TX bytes:2120736431 (2.1 GB)
          Interrupt:16 Memory:fabe0000-fac00000 

enp4s0    Link encap:Ethernet  HWaddr 00:25:90:33:a2:67  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 Memory:face0000-fad00000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:2082689 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2082689 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1 
          RX bytes:658968824 (658.9 MB)  TX bytes:658968824 (658.9 MB)

shaggy@Nightcrawler:~$ dmesg | grep enp
[    3.039679] e1000e 0000:04:00.0 enp4s0: renamed from eth1
[    3.055051] e1000e 0000:03:00.0 enp3s0: renamed from eth0
[   52.437901] IPv6: ADDRCONF(NETDEV_UP): enp3s0: link is not ready
[   55.479586] e1000e: enp3s0 NIC Link is Up 1000 Mbps Full Duplex, Flow Control: Rx/Tx
[   55.479896] IPv6: ADDRCONF(NETDEV_CHANGE): enp3s0: link becomes ready
[   67.227753] IPv6: ADDRCONF(NETDEV_UP): enp4s0: link is not ready
[   67.309634] IPv6: ADDRCONF(NETDEV_UP): enp4s0: link is not ready
[29684.336606] e1000e: enp3s0 NIC Link is Down
[29692.682501] IPv6: ADDRCONF(NETDEV_UP): enp3s0: link is not ready
[29696.017055] e1000e: enp3s0 NIC Link is Up 1000 Mbps Full Duplex, Flow Control: Rx/Tx
[29696.017367] IPv6: ADDRCONF(NETDEV_CHANGE): enp3s0: link becomes ready
shaggy@Nightcrawler:~$ cat /etc/NetworkManager/NetworkManager.conf
[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

[ifupdown]
managed=false



OK, Just did a reboot on the server and I got this
> 
$ sudo ifdown enp3s0 && sudo ifup -v enp3s0
[sudo] password for shaggy: 
Configuring interface enp3s0=enp3s0 (inet)
/bin/run-parts --exit-on-error --verbose /etc/network/if-pre-up.d
run-parts: executing /etc/network/if-pre-up.d/ethtool
run-parts: executing /etc/network/if-pre-up.d/ifenslave
+ [ inet = meta ]
+ IF_BOND_SLAVES=
+ [  ]
+ [  ]
+ [ -z  ]
+ exit
run-parts: executing /etc/network/if-pre-up.d/vlan
run-parts: executing /etc/network/if-pre-up.d/wireless-tools
run-parts: executing /etc/network/if-pre-up.d/wpasupplicant
/bin/ip addr add 192.168.1.100/255.255.255.0 broadcast 192.168.1.255 	  dev enp3s0 label enp3s0
/bin/ip link set dev enp3s0   up
 /bin/ip route add default via 192.168.1.1  dev enp3s0 onlink 
/bin/run-parts --exit-on-error --verbose /etc/network/if-up.d
run-parts: executing /etc/network/if-up.d/000resolvconf
run-parts: executing /etc/network/if-up.d/avahi-autoipd
run-parts: executing /etc/network/if-up.d/avahi-daemon
run-parts: executing /etc/network/if-up.d/ethtool
run-parts: executing /etc/network/if-up.d/ifenslave
+ [ inet = meta ]
+ [  ]
run-parts: executing /etc/network/if-up.d/ip
run-parts: executing /etc/network/if-up.d/ntpdate
run-parts: executing /etc/network/if-up.d/openssh-server
run-parts: executing /etc/network/if-up.d/postfix
run-parts: executing /etc/network/if-up.d/upstart
run-parts: executing /etc/network/if-up.d/wpasupplicant


And

> 
$ ifconfig
enp3s0    Link encap:Ethernet  HWaddr 00:25:90:33:a2:66  
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::3106:b842:2cae:988/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:516395 errors:0 dropped:46 overruns:0 frame:0
          TX packets:145129 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:751223800 (751.2 MB)  TX bytes:180689275 (180.6 MB)
          Interrupt:16 Memory:fabe0000-fac00000 


enp4s0    Link encap:Ethernet  HWaddr 00:25:90:33:a2:67  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 Memory:face0000-fad00000 


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:5666 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5666 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1 
          RX bytes:1294341 (1.2 MB)  TX bytes:1294341 (1.2 MB)


shaggy@Nightcrawler:~$ dmesg | grep enp
[    3.075818] e1000e 0000:03:00.0 enp3s0: renamed from eth0
[    3.095400] e1000e 0000:04:00.0 enp4s0: renamed from eth1
[   46.694992] IPv6: ADDRCONF(NETDEV_UP): enp3s0: link is not ready
[   49.348957] e1000e: enp3s0 NIC Link is Up 1000 Mbps Full Duplex, Flow Control: Rx/Tx
[   49.349268] IPv6: ADDRCONF(NETDEV_CHANGE): enp3s0: link becomes ready
[   64.955701] IPv6: ADDRCONF(NETDEV_UP): enp4s0: link is not ready
[   65.032296] IPv6: ADDRCONF(NETDEV_UP): enp4s0: link is not ready
[  872.483739] e1000e: enp3s0 NIC Link is Down
[  873.983475] IPv6: ADDRCONF(NETDEV_UP): enp3s0: link is not ready
[  878.004877] e1000e: enp3s0 NIC Link is Up 1000 Mbps Full Duplex, Flow Control: Rx/Tx
[  878.005187] IPv6: ADDRCONF(NETDEV_CHANGE): enp3s0: link becomes ready
shaggy@Nightcrawler:~$ cat /etc/NetworkManager/NetworkManager.conf
[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq


[ifupdown]
managed=false


Another thing, I can see the shares on the server from my windows machine and can access them, but I cannot get out on the server. Ping gets Destination Host Unreachable if I try and ping the router, another system, or Google's DNS servers.

---

### Post by chili555 on 2017-04-09
You got the x.100 address this time. I wonder why it was unavailable previously. Did you confirm that it's outside the DHCP pool used in the router? Please confirm that there is no possible collisions.

What does this tell us?```
route -n

```Is there any improvement if you change to:```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

#source /etc/networks/interfaces.d/*

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto enp3s0
iface enp3s0 inet static
address 192.168.1.100
netmask 255.255.255.0
gateway 192.168.1.1
[COLOR="#FF0000"]dns-nameservers  8.8.8.8 8.8.4.4[/COLOR]
```

---

### Post by pratherdude2 on 2017-04-09
> **chili555 said:**
> You got the x.100 address this time. I wonder why it was unavailable previously. Did you confirm that it's outside the DHCP pool used in the router? Please confirm that there is no possible collisions.

Yes I have the router to hand out IP Address in the 200 range, Only other static IP is my printer at 108.

> What does this tell us?```
route -n
```

Print out of route
```

$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    202    0        0 enp3s0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 enp3s0
192.168.1.0     0.0.0.0         255.255.255.0   U     202    0        0 enp3s0
```

> 
Is there any improvement if you change to:```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

#source /etc/networks/interfaces.d/*

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto enp3s0
iface enp3s0 inet static
address 192.168.1.100
netmask 255.255.255.0
gateway 192.168.1.1
[COLOR=#FF0000]dns-nameservers  8.8.8.8 8.8.4.4[/COLOR]
```

Removed the router as a DNS server with no change, still cannot ping the router or anything outside of it. Can't get out with a browser either. Although I can now ping and connect to other systems on the network.

---

### Post by chili555 on 2017-04-09
What do the connection details look like on some other (Windows??) machine on the network?

---

### Post by pratherdude2 on 2017-04-09
> **chili555 said:**
> What do the connection details look like on some other (Windows??) machine on the network?


Windows IP Configuration




Ethernet adapter Local Area Connection:


   Connection-specific DNS Suffix  . : PK5001Z
   Link-local IPv6 Address . . . . . : fe80::c5e7:7edd:e48e:89bc%12
   IPv4 Address. . . . . . . . . . . : 192.168.1.232
   Subnet Mask . . . . . . . . . . . : 255.255.255.0
   Default Gateway . . . . . . . . . : 192.168.1.1


Ethernet adapter VirtualBox Host-Only Network:


   Connection-specific DNS Suffix  . :
   Link-local IPv6 Address . . . . . : fe80::3102:a4b2:da7b:3404%15
   IPv4 Address. . . . . . . . . . . : 192.168.56.1
   Subnet Mask . . . . . . . . . . . : 255.255.255.0
   Default Gateway . . . . . . . . . :


Tunnel adapter isatap.{48C71C57-FB69-4669-9D7F-A5C72AAF357D}:


   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . :


I'm going to double check the router also.

---

### Post by pratherdude2 on 2017-04-09
Thanks for the help Chili and sorry to waste your time. The problem was an issue in the modem/router from the phone company, they had that IP address locked for some reason. Had to do a hard reset on the modem to clear it and now I'm good to go.

---

### Post by chili555 on 2017-04-09
Not a waste at all. Some poor searcher will stumble on this thread and learn a lot from this sequence.

Glad it's working! Have fun!

---

