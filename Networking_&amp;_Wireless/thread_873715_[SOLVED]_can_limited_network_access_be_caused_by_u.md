---
title: "[SOLVED] can limited network access be caused by ubuntu settings?"
date: 2008-07-29
forum: Networking &amp; Wireless
---

### Post by chuckbert on 2008-07-29
######################################################
Apparent solution is to manually add the gateway:
sudo route add default gw xxx.xxx.202.1
I see no reason that a reboot could have modified this.
######################################################

Hi,
My machine (running dapper) spontaneously restarted on Fri 18th July. When it came back up, network access is limited to machines on the same subnet. I can ping (ssh etc) any machine but any machine outside that subnet is met with 'Cannot reach network'. 
e.g. if my machine is xxx.xxx.202.78, I can ping xxx.xxx.202.79 fine, but not xxx.xxx.201.5.

This is on a university network and my it support is frankly pitiful.
I can't see anyway that this could be an issue with my machine, and that it is more likely to be a problem in the switch. 
Before I start shouting at people, I'd like some confirmation that this kind of behaviour can't stem from my machine.
If I'm wrong and there are any sensible diagnostics I can do, I'd be grateful for suggestions.

---

### Post by bab1 on 2008-07-29
Can you ping the gateway (your router/modem)?  It sounds like you lost the gateway.  Try ```
cat /etc/network/interfaces
``` to see if you have a gatway listed.

---

### Post by chuckbert on 2008-07-29
Thanks for the response.

I'm using dhcp so the relevant part of my /etc/network/interfaces says:

auto eth0
iface eth0 inet dhcp

ifconfig:
eth0      Link encap:Ethernet  HWaddr 00:01:80:63:02:F0  
          inet addr:XXXXXXXXXX  Bcast:XXXXXXXXXX  Mask:255.255.255.0
          inet6 addr: fe80::201:80ff:fe63:2f0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:721577 errors:0 dropped:0 overruns:0 frame:0
          TX packets:95673 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:114125445 (108.8 MiB)  TX bytes:91115760 (86.8 MiB)
          Interrupt:177 

I can ping the gateway xxx.xxx.202.1

The neighbouring machine is a macosx box which is networking fine (ifconfig below). THis makes me think that it must be something in ubuntu. The problem started after a restart which most probably included some updates, possibly even a kernel patch. Next time I'm at the machine I may try to reboot to the old kernel and see if it recovers.

ifconfig:
en0: flags=8863<UP,BROADCAST,SMART,RUNNING,SIMPLEX,MULTICAST> mtu 1500
        inet6 fe80::20d:93ff:fe63:d10a%en0 prefixlen 64 scopeid 0x4 
        inet XXXXXXXXXXXXX netmask 0xffffff00 broadcast XXXXXXXXXXXXXX
        ether 00:0d:93:63:d1:0a 
        media: autoselect (100baseTX <full-duplex>) status: active
        supported media: none autoselect 10baseT/UTP <half-duplex> 10baseT/UTP <full-duplex> 10baseT/UTP <full-duplex,hw-loopback> 100baseTX <half-duplex> 100baseTX <full-duplex> 100baseTX <full-duplex,hw-loopback>

---

### Post by bab1 on 2008-07-29
How about pinging google.com?  Maybe DNS is not working.  The DNS sever should be listed in /etc/resolv.conf if it is set statically.  

You can also see it in System >>Administration>>Network.

EDIT: This is a good description DNS services:
[http://ubuntu-tutorials.com/2007/03/14/how-to-setup-opendns-on-ubuntu/]("http://ubuntu-tutorials.com/2007/03/14/how-to-setup-opendns-on-ubuntu/")

---

### Post by chuckbert on 2008-07-29
At first I thought it was just a DNS issue, but I can't get a route to the DNS server. The problem seems to be that I can only get a route to my subnet (regardless of DNS names, using IP only).

---

### Post by bab1 on 2008-07-29
Make your router the dns server

read the tut I listed.

---

### Post by bab1 on 2008-07-29
Can you ping any of these:

google.com
64.233.187.99
128.125.253.136

EDIT:
So upon my re-read --
> (regardless of DNS names, [COLOR="Magenta"]using IP only[/COLOR]).

This is defiantly a DNS config problem.

---

### Post by chuckbert on 2008-07-30
Hi bab1,
Sorry - I think you misunderstood my meaning.
I am on xxx.xxx.202.78 and can only ping 202.1 .. 202.255
I cannot ping anything else (Network is unreachable).
As I mentioned above, this is a poorly admnisitered university lan, so I have no control over which machine to use as dns server. 
My dns server is xxx.xxx.201.2. I cannot ping this as it's not on my subnet. So, I cannot ping anything by dns name.
Thus the problem is that I cannot get a route out of xxx.xxx.202 from my ubuntu machine.
A macosx machine with analogous setup can get out.
I am trying to find out if there is any way this problem could be caused on my ubuntu box (after all the macosx machine works and this behaviour occurred after a reboot probably incorporating updates), or if it is more likely to be in the router, in which case I have to go and shout at someone to get it sorted out.

---

### Post by chuckbert on 2008-07-30
This guy seems to have had a similar problem (although vmware is involved somehow).
[http://ubuntuforums.org/showthread.php?p=5488275](http://ubuntuforums.org/showthread.php?p=5488275)
I will try booting with a previous kernel and see what happens.

---

### Post by chuckbert on 2008-07-30
Apparent solution is to manually add the gateway:
sudo route add default gw xxx.xxx.202.1
I see no reason that a reboot could have modified this ...

---

