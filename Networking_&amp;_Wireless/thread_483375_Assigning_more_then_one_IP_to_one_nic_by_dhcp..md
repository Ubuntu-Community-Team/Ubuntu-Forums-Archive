---
title: "Assigning more then one IP to one nic by dhcp."
date: 2007-06-24
forum: Networking &amp; Wireless
---

### Post by azzid on 2007-06-24
Hi,

my isp tend to be kind enough to distribute up to 5 ip adresses. 
Now I would like for my firewall to collect 2 adresses so I could configure it in a fancy-pants way.

Anyhow, I figured it should only be to add a virtual interface in **/etc/network/interfaces**.
So, I added the line:
```
iface eth2:0 inet dhcp
```

But I am unable to bring up that interface. When I try I get the following error:
```
SIOCSIFFLAGS: Cannot assign requested address
SIOCSIFFLAGS: Cannot assign requested address
Bind socket to interface: No such device
Failed to bring up eth2:0.
```

Anyone out there who can explain this to me? Is there another way to collect two adresses from the dhpc and then assign them both to the same physical nic?

---

### Post by netztier on 2007-06-25
> **azzid said:**
> 
Anyone out there who can explain this to me? Is there another way to collect two adresses from the dhpc and then assign them both to the same physical nic?

I don't know all the exact details, but what I can give you some things to consider:

[LIST]
[*]Using a subinterface is the right way, IMHO.
[*]remember that having two interfaces (logical or physical)  on the same IP Subnet (assuming that your ISP serves all your DHCP requests from the same scope/range/subnet) is basically a "no go thing", unless you know exactly what you're about to do.
[*]be very careful with routing and which interface your default route is going to point out of - having the packets leave through the wrong interface (and therefore possibly using the 2nd IP address as source) may collide with *connection-state rules* on the firewall you're possibly going to run on that box.
[*] to avoid configuration collisions, you might have to tweak the DHCP client's configuration (see **/etc/dhcp3/dhclient.conf**) to request nothing but address and subnet mask for the second subinterface, especially no DNS servers and no default gateway information.
[*] If you want to obtain more than one address by DHCP, you *must* make each request with a different MAC address - that's how most DHCP server distinguish different clients. Check the "hwaddr nn:nn:nn:nn:nn:nn" statement for **/etc/network/interfaces** and put some fake MAC address in there for the subinterface. Increasing the last number of the current card by one might be good enough.
[/LIST]

That's some input I can give...

best regards

Marc

---

### Post by azzid on 2007-06-25
Thanks! Really good answer, but I must be doing something wrong still.

I'm not even able to change the hwaddr of the virtual interface. I can change the mac adress of **eth2** just as I please, but I can't even get **eth2:0** to show up when I do *ifconfig -a*

---

### Post by netztier on 2007-06-25
> **azzid said:**
> Thanks! Really good answer, but I must be doing something wrong still.

I'm not even able to change the hwaddr of the virtual interface. I can change the mac adress of **eth2** just as I please, but I can't even get **eth2:0** to show up when I do *ifconfig -a*

Can we see that part of **/etc/network/interfaces**, please? You wouldn't have forgotten the **auto eth2:0 ** line, would you?

I have spotted the "alias" section in /etc/dhcp3/dhclient.conf - but I haven't yet figured out how to make use of it - but the solution might actually be there.

best regards

Marc

---

### Post by azzid on 2007-06-25
**/etc/network/interfaces**
```

auto lo eth2 eth2:0 eth1 eth0
iface lo inet loopback

iface eth2 inet dhcp
        hwaddress ether 00:30:04:20:7A:07

iface eth2:0 inet dhcp
        hwaddress ether 00:30:04:20:7A:08

iface eth1 inet static
        address 192.168.1.1
        netmask 255.255.255.0
        broadcast 192.168.1.255
        network 192.168.1.0

iface eth0 inet static
        address 10.0.1.1
        netmask 255.255.255.0
        broadcast 10.0.1.255
        network 10.0.1.0

```

**/etc/dhcp3/dhclient.conf**
```

request subnet-mask, broadcast-address, time-offset, routers,
        domain-name, domain-name-servers, host-name,
        netbios-name-servers, netbios-scope;
interface "eth2:0" {
                send dhcp-client-identifier 00:30:04:20:7A:08;
        }

```
**/etc/init.d/networking restart**
```

 * Reconfiguring network interfaces...	Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

Listening on LPF/eth2/00:30:04:20:7a:07
Sending on   LPF/eth2/00:30:04:20:7a:07
Sending on   Socket/fallback
DHCPRELEASE on eth2 to 172.22.249.166 port 67
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

Listening on LPF/eth2/00:30:04:20:7a:07
Sending on   LPF/eth2/00:30:04:20:7a:07
Sending on   Socket/fallback
DHCPDISCOVER on eth2 to 255.255.255.255 port 67 interval 7
DHCPOFFER from 85.227.147.130
DHCPREQUEST on eth2 to 255.255.255.255 port 67
DHCPACK from 85.227.147.130
bound to 85.227.147.215 -- renewal in 1768 seconds.
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

SIOCSIFFLAGS: Cannot assign requested address
SIOCSIFFLAGS: Cannot assign requested address
Bind socket to interface: No such device
Failed to bring up eth2:0.
										[ ok ]

```

That's about it I think, see anything weird?

---

### Post by netztier on 2007-07-03
> **azzid said:**
> **/etc/network/interfaces**

**/etc/dhcp3/dhclient.conf**
```

request subnet-mask, broadcast-address, time-offset, routers,
        domain-name, domain-name-servers, host-name,
        netbios-name-servers, netbios-scope;
interface "eth2:0" {
                send dhcp-client-identifier 00:30:04:20:7A:08;
        }

```
[

That's about it I think, see anything weird?

I'm not sure if that is a valid client identifier - on my DHCP server, Client IDs  - if they're sent by the client - mostly show up as 01:nn:nn:nn:nn:nn:nn, where nn:nn... is the actual MAC address. OTH - I've just skimmed through the DHCP RFC and it just says that the client identifier had to be unique within the Subnet - nothing more.

[http://osdir.com/ml/user-groups.linux.kansascity/2004-06/msg00083.html](http://osdir.com/ml/user-groups.linux.kansascity/2004-06/msg00083.html)

where it says:

```
You say you're running "dhclient", so I assume you mean the ISC DHCP
client.  Are you sure it won't grab multiple addresses?  According to
the dhclient.conf man page, you should be able to use something like:


   interface "eth0:1" {
       send dhcp-client-identifier "myhost-eth0:1";
   }


   interface "eth0:2" {
       send dhcp-client-identifier "myhost-eth0:2";
   }
```

Give it a try: define *two* subinterfaces with each a client-identifier of their own - and don't give an IP address to the "mother" interface at all.

best regards

Marc

---

