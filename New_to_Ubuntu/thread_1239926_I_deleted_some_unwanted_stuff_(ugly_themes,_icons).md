---
title: "I deleted some unwanted stuff (ugly themes, icons)"
date: 2009-08-14
forum: New to Ubuntu
---

### Post by Couto on 2009-08-14
Well yes, I deleted the themes, and icons that I didn't like right?

Now stupid me, the icon theme I'm using relied on some of the other icon themes I guess, now I'm missing icons. :-(

Is there a command I can do to get all the default Ubuntu 9.04 icons back?

Thank you.

---

### Post by pmlxuser on 2009-08-14
```

$cd ~
$rm -r .gnome2*

```
what the code does change to home directory cd ~
remove gnome settings files rm -r .gnome2*

---

### Post by Couto on 2009-08-14
> **pmlxuser said:**
> ```

$cd ~
$rm -r .gnome2*

```
what the code does change to home directory cd ~
remove gnome settings files rm -r .gnome2*

I did it and it did nothing? :s

---

### Post by pmlxuser on 2009-08-14
ohh is that so then

[code]
rm -r .gconf
[code]

that should do it.
ps: you can back up that folder first.

---

### Post by pmlxuser on 2009-08-14
ohh is that so then

[code]
rm -r .gconf
[code]

that should do it.
ps: you can back up that folder first.

---

### Post by Couto on 2009-08-14
> **pmlxuser said:**
> ohh is that so then

```

rm -r .gconf
[code]

that should do it.
ps: you can back up that folder first.

rm: cannot remove `.gconf': No such file or directory

Btw it's [code] 
```

---

### Post by Barrucadu on 2009-08-14
> **pmlxuser said:**
> ```

$cd ~
$rm -r .gnome2*

```
what the code does change to home directory cd ~
remove gnome settings files rm -r .gnome2*

> **pmlxuser said:**
> ohh is that so then

```

rm -r .gconf

```

that should do it.
ps: you can back up that folder first.

Err, no. They won't do a thing other than wipe his GNOME settings&#8230;

If you deleted the files, you'll have to figure out what you deleted and download them. I'm not sure if there is a package which contains them all.

---

### Post by Couto on 2009-08-14
> **Barrucadu said:**
> Err, no. They won't do a thing other than wipe his GNOME settings…

If you deleted the files, you'll have to figure out what you deleted and download them. I'm not sure if there is a package which contains them all.

I've got them.. I did their command and I had to redo my panels and stuff.. :(

---

