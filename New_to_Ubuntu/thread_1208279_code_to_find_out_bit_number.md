---
title: "code to find out bit number"
date: 2009-07-09
forum: New to Ubuntu
---

### Post by cybuss on 2009-07-09
can i get a code to check my bit number? friend never told me if im 32 bit or 64

---

### Post by wojox on 2009-07-09
Open a terminal :

```
uname -a
```

---

### Post by cybuss on 2009-07-09
> **wojox said:**
> Open a terminal :
then what?

---

### Post by wojox on 2009-07-09
Sorry

```
uname -a
```

---

### Post by fbugnon on 2009-07-09
> **cybuss said:**
> can i get a code to check my bit number? friend never told me if im 32 bit or 64

Are you talking about software or hardware?

If you want to know about your software, that is, how many bits is your ubuntu system, then do what wojox said and look for an i686 in the output, like: 

```
Linux fbugnon-desktop 2.6.28-13-generic #45-Ubuntu SMP Tue Jun 30 19:49:51 UTC 2009 **i686** GNU/Linux
```

If you have this, you're under 32 bits, if you have something else, ending with an "**_64**", then you have a 64 bits.


BUT, if you´re talking about hardware, try this command:

```
$ lshw 
```

It will come a very long output, look the cpu specifications (beginning).  For instance, in mine computer reads:

```
 *-cpu
          product: AMD Athlon(tm) 64 Processor 3500+
          vendor: Advanced Micro Devices [AMD]
          physical id: 1
          bus info: cpu@0
          version: 15.15.0
          size: 2200MHz
          capacity: 2200MHz
          width: **64 bits**

```

---

### Post by boblemur on 2009-07-09
type:

uname -m into terminal

if you have 32 bit version it will say: i386 and if you have 64 it will say x86_64

hope this helps :)

---

### Post by LookTJ on 2009-07-09
```
cat /proc/cpuinfo
```
in a terminal

---

### Post by wojox on 2009-07-09
Where is the bit # in cat /proc/cpuinfo ?

---

### Post by fbugnon on 2009-07-09
> **LookTJ said:**
> ```
cat /proc/cpuinfo
```
in a terminal

this is certainly a lot easier, *hardware-wise.*

---

### Post by LookTJ on 2009-07-09
> **wojox said:**
> Where is the bit # in cat /proc/cpuinfo ?
In a 64 bit CPU, the flags will show "lm"(long mode) while a 32 bit will not

---

