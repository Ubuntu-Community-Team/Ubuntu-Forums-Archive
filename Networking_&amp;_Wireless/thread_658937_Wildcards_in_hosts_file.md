---
title: "Wildcards in hosts file?"
date: 2008-01-05
forum: Networking &amp; Wireless
---

### Post by danieR on 2008-01-05
Is there a way to wildcard an alias in the hosts file? I'm trying to change a certain domain and all it's subdomains to loop back to 127.0.0.1, And I don't feel like writing
```
127.0.0.1 example.com www.example.com forum.example.com blog.example.com
```
etc... Especially as I'm going to add and remove a lot of those while developing :)

---

### Post by tehet on 2008-01-05
I'm not entirely sure what you mean but perhaps you can use /etc/resolv.conf. I've got a line in there like this:
```
search whatever.domain.net
```
Now, if I type "foo" in my browser, it resolves to foo.whatever.domain.net. Maybe you can use this in conjunction with /etc/hosts.

---

### Post by josef.sabl on 2008-05-07
> **danieR said:**
> Is there a way to wildcard an alias in the hosts file? I'm trying to change a certain domain and all it's subdomains to loop back to 127.0.0.1, And I don't feel like writing
```
127.0.0.1 example.com www.example.com forum.example.com blog.example.com
```
etc... Especially as I'm going to add and remove a lot of those while developing :)
Hello, have you resolved this? I have the exact same problem. Thank you.

---

