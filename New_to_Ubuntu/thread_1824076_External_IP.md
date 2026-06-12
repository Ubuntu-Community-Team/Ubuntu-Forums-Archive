---
title: "External IP"
date: 2011-08-13
forum: New to Ubuntu
---

### Post by ItalicPixels on 2011-08-13
I couldn't exactly find a method that works for me on this but what is the most simple method of finding my WAN IP on Ubuntu Server? Is there anything that doesn't involving having to use a Whatismyip or DynDns?

---

### Post by The Cog on 2011-08-13
The command **ifconfig** will show you all your local interfaces and their IP addresses. 

But if you are passing through an address-translating router (and I guess you are, based on your question), then there is no way to directly know what address yours is being translated to. You have to ask someone the other side of the translation what your address appears to be. Whatismyip is probably the easiest solution, but connecting to anything that tells you your IP address will do. Logging on to a server somewhere with SSH and typing **who**, for instance.

---

### Post by haqking on 2011-08-13
> **ItalicPixels said:**
> I couldn't exactly find a method that works for me on this but what is the most simple method of finding my WAN IP on Ubuntu Server? Is there anything that doesn't involving having to use a Whatismyip or DynDns?

Log into your router and check your WAN IP there

---

### Post by Rhizoid on 2011-08-13
Alternatively check with an online tool e.g.

[http://www.whatsmyip.org/](http://www.whatsmyip.org/)

or for a text only tool:

[http://checkip.dyndns.com/](http://checkip.dyndns.com/)

Cheese!

---

