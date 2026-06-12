---
title: "how to install tar file"
date: 2010-02-04
forum: New to Ubuntu
---

### Post by manny43 on 2010-02-04
Hello friends

I'd like to download and install Cheese-2.26.0.tar.gz and need some help how to install it.
Could you please teach me how to install it using terminal?Thank you very much.

---

### Post by howefield on 2010-02-04
Expend all that effort on a version older than what is available in the repository, (which is the current stable version).

Not likely ;)

---

### Post by oldos2er on 2010-02-04
Is your goal to run cheese, or learn to compile source code?

---

### Post by pirateghost on 2010-02-04
LOL.  ignore the tar file

```
sudo apt-get install cheese
```

done

---

### Post by Leppie on 2010-02-04
maybe he just wants to keep other people busy... :P

---

### Post by manny43 on 2010-02-04
Cheese 2.26.0 using the same webcam works great in Ubuntu 8.04 and Fedora 11 but the stable version
of Cheese freezes video in Ubuntu 9.10 and Fedora 12 that is the reason i'd like to install older version

---

### Post by Leppie on 2010-02-04
> **manny43 said:**
> Cheese 2.26.0 using the same webcam works great in Ubuntu 8.04 and Fedora 11 but the stable version
of Cheese freezes video in Ubuntu 9.10 and Fedora 12 that is the reason i'd like to install older version
then why don't you try the v.2.26.0 .deb package? [http://packages.ubuntu.com/jaunty/cheese](http://packages.ubuntu.com/jaunty/cheese)

---

### Post by warfacegod on 2010-02-04
You'll probably need to remove the newest version first:

```
sudo apt-get remove cheese
```

Now if that only worked for when my daughters squish their sliced cheese into my living room carpet.

---

### Post by Leppie on 2010-02-05
> **warfacegod said:**
> Now if that only worked for when my daughters squish their sliced cheese into my living room carpet.
for those cases there's:
```
sudo apt-get ***purge*** cheese
```

---

### Post by warfacegod on 2010-02-05
I would prefer:

sudo apt-get install steam-cleaner

---

### Post by Leppie on 2010-02-05
> **warfacegod said:**
> I would prefer:

sudo apt-get install steam-cleaner
that would be the next step ;)

---

### Post by manny43 on 2010-02-06
Thanks for the help

---

### Post by Leppie on 2010-02-07
you're welcome :)

---

