---
title: "Normal CPU usage"
date: 2009-01-19
forum: New to Ubuntu
---

### Post by fallencreations on 2009-01-19
Anyone know why my cpu usage is always at 9% or more while idling? I first thought my ram was slowing things down but I still have available memory. I am running Intrepid with a toshiba laptop. CPU = 3.02 pentium 4 -- 512mb ram

---

### Post by Blueball32 on 2009-01-19
Are you watching the graphs in the System Monitor App? If so, try and set your update rate of the graphs to 0.25 secs and see how CPU usage goes up...(one of my two cpu-cores is then always at ~100%) ;)

---

### Post by fishman78 on 2009-01-19
I had the same problem.  Try usuing htop.  It's the same, but uses terminal and doesn't consume tons of power.  Mine showed far less CPU usuage in htop.

```
sudo apt-get install htop
```

---

### Post by linux_tech on 2009-01-19
System>Admin>Sys Monitor

You can see what is using the most resources

Under processes tab, right-Click on the "Nice" value & select "Priority", from and you can modify; a higher value should use less system resources.
 (the lower the nice value, the higher the priority)

---

### Post by fallencreations on 2009-01-19
Thats interesting. Mine didn't get to 100 but went up. How do I tell true CPU usage then? Reason I'm asking is it seems like it takes longer than it should to open applications and directories. Even to close applications sometimes I see and hear the wheels spinning.

---

### Post by Kellemora on 2009-01-19
Hi Fallen

I may not explain this right, so I hope you catch what I mean, not what I say, hi hi........

Linux puts to USE whatever resources are available to it, rather than letting them sit idle and rust away.

For example, you may have one machine with 512 megs of memory and another machine with 2 gigs of memory, running the SAME program on each computer, both will show almost all the memory being used.

This is because it caches stuff you might use again, and holds it there until the memory is needed for something else.

When doing repetitive tasks, such as checking various files, the first file takes a while to load because it must load the associated program used with that file.  Then as you open each additional file, the program just pops up almost instantly, that's because it's waiting in the memory until something else takes it's place.

The CPU usage is similar.  A program that normally uses only 5% to 15% of CPU power to run may use 80% CPU power to run faster or more complexity faster to get done quicker.  But the CPU will still be showing that it's being used, even when Idle.  Now that part I haven't figured out yet.
Nor why a small program that uses little to no memory or CPU suddenly doesn't have enough memory to run, when I can open a program that uses 50 times more memory and it runs fine, right along with it.  So some things just don't make sense!

TTUL
Gary

---

