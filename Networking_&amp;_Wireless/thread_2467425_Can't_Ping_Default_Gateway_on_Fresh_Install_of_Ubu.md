---
title: "Can't Ping Default Gateway on Fresh Install of Ubuntu 20.04 LTS (Wifi Problems)"
date: 2021-09-26
forum: Networking &amp; Wireless
---

### Post by pi-pie on 2021-09-26
**Edit - Solved!:** I managed to get the internet working again after I manually changed the ip address on my laptop. I don't know why that worked but it did. 
For any other Linux Noobs that are having weird network issues and want to try changing the ip address, here is the process:
> open wifi settings
> on the 'IPv4' page select 'Manual' 
> run *route -n* in terminal to find your gateway address, destination address, and netmask. You'll need to install net-tools somehow to run *route -n*.
   - Note: You might see a 169.254.0.0 address as well, and it's my understanding that is there because you couldn't connect to wifi somehow. I just ignored it.
Here is the output when I ran it:
```

: route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.2.1     0.0.0.0         UG    20600  0        0 wlp4s0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlp4s0
192.168.2.0     0.0.0.0         255.255.255.0   U     600    0        0 wlp4s0

```
so the Gateway Address is 192.168.2.1 the destination address is 192.168.2.0 and the net mask is 255.255.255.0
> Choose an ip address by changing the last digit in the destination address and enter that into the 'address' field
  - Note: choose an ip address that your router can support, for example my router only supports ip addresses from 192.168.2.10 to 192.168.2.254
  - Note: try to choose an address not used by any other devices, this probably isn't an issue since most devices for casual users will have there devices choose automatic ip addresses so there (probably) shouldn't be any issues. But (I assume) this could cause a problem if two or more people choose the same manual ip address.
  - Note: You can see the ip addresses for devices on your network by going to http://<your gateway address>
> Enter the netmask and gateway addresses into there respective fields. In the end I input the following:
Address: 192.168.2.200
Netmask: 255.255.255.0
Gateway: 192.168.2.1


In the course of my research I also found that wifi problems could also be solved by:
**> **updating/upgrading ubuntu | run *sudo apt update && sudo apt upgrade -y*
**> **fixing the netmask in the kernel IP routing table
  -  using *sudo route add -net <your destination ip> gw <your gateway ip> netmask <your netmask> dev <your interface>*
       -  for example: [I]sudo route add -net 169.254.0.0 gw 0.0.0.0 netmask 255.255.0.0 dev wlp4s0
  -  use ip route add <your network ip>/<cidr> via <your gateway ip>[/I][I] dev <your interface>
       -  for example: sudo ip route add 172.16.0.0/24 via 0.0.0.0 dev wlp4s0
[/I]  -  see [https://www.poftut.com/add-new-route-ubuntu-linux/](https://www.poftut.com/add-new-route-ubuntu-linux/)
**> **disabling firewall | *sudo ufw disable*
**> **fixing problems with the wireless driver
  -  run *sudo lshw -C network *to find out your wireless hardware
  -  reinstall bcmwl if you have a broadcom driver | run *sudo apt-get --reinstall install bcmwl-kernel-source*
  -  see [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)
**> **restarting network manager | *sudo service network-manager restart*
**> **editing the netplan file | run *sudo nano /etc/netplan/*.yaml* to open
**> **editing the network manager config file | *sudo nano /etc/NetworkManager/NetworkManager.conf*
**> **changing band selection from automatic to force 2.4GHz wifi, if the router can't support 5GHz| run *nm-connection-editor*
**> **adding/changing dns servers. If *ping 8.8.8.8 *gives you something but you can't access the internet it's probably a problem with the dns servers, edit the nameservers protion of the netplan file or go into wifi settings and add ip addresses to the dns field. 8.8.8.8 and 8.8.4.4 are the ip addresses for the primary and secondary dns servers of Google Public DNS and should work.
**> **rebooting a few times

Hopefully this helps someone!


------
[B]Original Post:
[/B]------

I just installed Ubuntu 20.04 LTS on my old Macbook, but I can't reach to the internet. My wifi network shows up in 'available networks' and I can connect to it - but when I do there's a question mark on the wifi icon and no webpages will load. But, for some reason when I connect to my iPhone hotspot through wifi everything is fine (which is how I'm writing this now) which makes me think this is a routing issue, but I'm not sure.

The 'ip a' command lists the proper gateway (192.168.2.1) but I can't ping it (I am trying to ping the gateway when I am connected to my wifi network, not the iphone hotspot). From a different computer pinging 192.168.2.1 works fine, and from that computer the internet works perfectly - so this isn't an issue with the modem. The modem also allows for both 5GHz and 2.4 GHz connections so the automatic band selection isn't the problem either. 

Any help would be appreciated.

-----

route -n
```

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.2.1     0.0.0.0         UG    20600  0        0 wlp4s0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlp4s0
192.168.2.0     0.0.0.0         255.255.255.0   U     600    0        0 wlp4s0

```

ip r
```

default via 192.168.2.1 dev wlp4s0 proto dhcp metric 20600
169.254.0.0/16 dev wlp4s0 scope link metric 1000
192.168.2.0/24 dev wlp4s0 proto kernel scope link src 192.168.2.14 metric 600

```

ip a
```

1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host
       valid_lft forever preferred_lft forever
2: wlp4s0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
    link/ether 28:cf:e9:20:66:91 brd ff:ff:ff:ff:ff:ff
    inet 192.168.2.14/24 brd 192.168.2.255 scope global dynamic noprefixroute wlp4s0
       valid_lft 259152sec preferred_lft 259152sec
    inet6 fe80::10b2:2668:d04b:4e18/64 scope link noprefixroute
       valid_lft forever preferred_lft forever

```

ifconfig
```

lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 7198  bytes 641702 (641.7 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 7198  bytes 641702 (641.7 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

wlp4s0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.2.14  netmask 255.255.255.0  broadcast 192.168.2.255
        inet6 fe80::10b2:2668:d04b:4e18  prefixlen 64  scopeid 0x20<link>
        ether 28:cf:e9:20:66:91  txqueuelen 1000  (Ethernet)
        RX packets 15733  bytes 14738047 (14.7 MB)
        RX errors 0  dropped 0  overruns 0  frame 21658
        TX packets 13618  bytes 2453466 (2.4 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
        device interrupt 17  

```

telnet 192.168.2.1
```

Trying 192.168.2.1...
telnet: Unable to connect to remote host: No route to host

```

nano /etc/netplan/*.yaml
Original contents didn't have anything after the renderer line
(and, the access-points field has the correct router names/passwords)
```

# Let NetworkManager manage all devices on this system
network:
  version: 2
  renderer: NetworkManager
  wifis:
   wlp4s0:
    dhcp4: true
    access-points:
     "****":
       password: "****"
    addresses:
      - 192.168.2.0/24
    gateway4: 192.168.2.1
    nameservers:
      addresses:
        - 8.8.8.8
        - 8.8.4.4

```



nano /etc/NetworkManager/NetworkManager.conf
```
                                
[main]
plugins=ifupdown,keyfile

[ifupdown]
managed=false

[device]
wifi.scan-rand-mac-address=no

```

ip neighbor show
```

192.168.2.1 dev wlp4s0  INCOMPLETE

```

iptables -L -v -n
```

Chain INPUT (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination        

Chain FORWARD (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination        

Chain OUTPUT (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination

```

iptables -t nat -L -v -n
```

Chain PREROUTING (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         

Chain INPUT (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         

Chain OUTPUT (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         

Chain POSTROUTING (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         

```


nano /etc/resolv.conf
```

# This file is managed by man:systemd-resolved(8). Do not edit.
#
# This is a dynamic resolv.conf file for connecting local clients to the
# internal DNS stub resolver of systemd-resolved. This file lists all
# configured search domains.
#
# Run "resolvectl status" to see details about the uplink DNS servers
# currently in use.
#
# Third party programs must not access this file directly, but only through the
# symlink at /etc/resolv.conf. To manage man:resolv.conf(5) in a different way,
# replace this symlink by a static file or a different symlink.
#
# See man:systemd-resolved.service(8) for details about the supported modes of
# operation for /etc/resolv.conf.

nameserver 127.0.0.53
options edns0 trust-ad

```

lspci -k
(just the network stuff)
```

04:00.0 Network controller: Broadcom Inc. and subsidiaries BCM4331 802.11a/b/g/n (rev 02)
    Subsystem: Apple Inc. AirPort Extreme
    Kernel driver in use: wl
    Kernel modules: bcma, wl

```

ping 192.168.2.1
```

PING 192.168.2.1 (192.168.2.1) 56(84) bytes of data.
From 192.168.2.14 icmp_seq=1 Destination Host Unreachable
From 192.168.2.14 icmp_seq=2 Destination Host Unreachable
From 192.168.2.14 icmp_seq=3 Destination Host Unreachable
From 192.168.2.14 icmp_seq=4 Destination Host Unreachable
From 192.168.2.14 icmp_seq=5 Destination Host Unreachable
^C
--- 192.168.2.1 ping statistics ---
7 packets transmitted, 0 received, +5 errors, 100% packet loss, time 6060ms
pipe 3

```

ping 8.8.8.8
```

PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.
From 192.168.2.14 icmp_seq=1 Destination Host Unreachable
From 192.168.2.14 icmp_seq=2 Destination Host Unreachable
From 192.168.2.14 icmp_seq=3 Destination Host Unreachable
From 192.168.2.14 icmp_seq=4 Destination Host Unreachable
^C
--- 8.8.8.8 ping statistics ---
6 packets transmitted, 0 received, +4 errors, 100% packet loss, time 5070ms
pipe 3

```

---

