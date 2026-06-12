---
title: "Setting an Environment Path"
date: 2010-05-11
forum: New to Ubuntu
---

### Post by B34ST1Y on 2010-05-11
I was wondering how you would go about setting a path in shell.

For example, every time I issue the command "blah" What I really want it to do, is issue the command  "/usr/bin/home/blah"


can someone enlighten me?

---

### Post by B34ST1Y on 2010-05-11
I figured it out, for anyone who stumbles onto this thread later on - 

to set an environment variable in Linux, you simple get to a prompt, and type the name of the variable, followed by an = sign. Make sure you append it to the end of the already set variable.

Here is some sample code:

```

#$PATH
/data/data/com.teslacoilsw.quicksshd/dropbear:/usr/bin:/usr/sbin:/bin:/sbin:/system/sbin:/system/bin:/system/xbin:/system/xbin/bb:/data/local/bin:/data/data/com.google.ase/perl: not found
#PATH=/data/data/com.teslacoilsw.quicksshd/dropbear:/usr/bin:/usr/sbin:/bin:/sbin:/system/sbin:/system/bin:/system/xbin:/system/xbin/bb:/data/local/bin:/data/data/com.google.ase/perl:ADDINGMYVARIABLE/RIGHT/HERE/TO/THE/LIST


```

viola!

---

