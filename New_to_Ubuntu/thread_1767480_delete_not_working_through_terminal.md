---
title: "delete not working through terminal"
date: 2011-05-25
forum: New to Ubuntu
---

### Post by soylentcola on 2011-05-25
So in a foolish oversight, I extracted something as root through the terminal, but now that I'm trying to delete the directory (I no longer need it), the "rmdir -r" command isn't working, as it's telling me that the "-r" is an invalid option, yet, after checking the man page, it shows up!

Is there some link I'm missing here or am I just being dumb?

---

### Post by aeronutt on 2011-05-25
If it has root permissions, it may take: sudo rmdir -r

If that doesn't work, what does "which rmdir" show?

---

### Post by soylentcola on 2011-05-25
> **aeronutt said:**
> If it has root permissions, it may take: sudo rmdir -r

If that doesn't work, what does "which rmdir" show?Tried that as well, still nothing. :(

which rmdir gave me this:

```
tai@tai-K60IJ:~$ which rmdir
/bin/rmdir
```

---

### Post by greencookie on 2011-05-25
Hello.

rmdir does not have a -r flag.

[[link]("http://ss64.com/bash/rmdir.html")] 

Maybe you confused it with rm?

To recursively remove a folder and its contents you can use ```
 rm -rf *foldername*
```. But I suggest you be VERY careful while executing that command!! Please read on the man pages :) Cheers.

---

### Post by soylentcola on 2011-05-26
> **greencookie said:**
> Hello.

rmdir does not have a -r flag.

[[link]("http://ss64.com/bash/rmdir.html")] 

Maybe you confused it with rm?

To recursively remove a folder and its contents you can use ```
 rm -rf *foldername*
```. But I suggest you be VERY careful while executing that command!! Please read on the man pages :) Cheers.Worked like a charm! Thanks a lot! :D

---

