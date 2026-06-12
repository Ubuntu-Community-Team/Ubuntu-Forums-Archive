---
title: "Addming memory causes &quot;kernel panic&quot;"
date: 2009-01-23
forum: New to Ubuntu
---

### Post by moody_mark on 2009-01-23
Hi All, I have a little old Dell Optiplex PC running Kubuntu, it has 512MB ram and I decided to swap out the memory from 2 x 256MB 133Mhz to 2 x 512MB 133Mhz. Upon boot up I saw a message about "kernel panic". So i swapped the memory back and all is well.

Two questions:

1. If you swap out memory is there some prep work to do beforehand?
2. Where would this information all have gotten logged so I could post it up here?

---

### Post by philinux on 2009-01-23
Try each of the 512's on their own. You may have a dud.

---

### Post by billgoldberg on 2009-01-23
> **moody_mark said:**
> Hi All, I have a little old Dell Optiplex PC running Kubuntu, it has 512MB ram and I decided to swap out the memory from 2 x 256MB 133Mhz to 2 x 512MB 133Mhz. Upon boot up I saw a message about "kernel panic". So i swapped the memory back and all is well.

Two questions:

1. If you swap out memory is there some prep work to do beforehand?
2. Where would this information all have gotten logged so I could post it up here?

1. Nope.

I just switched my 512mb bars for 1gb bars last week.

Most likely it's bad ram memory, try each of the bars by themselfs.

However, my pc wouldn't even start when I tried the first set of bad ram memory I bought.

2. somewhere in /var/log

---

### Post by 3rdalbum on 2009-01-23
Either in /var/log/kern.log, /var/log/kern.0.log, or check in the Gnome System Log program. It depends when the kernel panic was in the startup - if it's before the disk was mounted read/write or if the kernel wasn't able to write out to the disk before the panic, then your system logs will be depressingly unhelpful :-(

---

### Post by Kevbert on 2009-01-23
Try running memtest from the boot menu with just one memory stick and then the other. It may just be that the memory is badly seated into the motherboard socket.

---

### Post by boof1988 on 2009-01-23
> **moody_mark said:**
> Hi All, I have a little old Dell Optiplex PC running Kubuntu, it has 512MB ram and I decided to swap out the memory from 2 x 256MB 133Mhz to 2 x 512MB 133Mhz. Upon boot up I saw a message about "kernel panic". So i swapped the memory back and all is well.

Two questions:

1. If you swap out memory is there some prep work to do beforehand?
2. Where would this information all have gotten logged so I could post it up here?

Which Optiplex is it?  What is the max allowed?

If it is a GX110, I believe the max allowed is 512.  I have a GX110 that I'm thinking of giving it a total of 512MB.

Here's a link for the GX110:  [http://support.dell.com/support/edocs/systems/opgx110/en/ug/specs.htm#memory](http://support.dell.com/support/edocs/systems/opgx110/en/ug/specs.htm#memory)

---

### Post by egalvan on 2009-01-23
> **boof1988 said:**
> Which Optiplex is it?  What is the max allowed?

If it is a GX110, I believe the max allowed is 512.  I have a GX110 that I'm thinking of giving it a total of 512MB.


I've been prepping several older Optiplex.

One is a Slot-1 model (GX1? I don't recall) with three slots.
Installed 3x256M and the machine reported 768M,
and memtest ran fine for the 24hr burn-in.

I think I may have tried a 512M on one of the GX110.
But I don't think they are limited to 512M.

I only have one 512M PC133 stick, and it doesn't work on all machines.

I'll be back Sunday with more info, if anyone still cares about such old iron.

ErnestG

P.S.
just for fun, I installed and tested the following on that 500MHz Slot1:
XP (Dell OEM) ran rather well.
Ubuntu ran very well.
Puppy 4.x ran like lightning, as always.

---

### Post by moody_mark on 2009-01-23
Well such a simple solution, thanks everyone. It appears one of the memory sticks is indeed a dud. One worked ok so I plugged one 512MB in with one 256MB one and now at least I have a little more memory.

Heres the first few lines from "lshw"

 ```
description: Space-saving Computer
    product: OptiPlex GX240
    vendor: Dell Computer Corporation
    serial: 8CSKC0J
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3 smp-1.4 smp
```

Interestingly enough I couldnt find anything in any logs about kernel panic. I searched under /var/log like so;

grep -i "panic" *  <<--returns nothing
find . | xargs grep -i "panic" <<-- returns nothing

So I guess the problem never got logged?

---

