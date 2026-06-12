---
title: "VPN over SSL"
date: 2009-12-15
forum: New to Ubuntu
---

### Post by koba101 on 2009-12-15
Anybody know a good VPN over SSL  software to use on Ubuntu?

I've 

I tired using OpenVpn but i'm not sure if it's the tool I need

is this something done over firefox only?

---

### Post by AndreasB123 on 2009-12-15
I connected 3 minutes ago fist time with the networkmanager to a SSL VPN.

Since Ubuntu 9.10 it works!

install network-manager-openconnect, than rightclick, edit connections (or how its called in english...) and fill in your connection informations...

Wiki: [http://wiki.ubuntuusers.de/Baustelle/Network-Manager/VPN_Plugins](http://wiki.ubuntuusers.de/Baustelle/Network-Manager/VPN_Plugins)


Andreas

---

### Post by DGortze380 on 2009-12-15
> **koba101 said:**
> Anybody know a good VPN over SSL  software to use on Ubuntu?

I've 

I tired using OpenVpn but i'm not sure if it's the tool I need

is this something done over firefox only?

Are you looking for a true VPN? or a Web VPN?

OpenVPN uses SSL and is a true VPN, not just a tunnel for web services.

---

### Post by koba101 on 2009-12-15
thanks andreas,,,,but i don't speak german well i'll giv it a shot

i believe VPN over SSL implements VPN using the SSL protocol. that's what i'm looking for

---

### Post by DGortze380 on 2009-12-15
> **koba101 said:**
> thanks andreas,,,,but i don't speak german well i'll giv it a shot

i believe VPN over SSL implements VPN using the SSL protocol. that's what i'm looking for

Yes, but SSL is just the encryption.

Lets try this another way. What are looking to use the VPN for?

---

### Post by koba101 on 2009-12-15
connecting to my university's network

---

### Post by DGortze380 on 2009-12-15
> **koba101 said:**
> connecting to my university's network

Ok. I'm trying to help here, but you need to give me something to work with. I still have no idea what you're trying to do.

Are you setting up a VPN Server?
What specifically do you need to access?
Is there a VPN set up that you just need to connect to?

What are you trying to do here?

---

### Post by koba101 on 2009-12-15
defeintely not trying to set up a VPN server

our university has a VPN, they offer web-based connection,  so I'm trying to connect to the VPN

no i'm not trying to set up a server...

what do i need to do to connect to their VPN

---

### Post by DGortze380 on 2009-12-15
> **koba101 said:**
> they offer web-based connection

You need credentials from your university. Point any web browser to their WebVPN Site and log-in.

---

### Post by koba101 on 2009-12-16
thanks

---

