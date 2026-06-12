---
title: "Running command line commands Ubuntu Server"
date: 2011-06-04
forum: New to Ubuntu
---

### Post by enenalan on 2011-06-04
Well, I just did my first Ubuntu Server install.  Everything went swimmingly, but, um.....  How do you actually execute list and change directory commands?  X-(  

Thanks!!!!!!!

---

### Post by papibe on 2011-06-04
There's lots of tutorials around, just google "bash tutorial" or "bash beginners". Anyway, here's a very useful ebook you can download: [The Linux Command Line]("http://linuxcommand.org/tlcl.php").

Regards.

---

### Post by AlphaLexman on 2011-06-04
To list files use:```
ls
```
See 'man ls'

To change directories, use ```
cd dirname/
```
See 'man bash'

---

### Post by enenalan on 2011-06-04
The problem is that I'm popping in ls, cd, etc. but it's not returning anything......  I'm halfway decent at bash - used it in the desktop edition for a couple of years - but in Ubuntu Server edition, I log in as myself, can run things like apt-get, but I can't seem to do basic file manipulation, copy, directory lists, or anything like that.......

---

### Post by wojox on 2011-06-04
There might not be anything in your /home directory that's visible. Try:

```
ls -al
```

[File & Directory Commands]("https://help.ubuntu.com/community/UsingTheTerminal#File%20&%20Directory%20Commands")

---

### Post by enenalan on 2011-06-04
Thanks wojox, that did it.....  And my last bothersome newbie post of the night - so if I can't see any file structure, how exactly do I access the rest of my file system?  E.g. like get into the etc directory?

---

### Post by enenalan on 2011-06-04
Never mind.  Figured it out.  I don't know what the heck I was doing earlier......  :-/

---

