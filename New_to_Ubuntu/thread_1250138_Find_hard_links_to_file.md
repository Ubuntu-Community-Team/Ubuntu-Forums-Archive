---
title: "Find hard links to file"
date: 2009-08-26
forum: New to Ubuntu
---

### Post by Paddy Landau on 2009-08-26
Suppose I have a file with hard links; for example:
```
$ touch ~/afile
$ ln ~/afile /someplace/bfile
$ ln ~/afile /cfile
```In this example, I have a file with three hard links, specifically [FONT=Courier New]~/afile[/FONT], [FONT=Courier New]/someplace/bfile[/FONT] and [FONT=Courier New]/cfile[/FONT].

Is there a way to list all the hard links that a file has? For example, if I were to use:
```
ls /someplace/bfile
```Is there a way that I can discover [FONT=Courier New]~/afile[/FONT] and [FONT=Courier New]/cfile[/FONT]?

---

### Post by Gen2ly on 2009-08-26
Since all links are treated as files, Paddy, there really isn't a  way to be able to know all links except by searching for them.  To find all symbolic links you could do:

```
find / -type l -exec ls -l {} \;
```

To find your specific link to a specific folder, grep your original directory with a pipe on the end.

---

### Post by DaithiF on 2009-08-26
actually i believe hardlinks show up in find as regular files type f, rather than symbolic links, type l.  
You can find files which have more than 1 hardlink by doing:
```
find -type f -links +1

```
also, when doing ls -l, the 2nd column shows the number of hardlinks to that file.

---

### Post by psycho on 2009-08-26
Since ls -i gives the unique inode of a file, you could use this to find the inode of one of your hardlinked files. Then, you could search for this inode. So if the inode was 20000, you could do something like:

```
ls -iR directories/to/search | grep 20000
```

---

### Post by Paddy Landau on 2009-08-26
Thank you all for your answers.

@Gen2ly: These are hard links, not symbolic links. Thanks for the idea, though, for when I next need to look for a symbolic link.

@DaithiF and psycho:

Now I know what *inode* means!

Combining your two answers, here's the simplest answer. (Obviously, change the starting directory as appropriate.)
```
find / -samefile ~/afile
```I shall mark this thread as solved.

---

