---
title: "kernal"
date: 2009-08-20
forum: New to Ubuntu
---

### Post by jojom271 on 2009-08-20
how do i find out what kind of kernal i have on my system. i also whanto know if ubuntu is using all of my memory my comp has 4 g. i have a toshiba sat m305 s49052 64/32 please let me know

---

### Post by fooman on 2009-08-20
go to system > administration > system monitor

the system tab will show you the kernel.  resources will show you the memory consumption.  processes will show you whats using those resources.

hope that helps.

---

### Post by howefield on 2009-08-20
Opena terminal and type 
```

uname -a
```

that'll give you the kernel, and open system > administration > system monitor to get your ram usage/total.

---

### Post by jojom271 on 2009-08-20
ok i did it says kernal linux 2.6.28-15-generic  gnome 2.26.1
it aslo says that it is using 2.8 gib of memory 
processor 0: inte pent dual cpu t3400
processor 0: intel pent dual cpu t3400@2.16 ghz

how do i get it to use all 4 gib and is the processor correct?

---

### Post by howefield on 2009-08-20
> **jojom271 said:**
> ok i did it says kernal linux 2.6.28-15-generic  gnome 2.26.1
it aslo says that it is using 2.8 gib of memory 
processor 0: inte pent dual cpu t3400
processor 0: intel pent dual cpu t3400@2.16 ghz

how do i get it to use all 4 gib and is the processor correct?

Again in the terminal type,

```
uname -r
```

Looks like you are using the 32 bit version of Ubuntu, to use all 4 gigs you would need to use the 64 bit version, (or the PAE enabled 32 bit).

And what I can gather about the specs of that laptop, it is reporting the correct cpu.

---

