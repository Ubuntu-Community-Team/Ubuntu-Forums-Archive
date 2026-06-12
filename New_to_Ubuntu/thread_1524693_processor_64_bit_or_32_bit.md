---
title: "processor 64 bit or 32 bit"
date: 2010-07-05
forum: New to Ubuntu
---

### Post by LittleGyko on 2010-07-05
Can someone tell me how I can find out whether my processor is 32 bit or 64 bit. 

Thanks

---

### Post by marin123 on 2010-07-05
open terminal and type:

lscpu

---

### Post by bodhi.zazen on 2010-07-05
```
grep ' lm ' /proc/cpuinfo
```

if that returns anything you have a 64 bit CPU.

See also :

[http://www.cyberciti.biz/faq/linux-how-to-find-if-processor-is-64-bit-or-not/](http://www.cyberciti.biz/faq/linux-how-to-find-if-processor-is-64-bit-or-not/)

---

### Post by LittleGyko on 2010-07-05
thanks, 

it returned quite a few things :). I also checked the link you send. I have a 32 bit linux kernel running. Actually I use ubuntu 10.04. Once I gain some comfort level with linux, I will try and install a 64 bit kernel. thanks once again.

---

### Post by LittleGyko on 2010-07-05
> :$ lscpu
Architecture:          i686
CPU op-mode(s):        32-bit, 64-bit
CPU(s):                4
Thread(s) per core:    2
Core(s) per socket:    2
CPU socket(s):         1
Vendor ID:             GenuineIntel
CPU family:            6
Model:                 37
Stepping:              2
CPU MHz:               933.000
Virtualization:        VT-x
L1d cache:             32K
L1i cache:             32K
L2 cache:              256K
L3 cache:              3072K
Does CPU op mode : 32 , 64 indicate 64 bit?

---

### Post by Directive 4 on 2010-07-05
> **LittleGyko said:**
> Does CPU op mode : 32 , 64 indicate 64 bit?


yes, it's 64 bit, but can pretend to be 32 bit,

nowadays 64 bit is just as stable as 32 bit, at least for me!

why not just go 64bit, just another way to increase your comfort zone, 

(depends on your free time i guess, but not any harder than 32 bit, maybe flash but a google of flash-aid will solve that)
:popcorn:

---

### Post by LittleGyko on 2010-07-05
I guess i should stick with this for some time before i pick up some general linux awareness. then i can carry out experiments. i did read sometime back on the net about the flash problem you mentioned.

---

### Post by Directive 4 on 2010-07-05
:D


pick up some general linux awareness **by** going 64 bit!

it's not very hard at all,

:D

---

