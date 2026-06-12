---
title: "Gnome-Utils"
date: 2009-06-26
forum: New to Ubuntu
---

### Post by blazingbazoooka on 2009-06-26
Would removing gnome-utils mess my ubuntu up? (because it says it will also remove ubuntu-desktop, which makes me kinda of cautious) 

Thanks :)

---

### Post by clonne4crw on 2009-06-26
I would guess not, because most of them are just graphical tools for configuring GNome. But I don't reccommend it. Especially since it wants to take Ubuntu-Desktop with it.

Removing ubuntu-desktop would end up removing all of the GUI components.

---

### Post by unutbu on 2009-06-26
ubuntu-desktop is a "metapackage". It is an empty package which names lots of other packages as dependencies. (One of those packages happens to be gnome-utils.)

It is okay to remove -- removing ubuntu-desktop will not remove all its dependencies. If you think of the package dependencies like a tree, ubuntu-desktop is a leaf at the top. Removing the leaf does not require sawing off the branch. However, installing the leaf requires growing the entire branch.

Thus installing ubuntu-desktop is an easy way to gain a complete Ubuntu desktop environment. But removing it does not remove the environment.

---

### Post by blazingbazoooka on 2009-06-26
I removed it... and nothing seems to have broken :p 

Thank you :)

---

### Post by kansasnoob on 2009-06-26
It will definitely hose your ability to run a distribution upgrade!

So, if you're running Jaunty and you decide to upgrade to Karmic, everything will break!

---

