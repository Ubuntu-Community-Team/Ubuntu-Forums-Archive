---
title: "removing a ppa repo"
date: 2009-11-23
forum: New to Ubuntu
---

### Post by mvalviar on 2009-11-23
I added a ppa repo using this ```
sudo add-apt-repository ppa:chromium-daily
```

It's turning up errors when I update. How do I remove it? I can't see it in sources.list.

---

### Post by ukripper on 2009-11-23
> **mvalviar said:**
> I added a ppa repo using this ```
sudo add-apt-repository ppa:chromium-daily
```

It's turning up errors when I update. How do I remove it? I can't see it in sources.list.

what error are you getting can you post the output?

---

### Post by wojox on 2009-11-23
Look in System > Administration > Software Sources > Other Software

---

### Post by emigrant on 2009-11-23
```
sudo gedit /etc/apt/sources.list
```

comment these lines:

```
deb http://ppa.launchpad.net/chromium-daily/ppa/ubuntu jaunty main
deb-src http://ppa.launchpad.net/chromium-daily/ppa/ubuntu jaunty main
```

---

### Post by sisco311 on 2009-11-23
It should be in:

/etc/apt/sources.list.d/<chromium-whatever>.list

---

### Post by blazemore on 2009-11-23
When you use apt-add-repository, it puts them in separate files under /etc/apt/sources.list/d

---

### Post by mvalviar on 2009-11-24
> **blazemore said:**
> When you use apt-add-repository, it puts them in separate files under /etc/apt/sources.list/d

Found them and removed them. SOLVED! Thanks.

---

