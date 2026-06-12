---
title: "Manually clearing out theme files"
date: 2009-11-19
forum: New to Ubuntu
---

### Post by Kjasontu on 2009-11-19
I added a Theme that must not have installed correctly called Moomex.  It does not show up in my list of available themes.  When I try to install it from a fresh download it tells me it already exists.  How do I manually clear the old files out?

Thanks.

---

### Post by jualin on 2009-11-19
Go to System, Preferences, Appearance and select the theme you want to delete and then click on "delete". Then you can install it from there as well by clicking on "install".
I used to have moomex as well, it is one of my favorites. What I don't like about it is the "oversize panel" :lol:
Hope this helps!

---

### Post by emigrant on 2009-11-19
if you can't find it through appearance panel,
go to these places and see:

/usr/share/themes
or
~/.themes

---

### Post by Kjasontu on 2009-11-19
> **emigrant said:**
> if you can't find it through appearance panel,
go to these places and see:

/usr/share/themes
or
~/.themes

It is not in "/usr/share/themes".  How do I find~/themes?

"Moomex" does not show in a directory search.

---

### Post by emigrant on 2009-11-19
i mean
~/.themes which is equal to /home/yourname/

or copy paste this into terminal
```
 ls -l  ~/.themes
```

or to find it

```
sudo find / -name *oomex
```

---

### Post by Kjasontu on 2009-11-19
> **emigrant said:**
> i mean
~/.themes which is equal to /home/yourname/

or copy paste this into terminal
```
 ls -l  ~/.themes
```or to find it

```
sudo find / -name *oomex
```

Thanks!! Found it.

---

