---
title: "Print Directories Via Terminal"
date: 2009-06-07
forum: New to Ubuntu
---

### Post by k_squired on 2009-06-07
Is it possible to print directories via the terminal?  If so can I use sudo to print root owned folders?

---

### Post by SuperSonic4 on 2009-06-07
If you mean list the directories in a given place use ```
ls -A /path/to/file
```. ```
man ls
``` will give you more info

If you mean via a printer then you might be able to use lp

---

### Post by k_squired on 2009-06-07
Actually, is it possible to print files IN a directory as well?

---

### Post by snova on 2009-06-07
> **k_squired said:**
> Is it possible to print directories via the terminal?  If so can I use sudo to print root owned folders?

Yes.

```
sudo ls /path/to/wherever
```

> **k_squired said:**
> Actually, is it po[QUOTE=k_squired;7416524]Actually, is it possible to print files IN a directory as well?

ssible to print files IN a directory as well?[/QUOTE]

```
ls /path/to/directory
```

ls understands many useful options. Try appending **-l** to that, for example.

```
man ls
```

---

