---
title: "Brasero/GnomeBaker won't work"
date: 2011-01-13
forum: New to Ubuntu
---

### Post by itsols on 2011-01-13
I'm trying to copy a CD with audio. The discs play ok. But I can't copy it.

Brasero gives this error in the logs when I try to copy:

Checking session consistency (brasero_burn_check_session_consistency brasero-burn.c:1744)
Unsupported type of task operation
Session error : An internal error occurred (brasero_burn_record brasero-burn.c:2862)

Any ideas please?

---

### Post by Alan A on 2011-01-15
Just hit the same problem.

I think this caused by a missing library. see :-

[https://bugs.launchpad.net/ubuntu/+source/brasero/+bug/529696]("https://bugs.launchpad.net/ubuntu/+source/brasero/+bug/529696")

Try installing cdrdao from the repository - worked for me.

```
sudo apt-get install cdrdao
```

---

### Post by itsols on 2011-01-15
Thanks Alan for your inputs, but that bug is an old one we had since version 9.04.

Anyway, maybe a reinstallation of cdrdao can make a difference.

Cheers!

---

