---
title: "Technical Specs"
date: 2009-05-28
forum: New to Ubuntu
---

### Post by kakashi_12 on 2009-05-28
Is there anywhere in Linux to view your RAM and processor speed? How much RAM will Ubuntu see? Or even better, Linux in general, how much will it see? Will it see dual-core or quad-core?

---

### Post by lisati on 2009-05-28
There are a handful of commands that might prove interesting. For example: ```
sudo dmidecode
```

---

### Post by timcredible on 2009-05-28
system->administration->system monitor->system will tell you how much memory and what kind/how many cpus you have.  as for 'will it see dual or quad core', yes, it will, unix/linux had multi-core systems long before windows.

---

### Post by kakashi_12 on 2009-05-28
awesome!

---

### Post by finer recliner on 2009-05-28
from the command line, you can generate a useful reference page using:

```
sudo lshw -html > ~/computer_specs.html
```

this will list the specs for ALL of your hardware and dump it to an html page in your home directory.

PS: this command works in ubuntu, but i'm not sure how many other distros have it.

---

### Post by fatality_uk on 2009-05-28
> **finer recliner said:**
> PS: this command works in ubuntu, but i'm not sure how many other distros have it.

Most do, or can easily get hold of it in repos.

---

### Post by mcduck on 2009-05-28
> **kakashi_12 said:**
> Is there anywhere in Linux to view your RAM and processor speed? How much RAM will Ubuntu see? Or even better, Linux in general, how much will it see? Will it see dual-core or quad-core?

cat/proc/cpuinfo will tell you information about your processor(s)
cat/proc/meminfo does the same for memory

32-bit Linux can use 32 processors/cores, and maximum of 4GB of memory (which includes not only RAM but also all the other memory addresses needed, so you usually get something around 3GB of usable RAM). USing kernel with PAE enabled will give you even more than that.

64-bit linux can address up to 64TB of physical RAM, I'm not quite sure how many processors/cores it can handle. Still a lot more than you'll be able to squeeze into any normal PC.

edit: World's current top 1 supercomputer runs Linux with 129600 cores. Although it's a cluster machine so they certainly didn't fit all those processors into single motherboard.. :D

---

### Post by kakashi_12 on 2009-05-28
good god. tb's of ram?! geez?!:popcorn:

---

