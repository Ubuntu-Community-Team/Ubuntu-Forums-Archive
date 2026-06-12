---
title: "MTRR mess, need help restoring"
date: 2009-11-29
forum: New to Ubuntu
---

### Post by jonrite on 2009-11-29
Hi all.
I'm in over my head. In my sad attempts to fix my laptop's fullscreen flash problems, I tried adding a new write-combining region to MTRR, which was recommended by another forum to fix the problem. When I attempted to go to fullscreen again, the window froze, and I couldn't even restart X with ctrl alt backspace.

Here is what comes up with cat /proc/mtrr
reg00: base=0x000000000 (    0MB), size= 2048MB, count=1: write-back
reg01: base=0x080000000 ( 2048MB), size=  512MB, count=1: write-back
reg02: base=0x09f800000 ( 2552MB), size=    8MB, count=1: uncachable
reg03: base=0x09f700000 ( 2551MB), size=    1MB, count=1: uncachable
reg04: base=0x0f0000000 ( 3840MB), size=  128MB, count=1: write-combining
reg05: base=0x0fb000000 ( 4016MB), size=   16MB, count=1: write-combining
reg06: base=0x0fb000000 ( 4016MB), size=    4KB, count=1: uncachable

I don't know what I need to keep, and what I need to get rid of, and don't know how to do either. 

Thank you.

Jonrite
Ubuntu 9.04
Inspiron e1405

---

