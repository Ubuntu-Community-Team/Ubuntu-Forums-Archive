---
title: "Limit Bandwidth Usage with apt-get"
date: 2009-08-04
forum: New to Ubuntu
---

### Post by ubudog on 2009-08-04
How do I do this?

---

### Post by wojox on 2009-08-04
```
sudo apt-get -o Acquire::http::Dl-Limit=25 upgrade
```

That limits apt-get to 25KB/s

I joined the group. Pretty cool.

---

### Post by Volt9000 on 2009-08-04
> **wojox said:**
> ```
sudo apt-get -o Acquire::http::Dl-Limit=25 upgrade
```

That limits apt-get to 25KB/s

I joined the group. Pretty cool.

Hey that's pretty cool.
Where can I get some information about other config options like that? The man page doesn't seem to have it.

---

### Post by ubudog on 2009-08-04
> **wojox said:**
> ```
sudo apt-get -o Acquire::http::Dl-Limit=25 upgrade
```

That limits apt-get to 25KB/s

I joined the group. Pretty cool.

Thanks!  Oh and thanks for joining the group :D

---

