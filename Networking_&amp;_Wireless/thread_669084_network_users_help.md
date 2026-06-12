---
title: "network users help"
date: 2008-01-16
forum: Networking &amp; Wireless
---

### Post by beaker15 on 2008-01-16
Hello, 
I hope someone can clear this up for me or give me a link to read but here goes:

I'm used to Windows networks where you have a server with Active Directory which contains details of users on your domain and when clients login to their computer, they're logging on to the network, not the individual PCs.

At the moment i'm setting up a network with an ubuntu server (Feisty) and several Windows clients, with a few ubuntu clients to be added sometime in the future. Currently, the users log in to their individual PCs and access the shares on the old server through samba. Also, the old server doesn't have a mail server on so i'm incorporating postfix on my new one.

Ok, here's my questions
1.Do linux networks have a network/domain name, like Windows netwoks? if so, where do i name it?
2.Can the Windows/Linux client users log into the network, instead of their PC?
3.Ideally, I'd like each user to have the same username for the network, email, samba and the database. Can this be done centrally or does it need to be done individually?


I'm a bit used to Windows networks so you'll have to forgive me if i'm thinking a bit 'too Microsoft'. Its a nasty habit.

thanks in advance

---

### Post by scxtt on 2008-01-16
would something like this work?: [http://www.samba.netfirms.com/PDC.htm](http://www.samba.netfirms.com/PDC.htm)

(check this too: [http://www.freeos.com/articles/3842/](http://www.freeos.com/articles/3842/))

maybe something w/ ldap too?

---

