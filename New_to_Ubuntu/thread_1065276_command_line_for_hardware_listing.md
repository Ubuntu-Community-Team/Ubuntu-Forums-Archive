---
title: "command line for hardware listing"
date: 2009-02-09
forum: New to Ubuntu
---

### Post by capnthommo on 2009-02-09
(solved)  hi there, (solved) 
i want to check the memory on my machine and wonder if anyone can tell me the command line to find out.  i thought i had 4Gb (3.6) of memory but the system monitor only shows 1.8.
thanks for any help.
nigel

---

### Post by taurus on 2009-02-09
```
free -m
```
Do you have an onboard graphic card that shares the video memory with your RAM?

---

### Post by capnthommo on 2009-02-10
thanks taurus it seems to confirm that i only have 1.8 G.  and here i have been thinking i had double that!  here's the output from the commamnd
```
nigel@ubuntunigellaptop:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          1881        837       1043          0         37        328
-/+ buffers/cache:        471       1409
Swap:         5506          0       5506

```
> Do you have an onboard graphic card that shares the video memory with your RAM?
i do have an on board graphic card, its an ATI Radeon something, but as to whether it shares video memory with my RAM i am afraid i don't know and wouldn't know how to find out.
i suspect that i have just been mistaken and overestimated how much mem i have.
Ah well, just have to maybe get a bigger one then if it became an issue - it's not at the moment and i am only using about 40% or so.
thanks again for that
nigel

---

### Post by Nepherte on 2009-02-10
2GB is usually sufficient. As you can see, you have 1.8GB RAM of which 837MB is used. 328MB of that 837MB is cached so things that the os might need is easily accessible and fast as well. So technically you're system is only using 837-328MB of actual RAM.

On board vga's generally shares video memory with  RAM, I'd say in your case as well.

---

