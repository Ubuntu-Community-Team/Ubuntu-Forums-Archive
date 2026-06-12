---
title: "[SOLVED] no files after unRAR"
date: 2009-01-07
forum: New to Ubuntu
---

### Post by omeriko on 2009-01-07
hey

i installed unrar-free like its said in various sites. but although now the archive manager can see inside the file, the extracted files never show up, and i can't find them in the search.

any ideas?

---

### Post by nhasian on 2009-01-07
i had some trouble with unrar-free so i removed it and installed the regular unrar and my problems disappeared.

```
sudo apt-get remove unrar-free  && apt-get install unrar
```

---

### Post by dbwalsh72 on 2009-01-07
I assume you could see files in the archive (ie, the archive is not empty). Probably the easy way around this is to re-extract the files. So first go to Places -> Home Folder. Choose File - Create Folder. Call it extract. Then reopen the archive, choose extract, browse to the folder you have just created, and then you know where they are.

We can deal with why search doesnt find the files later.

---

### Post by colau on 2009-08-16
> **omeriko said:**
> hey

i installed unrar-free like its said in various sites. but although now the archive manager can see inside the file, the extracted files never show up, and i can't find them in the search.

any ideas?
```

sudo aptitude install unrar
unrar e <filename.rar>

```

---

