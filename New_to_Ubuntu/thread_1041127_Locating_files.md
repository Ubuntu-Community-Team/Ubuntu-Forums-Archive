---
title: "Locating files"
date: 2009-01-16
forum: New to Ubuntu
---

### Post by Jynxx on 2009-01-16
Hey all. What command line do I use to locate files? I installed Vendetta and cant find where it installed to.

Thanks!

---

### Post by Malalo on 2009-01-16
You almost answered yourself...

```
locate Vendetta
```

should help you find your files.

---

### Post by Jynxx on 2009-01-16
Thank you!

---

### Post by Elfy on 2009-01-16
or whereis 

```
whereis vendetta
```

bear in mind that case sensitivity is important, it's likely that it'll be v

---

### Post by hyper_ch on 2009-01-16
or use the almighty "find". However locate is faster because it uses a database of indexed filenames/paths... if you recently added a new file and look for it, you first have to update the db:
```

sudo updatedb

```

---

### Post by Coreigh on 2009-01-16
CORRECTION. (hyper_ch has a typo.)

```
sudo updatedb
```
^to create or update the locate database^

```
locate foo
```
^to find a file named foo^

find can be pretty useful too, if you know how to use it.
[http://www.linux.ie/newusers/beginners-linux-guide/find.php](http://www.linux.ie/newusers/beginners-linux-guide/find.php)

---

### Post by Vadi on 2009-01-16
To join the umpteen methods fest, you can also use *Places&#8594;Search for Files...*

---

### Post by hyper_ch on 2009-01-16
> **Coreigh said:**
> CORRECTION. (hyper_ch has a typo.)

fixed :)

---

### Post by lavinog on 2009-01-16
locate is fast, but find gives you alot more options

find . -mmin -5
will find all files in the current folder and subfolders that have been modified in the last 5 mins

---

### Post by Ptero-4 on 2009-01-16
> **Vadi said:**
> To join the umpteen methods fest, you can also use *Places&#8594;Search for Files...*

The OP specified a command line method of searching files. Your method involves gnome.

---

### Post by Vadi on 2009-01-16
Sure does. The title however doesn't, so others who are looking for a more human way might come looking!

---

