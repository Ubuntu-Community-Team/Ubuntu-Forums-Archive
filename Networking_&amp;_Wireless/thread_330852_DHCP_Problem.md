---
title: "DHCP Problem"
date: 2007-01-03
forum: Networking &amp; Wireless
---

### Post by CitizenInsane on 2007-01-03
Hi All

I'm having a strange DHCP problem, hopefully someone can give me some pointers. 

My ISP is a bit strange (it's HomeChoice in the UK).  They do digital TV and Internet over ADSL.  They provide a set top box that also the internet router.  They don't officially support Linux but I've managed to get Dapper Drake working with it.  It pulls down an IP (which is controlled by HomeChoice and I cannot change) via DHCP no probs and everything works...at least for a while.

The thing is that the lease on the IP is only for 20-30 minutes - which is strange in itself but, ok, it shouldn't cause a problem.  Anyway...so every 30 minutes the DHCP client renews the lease and things carry on. 

The problem is that sometimes (and it's when ever I am using the internet heavily) it just drops out.  What seems to be happening is that HomeChoice seem to be dynamically reconfiguring the address router (I think they are actually switching it to another subnet).  What triggers this change seems to be something to do with amount I'm downloading, or perhaps the bandwidth I'm using I don't know, but if I'm actively using my connection sooner or later it will switch.  

If I restart the network interface in Ubuntu I can see the DHCPREQUEST to the DHCP server's last known address.  That fails because the router's address has changed. Next I see the DHCPDISCOVER broadcasts where it's trying to find the DHCP server's new address.  At this point the router should respond with an DHCPOFFER but it doesn't, it ignores the DHCPDISCOVERs until eventually the DHCP client gives up and goes to sleep.

Now this sounds immediately like a problem with the HomeChoice box (its ignoring DHCPDISCOVER broadcasts after it's switched to a new subnet), but the thing is if I actually reboot the linux box (rather that just restarting networking) then the HomeChoice box does respond to the DHCPDISCOVER and offer an IP on the new subnet.  So if the problem is with the HomeChoice box why would doing a full reboot of Ubuntu seem to work, while just restarting the interface doesn't?

Does HomeChoice's apparent policy of reconfiguring their router on the fly (seemingly on a whim) seem like valid neworking strategy because it seems very strange to me?  Should Ubuntu be able to cope with such a dynamic DHCP service?  Would Windows or MacOS handle it any different?

I could try HomeChoice support but I'm pretty sure i'll get the usual "we don't support Linux" response, so any help is appreciated before I switch to Windows to see if it fares any better.

Thanks

CitizenInsane

---

### Post by koenn on 2007-01-03
could you run ```
dhclient
``` in a terminal, 
- once while you're still connected 
- once after you're router has dropped you and refuses to give a new lease

and post the output here. 
It could have something to do that your computer already has an ip address and thinks it still has a valid lease or so. I'd like to see what exactly the router and your pc are telling eachother

(but i'll probably won't look at it until tomorrow - it's late here)

---

### Post by CitizenInsane on 2007-01-06
Hi koenn

Thanks for your response. Here is the dhclient output while it is working

```

citizenInsane@Rosebud:~$ sudo dhclient eth1
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

Listening on LPF/eth1/00:20:78:04:70:ee
Sending on   LPF/eth1/00:20:78:04:70:ee
Sending on   Socket/fallback
DHCPREQUEST on eth1 to 255.255.255.255 port 67
DHCPREQUEST on eth1 to 255.255.255.255 port 67
DHCPACK from 81.1.110.1
bound to 81.1.110.186 -- renewal in 1454 seconds.

```

and it is after it's dropped

```

citizenInsane@Rosebud:~$ sudo dhclient eth1
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

Listening on LPF/eth1/00:20:78:04:70:ee
Sending on LPF/eth1/00:20:78:04:70:ee
Sending on Socket/fallback
DHCPREQUEST on eth1 to 255.255.255.255 on port 67
DHCPREQUEST on eth1 to 255.255.255.255 on port 67
DHCPDISCOVER on eth1 to 255.255.255.255 on port 67 interval 7
DHCPDISCOVER on eth1 to 255.255.255.255 on port 67 interval 15
DHCPDISCOVER on eth1 to 255.255.255.255 on port 67 interval 20
DHCPDISCOVER on eth1 to 255.255.255.255 on port 67 interval 19
No DHCPOFFERS received.
Trying recorded lease 81.1.110.186
PING 81.1.110.1 (81.1.110.1) 56(84) bytes of data.

--- 81.1.110.1 ping statistics ---
1 packets transmitted, 0 received, +1 errors, 100% packet loss, time 0ms

No working leases in persistent database - sleeping.

```

and here it is after the machine is rebooted

```

citizenInsane@Rosebud:~$ sudo dhclient eth1
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

Listening on LPF/eth1/00:20:78:04:70:ee
Sending on   LPF/eth1/00:20:78:04:70:ee
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4
DHCPOFFER from 81.1.98.1
DHCPREQUEST on eth1 to 255.255.255.255 port 67
DHCPACK from 81.1.98.1
bound to 81.1.98.141 -- renewal in 1512 seconds.


```

Thanks for you help

CitizenInsane

---

### Post by Soarer on 2007-01-06
20 minutes is a really dumb time to lease an IP address. I can't see any reason for it, unless they simply don't have enough.

In my experience, Windows copes better with this. What seems to happen (I'm only guessing) is that Ubuntu actually requests another IP address on the same subnet, under the reasonable assumption that this is where it got the last one. Only if the lease is cleared (e.g. after reboot) will it actually request on 255.255.255.255 (which is what it reports it is doing).

I have looked on their website, but there is no information. They say there is a support site for customers, maybe you could try that. What you need to do is to set the router to do DNS translation - it should be able to do this. Then the router gets its IP from Homechoice, but always gives you an IP on an internal subnet (10.0.0.1 or 192.168.1 or something). 

Do you know if this is possible? Its a basic security feature on every router I've seen (though I haven't seen yours :))

---

### Post by koenn on 2007-01-06
it *is* rather unorthodox. 

If I read your posts correctly, they purposely change the network addresses to kill your connection when you're using it "too heavily", because at "normal" use, the dhcp lease just gets renewed as it is expected to be, correct ? 

you say
> If I restart the network interface in Ubuntu I can see the DHCPREQUEST to the DHCP server's last known address. That fails because the router's address has changed. Next I see the DHCPDISCOVER broadcasts where it's trying to find the DHCP server's new address.
could you show me that output ? 

could you also tell me the network mask (or just the complete output of ifconfig eth1) ?
btw, do you also have an eth0 ?

anyway, the behaviour of your computer is as described in the dhcp protocol so it should work, except that the dhcp server on your router refuses to acknowledge DHCPDISCOVER unless your computer has rebooted. I do not understand how it would do that - it can refuse DHCPREQUESTS if the request is for renbewal of an invalid address, but it shouldn't refuse DHCDISCOVER. 

you might be able to trick it (the next time they cut you of) by having your computer release its lease, so it will DISCOVER and REQUEST without any knowledge of previous leases - that could be close enough to the situation after a reboot. 
(with sudo or in a root terminal : )
```

dhclient -r
dhclient

```
if it works, you might make this a desktop launcher or something in a panel

---
> What you need to do is to set the router to do DNS translation - it should be able to do this. Then the router gets its IP from Homechoice, but always gives you an IP on an internal subnet (10.0.0.1 or 192.168.1 or something).
you probably mean NAT (Network Address Translation) - it might work, but from the sound of it, that router is probably not accessibe for maintenance by the customer, and might even not be able to do NAT.

---

### Post by Soarer on 2007-01-06
> **koenn said:**
> 
you probably mean NAT (Network Address Translation) 

Yes I do - thanks. Funny how I can always remember the word 'aphasia' :)

---

### Post by CitizenInsane on 2007-01-06
Thanks for you posts.

Yes.  It's strange.  I can only guessing at why they have such a weird arrangement and feel the need to switch subnets so often.  I don't they they are trying to intentionally kill the connection if I'm using it too much, because a) they have a fair use "limit" on the amount I'm allowed to download and I'm not coming anywhere near it, and b) just surfing web pages is enough to cause it to switch - not even downloading files or playing games.  Just pulling down web pages is hardly maxing out the connection.  

May be it is the fact that I am using the connection at all, ie if any connections are open when the router switches it screws something up.  Who knows.

As for the NAT - I can't access to the set top box / router so there is nothing I can do change the way it is working.

Here is the IFCONFIG
```

eth1      Link encap:Ethernet  HWaddr 00:20:78:04:70:EE
          inet addr:81.1.98.141  Bcast:81.1.98.255  Mask:255.255.255.0
          inet6 addr: fe80::220:78ff:fe04:70ee/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:77858 errors:237 dropped:0 overruns:0 frame:239
          TX packets:82565 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:44348978 (42.2 MiB)  TX bytes:33724024 (32.1 MiB)
          Interrupt:5 Base address:0xe000

```

I do also have an eth0.

You are right Soarer, HomeChoice have no technical info what so ever on their web site (and they don't have a customer support site).  Because they also do on demand TV and movies that are pretty secretive about how the whole thing works.

Thanks for your suggestions.  I'll try the dhcp -r trick you mentioned, but if not I'll install Windows and see if that is any better.

Thanks again.

 CitizenInsane

---

