---
title: "Help adding second NIC to 20.04 system for isolated cameras"
date: 2022-10-21
forum: Networking &amp; Wireless
---

### Post by JimLS on 2022-10-21
Have zoneminder on a Ubuntu 20.04 machine and have several IP cams with blocked internet access on my home network but wanting to put them on their own isolated network.  Have looked around some but need a dummies guide.  :)  I have installed a second NIC in the PC and it is recognized but not sure where to go from here.  Plan is to have a router on the isolated network with a different wifi id for wireless cam and to provide dhcp based on MAC.  Seems like that would be convenient to add cams and also when plugging in a PC to configure cams, etc (although I suppose that could be done from the zoneminder box having a laptop at the camera location would be useful for setup).  I could make the zoneminder second port have fixed IP or get it from dhcp - seems like a toss up which might be easier/better.

---

### Post by TheFu on 2022-10-21
This shouldn't be hard.  It is about controlling the routing table for each interface so traffic to specific subnets traverse on the correct NIC.  In theory, you won't need a router, just a normal $15 ethernet switch. I'm assuming 100% wired ethernet.  Wifi brings all sorts of added security complexities that are best avoided.  Of course, you could use an old wifi router on the 2nd LAN.  Just don't use the WAN port and connect all the ethernet cables to the built-in switch ports on that device.

You'll need to post exact IPs, exact routing tables, to get better help.  Or you can learn small-network networking in 2-3 online classes which will be very helpful.  Just know that subnets are how traffic knows where to go, so each LAN needs to be on a different subnet.  It is best if both LANs are non-standard for a number of reasons.  Since you'll be changing all the IPs anyway, it would be good to get all of them onto some odd subnets, not just the IP cameras, but all the devices.

Say use 10.202.80.1/24 and 10.101.90.1/24. Those are unlikely to be used many other places.

---

### Post by JimLS on 2022-10-22
Thanks for the reply but I was hoping for more specific details.  I will be using a router because I have one wifi camera but that's a detail I can deal with. 

You say I could learn small networking in a few classes.  Got any specific ones to suggest?  Free is preferred of course...

Exact IPs?  Ok, Say I have my current network as 192.168.10.x and want to set up my second one as 192.168.100.x.  Routing tables?  Haven't messed with those so don't know what you want...  

Seems like there should be some examples of how to do this without needing my exact IPs as I can easily translate any examples to other IPs.  But I haven't found any I could follow.

---

### Post by JimLS on 2022-10-22
Found this.  Looks to be exactly what I was looking for.  It's an older version of ubuntu but close enough I think to be able to follow on a more current os...
[http://www.ijohnsen.com/blog/zoneminder-install/](http://www.ijohnsen.com/blog/zoneminder-install/)

---

### Post by TheFu on 2022-10-22
I cannot recommend any classes or tutorials, since my knowledge was acquired in the 1990s and expanded in the very early 2000s.

14.04 network commands and configuration is nothing like 20.04.  20.04 uses netplan config files and all prior releases use ifupdown (/etc/networking/interfaces).  ifupdown has been deprecated and unsupported for a long time.  

Use netplan.io ... that's the website.  YAML config files are indentation sensitive. Even 1 space off and the config won't parse.
I do like the diagram in the link, though I didn't study it in detail.

> Exact IPs? Ok, Say I have my current network as 192.168.10.x and want to set up my second one as 192.168.100.x. Routing tables? Haven't messed with those so don't know what you want... 

First, I'd suggest you choose /24 networks to make the network math and configuration trivial.  /24 means a netmask of 255.255.255.0. It is a 1-for-1 translation.  So 192.168.10.x/24 tells us much about that network.  Similarly, 192.168.100.x/24 tells us much about that network.  

[https://en.wikipedia.org/wiki/Routing_table](https://en.wikipedia.org/wiki/Routing_table)  From a high level, the routing table is how a computer's network stack knows to send packets for 192.168.100.x out on eth11 instead of setting those packets on eth0.  If there isn't a routing table, the packets could be sent to  the default gateway and never arrive anywhere, certainly not where you want.  That wikipedia link has an example routing table.  Hopefully, your netplan config  with the 2 different IPs and subnets will be sufficient to get the routing table entries needed.  Check that with the 'ip route' command.

---

### Post by JimLS on 2022-12-01
Yes, /24 network is what I had in mind. Trying to follow some info I found on doing this...

I will have a router on both networks.  The one with internet connection as it has been.  And one on the camera network because some cameras are wifi only.  Since I have a router it seems easy to have it be a DHCP server based on MAC addresses (that's what I have on my main network).  But we can just do DHCP for starters and worry about specific addresses later.

So I am guessing my netplan file would be something like this?

```
Added file: /etc/netplan/02-network-dual-nic.yaml

network:
    version: 2
    renderer: NetworkManager
    ethernets:
        eno1:
            dhcp4: true
            dhcp6: no
        enp2s0:
            dhcp4: true
            dhcp6: no

```
I did:  sudo netplan --debug apply
and got this:
```

** (generate:279758): DEBUG: 21:13:32.157: Processing input file /etc/netplan/01-network-manager-all.yaml..
** (generate:279758): DEBUG: 21:13:32.157: starting new processing pass
** (generate:279758): DEBUG: 21:13:32.157: Processing input file /etc/netplan/02-network-dual-nic.yaml..
** (generate:279758): DEBUG: 21:13:32.157: starting new processing pass
** (generate:279758): DEBUG: 21:13:32.157: We have some netdefs, pass them through a final round of validation
** (generate:279758): DEBUG: 21:13:32.157: enp2s0: setting default backend to 2
** (generate:279758): DEBUG: 21:13:32.157: Configuration is valid
** (generate:279758): DEBUG: 21:13:32.157: eno1: setting default backend to 2
** (generate:279758): DEBUG: 21:13:32.157: Configuration is valid
** (generate:279758): DEBUG: 21:13:32.157: Generating output files..
** (generate:279758): DEBUG: 21:13:32.157: networkd: definition eno1 is not for us (backend 2)
** (generate:279758): DEBUG: 21:13:32.157: openvswitch: definition eno1 is not for us (backend 2)
** (generate:279758): DEBUG: 21:13:32.157: networkd: definition enp2s0 is not for us (backend 2)
** (generate:279758): DEBUG: 21:13:32.157: openvswitch: definition enp2s0 is not for us (backend 2)
(generate:279758): GLib-DEBUG: 21:13:32.158: posix_spawn avoided (fd close requested)
(generate:279758): GLib-DEBUG: 21:13:32.158: posix_spawn avoided (fd close requested)
DEBUG:no netplan generated networkd configuration exists
DEBUG:netplan generated NM configuration changed, restarting NM
DEBUG:eno1 not found in {}
DEBUG:enp2s0 not found in {'eno1': {'dhcp4': True, 'dhcp6': False}}
DEBUG:Merged config:
network:
  ethernets:
    eno1:
      dhcp4: true
      dhcp6: false
    enp2s0:
      dhcp4: true
      dhcp6: false
  renderer: NetworkManager
  version: 2

DEBUG:Link changes: {}
DEBUG:netplan triggering .link rules for lo
DEBUG:netplan triggering .link rules for enp2s0
DEBUG:netplan triggering .link rules for eno1
DEBUG:eno1 not found in {}
DEBUG:enp2s0 not found in {'eno1': {'dhcp4': True, 'dhcp6': False}}
DEBUG:Merged config:
network:
  ethernets:
    eno1:
      dhcp4: true
      dhcp6: false
    enp2s0:
      dhcp4: true
      dhcp6: false
  renderer: NetworkManager
  version: 2

jim@ZM-Myth:/
```

I have the DHCP router connected to the second port and the port does not get an address set.

---

### Post by JimLS on 2022-12-02
There was a problem with the router DHCP.  Once that was fixed the PC  got the expected IP addresses on both ports.  Now I am wondering if I  needed to do anything to get to this point as DHCP on both ports may be  default behavior.

---

