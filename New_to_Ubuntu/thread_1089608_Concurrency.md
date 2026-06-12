---
title: "Concurrency"
date: 2009-03-07
forum: New to Ubuntu
---

### Post by hedge2211 on 2009-03-07
I have just read on a website that if you set the concurrency to shell it ubuntu will work better with dual core processors, as all my computers are dual core I was considering doing it. However, i was wondering what concurrency was and how it made ubuntu work better with dual core processors. 

Thanks

---

### Post by miegiel on 2009-03-07
[http://www.google.nl/search?q=set+concurrency+shell](http://www.google.nl/search?q=set+concurrency+shell) :twisted:

---

### Post by iponeverything on 2009-03-07
> **hedge2211 said:**
> I have just read on a website that if you set the concurrency to shell it ubuntu will work better with dual core processors, as all my computers are dual core I was considering doing it. However, i was wondering what concurrency was and how it made ubuntu work better with dual core processors. 

Thanks

If you are compiling a kernel you can use the -j option to increase the number of parallel processes and hence which will make the compile faster on a multi-core machine.  Concurrency is running processes parallel - Ubuntu installs the SMP kernel by default. Install htop and you can see load on individual cores. If, for instance, you are running a rendering farm, its good to make sure that different parts of the computation can be farmed out to individual cores and not block on missing pieces.

thanks miegiel, I learn something new everyday.

---

