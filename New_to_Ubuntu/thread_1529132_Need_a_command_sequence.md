---
title: "Need a command sequence"
date: 2010-07-11
forum: New to Ubuntu
---

### Post by nnjond on 2010-07-11
Hi,

I need to fresh install and it would be convenient if i knew the commands to

Search /home for every file ive saved since 02_06_10, and then copy to a memory stick.

Can you help me please?

---

### Post by Darkness Des on 2010-07-11
You might want to look into the *find* command, that appears to be what's best.

---

### Post by kaibob on 2010-07-12
> **nnjond said:**
> Hi, I need to fresh install and it would be convenient if i knew the commands to Search /home for every file ive saved since 02_06_10, and then copy to a memory stick.

The following should do what you want. It finds files that have been modified since February 6, 2010 (156 days ago) and copies these files from the source directory to the target directory.

```
find /source/directory -mtime -156 -type f -exec cp '{}' /target/directory ';'
```

As written, this command copies all files to a single directory within the target directory. You may want to use the --parents option with the copy command to recreate the source directory structure within the target directory.

---

