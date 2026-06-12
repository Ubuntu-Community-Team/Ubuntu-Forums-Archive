---
title: "Old IP comes back after every reboot"
date: 2019-10-19
forum: Networking &amp; Wireless
---

### Post by hikariws on 2019-10-19
When I installed Ubuntu on my server I had set its IP addr static as 192.168.1.2.

Later I changed my subnet to 192.168.52.0 and set it to get its addr from DHCP server.

Normally everything works fine, but when I reboot my server its old IP addr comes back somehow. It's accessible from LAN and is able to connect to any device on LAN, using its DHCP addr, but oddly it can't connect to Internet.

See:

```
$ ifconfig
enp1s0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.52.2  netmask 255.255.255.0  broadcast 192.168.52.255
        inet6 fdfa::e1b6:ea08:3491:5a56  prefixlen 64  scopeid 0x0<global>
        inet6 2804:xxx:xxx:5fed:a8d7:1a13:69a0:5dd1  prefixlen 64  scopeid 0x0<global>
        inet6 2804:yyy:yyy:dfb:635d:ac39:2ac4:448c  prefixlen 64  scopeid 0x0<global>
        inet6 fdfa::a8d7:1a13:69a0:5dd1  prefixlen 64  scopeid 0x0<global>
        inet6 2804:xxx:xxx:5fed:cf9d:4ca:68d4:7d7e  prefixlen 64  scopeid 0x0<global>
        inet6 2804:xxx:xxx:5fed::2  prefixlen 128  scopeid 0x0<global>
        inet6 2804:yyy:yyy:dfb::2  prefixlen 128  scopeid 0x0<global>
        inet6 2804:xxx:xxx:5fed:e1b6:ea08:3491:5a56  prefixlen 64  scopeid 0x0<global>
        inet6 fdfa::2  prefixlen 128  scopeid 0x0<global>
        inet6 2804:yyy:yyy:dfb:a8d7:1a13:69a0:5dd1  prefixlen 64  scopeid 0x0<global>
        inet6 fe80::b685:b26b:79a1:4011  prefixlen 64  scopeid 0x20<link>
        inet6 fdfa::87bb:2467:f949:2e0e  prefixlen 64  scopeid 0x0<global>
        ether e0:d5:5e:f2:64:5e  txqueuelen 1000  (Ethernet)
        RX packets 694695  bytes 104331390 (104.3 MB)
        RX errors 0  dropped 1  overruns 0  frame 0
        TX packets 705398  bytes 650543466 (650.5 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 1410944  bytes 298724888 (298.7 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 1410944  bytes 298724888 (298.7 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

```

There's no reference to any 192.168.1, but when I try to reach Internet:

```
$ ping 8.8.8.8
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.
From 192.168.1.2 icmp_seq=1 Destination Host Unreachable
From 192.168.1.2 icmp_seq=2 Destination Host Unreachable
From 192.168.1.2 icmp_seq=3 Destination Host Unreachable
From 192.168.1.2 icmp_seq=4 Destination Host Unreachable
From 192.168.1.2 icmp_seq=5 Destination Host Unreachable

```

How come that happens?

Then I use this command:

```
sudo ip addr del 192.168.1.2/24 dev enp1s0
```

And then it works again!

```
$ ping 8.8.8.8
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.
64 bytes from 8.8.8.8: icmp_seq=1 ttl=52 time=31.0 ms
64 bytes from 8.8.8.8: icmp_seq=2 ttl=52 time=31.9 ms
^C
--- 8.8.8.8 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1000ms
rtt min/avg/max/mdev = 31.076/31.491/31.907/0.451 ms

```

This seems like a ghost!

I could try to add a .sh to delete this addr during startup, but first I wanna try to figure out what's happening and fix it.

---

### Post by Skaperen on 2019-10-20
is every device on the physical LAN numbered in the subnet 192.168.52.0/24?  or are there any devices still numbered in the subnet 192.168.1.0/24?

i agree that a good goal is to get the fix made to the real cause of the problem.  everything else, such as the script to make setting the address right convenient is a work-around.  OTOH, such a script can be made non-executable, or can be a symlink that is changed to point to a do-nothing script, when you are investigating the problem.

please try this command and post the results:```
ip addr show enp1s0
```

---

### Post by hikariws on 2019-10-20
Thanks for reply!

What do you mean by "[COLOR=#000000]every device on the physical LAN"?

Before:
[/COLOR]```
$ ip addr show enp1s0
2: enp1s0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
    link/ether e0:d5:5e:f2:64:5e brd ff:ff:ff:ff:ff:ff
    inet 192.168.52.2/24 brd 192.168.52.255 scope global dynamic noprefixroute enp1s0
       valid_lft 2879sec preferred_lft 2879sec
    inet 192.168.1.2/24 brd 192.168.1.255 scope global enp1s0
       valid_lft forever preferred_lft forever
    inet6 fdfa::21bf:7278:c5af:aea2/64 scope global temporary dynamic
       valid_lft 604085sec preferred_lft 85581sec
    inet6 fdfa::87bb:2467:f949:2e0e/64 scope global mngtmpaddr noprefixroute
       valid_lft forever preferred_lft forever
    inet6 2804:xxx:xxx:1661:21bf:7278:c5af:aea2/64 scope global temporary dynamic
       valid_lft 23692sec preferred_lft 23692sec
    inet6 2804:xxx:xxx:1661:3b50:ae32:e50:8df2/64 scope global dynamic mngtmpaddr noprefixroute
       valid_lft 23692sec preferred_lft 23692sec
    inet6 2804:yyy:yyy:5fed:21bf:7278:c5af:aea2/64 scope global temporary dynamic
       valid_lft 66889sec preferred_lft 52489sec
    inet6 2804:yyy:yyy:5fed:cf9d:4ca:68d4:7d7e/64 scope global dynamic mngtmpaddr noprefixroute
       valid_lft 66889sec preferred_lft 52489sec
    inet6 fdfa::2/128 scope global noprefixroute
       valid_lft forever preferred_lft forever
    inet6 2804:xxx:xxx:1661::2/128 scope global dynamic noprefixroute
       valid_lft 23692sec preferred_lft 23692sec
    inet6 2804:yyy:yyy:5fed::2/128 scope global dynamic noprefixroute
       valid_lft 66889sec preferred_lft 52489sec
    inet6 fe80::b685:b26b:79a1:4011/64 scope link noprefixroute
       valid_lft forever preferred_lft forever

```[COLOR=#000000]

Indeed... 192.168.1 is there...

After:
[/COLOR]```
$ ip addr show enp1s0
2: enp1s0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
    link/ether e0:d5:5e:f2:64:5e brd ff:ff:ff:ff:ff:ff
    inet 192.168.52.2/24 brd 192.168.52.255 scope global dynamic noprefixroute enp1s0
       valid_lft 2695sec preferred_lft 2695sec
    inet6 fdfa::21bf:7278:c5af:aea2/64 scope global temporary dynamic
       valid_lft 603901sec preferred_lft 85397sec
    inet6 fdfa::87bb:2467:f949:2e0e/64 scope global mngtmpaddr noprefixroute
       valid_lft forever preferred_lft forever
    inet6 2804:xxx:xxx:1661:21bf:7278:c5af:aea2/64 scope global temporary dynamic
       valid_lft 23508sec preferred_lft 23508sec
    inet6 2804:xxx:xxx:1661:3b50:ae32:e50:8df2/64 scope global dynamic mngtmpaddr noprefixroute
       valid_lft 23508sec preferred_lft 23508sec
    inet6 2804:yyy:yyy:5fed:21bf:7278:c5af:aea2/64 scope global temporary dynamic
       valid_lft 66705sec preferred_lft 52305sec
    inet6 2804:yyy:yyy:5fed:cf9d:4ca:68d4:7d7e/64 scope global dynamic mngtmpaddr noprefixroute
       valid_lft 66705sec preferred_lft 52305sec
    inet6 fdfa::2/128 scope global noprefixroute
       valid_lft forever preferred_lft forever
    inet6 2804:xxx:xxx:1661::2/128 scope global dynamic noprefixroute
       valid_lft 23508sec preferred_lft 23508sec
    inet6 2804:yyy:yyy:5fed::2/128 scope global dynamic noprefixroute
       valid_lft 66705sec preferred_lft 52305sec
    inet6 fe80::b685:b26b:79a1:4011/64 scope link noprefixroute
       valid_lft forever preferred_lft forever

```

---

### Post by hikariws on 2019-10-20
Well it's not working anymore even after deleting the old IP. Is it possible to reset network settings back to default, so that Ubuntu detects it again and tries to use DHCP?

---

### Post by hikariws on 2019-10-20
Really sorry for the mess I'm doing. I was taking a look at Network Manager ([COLOR=#242729][FONT=Consolas]nm-connection-editor[/FONT][/COLOR]) and `[COLOR=#000000][FONT=&amp]sudo ip addr del 192.168.1.2/24 dev enp1s0` stopped working. 192.168.1 was gone but Internet remained unreachable.

I then had read about Netplan, I'm trying to set fixed address for the time being. Here's now my [/FONT][/COLOR]/etc/netplan/01-network-manager-all.yaml:

```
network:
  version: 2
  renderer: networkd
  ethernets:
    enp1s0:
      dhcp4: no
      dhcp6: no
      addresses: [192.168.52.2/24]
      gateway4: 192.168.52.1
      nameservers:
        addresses: [192.168.52.2]

```

... and old 192.168.1 is still around after reboot... and I'm getting IPv6 address, even with dhcp6 client disabled. Something is *very* odd.

Anyway, after reboot, I run `[COLOR=#000000][FONT=&amp]sudo netplan --debug apply` and magically Internet gets reachable! Here's its output![/FONT][/COLOR]

```
$ sudo netplan --debug apply** (generate:3587): DEBUG: 18:21:51.730: Processing input file /etc/netplan/01-network-manager-all.yaml..
** (generate:3587): DEBUG: 18:21:51.730: starting new processing pass
** (generate:3587): DEBUG: 18:21:51.730: enp1s0: setting default backend to 1
** (generate:3587): DEBUG: 18:21:51.730: Configuration is valid
** (generate:3587): DEBUG: 18:21:51.730: Generating output files..
** (generate:3587): DEBUG: 18:21:51.730: NetworkManager: definition enp1s0 is not for us (backend 1)
DEBUG:netplan generated networkd configuration changed, restarting networkd
DEBUG:no netplan generated NM configuration exists
DEBUG:enp1s0 not found in {}
DEBUG:Merged config:
network:
  bonds: {}
  bridges: {}
  ethernets:
    enp1s0:
      addresses:
      - 192.168.52.2/24
      dhcp4: false
      dhcp6: false
      gateway4: 192.168.52.1
      nameservers:
        addresses:
        - 192.168.52.2
  vlans: {}
  wifis: {}


DEBUG:Skipping non-physical interface: lo
DEBUG:device enp1s0 operstate is up, not changing
DEBUG:{}
DEBUG:netplan triggering .link rules for lo
DEBUG:netplan triggering .link rules for enp1s0

```

Then Internet works again and this is what I get

```

$ ip a show
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host
       valid_lft forever preferred_lft forever
2: enp1s0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
    link/ether e0:d5:5e:f2:64:5e brd ff:ff:ff:ff:ff:ff
    inet 192.168.52.2/24 brd 192.168.52.255 scope global enp1s0
       valid_lft forever preferred_lft forever
    inet6 2804:xxx:xxx:5fed::c36/128 scope global dynamic noprefixroute
       valid_lft 53550sec preferred_lft 39150sec
    inet6 2804:yyy:yyy:1661::c36/128 scope global dynamic noprefixroute
       valid_lft 31956sec preferred_lft 31956sec
    inet6 fdfa::c36/128 scope global noprefixroute
       valid_lft forever preferred_lft forever
    inet6 fdfa::e2d5:5eff:fef2:645e/64 scope global mngtmpaddr noprefixroute
       valid_lft forever preferred_lft forever
    inet6 2804:yyy:yyy:1661:e2d5:5eff:fef2:645e/64 scope global dynamic mngtmpaddr noprefixroute
       valid_lft 31956sec preferred_lft 31956sec
    inet6 2804:xxx:xxx:5fed:e2d5:5eff:fef2:645e/64 scope global dynamic mngtmpaddr noprefixroute
       valid_lft 53550sec preferred_lft 39150sec
    inet6 fdfa::87bb:2467:f949:2e0e/64 scope global mngtmpaddr noprefixroute
       valid_lft forever preferred_lft forever
    inet6 2804:yyy:yyy:1661:3b50:ae32:e50:8df2/64 scope global dynamic mngtmpaddr noprefixroute
       valid_lft 31956sec preferred_lft 31956sec
    inet6 2804:xxx:xxx:5fed:cf9d:4ca:68d4:7d7e/64 scope global dynamic mngtmpaddr noprefixroute
       valid_lft 53550sec preferred_lft 39150sec
    inet6 fe80::e2d5:5eff:fef2:645e/64 scope link
       valid_lft forever preferred_lft forever

```

Somehow DHCPv6 client is in action. My guess is that something else is messing with network management, adding old 192.168.1 and running DHCPv6 client.

I have no idea of what else to try :(

---

### Post by #&amp;thj^% on 2019-10-20
There is a lot of information on this page: [https://websiteforstudents.com/configure-static-ip-addresses-on-ubuntu-18-04-beta/](https://websiteforstudents.com/configure-static-ip-addresses-on-ubuntu-18-04-beta/)
Please take the time to read fully and with understanding. 
Good Luck :)

---

### Post by webaake on 2019-10-21
Did you check the file /etc/network/interfaces ?

---

