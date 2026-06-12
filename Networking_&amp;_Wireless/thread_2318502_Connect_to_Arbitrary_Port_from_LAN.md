---
title: "Connect to Arbitrary Port from LAN"
date: 2016-03-26
forum: Networking &amp; Wireless
---

### Post by Jack Waugh on 2016-03-26
I have a web server up on some arbitrary port number that is not a well-known port (doesn't require superuser to listen on it) and happens to equal 3000 in my case. I can browse to the web server fine from the same machine with [http://localhost:3000/](http://localhost:3000/) . From another computer on the LAN, I can SSH into the server computer, so that proves that some ports work (a well known port number, at least). But when I try either IP # that the interfaces on my server computer are currently using (shown by "ifconfig"), from either the server computer itself or another computer on the LAN, the browser says it can't establish a connection. "sudo ufw status" responds "inactive". My router also says its firewall is turned off. Any idea how to turn on arbitrary ports for the local network, so they will work as well as the SSH port does?

---

### Post by TheFu on 2016-03-27
Depends on the web server, but many do not listen on the public IP by default. This is common for development tools like the RoR webserver.   So, the answer is wholly related to the web server being used. Which is it?

---

### Post by Jack Waugh on 2016-03-27
Thanks! That was it!

---

