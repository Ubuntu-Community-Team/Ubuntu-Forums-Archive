---
title: "How do I install ia32-libs in Ubuntu 8.10?"
date: 2008-12-06
forum: New to Ubuntu
---

### Post by RadiationHazard on 2008-12-06
I tried doing 

```
sudo apt-get install ia32-libs 
```

but I get an error...
```

jordan@jordan-laptop:~$ sudo apt-get install ia32-libs 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ia32-libs
jordan@jordan-laptop:~$
```

Anybody know how to fix this problem? :-k

---

### Post by kd7swh on 2008-12-06
Make sure you have the universe repository enabled then try
```
sudo apt-get update
```
before the:
```
sudo apt-get install ia32-libs
```

if that doesn't work here is a link to the package:

[http://packages.ubuntu.com/intrepid/ia32-libs](http://packages.ubuntu.com/intrepid/ia32-libs)

---

### Post by Catalyst2Death on 2008-12-06
Just to be clear, ia32 libs is only for 64-bit machines, so if your running 32-bit, it won't be in the repositories, hence the error.  I tried to find equivalents, but I didn't come up with anything.

[http://packages.ubuntu.com/feisty/libs/ia32-libs-sdl](http://packages.ubuntu.com/feisty/libs/ia32-libs-sdl)

otherwise you need to enable the universe repository (which AFAIK is enabled by default...)

---

### Post by RadiationHazard on 2008-12-06
well I don't have a 64 bit machine? I have a 32 bit. I'm trying to get Google's Android emulator to run on my laptop. How do I do it?

---

