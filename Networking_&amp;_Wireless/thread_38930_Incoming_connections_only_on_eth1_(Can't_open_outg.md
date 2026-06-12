---
title: "Incoming connections only on eth1 (Can't open outgoing connections)"
date: 2005-06-02
forum: Networking &amp; Wireless
---

### Post by caspian on 2005-06-02
Recently, we wired our house with ethernet, but when I connect to the network, I can't connect to any other computer on the network -- I can't even ping anyone. What makes this problem even more strange is that everyone else on the network can connect to me. They can ping me and ssh into my machine.

Does anyone know what this problem is caused by, or what I can do to correct it?

Thanks.

---

### Post by alastair on 2005-06-02
Nothing much to go on really ....

What "network" are you on - IP/mask etc. Describe it.

Output of :

ifconfig -a
route -n

---

### Post by caspian on 2005-06-02
Here's the output I get from running "ifconfig -a":

> eth0      Link encap:Ethernet  HWaddr 00:0E:35:68:AF:B0
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:1280 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1281 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000
          RX bytes:604366 (590.2 KiB)  TX bytes:149263 (145.7 KiB)
          Interrupt:11 Base address:0x2000 Memory:fceff000-fcefffff

eth1      Link encap:Ethernet  HWaddr 00:0E:7B:ED:90:0C
          inet addr:192.168.0.104  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::20e:7bff:feed:900c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1830 (1.7 KiB)  TX bytes:1404 (1.3 KiB)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:23188 errors:0 dropped:0 overruns:0 frame:0
          TX packets:23188 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:2118027 (2.0 MiB)  TX bytes:2118027 (2.0 MiB)

sit0      Link encap:IPv6-in-IPv4
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)


And "route -n"...

> Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     0.0.0.0         255.255.255.0   U     0      0        0 eth1
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 eth1


Thank you to anyone who can help me with this problem :D.

This seems to be very wierd -- I can connect to the network fine. Everyone else (including another Ubuntu machine) can connect to the network and ssh into my machine, but I can't seem to connect to any other computer on the network.

---

### Post by alastair on 2005-06-03
Something odd. 

Device eth0 is DOWN (not "up") but seems to have a lot of network packets transmitted/received.

Device eth1 is UP - but has hardly any network packets in/out.

Assuming your network is 192.168.0.0/24, the routing seems OK.

Have a look at your system log and see if there are any oddities in the probe/load for eth0 and eth1 i.e.

/var/log/syslog

Assuming other folks are not using firewalls etc.

---

### Post by janrinok on 2005-06-05
Alistair is giving lots of good advice but I am also confused by the fact that you have configured 2 NICs but you haven't mentioned why.  Most times when people have problems 'ping'ing its because they are accessing the wrong NIC.  Are you sure that your network is connected to the correct NIC?  Can you describe your network.  Is the machine that you are having problems with meant to be a firewall or gateway and, if not, why do you want to configure 2 NICs?
I find it easier to solve problems such as this in small stages e.g. configure 1 NIC, test it can talk to whatever it should talk to.  Then switch it off and configure the second NIC. ditto.  Then switch them both on and set up your bridge/firewall/gateway or whatever.  HTH and apologies to Alistair for butting in with my contribution.  Jan.

---

### Post by janrinok on 2005-06-05
Alastair
Apologies for spelling your name incorrectly in the previous posts - I should read more carefully!  Jan.

---

### Post by janrinok on 2005-06-05
Looking further into this one, if other computers can ping and ssh to you, then the connections are good. So, it looks like something is stopping traffic in the other direction and that seems to suggest a firewall.  What OS is on the other machines.  If it is XP are you sure that you haven't set the security level such that the firewall is invoked? Are you running ZoneAlarm, and is it set to accept your network?  If the other machines are also Linux, then what is in their logs?  Can you provide the 'ifconfig -a route -n' output for those machines as well?  Butting-out now..... Jan

---

