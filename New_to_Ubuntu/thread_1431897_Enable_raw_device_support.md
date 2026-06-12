---
title: "Enable raw device support"
date: 2010-03-17
forum: New to Ubuntu
---

### Post by kylea on 2010-03-17
I have been using LVM to create logical groups and volumes.

I now want to experiment with raw devices, like /dev/raw/rawx etc

I cannot get the raw command to work. I have seen comments that the driver has been disabled in 2.6 kernel.

here is the error from the command : 

raw /dev/raw/raw1 /dev/pv1/lvol0

Cannot open master raw device '/dev/raw/rawctl' (No such device or address)

Is there a way to re-enable it?

I have Ubuntu 9.10 64Bit

---

### Post by aeiah on 2010-03-17
i dont know much about this kind of thing, but i suppose you should ask why it has been disabled? has something better come along?

i have experience mounting raw images as block devices, so you access them like normal partitions. is that what you're after?

[http://equivocation.org/node/107](http://equivocation.org/node/107)

---

### Post by kylea on 2010-03-17
> **aeiah said:**
> i dont know much about this kind of thing, but i suppose you should ask why it has been disabled? has something better come along?

i have experience mounting raw images as block devices, so you access them like normal partitions. is that what you're after?

[http://equivocation.org/node/107](http://equivocation.org/node/107)

Yes - is the answer to both questions - the 2.6 kernel now expects O_DIRECT as the access method.

Unfortunately my database still uses raw file access.

I have done it before successfully on a 2.4 Red Hat kernel, just does not seem to work on 2.6.31 Ubuntu

---

