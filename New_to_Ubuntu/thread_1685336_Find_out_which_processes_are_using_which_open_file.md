---
title: "Find out which processes are using which open files?"
date: 2011-02-10
forum: New to Ubuntu
---

### Post by nosehat on 2011-02-10
In Ubuntu 10.10, how would I find out which running processes have opened which files on my system?

I see that I can list the running processes using the tool on the menu System/Administration/System Monitor, but how can I search for which files they have opened?

I am trying to troubleshoot a problem of being unable to close a truecrypt file system, detailed here [http://ubuntuforums.org/showthread.php?t=1680508](http://ubuntuforums.org/showthread.php?t=1680508)

Thanks!

---

### Post by Rubi1200 on 2011-02-11
> man lsof should get you going.

---

### Post by jroa on 2011-02-11
I am not sure if this will help, but this command will show you a lot of detail about processes running.

```
ps -ef
```

When you find what you are looking for, you can kill it.

---

