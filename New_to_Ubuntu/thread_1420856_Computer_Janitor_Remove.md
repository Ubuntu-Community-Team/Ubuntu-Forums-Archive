---
title: "Computer Janitor Remove"
date: 2010-03-03
forum: New to Ubuntu
---

### Post by soryu on 2010-03-03
I Don't use Comp Janitor At all Can I Uninstall It Without Problems?
i use bleach bit.

---

### Post by Penguin Guy on 2010-03-03
The package you're talking about is called "[FONT="Courier New"]computer-janitor-gtk[/FONT]" - you can remove this either through Synaptic ([FONT="Courier New"]System -> Administration -> Synaptic Package Manager[/FONT]), or through [the terminal]("http://www.psychocats.net/ubuntu/terminal"):
```

sudo apt-get remove computer-janitor-gtk

```

---

### Post by soryu on 2010-03-03
do you use this program? no problems in removing it?

---

### Post by QIII on 2010-03-03
Some components that are part of the GNOME package are not good candidates to remove.  They can take other dependencies with them and break GNOME.  (This is particularly true if you use the --purge switch.)

I'm not sure if Computer Janitor is in that category.

Unless you have a compelling reason to remove it, I would simply leave it.  It doesn't take up much room and it won't bother you if you don't bother it.

---

### Post by soryu on 2010-03-03
> **QIII said:**
> Some components that are part of the GNOME package are not good candidates to remove.  They can take other dependencies with them and break GNOME.  (This is particularly true if you use the --purge switch.)

I'm not sure if Computer Janitor is in that category.

Unless you have a compelling reason to remove it, I would simply leave it.  It doesn't take up much room and it won't bother you if you don't bother it.



right, ill leave it alone. thank you.

---

