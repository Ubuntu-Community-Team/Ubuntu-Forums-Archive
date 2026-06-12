---
title: "Howto set AT&amp;T Public Static IPs"
date: 2007-07-16
forum: Networking &amp; Wireless
---

### Post by orozcovision on 2007-07-16
Hello,

I'm currently in the planning of upgrading my ISP's (AT&T) services from High Speed DSL Dynamic IP addresses, to Static IP addresses.

I've been on the phone all day with their technical department, only to realize that they either: 1). Don't understand what I'm asking of them, or 2). They just don't know what they're doing.

Here is my current situation:

I have a Name Server, Web Server, and Email Server which I will be configuring for Static IP addresses.  Current setup at /etc/network/interfaces is as follows:

//---------------------------------
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.1.100
netmask 255.255.255.0
gateway 192.168.1.1
----------------------------------//

As you can see, this setup is already static.  My questions/concerns are: 

"How do I assign the public static IP address assigned by my ISP? 
Is this done through the Router? Or will I be replacing 192.168.1.100 with the assigned public IP?"
"How will this affect services which are chrooted?"
"What other configurations are involved for the other servers?"

Any help in these areas are greatly appreciated. Thanks.

Respectfully,
OrozcoVision

---

### Post by dreadlord_chris on 2007-07-16
You would set the static IP in your router. There shouldn't be any other changes necessary.

---

### Post by yabbadabbadont on 2007-07-16
If all your machines are connected through a router, then I would assume that it is the router's configuration that you would change to have the assigned static external IP address.  You probably wouldn't need to change anything on your actual machines.

Edit: Doh!  Too slow.  :D

---

### Post by orozcovision on 2007-07-16
Nice!  Thank you so much for your prompt responses.

--
OrozcoVision

---

