---
title: "Bulk Renaming"
date: 2009-10-10
forum: New to Ubuntu
---

### Post by Firerouge on 2009-10-10
Could someone please help me with the following problem.

I have a folder with a few thousand files. All of them start with a series of 4 digits a space a dash a space and then there name.

Example:
0023 - Awesome Name 1.Extension

I wish to remove all the numbers, spaces and dash before the actual name. Some of them also have dashes and numbers in the name, just to let you know.

Any Help would be appreciated.

---

### Post by sgosnell on 2009-10-10
The easiest way would be to write a C or Perl program to do it.  You should be able to write a script that will open each file in turn, truncate the name appropriately, and then rename the file.  I haven't done a lot of scripting, and I don't have the ambition to look up all the required commands, but it should be possible.

---

### Post by Bachstelze on 2009-10-10
```
rename -n 's/^[0-9]+\ -\ //' *.ext
```

it will not rename anything, just tell you what would be done. If it looks good, remove -n.

```
firas@iori ~ % ls -l *.ext
-rw-r--r-- 1 firas firas 0 2009-10-11 01:22 0123 - filename.ext
-rw-r--r-- 1 firas firas 0 2009-10-11 01:24 0125 - filename0125 - .ext
firas@iori ~ % rename -n 's/^[0-9]+\ -\ //' *.ext
0123 - filename.ext renamed as filename.ext
0125 - filename0125 - .ext renamed as filename0125 - .ext
firas@iori ~ % rename 's/^[0-9]+\ -\ //' *.ext
firas@iori ~ % ls -l *.ext
-rw-r--r-- 1 firas firas 0 2009-10-11 01:22 filename.ext
-rw-r--r-- 1 firas firas 0 2009-10-11 01:24 filename0125 - .ext

```

---

### Post by diesch on 2009-10-10
I prefer mmv (not installed by default) over rename as mmv does collision checking before it renames anything.

```

mmv '[0-9][0-9][0-9][0-9] - *' '#5'

```

---

### Post by uncannybuzzard on 2009-10-10
i prefer using a gui for renaming (one of the few applications where i think a gui is superior). check out thunar bulk rename and... pyrename i think it's called.

---

