---
title: "KDE on Ubuntu Lucid"
date: 2010-08-07
forum: New to Ubuntu
---

### Post by gavdari on 2010-08-07
Is it possible to install KDE on Ubuntu? If so, how? Are there any drawbacks? I've been customizing my GNOME to the point I'm loving it, but I'm so eager to test KDE too. If I don't like it, is it easy to remove and be right back at the same state I am (without KDE applications)?

---

### Post by dv3500ea on 2010-08-07
Yes, install [kdebase]("apt:kdebase").
If you don't like it, remove the package then run
```

sudo apt-get autoremove

```
in a terminal.

---

### Post by gavdari on 2010-08-07
Well, just curious, if I liked it a lot, is there a gnomebase to remove and then run the above command to clean it? :D  because I guess it'll be too crowded with all applications from GNOME and KDE at the same time.

---

### Post by Zeike on 2010-08-07
> **gavdari said:**
> Well, just curious, if I liked it a lot, is there a gnomebase to remove and then run the above command to clean it? :D  because I guess it'll be too crowded with all applications from GNOME and KDE at the same time.

See: [http://www.psychocats.net/ubuntu/purekde](http://www.psychocats.net/ubuntu/purekde)

There are also many other useful guides on that blog, including "puregnome" & "purexfce".

I'd also make sure you note what packages are being removed, in case you find later you actually need them.

---

### Post by sandyd on 2010-08-07
> **dv3500ea said:**
> Yes, install [kdebase]("apt:kdebase").
If you don't like it, remove the package then run
```

sudo apt-get autoremove

```in a terminal.
kde-minimal is a better idea.

---

