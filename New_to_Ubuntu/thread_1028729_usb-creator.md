---
title: "usb-creator"
date: 2009-01-02
forum: New to Ubuntu
---

### Post by Jheffrey on 2009-01-02
I run, 

sudo apt-get install usb-creator

and get this,

couldn't find package usb-creator

I think I have to add the repository, but where do I get it from?

Thanks,

Jheffrey

---

### Post by mc4100 on 2009-01-02
> **Jheffrey said:**
> I run, 

sudo apt-get install usb-creator

and get this,

couldn't find package usb-creator

I think I have to add the repository, but where do I get it from?

Thanks,

Jheffrey

Not very helpful ... but you shouldn't need a PPA. If you're running Intrepid, usb-creator is in the "main" repository. It should just install.
You can grab it manually [here]("http://packages.ubuntu.com/intrepid/usb-creator").

---

### Post by handydan918 on 2009-01-02
Should be in the repos. Post the output of ```
cat /etc/apt/sources.list
```

---

### Post by amauk on 2009-01-02
are you on Hardy or Intrepid?
it was added in Intrepid

---

### Post by Jheffrey on 2009-01-02
> **handydan918 said:**
> Should be in the repos. Post the output of ```
cat /etc/apt/sources.list
```

Here you go,

```

deb http://dell-mini.archive.canonical.com/ubuntu/ hardy main universe multiverse restricted
deb-src http://dell-mini.archive.canonical.com/ubuntu/ hardy main universe multiverse restricted

deb http://dell-mini.archive.canonical.com/ubuntu/ hardy-updates main universe multiverse restricted
deb-src http://dell-mini.archive.canonical.com/ubuntu/ hardy-updates main universe multiverse restricted

deb http://dell-mini.archive.canonical.com/ubuntu/ hardy-security main universe multiverse restricted
deb-src http://dell-mini.archive.canonical.com/ubuntu/ hardy-security main universe multiverse restricted

deb http://dell-mini.archive.canonical.com/ubuntu/ hardy-netbook-base main universe multiverse restricted
deb-src http://dell-mini.archive.canonical.com/ubuntu/ hardy-netbook-base main universe multiverse restricted

deb http://dell-mini.archive.canonical.com/ubuntu/ hardy-dell-mini main universe multiverse restricted
deb http://us.archive.ubuntu.com/ubuntu/ hardy main universe restricted multiverse
deb-src http://dell-mini.archive.canonical.com/ubuntu/ hardy-dell-mini main universe multiverse restricted
```

> **amauk said:**
> are you on Hardy or Intrepid?
it was added in Intrepid

I'm running 8.04.1(Hardy) on a Mini 9.

---

