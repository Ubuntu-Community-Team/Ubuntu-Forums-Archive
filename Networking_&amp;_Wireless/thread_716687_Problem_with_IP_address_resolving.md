---
title: "Problem with IP address resolving"
date: 2008-03-06
forum: Networking &amp; Wireless
---

### Post by aravindh.ero on 2008-03-06
Hi,
We are hosting a domain on windows 2000 server using IIS. 
Our DNS name is (For Ex:-www.abc.com) working fine. 
We are able to ping that IP from other place. 
But when we give the IP address (For Ex:- 192.168.1.1) instead 
of DNS name on any browser its not resolving. 
The error message shows "HTTP 404 not found". 
What could be a problem? 
Any one have any idea?
Awaiting for all your Suggestions,

Regards,
Aravindh

---

### Post by schmildo on 2008-03-06
The easiest solution would be to draw a picture of your network, then post it here for us to see.

There could be a few reasons for your problem.

It's important to know from where in your network you are pinging from, and to.

It is also important to check what IP address you are pinging.

It seems that your default gateway for the machine you are attempting to connect from, is mishandling the data.

Definitly draw a picture for us to see and we'll be better able to assist.

Good luck,

---

### Post by SpaceTeddy on 2008-03-06
mhm, if i might take an uneducated guess. i only know how apache works, but there you have to tell it which hostnames it should respond to... so my question is, is it possible to view the site from the server itself, by accessing (for example) the external ip or the loopback device ?

otherwise, i'm with schmildo - it's a network problem :(

---

