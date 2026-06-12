---
title: "[SOLVED] After getting ip-address cannot ping router that gave it"
date: 2008-03-31
forum: Networking &amp; Wireless
---

### Post by mlentink on 2008-03-31
I'm trying to troubleshoot a weird networking problem and I could use help.

The system concerned (HP/Compaq nx7400 notebook) runs Gutsy in a dual boot setup with XP. 
With XP there are no netwrking problems whatsoever. It connect wirelessly to the router, to the internet and sees all aother machines in the network.

A couple of days ago however, Ubuntu lost its connection to the internet. After which I started finding out why.

What I've checked so far:

The internal wireless card comes up and works. (checked with ifconfig)
It applies for, and gets an IP from the DHCP-server in the router. (checked with dhclient)
It then fails to see that very same router, or any other system in the network, except for my Ubuntu server:```

martin@alphard:~$ sudo dhclient -r eth1
There is already a pid file /var/run/dhclient.pid with pid 6502
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth1/00:18:de:be:b1:9a
Sending on   LPF/eth1/00:18:de:be:b1:9a
Sending on   Socket/fallback
DHCPRELEASE on eth1 to 192.168.123.254 port 67
martin@alphard:~$ sudo dhclient eth1
There is already a pid file /var/run/dhclient.pid with pid 134519120
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth1/00:18:de:be:b1:9a
Sending on   LPF/eth1/00:18:de:be:b1:9a
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3
ip length 331 disagrees with bytes received 534.
accepting packet with data after udp payload.
DHCPOFFER from 192.168.123.254
DHCPREQUEST on eth1 to 255.255.255.255 port 67
ip length 331 disagrees with bytes received 534.
accepting packet with data after udp payload.
DHCPACK from 192.168.123.254
bound to 192.168.123.100 -- renewal in 35561 seconds.
martin@alphard:~$ ping 192.168.123.254
PING 192.168.123.254 (192.168.123.254) 56(84) bytes of data.

--- 192.168.123.254 ping statistics ---
9 packets transmitted, 0 received, 100% packet loss, time 8027ms

martin@alphard:~$ ping -c 3 192.168.123.3
PING 192.168.123.3 (192.168.123.3) 56(84) bytes of data.
64 bytes from 192.168.123.3: icmp_seq=1 ttl=64 time=1.70 ms
64 bytes from 192.168.123.3: icmp_seq=2 ttl=64 time=1.83 ms
64 bytes from 192.168.123.3: icmp_seq=3 ttl=64 time=1.70 ms

--- 192.168.123.3 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2000ms
rtt min/avg/max/mdev = 1.701/1.747/1.837/0.063 ms
martin@alphard:~$ ping 192.168.123.1
PING 192.168.123.1 (192.168.123.1) 56(84) bytes of data.

--- 192.168.123.1 ping statistics ---
4 packets transmitted, 0 received, 100% packet loss, time 3010ms
```

Obviously, since it doesn't see the router/gateway, it doesn't have internet access, so I'm unfortunately typing this in Windows...

Anybody out here that can point me in the right direction?
You help is very appreciated, as I want to get back to a real os asap ;-)


Edit: I thought I had searched well before posting, but still overlooked [this post]("http://ubuntuforums.org/showthread.php?t=686354"), which went unanswered. There must be a couple of gurus out here that can ppoint us in the right direction...

---

### Post by mlentink on 2008-03-31
bump, after edit

---

### Post by superprash2003 on 2008-03-31
there could be an ip conflict.. could you post your ifconfig and ping results to router and say google.com

---

### Post by mlentink on 2008-03-31
I don really think there's a IP-conflict, but I could be mistaken

ifconfig:```

eth0      Link encap:Ethernet  HWaddr 00:17:08:45:58:B0  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:16 

eth1      Link encap:Ethernet  HWaddr 00:18:DE:BE:B1:9A  
          inet addr:192.168.123.100  Bcast:192.168.123.255  Mask:255.255.255.0
          inet6 addr: fe80::218:deff:febe:b19a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6772 errors:0 dropped:202 overruns:0 frame:0
          TX packets:2462 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6777868 (6.4 MB)  TX bytes:389611 (380.4 KB)
          Interrupt:17 Base address:0xc000 Memory:f4000000-f4000fff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

tun0      Link encap:UNSPEC  HWaddr 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00  
          inet addr:10.8.0.6  P-t-P:10.8.0.5  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:39 errors:0 dropped:0 overruns:0 frame:0
          TX packets:107 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:11153 (10.8 KB)  TX bytes:7804 (7.6 KB)
```

The ping for the router is already above (timeout)
ping (external): 
```
PING ubuntuforums.org (91.189.94.186) 56(84) bytes of data.
64 bytes from ohiggins.canonical.com (91.189.94.186): icmp_seq=1 ttl=50 time=23.4 ms
64 bytes from ohiggins.canonical.com (91.189.94.186): icmp_seq=2 ttl=50 time=21.8 ms
64 bytes from ohiggins.canonical.com (91.189.94.186): icmp_seq=3 ttl=50 time=23.5 ms
64 bytes from ohiggins.canonical.com (91.189.94.186): icmp_seq=4 ttl=50 time=22.7 ms
64 bytes from ohiggins.canonical.com (91.189.94.186): icmp_seq=5 ttl=50 time=24.6 ms
64 bytes from ohiggins.canonical.com (91.189.94.186): icmp_seq=6 ttl=50 time=22.3 ms

--- ubuntuforums.org ping statistics ---
6 packets transmitted, 6 received, 0% packet loss, time 25476ms
rtt min/avg/max/mdev = 21.893/23.114/24.684/0.909 ms

```

Does this tell you something?

---

### Post by superprash2003 on 2008-03-31
you are able to ping.. but not able to access the internet.. try this.. go to system->administration->Network->DNS tab and click on add and type 208.67.222.222 and then check if internet works

---

### Post by mlentink on 2008-03-31
I am sorry, I must not have expressed myself clearly.  
Internally, as you will see in my first post, I can ping nothing but my ubuntu server, which is on I192.168.123.3. Externally, I can ping and see this forum.

---

### Post by linuxwarz on 2008-03-31
I do not know your network setup, but back when I made a router on ubuntu, the policy for iptables was to drop all traffic to the router unless it knew your MAC address. Even with this policy in place, unknown computers still got DHCP.

So could something like this be happening to you? Could have some ACL blocks if you can get DHCP but cant ping.

---

### Post by lavinog on 2008-03-31
from your first post:
> ip length 331 disagrees with bytes received 534.
accepting packet with data after udp payload.

does this mean anything?

---

### Post by superprash2003 on 2008-03-31
are the ips of the other computers of the form 192.168.123.x ??also ae they on the same subnet?

---

### Post by mlentink on 2008-04-01
> **lavinog said:**
> from your first post:


does this mean anything?

Could very well be. I'm checking out a thread on this on the Debian forum at the moment, but so far without results.

---

### Post by mlentink on 2008-04-01
> **superprash2003 said:**
> are the ips of the other computers of the form 192.168.123.x ??also ae they on the same subnet?


Yes, they are. The LaCie NAS-box, My Ubuntu server, two printservers and obviously the NetGear router are all on fixed adresses, the user computers, including the Compaq nx7400 notebook this is about, are all given dhcp adresses in the 192.168.123.100 - 192.168.123.200 range. Without any problems. Even for this notebook, up until about a week ago.

I really appreciate your help so far.

---

### Post by superprash2003 on 2008-04-02
you are not able to ping the router which is giving you internet and an ip..strange.. i think we are missing something.. you said all are getting ip addresses between 192.168.123.100-200  then what is 192.168.123.3??

---

### Post by mlentink on 2008-04-03
Just my sort of way of trying to organize things.
Servers get fixed adresses 0-100, workstations variable (dhcp) adresses 100-200 and appliances like print-servers and routers fixed adresses 200-254.

And I agree, this is really weird, but it turns out I'm not the only one. There was another forum participant  that had a similar thread, without it being answered. I've asked him if he ever solved it, but so far no answer. 

I followed a thread in the Debian forum (see earlier post) but it turned out not to be applicable.

I'm pretty sure it's not related to the specific machine, as it works flawlessly in XP.

I'll keep searching...

---

### Post by superprash2003 on 2008-04-03
please recheck the the subnet of all your pcs.. since some you have manually fixed and others you used dhcp, so there is high probability of the subnets being different..

---

### Post by mlentink on 2008-04-04
> **superprash2003 said:**
> please recheck the the subnet of all your pcs.. since some you have manually fixed and others you used dhcp, so there is high probability of the subnets being different..

Thanks!

I&#314;l go over them all. Be a while though. Hope you stick with me!

Martin

---

### Post by mlentink on 2008-04-12
I just checked: running the Ubuntu Hardy beta does not give me the same problem. So it must be something in some setup somewhere. 
But where?

---

### Post by h4mx0r on 2008-04-12
If you think that's weird, I have the exact same issue with an integrated ethernet card. To get it to work I have to disable ipv6 then shutdown and unplug the system, next boot it will work perfectly fine until I dual boot to windows.

---

### Post by mlentink on 2008-04-12
> **h4mx0r said:**
> If you think that's weird

Yeah. 
But there should be a reason to the madness. These are but computers, right?

---

### Post by mlentink on 2008-04-18
I'm marking this as solved, even though it isn't.

But since installation of the Hardy beta took away the problem (yes, I can now ping all other coomputers in the lan), and since very few people seemed to have an idea of the cause, it becomes moot.

---

