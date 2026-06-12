---
title: "no /etc/inittab?"
date: 2010-06-02
forum: New to Ubuntu
---

### Post by lolzwut on 2010-06-02
I'm reading this book about linux and it's trying to teach about how linux boots. I understand everything but it says:


"The /etc/inittab file is the key to understanding the processes that init starts at various run levels. You can look at the contents of the file by using the more command as follows:

more /etc/inittab"


but when I do that I get:

```
/etc/inittab: No such file or directory
```


so does ubuntu have that file? If it doesn't what file preforms that operation? Is it a different name or something? Btw im using ubuntu 9. Thanx.

---

### Post by oldos2er on 2010-06-02
> **lolzwut said:**
> so does ubuntu have that file? If it doesn't what file preforms that operation? 

 No, Ubuntu hasn't used inittab for some time. Use upstart ([http://upstart.ubuntu.com/](http://upstart.ubuntu.com/)) instead.

---

### Post by lolzwut on 2010-06-02
but is it installed by default? It looks to me like you have to download and install that so what is already installed?

---

### Post by Bachstelze on 2010-06-02
> **lolzwut said:**
> but is it installed by default? It looks to me like you have to download and install that so what is already installed?

Ubuntu uses Upstart by default. Anything you will learn about Linux booting is probably based on the old SysV init and will not apply to recent releases of Ubuntu.

---

