---
title: "&quot;Appropriated&quot; ram/ ram not recognized"
date: 2009-01-22
forum: New to Ubuntu
---

### Post by klemperal on 2009-01-22
I just installed an additional 2 gigs of ram--the problem is that Ubuntu only sees 3.1 gigs of ram instead of 4.  I checked around in the bios and it says under "system memory" Total-4096 mb, Appropriated-896 mb, Available 3200 mb.  I guess my real question then is why is 896 mb of ram "appropriated" and how do I get it back?

---

### Post by bsharp on 2009-01-22
You are running 32-bit Ubuntu. To get the full use of it, you will have to reinstall with a 64-bit version.

---

### Post by jerome1232 on 2009-01-22
A couple of things can be coming into play here.

32 bit processors can only address up to 4 GB of ram, some of it is allocated to other devices and sometimes integrated graphics will take a chunk out too, when it's all said and done a 32 bit system see's ~3.2 - 3.4 GB's of ram.

1) Is your procesor 32 bit or 64 bit, if you don't know run this, if there's any output then your cpu is 64 bit, if no output 32 bit.
```
cat /proc/cpuinfo | grep lm
```

2) Is your OS 32 bit or 64 bit, i386,i486,i586,i686 are 32 bit, x86_64 is 64 bit
```
uname -m
```

If your processor is 64 bit, and your OS is 32 bit, then just install the 64 bit version of Ubuntu that should let you see all 4 GB's.

If your processor is 32 bit and your motherboard supports PAE then I would look into compiling a pae enabled kernel. pae lets a 32 bit system address up to 64 GB's of ram.
to check if your cpu is pae enabled
```
cat /proc/cpuinfo | grep pae
```

---

### Post by klemperal on 2009-01-22
I have a i64bit processor, an nvidia 8400gs with 512mb onboard, and I'm currently dual booting xp32 and Ubuntu 32.  I'm not certain that its specifically an Ubuntu 32 issue since in the bios splash says it is only seeing 3.2gb ram.  I double checked my mobo's specs and it says it supports up to 4gb so that shouldn't be the issue.

---

### Post by jerome1232 on 2009-01-22
I think I see what you mean, what motherboard are you using, what's the bios and what version of the bios are you using.

I think I would check out the motherboards/bios web page and see if this is an issue with that hardware. If so, maybe there's a bios update that resolves it and etc...

---

