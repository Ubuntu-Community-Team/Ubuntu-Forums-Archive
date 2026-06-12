---
title: "Trouble installing intltool /  Rhythmbox"
date: 2009-06-03
forum: New to Ubuntu
---

### Post by AlwaysBenji on 2009-06-03
Hello New Friends,


I just installed EasyPeasy onto my eeePC and it's running nicely and does everything I need it to except I am having trouble installing Rhythmbox, it tells me intltool is too old, to install 0.35.0 or later. So I downloaded the tarball for 0.40.6 and tried to install that but after running "make install" (which is the final step if I understood the install directions correctly), I was told the following by terminal:


mkdir: cannot create directory `/usr/local/share/man/man8': Permission denied
make[2]: *** [install-man8] Error 1
make[2]: Leaving directory `/home/user/Programs/intltool-0.40.6/doc'
make[1]: *** [install-am] Error 2



What is going on? How can I fix this problem? I want Rhythmbox as it's supposedly fantastic for Last.Fm. I hope somebody can help. I have used Linux a little in the past but I am still not savvy at this kinda thing yet.

---

### Post by s.fox on 2009-06-03
Hi and welcome to the forums,

You are having file permission problems.  Take a look [here]("https://help.ubuntu.com/community/FilePermissions") for useful information on how to fix.

-Ash R

P.S.  Also nice to see you on IRC

---

### Post by AlwaysBenji on 2009-06-03
Reading now, thanks very much, it's kinda making sense...I think :D

---

### Post by s.fox on 2009-06-03
Hi,

In IRC you mentioned you have had some difficulties applying chmod.

To apply chmod to a folder you would need to:

1)  Open up terminal and navigate to the folder you want to change permissions on.  (If you need help,  please say :)  )

2)  Run this command

```
chmod 666 foldername
```

Hope this helps,

-Ash R

---

### Post by andrew.46 on 2009-06-03
Hi AlwaysBenji,

> **AlwaysBenji said:**
> What is going on? How can I fix this problem? I want Rhythmbox as it's supposedly fantastic for Last.Fm. I hope somebody can help. I have used Linux a little in the past but I am still not savvy at this kinda thing yet. 

Sorry to duck away after our brief chat on IRC :-). But I think the issue was eventually resolved for you by installing Rhythmbox from the Synaptic package manager rather than attempting to compile a new copy?

All the best

Andrew

---

