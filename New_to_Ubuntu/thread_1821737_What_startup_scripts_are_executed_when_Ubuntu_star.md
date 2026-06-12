---
title: "What startup scripts are executed when Ubuntu starts?"
date: 2011-08-09
forum: New to Ubuntu
---

### Post by pkirkaas on 2011-08-09
Hi, 

When you log into Ubuntu, what user initialization files are executed by default?  .profile, .bashrc, ??? And what files when running the default terminal?

I want to initialize some things for my entire Ubuntu environment (like, set some environment variables), and other things only when I start a bash terminal session (for example, my terminal prompt).

Thanks for any info.

---

### Post by cj13579 on 2011-08-09
If you just want to set a variable when you launch a terminal window and have it last for the duration of that terminal session just use export, e.g:

```
export VARIABLE=*value*
```

---

### Post by Paddy Landau on 2011-08-09
The file .bashrc in your home folder.

---

