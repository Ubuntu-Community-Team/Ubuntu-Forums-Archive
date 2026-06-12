---
title: "Allocate memory"
date: 2009-10-08
forum: New to Ubuntu
---

### Post by z0rf on 2009-10-08
I have Ubuntu 64bit 9.04 installed.
It runs on 512MB DDR2 RAM. However, when I type $ free
it shows this:

             ```
total       used       free     shared    buffers     cached
Mem:        434360     134084     300276          0       8252      58008
-/+ buffers/cache:      67824     366536
Swap:      6787420        100    6787320
```

Does this mean i just lost 80MB of RAM or is this normal?
I kinda expected that under total it should say 512000 something instead of
434360.

Kind Regards

David

---

### Post by wojox on 2009-10-08
Ive got 512 MB DDR RAM 32 bit this is what I get:

```
wojox@wojox-desktop:~$ free -m
             total       used       free     shared    buffers     cached
Mem:           497        351        145          0         18        171
-/+ buffers/cache:        162        335
Swap:         1451          0       1451
```

GPU maybe?

---

### Post by Anarci on 2009-10-08
Rather use ```
free -m
``` to display in megabytes - your expected ram would be 1024 X 512 = 524288 KiB.

Running free on my pc also shows less ram than expected but the gnome system monitor says that I have 2 GiB, although I don't know why free displays less

---

### Post by XCan on 2009-10-08
As wojox stated, I think it's related to your graphics chip. Is it by chance an integrated one? Such chips can reserve RAM for its own use.

---

### Post by LowSky on 2009-10-08
just so you know 512MB is 524288kb
your missing about 128 MB or ram, do you havew onboard graphics, thats where it went if thats the case.

---

### Post by z0rf on 2009-10-08
Ah, I do have an onboard graphics card.
It stole quite a lot memory for a computer that has no monitor attached
and needs only to display a cursor.
Which brings up another question:

Can i Edit my bios without attaching a monitor?

If not, ill have to attach one which is quite a pain in the *ss...

Thanks so far!

---

### Post by wojox on 2009-10-08
No, you need a monitior to edit bios. So this is a headless server?

---

### Post by arrange on 2009-10-08
> **z0rf said:**
> ...

Does this mean i just lost 80MB of RAM or is this normal?
I kinda expected that under total it should say 512000 something instead of
434360.

Kind Regards

David
I don't know, but in my experience it's not normal. Could you post/upload/pastebin the initial part of dmesg, let's say the part you get by running```
dmesg | head -200
```

---

### Post by z0rf on 2009-10-09
I hooked up a monitor and set shared memory to VGA on 32 MB instead of auto. And now the numer is 467128.... so is does seem to matter?
Only missing 50/60MB now. More acceptable.

Someone still think this is abnormal? :)

---

### Post by z0rf on 2009-10-09
> **arrange said:**
> I don't know, but in my experience it's not normal. Could you post/upload/pastebin the initial part of dmesg, let's say the part you get by running```
dmesg | head -200
```

This is the pastebin: I can't decipher any of it :) This what you requested of me?

[http://pastebin.com/m4032c791](http://pastebin.com/m4032c791)

---

### Post by mcduck on 2009-10-09
> **z0rf said:**
> I hooked up a monitor and set shared memory to VGA on 32 MB instead of auto. And now the numer is 467128.... so is does seem to matter?
Only missing 50/60MB now. More acceptable.

Someone still think this is abnormal? :)

That's normal. The rest is the part of your RAM occupied by the Linux kernel itself.

The kernel is loaded into RAM at boot, and will always stay there. That part of memory will not ever be available to any programs, so most Linux applications won't even count it into the total memory value. 

So, the amount of total RAM "free" will report is the amount of your physical RAM minus the space occupied by kernel and the part possibly used by your graphics card. So even without integrated graphics card using your RAM the total RAM value reported by "free" will never be the same as your physical RAM.

---

### Post by arrange on 2009-10-09
Still it does not explain why he has only 491200k available - see z0rf's```
dmesg | grep Memory
[    0.004000] Memory: 458288k/491200k available (4749k kernel code, 452k absent, 31732k reserved, 2523k data, 536k init)
```

How much RAM do you see in BIOS (you should see the figure shortly after boot)?

---

