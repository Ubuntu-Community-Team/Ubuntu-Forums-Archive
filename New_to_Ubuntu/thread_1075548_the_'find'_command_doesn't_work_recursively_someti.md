---
title: "the 'find' command doesn't work recursively sometimes"
date: 2009-02-20
forum: New to Ubuntu
---

### Post by munishvit on 2009-02-20
$ find directory_list -option criteria -print
Find command is suppose to search the given directory recursively. But, it doesn't, if your pwd happens to be that directory or any of its subdirectories.
cd /media/disk
find /media/disk -name *.exe -print
What could be the reason behind this? or m i doing some mistake?

---

### Post by zacktu on 2009-02-20
The find command is working properly, as /media is owned by root.

---

### Post by munishvit on 2009-02-20
> **zacktu said:**
> The find command is working properly, as /media is owned by root.

You please try:
cd ~
mkdir test
mkdir test/dir1 test/dir2
cat > virus.exe	//then write something followed by Ctrl-D
cd test
cp virus.exe dir1/virus1.exe
cp virus.exe dir2/virus2.exe
right now pwd is ~/test
find ~/test -name *.exe -print	//it shows only virus.exe ***
now try
cd ..
find ~/test -name *.exe -print	//now it shows all d three

*** this time we don't require root privilege....even then its not behaving recursively

---

### Post by snova on 2009-02-20
> **munishvit said:**
> find /media/disk -name *.exe -print

Quote *.exe:

```
find /media/disk -name '*.exe' -print
```

Otherwise, the shell will perform globbing, and mess up the command to something like this:

```
find /media/disk -name virus.exe -print
```

Or even something invalid to the command:

```
find /media/disk -name virus1.exe virus2.exe something.exe -print
```

---

### Post by munishvit on 2009-02-22
> **snova said:**
> Quote *.exe:

```
find /media/disk -name '*.exe' -print
```

Otherwise, the shell will perform globbing, and mess up the command to something like this:

```
find /media/disk -name virus.exe -print
```

Or even something invalid to the command:

```
find /media/disk -name virus1.exe virus2.exe something.exe -print
```

Ya, you are right, i figured out the same thing after checking unix complete reference
when you use a wildcard with the -name option, you have to quote it. 
$ find /home/munish/test -name '*.exe' -print
If you don't , the filename matching process would replace *.exe with the names of all of the files in the present working directory (pwd) that ends with .exe  ending.
anyway...thnx

---

### Post by zacktu on 2009-02-22
I guess I would not have made test as the root of my search.  The command sequence

cd
find . -name *.exe

finds all three of your files.

---

