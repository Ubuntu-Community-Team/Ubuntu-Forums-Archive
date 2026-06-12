---
title: "Help with port forwarding and DNS"
date: 2008-02-20
forum: Networking &amp; Wireless
---

### Post by WeedGrinch on 2008-02-20
Ok, i've setup php and mysql, and apache, and when I go to 10.0.0.7 it goes to my server.  But when i go to my external ip address is opens my modem settings.  I set port 80 to forward to my ip to 10.0.0.7 but when i go to my external ip address in firefox it takes me to my modem settings still :(

help please.

---

### Post by kaginken on 2008-02-20
Are you trying your external IP from within your local area network, or from the outside, ie you're neighbors house or a blackberry.

If you want to test your external IP, you can't from inside your house, ie local network.  If you have a blackberry, or a friend with internet, test it that way.

---

### Post by WeedGrinch on 2008-02-20
> **kaginken said:**
> Are you trying your external IP from within your local area network, or from the outside, ie you're neighbors house or a blackberry.

If you want to test your external IP, you can't from inside your house, ie local network.  If you have a blackberry, or a friend with internet, test it that way.

Tried, for friends it times out.

---

### Post by kaginken on 2008-02-20
Try telnetting into port 80 like so:

telnet <external-ip> 80  (from outside your LAN)

If your curser disappears, you've connected.  You can test this further by then typing:

GET <enter>

and you should get your index.html page in pure text in your terminal window.

Does that work?  

Note the exact time you try this, and check your router/firewall log(s).  They should reveal some info also.  If your traffic is passing through, check your webservers logs.

Hope that helps!

---

### Post by WeedGrinch on 2008-02-20
> **kaginken said:**
> Try telnetting into port 80 like so:

telnet <external-ip> 80  (from outside your LAN)

If your curser disappears, you've connected.  You can test this further by then typing:

GET <enter>

and you should get your index.html page in pure text in your terminal window.

Does that work?  

Note the exact time you try this, and check your router/firewall log(s).  They should reveal some info also.  If your traffic is passing through, check your webservers logs.

Hope that helps!

no 1 can ping my IP, doesnt connect.

---

### Post by kaginken on 2008-02-20
If you can't telnet in - then your firewall/router is misconfigured.  

Check your logs on your firewall/router.

---

