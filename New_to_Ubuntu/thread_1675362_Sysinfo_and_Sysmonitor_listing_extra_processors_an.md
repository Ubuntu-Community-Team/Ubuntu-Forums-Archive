---
title: "Sysinfo and Sysmonitor listing extra processors and less RAM"
date: 2011-01-25
forum: New to Ubuntu
---

### Post by beltontennis on 2011-01-25
I am using an Intel(R) Core(TM) i5 CPU M 460  @ 2.53GHz which should only have 2 cores.  Sysinfo is listing 4 CPUs and System Monitor is tracking the usage of all 4.  

Also I have 4gig of DDR3 RAM installed and both sysinfo and system monitor are only registering 3.6gigs.  Is this behavior normal?

I am running 10.10 64bit on an Acer Aspire.

---

### Post by slooksterpsv on 2011-01-25
> **beltontennis said:**
> I am using an Intel(R) Core(TM) i5 CPU M 460  @ 2.53GHz which should only have 2 cores.  Sysinfo is listing 4 CPUs and System Monitor is tracking the usage of all 4.  

Also I have 4gig of DDR3 RAM installed and both sysinfo and system monitor are only registering 3.6gigs.  Is this behavior normal?

I am running 10.10 64bit on an Acer Aspire.

Right, that all sounds correct.

The Core i5, if it's a dual-core, has Hyper-Threading Technology, which some OSes perceive as another core/cpu, when all it is is another threader.

[quote=Wikipedia]
Hyper-threading is an Intel-proprietary technology used to improve parallelization of computations (doing multiple tasks at once) performed on PC microprocessors. **For each processor core that is physically present, the operating system addresses two virtual processors, and shares the workload between them when possible**
[/quote]

The RAM, 3.6GB sounds right cause if you don't have a dedicated graphics card (not integrated) then it uses RAM for the Display.

---

### Post by matt_symes on 2011-01-25
Hi

Open a terminal and type (case sensitive)

```
cat /proc/cpuinfo | grep processor
```

Post the results back here.

Also, in the terminal type

```
free -m
```

Post the results back here.

Kind regards

---

### Post by [Snc] on 2011-01-25
> **beltontennis said:**
> I am using an Intel(R) Core(TM) i5 CPU M 460  @ 2.53GHz which should only have 2 cores.  Sysinfo is listing 4 CPUs and System Monitor is tracking the usage of all 4.  

Also I have 4gig of DDR3 RAM installed and both sysinfo and system monitor are only registering 3.6gigs.  Is this behavior normal?

I am running 10.10 64bit on an Acer Aspire.

i5 M 460 is multithreaded, this means every core has two threads, so the system sees 4 CPUs (not 4 cores!)

Also some memory has to be reserverd and with this I5, you have, you also have embedded graphics, thus some memory could be assigned to it.

info: [http://ark.intel.com/Product.aspx?id=50179](http://ark.intel.com/Product.aspx?id=50179)

---

### Post by beltontennis on 2011-01-25
Thanks for the responses.  That makes sense.  I have the intel HD graphics which I believe is integrated so that explains the RAM issue.

Thanks.

---

### Post by monteagus on 2011-03-15
searching for a solution as the one listed above...
i find this thread...but as i read and find out that nothing is wrong i noticed that i do have a 1GB ATI Mobility Radeon™ HD5470
but i dont have it listed there...
also i was working with gimp and i dont know if this is normal but gimp seems to use all my ram  3.7g so now i dont know if ubuntu is using my graphic card or not...
:confused:

---

