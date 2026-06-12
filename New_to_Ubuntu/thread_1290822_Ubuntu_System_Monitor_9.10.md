---
title: "Ubuntu System Monitor 9.10"
date: 2009-10-13
forum: New to Ubuntu
---

### Post by LinuxRocks9.04 on 2009-10-13
I had recently installed Ubuntu 9.10 on my IBM ThinkCentre, and was checking the hardware info. I looked at system monitor, and it showed for the CPU info:

Processor 0: 3.00 GHz

Processor 1: 3.00 GHz

So I was just wondering whether that meant it had a dual processor or dual core setup? Or both?

---

### Post by sandyd on 2009-10-13
it can mean either one.
when you have dual core, ubuntu treats it like the cores are connected by a PAE (physical address Extension)
when there are two seperate processors, there really is a PAE between them two, so, ubuntu reconizes them as being connected with a PAE too.

---

### Post by sandyd on 2009-10-13
to find out your cpu, run
```
lshw -c cpu

```that will list all of the cpus.
for one processor, there should be one *-cpu entry
for two, there should be two *-cpu entries... and so on...

note - dual tripple and quad core procesors are counted together.

---

### Post by mick55 on 2009-10-13
open Terminal and type

```
inxi -F
```This will list all your hardware, and you will be able to see 
for yourself whether it's dual core/processors.

---

### Post by uberg on 2009-10-13
Mick I can't find the command you just posted??

---

### Post by LinuxRocks9.04 on 2009-10-13
Ok, thanks for the replies. :) I figured it out now.

I agree with uberg, it says 'command not found'. Any clarifications, mick?

---

### Post by mick55 on 2009-10-14
Sorry about that.

Oddly, it's a valid command in Linux Mint 7 which is 
based on Ubuntu 9.04, and that's the machine i spend
most of my time on any more.
Next time before i post a command i will boot up my
laptop (Jaunty 9.04) and test it on it first.

[html]http://techpatterns.com/forums/about1133.html[/html]Good catch!Thank you

Cheers
mick

---

### Post by sahabcse on 2009-10-14
try the below command

cat /proc/cpuinfo

---

### Post by uberg on 2009-10-14
Mick, one of the first Google hacks I ever learned was when you make a spelling mistake don't be so quick to correct it.  The mistake you made might lead to good results.  So your "mistake" has now turned me on to another potential tool.  I will be checking out inxi now.  THANK you.

---

