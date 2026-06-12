---
title: "Web Server only visible inside network"
date: 2008-03-07
forum: Networking &amp; Wireless
---

### Post by vlenza on 2008-03-07
I've installed the Ubuntu LAMP server, and have installed Joomla just fine from another machine within the network.  When using the local IP address from a machine on the same router - using 192.168.1.104 - I can access everything just fine.  But when I try to view the site from outside the router, the request times out.

Of course I've changed the Ubuntu box to a static IP, and have forwarded port 80 to that address.  I've even put the box's IP address into the DMZ, but still I get the timeout error from outside the network.  

Any ideas?

---

### Post by ShinHadoken on 2008-03-07
Sorry, I actually just posted about the same problem. I'll let you know if I get anything. :)

---

### Post by HereInOz on 2008-03-08
I had the same problem a while back at a client's place and it actually related to the router using port 80 for its web based management console, and this was causing it to block incoming requests on port 80.

I haven't seen this behaviour on any other router/modems, so this had us stumped for a while.  We changed the port for the management console of the router/modem to port 8080, and that solved the problem.  You just have to remember to add :8080 to the address when you want to access the management console.

I don't know if this is the same problem for you blokes, but I thought it worth a mention.

---

