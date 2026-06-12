---
title: "A computer science problem"
date: 2009-04-18
forum: New to Ubuntu
---

### Post by bcasanov on 2009-04-18
Edited

---

### Post by alphacrucis2 on 2009-04-18
> **bcasanov said:**
> Hi, 

I'm taking an Operating Systems class and am relatively new to computer science (I have only taken one programming course).  I have encountered a problem that I'm trying to work out:

CD-quality music requires sampling the sound signal 44,100 times per second. Suppose that a timer generates an interrupt at this rate and that each interrupt takes 1 microsec to handle on a 1-GHz CPU. What is the slowest clock rate that could be used and not lose any data? Assume that the number of instructions to be processed for an interrupt is constant, so halving the clock speed doubles the interrupt handling time.

I think I have an okay (maybe just beginner) understanding of interrupts, and know what clock rate is and that 1 GHZ means 1 billion cycles per second.  What I am trying to understand is if there is any formula for determining when data loss starts to occur, and if there is a formula for calculating the lowest clock rate for the interrupt.  I think I'm kind of lost, but I would appreciate any kindly advice to help me see a path to solving this problem.

The interrupt has to be processed in a maximum of 1/44100 of a second right. Just a bit of arithmetic from there.

---

### Post by LesterPalooza on 2009-04-18
Oooh.. You're class sounds interesting :D Im taking Computer Science too but I am more into programming...

---

### Post by bcasanov on 2009-04-18
Thank you! That's exactly the key to solve the problem: what the maximum time for processing the interrupt should have!  I was wondering around in cirlces before.  Now I've figured the ratio that applies.

---

### Post by cariboo on 2009-04-18
This sounds suspiciously like a home work problem,

> 1.While we are happy to serve as a resource for hints and for asking questions when you get stuck and need a little help, the Ubuntu Forums should not be thought of as a homework service. Please do not post your homework assignments expecting someone else to do it for you. Any such threads will be taken offline and warnings or infractions may be issued. 


I'm not going to do anything, but be aware of the [C of C]("http://ubuntuforums.org/index.php?page=policy").

Jim

---

