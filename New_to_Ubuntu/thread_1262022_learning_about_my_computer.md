---
title: "learning about my computer"
date: 2009-09-09
forum: New to Ubuntu
---

### Post by sfkrystal on 2009-09-09
hi all..

so, sysinfo says:

> general system information[INDENT]release 5.0
gnome 2.26.1 (Ubuntu 2009-05-06)
kernel 2.6.28-15-generic (#49-Ubuntu SMP Tue Aug 18 18:40:08 UTC 2009)
[/INDENT]cpu[INDENT]model name Intel(R) Pentium(R) M processor 1700MHz
l2 cache 1024 KB
[/INDENT]memory[INDENT]memory total 1002 MiB
swap total 1929 MiB[/INDENT]and I'm trying to figure out what this means.. it's a ThinkPad T41p.

how do I simplify this all down to the simplest one-line description about my computer like many of you have in your signatures? I think I'm running Xubuntu 9.04 with a 1.7GHz cpu, 1GB memory.. does that look right? I'm getting confused with all the information that the different programs/commands (sysinfo, hardinfo, lshw) give.

side question: why does lshw say I should run it as a super-user?

and another question: how do I find out the resolution of my screen?

---

### Post by Excedio on 2009-09-09
> **sfkrystal said:**
> hi all..
 
so, sysinfo says:
 
and I'm trying to figure out what this means.. it's a ThinkPad T41p.
 
how do I simplify this all down to the simplest one-line description about my computer like many of you have in your signatures? I think I'm running Xubuntu 9.04 with a 1.7GHz cpu, 1GB memory.. does that look right? I'm getting confused with all the information that the different programs/commands (sysinfo, hardinfo, lshw) give.
 
side question: why does lshw say I should run it as a super-user?
 
and another question: how do I find out the resolution of my screen?
 
 
Signatures are personal. I just happen to have a lot of detail. Going online and finding your computer specs would be good too. "1.7GHz cpu, 1GB memory" will work also.
 
Running
```
sudo lshw
```
will give you more accurate information in most cases.
 
Go to System > Preferences > Screen Resolution

---

### Post by Sealbhach on 2009-09-09
A useful tool you can use is something called "hardinfo". You can find it in Synaptic.

.

---

### Post by tgalati4 on 2009-09-09
If you go to thinkwiki.org you can find a lot of info:

[T-Series]("http://www.thinkwiki.org/wiki/Category:T_Series")

general system information

    release 5.0  (Must have been 4 earlier releases!)
    gnome 2.26.1 (Ubuntu 2009-05-06)  (This is your current version of gnome--The Desktop Manager)
    kernel 2.6.28-15-generic (#49-Ubuntu SMP Tue Aug 18 18:40:08 UTC 2009) (This is your current version of your kernel.  Important to know when some piece of hardware doesn't work, especially mixing new and really old hardware.)

cpu

    model name Intel(R) Pentium(R) M processor 1700MHz  (1.7 GHz multi-stepping Mobile (M) Centrino processor)
    l2 cache 1024 KB  (1 MB of L2 cache, this RAM is quicker than normal RAM, bigger is better.  Newer processors have 2 MB typically).  Memory goes from slow hard disk-->RAM-->L2 cache-->L1 cache-->CPU

memory

    memory total 1002 MiB  (1 GB of RAM--Your machine will take 2 GB max--2 1-gig sticks)
    swap total 1929 MiB  (Swap file is on the hard disk, useful for faking the amount of RAM you have.  Run the "free" command to show how much RAM is being used.  Total memory is real RAM + swap space, so you have ~3 GB or memory.

---

