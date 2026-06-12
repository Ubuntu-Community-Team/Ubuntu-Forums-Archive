---
title: "'ldconfig' not found on PATH"
date: 2010-02-05
forum: New to Ubuntu
---

### Post by fyregirl on 2010-02-05
I think I may have deleted something by accident, although I am not sure how.

I have been trying to get a Vodaphone Mobile internet key to work in Ubuntu, but because I cannot access internet on this machine at the moment, I have been downloading all the required packages to another machine and transferring and installing them one by one (I looked for a simple way, but couldn't find one - everything assumed I should be able to download directly to my machine).

Anyway, everything was installing, package by package, when I hit a hiccup, and the following appeared in terminal.
dpkg: 'ldconfig' not found on PATH
dpkg: 1 expected program(s) not found on PATH
NB: root's PATH should usually contain /usr/local/sbin, /usr/sbin and /sbin.

Now nothing is happening, and I have no idea what I have done wrong or how to fix it.  I did google extensively before posting here.

I am by the way, a raw beginner, so please, if anyone can help, don't assume I have a lot of background knowledge.

I am not sure what else anyone would need to know in order to help me, but please tell me, if you need more detail.

Thanks

---

### Post by Bachstelze on 2010-02-05
Please do

```
echo $PATH
```

And paste the results.

---

### Post by fyregirl on 2010-02-11
sorry it's taken me so long to reply...my internet access is extremely limited right now.

Here is what came up when I typed that command....

/home/fyregirl/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games


Any ideas?

---

