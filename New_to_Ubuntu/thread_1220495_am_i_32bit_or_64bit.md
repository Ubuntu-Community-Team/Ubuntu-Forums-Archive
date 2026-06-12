---
title: "am i 32bit or 64bit?"
date: 2009-07-22
forum: New to Ubuntu
---

### Post by bacchusmarsh on 2009-07-22
How do i find out if i am running 32bit ubuntu or 64bit ubuntu?

---

### Post by unutbu on 2009-07-22
```
uname -m
```
i686 means 32-bit
x86_64 or amd64 means 64-bit

or
```
getconf LONG_BIT
```returns 32 if the OS is 32-bit
returns 64 if the OS is 64-bit.

---

### Post by sandyd on 2009-07-22
type in 
```

uname -a

```
in the terminal
That will show your Ubuntu version

---

### Post by masterkoppa on 2009-07-22
Depends on what procesor you have. Besides this you should consider the pros vs cons of 32 vs 64 bit. I would recomend you red this article: [32bit vs 64bit]("https://help.ubuntu.com/community/32bit_and_64bit")

---

### Post by bacchusmarsh on 2009-07-22
Thank you all...

---

### Post by ~sHyLoCk~ on 2009-07-22
```
arch 32/64?? :O :D
```

:P

---

### Post by Elep.Repu on 2009-07-22
If you like GUI, Administration/System Monitor
Then far left tab. :)

---

### Post by LookTJ on 2009-07-22
**Hardware:**```
cat /proc/cpuinfo
```

Look for "lm" under the flags. If it's there, it is 64 bit
[B]
Software:[/B] ```
uname -a
```

Look for x64 or something like that along the line.

Hope that helps. :)

---

### Post by bodhi.zazen on 2009-07-23
> **LookTJ said:**
> **Hardware:**```
cat /proc/cpuinfo
```Look for "lm" under the flags. If it's there, it is 64 bit
[B]
Software:[/B] ```
uname -a
```Look for x64 or something like that along the line.

Hope that helps. :)

+1

```
grep ' lm ' /proc/cpuinfo --color=auto 
```

If that code returns output you have a 64 bip processor.

I like uname -m for software

---

