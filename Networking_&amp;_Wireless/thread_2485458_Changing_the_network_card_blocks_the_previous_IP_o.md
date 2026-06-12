---
title: "Changing the network card blocks the previous IP on the local network"
date: 2023-03-30
forum: Networking &amp; Wireless
---

### Post by grzesiek811 on 2023-03-30
Hi,
I have a problem with the IP on the local network.
I've changed the motherboard and processor from Core i3 4130T to i3 7100. However, I keep SSD with the ubuntu system, because I did not want to configure everything again.
The problem is that I can't set the previous IP on the network. The computer's IP on the local network is 192.168.100.2. When I set it now, I do not have access to the Internet, the local network works. When I set a different IP or DHCP everything works, including the internet. When I put the disk back into the old computer, the requested IP works.

It's like the system blocked the IP for the previous computer and now I can't use it. Other IPs work. I could give different, but again I have some settings in the network and on the router, where I would have to change the IP. Unless it's somewhere on the router. I have a Huawei HG8245H router.

Can anyone help me find this issue?

---

### Post by TheFu on 2023-03-30
DHCP leases are tied to the MAC of the ethernet controller. When you changed the motherboard, if you were using the built-in ethernet controller, then your DHCP server did what it should and created a new IP for a completely different MAC.

To get help, we need to know a few things:
a) Which OS?
b) Which release of the OS?
c) Which tool(s) are you using to set the networking up?  I use netplan, but I suspect you do not.
d) Inside the router, there is a "DHCP range" set.  Any static IP must be outside that range, but on the same subnet.
e) Some/most routers support something called "DHCP Reservations", this is a way to have a MAC -to- IP DHCP answer.  Again, the IP for the static answer needs to be outside the "DHCP range".  That DHCP range is for dynamic devices ... think guests only.

So, say your local network is 192.168.100.0/24.  That provides 255 IP addresses. More than any home should need.  Heck, I use about 100 IPs, but I'm an extreme case.
Now, say your gateway/router is on 192.168.100.1 and you want all your other normal devices to be in a "static range" of .1 - .50, so you'd make the "DHCP Range" .100-.120.
Whenever you set a static IP, choose a unique IP in the 192.168.100.2 - 192.168.100.50 range. Never reuse it, unless the machine is gone from your network.  This range of IPs will also be used by all your "DHCP Reservations" - which is good for laptops, smartphones, and network devices that don't allow easy setting of a static IP.  For example, I have some HDHomerun network TV tuners that get their static IPs via DHCP reservations.  
Guest devices on your network (BTW, you shouldn't really allow **any** guests onto your subnet), will be assigned 192.168.100.100-.120.  Guests really should be on a different subnet. This applies to wifi devices too, BTW.  Security.  That other subnet is where any IP cameras, washing machines, and your kid's friends should go. 

There's a website that has lots of router manuals for hundreds of different brands of routers, if you've lost yours.  Inside the manual, should be a way to setup DHCP reservations - that way, when a specific device makes an DHCP request on the network, it is returned specific settings, like a static IP.  This is all based on the MAC of the requesting ethernet device.  
Google found this: [https://hg8245h.wordpress.com/2015/12/14/how-to-assign-static-ip-address-on-hg8245h/#more-64](https://hg8245h.wordpress.com/2015/12/14/how-to-assign-static-ip-address-on-hg8245h/#more-64) , but there are lots of Huawei forum posts about this too, which I didn't click.

So, all you need now is a way to get a list of MAC addresses and hopefully, a list of devices.  In the olden days, we'd use 'arp' to do that.  The new command is **ip -r neighbour**.  The -r switch is to perform DNS lookups to get a name -to- MAC mapping.  Remove the -r to get the IP-to-MAC mapping.

Clear as mud?

---

### Post by grzesiek811 on 2023-03-30
I've linked IP with new motherboard mac address on router ARP and nie it works.

---

