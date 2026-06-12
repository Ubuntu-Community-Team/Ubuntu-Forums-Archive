---
title: "high cpu usage FLAC encoding"
date: 2009-07-23
forum: New to Ubuntu
---

### Post by rascal+1/2 on 2009-07-23
Hi 

I have 

Intel Core i7 920 @ 2.67 GHz, running Jaunty 64-bit. 
The file /proc/cpuinfo shows processors 0-7, I'm kinda confused because I thought it's quad core (from wikipedia)... Anyway, some of the processors, but not all, spike to 100% usage and plateau for about 5-10 seconds while encoding tracks. I saw this in system monitor and in top. 

Is this normal? I am pretty new to Ubuntu as well as digital music. I'm using grip/FLAC, encoding to 128 kbit.

I do not want to wear on the processor. Any thoughts?

Thanks

Josh

---

### Post by llamabr on 2009-07-23
You won't wear out the processor.  And yes, compiling or encoding is pretty cpu intensive.  You can mess with the 'nice' levels, but it's normal, I'd leave it alone.

---

### Post by DGortze380 on 2009-07-23
> **rascal+1/2 said:**
> Hi 

I have 

Intel Core i7 920 @ 2.67 GHz, running Jaunty 64-bit. 
The file /proc/cpuinfo shows processors 0-7, I'm kinda confused because I thought it's quad core (from wikipedia)... Anyway, some of the processors, but not all, spike to 100% usage and plateau for about 5-10 seconds while encoding tracks. I saw this in system monitor and in top. 

Is this normal? I am pretty new to Ubuntu as well as digital music. I'm using grip/FLAC, encoding to 128 kbit.

I do not want to wear on the processor. Any thoughts?

Thanks

Josh

Yes, encoding is processor intensive. It's fine.

---

### Post by dfreer on 2009-07-23
> **rascal+1/2 said:**
> Hi 

I have 

Intel Core i7 920 @ 2.67 GHz, running Jaunty 64-bit. 
The file /proc/cpuinfo shows processors 0-7, I'm kinda confused because I thought it's quad core (from wikipedia)

I believe that's because your processor supports Hyper Threading. The simple way of looking at it is 1 core + hyperthreading = 2 virtual processors, your 4 cores + hyperthreading = 8 virtual processors.

---

### Post by rascal+1/2 on 2009-07-24
Thanks for the peace of mind, you all rock.. Also nice to know about hyperthreading.. Just wondering, for the ondemand in the cpu applet to kick in, would then all 8 "processors" need to be at 100%, to bump up the GHz?

Josh

---

