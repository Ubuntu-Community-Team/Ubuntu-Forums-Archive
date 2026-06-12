---
title: "Cannot remotely connect to my computer (with  ftp)"
date: 2008-05-18
forum: Networking &amp; Wireless
---

### Post by mat28590 on 2008-05-18
I'm running Hardy Heron (64-bit), linksys am200 modem, DI-523 (d-link) router. I'm connected by wire to the router.

When i do: ftp <myipadress> (i got my ip address from [www.whatismyipaddress.com](www.whatismyipaddress.com))
i get the "timed out" error after about 2 minutes of it doing nothing.

I CAN connect using another computer on the local network, if i do:
ftp <192.168.0.187> where 192.168.0.187 is the local ip of the computer running proftp

I forwarded the ftp port on my router to the computer running proftpd and it still doesn't work.

I'm really stuck

Any thoughts?

---

### Post by SpaceTeddy on 2008-05-18
home routers like your d-link DI-523 will do the forwarding, but they only see it neccessary for incomming equests from the internet. Try to run your test again when you are not on the internal network. 

The reason they do that is to prevent users from ever locking themselves out of the router. If you forwarded port 80 on your router, and it would really forward any port 80 request, you would never ever be able to load the configuation page again. since anything would be forwarded. So the restiction on (most) of these devices is that only traffic that really come in on the external network device (WAN Port) will be forwarded.

try to access your server again when you are really on the internet.

i hope this make sense... :)

---

