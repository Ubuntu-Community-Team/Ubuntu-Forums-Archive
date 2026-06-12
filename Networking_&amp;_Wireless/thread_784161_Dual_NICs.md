---
title: "Dual NICs"
date: 2008-05-06
forum: Networking &amp; Wireless
---

### Post by psyion on 2008-05-06
Hello Everyone

I have my server setup with 2 NICs both connected to different routers.

Router A (eth1)

Router B (eth0)

I have set my network cards up using the following interfaces file

```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
address 192.168.1.69
netmask 255.255.255.0
gateway 192.167.1.254

iface eth1 inet static
address 192.168.0.2
netmask 255.255.0.0
gateway 192.168.0.1

auto eth1
```

I would like the server to access the internet from eth1 card and ignore the internet on eth0. I would also like to be able to connect to the server from any of the computers attached to router b(eth0). The current setting do appear to work but i cant be sure which internet connect its using....

Just to clarify

Router A(eth1) is connected to its own internet connection that i want to use only for server traffic.

Router B(eth0) is connected to the internet and all of the computers in my home and i only want this internet connection to be used by desktop pcs in the home.

If anyone could explain to me what i need to change in this file to get it working how i want i would be greatful. I'm very new to Linux but i have set similar networks up on windows.

Thanks in advance guys, hope ya can help

---

### Post by psyion on 2008-05-06
BUMP!

anyone know the answer?

can anyone tell me what the inet in

iface eth1 inet static


is for?

---

### Post by jtrindle on 2008-05-06
I'm curious why you have a "gateway" line in the eth0 interface.  Does that IP really let you out into another network?

If you don't want eth0 to use that IP to get out, take out the gateway line. 

The word "inet" in the interface definition line just means normal IPV4 TCP/IP.  This is as opposed to IPV6 or Novell IPX... according to the interfaces man page:

   man interfaces

at the terminal prompt.

---

