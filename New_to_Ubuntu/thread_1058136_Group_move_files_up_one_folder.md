---
title: "Group move files up one folder"
date: 2009-02-02
forum: New to Ubuntu
---

### Post by NEUR0M4NCER on 2009-02-02
Hi - file structure is like this:
```

Parent Folder>File1 Folder>File1.abc
                           File1.xyz
              File2 Folder>File2.abc
                           File2.xyz
              File3 Folder>File3.abc
                           File3.xyz

```
Is there any way of moving all of the files into the Parent Folder quickly?

---

### Post by squaregoldfish on 2009-02-02
I'm winging it slightly here, but try this (note - I haven't tested it!):

```
cd <parentDir>
find . -type f -exec mv {} \;
```

The find -type f will descend into the directory tree looking for files only. The -exec flag will move the files to the current directory.

Hope this helps
Steve.

---

### Post by NEUR0M4NCER on 2009-02-02
Hi - thanks for the suggestion. It tried the above, but it gives error
```

find: missing argument to `-exec'

```

---

### Post by squaregoldfish on 2009-02-02
Oops - the find command should end with \; and not .;

I'll edit the original message.

Steve.

---

### Post by jerome1232 on 2009-02-02
wouldn't this move all files in the current directory up one directory (is that what your asking?)

```
mv * ../
```

---

