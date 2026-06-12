---
title: "ssh syntax"
date: 2007-03-22
forum: Networking &amp; Wireless
---

### Post by Ephilei on 2007-03-22
I'm not asking for help. I found my own answer and thought I'd write it down for future users like me.  In my experience, contrary to my google searches, you cannot log on with 

```
ssh host username
```

I received a lot of password denials: 

```
Permission denied (publickey,password).
```

After hours and hours, I realized all I had to do was login using the syntax

```
ssh username@host
```

This is only my experience and I don't know why the syntax differs. Maybe it's Ubuntu? It might be a bug particular to my machine.

---

### Post by Seti on 2007-03-22
You can also do:
```

ssh -l username host

```

as per the ssh manpage.

---

### Post by Ephilei on 2007-03-22
Yeah.

---

