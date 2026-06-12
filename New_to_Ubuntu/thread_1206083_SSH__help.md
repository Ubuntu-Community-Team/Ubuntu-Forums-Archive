---
title: "SSH  help"
date: 2009-07-06
forum: New to Ubuntu
---

### Post by DSn0wMan on 2009-07-06
When I try to ssh to a server it seems like I am required to put the fully qualified name or it wont resolve

does not work: ```
ssh myhost
```  
does work: ```
ssh myhost.mydomain.com 
```

With Windows and putty the first one works fine. Is there some way to use the shorter version within Ubuntu?

---

### Post by Celauran on 2009-07-06
Add myhost to /etc/hosts or create an entry in ~/.ssh/config

---

### Post by DSn0wMan on 2009-07-06
> **Celauran said:**
> Add myhost to /etc/hosts or create an entry in ~/.ssh/config


I realise that I could just add it to /etc/hosts, but that gets tedious if you have to keep track of more than a few hosts.

I guess I am wondering why DNS does not just resolve it for me like it does on windows. I do end up with the proper nameserver in resolve.conf

---

