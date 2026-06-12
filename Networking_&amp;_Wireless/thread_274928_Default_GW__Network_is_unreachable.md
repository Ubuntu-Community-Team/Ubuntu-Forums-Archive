---
title: "Default GW : Network is unreachable"
date: 2006-10-10
forum: Networking &amp; Wireless
---

### Post by Kurdt on 2006-10-10
I've just switched from one ISP to another, so I have to change Default GW, and i do this:

> $ sudo route -v add default gw 200.55.61.1
SIOCADDRT: Network is unreachable

BUT:

> $ ping 200.55.61.1
PING 200.55.61.1 (200.55.61.1) 56(84) bytes of data.
64 bytes from 200.55.61.1: icmp_seq=1 ttl=253 time=11.1 ms
64 bytes from 200.55.61.1: icmp_seq=2 ttl=253 time=11.1 ms
64 bytes from 200.55.61.1: icmp_seq=3 ttl=253 time=11.9 ms
64 bytes from 200.55.61.1: icmp_seq=4 ttl=253 time=11.8 ms

What's happening here? I can reach 200.55.61.1 wich is the IP address of the new ISP's router. Why am i getting network is unreachable ?

Thanks to all

---

### Post by Iowan on 2006-10-10
From **man route**:> gw GW  route  packets  via a gateway.  NOTE: The specified gateway must be reachable first. This usually means that you have to set up a static route to the gateway beforehand.
(I've no idea how you'd set up the static route beforehand...)
I presume editing the **/etc/network/interfaces** file doesn't help?

---

### Post by Kurdt on 2006-10-11
Could it be related the fact that my subnet is 192.168.1.x and GW is 200.x ? (and not 192.168.1.x)

Because i can add my old isp router ip address like this:

```
$ sudo route -v add default gw 192.168.1.120
```

With no errors...

Iowan: You said something about /etc/network/interfaces, but, I haven't did that before with my old router, interfaces doesn't says anything in special.

This is my route

> Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     *               255.255.255.0   U     0      0        0 wlan0
default         192.168.1.120   0.0.0.0         UG    0      0        0 wlan0


192.168.1.120 is my old isp router, thanks in advance

---

### Post by dbott67 on 2006-10-11
> **Kurdt said:**
> Could it be related the fact that my subnet is 192.168.1.x and GW is 200.x ? (and not 192.168.1.x)

...

192.168.1.120 is my old isp router, thanks in advance

This router, is it a D-Link/Linksys/Netgear-type device? Are you still using it?  If so, I'm pretty sure that this is the problem.  You're computer is only aware of one subnet: 192.168.1.xxx and the gateway is normally the address of your router and requires a local address on the same subnet.  Run the commands **ifconfig** & **route** from a terminal and post results here:

*[COLOR="Red"]As an aside, in order to set the GW to 200.x.y.z, you would need a 2nd NIC with an address on that subnet (i.e. 200.x.y.w), which creates a multi-homed network and is another topic for discussion -or- you would need to remove the router and program your NIC with the ISP provided settings (my advice --- keep the router!).  Computers can only communicate with devices on the same local network; it is the job of the router/gateway to pass packets from one network to another.[/COLOR]*

```
ifconfig

eth0      Link encap:Ethernet  HWaddr 00:50:BA:C0:A7:55  
          inet addr:192.168.1.106  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::250:baff:fec0:a755/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:243494 errors:0 dropped:0 overruns:0 frame:0
          TX packets:189741 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:230455827 (219.7 MiB)  TX bytes:26936552 (25.6 MiB)
          Interrupt:185 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1984 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1984 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:118612 (115.8 KiB)  TX bytes:118612 (115.8 KiB)
```
and
```
route

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     *               255.255.255.0   U     0      0        0 eth0
default         192.168.1.120     0.0.0.0         UG    0      0        0 eth0
```

The gateway displayed should be 192.168.1.120.  Your router handles the traffic & forwards all NON-local traffic to the external interface (200.55.61.1).

Check you /etc/resolv.conf to make sure that your computer is using your router to perform DNS lookups:

```
cat /etc/resolv.conf
nameserver 192.168.1.120
```

Any settings provided by your new ISP should be programmed in the router on the WAN settings page.

-Dave

---

### Post by Iowan on 2006-10-11
I guess I'm a bit confused (so what's new?) as to where your router/gateway is located (whether you have physical access to it).  I checked my workstation last night and, because it's set for DHCP, there is no gateway setting available (I was expecting to find it in the aforementioned /etc/network/interfaces file).

---

### Post by dbott67 on 2006-10-11
The gateway (and other pertinent info) is programmed into the router, and is set via DHCP to the client (the router passes IP address, subnet mask, gateway & DNS information to the client). 

In Windows XP all of the information is visible via the **ipconfig /all** command, but as far as I know there is no equivalent linux command:

```
C:\WINDOWS>ipconfig /all

Windows IP Configuration

        Host Name . . . . . . . . . . . . : DAVIDBOTT
        Primary Dns Suffix  . . . . . . . : stcatharines.library.on.ca
        Node Type . . . . . . . . . . . . : Unknown
        IP Routing Enabled. . . . . . . . : No
        WINS Proxy Enabled. . . . . . . . : No
        DNS Suffix Search List. . . . . . : stcatharines.library.on.ca
                                            library.on.ca
                                            on.ca


Ethernet adapter Local Area Connection:

        Connection-specific DNS Suffix  . :
        Description . . . . . . . . . . . : 3Com 3C920B-EMB-WNM Integrated Fast
Ethernet Controller
        Physical Address. . . . . . . . . : 00-0E-A6-BE-50-A0
        Dhcp Enabled. . . . . . . . . . . : No
        IP Address. . . . . . . . . . . . : 192.168.128.18
        Subnet Mask . . . . . . . . . . . : 255.255.255.0
        Default Gateway . . . . . . . . . : 192.168.128.4
        DHCP Class ID . . . . . . . . . . :
        DNS Servers . . . . . . . . . . . : 192.168.128.25
```

The linux command **ifconfig** only displays the IP, subnet & broadcast address.  The gateway is displayed via the **route** command (see my post above).

-Dave

---

