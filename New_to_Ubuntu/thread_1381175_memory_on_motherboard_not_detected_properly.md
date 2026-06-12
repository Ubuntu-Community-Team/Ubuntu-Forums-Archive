---
title: "memory on motherboard not detected properly"
date: 2010-01-14
forum: New to Ubuntu
---

### Post by F W Adams on 2010-01-14
Very strange problem

Motherboard as bought was initially 2 GB, using only one of the two slots, everything working fine with the 2 GB.

Today added a further 2 GB into second memory slot.
System/Administration/System monitor now says I have 3 GB. Thinking there was a mistake and that I had only inserted 1 GB I checked the bios. There was no mistake, the bios is saying I have 4 GB. The correct figure.

I'm using 8.04, hardy. 32 bit version. Motherboard is Foxconn M61PMV Series.

Any ideas?

---

### Post by Dreakon on 2010-01-14
I believe 32-bit only detects up to 3gb of RAM.  That's why they came out with 64-bit... it can detect up to like 64gb of it or something lol.

Hope I helped a little. :)

---

### Post by Cheesemill on 2010-01-14
32-bit can address up to 4GB of total address space. This includes your RAM, graphics card, sound card, etc...

So basically your usable RAM is 4GB minus graphics RAM minus sound RAM etc....

Search the forums, there are umpteen different threads on the subject.

---

### Post by mk1w86 on 2010-01-14
> I'm using 8.04, hardy. 32 bit version. Motherboard is Foxconn M61PMV Series.

Any ideas?

If you want to use all your RAM I recommend you switch to 64bit Ubuntu.  If you absolutely need 32bit you can use PAE to address the 4GB RAM but this can introduce various problems.

---

### Post by Cheesemill on 2010-01-14
> **mk1w86 said:**
> If you want to use all your RAM I recommend you switch to 64bit Ubuntu.

Obviously only possible if the OP has a 64-bit processor :)

---

### Post by audiomick on 2010-01-14
> **Cheesemill said:**
> Obviously only possible if the OP has a 32-bit processor :)

er, 64 bit perhaps?;)

---

### Post by Cheesemill on 2010-01-14
Well spotted.

---

### Post by mk1w86 on 2010-01-14
> **Cheesemill said:**
> Obviously only possible if the OP has a 64-bit processor :)

Oops, I just assumed the OP would, having that much RAM. :oops:

Out of interest what processor do you have F W Adams?

---

### Post by F W Adams on 2010-01-14
The other things seem to grab a lot more memory than actually needed, is it that only addresses starting with 00, 01 or 10 are allocated to main memory? It's not so much a practical thing for anything I need at the moment. I was just feeling a bit extravegent and bought some more memory and felt someone had stolen 1 GB of it. I didn't know what was happening.

I think I read that one trouble with 64 bit is that the cashe is used up more greedily because of the addresses being twice as long. I've got 64 bits available. I'll also look up PAE and see what that is. 

Ok, thanks for answers. 

I can remember in the early 70's thinking that we'd never be able fill up all the address space available with 16 bits ( 64 KB ) with physical memory.

---

