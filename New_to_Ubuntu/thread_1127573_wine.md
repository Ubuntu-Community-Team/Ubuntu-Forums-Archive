---
title: "wine?"
date: 2009-04-16
forum: New to Ubuntu
---

### Post by trinidadflores on 2009-04-16
I have wine installed on my machine i was using it for several programs thta i normally used while I had winblows installed, but now I have totally cut off that need for having these programs installed.  How do i make sure that everything is deleted?

---

### Post by oldos2er on 2009-04-16
To remove Wine:
```
sudo apt-get purge wine
```

---

### Post by kirsis on 2009-04-16
After purging, delete the ~/.wine directory.

```
rm ~/.wine -r
```

---

### Post by danni-la on 2009-04-16
if the above don't remove all the menu listings and icons etc try this...

[http://wiki.winehq.org/FAQ#head-9893ae50079ca7a959258f0bc9a17aaf2e69b391](http://wiki.winehq.org/FAQ#head-9893ae50079ca7a959258f0bc9a17aaf2e69b391)

---

