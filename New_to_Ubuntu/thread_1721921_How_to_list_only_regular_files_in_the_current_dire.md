---
title: "How to list only regular files in the current directory?"
date: 2011-04-05
forum: New to Ubuntu
---

### Post by adit on 2011-04-05
What command should I issue to list only regular files in the current directory?  I know this can be achieved by passing the output of 'ls -l' to a perl script to extract the regular files.  Is there a built-in way? (by passing some arguments to ls)

---

### Post by deathadder on 2011-04-05
> **adit said:**
> What command should I issue to list only regular files in the current directory?  I know this can be achieved by passing the output of 'ls -l' to a perl script to extract the regular files.  Is there a built-in way? (by passing some arguments to ls)
I'm not sure if you can do it with ls, without piping to another script / app. But if you want to find all of the regular files in the current directory you can use find:
```
find ./ -type f -maxdepth 1
```
The maxdepth argument stops find from descending through the filestructure, while type takes the followings arguments:
> 
-type c
              File is of type c:

              b      block (buffered) special

              c      character (unbuffered) special

              d      directory

              p      named pipe (FIFO)

              f      regular file

              l      symbolic link

              s      socket

              D      door (Solaris)


---

### Post by deathadder on 2011-04-05
Hmm, so it appears you can do it with ls by passing the --file-type argument, this appeands an @ to symbloic links and a slash to directory names. You would then need to drop those characters using grep.
```
ls --file-type | grep -v @ | grep -v /
```
I'm not sure if there's other characters it addeds depending on what's in the directory. 

The find command is probably the quicker / cleaner solution though.

---

