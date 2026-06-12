---
title: "Intel Pro 1000GT Ubuntu 8.04 VLAN recognition"
date: 2008-06-23
forum: Networking &amp; Wireless
---

### Post by ericbrowning on 2008-06-23
Alright I have an Intel Pro 1000GT in an Ubuntu 8.04 P4 2.2Ghz generic PC.  I have been trying to enable VLAN 10 on eth1 (the intel pro card) to no avail.  The problem is all the IPs can be pinged on VLAN 1 regardless of configuration. Ideally I should be able to use ping -I 172.16.2.12 172.16.1.228 to ping the other VLAN 10 attached device correct?  I have the mtu set 4 bytes smaller to account for the extra 4 bytes added by VLAN tagging as per several VLAN how-to guides.

Yes I used synaptic to install the vlan package and the 8021q module is loaded and I do see it in the /etc/modules file.

The /proc/net/vlan/config shows this:
> VLAN Dev name    | VLAN ID
Name-Type: VLAN_NAME_TYPE_RAW_PLUS_VID_NO_PAD
eth1.10        | 10  | eth1

And /proc/net/vlan/eth1.10 shows this:
> eth1.10  VID: 10         REORDER_HDR: 1  dev->priv_flags: 1
         total frames received            0
          total bytes received            0
      Broadcast/Multicast Rcvd            0

      total frames transmitted          115
       total bytes transmitted        16955
            total headroom inc            0
           total encap on xmit            0
Device: eth1
INGRESS priority mappings: 0:0  1:0  2:0  3:0  4:0  5:0  6:0 7:0
EGRESSS priority Mappings:


Below is my /etc/network/interfaces file:

> 
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0

iface eth0 inet static
address 172.16.2.10
netmask 255.255.248.0
gateway 172.16.0.1
mtu 1496

auto eth1

iface eth1 inet static
address 172.16.2.11
netmask 255.255.248.0
gateway 172.16.0.1
mtu 1496

auto eth1.10

iface eth1.10 inet static
address 172.16.2.12
netmask 255.255.248.0
vlan-raw-device eth1
gateway 172.16.0.1
mtu 1496


ifconfig reports this:
> eth0      Link encap:Ethernet  HWaddr 00:08:02:c1:98:67  
          inet addr:172.16.2.10  Bcast:172.16.7.255  Mask:255.255.248.0
          inet6 addr: fe80::208:2ff:fec1:9867/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1496  Metric:1
          RX packets:1071 errors:0 dropped:0 overruns:0 frame:0
          TX packets:38 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:98400 (96.0 KB)  TX bytes:5469 (5.3 KB)

eth1      Link encap:Ethernet  HWaddr 00:1b:21:19:e1:b7  
          inet addr:172.16.2.11  Bcast:172.16.7.255  Mask:255.255.248.0
          inet6 addr: fe80::21b:21ff:fe19:e1b7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1496  Metric:1
          RX packets:1216 errors:0 dropped:0 overruns:0 frame:0
          TX packets:314 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:118546 (115.7 KB)  TX bytes:36436 (35.5 KB)
          Base address:0x1000 Memory:fc500000-fc520000 

eth1.10   Link encap:Ethernet  HWaddr 00:1b:21:19:e1:b7  
          inet addr:172.16.2.12  Bcast:172.16.7.255  Mask:255.255.248.0
          inet6 addr: fe80::21b:21ff:fe19:e1b7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1496  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:36 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:5377 (5.2 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2206 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2206 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:111846 (109.2 KB)  TX bytes:111846 (109.2 KB)

Yes I have verified that the port eth1 and eth1.10 are connected to is an 802.1q tagged port by plugging in my Mac laptop and configuring a virtual interface for VLAN 10 and pinging another device on an untagged VLAN 10 port on a different switch (means 802.1q tagging is working between switches), in this case a printer I pinged.  

Any ideas of where to go next? (before I'm bald)

---

