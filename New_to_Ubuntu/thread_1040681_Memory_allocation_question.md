---
title: "Memory allocation question"
date: 2009-01-15
forum: New to Ubuntu
---

### Post by grantj on 2009-01-15
Hi,

I'm certainly an absolute beginner but I have a feeling the question I have is not for beginners!

I have a quad core machine with 8G of RAM total. I'm running some data analysis which takes ~28hrs per data set and I was looking for ways to reduce the time. I found the system monitor which revealed that it was only using a single core. What I'm wondering is: is a program restricted to using one core at a time? If so, does this mean it is restricted to 2G (i.e. 1/4) of the RAM? The follow up question is: can I alter the amount of allocated RAM on each core? So that the core dedicated to this analysis program would be given say 5G and the other 3 cores 1G each. Is this possible? If so would it be complicated to carry out?

Thanks,

---

### Post by mjheagle8 on 2009-01-15
a program generally only runs on one core. to use multiple cores of the processor, there is a technology called hyperthreading. this allows multiple processes of a program to run in parallel on different cores. otherwise, they run sequentially on the same core. there is no ram per core allocation. you can only address 4gb of ram on a 32 bit system, which is why there is a limit. ram is allocated by the operating system as necessary at the program's request. 
i'm not 100% sure of all this, but this is what is true to the best of my knowledge. hope this helps!

---

### Post by grantj on 2009-01-15
Thanks for the speedy reply. 

So I think what you're saying is that each core is not restricted to 2Gb of RAM and that a single core could potentially use up to 4GB on a 32 bit system? Is that more or less correct? If so then what could a single core use on a 64 bit system?

Thanks again,

---

### Post by mjheagle8 on 2009-01-15
of course. no problem :) sure. i believe 8 gb on a 64 bit system.

---

### Post by snova on 2009-01-15
Memory is not allocated per-core. In fact, there is no connection between memory and cores. They are separate entities.

Also, the program would have to be specially designed to be able to run on multiple cores at the same time. If it's only running on one, I would make the assumption that it doesn't support it.

---

### Post by bhaverkamp on 2009-01-15
hyperthreading is not a technology for using multiple cores. It is a pre-multicore technology built into some intel processors that allows multiple threads to run simultaneously on a single core by using unused slots in the processors pipeline. In this case where the application is single threaded hyperthreading would provide the same non-boost that multiple cores do. I would check to see if your data analysis program has options to support multiple cores or perhaps has an update to provide that support.

---

### Post by mjheagle8 on 2009-01-15
> **bhaverkamp said:**
> hyperthreading is not a technology for using multiple cores. It is a pre-multicore technology built into some intel processors that allows multiple threads to run simultaneously on a single core by using unused slots in the processors pipeline. In this case where the application is single threaded hyperthreading would provide the same non-boost that multiple cores do. I would check to see if your data analysis program has options to support multiple cores or perhaps has an update to provide that support.

oh sorry, my bad. thats what i thought it did. thanks for the info!

---

### Post by bodhi.zazen on 2009-01-15
And, not to nit pick, but 32 bit OS can use up to 64 Gb RAM

[http://en.wikipedia.org/wiki/Physical_Address_Extension](http://en.wikipedia.org/wiki/Physical_Address_Extension)

---

### Post by handydan918 on 2009-01-15
@ OP:
One possibility to utilize all your cores might be to run multiple instances of the program in question, on different datasets. Can't hurt to give it a shot...

---

### Post by grantj on 2009-01-16
Yes, that's exactly what I've been doing, running 3 data sets simultaneously. It leaves 1 core un-used in case I need to do anything else.

Looking at things a bit more closely I see that even running 3 cores at 100% is only using 26% of the memory which I assume means they aren't slowing each other down and that my limitation is with CPU speed and not RAM.

Thanks for all your assistance,

---

