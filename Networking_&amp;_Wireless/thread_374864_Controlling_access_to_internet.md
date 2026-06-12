---
title: "Controlling access to internet"
date: 2007-03-03
forum: Networking &amp; Wireless
---

### Post by RudolfMDLT on 2007-03-03
Hey!

I did some holiday work for a company that used RouterBoards to bridge internet connections with Wifi connections. They used a HotSpot technology to intercept any HTTP traffic and redirect the person's browser to an http login screen. the login credentials where stored on an remote RADIUS server.

Now I want to replicate this in some smaller manner for my a friend's coffee shop. I have some networking experience on NT and Windows 2000 but I have never setup a Linux network more complex than peer to peer.

What I would like to do is:

[ADSL internet]------>[Linux Proxy/Hotspot/User Control, running DHCP]------>[WiFi Access point]------>[2 or 3 random users with laptops]

Is what I am asking basically a proxy server? I would be very grateful if some one could help me with some basic insight on this:

1) What open source software exists that would allow me to control who access's the Internet - ie, the user would need to logon in order to use the internet?
2) How would this login work - I would prefer a browser based login?

I would really appreciate any help from the comunity!

Thank you very much!

Rudolf

---

### Post by Mr. C. on 2007-03-03
Go over the [www.smoothwall.org](www.smoothwall.org) and read about Captive Portal in the community add-ons area.

A captive portal does what you require - forces new users to a web login, and then reconfigures the firewall rules to allow traffic.

Smoothwall is an outstanding open source, free product.  All you need is an old PC, a small disk, and two or three ethernet cards.

MrC

---

### Post by RudolfMDLT on 2007-03-03
Thank you very much! It looks like it could do the job! Awesome!

---

### Post by Mr. C. on 2007-03-03
You're welcome.

I've been running a smoothwall for years, and have been very pleased with it.

While you are there, take note of the "superkernel" package.  It adds several additional features you might desire.  You might find it best to first get acquainted with the vanilla product, then some addons, then jump to the superkernel and captive portal software.

Best of luck,
MrC

---

### Post by nicoladimaria on 2007-04-02
I'd like to set up a free hot spot using open source software. I checked this smoothwall but it looks like it's a firewall. would it be useful for my purpouse ?
thanks

---

### Post by Mr. C. on 2007-04-02
A hotspot can be as minimal as an access point connected to your internet.  What are your requirements ?

MrC

---

### Post by mchan on 2007-04-09
MrC,
I am facing the same situtation, I want to set up some access points in a communities that are controlled by a remote radius server (web based authentication through http) in a public IP address / 139.142.xx.xx:1812 or [http://www.domain.com/login](http://www.domain.com/login).
I am trying to intergated the Ubuntu (edgy) with this "SmoothWall" but cannot located the addon as you mentioned.
I also have trouble to locat the documentation for such installation.
Please help.
Michael

---

### Post by Mr. C. on 2007-04-09
[http://community.smoothwall.org/forum/search.php?mode=results](http://community.smoothwall.org/forum/search.php?mode=results)

---

