---
title: "IPv6 not configuring from /etc/network/interfaces on boot"
date: 2006-10-25
forum: Networking &amp; Wireless
---

### Post by Bytor on 2006-10-25
Hello all,

I'm having poblems gettign IPv6 to be properly configured when Ubuntu boots. I've only just started with Ubuntu, but I have been using OpenBSD for years so I'm not a un*x newbie. Let me describe my problem. I'm running Ubuntu 6.06LTS, BTW, with the 2.6.15-27-686 kernel on a dual P3-450 OC'ed to 506MHz with 640MB of RAM.

In /etc/entwork/interfaces I have the following:
```

[cory@fenris] 14:34:34 [3]~> cat /etc/network/interfaces
auto lo
iface lo inet loopback
iface lo inet6 loopback
auto eth0
iface eth0 inet static
        address 192.168.0.2
        netmask 255.255.255.0
        up route add default gw 192.168.0.1
        down route del default gw 192.168.0.1
iface eth0 inet6 static
        address 2001:5c0:92cf::c0a8:2
        netmask 64
        up route -A inet6 add default gw 2001:5c0:92cf::c0a8:1
        down route -A inet6 del default gw 2001:5c0:92cf::c0a8:1

```

But right after booting, my network config looks like this:

```

[cory@fenris] 14:35:13 [4]~> ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:0E:0C:B9:4D:ED
          inet addr:192.168.0.2  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: 2001:5c0:92cf:0:20e:cff:feb9:4ded/64 Scope:Global
          inet6 addr: fe80::20e:cff:feb9:4ded/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3623 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3404 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:559109 (546.0 KiB)  TX bytes:832420 (812.9 KiB)
          Base address:0xa800 Memory:e3800000-e3820000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:3151 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3151 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:287682 (280.9 KiB)  TX bytes:287682 (280.9 KiB)

sit0      Link encap:IPv6-in-IPv4
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

```

Notice that while eth0 has been given an IPv6 address, it is not the one I assigned in /etc/network/interfaces. Its actually the IPv6 stateless autoconfig address based upon the cards MAC address.

When I try to do an ifdown command, I get the following:

```

[cory@fenris] 14:35:49 [5]~> sudo ifdown eth0
Password:
ifdown: interface eth0 not configured

```

But then "sudo ifconfig eth0 down" works just fine. I then do a "sudo ifup eth0" and things are the way I set it to be in /etc/network/interfaces. Viz:

```

[cory@fenris] 14:36:45 [7]~> ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:0E:0C:B9:4D:ED
          inet addr:192.168.0.2  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: 2001:5c0:92cf:0:20e:cff:feb9:4ded/64 Scope:Global
          inet6 addr: fe80::20e:cff:feb9:4ded/64 Scope:Link
          inet6 addr: 2001:5c0:92cf::c0a8:2/64 Scope:Global
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3769 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3521 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:593414 (579.5 KiB)  TX bytes:851359 (831.4 KiB)
          Base address:0xa800 Memory:e3800000-e3820000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:5347 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5347 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:486087 (474.6 KiB)  TX bytes:486087 (474.6 KiB)

sit0      Link encap:IPv6-in-IPv4
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

```

I would assume hat because "ifup eth0" worked without errors that therefore /etc/network/interfaces is all good. But if so, then why is my IPv6 config not happening? The only thing I could find from dmesg that even remotely relates to networking were a few lines about eth0 being found on probe, seeting to 100Mb or 1000Mb speeds and watchdog timers. Similar lines were repeated in other files in /var/log, but, again, nothing else useful.

I would suspect that "sudo ifdown eth0" is symptom of the problem, but I am at a loss as to where to look. I just can't figure out why IPv6 is not configuring properly the way I want it.

I would really appreciate some help with this as I am finding it rather frustrating.

---

### Post by Paris Heng on 2007-09-11
Hi,

IF not configure from configuration file, what the way to configure?

Thanx

---

### Post by AlfonsName on 2008-02-22
See [http://www.melb.apana.org.au/wiki/IPv6ConfigurationForDebian](http://www.melb.apana.org.au/wiki/IPv6ConfigurationForDebian) as Ubuntu is a Debian derivate.
Looks like the ipv6 module was loaded before configuring ipv6.

---

### Post by netztier on 2008-02-22
> **Bytor said:**
> 
But right after booting, my network config looks like this:

```

[cory@fenris] 14:35:13 [4]~> ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:0E:0C:**B9:4D:ED**
          inet addr:192.168.0.2  Bcast:192.168.0.255  Mask:255.255.255.0
          [COLOR="Blue"]inet6 addr: 2001:5c0:92cf:0:20e:cff:fe**b9:4ded**/64 Scope:Global[/COLOR]
          inet6 addr: fe80::20e:cff:feb9:4ded/64 Scope:Link


```



Looks like you already have a global scope address; is there some router in your subnet sending out router-advertisments? That global scope address above has your NIC's MAC address encoded into it.

This leads to the suspicion that upon booting, your machine sends our a router solliciation message and gets a valid prefix advertisment from a router, does an EUI-64-conversion it's MAC address and thus already has an IPv6 address in the 2001:5c0:92cf:0000 /64 subnet.

Without being perfectly sure, I believe this might have to do with autoconfiguration or accepting router advertismets (this is from my homebuilt IPv6 router on a Sun Ultra 5)
```
marc@fire:**/proc/sys/net/ipv6/conf/eth0**$ more *       
[COLOR="Red"]::::::::::::::
accept_ra
::::::::::::::
1[/COLOR]
::::::::::::::
accept_ra_defrtr
::::::::::::::
1
::::::::::::::
accept_ra_pinfo
::::::::::::::
1
::::::::::::::
accept_redirects
::::::::::::::
1
::::::::::::::
accept_source_route
::::::::::::::
0
[COLOR="Red"]::::::::::::::
autoconf
::::::::::::::
1[/COLOR]
::::::::::::::
dad_transmits
::::::::::::::
1
::::::::::::::
force_mld_version
::::::::::::::
0
::::::::::::::
forwarding
::::::::::::::
1
::::::::::::::
hop_limit
::::::::::::::
64
::::::::::::::
max_addresses
::::::::::::::
16
::::::::::::::
max_desync_factor
::::::::::::::
600
::::::::::::::
mtu
::::::::::::::
1500
::::::::::::::
proxy_ndp
::::::::::::::
0
::::::::::::::
regen_max_retry
::::::::::::::
5
::::::::::::::
router_solicitation_delay
::::::::::::::
1
::::::::::::::
router_solicitation_interval
::::::::::::::
4
::::::::::::::
router_solicitations
::::::::::::::
3
::::::::::::::
temp_prefered_lft
::::::::::::::
86400
::::::::::::::
temp_valid_lft
::::::::::::::
604800
::::::::::::::
use_tempaddr
::::::::::::::
0
```

By setting the contents of the respective files to "1" or "0", you should be able to influence your IPv6 stack's behaviour. Be sure to read the documentation before fiddling with these, though.

best regards

Marc

---

### Post by Bytor on 2008-02-22
> **netztier said:**
> Looks like you already have a global scope address; is there some router in your subnet sending out router-advertisments? That global scope address above has your NIC's MAC address encoded into it.

This leads to the suspicion that upon booting, your machine sends our a router solliciation message and gets a valid prefix advertisment from a router, does an EUI-64-conversion it's MAC address and thus already has an IPv6 address in the 2001:5c0:92cf:0000 /64 subnet.


Oi! This was aaaaages ago, over a year. :-) I've since upgraded to 7.10 server.

Anyways, yes, I know that is the MAC in the assign IPv6 address. If you check my post, you'll see I knew that because I mentioned IPv6's stateless autoconfig. "Its actually the IPv6 stateless autoconfig address based upon the cards MAC address."

However, that should not affect assignment of a static address as NICs. I had ended up placing the following line sin /etc/rc.local /etc/rc.local:

```

ifconfig eth0 add 2001:5c0:92cf::c0a8:2/64
route -6 add default 2001:5c:92cf::c0a8:1

```

The result was the NIC had both the stateless autoconfig address and the static IPv6 address set on it. I still have to have those lines in rc.local even in 7.10.

```

root@xanadu:/etc/network# ifconfig eth0
eth0      Link encap:Ethernet  HWaddr 00:0E:0C:B9:4D:ED
          inet addr:192.168.0.2  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: 2001:5c0:92cf:0:20e:cff:feb9:4ded/64 Scope:Global
          inet6 addr: fe80::20e:cff:feb9:4ded/64 Scope:Link
          [COLOR="Red"]inet6 addr: 2001:5c0:92cf::c0a8:2/64 Scope:Global[/COLOR]
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:26864779 errors:65 dropped:0 overruns:0 frame:33
          TX packets:27902505 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:728746296 (694.9 MB)  TX bytes:2532697679 (2.3 GB)
          Base address:0xa800 Memory:de800000-de820000

```

 Thus, even if the settings in /etc/network/interfaces are done **after** the network subsystem has done stateless autoconfig my static address should still be applied since the interface can have more than one address. If the stuff in interfaces is done **before** stateless autoconfig, it should **not** get wiped out by stateless.


AlfonsName's link suggests that the ipv6 kernel module was not loaded at the time interfaces got parsed and to add "pre-up modprobe ipv6". If that is the case, on wonders what the network subsystem coders were smoking by allowing interfaces to be run through before all network-related kernel modules were loaded.

However, the machine is only rebooted when updates says so, it will be weeks before I test out whether adding that pre-up will work.

---

