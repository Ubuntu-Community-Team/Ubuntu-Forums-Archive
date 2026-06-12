---
title: "uninstalling frostwire"
date: 2009-05-04
forum: New to Ubuntu
---

### Post by fminmexico on 2009-05-04
I am trying to uninstall frostwire,it does not show in addremove or in synaptic package manager.I tried to delete the folder but delete was grayed out.How do I uninstal it
   fminmexico.

---

### Post by michy99 on 2009-05-04
How did you install it? Did you download a .deb file or did you compile it from source code?

---

### Post by fminmexico on 2009-05-04
> **michy99 said:**
> How did you install it? Did you download a .deb file or did you compile it from source code?

I downloaded it as deb and it automatically installed.
    fminmexico

---

### Post by fooman on 2009-05-04
if it was a .deb file,  then you should be able to uninstall it using synaptic.

go to system > administration > synaptic package manager

when it opens,  click on "search" and type frostwire into the box.  when the search results pop up,  right-click on frostwire and choose "mark for removal" from the menu.

---

### Post by fminmexico on 2009-05-04
> **fooman said:**
> if it was a .deb file,  then you should be able to uninstall it using synaptic.

go to system > administration > synaptic package manager

when it opens,  click on "search" and type frostwire into the box.  when the search results pop up,  right-click on frostwire and choose "mark for removal" from the menu.

as I said in my previous post it does not show in synaptic.
   fminmexico.

---

### Post by michy99 on 2009-05-04
Try this:

```
sudo dpkg --remove frostwire
```

---

### Post by Sarai the Geek on 2009-05-04
> **michy99 said:**
> Try this:

```
sudo dpkg --remove frostwire
```

If that doesn't work, try this:

```
dpkg -l '*frost*'
```

It'll run a wildcard search for all packages with frost in their name- shouldn't be too many. ;)

Once you've got the exact package name use the command suggested by michy99 to nuke it.

---

### Post by fminmexico on 2009-05-04
> **michy99 said:**
> Try this:

```
sudo dpkg --remove frostwire
```

thank you that worked
  fminmexico

---

