---
title: "localhost problems"
date: 2007-05-31
forum: Networking &amp; Wireless
---

### Post by Depressed Man on 2007-05-31
I'm trying to use the webmail extension in thunderbird to download hotmail and yahoo emails. But it keeps giving me localhost errors so I tried pinging localhost.

Which seems for the first line in a reply to send ping data but I get nothing after that.

---

### Post by jonallport on 2007-06-01
'localhost' is the alias of the 127.0.0.1 loopback address, if you ping it you will always get a reply provided a valid, functioning tcp/ip stack is loaded.

I think you problem is down to a misconfiguration in thunderbird, have a look at the server settings and make sure they point to valid mailservers.

Also, are you doing anything wierd/wonderful with mail filtering; I've come across examples (mostly under Windows) where mail is retrived by a filter from the mailserver and the mail client gets the mail via a loopback to the filter software running as a server locally.  I wouldn't expect anything under a UNIX to do this as it'd be more efficient to pipe it!

My bet is a misconfig.

J :^)

---

### Post by Depressed Man on 2007-06-01
I think the problem is I don't get a reply. It just states it's doing the first ping and I get nothing about a reply.

---

### Post by jonallport on 2007-06-02
Have you got a valid /etc/hosts? 

Does it have a 'localhost 127.0.0.1' entry?

---

