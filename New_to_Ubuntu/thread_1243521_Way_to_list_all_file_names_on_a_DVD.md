---
title: "Way to list all file names on a DVD?"
date: 2009-08-18
forum: New to Ubuntu
---

### Post by paker on 2009-08-18
A data DVD has folders and subfolders. Is there a way to see (list or print) all files without clicking on individual folder and subfolder? Thanks.

---

### Post by wizard10000 on 2009-08-18
> **paker said:**
> A data DVD has folders and subfolders. Is there a way to see (list or print) all files without clicking on individual folder and subfolder? Thanks.

Sure  :)

From a terminal window you'd change to the directory you want listed and type

```
ls -R
```

You could even redirect the output to a text file and then read or print that.

```
ls -R > */path/to/filename.txt*
```

If you read the man page for ls you'll find you can really customize the output if you want.

cheers -

---

### Post by PGScooter on 2009-08-18
I like wizard's way better, but just to give you another option:
```
find
```

---

### Post by philinux on 2009-08-18
> **paker said:**
> A data DVD has folders and subfolders. Is there a way to see (list or print) all files without clicking on individual folder and subfolder? Thanks.

In nautlilus change to the view from icon to list.

---

### Post by paker on 2009-08-18
Thanks. "ls -R > /pathname/to/filename.txt" worked beautifully. Actually, I used filename.ods for spreadsheet format. Thanks a lot folks.

---

