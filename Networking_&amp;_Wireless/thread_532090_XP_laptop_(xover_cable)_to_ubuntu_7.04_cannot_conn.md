---
title: "XP laptop (xover cable) to ubuntu 7.04 cannot connect internet"
date: 2007-08-22
forum: Networking &amp; Wireless
---

### Post by SnakeHips on 2007-08-22
HI ,I have honestly tried and tried again to get my xp laptop to "see" the internet via my ubuntu box without success. Additionally I have read and read many threads here with the similar problem but now I am stuck.

The ubuntu box connects to the internet via adsl modem

The xp laptop connects to the ubuntu box via a crossover cable.

the machines can "ping" eachother. 

Any help will be gratefully recieved...

---

### Post by livestockPimp on 2007-08-22
copy the output of "ifconfig" and "route" in here.

---

### Post by SnakeHips on 2007-08-22
My son will be so happy if this can be fixed.......



>>ifconfig.........

eth0:avah Link encap:Ethernet  HWaddr 00:11:2F:7F:61:E1  
          inet addr:169.254.7.214  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:83 errors:0 dropped:0 overruns:0 frame:0
          TX packets:83 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:6444 (6.2 KiB)  TX bytes:6444 (6.2 KiB)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:90.240.128.246  P-t-P:62.25.195.38  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:29066 errors:0 dropped:0 overruns:0 frame:0
          TX packets:29272 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:6121455 (5.8 MiB)  TX bytes:1996510 (1.9 MiB)


pete@myplace:~$ route 
Kernel IP routeing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
l0.wfd103.plane *               255.255.255.255 UH    0      0        0 ppp0
link-local      *               255.255.0.0     U     0      0        0 eth0
default         *               0.0.0.0         U     0      0        0 ppp0
default         *               0.0.0.0         U     1000   0        0 eth0
pete@myplace:~$

---

### Post by livestockPimp on 2007-08-22
few more questions, is this a USB modem, or LAN modem, next have you got the "default gateway" on the laptop configured as the IP address of the Linux machine?

---

### Post by SnakeHips on 2007-08-22
Hi,

Its a USB ADSL modem and works fine with the ubuntu box.

ive set these values on the  laptop

ip address: 192.168.0.1 

subnet : 255:255:255:0 

These values i got from system/administartion/network settings/wired connaection.


Hope im not being thick...

---

### Post by livestockPimp on 2007-08-22
ok, I dont even know how you would be pinging the other computer, your eth0 (the only network card in your machine according to the output you posted from ifconfig) is on a completely different network.

you will need to make eth0 on the same network as the windows machine, eg: give it a 192.168.0.10 IP

to do this type "ifconfig eth0 192.168.0.10" this will put them on the same network. with this done you can now go back to the network settings on the windows PC and set it to have the 192.168.0.1 IP with a subnet of 255.255.255.0, default gateway 192.168.0.10  (this needs to be the IP of the ethernet adapter the linux machine is connected to it on) and for the primary DNS set it to 192.168.10.1

this should work I believe.

---

### Post by livestockPimp on 2007-08-22
if you want to make the network card always have the same IP on the linux box, edit the /etc/network/interfaces with your favorite editor,
pico /etc/network/interfaces
and set the IP under the eth0 section.

---

### Post by SnakeHips on 2007-08-23
I must be missing something here..... ?

ok, so i've fixed the i.p. address on eth0

>>>>>>>>>>>>>>>>>>>

pete@myplace:~$ ifconfig 
eth0      Link encap:Ethernet  HWaddr *************************  
          inet addr:192.168.0.10  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::211:2fff:fe7f:61e1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:51 errors:0 dropped:0 overruns:0 frame:0
          TX packets:64 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:7244 (7.0 KiB)  TX bytes:10032 (9.7 KiB)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:72 errors:0 dropped:0 overruns:0 frame:0
          TX packets:72 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5404 (5.2 KiB)  TX bytes:5404 (5.2 KiB)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:84.68.8.43  P-t-P:62.25.198.136  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:1044 errors:0 dropped:0 overruns:0 frame:0
          TX packets:883 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:1209274 (1.1 MiB)  TX bytes:97800 (95.5 KiB)

pete@myplace:~$ route
Kernel IP routeing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
ge0-1.lns1-c10. *               255.255.255.255 UH    0      0        0 ppp0
192.168.0.0     *               255.255.255.0   U     0      0        0 eth0
link-local      *               255.255.0.0     U     1000   0        0 eth0
default         *               0.0.0.0         U     0      0        0 ppp0
pete@myplace:~$ 

>>>>>>>>>>>>>>

............and the settings on the xp laptop are as follows

I.P.         192.168.0.1
subnet mask  255.255.255.0
def gateway  192.168.0.10
pref dns     192.168.10.1

......and when I ping the xp laptop

pete@myplace:~$ ping 192.168.0.1
PING 192.168.0.1 (192.168.0.1) 56(84) bytes of data.
64 bytes from 192.168.0.1: icmp_seq=1 ttl=128 time=0.106 ms
64 bytes from 192.168.0.1: icmp_seq=2 ttl=128 time=0.104 ms
64 bytes from 192.168.0.1: icmp_seq=3 ttl=128 time=0.102 ms
64 bytes from 192.168.0.1: icmp_seq=4 ttl=128 time=0.124 ms
64 bytes from 192.168.0.1: icmp_seq=5 ttl=128 time=0.121 ms
64 bytes from 192.168.0.1: icmp_seq=6 ttl=128 time=0.114 ms
64 bytes from 192.168.0.1: icmp_seq=7 ttl=128 time=0.106 ms
64 bytes from 192.168.0.1: icmp_seq=8 ttl=128 time=0.125 ms
64 bytes from 192.168.0.1: icmp_seq=9 ttl=128 time=0.118 ms


....and the xp laptop can *ping* and get replies from the ubuntu box.

I tried to ping google from the laptop but it times out

Seems the xp laptop cant see further than the ubuntu box.......any ideas?

---

### Post by livestockPimp on 2007-08-23
............and the settings on the xp laptop are as follows

I.P. 192.168.0.1
subnet mask 255.255.255.0
def gateway 192.168.0.10
pref dns 192.168.10.1

DNS is meant to be 192.168.0.10

(Sorry, that was a typo I made, was 4am when i wrote that)

---

### Post by livestockPimp on 2007-08-23
once this is done, don't just try and ping the machine it is connected to, try to ping an external IP of a server or something, maybe try your ISP's dns server.

if this is not working still then on the XP machine type "tracert <INSERT EXTERNAL IP>" this will show you the route path ensuring that you are getting an extrernal connection.

---

### Post by will71110 on 2007-08-23
do a tracert 1.1.1.1 from your xp box and post here.

---

### Post by SnakeHips on 2007-08-23
.....and the settings on the xp laptop are now......

I.P. 192.168.0.1
subnet mask 255.255.255.0
def gateway 192.168.0.10
pref dns 192.168.0.10

still no luck though ,get "page not found error" in browser.......not sure where to look now ??

---

### Post by will71110 on 2007-08-23
Question about your DNS.  You have your XP box pointed at your Ubuntu box for DNS requests.  Are you running a DNS server on that box?  If not that wont work.  What you can do however is point your xp box to the same DNS as the Ubuntu box.

---

### Post by SnakeHips on 2007-08-23
....from the xp laptop......tracert 1.1.1.1.

tracing route to 1.1.1.1.
over a maximum of 30 hops

1	 *	*	*     request timed out
2
3
4
5
6
7
8
9
10 etc etc etc

---

### Post by will71110 on 2007-08-23
Ok...so it looks like your not getting routed though ubuntu.  Wht does route in the command promp show on your XP box?

---

### Post by SnakeHips on 2007-08-23
....route at command prompt the following....

Route

Displays and modifies the entries in the local IP routing table. Used without parameters, route displays help.
Syntax

route [-f] [-p] [Command [Destination] [mask Netmask] [Gateway] [metric Metric]] [if Interface]]
Top of pageTop of page
Parameters

-f : Clears the routing table of all entries that are not host routes (routes with a netmask of 255.255.255.255), the loopback network route (routes with a destination of 127.0.0.0 and a netmask of 255.0.0.0), or a multicast route (routes with a destination of 224.0.0.0 and a netmask of 240.0.0.0). If this is used in conjunction with one of the commands (such as add, change, or delete), the table is cleared prior to running the command.

-p : When used with the add command, the specified route is added to the registry and is used to initialize the IP routing table whenever the TCP/IP protocol is started. By default, added routes are not preserved when the TCP/IP protocol is started. When used with the print command, the list of persistent routes is displayed. This parameter is ignored for all other commands. Persistent routes are stored in the registry location HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\Tcpip\Parameters\PersistentRoutes.

Command : Specifies the command you want to run. The following table lists valid commands.
Command	Purpose

add
Adds a route.

change
Modifies an existing route.

delete
Deletes a route or routes.

print
Prints a route or routes.

---

### Post by will71110 on 2007-08-23
Sorry. forgot to say route print

But I think I have your problem solved.  you have to mod yout iptables in ubuntu to forward traffic.  I'm doing alittle reading on it and I'll post again when or if I have it figured out.

EDIT:  You'll have to turn your ubuntu box into a NAT.  iptables will let you do this but it has to be ran in root.  this page talks about how to do this if you would like to read up.  [http://www.revsys.com/writings/quicktips/nat.html](http://www.revsys.com/writings/quicktips/nat.html)( on the site it says use eth0 and eth1....Your going to using ppp0 as your external interface and eth0 and the internal)

---

### Post by will71110 on 2007-08-23
See the edit above

---

