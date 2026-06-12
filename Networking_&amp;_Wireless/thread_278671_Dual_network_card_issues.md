---
title: "Dual network card issues"
date: 2006-10-16
forum: Networking &amp; Wireless
---

### Post by dogend on 2006-10-16
I am sure this is something stupid but I just can't seem to figure it out.  I have 2 Ubuntu machines both running lamp 6.06.  They are fairly fresh installs with not much done to them.  Each machine as 2 Ethernet cards (eth0 and eth1.  For some reason I can't get the second pair (the eth1s) to talk when they are on a different subnet/hub.  If I configure them on the same subnet and move them all to the same hub as the eth0 all 4 cards can talk to each other.  i have tested both hubs and they work fine.  it looks to me like it is somehow routing traffic on the local eth1 network to the default route which sits on the eth0 connected network.  here are some dumps:
---------------------------------
server 2 interfaces config
cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
address 192.168.1.37
netmask 255.255.255.0
gateway 192.168.1.1

auto eth1
iface eth1 inet static
address 172.16.1.37
netmask 255.255.255.0


--------------------------------------
server 1 interfaces config
gfhs001:~$ cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
#iface eth0 inet dhcp
iface eth0 inet static
address 192.168.1.47
netmask 255.255.255.0
gateway 192.168.1.1

auto eth1
iface eth1 inet static
address 172.16.1.47
netmask 255.255.255.0


--------------------------------
route -n on server2
gfhs002:/$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
172.16.1.0      0.0.0.0         255.255.255.0   U     0      0        0 eth1
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0

---------------------------------------------------

ifconfig on server2
eth0      Link encap:Ethernet  HWaddr 00:09:6B:2B:3F:DD
          inet addr:192.168.1.37  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::209:6bff:fe2b:3fdd/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7839 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7292 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1495570 (1.4 MiB)  TX bytes:876557 (856.0 KiB)

eth1      Link encap:Ethernet  HWaddr 00:08:54:B1:9B:A8
          inet addr:172.16.1.37  Bcast:172.16.1.255  Mask:255.255.255.0
          inet6 addr: fe80::208:54ff:feb1:9ba8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3 errors:0 dropped:1073741806 overruns:0 frame:0
          TX packets:6 errors:0 dropped:112 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:180 (180.0 b)  TX bytes:468 (468.0 b)
          Interrupt:217 Base address:0x4000

---------------------------------------------
ifconfig on server1
ifconfig
eth0      Link encap:Ethernet  HWaddr 00:09:6B:43:7F:62
          inet addr:192.168.1.47  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::209:6bff:fe43:7f62/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3892 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5209 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:428434 (418.3 KiB)  TX bytes:540105 (527.4 KiB)

eth1      Link encap:Ethernet  HWaddr 00:08:54:B1:91:81
          inet addr:172.16.1.47  Bcast:172.16.1.255  Mask:255.255.255.0
          inet6 addr: fe80::208:54ff:feb1:9181/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3 errors:0 dropped:0 overruns:0 frame:0
          TX packets:23 errors:0 dropped:124 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:294 (294.0 b)  TX bytes:1875 (1.8 KiB)
          Interrupt:209 Base address:0xa000

----------------------------------------
route -n on server1
route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
172.16.1.0      0.0.0.0         255.255.255.0   U     0      0        0 eth1
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0


-----------------------------------
there seems to be a huge number of drops on server 2 however when i configure both server eth1 on the 192.168.1.x subnets it all works fine so it doesn't seem to be hardware.

Any help would be greatly appreciated.

---

### Post by mips on 2006-10-17
Give us a bit of a network diagram of how things are connected. Do you have multiple gateways ?

Dunno what you are trying to achieve so i'm taking a stab at it.

No traffic will go via Eth1 as it only advertises a route to 172.16.1.0 unless the traffic is destined for that specific network.

---

### Post by dogend on 2006-10-17
192.168.1.x is where all the users and the gateway to the internet will be connected.  The 172.16.1.x is just for the 2 servers to replicate data back and forth.  I had a need for backups every 10 minutes and even though rsync only copies changes I wanted to try and keep it on a different network as to not impact users as much.  basically nothing but server to server should be going over the 172.16.1.x.

---

### Post by dogend on 2006-10-17
duplicate

---

### Post by alaman on 2006-10-17
Are the eth1 interfaces connected via another hub and/or a cross'd cable?

---

### Post by mips on 2006-10-17
Can you ping from the one server to the other using the 172 addresses ?
What does the traceroute output look like if you try and trace the route taken from the one server to the other using the 172 addresses ?

---

### Post by dogend on 2006-10-18
i am not sure i know why but i reinstalled ubuntu on server1 and the problem went away.  thanks for the interest mips and alaman in helping me out.

---

### Post by Gizmo_RA2 on 2006-10-24
Hi I am having a similar problem :S

I have a server with 2 ethernet cards, eth0 is a Gigabit card and eth1 is 100Mb.

I want to set it up like this.....


192.168.1.254 192.168.1.41-192.168.1.43 192.168.1.46
Router----------eth1-----------eth0-----------Desktop

sorry about the spacing, don't know how to insert &nbsp's into this forum :S

The desktop can't access eth1 (thats to be expected)
The problems begin with the desktop not being able to access eth0 (not supposed to happen :S)
eth0 can ping 192.168.1.46 (expected)
eth1 can ping 192.168.1.254 (expected)
eth0 can not ping 192.168.1.254 (expected)
eth1 can not ping 192.168.1.46 (expected)
The router can access eth0 and eth1 (its only supposed to access eth1 :S)

I also eventually want it so eth1 and eth0 are bridged but still have ip addresses (but I havn't got to the bridging yet)

/etc/network/interfaces
########################
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.1.43
netmask 255.255.255.0
gateway 192.168.1.254

auto eth1
iface eth1 inet static
address 192.168.1.41
netmask 255.255.255.0
########################


ifconfig
########################
eth0
Link encap:Ethernet
inet addr:192.168.1.43 Bcast:192.168.1.255 Mask:255.255.255.0

eth1
Link encap:Ethernet
inet addr:192.168.1.41 Bcast:192.168.1.255 Mask:255.255.255.0
########################

If you need anymore info or want me to post elsewhere just let me know.

---

### Post by mips on 2006-10-24
> **Gizmo_RA2 said:**
> Hi I am having a similar problem :S


No, your problem is completely different.

You have both nics on one machine within the same subnet, this is a big no-no.

See post #11 below for a explanation.
[http://www.ubuntuforums.org/showthread.php?t=117356](http://www.ubuntuforums.org/showthread.php?t=117356)

If you want both (or more) nics on one machine to work at the same time you HAVE to do nic bonding or put each nic into a different subnet, all depends on the application.

In your case each nic has to be in a seperate network.

---

