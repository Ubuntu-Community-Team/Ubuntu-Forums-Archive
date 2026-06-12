---
title: "[SOLVED] how do you delete directory?"
date: 2008-12-17
forum: New to Ubuntu
---

### Post by aszxcv on 2008-12-17
how do you delete directory?

---

### Post by super.rad on 2008-12-17
```
rm -r /location/of/directory
```

---

### Post by taurus on 2008-12-17
If a directory is empty, you would do

```
rmdir directory_name
```
And if it is not and you want to remove everything in it, then you would do

```
rm -rf directory_name
```

---

### Post by starcannon on 2008-12-17
From the gui you simply r-click and send to trash.
From the cli you use the rm command with the -r flag to make it recurse into the directory; that said, you should use rm with the -r flag very carefully, point it the wrong way and precious data will be gone in the blink of an eye. Best bet is to:
```
man rm
```
read twice delete once.

---

