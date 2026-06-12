---
title: "Install IR receiver driver from source code"
date: 2009-09-07
forum: New to Ubuntu
---

### Post by sn3rd on 2009-09-07
I've been trying to get my IR receiver working on my Dell Studio 1537.

lshal shows that it's there: an ITE8708. 

lirc's setup doesn't have an option for that receiver. After some searching, I think the driver just isn't included. 

I emailed the manufacturer as someone in another thread said they had a reply.

I received a reply with two files attached: lirc_it85.c and lirc_it85.h 

The contents of these files is similar to those found under lirc's drivers for the ITE8709. 

I think i need to compile this and put it somewhere, and then modprobe to enable it. 

But I have no idea if that's correct or what the details are. 

Could someone please point me in the right direction regarding getting the module compiled and installed for this driver and indeed, drivers in general.

---

### Post by tjodSK on 2009-09-21
Hello

can you share the code (.c and  .h), please?

---

