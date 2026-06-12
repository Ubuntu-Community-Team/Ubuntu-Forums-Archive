---
title: "Command not found?"
date: 2010-04-11
forum: New to Ubuntu
---

### Post by plasticM on 2010-04-11
Hi there,

I'm sure this is probably the most stupid question ever and I'm missing something obvious, but here goes.

From my terminal:
```
me@Computer:/var/lib/gems/1.8/gems/iplayer-dl-0.1.19/bin$ ls
iplayer-dl  iplayer-dl-gui
me@Computer:/var/lib/gems/1.8/gems/iplayer-dl-0.1.19/bin$ iplayer-dl
iplayer-dl: command not found
```

The file in question is executable and I'm actually in the directory!  How can the command not be found?!!!

I would be very grateful for where I'm going wrong here, especially since the same thing works fine on my laptop (exact same setup).

---

### Post by lisati on 2010-04-11
Try: ```
./iplayer-dl
```

Ubuntu, by default, doesn't look in the current directory for programs to run. Adding "./" to the front overrides this.

---

### Post by ankit.vader on 2010-04-11
Can you show the output for ls -l

---

### Post by 3rdalbum on 2010-04-11
> **lisati said:**
> Try: ```
./iplayer-dl
```

Ubuntu, by default, doesn't look in the current directory for programs to run. Adding "./" to the front overrides this.

+1. You could also add that directory to $PATH.

---

### Post by plasticM on 2010-04-11
Hi,

Thanks for the very quick replies.  I would have thought the current directory would be the only obvious place to look (?).  So where does it look?  Just the path? And if so what's the easiest way to add this location (and similar ones) to the path.

Incidentally the file I needed was the one at /var/lib/gems/1.8/bin/ to make the requires work, not the location specified previously.

Thanks.

---

### Post by codemaniac on 2010-04-11
To add /var/lib/gems/1.8/bin/ to your existing path variable put this in the console..
PATH=$PATH:/var/lib/gems/1.8/bin/

to make that change permanent put the above line into your bashrc file..

---

### Post by oldos2er on 2010-04-11
> **plasticM said:**
> Hi,

Thanks for the very quick replies.  I would have thought the current directory would be the only obvious place to look (?).  So where does it look?  Just the path? 

 Yes, just the path, which by design does not include the current directory. You can either use ./file, as mentioned earlier, or an absolute path, e.g. /some/path/to/an/executable/file.

---

