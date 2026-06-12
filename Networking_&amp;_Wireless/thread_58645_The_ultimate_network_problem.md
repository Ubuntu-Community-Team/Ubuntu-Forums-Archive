---
title: "The ultimate network problem"
date: 2005-08-21
forum: Networking &amp; Wireless
---

### Post by introspectif on 2005-08-21
[Although this is posted under 'Hardware Help', I doubt that this is a hardware problem. But since 'Networking' is the closest thing that the problem might fit into, I am posting it here.]

THE CONFIGURATION

Hardware:
Computer (Ubuntu 5.04, with dhclient3) - Router (SMC, SMC7004VBR) - ADSL Ethernet modem (Efficient Networks, SpeedStream 5260)

THE SYMPTOMS

Cannot access any sites in Mozilla Firefox. Cannot download packages through Synaptics. Cannot ping any addresses from the terminal... basically I'm just not connected.

Resetting the router makes everything work properly i.e. can access sites through Mozilla Firefox, can download packages through Synaptics etc.

THE BACKGROUND

I mainly use Slackware and Windows XP. I've tried some other Linux distros as well, such as DamnSmallLinux, Slax, Knoppix, PuppyLinux. I've had no problems accessing the Internet using those OS/distros with the same hardware configuration. Then comes Ubuntu.

I've tried Ubuntu 4.10, and had the same problem. So I told myself, maybe this is a bug that should be fixed by the next release. So when 5.04 was released, I installed it, only to find that the problem has not been fixed.

As a Linux newbie should, I searched the forums and Googled for solutions. Tried almost everything I could find e.g. the resolvconf+pump+dnsmasq solution, the disable-ipv6 solution, the dhcpcd solution... and none worked. And there are also some threads which do not even end with a solution -- perhaps the user forgot to inform us whether the solution worked. (Or he gave up altogether?)

THE COMPLAINT

To the developers, I would appreciate the reassurance that this is being worked on. I'm not hoping that Ubuntu will support unknown hardware of mine or make my computer do a magic trick in front of me. It's just a normal network configuration that should not screw up (evidence: all the other distros and Windows XP -- they just work). And even if there is some wonderful fix which I've yet to discover, it's still a fix -- my opinion remains that Internet should work out of the box.

THE PLEA

If there are users who have experienced the same problem and have found a solution that works, please post it here. I'd appreciate it very much. Thanks in advance.

---

### Post by nad on 2005-08-21
After you reset the router, does your connection last for your entire session?

If you log out and back in?

Have you tried with a static address?

---

### Post by cwaldbieser on 2005-08-21
[QUOTE=introspectif]
THE CONFIGURATION

Hardware:
Computer (Ubuntu 5.04, with dhclient3) - Router (SMC, SMC7004VBR) - ADSL Ethernet modem (Efficient Networks, SpeedStream 5260)
[/QUOTE]
I will assume that the router is connected to the ADSL modem and your Ubuntu machine is wired via ethernet to the router.  The output of the following commands is generally invaluable in diagnosing network problems:
```

$ ifconfig -a
$ route

``` 

If you have a working Linux box also plugged into the router, you may want to post that output, too, for comparison purposes.  If you have a working Windows box connected to the router, you can post the output of
```

C:\>ipconfig
c:\>route print

``` 
for the same comparison purpose.  This output will immediately give an overall picture of the network.  

Also, if you know the router's IP address from the LAN side of the network, it would probably be good if you could explicitly post that, though it can often be derived from one of the other outputs above.
Thanks.

---

### Post by introspectif on 2005-08-21
[QUOTE=nad]After you reset the router, does your connection last for your entire session?

If you log out and back in?

Have you tried with a static address?[/QUOTE]
 Yes, the connection lasts for the whole session, until I reboot the computer. 

I have not tried a static address, because I don't have the info I need to do that i.e. ISP's name servers etc. But that's besides the point anyway, because my connection works fine under Slackware and WIndows XP.

---

### Post by introspectif on 2005-08-21
I've only one Linux box, and here's the output of the two commands:
```
root@home:/ # ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:0E:2E:03:41:AA
          inet addr:192.168.2.101  Bcast:192.168.2.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:409 errors:0 dropped:0 overruns:0 frame:0
          TX packets:432 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:168907 (164.9 KiB)  TX bytes:120415 (117.5 KiB)
          Interrupt:10 Base address:0x1000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2955 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2955 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:265998 (259.7 KiB)  TX bytes:265998 (259.7 KiB)

root@home:/ # route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.2.0     *               255.255.255.0   U     0      0        0 eth0
default         .               0.0.0.0         UG    0      0        0 eth0
root@home:/ #
```

---

### Post by nad on 2005-08-21
It's not picking up the default gateway.

This does seem to be an ubuntu issue. Why does ubuntu's implementation of dhclient fail? Permissions? Anyone?

Have you modified /etc/dhclient.conf?

---

### Post by introspectif on 2005-08-21
This is my dhclient.conf : 

```
# Configuration file for /sbin/dhclient, which is included in Debian's
#	dhcp3-client package.
#
# This is a sample configuration file for dhclient. See dhclient.conf's
#	man page for more information about the syntax of this file
#	and a more comprehensive list of the parameters understood by
#	dhclient.
#
# Normally, if the DHCP server provides reasonable information and does
#	not leave anything out (like the domain name, for example), then
#	few changes must be made to this file, if any.
#

#send host-name "andare.fugue.com";
#send dhcp-client-identifier 1:0:a0:24:ab:fb:9c;
#send dhcp-lease-time 3600;
#supersede domain-name "fugue.com home.vix.com";
#prepend domain-name-servers 127.0.0.1;
request subnet-mask, broadcast-address, time-offset, routers,
	domain-name, domain-name-servers, host-name,
	netbios-name-servers, netbios-scope;
#require subnet-mask, domain-name-servers;
#timeout 60;
#retry 60;
#reboot 10;
#select-timeout 5;
#initial-interval 2;
#script "/etc/dhcp3/dhclient-script";
#media "-link0 -link1 -link2", "link0 link1";
#reject 192.33.137.209;

#alias {
#  interface "eth0";
#  fixed-address 192.5.5.213;
#  option subnet-mask 255.255.255.255;
#}

#lease {
#  interface "eth0";
#  fixed-address 192.33.137.200;
#  medium "link0 link1";
#  option host-name "andare.swiftmedia.com";
#  option subnet-mask 255.255.255.0;
#  option broadcast-address 192.33.137.255;
#  option routers 192.33.137.250;
#  option domain-name-servers 127.0.0.1;
#  renew 2 2000/1/12 00:00:01;
#  rebind 2 2000/1/12 00:00:01;
#  expire 2 2000/1/12 00:00:01;
#}
```

---

### Post by cwaldbieser on 2005-08-21
[QUOTE=introspectif]
root@home:/ # route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.2.0     *               255.255.255.0   U     0      0        0 eth0
default         .               0.0.0.0         UG    0      0        0 eth0
root@home:/ #[/CODE][/QUOTE]
If you issue these commands:
```
$ sudo route del -net default
$ sudo route add -net default gw 192.168.2.1
```
(delete your default route then add a new default route to your router), does that let you reach the Internet?  Note, this will not last through a reboot-- nad appears to be correct that something funky is going on with your dhclient.  

Also, I guessed your router is address 192.168.2.1-- but it's a pretty good guess based on your LAN network info given above.  This should be the same as your "default gateway" on WinXP.

---

### Post by introspectif on 2005-08-21
No, cwaldbieser, issuing those commands didn't fix it. Resetting my router is still the only way. Btw, I reckon you're correct that 192.168.2.1 is my router's IP address because that's address of the web interface to configure my router.

---

### Post by nad on 2005-08-21
Your dhclient.conf may be faulty. Personnally, I would comment out the request line and see if enough parameters are supplied automatically for a connection.

From man dhclient.conf:

       The require statement lists options that must be sent in order  for  an
       offer  to  be  accepted.    Offers  that  do not contain all the listed
       options will be ignored.

Edit: Sorry, I confused request and require, however, my previous suggestion still holds.

---

### Post by cwaldbieser on 2005-08-21
[QUOTE=introspectif]No, cwaldbieser, issuing those commands didn't fix it. Resetting my router is still the only way. Btw, I reckon you're correct that 192.168.2.1 is my router's IP address because that's address of the web interface to configure my router.[/QUOTE]
That's kinda weird.  What does the output do you get after issuing these commands:
```

$ sudo route del 0.0.0.0
$ sudo route add -net 0.0.0.0 netmask 255.255.255.255 gw 192.168.2.1
$ route

```

I am expecting it to look like:
```

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.2.0     *               255.255.255.0   U     0      0        0 eth0
default         192.168.2.1     0.0.0.0         UG    0      0        0 eth0

```

If it does look like that, try these tests:
```

$ ping -c 3 192.168.2.1
$ ping -c 3 64.233.161.147

```
The first test pings your router.
The second test pings [www.google.com](www.google.com), but doesn't do any DNS lookup.

If the routing table doesn't look how I am expecting, could you post what it does end up looking like?  Do those commands give any errors?

Thanks,

---

### Post by introspectif on 2005-08-25
I'm sorry for the inactivity on this thread. I work in the army and seldom get to go home to try your suggestion(s) on my computer. Will post the results when I get the opportunity.

---

### Post by introspectif on 2005-08-25
Here's my output, cwaldbieser. 

```
root@home:/ # route del 0.0.0.0
SIOCDELRT: No such process
root@home:/ # route add -net 0.0.0.0 netmask 255.255.255.255 gw 192.168.2.1
root@home:/ # route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
default         .               255.255.255.255 UGH   0      0        0 eth0
192.168.2.0     *               255.255.255.0   U     0      0        0 eth0
default         .               0.0.0.0         UG    0      0        0 eth0
root@home:/ #
```

It's like yours, but with an extra entry.

---

### Post by nad on 2005-08-25
Your routing table still shows no default route.

Issue the command: sudo /etc/init.d/networking restart

then: route

If your default route is not recognized, issue the command: route add default gw 192.168.2.1 .

---

### Post by introspectif on 2005-08-27
```
root@home:/ # /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                   [ ok ]
root@home:/ # route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
root@home:/ # route add default gw 192.168.2.1
SIOCADDRT: Network is unreachable
root@home:/ # route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
root@home:/ # ifup eth0
Internet Systems Consortium DHCP Client V3.0.1
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/eth0/00:0e:2e:03:41:aa
Sending on   LPF/eth0/00:0e:2e:03:41:aa
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPOFFER from 192.168.2.1
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 192.168.2.1
bound to 192.168.2.100 -- renewal in 1022363284 seconds.
root@home:/ # route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.2.0     *               255.255.255.0   U     0      0        0 eth0
default         .               0.0.0.0         UG    0      0        0 eth0
root@home:/ # /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                   [ ok ]
```

Still couldn't connect. So I reset my router. After my router was initialised i.e. the LED lights stopped blinking...

```
root@home:/ # route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
root@home:/ # route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
root@home:/ # route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
root@home:/ # route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
root@home:/ # route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
root@home:/ # ifup eth0
Internet Systems Consortium DHCP Client V3.0.1
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

Listening on LPF/eth0/00:0e:2e:03:41:aa
Sending on   LPF/eth0/00:0e:2e:03:41:aa
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPOFFER from 192.168.2.1
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 192.168.2.1
bound to 192.168.2.100 -- renewal in 1022363084 seconds.
root@home:/ # route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.2.0     *               255.255.255.0   U     0      0        0 eth0
default         .               0.0.0.0         UG    0      0        0 eth0
root@home:/ #
```

Now I'm connected, so I posted this.

---

