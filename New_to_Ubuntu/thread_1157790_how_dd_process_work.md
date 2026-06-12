---
title: "how dd process work?"
date: 2009-05-13
forum: New to Ubuntu
---

### Post by plusnplus on 2009-05-13
Hi..,
I try wipe my hd use dd if=/dev/urandom of=/dev/sda.
It take very long time and still run.
I see the status use kill -USR1 (PID).
If it say 20gb copied, actually the process of wiping is from begining block of the harddisk, random  or...?

my harddisk capacity is 160gb, but so far i only use 8-10gb.
if i stop the dd process, is my hard disk already can say clean?

thank for any reply.

---

### Post by Lampi on 2009-05-13
you could use shred to wipe your disc instead

I use it like this:

```
shred -vzn5 /dev<devicename>
```

So at the end it will have erased each sector 5 times - should be enough.

---

### Post by plusnplus on 2009-05-13
I knew there is other method that run faster.
I just want to know, if I want stop in the middle of the process, how actually dd process work.

---

### Post by Lampi on 2009-05-14
> **plusnplus said:**
> Hi..,
my harddisk capacity is 160gb, but so far i only use 8-10gb.
if i stop the dd process, is my hard disk already can say clean?
No. Whatever *used* to be in the remaining 150GB of your drive is enlisted in your partition table as free space, but if there was some sensible data some time ago it is all there and can be restored if you never format this space.

I recommend shred over dd for wiping not only for speed reasons, you sould also make sure you wipe each sector more than once. Funny as it sounds: if someone has the resources, he is able to restore a big amount of the erased data, if each sector has been only wiped once.

---

