---
title: "Help needed!"
date: 2007-09-21
forum: Networking &amp; Wireless
---

### Post by Chris_Hansen on 2007-09-21
I need to make some kind of local name lookup on our edubuntu server, more specifically along the following lines:

When the following mail.mydomain.com is entered on a client or the server, i need to make it auto resolve to a specific ip.

How do I accomplish that?

---

### Post by helgman on 2007-09-21
If you want a specific name (aka mail.mydomain.com) to point to a specific IP-address (aka 10.0.0.4) you can add it in your hosts-file - this is if you are only going to be needing it on ONE or TWO machines. If there's a lot of machines you really should fix it via DNS.

If you go for the host-files solution (1 or 2 machines) open */etc/hosts*

and add a line like:

```
<ip-address>     <name-it-should-resolve-from>
```

So the example above would be:

```
10.0.0.4    mail.mydomain.com
```

If you are going for DNS you really should look things up and think them through (or even better talk to the one in charge of the domain). There is a lot more information needed to make that work ...

Regards,
Helgman

---

### Post by Chris_Hansen on 2007-09-21
Helgman,

Thank you for your help, this was just what i needed! :-)

---

