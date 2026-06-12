---
title: "SSH on eth1 while eth0 is up"
date: 2007-07-11
forum: Networking &amp; Wireless
---

### Post by altonbr on 2007-07-11
I used to be able to SSH on one network and than the other because one was 192.168.2.* and the other 192.168.1.* ... but now, I had my residential line router replaced (so now they're both Linksys) and both 192.168.1.* ...

So right now, my eth0 is 192.168.1.50 and my eth1 is 192.168.1.171. I need to travel along my eth1 network to 192.168.1.20, so how would I go about using my eth1 for this job?

I've used `sudo ifdown eth0 && sudo ifup eth1` (which I don't like to do because I have other services that need my residential line, not my business line) and it still can't seem to find my servers.

Is this making any sense?

---

### Post by netztier on 2007-07-11
> **altonbr said:**
> I used to be able to SSH on one network and than the other because one was 192.168.2.* and the other 192.168.1.* ... but now, I had my residential line router replaced (so now they're both Linksys) and both 192.168.1.* ...

So right now, my eth0 is 192.168.1.50 and my eth1 is 192.168.1.171. I need to travel along my eth1 network to 192.168.1.20, so how would I go about using my eth1 for this job?

I've used `sudo ifdown eth0 && sudo ifup eth1` (which I don't like to do because I have other services that need my residential line, not my business line) and it still can't seem to find my servers.

Is this making any sense?

Well, why don't you go and reconfigure one of the routers to use the 192.168.2.* network?
No big deal.. You can't have two interfaces in the same subnet - unless you take very special precautions against configuration conflicts.

best regards

Marc

---

### Post by altonbr on 2007-07-11
OK, good idea.

So I have one broadcast at 255.255.255.0 and the other at 255.255.255.128

> eth0      Link encap:Ethernet  HWaddr 00:12:3F:6C:35:83  
          inet addr:192.168.1.50  Bcast:192.168.1.255  Mask:255.255.255.128
          inet6 addr: fe80::212:3fff:fe6c:3583/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:17 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:522 (522.0 b)  TX bytes:1870 (1.8 KB)
          Interrupt:17 

eth1      Link encap:Ethernet  HWaddr 00:A0:C9:0F:85:21  
          inet addr:192.168.1.171  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

So how do I talk to the eth1 networking using ssh now?

I still get the same error:
> user@hostname:~$ ssh 192.168.1.20
ssh: connect to host 192.168.1.20 port 22: No route to host

---

### Post by netztier on 2007-07-12
> **altonbr said:**
> OK, good idea.

So I have one broadcast at 255.255.255.0 and the other at 255.255.255.128



So how do I talk to the eth1 networking using ssh now?

I still get the same error:

No wonder - you got it quite wrong! From your box's point of view, both interfaces are still in the  the same same subnet - halfway, at least.

You need to change the Subnet mask to 255.255.255.128 if you want to finish what you've started. You are trying to subnet your 192.168.1.0 /24 into two /25 networks with 128 addresses each. This is done with the subnet mask, not with the broadcast statement!

Configure one network (and that includes ALL devices participating on that LAN, including Routers!) with these parameters:
[INDENT]
IP address:        192.168.1.x (where 1 <= x >=126)
Subnet Mask:     255.255.255.128 
brodcast addr:   192.168.1.127  (where configurable)[/INDENT]

and the other (again, all NICs in that network, including Router LAN interfaces)
[INDENT]
IP address:         192.168.1.x (where 129 <= x >=254)
Subnet Mask:      255.255.255.128
Broadcast Addr: 192.168.1.255  (where configurable)[/INDENT]

And then you have the trouble that on a Computer with two simultaneously active NICs, you can only have one default gateway. So only **one** of your NICs can take a "gateway 192.168.1.x" statement in /etc/network/interfaces - make sure that it's the one that connects to a router that has internet access.

PS: multiple Interfaces on a box is asking for trou^H^H^H^H ... advanced configuration. What is it that you actually want to achieve, and how does your network look like? Can you elaborate?

best regards

Marc

---

### Post by altonbr on 2007-07-12
Thanks for explaining that Marc; I'll give it a try and report back.

My network consists of two lines; One residential, the other commercial.

The commercial line is running 1 server, which itself is running 3 virtual machines.

The residential line is running my computer and other family members laptops and what not. So you can see that I've set up (or in the process of setting up) a home business.

I was hoping to control everything from my desktop - I would do my web development on this machine and then be able to send the files across the LAN to the server. This would save time and bandwidth. I currently download all sorts of Linux ISOs and what have you via Deluge Torrent, so I don't want my bandwidth taken up on my commercial line (which is reserved for websites).

So my commercial line on my desktop is eth1 and my residential is eth0 (primary). I was hoping that I would be able to have one computer run on two networks - as a gateway. And as I said, I was able to do so when the residential router was on a 192.168.2.* network.

Make sense, or do you want more of a technical background?

Thanks again Marc.

---

### Post by netztier on 2007-07-12
> **altonbr said:**
> 
My network consists of two lines; One residential, the other commercial.

The commercial line is running 1 server, which itself is running 3 virtual machines.

The residential line is running my computer and other family members laptops and what not. So you can see that I've set up (or in the process of setting up) a home business.


Now that's a quite sound idea to keep separate things separate.

> So my commercial line on my desktop is eth1 and my residential is eth0 (primary). I was hoping that I would be able to have one computer run on two networks - as a gateway. And as I said, I was able to do so when the residential router was on a 192.168.2.* network.


Okay, I get it now.

If you want a host (i.e. your desktop) to have each an interface in both networks, you must make sure that these networks are "distinct" in the IP sense: The network numbers must be different and the address ranges must not overlap.

With the old router, this condition was met:

```
commercial  network: 192.168.1.0 (255.255.255.0)
residential network: 192.168.2.0 (255.255.255.0)
```

With these, your two-interface desktop had each an interface in different networks, and they were separate, that's why it worked.

Now as I said in the other post, per network, all devices must use the same network address (that's the "first" or "zero" address in your network), and the same subnet mask. 
In general, you can't configure the network address - it's implicitey calculated from the IP address and the subnet mask.

Sticking with 255.255.255.0 as subnet mask (can also be written as " /24") is a good idea. It makes discerning the network addresses easy: you just have to modify the third octet of the IP address, like in the above example or in this list:

```

**network address     subnet mask         IP addresses        local broadcast addr.**
192.168.**0**.0    /24  255.255.255.0       from .1 to .254     192.168.0.255
192.168.**1**.0    /24  255.255.255.0       from .1 to .254     192.168.1.255
192.168.**2**.0    /24  255.255.255.0       from .1 to .254     192.168.2.255
192.168.**3**.0    /24  255.255.255.0       from .1 to .254     192.168.3.255
...

```

Now if you wanted to go "advanced", you could sub-divide any of these. For instance let's cut one in half, with another (said "longer") subnet mask:

```
**network address     subnet mask         IP addresses        local broadcast addr.**
192.168.0.0    /25  (255.255.255.128)	from .1 to .126     192.168.0.127
192.168.0.128  /25  (255.255.255.128)   from .129 to .254   192.168.0.255

```

Or another one into four subnets, for example:

```
**Network address     subnet mask         IP addresses        local broadcast addr.**
192.168.1.0    /26  (255.255.255.192)	from .1 to .62      192.168.1.63
192.168.1.64   /26  (255.255.255.192)   from .65 to .126    192.168.1.127
192.168.1.128  /26  (255.255.255.192)   from .129 to .190   192.168.1.191
192.168.1.192  /26  (255.255.255.192)   from .193 to .254   192.168.1.255
```

so.. where does this lead us to?
[COLOR="Red"]**You will have to reconfigure one of the routers - there's no way around this.**[/COLOR]

I suggest you pick network addresses as you had them before:

```
commercial  192.168.1.0 (255.255.255.0)
residential 192.168.2.0 (255.255.255.0)

```

So you'll have to login to the new residential router and reconfigure it:

```
LAN IP address:  192.168.2.1
Subnet Mask:     255.255.255.0
DHCP Range:      192.168.2.100 - 192.168.2.150

```


Then you configure the two-Interface machine like follows::

```

**/etc/network/interfaces:**

# eth1 connecting to the commercial LAN
# note, **no** gateway statement!
auto eth1
iface eth1 inet static
address 192.168.1.20     [SIZE="1"](note: an IP address *outside* the commercial router's DHCP range!)[/SIZE]
netmask 255.255.255.0

# eth0 connecting to the residential LAN
# learns default gateway address from DHCP
auto eth0
iface eth0 inet dhcp
```

Note: if both routers are running DHCP servers (which they probably are), don't use dhcp on both interfaces. Since both routers are going to advertise themselves as default gateways, it's very probably going to generate conflicts in the routing table and mess up the DNS configuration in **/etc/resolv.conf**.

With DHCP on one interface and static configuration on the other, you should end up with a routing table somewhat like this:

```
marc@cube:~$ **netstat -nr**
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
192.168.1.0     0.0.0.0         255.255.255.0   U         0 0          0 eth1
192.168.2.0     0.0.0.0         255.255.255.0   U         0 0          0 eth0
0.0.0.0         192.168.2.1     0.0.0.0         UG        0 0          0 eth0

```

This tells us that 192.168.2.0 /24 (the residential LAN) is reachable via eth0, and that 192.168.1.0 /24 (the commercial LAN) is through eth1.  Furthermore, anything else (0.0.0.0 /0) can be reached via the *default gateway* at 192.168.2.1. This entry is also called the *default route*. A routing table should only contain one default route entry - only one is going to be effective, anyhow.

Your **server** in the commercial LAN probably has a configuration like this - if configured with a static IP address.

```
# eth0 connecting to the commercial LAN
auto eth0
iface eth0 inet static
address 192.168.1.25    [SIZE="1"](note: an IP address *outside* the commercial router's DHCP range!)[/SIZE]
netmask 255.255.255.0
gateway 192.168.1.1

```

.25 is just a suggestion - pick any from the range. The routing table should look something like this:

```
**netstat -nr**
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
192.168.1.0     0.0.0.0         255.255.255.0   U         0 0          0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG        0 0          0 eth0

```

Note: as default gateway, the server uses the IP address of the router on the commercial LAN! You may of course also let the DHCP service in the commercial router dole out IP address, subnet mask, default gateway and DNS information to the server - thats up to you. I suggest you configure it manually, though.

I hope that this was clear enough and that I got all network numbers and interface names right. If not, just ask back!

best regards

Marc

---

