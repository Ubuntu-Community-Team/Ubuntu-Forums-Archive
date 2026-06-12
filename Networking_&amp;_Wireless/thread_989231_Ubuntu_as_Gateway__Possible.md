---
title: "Ubuntu as Gateway?  Possible?"
date: 2008-11-21
forum: Networking &amp; Wireless
---

### Post by ubernatural on 2008-11-21
Hi folks,

I'm actually unable to connect to a PPTP vpn from my Vista machine but have no troubles with an Ubuntu (Hardy) machine.  The Vista vpn troubleshooting is really really difficult so I thought I'd try to make it easier on myself.  I'd like to establish a vpn connection on my Hardy box, then set that up as a gateway so I can add a route to my Vista machine pushing all 192.168.60.* traffic through it.  I'm pretty confident I can set up the route in Vista, but want to know if I can set up Ubuntu to be a vpn gateway of sorts.

Anyone know if this is possible, and if so how I might go about setting that up?

John

---

### Post by ubernatural on 2008-11-21
OK, I think I may have hit on the correct term for googling.  I think what I want is IP forwarding.  I changed some settings, but must be missing something (either that or I'm completely off track).

My home network is 192.168.21.*.  My vpn network is 192.168.60.*.  A vpn connection is established on my Ubuntu machine (192.168.21.100), and I can successfully ping 192.168.60.131 from the Ubuntu machine.  The Vista machine is 192.168.60.44, and can successfully ping the Ubuntu machine.  Now to forwarding.

The following commands are run on my Ubuntu machine:
```
john@buck:~$ sudo cat /proc/sys/net/ipv4/ip_forward
1
john@buck:~$ sudo iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination
```

The following commands are run on my Vista machine:
```
C:\Users\John>route print
===========================================================================
Interface List
 22 ...00 ff 46 66 f0 57 ...... VirtualBox TAP Adapter
  8 ...00 1b fc 1c e7 92 ...... Realtek RTL8168B/8111B Family PCI-E Gigabit Ethernet NIC (NDIS 6.0)
 18 ...00 50 56 c0 00 01 ...... VMware Virtual Ethernet Adapter for VMnet1
 20 ...00 50 56 c0 00 08 ...... VMware Virtual Ethernet Adapter for VMnet8
  1 ........................... Software Loopback Interface 1
  9 ...02 00 54 55 4e 01 ...... Teredo Tunneling Pseudo-Interface
 19 ...00 00 00 00 00 00 00 e0  isatap.{DE042712-DB40-4396-BF5A-BC507A7B88AB}
 21 ...00 00 00 00 00 00 00 e0  isatap.{0A48D199-DF5B-4889-B1E1-3B67F142C251}
 24 ...00 00 00 00 00 00 00 e0  isatap.{4666F057-A0BB-49BD-9928-870E4EFB4BE4}
 26 ...00 00 00 00 00 00 00 e0  isatap.{1DEA3456-BC94-4417-A926-68A16B08C017}
===========================================================================

IPv4 Route Table
===========================================================================
Active Routes:
Network Destination        Netmask          Gateway       Interface  Metric
          0.0.0.0          0.0.0.0     192.168.21.1    192.168.21.44    276
        127.0.0.0        255.0.0.0         On-link         127.0.0.1    306
        127.0.0.1  255.255.255.255         On-link         127.0.0.1    306
  127.255.255.255  255.255.255.255         On-link         127.0.0.1    306
      169.254.0.0      255.255.0.0         On-link     192.168.21.44    296
  169.254.255.255  255.255.255.255         On-link     192.168.21.44    276
     192.168.13.0    255.255.255.0         On-link      192.168.13.1    276
     192.168.13.1  255.255.255.255         On-link      192.168.13.1    276
   192.168.13.255  255.255.255.255         On-link      192.168.13.1    276
     192.168.21.0    255.255.255.0         On-link     192.168.21.44    276
    192.168.21.44  255.255.255.255         On-link     192.168.21.44    276
   192.168.21.255  255.255.255.255         On-link     192.168.21.44    276
     192.168.60.0    255.255.255.0   192.168.21.100    192.168.21.44     21
    192.168.126.0    255.255.255.0         On-link     192.168.126.1    276
    192.168.126.1  255.255.255.255         On-link     192.168.126.1    276
  192.168.126.255  255.255.255.255         On-link     192.168.126.1    276
        224.0.0.0        240.0.0.0         On-link         127.0.0.1    306
        224.0.0.0        240.0.0.0         On-link     192.168.126.1    276
        224.0.0.0        240.0.0.0         On-link      192.168.13.1    276
        224.0.0.0        240.0.0.0         On-link     192.168.21.44    276
  255.255.255.255  255.255.255.255         On-link         127.0.0.1    306
  255.255.255.255  255.255.255.255         On-link     192.168.126.1    276
  255.255.255.255  255.255.255.255         On-link      192.168.13.1    276
  255.255.255.255  255.255.255.255         On-link     192.168.21.44    276
===========================================================================
Persistent Routes:
  Network Address          Netmask  Gateway Address  Metric
          0.0.0.0          0.0.0.0     192.168.21.1  Default
     192.168.60.0    255.255.255.0   192.168.21.100       1
===========================================================================

IPv6 Route Table
===========================================================================
Active Routes:
 If Metric Network Destination      Gateway
  1    306 ::1/128                  On-link
 18    276 fe80::/64                On-link
 20    276 fe80::/64                On-link
  8    276 fe80::/64                On-link
 18    276 fe80::7585:6160:4eb7:7641/128
                                    On-link
 20    276 fe80::b4eb:9707:d719:a0d9/128
                                    On-link
  8    276 fe80::c4e7:b7cf:135f:9160/128
                                    On-link
  1    306 ff00::/8                 On-link
 18    276 ff00::/8                 On-link
 20    276 ff00::/8                 On-link
  8    276 ff00::/8                 On-link
===========================================================================
Persistent Routes:
  None
C:\Users\John>ping 192.168.60.131

Pinging 192.168.60.131 with 32 bytes of data:
Request timed out.
Request timed out.
Request timed out.

Ping statistics for 192.168.60.131:
    Packets: Sent = 3, Received = 0, Lost = 3 (100% loss),
C:\Users\John>tracert 192.168.60.131

Tracing route to 192.168.60.131 over a maximum of 30 hops

  1    <1 ms    <1 ms    <1 ms  192.168.21.100
  2     *        *        *     Request timed out.
  3  ^C

```
It *seems* like everything is set up according to how I've read that it should be, but Ubuntu isn't forwarding the traffic...  Any help would be appreciated.

John

---

