---
title: "Intel Celeron or Intel Pentium 4  - which is newer or faster - ?"
date: 2009-09-26
forum: New to Ubuntu
---

### Post by mjp29 on 2009-09-26
Curious question here

I thought the Pentium 4 desktop that was given to me had a much older chip in it (and being older equals being slower) than the Intel Celeron chip laptop I'm typing on now which is an old laptop.

In my mind the Intel Celeron chips (stickers on the computers) represented that such computer had a more modern chip than any Intel Pentium chip.

But after reading about the time-line of the Intel chips on the Internet it appears that perhaps this may not be the case - ?

What command can I type into terminal on both the Celeron and Pentium 4 to see which is actually faster processor?

It appears that there were many years where Intel Pentium chips also had versions of Celeron chips at the same time.

So confusing.

All I know is that the desktop Pentium 4 appears to me as running much faster than my Intel Celeron laptop computer (both have Ubuntu on them when I notice this).

p.s. anyone old enough to remember the great problem where a Pentium chip was calculating math wrong.

---

### Post by halitech on 2009-09-26
Celeron chips have been around since the days of Pentium 3s and started with the celeron 266 so its possible that the celeron you have in the laptop is older then the P4 in the desktop.

```
lshw -C cpu
```should give you the speed of the cpu in each machine.

[http://en.wikipedia.org/wiki/List_of_Intel_Celeron_microprocessors](http://en.wikipedia.org/wiki/List_of_Intel_Celeron_microprocessors)

[http://en.wikipedia.org/wiki/List_of_Intel_Pentium_4_microprocessors](http://en.wikipedia.org/wiki/List_of_Intel_Pentium_4_microprocessors)

---

### Post by mjp29 on 2009-09-26
my laptop that i'm typing on now is (from terminal) is below

michael@michael-laptop:~$ lshw -C cpu
WARNING: you should run this program as super-user.
  *-cpu                   
       product: Mobile Intel(R) Celeron(R) CPU 2.20GHz
       vendor: Intel Corp.
       physical id: 2
       bus info: cpu@0
       version: 15.2.9
       size: 18EHz
       width: 32 bits
       capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe up pebs bts cid xtpr
       configuration: id=0
michael@michael-laptop:~$ 

the desktop that i just typed in the same thing in terminal reported the below

my Pentium 4 is below (from Terminal command) is

michael@michael-desktop:~$ lshw -C cpu
WARNING: you should run this program as super-user.
  *-cpu                   
       product: Intel(R) Pentium(R) 4 CPU 2.80GHz
       vendor: Intel Corp.
       physical id: 1
       bus info: cpu@0
       version: 15.4.1
       serial: 0000-0F41-0000-0000-0000-0000
       size: 18EHz
       width: 32 bits
       capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe constant_tsc up pebs bts pni dtes64 monitor ds_cpl cid xtpr
       configuration: id=0
michael@michael-desktop:~$


But the ultimate question is this:  Which computer (the Celeron laptop) or the Intel Pentium 4 desktop is the faster processor (or even the newer computer) - who cares really which one is newer but which one is faster?

Some care about both, I do.  I for one would find it extremely interesting if one chip was newer but could hold less ram than the other (I know for a fact that the Celeron chip would not allow us/me to add much ram to).


p.s. (or ps,ps) what could one type into terminal on both machines to see how much ram they have now and how much ram each could take ... perhaps the amount of ram each has/or can take are important considerations too.

---

### Post by powel212 on 2009-09-26
Great way to test your cpu

[http://ubuntuforums.org/showthread.php?t=60264](http://ubuntuforums.org/showthread.php?t=60264)

Powel

---

### Post by Bölvaður on 2009-09-26
> **mjp29 said:**
> p.s. (or ps,ps) what could one type into terminal on both machines to see how much ram they have now and how much ram each could take ... perhaps the amount of ram each has/or can take are important considerations too.

```
free -m
``` where m stands for megabytes (MiB) but you can change it for k or something, you might want to read upon this command to undertsand the output.


Also [http://dl.getdropbox.com/u/955154/super.tar.gz]("http://dl.getdropbox.com/u/955154/super.tar.gz") (sorry I cannot find the linux version of super pi)

This is just to see how fast your cpu calculates, so it gives a good estimate.
[more info]("http://ubuntuforums.org/showthread.php?t=60264")

---

### Post by powel212 on 2009-09-26
linux version of super pi [here]("http://ubuntuforums.org/attachment.php?attachmentid=129903&d=1254021912")

extract it to your home directory and run

```
sudo ./super_pi 20
```

---

### Post by anewguy on 2009-09-26
Several things can affect the apparent speed - the amount of memory, how much of it is being used, the video adapter and driver and speed of its' memory and pipelines, the chipset support on the motherboard - especially northbridge and southbridge (or just the 1 if the newer single bridge chips), the actual speed of the CPU and the cache for the cpu to name a few.  Even though the Celeron says 2.2ghz, the Celeron will have a smaller cache than the P4.  If I remember correctly, I *think* there was a version of the P4 (I may be thinking of something else here) that had 2 "cores" - not as sophisticated as todays dual-core cpus, but 2 "cores" none the less.

Sometimes things can be easy - a vast difference in available memory and total memory, a hard drive with a larger buffer, higher transfer rate and rotational speed, etc., while others can be a little more obscure.

Dave :)

EDIT:  Should add as an example that most cheaper laptops use a 4200 rpm drive with a low amount of cache.  Most desktop drives will be at least 5400 rpm, usually 7200 rpm, and have larger cache.  Just this alone can make a large difference in perceived speed.

---

### Post by halitech on 2009-09-26
Based on the speeds posted, the desktop has the faster processor (2.8 vs 2.2)

The amount of ram, running apps willa also contribute to how the machine runs. Its not the chip which may have the limit on the ram but more likely the motherboard in the machine.

to check the ram type in ```
free -m
```

---

### Post by Lightstar on 2009-09-26
assuming you have the same ram memory, I'd go with the pentium 4, definitely.

Celeron is the "budget" type of processor.  It's cheaper, and not as good as a pentium 4.

---

### Post by powel212 on 2009-09-26
One important thing to remember about the old P4 CPUs is that they run Very hot. Hot enough to cook themselves so be sure you have a good and clean heat-sync and a good fan. Many computer manufacturers in the P4 days put nice fast expensive CPUs in their machines and then put a stupid little 2Dollar fan on them. When the fan quits your chip will fry very quickly. A good heat sync and fan can be purchased for about 10-15 Bucks US. With a good fan these old processors can run well for years.

Powel

---

### Post by wdzieczny on 2009-09-27
If I remember correctly (unsure if this still stands today) The Celeron chip was just a PIII/4 chip that failed somewhere in the quality control of The Pentium chip.

---

