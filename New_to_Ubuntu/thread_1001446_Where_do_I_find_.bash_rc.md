---
title: "Where do I find .bash rc"
date: 2008-12-03
forum: New to Ubuntu
---

### Post by Mick8882003 on 2008-12-03
So I have some software that need a few additions to .bashrc where do I find this please?

Thanks Mick C

---

### Post by iaculallad on 2008-12-03
> **Mick8882003 said:**
> So I have some software that need a few additions to .bashrc where do I find this please?

Thanks Mick C

Global:

> /etc/bash.bashrc 

User:

> ~/.bashrc

---

### Post by nhasian on 2008-12-04
a good command to know is *locate*

it reads all the files from a database that is updated every morning at 5am i think.  if you've recently added files then you can manually update the database with the command

```
sudo updatedb
```

---

### Post by rakris on 2008-12-04
If its not there then create it.

---

### Post by conscious on 2008-12-04
It is (or should be) in your home directory. All files with names beginning with a dot are hidden, so to see it in Nautilus, press Ctrl+H.

---

