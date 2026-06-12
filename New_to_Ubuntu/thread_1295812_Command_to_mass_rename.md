---
title: "Command to mass rename"
date: 2009-10-19
forum: New to Ubuntu
---

### Post by RealG187 on 2009-10-19
Ubuntu One has added ".u1conflict" to a bunch of my files. I need a command to rename them back. I am not posting this in the Ubuntu one section, because this can apply to more than just files affected by Ubuntu One...

```
mpg@MIKED6:~/Desktop/d$ mv *.u1conflict *
mv: target `test.u1conflict' is not a directory
```
That was unsuccessful...

---

### Post by lavinog on 2009-10-19
do this first to make sure it does what you want:
```

for x in *.u1conflict;do echo mv -v ${x} ${x%.u1conflict};done

```


then remove the echo to actually perform the operation
```

for x in *.u1conflict;do mv -v ${x} ${x%.u1conflict};done

```

---

### Post by renkinjutsu on 2009-10-19
try this:

from the terminal, cd into your Ubuntu 1 directory and paste this ```
rename 's/\.u1conflict//g' *
```

---

### Post by RealG187 on 2009-10-20
Both of the commands worked in a test directory with 2 files with .u1added to them. Can they be made recursive?

For the second one I assume
```
rename -r 's/\.u1conflict//g' *
```
would do that? Not sure for the first.

I am not even sure how those commands work, it's all foreign to me...

---

### Post by lavinog on 2009-10-20
> **RealG187 said:**
> Both of the commands worked in a test directory with 2 files with .u1added to them. Can they be made recursive?

For the second one I assume
```
rename -r 's/\.u1conflict//g' *
```
would do that? Not sure for the first.

I am not even sure how those commands work, it's all foreign to me...

you might be able to try this:
```

find -name '*.u1conflict' -exec rename 's/\.u1conflict//g' {} \;

```
I don't have any u1conflict files to test this with

explanation:
```

**find -name 'filepattern'**
#finds all files matching the filepattern (needs to be in quotes)

**-exec command {} \;**
# executes command for each file found
# {} is the placeholder for the filename passed to the command
# \; determines the end of the command

** rename 's/\.u1conflict//g' filenames**
# renames the files according to the regexp string

#one of the most common reg expressions that finds a pattern and replaces it with string: 
**'s/pattern/string/g'**

the \. is an escaped period because a period has another meaning in regexp strings
the g at the end is for global. Without it only the first match in the line is replaced.

```

---

### Post by renkinjutsu on 2009-10-21
also, rename can read from standard input if file names aren't given, so cd'ing to your ubuntu 1 directory and executing
```
find | rename 's/\.u1conflict//g'
```
would also work

---

