---
title: "Trouble installing ndiswrapper"
date: 2009-03-07
forum: New to Ubuntu
---

### Post by MrPickle on 2009-03-07
Whenever I try and make ndiswrapper it fails and says:

> Makefile:51: *** No .config found in , please set KBUILD to configured kernel. Stop.

Why? I am trying to install ndiswrapper 1.54 on Ubuntu 8.04

---

### Post by Kareeser on 2009-03-07
What's wrong with

```
sudo apt-get install ndiswrapper
```

?

---

### Post by MrPickle on 2009-03-07
That doesn't work it says:

E: Unable to find package ndiswrapper

---

### Post by Crafty Kisses on 2009-03-07
If you still want to compile ndiswrapper from source, you need the "build-essential" package, and you can install that by running the following:
```
sudo apt-get install build-essential
```
That's one option, if you want to install ndiswrapper through the repos, you need to run the following:
```
sudo apt-get install ndiswrapper-common
```

---

### Post by MrPickle on 2009-03-07
I figured out why I was getting the

> E: Couldn't find package ndiswrapper

it was because I didn't have the CD on the repositories.

I have installed the build essentials but I still get the config error.

---

