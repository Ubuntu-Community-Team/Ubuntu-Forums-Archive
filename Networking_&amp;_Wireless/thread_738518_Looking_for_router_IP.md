---
title: "Looking for router IP"
date: 2008-03-28
forum: Networking &amp; Wireless
---

### Post by Alarindris on 2008-03-28
I'm trying to figure out what my router's IP address is.  I pulled an old one out of the graveyard and I want to make sure the firewall is on etc.  Its a linksys and I've tried 192.168.0.1, 192.168.1.0 and 192.168.1.1 in my browser and none are right (or I'm not getting the login screen). 

```
ifconfig -a
```

returns 

```
eth0      Link encap:Ethernet  HWaddr 00:16:17:31:E1:74  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:20 

eth1      Link encap:Ethernet  HWaddr 00:E0:29:1D:34:4F  
          inet addr:70.94.248.100  Bcast:255.255.255.255  Mask:255.255.240.0
          inet6 addr: fe80::2e0:29ff:fe1d:344f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:231365 errors:0 dropped:0 overruns:0 frame:0
          TX packets:136574 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:221699213 (211.4 MB)  TX bytes:22772151 (21.7 MB)
          Interrupt:19 Base address:0x2c00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:866 errors:0 dropped:0 overruns:0 frame:0
          TX packets:866 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:72016 (70.3 KB)  TX bytes:72016 (70.3 KB)
```

```
route -n
```

returns 

```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
70.94.240.0     0.0.0.0         255.255.240.0   U     0      0        0 eth1
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth1
0.0.0.0         70.94.240.1     0.0.0.0         UG    0      0        0 eth1

```

Not sure where to go from here.  Any thing else I can try?

---

### Post by jimv on 2008-03-28
Try 70.94.240.1

---

### Post by jetsam on 2008-03-28
Mine's the same as my gateway address, which in your case is 70.94.240.1.  Seems an unusual address for a consumer router, as they're usually 10.x.x.x or 192.x.x.x.  

Give 70.94.240.1 a try.  Your setup is more complex than mine.  Your eth0 doesn't even have an ip address assigned, so you must be using eth1.  I assume that makes sense for your hardware.

---

### Post by chili555 on 2008-03-28
```
chili@LAPTOP60:~$ whois 70.94.240.1

OrgName:    Road Runner HoldCo LLC 
OrgID:      RRWE
Address:    13241 Woodland Park Road
City:       Herndon
StateProv:  VA
PostalCode: 20171
Country:    US
```Looks like you are attached directly to the DSL or cable modem, not the router.

If you attach to the router and leave the DSL or cable modem out of the chain, can you do:```
sudo dhclient eth1
```and get an IP address? If so, please post that *ifconfig.* Thanks.

---

### Post by Alarindris on 2008-03-28
sudo dhclient eth1 returns

```
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth1/00:e0:29:1d:34:4f
Sending on   LPF/eth1/00:e0:29:1d:34:4f
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
DHCPOFFER from 76.51.64.1
DHCPREQUEST on eth1 to 255.255.255.255 port 67
DHCPACK from 76.51.64.1
bound to 70.94.248.100 -- renewal in 37319 seconds.
```

ifconfig returns

```
eth0      Link encap:Ethernet  HWaddr 00:16:17:31:E1:74  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:20 

eth1      Link encap:Ethernet  HWaddr 00:E0:29:1D:34:4F  
          inet addr:70.94.248.100  Bcast:255.255.255.255  Mask:255.255.240.0
          inet6 addr: fe80::2e0:29ff:fe1d:344f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:928745 errors:0 dropped:0 overruns:0 frame:0
          TX packets:588635 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:898784470 (857.1 MB)  TX bytes:93946824 (89.5 MB)
          Interrupt:19 Base address:0x2c00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:3527 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3527 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:297172 (290.2 KB)  TX bytes:297172 (290.2 KB)


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:3527 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3527 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:297172 (290.2 KB)  TX bytes:297172 (290.2 KB)
```

Eth0 is my onboard card, im using a PCI card, eth1. Not sure what 70.94.240.1 is, but I can't connect to it. Same with 76.51.64.1 and 70.94.248.100.

---

### Post by stroyan on 2008-03-28
Press the reset button on the back of the router.  That should reset address and password.
And go to linksys.com to get firmware updates and download the manual.

---

### Post by Alarindris on 2008-03-28
Ok, well I considered that.  Will I have any trouble reconnecting to it?

---

### Post by stroyan on 2008-03-28
It ought to be easier to use with default settings than whatever random settings it had when you found it.  Of course, you should change the admin password to a non-default value.
If it is already some non-default value then you will be pressing the reset button soon anyway,
(unless the admin password is written on the bottom of the case ;-)

---

### Post by Alarindris on 2008-03-28
Good call.  Sometimes it's easier to start from scratch.

---

### Post by jetsam on 2008-03-28
If restarting the router gives you connectivity problems, you can connect directly to the cable modem to get online for further assistance.  

Get the manual first, though...  you need to find out the default password before you reset it.  

It seems like it's set up to act only as a switch at this point and not a router.  The only problem I can forsee is if your dsl or cable modem already has a router inside it.  (some of them do.)  Two routers can cause conflicts.

---

### Post by Alarindris on 2008-03-28
Well, that didn't work either.   I reset the modem and ran 
sudo dhclient eth1

returning
```
There is already a pid file /var/run/dhclient.pid with pid 6404
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth1/00:e0:29:1d:34:4f
Sending on   LPF/eth1/00:e0:29:1d:34:4f
Sending on   Socket/fallback
DHCPREQUEST on eth1 to 255.255.255.255 port 67
DHCPNAK from 192.168.1.1
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
DHCPOFFER from 76.51.64.1
DHCPREQUEST on eth1 to 255.255.255.255 port 67
DHCPACK from 76.51.64.1
bound to 70.94.248.100 -- renewal in 31814 seconds.

```

Woot, thought it was fixed.  Tried 192.168.1.1, and it still hasn't connected.  I pinged it in the terminal and nothing has happened for at least 2-3 minutes now. Hmmm...

---

### Post by Alarindris on 2008-03-28
Missed that last reply.  I know what the default password would be, so no problems, could look it up anyway.  My cable modem is not a router, it only has one output on it.

---

### Post by jetsam on 2008-03-28
> DHCPNAK from 192.168.1.1

That's at least a sign of life from the router.  DHCPNAK is DHCP negative aknowlegement.  I'm thinking maybe the router is not bound correctly to the cable modem yet.  I think what I would do at this point is disconnect the computer, then power cycle the cable modem and router together alone so they establish communications with each other and then reconnect the computer to the router and try dhclient again.  

AN alternative would be to take the cable modem out of the picture like chili555 recommended and just connect to the router.

---

### Post by Alarindris on 2008-03-28
Ok, I will try power cycling.  Not sure what you mean by taking the cable modem out of the picture though, I thought I already did that.  Will post my results after the restart.

---

### Post by Alarindris on 2008-03-28
No luck after power cycling.  I should also clarify that I have no reason to believe there is anything wrong with the router, I am also currently going through the router, no connection problems.  Just cant find it!

---

### Post by jetsam on 2008-03-28
You're getting an ip address assigned from Road Runner instead of the router.  This puts you on a different subnet than the router, so you can't communicate with it.  

If you unplug the router from the cable modem entirely, you won't be getting dhcp responses from the cable company so hopefully, you should get assigned a 192.168.1.x address by the router and can communicate with the router directly.  Of course, you won't be on the internet at that point...  

...I don't know what you do at that point.  Rejoice in your router?  Sorry, I'm reaching the limits of my comprehension. :???:

---

### Post by Alarindris on 2008-03-28
Ok, maybe I'm not understanding you then.  You want me to unplug the ethernet cables?  Please hang with me here, I don't like not having a firewall up : /

---

### Post by Alarindris on 2008-03-28
Update:  I can access the router no problem in XP, the other computer attached to the router.  That is not cool.  I am also not listed on the DHCP clients table.  When I run dhclient eth1 it sees the router and then binds me to the cable modem.

Edit: It appears my firmware is also out of date.  I've got an updated .bin file, but no idea what to do with it, never updated with linux before, I'm fairly new.  Any advice on that would be much appreciated.

---

### Post by jetsam on 2008-03-28
Would be easier to upgrade from XP at this point since you can't connect from Linux yet.  Possibly that would solve your problem.  

It's good that the router is working with XP, though.  

What I don't understand is why the router isn't assigning you an ip address.  I'm pretty sure you could do it manually by setting yourself a static ip address with these settings:
```
ip: 192.168.1.101
subnet mask: 255.255.255.0
gateway address: 192.168.1.1

```

If that works, it should give you net access and enable you to get to the router admin page.  Maybe its logs can give you a clue about why it rejected your DHCP request.

---

### Post by chili555 on 2008-03-28
> I don't like not having a firewall up : /Not me, either, but we are going to isolate you completely from the outside world temporarily. Something sounds very wrong.

On the back of your router, you should have 5 ethernet jacks, one marked 'WAN' and 4 marked 'LAN.' Please disconnect the cable modem from it's jack completely. Now your Ubuntu machine should be connected to any of the 'LAN' jacks. Reboot it and then run *ifconfig*. Do you get a 192.168.x.x IP address?

Your Ubuntu machine and your XP machine should be connected to LAN jacks and your cable modem to the only WAN jack. Is that how you've done it?

---

### Post by Alarindris on 2008-03-29
*Your Ubuntu machine and your XP machine should be connected to LAN jacks and your cable modem to the only WAN jack. Is that how you've done it?*

Actually no, I've got the cable modem plugged into 'uplink' assuming WAN was for wireless or something, although it is not a wireless router. In total I've got 6 jacks.  I'll try rebooting with it removed and see what happens.

---

### Post by jetsam on 2008-03-29
The uplink port is for expanding the router with an additional switch to add more ports.  WAN just stands for Wide Area Network, in this case AKA the internet.  

The modem should be connected to the WAN port.  More than likely, that will fix the problem.  

It makes some sense out of why your cable company is even getting your DHCP requests to begin with.  Most routers should stop broadcast requests like DHCP so that they only communicate internally throughout the network.  Since you're connected through the uplink port, the requests are being forwarded on to the cable modem.

---

### Post by Alarindris on 2008-03-29
Awesome, that fixed it.  It's interesting to note that running windows all these years, hooking up the router that way, I never noticed it.  On the other hand, it didn't really seem to pose a problem (although I could be wrong).

Thanks for all the help, I will try to repay the forums as best I can :D

Alar

---

