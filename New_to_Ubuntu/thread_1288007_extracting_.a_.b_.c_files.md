---
title: "extracting .a .b .c files?"
date: 2009-10-10
forum: New to Ubuntu
---

### Post by sandyd on 2009-10-10
i just got some compressed archives from a friend who wanted to use my comp as a backup center.

however, the extensions are weird and i can't open them

their in the forumat
file.a
file.b
file.c....

and i have no idea on how to open them

help?

---

### Post by Bachstelze on 2009-10-10
Try

```
file filename.a
```

it could give you some input about them.

---

### Post by damis648 on 2009-10-10
Just try opening them with archive manager, see if it can do it. It may be able to determine the file type based on the mime type.

---

### Post by sandyd on 2009-10-10
hmm...
its a data archive.

and just also noticed something, my mistake.

the extension is 
filename.7z.__a
filename.7z.__b
filename.7z.__c

if that helps.

---

### Post by Bachstelze on 2009-10-10
Aha, it's 7z. So

```
7zr x filename.7z.__a
```

---

### Post by Vaphell on 2009-10-10
looks like some 7z stuff and file-roller should be able to open it

---

### Post by sandyd on 2009-10-10
hmm... no dice..
```

7-Zip (A) 9.04 beta  Copyright (c) 1999-2009 Igor Pavlov  2009-05-30
p7zip Version 9.04 (locale=en_CA.UTF-8,Utf16=on,HugeFiles=on,2 CPUs)

Processing archive: bkup-jennifer.7z.__a

Error: Can not open file as archive


```

---

### Post by diesch on 2009-10-10
Looks like archives created by 7z.

Install p7zip-full, then unpack with ```
7z x filename.7z.__a
```

---

### Post by sandyd on 2009-10-10
P.S.

when i open it as a gzip file, it gives me a file named 7z.__a.uncompressed. 
huh?

---

### Post by sandyd on 2009-10-10
found it.

someone used ffsj file splitter.....

---

