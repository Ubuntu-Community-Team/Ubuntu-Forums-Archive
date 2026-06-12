---
title: "Static AND dhcp on same NIC?"
date: 2008-06-11
forum: Networking &amp; Wireless
---

### Post by gilgongo on 2008-06-11
Hi - I've got a machine that for various reason I cannot have a static IP address for on the LAN. I also need to ssh in and admin the box (and I can't keep a monitor attached to it).

So my first thought was to try and give the box a dhcp lease on the primary interface (eth0) and a static address on a different network on eth0:0. I would then configure my client machine to also have an alias on that network. That way, the box would be able to get to the net via the dhcp lease, and I would be able to ssh in via its static IP. Like this:

# The primary network interface (dynamic)
allow-hotplug eth0
iface eth0 inet dhcp

# The secondary interface (static)
auto eth0:0 inet static
address 192.168.1.1
netmask 255.255.255.0
network 192.168.0.0
gateway 192.168.1.1

(note that the dhcp leases are in the range 172.20.*.*)

However, when I try that, I get:

/etc/init.d/networking restart
Reconfiguring network interfaces.../etc/network/interfaces:16: misplaced option
ifdown: couldn't read interfaces file "/etc/network/interfaces"
/etc/network/interfaces:16: misplaced option
ifup: couldn't read interfaces file "/etc/network/interfaces"

Does anyone know if it's even possible to do this? If so, how?

---

### Post by haldean on 2008-06-11
I have no idea how to assign two different IPs to a single network card, but you might find people who do on the Networking forum: [http://ubuntuforums.org/forumdisplay.php?f=336](http://ubuntuforums.org/forumdisplay.php?f=336)

---

### Post by gilgongo on 2008-06-11
Er - this is the Network forum.

---

### Post by chili555 on 2008-06-11
> network 192.168.0.0I think this is the incorrect line, and I doubt it's needed at all. Please remove it and see if networking restarts correctly.

---

### Post by ilrudie on 2008-06-11
Many routers support ip reservations through dhcp.  Seems like a simpler solution for your situation unless you need the computer to be on two different subnets for some reason.  If your router firmware doesn't support ip reservations you can look to see if your router model is supported by dd-wrt.

---

### Post by timcredible on 2008-06-11
can you have the dhcp server always give that machine the same address?  if not, is there dynamic dns or AD on your network?  if so, have the server register with the dynamic dns or AD so you can use a name.  if none of these apply, maybe have a script on the server connect to your client so you can check to see who's connected to your machine and get it's ip address that way.

---

### Post by gilgongo on 2008-06-11
I have no control over the router or dhcp server (sorry, I should have made that clear), so I can't get it to assign a static IP.

BTW I've also tried removing the "network" option but I still get the same error.

---

### Post by chili555 on 2008-06-11
I'm not at all sure you need to do anything specific to the router to utilize a static IP. Are you sure you cannot just use a static IP?

---

### Post by gilgongo on 2008-06-11
Well, I suppose I could give it an address and hope that it doesn't clash with something else on the network. The trouble is I wouldn't know until it was too late. I don't know what the DHCP pool range is.

---

### Post by chili555 on 2008-06-11
How many computers are active in the office? What's the IP address look like on you own machine? 172.20.8.101, for example? If there were 50 active computers in the office, I'd start my experiments at 172.20.8.199. You may get lucky.

---

### Post by gilgongo on 2008-06-12
Looks like that might be my only option. Thre are about 2,000 active machines in this office. I've managed to work out how to add a static IP to the Ubuntu box (just add the relevant ipconfig command to the if-up.d folder), but now I can't work out how to do the same thing to my Windows boxen so they can see the server.

---

### Post by rogier.de.groot on 2008-06-12
I've just tested this, my /etc/network/interfaces looks like:

## START HERE
iface lo inet loopback
auto lo

iface eth0 inet static
address 192.168.1.6
netmask 255.255.255.0
gateway 192.168.1.254
auto eth0

iface eth0:1 inet static
address 10.0.0.1
netmask 255.0.0.0
aut0 eth0:1
## END HERE

Hope this helps... In your case change use:
iface eth0 inet dhcp
auto eth0
for the regular connection...

---

### Post by gilgongo on 2008-06-13
Nice one - thank rogier. I was doing it with a script, but what you have is more convenient. Now all I need to work out is how to do the same thing on my Windows client machines...

---

