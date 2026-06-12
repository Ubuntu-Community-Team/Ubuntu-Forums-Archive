---
title: "Management of user logins, home directories"
date: 2006-10-26
forum: Networking &amp; Wireless
---

### Post by amagi on 2006-10-26
Hi there,

I have been looking into possibilities to create a simular settup under linux as more or less is possible with (a simple) Windows domain setup.

I want users to be centrally management so that there is one server to keep the accounts. This can be easely solved by using LDAP

The next thing I want is to have all the home directories of users stored on the central server. In all documentation NFS is mentioned for this possibility. When all the computers are fixed on the network this would not be a problem.

Now my problem:

I want people with laptops be able to work connected as well as disconnected from the network so that they can work at home or at another location. This means that if they work disconnected:

1. they do not have access to the LDAP server
2. they can not mount their home directory

My question is, have people solutions (perhaps its easy but I just do not see it) for this situation. I just can not believe that all the companies working with linux (red-hat, suse, novell, etc.) do not have people with laptops around.

Thanks

---

### Post by Iowan on 2006-10-26
So far, my experience has _LDAP_ and _easy_ as contradictory terms.  I haven't even contemplated it... but I suspect **Sessions** could be used to have an *online* or *offline* mode for a laptop.

---

### Post by amagi on 2006-10-27
I think I have to agree that ldap is not 'easy' but at least it is possible and there exists info. But for 'roaming usage' I have not yet encountered any info.

Can you explain a bit more what you mean with sessions?

---

