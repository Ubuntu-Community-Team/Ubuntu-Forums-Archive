---
title: "Remote access to Linux Server 9.10"
date: 2010-03-10
forum: New to Ubuntu
---

### Post by Walter Vrey on 2010-03-10
Hi,

I have installed a slave server on my client's local lan, that replicate a web database mysql db.

I am using Ubuntu server 9.10 - no GUI installed - all command line.

I have installed Open SSH and can connect to the linux server via Putty from a Windows platform from the LAN

Now I need to be able to get remote access to the linux box to monitor the slave server form our offices. Obviously I need an external IP to be able to connect - I think...

Please advise the best way to get remote access to the linux server without having the client to operate anything from their side.
I need some kind of access - almost like the windows app - logmein. 
Is there software I can install on the linux box or something??

Kindly advise.
Regards
Walter

---

### Post by Grenage on 2010-03-10
Assuming that the office is a common scenario, with a handful of computers using an internet gateway as their default gateway.

Does the customer have a static IP?
If not, does their internet router support a dynamic DNS service  (dyndns etc.)?
If not, there might be a linux client for a dynamic DNS service.

You'll need to configure port forwarding on the router, to forward the relevant ports to the server.

You'd be best using keys rather that passphrases for security on the server; if not, make sure your passphrase is strong.  Consider using fail2ban to block IP addresses that are trying to get in (and failing).

---

