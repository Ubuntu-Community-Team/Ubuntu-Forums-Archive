---
title: "Can ping but cant resolve host address following recent upgrade"
date: 2010-05-08
forum: New to Ubuntu
---

### Post by Rorke on 2010-05-08
I lost all network function following an upgrade. Don't know what was upgraded, as it was on my daughter's PC and she installs all updates by default.

The network manager icon never connected (but all works fine in XP).

I set up a manual IP address (although I'm a newbie here).

Now I can ping the router and my PC, I can ping back. But wget and all internet programs report 'unable to resolve host address'.
I checked her 

/etc/hosts

127.0.0.1 localhost 
127.0.1.1 alice.Belkin alice

and some stuff about IPv6

Any thoughts? It seems like I've missed something totally obvious as I can't find anything in the forums!

---

### Post by 3rdalbum on 2010-05-08
Check your DNS. If the router isn't pushing out the DNS information to the computer, then you might need to use Opendns.com as the DNS service.

---

### Post by davec64 on 2010-05-08
Did you set up the Static IP Adddress using Network Manager?

If so, you need to set the DNS address. Set it to the address of your router (the default gateway) and let the router forward the DNS resolution. Alternatively if you know the DNS server addresses of you ISP you could set it to that.

This caught me out as well with the same problem you had, I'm sure in previous versions if you left the DNS address out it automatically went to the default gateway, but I might be wrong!

---

### Post by Rorke on 2010-05-08
I did set the DNS address (and all the other addresses) in Network Manager.
 I don't know how to check the DSN.
The router, when I login, has a list of the 4 IP addresses I expect to see. The only slight thought is that the PC name next to the IP address in the router is a very old one.

---

