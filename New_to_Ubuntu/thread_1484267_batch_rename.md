---
title: "batch rename"
date: 2010-05-15
forum: New to Ubuntu
---

### Post by phillw on 2010-05-15
Hi,

an easy one for you good people used to shell scripts :)

I have files like B13800&#61474;205154.eps.jpg that I want to rename to B13800.jpg

The good news is that the 'bit' I want to keep is the first 6 characters and they will all have .jpg at the end

Thanks,

Phill.

---

### Post by crjackson on 2010-05-15
Not a shell command but I prefer to use Renamthemall.  Have you checked it out?

---

### Post by ibuclaw on 2010-05-15
```
rename -v 's/^(.{6}).*?(.jpg)$/$1$2/' *
```

---

### Post by crjackson on 2010-05-15
> **ibuclaw said:**
> ```
rename -v 's/^(.{6}).*$/$1.jpg/' *
```

I could have never figured that out..  Don't even know what it means.

---

### Post by Paddy Landau on 2010-05-15
Also try pyrenamer. It's in the repositories.

---

### Post by phillw on 2010-05-15
> **ibuclaw said:**
> ```
rename -v 's/^(.{6}).*?(.jpg)$/$1$2/' *
```

Thanks, ibuclaw - I had spent some time reading the man page for rename - it may as well be in chinese :-)

Phill.

---

### Post by ibuclaw on 2010-05-15
> **phillw said:**
> Thanks, ibuclaw - I had spent some time reading the man page for rename - it may as well be in chinese :-)

Phill.

It's better than chinese, it's PERL!!!  :)

---

