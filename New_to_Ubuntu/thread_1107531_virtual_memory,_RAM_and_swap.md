---
title: "virtual memory, RAM and swap"
date: 2009-03-26
forum: New to Ubuntu
---

### Post by flylehe on 2009-03-26
Hi,
I was wondering  

1.if "virtual memory size = RAM size + swap size"?

2. For a n-bit system, when setting virtual memory size, is the maximum allowable size 2^n bytes?

3. If the system runs out of virtual memory size that I previously set, will it takes more space from unused hard disk space as its temporary virtual memory?

Thanks!

---

### Post by snova on 2009-03-26
> **flylehe said:**
> 1.if "virtual memory size = RAM size + swap size"?

That sounds about right. Though I've also heard "virtual memory = swap", so maybe not...

> 2. For a n-bit system, when setting virtual memory size, is the maximum allowable size 2^n bytes?

No, you can go higher. For example, a 32-bit system can use more than 4 GB with [PAE]("http://en.wikipedia.org/wiki/Physical_Address_Extension"). As to 64-bit systems, that's not really a problem yet. :)

> 3. If the system runs out of virtual memory size that I previously set, will it takes more space from unused hard disk space as its temporary virtual memory?

If you have swap space left, it will use it, beyond that, no. It will actually kill off processes if you use all of it.

---

### Post by aeiah on 2009-03-26
under normal use the term virtual memory is really just the microsoft term for swap. page file and scratch disk are other phrases used.

swap can be any size you want but it starts to become a waste after a while. unless you're doing very intensive things, you may not use the swap at all in a system with 1GB or more ram, but having a swap that's at least as big as your ram will make hibernation possible.

the whole 'swap twice the size of your ram' thing isn't as applicable as it was back when most people had between 128 and 512mb ram.

and no, virtual memory / swap space is predefined and as far as i know, cant be automatically grown. it probably can with some clever scripts and LVM but it'd be more trouble than it's worth.

---

### Post by BDNiner on 2009-03-26
1) Virtual memory and swap are terms that describe the same thing. Virtual memory is space on your hard disk that the operating system uses to store information when you have used up all your RAM.

2) I don't believe there is a limit on the amount of virtual memory as long as you have the hard disk space. Once you run out of hard disk space then you cannot add more virtual memory unless you delete some data.

3) In windows you can set you virtual memory to a range, so windows will only use more virtual memory if you are running programs that require it. In Linux the virtual memory or swap size is determined when the system is installed and can only be altered using a partition editor.

---

