---
title: "GCC from scratch: Cannot Compute Suffixes"
date: 2011-04-09
forum: New to Ubuntu
---

### Post by Pureferret on 2011-04-09
I've been trying to install GCC from scratch, as my main PC has no internet. I've installed all of the dependencies I can think of/been asked too, i.e. MPC, MPFC, and others. 

Googling has be believe I have some library linking errors, but I have no idea where to start on that.

I've attached the relevant snippet of my config.log

---

### Post by TeoBigusGeekus on 2011-04-09
```
error while loading shared libraries: libmpc.so.2: cannot open shared object file: No such file or directory
```
Have you installed libmpc?

---

### Post by Pureferret on 2011-04-09
I downloaded and installed (correctly I believe) mpc-0.8.1, which I'm assuming contained libmpc. Though I'd be glad to be corrected.

---

### Post by TeoBigusGeekus on 2011-04-09
See [this]("http://packages.ubuntu.com/search?keywords=libmpc-dev") page.

---

### Post by Pureferret on 2011-04-09
Thanks very much, I've downloaded the package and will try it out tonight. 

Will this package work without access to the internet?

---

### Post by TeoBigusGeekus on 2011-04-09
> **Pureferret said:**
> Thanks very much, I've downloaded the package and will try it out tonight. 

Will this package work without access to the internet?

I hope so...
Make sure you also have the other 3 packages that the page mentions as dependencies for libmpc.

---

### Post by Pureferret on 2011-04-09
Awesome, I shall report back later :D

---

### Post by Pureferret on 2011-04-10
Ok so that fixed several of my issues, but now I'm having trouble with some sort of fortran library (?). I don't need fortran (at least not right now) so I've tried to disable it, but not had any luck. I also tried to disable multilib whcih was giving errors. No idea if --disable-multilib does anything useful, but I saw it somewhere after some googling. 

Again I've attached config.log in two parts and the also this time the error (which doesn't seem duplicated in config.log, I could be wrong).

---

### Post by sandyd on 2011-04-10
are you using x64 or x86

---

### Post by Pureferret on 2011-04-10
I'm using 64bit. I've been trying to pick out all the 64bit packages I've been installing but I may have missed one or two, is that the issue do you think?

---

### Post by sandyd on 2011-04-10
> **Pureferret said:**
> I'm using 64bit. I've been trying to pick out all the 64bit packages I've been installing but I may have missed one or two, is that the issue do you think?
use keryx. [http://keryxproject.org/download/](http://keryxproject.org/download/)
download build-essential using it.

---

### Post by Pureferret on 2011-04-10
This looks good but there's not much I can do right now. It's a duel boot right now and Im half-way through some coursework. I've d'loaded the deb and I shall fiddle with it sometime tonight.

---

### Post by sandyd on 2011-04-10
> **Pureferret said:**
> This looks good but there's not much I can do right now. It's a duel boot right now and Im half-way through some coursework. I've d'loaded the deb and I shall fiddle with it sometime tonight.
Its for windows & ubuntu btw.

---

### Post by wep940 on 2011-04-11
Even without internet, you should be able to install GCC just using the LiveCD.  Install the build-essential package located in the /pool/main/b folder.  You might also try installing gcc-4.4 and the defaults after that - their in the /pool/main/g folder.

---

