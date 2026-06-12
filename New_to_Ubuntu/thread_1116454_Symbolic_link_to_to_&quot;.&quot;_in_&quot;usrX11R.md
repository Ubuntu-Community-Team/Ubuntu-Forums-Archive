---
title: "Symbolic link to to &quot;.&quot; in &quot;/usr/X11R6/bin/X11&quot;"
date: 2009-04-04
forum: New to Ubuntu
---

### Post by victorbrca on 2009-04-04
This is the first time I notice this. Could not find anything on Google. Is there a reason for this sym link?

```
/usr/X11R6/bin/X11 $ ls -l X*
-rwsr-sr-x 1 root root    7460 2008-06-25 16:53 X
lrwxrwxrwx 1 root root       1 2008-07-13 02:36 X11 -> .
-rwxr-xr-x 1 root root 1693212 2008-06-12 21:22 Xorg
```


Vic.

---

### Post by dusan.saiko on 2009-04-05
I have this symlink as well.
Actually, 

```

/usr/X11R6$ ls -la
total 8
drwxr-xr-x  2 root root 4096 2009-03-24 11:38 .
drwxr-xr-x 12 root root 4096 2009-04-01 08:53 ..
lrwxrwxrwx  1 root root    6 2009-04-01 07:57 bin -> ../bin

```

Seems like all /usr/X11R6/bin was moved to /usr/bin and that symlink is path compatibility for some apps,

all of these will work:

/usr/X11R6/bin/startx
/usr/bin/startx
/usr/bin/X11/startx
/usr/X11R6/bin/X11/startx

---

### Post by victorbrca on 2009-04-06
But that's a different sym link. It has nothing to do with what I had pointed.

The problem with the sym link I had pointed is that something like this could happen:

```
$ pwd
/usr/X11R6/bin/X11/X11/X11/X11/X11/X11/X11/X11/X11/X11/X11/X11/X11/X11/X11/X11/X11/X11/X11/X11/X11/X11/X11/X11/X11/X11/X11/X11/X11/X11/X11/X11/X11/X11/X11/X11/X11/X11/X11
```

---

