---
title: "command for displaying names of folders"
date: 2010-01-04
forum: New to Ubuntu
---

### Post by bobin on 2010-01-04
and sub-folders and the files in subfolders and hidden folders

---

### Post by Shippou on 2010-01-04
```

ls -R

```

Take note, this produces A LOT of output.

For later viewing, save in a text file:

```

ls -R > <filename_here>.txt

```

---

### Post by oldos2er on 2010-01-04
```
ls -la | more
``` or if you prefer less ```
ls -la | less
```

Oops, should've added 'R' too.

---

### Post by mcduck on 2010-01-04
You can also just pipe the output directly to some reader, for example:

```
ls -R | less
```

This allows you to scroll up & down the output.

---

