---
title: "Looking for assistance with Netplan, bonding, Internet on untagged vlan bond0, Inside"
date: 2023-10-15
forum: Networking &amp; Wireless
---

### Post by david144 on 2023-10-15
[I][B][U]Looking for assistance with Netplan, bonding, Internet on untagged vlan bond0, Inside networks on tagged vlans on bond0, and inter-VLAN Routing and Masquerade
[/U][/B][/I]
(Saving for solution at top)

---

### Post by david144 on 2023-10-15
TLDR: feels like the kernel is randomly selecting interfaces for IP's in the same subnet and doesn't want to respond to ARPs for itself.


Hello everyone, thank you in advance for taking the time to read this long post. I'm replacing my work supplied Next Generation Palo Alto Firewall, that I'm turning back in to the office, with my ubuntu server with multiple nics that I want to setup in an lacp bond. Hopefully if this gets solved this thread will help others, I have not found a decent write up or examples of doing what I'm trying in that the Ubuntu server is the router for all networks not bridging to other routers.


Problem:
I'm seeing my lacp link as up, bond0 is getting IP from DHCP and as source IP bond0 can ping to the internet, unfortunately my vlans are not masquerading/routing, right now I'm just working with vl777 to try and get to make sure I can route through the masquerade just to ping the bond0's gateway.

---

### Post by david144 on 2023-10-15
Hear is a graphic which may help.
[https://ubuntuforums.org/attachment.php?attachmentid=292863&stc=1](https://ubuntuforums.org/attachment.php?attachmentid=292863&stc=1)

---

### Post by david144 on 2023-10-15
Packet Captures

---

### Post by david144 on 2023-10-15
_Observations:_
1. my Management IP for the host on the Qualcomm nic enp6s0 can ping the switches in the same vlan, but not the bond0 vl777 interface, tcpdump is showing arp requests for 10.7.77.2 wanting to know who is 10.7.77.1 but no response
2. my PC connected in the management network with USB nic, and the switches can ping the Ubuntu host on both the bond0 vl777 interface (10.7.77.1), and the Qualcomm nic (10.7.77.2) however responses for both IPs come from enp6s0, they sometimes see the same MAC address for both IPs (that of the bond) or they will be swapped (IP for vl777 will show enp6s0's MAC and vice versa)
3. the bond0 vl777 (10.7.77.1) interface can ping the switches but cannot ping the enp6s0 (10.7.77.2), tcpdump on enp6s0 interface is showing the echo requests coming in, but no echo reply going out (presumably because of the incomplete ARP state)
4. I also see the ARP requests for who has 10.7.77.1 tell 10.7.77.2 coming from both the enp6s0 AND vl777 interfaces


_Feelings:_
(it's ok to cry..)
1. Ubuntu is very confused on why I have two different interfaces in the same network, one of which is the default route for the other. In my head this seems very logical and should work but I'm not sure if I've missed some critical component of setting up this routing.

--edit: On my Palo and Juniper firewalls the management plane is handled separate from the dataplane, so part of the problem I imagine here is that the two interfaces are in the same route table. Maybe I need to try VRFs for every VLAN and the management interface? still feels like I've got a bigger problem with the ARP between enp6s0 and vl777. :confused:


I haven't spent time testing the other vlan interfaces. I want vl777 working before I move forward.

---

### Post by david144 on 2023-10-15
Observation 1, incomplete ARP for vl777 IP 10.7.77.1
```

root@<redacted>:/home/dave# ping -I enp6s0 -c 1 10.7.77.1
PING 10.7.77.1 (10.7.77.1) from 10.7.77.2 enp6s0: 56(84) bytes of data.
From 10.7.77.2 icmp_seq=1 Destination Host Unreachable


--- 10.7.77.1 ping statistics ---
1 packets transmitted, 0 received, +1 errors, 100% packet loss, time 0ms


root@<redacted>:/home/dave# ping -I enp6s0 -c 1 10.7.77.3
PING 10.7.77.3 (10.7.77.3) from 10.7.77.2 enp6s0: 56(84) bytes of data.
64 bytes from 10.7.77.3: icmp_seq=1 ttl=64 time=0.774 ms


--- 10.7.77.3 ping statistics ---
1 packets transmitted, 1 received, 0% packet loss, time 0ms
rtt min/avg/max/mdev = 0.774/0.774/0.774/0.000 ms
root@<redacted>:/home/dave# ping -I enp6s0 -c 1 10.7.77.4
PING 10.7.77.4 (10.7.77.4) from 10.7.77.2 enp6s0: 56(84) bytes of data.
64 bytes from 10.7.77.4: icmp_seq=1 ttl=64 time=0.785 ms


--- 10.7.77.4 ping statistics ---
1 packets transmitted, 1 received, 0% packet loss, time 0ms
rtt min/avg/max/mdev = 0.785/0.785/0.785/0.000 ms


root@<redacted>:/home/dave# arp -a
<redacted> (10.7.77.1) at <incomplete> on enp6s0                       # incomplete arp  :'(
? (10.7.77.3) at 2c:fa:a2:aa:c0:54 [ether] on enp6s0
? (10.7.77.4) at 2c:fa:a2:58:45:a2 [ether] on vl777
_gateway (192.168.4.1) at 14:dd:a9:97:76:70 [ether] on bond0
? (10.7.77.254) at 00:24:9b:16:b8:97 [ether] on vl777
? (10.7.77.4) at 2c:fa:a2:58:45:a2 [ether] on enp6s0
? (10.7.77.3) at 2c:fa:a2:aa:c0:54 [ether] on vl777
<redacted> (192.168.4.103) at <incomplete> on vl777
? (10.7.77.254) at 00:24:9b:16:b8:97 [ether] on enp6s0
_gateway (192.168.4.1) at <incomplete> on vl777
```




Observation 2, ARP tables from PC and Switch:
```

--PC--  (this moment they looked swapped)
Interface: 10.7.77.254 --- 0xb
  Internet Address      Physical Address      Type
  10.7.77.1             00-21-97-8e-84-42     dynamic                                            # this should be 92-ca-c3-7a-51-ba
  10.7.77.2             92-ca-c3-7a-51-ba     dynamic                                            # this should be 00-21-97-8e-84-42
  10.7.77.3             2c-fa-a2-aa-c0-54     dynamic
  10.7.77.4             2c-fa-a2-58-45-a2     dynamic


--SWITCH--   ( this moment they looked duplicated like both were on the bond )
<redacted>-OS6450-24> show arp


Total 3 arp entries
 Flags (P=Proxy, V=VRRP)


 IP Addr           Hardware Addr       Type       Flags   Port     Interface   Name
-----------------+-------------------+----------+-------+--------+-----------+----------
 10.7.77.1         92:ca:c3:7a:51:ba   DYNAMIC                0/2  vlan 777
 10.7.77.2         92:ca:c3:7a:51:ba   DYNAMIC                0/2  vlan 777                        # this should be 00:21:97:8e:84:42
 10.7.77.254       00:24:9b:16:b8:97   DYNAMIC                0/1  vlan 777
```




Observation 3, ICMP echo request from 10.7.77.1 getting to enp6s0 interface, but no echo reply, and no response to the arp Request who-has:
```

root@<redacted>:/home/dave# tcpdump -evvvnni enp6s0 not host 10.7.77.254 -s 65535
tcpdump: listening on enp6s0, link-type EN10MB (Ethernet), snapshot length 65535 bytes
05:32:42.192512 92:ca:c3:7a:51:ba > 00:21:97:8e:84:42, ethertype IPv4 (0x0800), length 98: (tos 0x0, ttl 64, id 41111, offset 0, flags [DF], proto ICMP (1), length 84)
    10.7.77.1 > 10.7.77.2: ICMP echo request, id 6, seq 1, length 64
05:32:43.201292 92:ca:c3:7a:51:ba > 00:21:97:8e:84:42, ethertype IPv4 (0x0800), length 98: (tos 0x0, ttl 64, id 41135, offset 0, flags [DF], proto ICMP (1), length 84)
    10.7.77.1 > 10.7.77.2: ICMP echo request, id 6, seq 2, length 64
05:32:44.225215 92:ca:c3:7a:51:ba > 00:21:97:8e:84:42, ethertype IPv4 (0x0800), length 98: (tos 0x0, ttl 64, id 41244, offset 0, flags [DF], proto ICMP (1), length 84)
    10.7.77.1 > 10.7.77.2: ICMP echo request, id 6, seq 3, length 64
05:32:45.249218 92:ca:c3:7a:51:ba > 00:21:97:8e:84:42, ethertype IPv4 (0x0800), length 98: (tos 0x0, ttl 64, id 41485, offset 0, flags [DF], proto ICMP (1), length 84)
    10.7.77.1 > 10.7.77.2: ICMP echo request, id 6, seq 4, length 64
05:32:46.273222 92:ca:c3:7a:51:ba > 00:21:97:8e:84:42, ethertype IPv4 (0x0800), length 98: (tos 0x0, ttl 64, id 41520, offset 0, flags [DF], proto ICMP (1), length 84)
    10.7.77.1 > 10.7.77.2: ICMP echo request, id 6, seq 5, length 64
05:32:47.297221 92:ca:c3:7a:51:ba > 00:21:97:8e:84:42, ethertype IPv4 (0x0800), length 98: (tos 0x0, ttl 64, id 41677, offset 0, flags [DF], proto ICMP (1), length 84)
    10.7.77.1 > 10.7.77.2: ICMP echo request, id 6, seq 6, length 64
05:32:47.425192 92:ca:c3:7a:51:ba > 00:21:97:8e:84:42, ethertype ARP (0x0806), length 60: Ethernet (len 6), IPv4 (len 4), Request who-has 10.7.77.2 tell 10.7.77.1, length 46
05:32:48.449202 92:ca:c3:7a:51:ba > 00:21:97:8e:84:42, ethertype ARP (0x0806), length 60: Ethernet (len 6), IPv4 (len 4), Request who-has 10.7.77.2 tell 10.7.77.1, length 46
05:32:49.473192 92:ca:c3:7a:51:ba > 00:21:97:8e:84:42, ethertype ARP (0x0806), length 60: Ethernet (len 6), IPv4 (len 4), Request who-has 10.7.77.2 tell 10.7.77.1, length 46
```




Observation 4, Interesting ARP behaviour seen, but not written in pcap:
```

* "In" - the packet was unicast to the host;
* "B" - the packet was broadcast;
* "M" - the packet wasn't broadcast but was multicast;
* "P" - the packet was unicast to some other host and this host received it because the network adapter was in promiscuous mode;
* "Out" - the packet was sent by the host and "wrapped around" and delivered to the PF_PACKET socket.


root@<redacted>:/home/dave# tcpdump -nni any not host 10.7.77.254 | grep 10.7.77.1
tcpdump: data link type LINUX_SLL2
tcpdump: verbose output suppressed, use -v[v]... for full protocol decode
listening on any, link-type LINUX_SLL2 (Linux cooked v2), snapshot length 262144 bytes
23:01:17.028236 enp6s0 Out ARP, Request who-has 10.7.77.1 tell 10.7.77.2, length 28
23:01:17.028276 vl777 B   ARP, Request who-has 10.7.77.1 tell 10.7.77.2, length 46
23:01:18.052237 enp6s0 Out ARP, Request who-has 10.7.77.1 tell 10.7.77.2, length 28
23:01:18.052278 vl777 B   ARP, Request who-has 10.7.77.1 tell 10.7.77.2, length 46
23:01:19.076526 enp6s0 Out ARP, Request who-has 10.7.77.1 tell 10.7.77.2, length 28
23:01:19.076545 vl777 B   ARP, Request who-has 10.7.77.1 tell 10.7.77.2, length 46
23:01:20.100221 enp6s0 Out ARP, Request who-has 10.7.77.1 tell 10.7.77.2, length 28
23:01:20.100242 vl777 B   ARP, Request who-has 10.7.77.1 tell 10.7.77.2, length 46
23:01:21.124224 enp6s0 Out ARP, Request who-has 10.7.77.1 tell 10.7.77.2, length 28
23:01:21.124243 vl777 B   ARP, Request who-has 10.7.77.1 tell 10.7.77.2, length 46
23:01:22.148332 enp6s0 Out ARP, Request who-has 10.7.77.1 tell 10.7.77.2, length 28
23:01:22.148351 vl777 B   ARP, Request who-has 10.7.77.1 tell 10.7.77.2, length 46
23:01:23.172226 enp6s0 Out ARP, Request who-has 10.7.77.1 tell 10.7.77.2, length 28
23:01:23.172249 vl777 B   ARP, Request who-has 10.7.77.1 tell 10.7.77.2, length 46
23:01:24.196220 enp6s0 Out ARP, Request who-has 10.7.77.1 tell 10.7.77.2, length 28
23:01:24.196247 vl777 B   ARP, Request who-has 10.7.77.1 tell 10.7.77.2, length 46
23:01:25.220390 enp6s0 Out ARP, Request who-has 10.7.77.1 tell 10.7.77.2, length 28
23:01:25.220415 vl777 B   ARP, Request who-has 10.7.77.1 tell 10.7.77.2, length 46
23:01:26.244229 enp6s0 Out ARP, Request who-has 10.7.77.1 tell 10.7.77.2, length 28
23:01:26.244248 vl777 B   ARP, Request who-has 10.7.77.1 tell 10.7.77.2, length 46
23:01:27.268224 enp6s0 Out ARP, Request who-has 10.7.77.1 tell 10.7.77.2, length 28
23:01:27.268244 vl777 B   ARP, Request who-has 10.7.77.1 tell 10.7.77.2, length 46
23:01:28.292349 enp6s0 Out ARP, Request who-has 10.7.77.1 tell 10.7.77.2, length 28
23:01:28.292376 vl777 B   ARP, Request who-has 10.7.77.1 tell 10.7.77.2, length 46
23:01:29.316229 enp6s0 Out ARP, Request who-has 10.7.77.1 tell 10.7.77.2, length 28
```

---

### Post by david144 on 2023-10-15
Version
```

root@<redacted>:/# lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 22.04.3 LTS
Release:        22.04
Codename:       jammy


root@<redacted>:/#uname -nra
Linux <redacted> 5.15.0-86-generic #96-Ubuntu SMP Wed Sep 20 08:23:49 UTC 2023 x86_64 x86_64 x86_64 GNU/Linux
```




I have a Intel dual port NIC (82546EB), Intel quad port NIC (82575GB), and an onboard Qualcomm single port NIC (Atheros):
```

root@<redacted>:/etc# lspci | grep -i net
03:00.0 Ethernet controller: Intel Corporation 82575GB Gigabit Network Connection (rev 02)
03:00.1 Ethernet controller: Intel Corporation 82575GB Gigabit Network Connection (rev 02)
04:00.0 Ethernet controller: Intel Corporation 82575GB Gigabit Network Connection (rev 02)
04:00.1 Ethernet controller: Intel Corporation 82575GB Gigabit Network Connection (rev 02)
06:00.0 Ethernet controller: Qualcomm Atheros Attansic L1 Gigabit Ethernet (rev b0)
07:01.0 Ethernet controller: Intel Corporation 82546EB Gigabit Ethernet Controller (Copper) (rev 03)
07:01.1 Ethernet controller: Intel Corporation 82546EB Gigabit Ethernet Controller (Copper) (rev 03)


root@<redacted>:/etc# ifconfig -a | grep flags
bond0: flags=5187<UP,BROADCAST,RUNNING,MASTER,MULTICAST>  mtu 1500
enp3s0f0: flags=6211<UP,BROADCAST,RUNNING,SLAVE,MULTICAST>  mtu 1500
enp3s0f1: flags=6211<UP,BROADCAST,RUNNING,SLAVE,MULTICAST>  mtu 1500
enp4s0f0: flags=6211<UP,BROADCAST,RUNNING,SLAVE,MULTICAST>  mtu 1500
enp4s0f1: flags=6211<UP,BROADCAST,RUNNING,SLAVE,MULTICAST>  mtu 1500
enp6s0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
enp7s1f0: flags=6211<UP,BROADCAST,RUNNING,SLAVE,MULTICAST>  mtu 1500
enp7s1f1: flags=4099<UP,BROADCAST,MULTICAST>  mtu 1500                     #currently not a bond0 interface, and not connected (L1 down)
lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
vl2: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
vl3: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
vl4: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
vl777: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
vl1000: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
vl2000: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500


single nic:
root@<redacted>:/usr/share/ufw/iptables# ip link show enp6s0
2: enp6s0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP mode DEFAULT group default qlen 1000
    link/ether 00:21:97:8e:84:42 brd ff:ff:ff:ff:ff:ff


bond:
root@<redacted>:/etc# ip link show enp7s1f1
6: enp7s1f1: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc fq_codel state DOWN mode DEFAULT group default qlen 1000
    link/ether 1c:fd:08:76:7d:9d brd ff:ff:ff:ff:ff:ff
root@<redacted>:/etc# ip link show enp3s0f0
3: enp3s0f0: <BROADCAST,MULTICAST,SLAVE,UP,LOWER_UP> mtu 1500 qdisc mq master bond0 state UP mode DEFAULT group default qlen 1000
    link/ether 92:ca:c3:7a:51:ba brd ff:ff:ff:ff:ff:ff permaddr 00:1b:21:49:27:b0
root@<redacted>:/etc# ip link show enp3s0f1
5: enp3s0f1: <BROADCAST,MULTICAST,SLAVE,UP,LOWER_UP> mtu 1500 qdisc mq master bond0 state UP mode DEFAULT group default qlen 1000
    link/ether 92:ca:c3:7a:51:ba brd ff:ff:ff:ff:ff:ff permaddr 00:1b:21:49:27:b1
root@<redacted>:/etc# ip link show enp4s0f0
7: enp4s0f0: <BROADCAST,MULTICAST,SLAVE,UP,LOWER_UP> mtu 1500 qdisc mq master bond0 state UP mode DEFAULT group default qlen 1000
    link/ether 92:ca:c3:7a:51:ba brd ff:ff:ff:ff:ff:ff permaddr 00:1b:21:49:27:b4
root@<redacted>:/etc# ip link show enp4s0f1
8: enp4s0f1: <BROADCAST,MULTICAST,SLAVE,UP,LOWER_UP> mtu 1500 qdisc mq master bond0 state UP mode DEFAULT group default qlen 1000
    link/ether 92:ca:c3:7a:51:ba brd ff:ff:ff:ff:ff:ff permaddr 00:1b:21:49:27:b5
root@<redacted>:/etc# ip link show enp7s1f0
4: enp7s1f0: <BROADCAST,MULTICAST,SLAVE,UP,LOWER_UP> mtu 1500 qdisc fq_codel master bond0 state UP mode DEFAULT group default qlen 1000
    link/ether 92:ca:c3:7a:51:ba brd ff:ff:ff:ff:ff:ff permaddr 1c:fd:08:76:7d:9c
root@<redacted>:/etc# ip link show enp7s1f1
6: enp7s1f1: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc fq_codel state DOWN mode DEFAULT group default qlen 1000
    link/ether 1c:fd:08:76:7d:9d brd ff:ff:ff:ff:ff:ff
```

---

### Post by david144 on 2023-10-15
The bond will be just the two Intel NICs (currently enp7s1f1 is not included in the bond as I was temporarily plugging it in using DHCP without the bond for apt installs, but 5 vs 6 interfaces shouldn't be a problem for lacp)


/etc/netplan/00-installer-config:
```

network:
  version: 2
  ethernets:
    enp6s0:
      dhcp4: false
      match:
        macaddress: 00:21:97:8e:84:42
      addresses: [ 10.7.77.2/24 ]
      routes:
        - to: default
          via: 10.7.77.1
      nameservers:
        search: [mgmt.<redacted>]
        addresses: [8.8.8.8, 1.1.1.1]
    enp7s1f0:
      dhcp4: false
    enp7s1f1:
      dhcp4: true
    enp3s0f0:
      dhcp4: false
    enp3s0f1:
      dhcp4: false
    enp4s0f0:
      dhcp4: false
    enp4s0f1:
      dhcp4: false
  bonds:
# outside/untrust/Internet/Big-Bad-World
    bond0:
      mtu: 1500
      interfaces: [ enp3s0f0, enp3s0f1, enp4s0f0, enp4s0f1, enp7s1f0 ]
      parameters:
        mode: 802.3ad
        mii-monitor-interval: 1
        gratuitious-arp: 5
      dhcp4: true
#
  vlans:
# mgmt-net
    vl777:
      dhcp4: false
      link: bond0
      id: 777
      addresses: [ 10.7.77.1/24 ]
      mtu: 1500
# tenant-net
    vl2:
      dhcp4: false
      id: 2
      link: bond0
      addresses: [ 10.0.2.1/24 ]
      mtu: 1500
# guest-net
    vl3:
      dhcp4: false
      id: 3
      link: bond0
      addresses: [ 10.0.3.1/24 ]
      mtu: 1500
# WorkRAP-outside
    vl4:
      dhcp4: false
      id: 4
      link: bond0
      addresses: [ 10.0.4.1/24 ]
      mtu: 1500
# dave-net                                            # this is currently disabled as I didn't want the route table getting confused while I test it behind my existing asus wifi-router using same network
#    vl192:
#      dhcp4: false
#      id: 192
#      link: bond0
#      addresses: [ 192.168.4.1/24 ]
#      mtu: 1500
# security-net
    vl1000:
      dhcp4: false
      id: 1000
      link: bond0
      addresses: [ 10.100.0.1/16 ]
      mtu: 1500
# plex-net
    vl2000:
      dhcp4: false
      id: 2000
      link: bond0
      addresses: [ 10.200.0.1/16 ]
      mtu: 1500
```




netstat -nr:
```

Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
0.0.0.0         10.7.77.1       0.0.0.0         UG        0 0          0 enp6s0
0.0.0.0         192.168.4.1     0.0.0.0         UG        0 0          0 bond0
8.8.8.8         192.168.4.1     255.255.255.255 UGH       0 0          0 bond0
10.0.2.0        0.0.0.0         255.255.255.0   U         0 0          0 vl2
10.0.3.0        0.0.0.0         255.255.255.0   U         0 0          0 vl3
10.0.4.0        0.0.0.0         255.255.255.0   U         0 0          0 vl4
10.7.77.0       0.0.0.0         255.255.255.0   U         0 0          0 enp6s0
10.7.77.0       0.0.0.0         255.255.255.0   U         0 0          0 vl777
10.100.0.0      0.0.0.0         255.255.0.0     U         0 0          0 vl1000
10.200.0.0      0.0.0.0         255.255.0.0     U         0 0          0 vl2000
192.168.4.0     0.0.0.0         255.255.255.0   U         0 0          0 bond0
192.168.4.1     0.0.0.0         255.255.255.255 UH        0 0          0 bond0
```

---

### Post by david144 on 2023-10-15
/etc/sysctl.conf:
```

net.ipv4.ip_forward=1
fs.inotify.max_user_watches = 300000
```




/etc/default/ufw:
```

IPV6=yes
DEFAULT_INPUT_POLICY="DROP"
DEFAULT_OUTPUT_POLICY="ACCEPT"
DEFAULT_FORWARD_POLICY="ACCEPT"
DEFAULT_APPLICATION_POLICY="SKIP"
MANAGE_BUILTINS=no
IPT_SYSCTL=/etc/ufw/sysctl.conf
IPT_MODULES=""
```

---

### Post by david144 on 2023-10-15
/etc/ufw/before.rules:
```

*nat
:POSTROUTING ACCEPT [0:0]
#-A POSTROUTING -s 192.168.4.0/24 -o bond0 -j MASQUERADE  # this is currently disabled as I didn't want the route table getting confused while I test it behind my existing asus wifi-router using same network
-A POSTROUTING -s 10.0.2.0/24 -o bond0 -j MASQUERADE
-A POSTROUTING -s 10.0.3.0/24 -o bond0 -j MASQUERADE
-A POSTROUTING -s 10.0.4.0/24 -o bond0 -j MASQUERADE
-A POSTROUTING -s 10.7.77.0/24 -o bond0 -j MASQUERADE
-A POSTROUTING -s 10.100.0.0/16 -o bond0 -j MASQUERADE
-A POSTROUTING -s 10.200.0.0/16 -o bond0 -j MASQUERADE
COMMIT
*filter
:ufw-before-input - [0:0]
:ufw-before-output - [0:0]
:ufw-before-forward - [0:0]
:ufw-not-local - [0:0]
-A ufw-before-input -i lo -j ACCEPT
-A ufw-before-output -o lo -j ACCEPT
-A ufw-before-input -m conntrack --ctstate RELATED,ESTABLISHED -j ACCEPT
-A ufw-before-output -m conntrack --ctstate RELATED,ESTABLISHED -j ACCEPT
-A ufw-before-forward -m conntrack --ctstate RELATED,ESTABLISHED -j ACCEPT
-A ufw-before-input -m conntrack --ctstate INVALID -j ufw-logging-deny
-A ufw-before-input -m conntrack --ctstate INVALID -j DROP
-A ufw-before-input -p icmp --icmp-type destination-unreachable -j ACCEPT
-A ufw-before-input -p icmp --icmp-type time-exceeded -j ACCEPT
-A ufw-before-input -p icmp --icmp-type parameter-problem -j ACCEPT
-A ufw-before-input -p icmp --icmp-type echo-request -j ACCEPT
-A ufw-before-forward -p icmp --icmp-type destination-unreachable -j ACCEPT
-A ufw-before-forward -p icmp --icmp-type time-exceeded -j ACCEPT
-A ufw-before-forward -p icmp --icmp-type parameter-problem -j ACCEPT
-A ufw-before-forward -p icmp --icmp-type echo-request -j ACCEPT
-A ufw-before-input -p udp --sport 67 --dport 68 -j ACCEPT
-A ufw-before-input -j ufw-not-local
-A ufw-not-local -m addrtype --dst-type LOCAL -j RETURN
-A ufw-not-local -m addrtype --dst-type MULTICAST -j RETURN
-A ufw-not-local -m addrtype --dst-type BROADCAST -j RETURN
-A ufw-not-local -m limit --limit 3/min --limit-burst 10 -j ufw-logging-deny
-A ufw-not-local -j DROP
-A ufw-before-input -p udp -d 224.0.0.251 --dport 5353 -j ACCEPT
-A ufw-before-input -p udp -d 239.255.255.250 --dport 1900 -j ACCEPT
COMMIT
```




/usr/share/ufw/iptables/before.rules
```

root@<redacted>:/usr/share/ufw/iptables# cat before.rules
*filter
:ufw-before-input - [0:0]
:ufw-before-output - [0:0]
:ufw-before-forward - [0:0]
:ufw-not-local - [0:0]
-A ufw-before-input -i lo -j ACCEPT
-A ufw-before-output -o lo -j ACCEPT
-A ufw-before-input -m conntrack --ctstate RELATED,ESTABLISHED -j ACCEPT
-A ufw-before-output -m conntrack --ctstate RELATED,ESTABLISHED -j ACCEPT
-A ufw-before-forward -m conntrack --ctstate RELATED,ESTABLISHED -j ACCEPT
-A ufw-before-input -m conntrack --ctstate INVALID -j ufw-logging-deny
-A ufw-before-input -m conntrack --ctstate INVALID -j DROP
-A ufw-before-input -p icmp --icmp-type destination-unreachable -j ACCEPT
-A ufw-before-input -p icmp --icmp-type time-exceeded -j ACCEPT
-A ufw-before-input -p icmp --icmp-type parameter-problem -j ACCEPT
-A ufw-before-input -p icmp --icmp-type echo-request -j ACCEPT
-A ufw-before-forward -p icmp --icmp-type destination-unreachable -j ACCEPT
-A ufw-before-forward -p icmp --icmp-type time-exceeded -j ACCEPT
-A ufw-before-forward -p icmp --icmp-type parameter-problem -j ACCEPT
-A ufw-before-forward -p icmp --icmp-type echo-request -j ACCEPT
-A ufw-before-input -p udp --sport 67 --dport 68 -j ACCEPT
-A ufw-before-input -j ufw-not-local
-A ufw-not-local -m addrtype --dst-type LOCAL -j RETURN
-A ufw-not-local -m addrtype --dst-type MULTICAST -j RETURN
-A ufw-not-local -m addrtype --dst-type BROADCAST -j RETURN
-A ufw-not-local -m limit --limit 3/min --limit-burst 10 -j ufw-logging-deny
-A ufw-not-local -j DROP
-A ufw-before-input -p udp -d 224.0.0.251 --dport 5353 -j ACCEPT
-A ufw-before-input -p udp -d 239.255.255.250 --dport 1900 -j ACCEPT
COMMIT
```

---

### Post by david144 on 2023-10-15
/usr/share/ufw/iptables/after.rules
```

*filter
:ufw-after-input - [0:0]
:ufw-after-output - [0:0]
:ufw-after-forward - [0:0]
-A ufw-after-input -p udp --dport 137 -j ufw-skip-to-policy-input
-A ufw-after-input -p udp --dport 138 -j ufw-skip-to-policy-input
-A ufw-after-input -p tcp --dport 139 -j ufw-skip-to-policy-input
-A ufw-after-input -p tcp --dport 445 -j ufw-skip-to-policy-input
-A ufw-after-input -p udp --dport 67 -j ufw-skip-to-policy-input
-A ufw-after-input -p udp --dport 68 -j ufw-skip-to-policy-input
-A ufw-after-input -m addrtype --dst-type BROADCAST -j ufw-skip-to-policy-input
COMMIT
```




/usr/share/ufw/iptables/user.rules
```

*filter
:ufw-user-input - [0:0]
:ufw-user-output - [0:0]
:ufw-user-forward - [0:0]
:ufw-user-limit - [0:0]
:ufw-user-limit-accept - [0:0]
-A ufw-user-limit -m limit --limit 3/minute -j LOG --log-prefix "[UFW LIMIT BLOCK] "
-A ufw-user-limit -j REJECT
-A ufw-user-limit-accept -j ACCEPT
COMMIT
```

---

### Post by david144 on 2023-10-15
iptables --list-rules output:
```

-P INPUT DROP
-P FORWARD ACCEPT
-P OUTPUT ACCEPT
-N ufw-after-forward
-N ufw-after-input
-N ufw-after-logging-forward
-N ufw-after-logging-input
-N ufw-after-logging-output
-N ufw-after-output
-N ufw-before-forward
-N ufw-before-input
-N ufw-before-logging-forward
-N ufw-before-logging-input
-N ufw-before-logging-output
-N ufw-before-output
-N ufw-logging-allow
-N ufw-logging-deny
-N ufw-not-local
-N ufw-reject-forward
-N ufw-reject-input
-N ufw-reject-output
-N ufw-skip-to-policy-forward
-N ufw-skip-to-policy-input
-N ufw-skip-to-policy-output
-N ufw-track-forward
-N ufw-track-input
-N ufw-track-output
-N ufw-user-forward
-N ufw-user-input
-N ufw-user-limit
-N ufw-user-limit-accept
-N ufw-user-logging-forward
-N ufw-user-logging-input
-N ufw-user-logging-output
-N ufw-user-output
-A INPUT -j ufw-before-logging-input
-A INPUT -j ufw-before-input
-A INPUT -j ufw-after-input
-A INPUT -j ufw-after-logging-input
-A INPUT -j ufw-reject-input
-A INPUT -j ufw-track-input
-A FORWARD -j ufw-before-logging-forward
-A FORWARD -j ufw-before-forward
-A FORWARD -j ufw-after-forward
-A FORWARD -j ufw-after-logging-forward
-A FORWARD -j ufw-reject-forward
-A FORWARD -j ufw-track-forward
-A OUTPUT -j ufw-before-logging-output
-A OUTPUT -j ufw-before-output
-A OUTPUT -j ufw-after-output
-A OUTPUT -j ufw-after-logging-output
-A OUTPUT -j ufw-reject-output
-A OUTPUT -j ufw-track-output
-A ufw-after-input -p udp -m udp --dport 137 -j ufw-skip-to-policy-input
-A ufw-after-input -p udp -m udp --dport 138 -j ufw-skip-to-policy-input
-A ufw-after-input -p tcp -m tcp --dport 139 -j ufw-skip-to-policy-input
-A ufw-after-input -p tcp -m tcp --dport 445 -j ufw-skip-to-policy-input
-A ufw-after-input -p udp -m udp --dport 67 -j ufw-skip-to-policy-input
-A ufw-after-input -p udp -m udp --dport 68 -j ufw-skip-to-policy-input
-A ufw-after-input -m addrtype --dst-type BROADCAST -j ufw-skip-to-policy-input
-A ufw-after-logging-input -m limit --limit 3/min --limit-burst 10 -j LOG --log-prefix "[UFW BLOCK] "
-A ufw-before-forward -m conntrack --ctstate RELATED,ESTABLISHED -j ACCEPT
-A ufw-before-forward -p icmp -m icmp --icmp-type 3 -j ACCEPT
-A ufw-before-forward -p icmp -m icmp --icmp-type 11 -j ACCEPT
-A ufw-before-forward -p icmp -m icmp --icmp-type 12 -j ACCEPT
-A ufw-before-forward -p icmp -m icmp --icmp-type 8 -j ACCEPT
-A ufw-before-forward -j ufw-user-forward
-A ufw-before-input -i lo -j ACCEPT
-A ufw-before-input -m conntrack --ctstate RELATED,ESTABLISHED -j ACCEPT
-A ufw-before-input -m conntrack --ctstate INVALID -j ufw-logging-deny
-A ufw-before-input -m conntrack --ctstate INVALID -j DROP
-A ufw-before-input -p icmp -m icmp --icmp-type 3 -j ACCEPT
-A ufw-before-input -p icmp -m icmp --icmp-type 11 -j ACCEPT
-A ufw-before-input -p icmp -m icmp --icmp-type 12 -j ACCEPT
-A ufw-before-input -p icmp -m icmp --icmp-type 8 -j ACCEPT
-A ufw-before-input -p udp -m udp --sport 67 --dport 68 -j ACCEPT
-A ufw-before-input -j ufw-not-local
-A ufw-before-input -d 224.0.0.251/32 -p udp -m udp --dport 5353 -j ACCEPT
-A ufw-before-input -d 239.255.255.250/32 -p udp -m udp --dport 1900 -j ACCEPT
-A ufw-before-input -j ufw-user-input
-A ufw-before-output -o lo -j ACCEPT
-A ufw-before-output -m conntrack --ctstate RELATED,ESTABLISHED -j ACCEPT
-A ufw-before-output -j ufw-user-output
-A ufw-logging-allow -m limit --limit 3/min --limit-burst 10 -j LOG --log-prefix "[UFW ALLOW] "
-A ufw-logging-deny -m conntrack --ctstate INVALID -m limit --limit 3/min --limit-burst 10 -j RETURN
-A ufw-logging-deny -m limit --limit 3/min --limit-burst 10 -j LOG --log-prefix "[UFW BLOCK] "
-A ufw-not-local -m addrtype --dst-type LOCAL -j RETURN
-A ufw-not-local -m addrtype --dst-type MULTICAST -j RETURN
-A ufw-not-local -m addrtype --dst-type BROADCAST -j RETURN
-A ufw-not-local -m limit --limit 3/min --limit-burst 10 -j ufw-logging-deny
-A ufw-not-local -j DROP
-A ufw-skip-to-policy-forward -j ACCEPT
-A ufw-skip-to-policy-input -j DROP
-A ufw-skip-to-policy-output -j ACCEPT
-A ufw-track-forward -p tcp -m conntrack --ctstate NEW -j ACCEPT
-A ufw-track-forward -p udp -m conntrack --ctstate NEW -j ACCEPT
-A ufw-track-output -p tcp -m conntrack --ctstate NEW -j ACCEPT
-A ufw-track-output -p udp -m conntrack --ctstate NEW -j ACCEPT
-A ufw-user-input -s 192.168.4.103/32 -d 10.7.77.1/32 -j ACCEPT
-A ufw-user-input -s 10.7.77.2/32 -d 10.7.77.1/32 -j ACCEPT
-A ufw-user-input -s 192.168.4.10/32 -p tcp -m tcp --dport 22 -j ACCEPT
-A ufw-user-input -d 238.255.255.250/32 -j DROP
-A ufw-user-input -d 239.255.255.250/32 -j DROP
-A ufw-user-input -d 224.0.0.1/32 -j DROP
-A ufw-user-input -s 10.0.2.0/24 -d 10.0.2.1/32 -p udp -m udp --dport 67 -j ACCEPT
-A ufw-user-input -s 10.0.3.0/24 -d 10.0.3.1/32 -p udp -m udp --dport 67 -j ACCEPT
-A ufw-user-input -s 10.0.4.0/24 -d 10.0.4.1/32 -p udp -m udp --dport 67 -j ACCEPT
-A ufw-user-input -s 192.168.4.0/24 -d 192.168.4.1/32 -p udp -m udp --dport 67 -j ACCEPT
-A ufw-user-input -s 10.100.0.0/16 -d 10.100.0.1/32 -p udp -m udp --dport 67 -j ACCEPT
-A ufw-user-input -s 10.200.0.0/16 -d 10.200.0.1/32 -p udp -m udp --dport 67 -j ACCEPT
-A ufw-user-input -s 10.7.77.254/32 -d 10.7.77.2/32 -p tcp -m tcp --dport 22 -j ACCEPT
-A ufw-user-input -s 192.168.4.10/32 -d 10.7.77.2/32 -p tcp -m tcp --dport 22 -j ACCEPT
-A ufw-user-input -s 192.168.4.10/32 -d 10.7.77.0/24 -p tcp -m tcp --dport 22 -j ACCEPT
-A ufw-user-input -s 10.0.0.0/8 -d 10.7.77.0/24 -j DROP
-A ufw-user-input -s 10.0.2.0/24 -d 192.168.4.0/24 -j DROP
-A ufw-user-input -s 10.0.3.0/24 -d 192.168.4.0/24 -j DROP
-A ufw-user-input -s 10.0.4.0/24 -d 192.168.4.0/24 -j DROP
-A ufw-user-input -s 10.100.0.0/16 -d 192.168.4.0/24 -j DROP
-A ufw-user-input -s 10.200.0.0/16 -d 192.168.4.0/24 -j DROP
-A ufw-user-input -s 10.0.2.0/24 -d 10.0.3.0/24 -j DROP
-A ufw-user-input -s 10.0.2.0/24 -d 10.0.4.0/24 -j DROP
-A ufw-user-input -s 10.0.2.0/24 -d 10.100.0.0/16 -j DROP
-A ufw-user-input -s 10.0.2.0/24 -d 10.200.0.0/16 -j DROP
-A ufw-user-input -s 10.0.3.0/24 -d 10.0.2.0/24 -j DROP
-A ufw-user-input -s 10.0.3.0/24 -d 10.0.4.0/24 -j DROP
-A ufw-user-input -s 10.0.3.0/24 -d 10.100.0.0/16 -j DROP
-A ufw-user-input -s 10.0.3.0/24 -d 10.200.0.0/16 -j DROP
-A ufw-user-input -s 10.0.4.0/24 -d 10.0.2.0/24 -j DROP
-A ufw-user-input -s 10.0.4.0/24 -d 10.0.3.0/24 -j DROP
-A ufw-user-input -s 10.0.4.0/24 -d 10.100.0.0/16 -j DROP
-A ufw-user-input -s 10.0.4.0/24 -d 10.200.0.0/16 -j DROP
-A ufw-user-input -s 10.100.0.0/16 -d 10.0.2.0/24 -j DROP
-A ufw-user-input -s 10.100.0.0/16 -d 10.0.3.0/24 -j DROP
-A ufw-user-input -s 10.100.0.0/16 -d 10.0.4.0/24 -j DROP
-A ufw-user-input -s 10.100.0.0/16 -d 10.200.0.0/16 -j DROP
-A ufw-user-input -s 10.200.0.0/16 -d 10.0.2.0/24 -j DROP
-A ufw-user-input -s 10.200.0.0/16 -d 10.0.3.0/24 -j DROP
-A ufw-user-input -s 10.200.0.0/16 -d 10.0.4.0/24 -j DROP
-A ufw-user-input -s 10.200.0.0/16 -d 10.100.0.0/16 -j DROP
-A ufw-user-input -s 192.168.4.0/24 -j ACCEPT
-A ufw-user-input -s 10.0.2.0/24 -j ACCEPT
-A ufw-user-input -s 10.0.3.0/24 -j ACCEPT
-A ufw-user-input -s 10.0.4.0/24 -j ACCEPT
-A ufw-user-input -s 10.100.0.0/16 -j ACCEPT
-A ufw-user-input -s 10.200.0.0/16 -j ACCEPT
-A ufw-user-input -j DROP
-A ufw-user-input -s 10.7.77.2/32 -d 8.8.8.8/32 -j ACCEPT
-A ufw-user-limit -m limit --limit 3/min -j LOG --log-prefix "[UFW LIMIT BLOCK] "
-A ufw-user-limit -j REJECT --reject-with icmp-port-unreachable
-A ufw-user-limit-accept -j ACCEPT
```

---

### Post by david144 on 2023-10-15
ufw status numbered:
```

Status: active


     To                         Action      From
     --                         ------      ----
[ 1] Anywhere on bond0          ALLOW FWD   10.7.77.0/24 on vl777   # Allow traffic received on vl777 to forward to the internet on bond0 (I believe I wrote this correctly, with or without made no difference in what I would observe)
[ 2] 8.8.8.8                    ALLOW IN    10.7.77.2               # Allow for ping/dns checks
[ 3] 192.168.4.1                ALLOW IN    10.7.77.2               # Allow for ping/dns checks
[ 4] 8.8.8.8                    ALLOW IN    10.7.77.1               # Allow for ping/dns checks
[ 5] 192.168.4.1                ALLOW IN    10.7.77.1               # Allow for ping/dns checks
[ 6] 10.7.77.2                  ALLOW IN    10.7.77.1               # testing to make sure UFW wasn't getting in the way of the ARP requests
[ 7] 10.7.77.1                  ALLOW IN    10.7.77.2               # testing to make sure UFW wasn't getting in the way of the ARP requests
[ 8] 22/tcp                     ALLOW IN    192.168.4.10            # this is my PC to allow me SSH to any of the vlans later
[ 9] 238.255.255.250            DENY IN     Anywhere                # UPnP SSDP alive
[10] 239.255.255.250            DENY IN     Anywhere                # UPnP SSDP
[11] 224.0.0.1                  DENY IN     Anywhere                # all-hosts multicast
[12] 10.0.2.1 67/udp            ALLOW IN    10.0.2.0/24             # DHCP renewal
[13] 10.0.3.1 67/udp            ALLOW IN    10.0.3.0/24             # ^
[14] 10.0.4.1 67/udp            ALLOW IN    10.0.4.0/24             # ^^
[15] 192.168.4.1 67/udp         ALLOW IN    192.168.4.0/24          # ^^^
[16] 10.100.0.1 67/udp          ALLOW IN    10.100.0.0/16           # ^^^^
[17] 10.200.0.1 67/udp          ALLOW IN    10.200.0.0/16           # ^^^^^
[18] 10.7.77.1 22/tcp           ALLOW IN    10.7.77.254             # allow SSH from my temp IP in management
[19] 10.7.77.2 22/tcp           ALLOW IN    10.7.77.254             # allow SSH from my temp IP in management
[20] 10.7.77.0/24               DENY IN     10.0.0.0/8              # deny all my other local networks traffic destined for management
[21] 192.168.4.0/24             DENY IN     10.0.2.0/24             # deny my other networks access to dave-net
[22] 192.168.4.0/24             DENY IN     10.0.3.0/24             # ^
[23] 192.168.4.0/24             DENY IN     10.0.4.0/24             # ^^
[24] 192.168.4.0/24             DENY IN     10.100.0.0/16           # ^^^
[25] 192.168.4.0/24             DENY IN     10.200.0.0/16           # ^^^^
[26] 10.0.3.0/24                DENY IN     10.0.2.0/24             # deny tenant network access to other networks
[27] 10.0.4.0/24                DENY IN     10.0.2.0/24             # ^
[28] 10.100.0.0/16              DENY IN     10.0.2.0/24             # ^^
[29] 10.200.0.0/16              DENY IN     10.0.2.0/24             # ^^^
[30] 10.0.2.0/24                DENY IN     10.0.3.0/24             # deny guest network access to other networks
[31] 10.0.4.0/24                DENY IN     10.0.3.0/24             # ^
[32] 10.100.0.0/16              DENY IN     10.0.3.0/24             # ^^
[33] 10.200.0.0/16              DENY IN     10.0.3.0/24             # ^^^
[34] 10.0.2.0/24                DENY IN     10.0.4.0/24             # deny work-rap network access to other networks
[35] 10.0.3.0/24                DENY IN     10.0.4.0/24             # ^
[36] 10.100.0.0/16              DENY IN     10.0.4.0/24             # ^^
[37] 10.200.0.0/16              DENY IN     10.0.4.0/24             # ^^^
[38] 10.0.2.0/24                DENY IN     10.100.0.0/16           # deny security network access to other networks
[39] 10.0.3.0/24                DENY IN     10.100.0.0/16           # ^
[40] 10.0.4.0/24                DENY IN     10.100.0.0/16           # ^^
[41] 10.200.0.0/16              DENY IN     10.100.0.0/16           # ^^^
[42] 10.0.2.0/24                DENY IN     10.200.0.0/16           # deny plex network access to other networks
[43] 10.0.3.0/24                DENY IN     10.200.0.0/16           # ^
[44] 10.0.4.0/24                DENY IN     10.200.0.0/16           # ^^
[45] 10.100.0.0/16              DENY IN     10.200.0.0/16           # ^^^
[46] Anywhere                   ALLOW IN    192.168.4.0/24          # Allow dave-net to any
[47] Anywhere                   ALLOW IN    10.0.2.0/24             # Allow tenant-net to any
[48] Anywhere                   ALLOW IN    10.0.3.0/24             # Allow guest-net to any
[49] Anywhere                   ALLOW IN    10.0.4.0/24             # Allow work-rap-net to any
[50] Anywhere                   ALLOW IN    10.100.0.0/16           # Allow security-net to any
[51] Anywhere                   ALLOW IN    10.200.0.0/16           # Allow plex-net to any
[52] Anywhere                   DENY IN     Anywhere                # deny all other traffic
```

---

