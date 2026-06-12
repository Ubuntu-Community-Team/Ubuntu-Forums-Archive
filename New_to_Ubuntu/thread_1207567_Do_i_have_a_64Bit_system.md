---
title: "Do i have a 64Bit system"
date: 2009-07-08
forum: New to Ubuntu
---

### Post by Short__Error on 2009-07-08
How do i tell weather or not i have a 64bit system when i bought my laptop it came with a 32bit version of Vista(i took Vista off)?
 

My system: [SIZE=3]HP Pavilion dv9620us Notebook PC[/SIZE]
[LIST]
[*]1.9 GHz AMD Turion 64 X2 Dual-Core Mobile Technology TL-58
[/LIST]So any help would be greatly appreciated!!!

---

### Post by masux594 on 2009-07-08
```
uname -a
```If the answer contain 'x86_64' is 64 bit.

Sysc, A

---

### Post by doas777 on 2009-07-08
yes you have 64 bit-capable hardware. I run ubuntu 64 on a couple of very similar models (dv9205/dv9830). give the 64bit a try

---

### Post by RD1 on 2009-07-08
> AMD Turion 64 X2

... pretty much says it all .....

---

### Post by baizon on 2009-07-08
[QUOTE=Wikipedia]AMD Turion is the brand name AMD applies to its 64-bit low-power consumption (mobile) processors codenamed K8[/QUOTE]
As you can see your CPU supports 64bit computer architecture (OS).

---

### Post by Short__Error on 2009-07-08
Ok think you very much i will upgrade when i get home :D

---

### Post by anystupidname on 2009-07-08
First guess, you have a 64bit system just because of what your sig says your processor is.

[http://en.wikipedia.org/wiki/AMD_Turion](http://en.wikipedia.org/wiki/AMD_Turion)

You can confirm this with:
```
cat /proc/cpuinfo | grep lm
```

Please note that "uname -a" will only tell you if the linux version/distro you are running is 64 bit. (not whether your computer is 64 bit capable) I'm just nitpicking for the sake of others reading this thread who may need to know this.

---

### Post by masux594 on 2009-07-08
Hmm .. the question is: Do i have a 64 bit cpu? Or.. is my system for 64 bit cpu? Every question is already answered =)

Sysc, A

---

### Post by oldos2er on 2009-07-08
> **Short__Error said:**
> Ok think you very much i will upgrade when i get home :D

 There is no upgrade to 64-bit available. You need to do a full install.

---

### Post by Short__Error on 2009-07-08
Did and done it it works great on my laptop :guitar:

---

