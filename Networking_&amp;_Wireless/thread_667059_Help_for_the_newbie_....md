---
title: "Help for the newbie ..."
date: 2008-01-14
forum: Networking &amp; Wireless
---

### Post by bacoxswain on 2008-01-14
Greetings;
Here's hoping someone out there that knows alittle about Ubuntu networking can tell me how to configure myself so I can get out of the doghouse.

My significant other has asked for the following:

1) A simple URL address -> Done! I have setup DNS service through Dyndns.com with a custom DNS.

2) Ability to access our Asterisk server via soft phone -> Done! That was easily done with port fowarding.

3) Ability to access the 3 NAS servers and/or any other server on our home network over the public internet with an address similar to nas1.mydomain.net -> I'm lost on this one and require assistance for someone more skilled than I am.  I have installed Ubuntu 7.10 LAMP server and I have no idea as to where to go or what to do next.

In the LAN closet is a Linksys BEFSR41 router that is setup for NAT. 

If it is possible to do this PLEASE let me know.
-Chris

---

### Post by sqrt2 on 2008-01-14
When a browser connects to a site, it also transmits the domain name of the site it wants to reach in the HTTP header. (That's because the name first is resolved to an IP address and the browser connects to that address, but there can be many sites hosted behind the same IP address.) HTTP servers decide on what content to serve based on this "Host" entry in the HTTP header.

What you could do, is forward mydomain.net:4242, :4243, and :4244 to port 80 of your NAS devices in your LAN. Then you configure nas(1|2|3).mydomain.net to point to the same IP address as mydomain.net (as that's the only IP address you have and even if you had more, your router probably can handle only one). You forward port 80 at your router to a computer in your LAN that hosts a web server. This web server then redirects you to mydomain.net:424(2|3|4) based on the "Host" entry in the HTTP header. (The Apache directive "Redirect" can do such a thing, in combination with Virtual Hosts.)

It's not simple, but there's nothing simpler I can think of now.

---

