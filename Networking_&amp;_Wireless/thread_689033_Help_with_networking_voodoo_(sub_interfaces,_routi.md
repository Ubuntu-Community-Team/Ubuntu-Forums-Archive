---
title: "Help with networking voodoo (sub interfaces, routing, NAT, etc...)"
date: 2008-02-06
forum: Networking &amp; Wireless
---

### Post by theCSapprentice on 2008-02-06
Ok, here's what I've got:

----> Ubuntu Desktop ( 1 NIC )
----> Ubuntu Laptop ( 1 NIC )
----> 4-port hub
----> Very restrictive university network ( allows only 1 IP for the port in my dorm )

Here's what I want to do:

I need the desktop to connect with DHCP to the university network. I have no choice in this. However, I would also like to connect my laptop to the network at the same time. So, my thought was to use my desktop as a router/NAT combo and put my laptop behind it. So far so good, except that I only have one interface on the desktop. After some research I have determined that my best choice would be create a sub interface on the desktop, assign it a separate subnet, and place my laptop on it (It would be nice to do this with DHCP, but I'll take what I can get).

So I have a fairly good idea what I want to do, but I'm not sure what commands I need to put it all together. Somehow I need to route(with NAT) a sub interface to a main interface, which does not have the luxury of keeping a static IP.  

Any advice on the problem would be great. ( And no, adding another NIC is not possible in this case. :( )

---

### Post by Dark Hornet on 2008-02-06
I am not sure that would be your easiest solution....off the top of my head, I would just go buy a cheap router/4 port switch, and connect that to your dorm connection.  Your school will still assign you a DHCP address to the router, then you will just hook both of your computers to the router/4 port switch, and run NAT from your router.  Most of them will do this automatically, and have very easy GUI interfaces.  Good Luck!

---

### Post by theCSapprentice on 2008-02-06
Yeah, I could....

In truth, I've already considered this option, and I would rather not spend the extra money if possible. Buying new hardware is sort of my last resort.

---

### Post by netztier on 2008-02-06
> **theCSapprentice said:**
> Yeah, I could....

In truth, I've already considered this option, and I would rather not spend the extra money if possible. Buying new hardware is sort of my last resort.

You won't be able to get around some machine acting as a router. You could add a second NIC to the Ubuntu box and use this second NIC as "external" interface towards the campus network, while you use the other NIC as "internal" to connect your Laptop or hub.

... Ok now here's the re-edit: 

I also suggest: get a general purpose wireless broadband router like the Linksys WRT54G - and if you like to learn about linux networking, take a WRT54GL version - it runs Linux and can be equipped with alternative firmwares such as DD-WRT and the likes.
And it saves you from having to let the desktop run whenever you want to access the (Inter)Net from your laptop.



Now.. 

It might be possible to work with routing and NAT as well, even if your Ubuntu desktop only has a single LAN interface. 

However, I can't see a way of doing this without a major drawback: your internal network must have static IP addressing. 

At first: ditch network-manager. It will probably interfere with anything you'd like to configure on the desktop. Then, figure out which IP subnet your campus network is assigning IP addresses from. For the sake of the example, let's assume that your campus network subnet is 10.100.100.0  (netmask 255.255.255.0).

Then, choose a different IP subnet for your own "internal" network, let's take 192.168.100.0 (netmask 255.255.255.0). Configure eth0 for dhcp and create a subinterface on it. Note that there is *no* gateway statement for eth0:192

```
auto eth0
 ifache eth0 inet dhcp

auto eth0:192
iface eth0:192 inet static
 address 192.168.100.1
 netmask 255.255.255.0

```

Now on the Laptop, configure this (assuming that it's eth0)

```

auto eth0
iface eth0 inet static
 address 192.168.100.10
 netmask 255.255.255.0
 gateway 192.168.100.1

```

... you should be able to talk to your desktop PC on it's 192.168.100.1 address. 

The rest follows: configuring routing, network address translation, if needed proxy services etc on the ubuntu desktop, and you're almost there. You can follow one of the numerous guides on the forums and the web - just make sure you leave out the part with the DHCP server on your "internal" LAN, as it does not apply here.

However, this is not proper networking, this  setup is only a kludge, with running two subnets on the same LAN and using a router-on-a-stick to forward IP packets between the different subnets.

Possibly, your campus LAN admin might have been hard on you, and he configured MAC-address security on the individual switch ports, so that only ever one MAC-address may be active per port. In that case, the above solution won't work - there would be no way around a second NIC for the ubuntu desktop or - again - a separate LAN router.


best regards

Marc

---

### Post by sublimation on 2008-02-06
I'm on a University Campus as well, my solution has been to use a wireless router. I've got a [Netgear G Wireless]("http://www.radioshack.com/product/index.jsp?productId=2208567") (Currently on sale at Radio Shack) Which I've set up to use the MAC from my Desktop so the University Network accepts the router's connection. Since I don't expect the wireless router to travel much beyond dormroom cinderblock walls, I'm pretty confident that the cheapest wireless router would be probably your most convinient route.

For $40 you can get a router/wireless router, which will be useful to you after college. 
My suggestion is to spring for the wireless one, as it's basically a zero-config option for both your machines.

That said, you're going to need some method to allow one of your computers (or the switch) to connect to both the other computer and the internet. If you could access a wireless network with your laptop you could connect through that... other than that I can't think of any solution that will involve no new hardware. A new NIC would cost around $20, which is pretty much your cheapest option.

Hope this helps some!

---

### Post by theCSapprentice on 2008-02-06
I think I might have to go with the router option. I was just hoping for something simpler than what I have set up now. Currently I have a wireless dongle acting as an access point for the laptop, but the link is flaky and its a pain to fix it when it goes down. At least a router will save me unneeded stress...

Out of curiosity, why would the routing between sub interfaces cause a problem with MAC restrictions? Wouldn't the outside see only the MAC of my desktop and not the laptop?

---

### Post by netztier on 2008-02-06
> **theCSapprentice said:**
> 
Out of curiosity, why would the routing between sub interfaces cause a problem with MAC restrictions? Wouldn't the outside see only the MAC of my desktop and not the laptop?

The "outside" being the switch port of your campus LAN would *not* see your Laptop's MAC address, *if* these two LANs were separate broadcast domains.

Connecting the hub to your wall outlet and the desktop and laptop to that hub, brings all of them into the same broadcast domain - regardless of the fact that they all use different IP subnets. So if your laptop sends an ARP broadcast for 192.168.100.1 (which is the "inside" address on the ethernet subinterface on your desktop), this broadcast would also travel through the uplink to the campus LAN. 

The switch up there would see an incoming broadcast frame with the source MAC address of your laptop computer. Whatever action the admin did configure to happen in this moment, will then happen... I for one have one or two places in my networks where the appearance of an unexpected MAC address leads to an instant administrative shutdown of the port. (oh.. I didn't even want that connection - they made me put in such a "security measure"). 

In an environment like yours, as admin, I would enforce that every switch port can "learn" a single MAC address at a time. So either students can connect only a single PC at a time or they'll have to set up a NAT device to hide their own dorm network behind it. And looking at the things sloshing around in a campus network, I'd even strongly suggest to students to put in their own NAT router or a decent little firewall to protect their PCs from the others.

If you had two NICs in your desktop and used one for your "internal" network and one for the campus LAN, there'd be no such trouble; broadcast domains 'd be properly separated, your laptop could remain configured for DHCP (which is, frankly, the only reasonable mode to assign IP addresses), and with **firestarter** on the desktop, you can even have a GUI to configure NAT/Firewall/routing comfortably. A reasonably good 100Mbps NIC can be had for a handful of bucks definitely worth spending if your don't want to buy a router. 

The downside: you have to keep your desktop running if you want to access the (Inter)net from your laptop...

regards

Marc

---

