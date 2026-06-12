---
title: "Lucid - what printing package(s) needed?"
date: 2010-09-29
forum: New to Ubuntu
---

### Post by cavh on 2010-09-29
Hi everyone,

I did a minimal install of Lucid (32 bit) - so minimal that I have no printing available other than 'print to file'. What's the recommended way of adding print functionality to Lucid? Is CUPS still used?

Thanks in advance.

---

### Post by andrewthomas on 2010-09-29
> **cavh said:**
>  Is CUPS still used?

Thanks in advance.
yes

---

### Post by cavh on 2010-09-29
Thanks Andrew. Is it just a case of installing the cups-client and cups-common packages then? What do I need to get the GUI to set up a new (network) printer?

---

### Post by cavh on 2010-09-29
Solved - all I had to do was

```
sudo apt-get install cups system-config-printer-gnome
```

in a terminal

---

