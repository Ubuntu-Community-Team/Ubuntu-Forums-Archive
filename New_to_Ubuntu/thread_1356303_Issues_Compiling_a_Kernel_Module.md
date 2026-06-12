---
title: "Issues Compiling a Kernel Module"
date: 2009-12-15
forum: New to Ubuntu
---

### Post by theharshone on 2009-12-15
Hello,

I am having difficulty compiling the legacy rt2570 kernel module. The current rt2x00 kernel module that is built into the kernel does not play well with certain games (Tremulous) causing my router to lose connection with my isp (I don't know why or how it does it. All I know is that if I use the legacy driver, it does not happen.) So, I did a clean install of 9.10 and installed all the required packages to compile modules.

```

sudo apt-get install build-essential
sudo apt-get build-dep linux
sudo apt-get build-dep linux-source (I think this did the same thing as the above command, but I did it just to be thorough.)

```

When I try to compile the driver, I get this:
```

make[1]: Entering directory `/usr/src/linux-headers-2.6.31-17-generic'
  Building modules, stage 2.
  MODPOST 0 modules
make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-17-generic'
rt2570.ko failed to build!
make: *** [module] Error 1

```

It does not actually compile the module. Then, I tried to compile another miscellaneous module, but that compiled fine. What am I doing wrong that is preventing me from compiling the module? It worked fine on 9.04.

Thanks.

---

### Post by theharshone on 2009-12-17
So, I spent all day trying to get the existing one to work for me, but no such luck. Has no one experienced a problem like this>

---

### Post by outleradam on 2009-12-27
yes. I am having the same issue

---

### Post by wmatthews on 2010-03-22
I am having the same issue.  Can't figure out what it is but if I find out I will let you know as I hope you will for me...

---

