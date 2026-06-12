---
title: "Is cascading dns resolution possible?"
date: 2007-03-06
forum: Networking &amp; Wireless
---

### Post by gp2x on 2007-03-06
Hi all

I have a vpn running and would like to query the DNS server on the other end as well as the local one. That is, if the local query fails then query the remote DNS server.

It doesnt look like the linux resolver supports this sort of cascading resolution..... is this right?

Thanks

---

### Post by Mr. C. on 2007-03-06
Huh?

You will either get AN answer, or NO answer.  NO answer will be the result of a timeout.  I do not think you want every query to result in a >10 second timeout.

What are you trying to accomplish?

MrC

---

### Post by chili555 on 2007-03-06
> It doesnt look like the linux resolver supports this sort of cascading resolution

I think that is exactly what it does, actually. From man resolv.conf:> The algorithm  used  is to try a name server, and if the query times out, try the next, until out of name servers, then repeat trying all the name servers until a maximum number of retries are made.

If in doubt, RTFM*.

*Read The Friendly Manual

---

### Post by Mr. C. on 2007-03-06
gp2x,

The point I was trying to make is that one does NOT want to select name servers, where the first is expected to fail frequently, to next try the second.  This WILL result in long time delays for almost everything.


Again, gp2x, what are you trying to accomplish?

---

### Post by gp2x on 2007-03-23
Sorry guys 

What Im trying to do is if a query returns no answer (ie, it returns with 'dunno') then it will try the next server.

Reason being that Im using openvpn and wish to query the remote DNS server, but only if the domain is unknown to the local one. 

Hope that makes sense.

---

### Post by Mr. C. on 2007-03-23
What you are trying to do make sense, and the system is built to withstand non-responsive name servers.  But there is a timeout period, which will delay all your lookups to be unusable.

The resolver will automatically try the next resolver down the list in /etc/resolv.conf only after a 15 second waiting period for a timeout.

The resolver *expects* the name server's it has been supplied with to be recursive.  They either provide the answer, or they provide NXDOMAIN.

Run your own recursive name server if you want more control.

MrC

---

### Post by gp2x on 2007-03-25
Thanks for that

I realise now that the only way to achieve this is to run my own bind server and refer to other nameservers as necessary.

I think Ill just use /etc/hosts for the time being :D

Thanks again

---

### Post by Mr. C. on 2007-03-25
You're welcome.  Its pretty trivial to setup a local caching name server.

Let us know if you need assistance.
MrC

---

