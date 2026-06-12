---
title: "PPTP VPN needs to be inbound only"
date: 2013-10-15
forum: Networking &amp; Wireless
---

### Post by Malalo on 2013-10-15
Hi guys,

So my ISP offers me this PPTP VPN to provide me with a "static IP and no ports blocked" connection. It works great.
Unfortunately, the no-ip update client send this new static IP address instead of the dynamic one from my modem.

I have different hosts on no-ip and I only need one to have the static IP (the VPN connection is a bit shaky). The others should use the dynamic IP address from my modem where the connection is much more reliable.

Support from no-ip says their servers no a "pingback" to confirm the IP address and since the client apparently uses the static IP to send the info, that's what the server keeps as an updated IP address.

Is there a way to setup the VPN connection to be inbound only ? I've set it up through Webmin.

Thanks !

---

### Post by houstonbofh on 2013-10-16
In the VPN settings under IPv4 click routes and check use this connection only for resources on it's network.  That way the path to no-ip will be via the DSL connection, not the VPN.  However, the routing loop (In one path and out another) may cause issues.

---

### Post by Malalo on 2013-10-16
> **houstonbofh said:**
> In the VPN settings under IPv4 click routes and check use this connection only for resources on it's network.  That way the path to no-ip will be via the DSL connection, not the VPN.  However, the routing loop (In one path and out another) may cause issues.

Thanks for the reply. I created the PPTP connection through Webmin and when I go into the connection's settings, there's a section about routes but nothing about "use this connection only for resources on it's network". 
What I see is this (sorry for bad image quality) :
[[IMG]http://img22.imageshack.us/img22/9325/b7wl.jpg[/IMG]](http://imageshack.us/photo/my-images/22/b7wl.jpg/)

This is an image I took from Google Images. Differences in my settings are :
- usename defined
- PPP options file set to "None"
- Delete old default route set to "Yes"
- Some differences in the encryption (but I don't think its relevant).

You say I might run into some issues because of the routing loop. Can you give me examples ?

---

### Post by houstonbofh on 2013-10-16
So...  I do not use webmin.  I will have a hard time helping you with that. :)  The option I was talking about was for a desktop install.  No clue how to make them match.

As for the routing loop;  You have a connection coming in on the VPN static IP.  It is routed to your server.  It answers, but instead of going back out the VPN it goes out the DSL, acquiring a different IP address in the process.  Routing is very simple. It says, this IP address just asked me a question, so how do I get back?  That route is the same regardless of how you were contacted.  This is why most VPNs just kind of take over the system and the routes.  Unfortunatly, that makes life hard for you and no-ip.

---

