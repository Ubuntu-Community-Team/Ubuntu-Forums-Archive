---
title: "NIC / Router / PPOE ?"
date: 2005-08-14
forum: Networking &amp; Wireless
---

### Post by budzooka on 2005-08-14
I just installed Ubuntu for the first time and love it, but I'm having problems with connecting to my router:

- I'm on DSL and am running a D-Link DI-624 Router
- I can do a ping loopback and am getting a response from the NIC
- I can't ping the Router or anywhere outside
- Cables and Router ports are fine
- Other 2 machines, including WLAN are perfectly fine
- I can see, using the network tools, that packets are being sent and recieved. the NIC seems to be getting ARP requests

- I ran 'sudo pppoeconf' from the terminal and I keep getting this:

**"Sorry I scanned 1 interface but the Access Concentrator of your provider did not respond......'** blah blah blah

Then, on a whim, I accessed my router and set up my NIC on this Ubuntu machine as a 'Static DHCP' for its MAC address - so it recieves the same IP everytime. Nothing doing

Then I set up the whole damn network on static and I'm still not getting into the LAN

Can someone please explain what  I'm doing wrong or what I missed?  ](*,) 

Thanks in advance

---

### Post by budzooka on 2005-08-14
Output from 'ifconfig':

eth0      Link encap:Ethernet  HWaddr 00:11:95:5D:EE:4D
          inet6 addr: fe80::211:95ff:fe5d:ee4d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2803 errors:0 dropped:0 overruns:0 frame:0
          TX packets:445 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:920021 (898.4 KiB)  TX bytes:226204 (220.9 KiB)
          Interrupt:11 Base address:0xe800

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:26438 errors:0 dropped:0 overruns:0 frame:0
          TX packets:26438 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:2412148 (2.3 MiB)  TX bytes:2412148 (2.3 MiB)

---

### Post by cwaldbieser on 2005-08-14
Can you post the output of "$ ifconfig -a" and "$route" (from the terminal).  Also, even though it is sometimes easy to guess what a home network looks like, could you briefly describe the connections?

Also, I am not entirely sure what you meant when you said
> 
I can do a ping loopback and am getting a response from the NIC

Can you clarify what you meant by that?  At first I thought you meant you did a ping 127.0.0.1, but that doesn't seem to make sense to me.

---

### Post by budzooka on 2005-08-14
cwaldbieser,

Thanks for the response.... I even tried 'eth0 up/down' and a reboot to see what the results would be and still no connecto.


Ping Loopback = 127.0.0.1 [at least thats what my Cisco instr. called it..]

Also:: Pinging the Router or the Modem from the terminal always replies 'Network Unreachable'

Inbound DSL Line > DSL Modem > Router / Wireless Router Running DHCP

- DSL Modem and Router connected w/ CAT5e
- WinDoze PC connected via CAT5e at port 1 - Running
- Ubuntu box connected via CAT5e at port 2 - Down
- WinDoze PC connected via CAT5e at port 3 - Running
- Laptop connected via WLAN - Running


**ifconfig -a :::**

eth0      Link encap:Ethernet  HWaddr 00:11:95:5D:EE:4D
          inet6 addr: fe80::211:95ff:fe5d:ee4d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2792 errors:0 dropped:0 overruns:0 frame:0
          TX packets:103 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:922556 (900.9 KiB)  TX bytes:33894 (33.0 KiB)
          Interrupt:11 Base address:0xe800

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:3056 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3056 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:277870 (271.3 KiB)  TX bytes:277870 (271.3 KiB)

sit0      Link encap:IPv6-in-IPv4
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dopped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

**$route :::**

eth0      Link encap:Ethernet  HWaddr 00:11:95:5D:EE:4D
          inet6 addr: fe80::211:95ff:fe5d:ee4d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2872 errors:0 dropped:0 overruns:0 frame:0
          TX packets:106 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:949212 (926.9 KiB)  TX bytes:34920 (34.1 KiB)
          Interrupt:11 Base address:0xe800

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:3815 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3815 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0

**route -n :::**

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface

---

### Post by cwaldbieser on 2005-08-14
OK, it looks like you don't have an ipv4 IP address for your Ubuntu machine, not does it have any routing info.  Since your router is providing IP addresses via DHCP, I would try running:
```
$ sudo dhclient
```
to see if that brings you up.

If that doesn't work, I assume the Windows machines are working.  On one of them, open cmd.exe and post the output of:

```
C:\>ipconfig
C:\>route print
```
This will help me figure out what you network and router information is supposed to be.

---

### Post by budzooka on 2005-08-15
Thanks again for the help.... I'm at work and will grab those outputs as soon as I get to the house

:^)

- budzooka

---

### Post by budzooka on 2005-08-15
**This is the output from 'sudo dhclient' ::**


sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/sit0/
Sending on   LPF/sit0/
Listening on LPF/eth0/00:11:95:5d:ee:4d
Sending on   LPF/eth0/00:11:95:5d:ee:4d
Listening on LPF/lo/
Sending on   LPF/lo/
Sending on   Socket/fallback
DHCPDISCOVER on sit0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on lo to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on sit0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on lo to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on sit0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on lo to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on lo to 255.255.255.255 port 67 interval 19
DHCPDISCOVER on sit0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on sit0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on lo to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on sit0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on lo to 255.255.255.255 port 67 interval 7
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

[B]
IPCONFIG from the Windoze machine ::[/B]

Windows IP Configuration


Ethernet adapter Local Area Connection:

        Connection-specific DNS Suffix  . : launchmodem.com
        IP Address. . . . . . . . . . . . : 192.168.0.100
        Subnet Mask . . . . . . . . . . . : 255.255.255.0
        Default Gateway . . . . . . . . . : 192.168.0.1

**Route Print output ::**

=======================
Interface List
0x1 ........................... MS TCP Loopback interface
0x2 ...00 40 05 37 e2 c1 ...... Realtek RTL8139 Family PCI Fast Ethernet NIC - P
acket Scheduler Miniport
===========================================================================
===========================================================================
Active Routes:
Network Destination        Netmask          Gateway       Interface  Metric
          0.0.0.0          0.0.0.0      192.168.0.1   192.168.0.100       20
        127.0.0.0        255.0.0.0        127.0.0.1       127.0.0.1       1
      192.168.0.0    255.255.255.0    192.168.0.100   192.168.0.100       20
    192.168.0.100  255.255.255.255        127.0.0.1       127.0.0.1       20
    192.168.0.255  255.255.255.255    192.168.0.100   192.168.0.100       20
        224.0.0.0        240.0.0.0    192.168.0.100   192.168.0.100       20
  255.255.255.255  255.255.255.255    192.168.0.100   192.168.0.100       1
Default Gateway:       192.168.0.1
===========================================================================
Persistent Routes:
  None

---

### Post by budzooka on 2005-08-15
[COLOR=Red][B]
*** Issue Resolved***[/B][/COLOR]

 :mad: I am suuuuuuuuuuch an imbicile! 

I checked my logs in the router after watching the lights blip back and forth from the NIC and the router a few times and still no sign of anything in the logs - - this is weird. So I set up the router again for 'Static DHCP' for the MAC address of the NIC and assigned it 192.168.0.200 - went back to the Ubuntu machine and assigned the IP etc etc and opened Firefox....

Well this time it just keeps spinning and going nowhere but NOT giving the 'can not be found' dead-end. So, I open the terminal and ping the router and FINALLY i'm getting responses... but no internet

I go back to the router and log in. and I'm double checking all the settings, all the IP's, you name it...... then I remember the weekend I bought this house and setting up the network ----- then i remember some neighborhood laptop trying to access the network minutes after the install ---- then I remember ------

**THE MAC FILTERS I SET UP!!!!!** 

This DLink router interface is weird, the MAC filter is just a radio button that you select and THEN it appears with the settings. When you first look at the 'filters' tab the 'IP Filter' radio button is selected and, of course, there's no IP's being filtered, the MAC filter is hiding behind the scenes because -DUH- if its not selected its not activated, right? WRONG!!!!

Added in the NIC's MAC addy into the filter and away we go 

Whew.... damn glad thats over

Thanks for all the assistance and for giving me some great advice to figuring out the problem here - i really appreciate it... maybe this thread will help someone down the road...

Peace

-b

---

