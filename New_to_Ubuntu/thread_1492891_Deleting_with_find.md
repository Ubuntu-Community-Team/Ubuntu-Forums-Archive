---
title: "Deleting with find"
date: 2010-05-25
forum: New to Ubuntu
---

### Post by Ozymandias_117 on 2010-05-25
Hi, I was hoping someone could explain to me what the difference between ```
find ~ -name "*~" -exec rm {} +
``` and ```
find ~ -name "*~" -delete
``` is.

Doing a few small scale tests, they seem to come out with the same result, yet all the help forums tell people -exec rm {} +. Wouldn't it be simpler to just say -delete?

---

### Post by Superkoop on 2010-05-25
Based on my readings of the man page, it seems exec rm {} + is more safe than delete.

```
 -delete
              Delete files; true if removal succeeded.  If the removal failed,
              an  error message is issued.  If -delete fails, find's exit sta&#8208;
              tus will be nonzero (when it eventually exits).  Use of  -delete
              automatically turns on the -depth option.

              Warnings:  Don't  forget that the find command line is evaluated
              as an expression, so putting -delete first will make find try to
              delete everything below the starting points you specified.  When
              testing a find command line that you later intend  to  use  with
              -delete,  you should explicitly specify -depth in order to avoid
              later surprises.  Because -delete  implies  -depth,  you  cannot
              usefully use -prune and -delete together.

```

```
 -exec command {} +
              This  variant  of the -exec action runs the specified command on
              the selected files, but the command line is built  by  appending
              each  selected file name at the end; the total number of invoca&#8208;
              tions of the command will  be  much  less  than  the  number  of
              matched  files.   The command line is built in much the same way
              that xargs builds its command lines.  Only one instance of  `{}'
              is  allowed  within the command.  The command is executed in the
              starting directory.
```

Source: ```
man find
```

---

### Post by Ozymandias_117 on 2010-05-25
I agree that's what it looks like, except I can't seem to find any differences in the files it finds between ```
find / -name "*~"
``` and ```
find / -name "*~" -depth
``` which is what it appears to be saying is why it would be dangerous. That -depth should somehow find more files.

---

