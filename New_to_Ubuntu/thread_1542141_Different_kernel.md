---
title: "Different kernel?"
date: 2010-07-30
forum: New to Ubuntu
---

### Post by limjix on 2010-07-30
I want to ask, I have noticed that some people talk about different kernels other than the "generic" kernel. What other kernels are there out there for ubuntu linux 10.04? Which is better?

Any good links ?

I am running on an AMD P320 dual core processor, and currently using the 32bit version of Ubuntu. 

Thanks :)

---

### Post by Bachstelze on 2010-07-30
Search for [font=monospace]linux-image[/font] in Synaptic and you'll see them.  You probably don't want to use any of them, the -generic one is the default for a reason: it's the most suitable for most people.

---

### Post by limjix on 2010-07-30
But does it also mean that some other kernel might work better on my system??

How would i know whether or not another kernel is better?

---

### Post by Bachstelze on 2010-07-30
> **limjix said:**
> But does it also mean that some other kernel might work better on my system??

How would i know whether or not another kernel is better?

They are for very specific use cases.  The 386 kernel is for very old machines, the PAE kernel is for servers with a lot of RAM, the rt kernel is for multimedia production or embedded applications that must have as low latency as possible, etc..  None of this applies to you, you would know if it did.

---

