---
title: "Question  xD card reader does not work in Dell."
date: 2009-08-29
forum: New to Ubuntu
---

### Post by ovroniil on 2009-08-29
I am using Dell Inspiron. My built in card reader cant recognize 2GB Olympus xD memory card. But ubuntu does not even show any card in my laptop. But it can recognize SD memory cards.

I am using Ubuntu 9.04 and my kernel is 2.6.30.
 
What should i do??

---

### Post by ovroniil on 2009-08-29
Forgot to say, that xD card works well in Windows. In Ubuntu it is not even mounted. It is not shown under Places or Computer.

---

### Post by ovroniil on 2009-09-15
**Bump**

Guys, it is still not working!!

---

### Post by halitech on 2009-09-15
remove the card then plug it back in and in the terminal run
```
dmesg | tail
``` and post the results back here

---

### Post by suxenexus on 2011-08-19
Sorry for bumping this thread.  I got the same problem too.  Here's the result with the command you gave:
```
[ 2669.070101] r852: detected xD writeable card in slot
[ 2669.359829] keyboard: can't emulate rawmode for keycode 240
[ 2669.359856] keyboard: can't emulate rawmode for keycode 240
[ 2669.364440] keyboard: can't emulate rawmode for keycode 240
[ 2669.364460] keyboard: can't emulate rawmode for keycode 240
[ 2669.380098] No NAND device found.
[ 2669.380117] r852: detected xD writeable card in slot
[ 2669.690117] NAND device: Manufacturer ID: 0x98, Chip ID: 0xd5 (Toshiba xD 2GiB 3,3V)
[ 2669.692227] sm_ftl: Found 2048 MiB xD/SmartMedia FTL on mtd0
[ 2669.714119]  smblka: smblka1

```

---

