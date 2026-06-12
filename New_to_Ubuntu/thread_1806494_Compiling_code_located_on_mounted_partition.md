---
title: "Compiling code located on mounted partition"
date: 2011-07-17
forum: New to Ubuntu
---

### Post by srivatsacsn on 2011-07-17
Hi,
I'm trying to compile C++ source files located on my mounted partition, but every time the compilation fails with 'Permission denied' message. 
Steps that I took:
1. Run g++ as sudo (also, invoke codeblocks with gksudo)
2. Use lsattr to print attributes gives

```
sudo lsattr /media/<pathtofile>/mytest.cpp
lsattr: Function not implemented While reading flags on /media/<pathtofile>/mytest.cpp
``` Could anybody please tell me -
1. Are there any options that the partition has to be mounted with?  (I currently mount it by visiting the appropriate partition name in Places menu.
2. If there are any steps/workarounds to this?

---

### Post by mikewhatever on 2011-07-17
Can you tell us what's the file system of that partition. It looks like the function doesn't like the flags of mytest.cpp, and the file system could be the cause.

---

### Post by trozamon on 2011-07-17
Who owns the files in the partition? You or the root account?

To figure out, run:

```
ls -lRA /path/to/partition
```

---

### Post by srivatsacsn on 2011-07-21
> **mikewhatever said:**
> Can you tell us what's the file system of that partition. It looks like the function doesn't like the flags of mytest.cpp, and the file system could be the cause.

It is an NTFS partition.

---

### Post by srivatsacsn on 2011-07-21
> **trozamon said:**
> Who owns the files in the partition? You or the root account?

To figure out, run:

```
ls -lRA /path/to/partition
```

Running ls with the options mentioned produces the following output:
```
-rw------- 1 srivatsa srivatsa 34244 2011-07-17 17:55 /path/to/partition/mytest.cpp
```
I tried changing the permission with 
```
sudo chmod +x --verbose /path/to/file
mode of `/path/to/file' changed to 0711 (rwx--x--x)

```
When I check the permissions of the file again using the ls -lRA, the permissions are shown to be  unchanged.

---

### Post by The Cog on 2011-07-21
NTFS cannot store unix style permissions flags. It's probably best to move the whole source directory to a proper unix type filesystem.

---

