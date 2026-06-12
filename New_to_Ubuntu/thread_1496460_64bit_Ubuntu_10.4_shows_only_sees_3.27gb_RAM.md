---
title: "64bit Ubuntu 10.4 shows only sees 3.27gb RAM?"
date: 2010-05-29
forum: New to Ubuntu
---

### Post by aktiwers on 2010-05-29
Ubuntu only detects 3.2gb RAM instead of the 4gb installed?

```
aktiwers@HAL2:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          3270       1874       1396          0         20        295
-/+ buffers/cache:       1559       1711
Swap:          952        346        606
``````
aktiwers@HAL2:~$ uname -a
Linux HAL2 2.6.32-22-generic #33-Ubuntu SMP Wed Apr 28 13:28:05 UTC 2010 x86_64 GNU/Linux
aktiwers@HAL2:~$]
```Anyone has any ideas?

---

### Post by howefield on 2010-05-29
> **aktiwers said:**
> Ubuntu only detects 3.2gb RAM instead of the 4gb installed?

So what's the problem ? ;)

What's the make/model of the computer as some chips sets will restrict you from using all your 4 gigs, even with a 64 bit operating system.

---

### Post by redbook4574 on 2010-05-29
> **aktiwers said:**
> Ubuntu only detects 3.2gb RAM instead of the 4gb installed?

```
aktiwers@HAL2:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          3270       1874       1396          0         20        295
-/+ buffers/cache:       1559       1711
Swap:          952        346        606
``````
aktiwers@HAL2:~$ uname -a
Linux HAL2 2.6.32-22-generic #33-Ubuntu SMP Wed Apr 28 13:28:05 UTC 2010 x86_64 GNU/Linux
aktiwers@HAL2:~$]
```Anyone has any ideas?

Is this a laptop by any chance, and could the missing ram be allocated to the graphics card ??

---

### Post by aktiwers on 2010-05-29
I build the PC myself.. its a:

CPU: Intel Core 2 Quad Q9550 2.83 GHz / Mhz
Mobo: Asus P5Q PRO
RAM: Kingston HyperX   PC2-6400CL5, 4096
Videocard: Foxconn 9800GTX 

Back on Ubuntu 8.10 this was not a problem and all 4gb where shown.
I don't believe any of the RAM has been allocated to the videocard.
How would I check that? 

Thanks for the replys :)

---

### Post by howefield on 2010-05-29
> **aktiwers said:**
> I don't believe any of the RAM has been allocated to the videocard.

Not likely to be the graphic card on the basis that the card has 512 meg of dedicated DDR3 memory and even if it can take more in the form of shared memory, you'd likely know about about it as you would need to set it up through the Bios.

---

### Post by aktiwers on 2010-05-29
> **howefield said:**
> Not likely to be the graphic card on the basis that the card has 512 meg of dedicated DDR3 memory and even if it can take more in the form of shared memory, you'd likely know about about it as you would need to set it up through the Bios.

Yeah thats what I thought..

Any ideas on why Ubuntu only detects the 3.2gb and not all 4gb?

---

### Post by sdennie on 2010-05-29
I would check in your BIOS for an option called something like, "Map around memory hole".  It needs to be turned on.

---

### Post by aktiwers on 2010-05-29
> **sdennie said:**
> I would check in your BIOS for an option called something like, "Map around memory hole".  It needs to be turned on.

Thanks sdennie, that did it :)

---

