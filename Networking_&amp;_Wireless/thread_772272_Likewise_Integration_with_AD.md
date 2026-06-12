---
title: "Likewise Integration with AD?"
date: 2008-04-28
forum: Networking &amp; Wireless
---

### Post by johnwillis on 2008-04-28
Hi,

I've just installed Hardy on my Windows 2003 network and I'm having a bit of problem with user authentication on the network.

I've installed "Likewise -gui" and I've managed to join the domain "kingsnortongirls.bham.sch.uk" and my computer account has been successfully created in AD as "SERVXP2" and the Likewise GUI is now allowing me to "leave domain" so I presume it is working correctly.

However when I reach the login screen I cannot log in, I just get "error" given to me.

I've tried the following variations:

[email]jwillis@kingsnortongirls.bham.sch.uk[/email]

KINGSNORTONGIRL\jwillis

jwillis

What am I messing up here?

Many Thanks

J

EDIT:

I've solved this problem by putting in multiple servers on the Kerbros Config screen (adminsvr, curricsvr1, dc3) and this has solved the problem with logging on.

Now does anyone know how to map home directories to network shares for users on logon?

Thanks

J

---

