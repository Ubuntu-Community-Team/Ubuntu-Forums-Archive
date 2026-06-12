---
title: "Top vs System Monitor"
date: 2009-01-10
forum: New to Ubuntu
---

### Post by Charger71 on 2009-01-10
Greetings,

I'm viewing System Monitor and comparing it to what the Top command is reporting and they're drastically different in what they report for RAM usage.  Please see the attachment.  If I'm reading both correctly, Top is reporting about 4gig used out of 8.  System Monitor is reporting 1.3 used out of 7.8...what gives?

Thanks,

---

### Post by zero244 on 2009-01-10
Ive noticed that too and would be interested to know.

If my eyes are not failing me it looks like you have 8-gigs of ram.
I havent seen too many people running that much memory.

Im running this machine on 1-gig, though I am thinking about adding another gig soon.

---

### Post by Charger71 on 2009-01-10
> **zero244 said:**
> Ive noticed that too and would be interested to know.

If my eyes are not failing me it looks like you have 8-gigs of ram.
I havent seen too many people running that much memory.

Im running this machine on 1-gig, though I am thinking about adding another gig soon.

You're eyes are working properly. :)  I wanted to get the most out of Vista64.  But it's cheap if you're running DDR2:
[http://www.newegg.com/Product/Product.aspx?Item=N82E16820145184]("http://www.newegg.com/Product/Product.aspx?Item=N82E16820145184")

I just installed 8.10 today on a secondary drive and after getting my ati(amd)4870 drivers running property, I'm having a blast with Ubuntu.  It's so smooth and snappy.  I resisted as long as possible before booting back into Vista, but eventually I wanted sound and the ability to play the 1 or 2 games I enjoy.  So sad!  I wouldn't even boot into windows anymore if my creative x-fi card worked and WAR had a linux version.  But I digress...

BTW: I tend to believe 'Top' over System Monitor, as I know 'Top' is a core Unix command.  Maybe 'Top' is including system cache, where System Monitor is not?

cheers!

---

### Post by cariboo on 2009-01-10
To check if the way top displays memory usage is correct in a terminal type:

```
free -m
```

The output on my 2Gb system looks like this:

```
free -m
             total       used       free     shared    buffers     cached
Mem:          1987       1238        748          0         40        642
-/+ buffers/cache:        555       1431
Swap:            0          0          0
```

Jim

---

### Post by Charger71 on 2009-01-10
> **cariboo907 said:**
> To check if the way top displays memory usage is correct in a terminal type:

```
free -m
```

The output on my 2Gb system looks like this:

```
free -m
             total       used       free     shared    buffers     cached
Mem:          1987       1238        748          0         40        642
-/+ buffers/cache:        555       1431
Swap:            0          0          0
```

Jim

Thanks Jim - 'free' displayed the same stats as 'top' did.

---

