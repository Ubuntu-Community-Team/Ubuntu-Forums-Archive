---
title: "Intrepid Ibex required specs?"
date: 2009-02-23
forum: New to Ubuntu
---

### Post by michael91 on 2009-02-23
What are the specs required to run Ibex? For the past month or so, my computer (running Ibex) has been freezing a lot. Sometimes it lasts for only a minute after logging on, sometimes a few hours. It sometimes happens when I open a few folders at the same time (during the lag); other times it doesn't. It's happened when I've moved my cursor over a hyperlink. I've given up using IM programs, solely for the fact that the computer will most likely freeze a few minutes into a conversation. As I assume this would do to any computer user, it's frustrated me to the point where I think about smashing the computer or throwing it out the window or something like that (I wouldn't really do it, though). Also, how do I check the current specs that my computer is running on?

---

### Post by supersonicdarky on 2009-02-23
[https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)

I'd guess too little ram.

Specs:
```
cat /proc/cpuinfo /proc/meminfo
```
There are better tools, but this is present already.

---

### Post by michael91 on 2009-02-24
Thanks for the links.

The page lists:

# 300 MHz x86 processor
# 64 MB of system memory (RAM)
# At least 4 GB of disk space (for full installation and swap space)
# VGA graphics card capable of 640x480 resolution
# CD-ROM drive or network card 
The specs [minus what the Mem (I assume RAM) was using at time of copy/paste] that my computer state are:

processor	: 0
vendor_id	: GenuineIntel
cpu family	: 15
model		: 4
model name	: Intel(R) Pentium(R) 4 CPU 3.00GHz
stepping	: 1
cpu MHz		: 2992.512
cache size	: 1024 KB
physical id	: 0
siblings	: 1
core id		: 0
cpu cores	: 1
apicid		: 0
initial apicid	: 0
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 3
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx constant_tsc up pebs bts pni monitor ds_cpl cid xtpr
bogomips	: 5985.02
clflush size	: 64
power management:

MemTotal:      1031976 kB
MemFree:        314664 kB

I don't really know what most of that means, so just to be sure that enough info was pasted, all, except for what the Memory's being used on, is there.

In case it's of any help, a fair few of the times that the computer has frozen, some light blue bar appears. Sometimes it's over the time/date, sometimes it's over the System Monitor that I have in the top bar, other times it's down over the tabs for the open windows.

---

### Post by michael91 on 2009-02-24
I should also state that the HDD is 80GB, I have a CD Drive (actually a DVD Burner), and my computer easily runs on 1024*768 resolution.

And, for some reason, this problem only started when I upgraded to Ibex. I was either running Gutsy or Hardy before this and the computer worked perfectly.

---

### Post by michael91 on 2009-02-25
I would love for this problem to be solved, so bump.

---

### Post by howefield on 2009-02-25
The minimum specs you post above are for running a server install, ie one with no GUI, you have to look at the minimum recommended specs further down the page.

# 700 MHz x86 processor
# 384 MB of system memory (RAM)
# 8 GB of disk space
# Graphics card capable of 1024x768 resolution
# Sound card
# A network or Internet connection 

All of which should be fairly comfortable on your machine. So it might be more likely to be a compatibility issue with your hardware, rather than pure specs.

To diagnose why it is freezing is difficult as there are many possible causes, including heat build up and failing hardware amongst others.

Edit : missed you saying it worked perfectly with previous Ubuntu versions, there is your answer. Go back to what worked, and have some piece of mind and a decent computing experience and try Jaunty when it is released. (only a few more weeks).

---

