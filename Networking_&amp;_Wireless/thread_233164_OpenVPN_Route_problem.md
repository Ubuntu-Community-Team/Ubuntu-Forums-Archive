---
title: "OpenVPN Route problem"
date: 2006-08-09
forum: Networking &amp; Wireless
---

### Post by Blues- on 2006-08-09
Hi all, I'm having problems with my VPN Routing.
I'm using OpenVPN and I'm 99% sure that my problem has nothing todo with the VPN setup, but the NAT/Routing setup on my Ubuntu server.

The Server has the following setup ...
LAN
 - IP: 10.0.0.1
 - Mask: 255.255.255.0
 - DNS and DHCP on same machine
 - Default Gateway 10.0.0.200

Virtual LAN for VPN
 - Server IP: 10.1.0.1
 - Mask: 255.255.255.0


The VPN (Windows) client gets the IP 10.1.0.2
and successfully connects to the server on 10.1.0.1 via TAP.
I can both ping 10.0.0.1 and 10.1.0.1 from the VPN client,
but other machines on the server network are not reachable from the VPN client, (the 10.0.0.X) network.

I believe that there must be some routing issues on the box, because i want the VPN clients to be able to communicate with other hosts on the lan.
BTW, I'm not running any firewall on the server machine.

For reference I've added the route table on the server machine below...
> Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.0.0.0        *               255.255.255.0   U     0      0        0 eth0
10.2.0.0        *               255.255.255.0   U     0      0        0 eth1
10.1.0.0        *               255.255.255.0   U     0      0        0 tap0
default         10.0.0.200      0.0.0.0         UG    0      0        0 eth0


And below is route Print from the XP VPN client and the ipconfig output,
```
Ethernet adapter OpenVPN:

        Connection-specific DNS Suffix  . :
        Description . . . . . . . . . . . : TAP-Win32 Adapter V8
        Physical Address. . . . . . . . . : 00-FF-70-C9-63-A3
        Dhcp Enabled. . . . . . . . . . . : Yes
        Autoconfiguration Enabled . . . . : Yes
        IP Address. . . . . . . . . . . . : 10.1.0.2
        Subnet Mask . . . . . . . . . . . : 255.255.255.0
        Default Gateway . . . . . . . . . :
        DHCP Server . . . . . . . . . . . : 10.1.0.0
        DNS Servers . . . . . . . . . . . : 10.0.0.1
                                            10.0.0.200
        Lease Obtained. . . . . . . . . . : 9. ágúst 2006 22:11:14
        Lease Expires . . . . . . . . . . : 9. ágúst 2007 22:11:14
```

Route Print ..
```
Active Routes:
Network Destination        Netmask          Gateway       Interface  Metric
          0.0.0.0          0.0.0.0  192.168.253.254  192.168.253.152      10
         10.0.0.0    255.255.255.0         10.1.0.1        10.1.0.2       1
         10.1.0.0    255.255.255.0         10.1.0.2        10.1.0.2       30
         10.1.0.0    255.255.255.0         10.1.0.1        10.1.0.2       1
         10.1.0.2  255.255.255.255        127.0.0.1       127.0.0.1       30
   10.255.255.255  255.255.255.255         10.1.0.2        10.1.0.2       30
        127.0.0.0        255.0.0.0        127.0.0.1       127.0.0.1       1
    192.168.253.0    255.255.255.0  192.168.253.152  192.168.253.152      10
  192.168.253.152  255.255.255.255        127.0.0.1       127.0.0.1       10
  192.168.253.255  255.255.255.255  192.168.253.152  192.168.253.152      10
        224.0.0.0        240.0.0.0         10.1.0.2        10.1.0.2       30
        224.0.0.0        240.0.0.0  192.168.253.152  192.168.253.152      10
  255.255.255.255  255.255.255.255         10.1.0.2        10.1.0.2       1
  255.255.255.255  255.255.255.255  192.168.253.152  192.168.253.152      1
Default Gateway:   192.168.253.254
===========================================================================
Persistent Routes:
  None
```

I have already added ```
net.ipv4.ip_forward = 1
``` in my sysctl.conf and restarted the network interface.

BTW, eth1 (10.2.0.1) is an unused nic but active on the server machine.

Any help is appreciated ..
Thanks in advance,
Cheers,
Blues-.

---

### Post by cylon359 on 2006-08-10
Your problem is that the other computers don't know how to find your 10.1.0.x subnet.  The default gateway, 10.0.0.200 needs to know how to route to 10.1.0.x, otherwise it will route it to its default gateway.  The alternative is for each computer to have its own routing entry for 10.1.0.x that routes that subnet to 10.0.0.1

---

