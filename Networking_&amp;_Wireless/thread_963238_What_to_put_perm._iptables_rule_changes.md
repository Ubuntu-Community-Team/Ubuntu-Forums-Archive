---
title: "What to put perm. iptables rule changes?"
date: 2008-10-30
forum: Networking &amp; Wireless
---

### Post by needhelpplease on 2008-10-30
Very simple question:

I'm using Hardy Heron server.  I know that Ubuntu has had iptables for a long time now.  I need to have a few rules added when the server boots up.  In particular, I'm using a line to forward port 80 to port 8080 so I can run Tomcat as non-root.

The rule is easy:

```
iptables -t nat -A OUTPUT -o lo -p tcp --dport 80 -j REDIRECT --to-port 8080
```

(does it on loopback)

What's the right place to put that so it gets run on boot?  Is there some kind of local FW rules file I should put that in?

Thanks

---

### Post by dmizer on 2008-10-30
Take a look here: [https://help.ubuntu.com/community/IptablesHowTo#Saving%20iptables](https://help.ubuntu.com/community/IptablesHowTo#Saving%20iptables) :)

---

### Post by needhelpplease on 2008-10-30
Cool, thanks.  I'll do that.

---

### Post by needhelpplease on 2008-10-30
Another question: what about using UFW?

It's very easy to use it to set up simple stuff like "allow SSH".  And it has a file called /etc/ufc/after.rules which looks like it might be the place to drop in custom rules?

---

### Post by dmizer on 2008-10-30
> **needhelpplease said:**
> Another question: what about using UFW?

It's very easy to use it to set up simple stuff like "allow SSH".  And it has a file called /etc/ufc/after.rules which looks like it might be the place to drop in custom rules?

I've never personally used it, so I know nothing about it but people who use it seem to like it.

---

