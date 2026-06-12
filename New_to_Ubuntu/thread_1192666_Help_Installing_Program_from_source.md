---
title: "Help Installing Program from source"
date: 2009-06-20
forum: New to Ubuntu
---

### Post by CapitanYochua on 2009-06-20
Hey, I need help trying to install a program from source (I don't think it is in the synaptic).

 Anyways this is my output from running ./configure
[http://paste.ubuntu.com/200177/plain/](http://paste.ubuntu.com/200177/plain/)

I'm assuming it didn't work since the make command won't work after running ./configure. 

And this is my config log
[http://paste.ubuntu.com/200180/plain/](http://paste.ubuntu.com/200180/plain/)

Any help would be appreciated.
Thank you.

---

### Post by michy99 on 2009-06-20
It doesn't look like you have any compilers installed. You need to run```
sudo apt-get install build-essential
```

---

### Post by CapitanYochua on 2009-06-20
Yeah, that was it! Thank you! I wonder why that doesn't come installed in ubuntu.

---

### Post by michy99 on 2009-06-20
> **CapitanYochua said:**
> Yeah, that was it! Thank you! I wonder why that doesn't come installed in ubuntu.

Because Ubuntu doesn't assume you will be compiling programs from source.

---

### Post by andrew.46 on 2009-06-21
Hi CapitanYochua,

> **CapitanYochua said:**
> Yeah, that was it! Thank you! I wonder why that doesn't come installed in ubuntu.

As michy99 has suggested Ubuntu is more of a repository-based distro with an absolutely *enormous* range of pre-built binaries available and so compiling from source, while easily accomplished by installing the meta package 'build-essential', is not necessarily a frontline necessity as it is in distros like Slackware or Gentoo. This leads quite neatly into the current requirement that Ubuntu be distributed as either an iso or cd that is less than about 700mb. I am glad that I am not the one who decides what goes on the CD and what does not :-).

Andrew

---

