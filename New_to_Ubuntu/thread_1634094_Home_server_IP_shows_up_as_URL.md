---
title: "Home server IP shows up as URL"
date: 2010-11-30
forum: New to Ubuntu
---

### Post by sharkllama on 2010-11-30
Hi, 
   I've just setup a home server and registered a domain at namecheap.com.  They're currently forwarding the aforementioned domain to my home router's IP (which is static) which then forwards requests from port 80 over the LAN to my home server and everything is working almost perfectly.  

Here's the problem:

When I enter [http://www](http://www).[DOMAIN].com the URL is correctly forwarded to my home server but my browser displays my home server's IP instead of my domain.

Thus, if I type this: [http://www](http://www).[DOMAIN].com
I see this: [http://xx.x.xx.xxx](http://xx.x.xx.xxx)

Any ideas what may be causing this (possibly some apache misconfiguration)?
-Brant

---

### Post by 00arthuryu on 2010-11-30
It shouldn't display any of your internal IPs if you're using a computer outside your LAN. But to the problem itself, I think its a problem with the router's loopback function, since the IP your domain redirects to is itself, your internal IP is normally used. I know this can happen with certain (if not many) loopback-able routers. It certainly does it on mine.

If you want to check out if it still gives out your internal IP from a computer outside your LAN, try accessing your webserver from a proxy, or a mates computer.

---

### Post by TSJason on 2010-11-30
Out of curiosity do you have a proper virtualhost setup in apache that reflects the "ServerName" as the domain or is apache just falling through to the default location?

---

