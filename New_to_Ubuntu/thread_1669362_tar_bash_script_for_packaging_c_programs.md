---
title: "tar bash script for packaging c programs"
date: 2011-01-17
forum: New to Ubuntu
---

### Post by Gralamin on 2011-01-17
Since I commonly need to wrap up c programs for submission for school, I created a bash script to do so:

```
find -type f -regextype 'egrep' -regex '\.\/(.+\.[ch]|[Mm]akefile|README|.+\.html|.+\.css)' ! -regex '(.+memwatch\.[ch]|.+DEBUG\/.+)' | xargs tar cvf submit.tar
```
(Find all files that are .c or h, the Makefile, readme, html, css; and that are not memwatch or in the DEBUG directory).

The only issue is that it creates a directory in the tar named ".". I would like to remove this directory in the same command, and was trying to figure out how to use sed to do so.

Thanks for any help.

Sample output without the submit.tar:
```
gralamin@gralamin-laptop:~/test$ find -type f -regextype 'egrep' -regex '\.\/(.+\.[ch]|[Mm]akefile|README|.+\.html|.+\.css)' ! -regex '(.+memwatch\.[ch]|.+DEBUG\/.+)'
./global.h
./size.h
./output.c
./report.html
./output.h
./debug.h
./README
./style.css
./Makefile

```

---

### Post by kroq-gar78 on 2011-01-17
I have this problem too when trying to move source code between my computers. What I did to package was 
```
tar -jcvf src.tar.bz2 ./*
```I had to remove the './' part for  it to remove that '.' directory in the archive. I'm not very familiar  with find (I never use it) but if you have './' in there to find files  in the current directory, remove that, and your problem might be solved.

---

### Post by Gralamin on 2011-01-17
> **kroq-gar78 said:**
> I had to remove the './' part for  it to remove that '.' directory in the archive. I'm not very familiar  with find (I never use it) but if you have './' in there to find files

The './' is part of find's output, unfortunately.

---

