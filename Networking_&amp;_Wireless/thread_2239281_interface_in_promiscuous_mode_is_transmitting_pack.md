---
title: "interface in promiscuous mode is transmitting packets"
date: 2014-08-13
forum: Networking &amp; Wireless
---

### Post by Coogan on 2014-08-13
I've been having this odd problem with my networking for the past several months, but it hasn't really affected anything until now.

I have a 12.04 LTS server with 3 1G interfaces.  Eth0 is the built-in interface on the motherboard, and is the primary interface for the system.  Eth1 is the first interface on a dual-interface Intel NIC card and is in a down state.  Eth2 is the second interface on the Intel card and is up in promiscuous mode.  Eth2 is fed a feed from a tap (technically, a hardware span port) that sits between my border router and my network switch.  Every device, wired or wireless, runs thru the switch then the router to access the internet.  Any data between two systems on the network should only go thru the switch.  Therefore it seems, the tap, and thus Eth2, should only see traffic from the LAN to the internet.

The reason for doing this is security and bandwidth monitoring.  Another thing to note is the Eth2 is NOT assigned an IP address.

Quick ifconfig:

```

eth0      Link encap:Ethernet  HWaddr 6c:f0:49:d5:a8:61  
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::6ef0:49ff:fed5:a861/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:173716287 errors:0 dropped:0 overruns:0 frame:0
          TX packets:978669166 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1789153 (1.7 MB)  TX bytes:1201659019 (1.2 GB)
          Interrupt:42 Base address:0xe000 

eth2      Link encap:Ethernet  HWaddr 00:15:17:5b:74:2b  
          inet6 addr: fe80::215:17ff:fe5b:742b/64 Scope:Link
          UP BROADCAST RUNNING PROMISC MULTICAST  MTU:1500  Metric:1
          RX packets:39107567 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7578 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:39184939063 (39.1 GB)  TX bytes:559562 (559.5 KB)
          Interrupt:17 Memory:fbea0000-fbec0000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4397081580 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4397081580 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:193686202866 (193.6 GB)  TX bytes:193686202866 (193.6 GB)

```

The system has multiple servers running:  SSH, DNS, DHCP, Samba, FTP, and Apache.

Somehow, for some reason, when running tcpdump on each eth0 and eth2, each interface is carrying half of the local server traffic.  For example, tcpdump -i eth0 "port 22" shows all packets from the client system to the server, and tcpdump -i eth2 "port 22" shows all packets from the server back to the client.

I'm seeing two big problems here that I can't figure out - an interface, in promiscuous mode, with no IP address, is transmitting packets, and topologically-speaking, there's no way the tap should be able to see inter-LAN traffic at all.  I have the strong suspicion that both of these as symptoms of something wrong with the networking configuration, but for the life of my, I can't figure it out.

Some guidance would be greatly appreciated.

Coog

---

### Post by Coogan on 2014-08-13
Any ideas so far?  If it helps, there's other wierdness going on with the interfaces.

1.  A few months ago, I ran a scan on the system.  The scanner (OpenVAS) reported replies from the FTP server from not only IP 192.168.1.100 (eth0), but also .101 (eth1) and .102 (eth2 at the time).  I can't remember if eth1 and eth2 were in a down state at the time, but I do know that neither had cables plugged in.
2.  I recently set eth2 to 0.0.0.0, which is what I read to do (via Google) to set an interface with no IP address.  Not long after that, a Win7 system I have that has SMB shares mounted from the Ubuntu box lost connection to the shares and couldn't reconnect using the NetBIOS name of the server.  I fired up Wireshark on the Win7 system and captured some traffic when trying to remount the shares, and found that the Samba server was reporting that the NetBIOS name resolved to 192.168.1.102 (eth2).  I tried binding the Samba server to eth0 and restarting it, but it still reported the wrong address.  I ended up having to mount the shares via IP address instead of NetBIOS name.
3.  I don't know if it's related to this, but the interface lo is exchanging a lot of data with itself.  Notice in the above ifconfig that lo has sent and received the same amount of packets.  I ran tcpdump on the lo interface and it's bouncing a lot of small UDP packets to and from 127.0.0.1.  I have no idea what's going on with that.
4.  About half the time I reboot the system, it takes a LONG time (like 10 minutes) to come back up.  I've got a monitor hooked up to it and found that it's continuously timing out getting the network configuration.  Eventually it does come back up and everything seems normal.  However, it always come up with no default route in the routing table.  I eventually had to add it to the interfaces file.

Coog

---

### Post by Coogan on 2014-08-14
So nothing I can try?  Should I just submit a bug report?

Coog

---

