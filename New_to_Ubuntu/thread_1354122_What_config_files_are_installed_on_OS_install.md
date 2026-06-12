---
title: "What config files are installed on OS install?"
date: 2009-12-13
forum: New to Ubuntu
---

### Post by Mark_in_Hollywood on 2009-12-13
I want print a Nautilus listing of my ./*.*  files/folders under /home.

How do I do this? 

I looked at both online help and Contents help and cannot find a way to print a directory listing.

---

### Post by Physical Hook on 2009-12-13
What is *Nautilus listing* ?

```
ls -al $HOME
```

.. will list all files in your home directory.

---

### Post by bacardiandwatermelon on 2009-12-13
Is this what you are after?

```
ls -R > test.txt
```

---

