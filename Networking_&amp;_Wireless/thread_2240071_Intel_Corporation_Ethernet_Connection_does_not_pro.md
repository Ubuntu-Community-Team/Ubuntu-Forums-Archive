---
title: "Intel Corporation Ethernet Connection does not properly start"
date: 2014-08-17
forum: Networking &amp; Wireless
---

### Post by scar_Alejos_Duca on 2014-08-17
I'm experiencing some problems when trying to connect my PC to the router through a switch. When the PC is directly connected to the router, everything works fine, Ubuntu (14.04) starts normally, and the Internet connection runs inmediately. The Ethernet controller is the Intel Corporation Ethernet Connection, as lspci returns:

$ lspci | grep Eth
00:19.0 Ethernet controller: Intel Corporation Ethernet Connection I217-V (rev 04)

However, when I try to connect through the switch what I get is the following: 
dmesg returns:

$ dmesg | grep eth
[    1.035585] e1000e 0000:00:19.0 eth0: registered PHC clock
[    1.035587] e1000e 0000:00:19.0 eth0: (PCI Express:2.5GT/s:Width x1) 00:22:4d:a7:be:5d
[    1.035589] e1000e 0000:00:19.0 eth0: Intel(R) PRO/1000 Network Connection
[    1.035625] e1000e 0000:00:19.0 eth0: MAC: 11, PHY: 12, PBA No: FFFFFF-0FF
[    1.357838] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[    2.165413] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[    2.165574] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[    2.641287] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   16.715086] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: Rx/Tx
[   16.715090] e1000e 0000:00:19.0 eth0: 10/100 speed: disabling TSO
[   16.715117] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready

It looks like eth0 is properly working. Actually, nm-tool returns:

$ nm-tool
- Device: eth0  [Conexión cableada] -------------------------------------------
  Type:              Wired
  Driver:            e1000e
  State:             connected
  Default:           yes
  HW Address:        00:22:4D:A7:BE:5D

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.30
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             80.58.61.250
    DNS:             80.58.61.254
    DNS:             192.168.1.1

However, ping returns:
$ ping 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
From 192.168.1.30 icmp_seq=1 Destination Host Unreachable
From 192.168.1.30 icmp_seq=2 Destination Host Unreachable
From 192.168.1.30 icmp_seq=3 Destination Host Unreachable

The connection is restored by restarting it:
# ifconfig eth0 down
# ifconfig eth0 up

From this point on, everything runs smoothly, as if the PC were directly connected to the router.

It seems to be an issue related to the integrated LAN adaptor, since my laptop connects without problems. My desktop board is an Intel DB85FL.

I'd be grateful if anyone could give some ideas on how to solve this issue. Thank you in advance.

---

### Post by scar_Alejos_Duca on 2014-08-25
This is a clear example on how a bad connection can ruin your day. I feel a bit ashamed to acknowledge that I realized that after checking the wall plug (in my defense, I must say that it was concealed by a large bookcase, so it couldn't be easily accessed).

It looks like it took too long to the e1000e driver to negotiate the connection speed. Then the driver just reduced the connection speed to 100Mb and stopped negotiating. For some reason (unfortunately, I don't know the details on how this driver is implemented, and I guess these details are far away from where my understanding could go), the negotiation properly worked after restarting the driver.

---

### Post by varunendra on 2014-08-25
Glad you sorted it out by yourself, I was about to post some random suggestions, glad I didn't :p

The correct way to mark a thread as solved is via "Thread Tools" link above the first post.

Welcome to the forums! :)

---

