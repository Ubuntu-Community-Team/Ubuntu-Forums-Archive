---
title: "CPU Stepping"
date: 2011-02-10
forum: New to Ubuntu
---

### Post by dalekirkwood on 2011-02-10
Can someone help me understand this please. When I check my laptop specs using 'lshw' command I get told my AMD Sempron M100 is a 800mhz when it actually a 2ghz. I have just upgraded from 10.04 to 10.10 due to a nautulis problem. On 10.04 it recognised it as a 2ghz but the system seems no slower. Can anyone help?

Thanks:confused:

---

### Post by MartyBuntu on 2011-02-10
This is a power saving feature, nothing to worry about.
The CPU will throttle down when power is not required.

The reason it may not have throttled in the past is perhaps there was an addition to the kernel that supported you hardware.

---

### Post by asmoore82 on 2011-02-10
"System -> Administration -> System Monitor" should show your
CPU's max speed on the first "System" tab.

`lshw` and "/proc/" show the speed a CPU is currently running at.

Here's a cheap test to make sure your CPU is throttling up OK:
Check CPU core(s) speed(s):
```
**grep MHz /proc/cpuinfo** 
cpu MHz		: 933.000
cpu MHz		: 933.000
cpu MHz		: 933.000
cpu MHz		: 933.000
cpu MHz		: 933.000
cpu MHz		: 933.000
cpu MHz		: 933.000
cpu MHz		: 933.000
```
Run this in 1 or 2 terminals and leave it running:
```
cat </dev/zero >/dev/null
```
Check speeds again:
```
**grep MHz /proc/cpuinfo **
cpu MHz		: 933.000
cpu MHz		: 933.000
cpu MHz		: 1734.000
cpu MHz		: 933.000
cpu MHz		: 1734.000
cpu MHz		: 933.000
cpu MHz		: 933.000
cpu MHz		: 933.000
```
^Intel® Core&#8482; i7 Quad Q740 @1.7GHz here :D.

Use Control+c to kill those `cat` processes.

---

### Post by airplanesimen on 2011-02-10
right click on your panel, and select "add to panel". then find the "Cpu frequency" (or something like that), and klick "add to panel". Then it appears an aplet where you can change your cpu speed after what you need -(and check the maximum power of your processor at once)

---

### Post by asmoore82 on 2011-02-10
> **airplanesimen said:**
> right click on your panel, and select "add to panel". then find the "Cpu frequency" (or something like that), and klick "add to panel". Then it appears an aplet where you can change your cpu speed after what you need -(and check the maximum power of your processor at once)

For my 8 logical cores, the panel applet doesn't show anything
when only 1 or 2 of them have throttled up to full speed.
But I do keep it around anyway, to make sure my system is never
accidentally switched to the "maximum performance" profile.
Might as well call that the "heat pump" profile.

---

### Post by dalekirkwood on 2011-02-10
Thanks for all your help. asmoore82 i did the test and it came out with 800mhz then 2000mhz :-). and airplanesimen the tool is very handy. thanks

---

### Post by airplanesimen on 2011-02-11
> **asmoore82 said:**
> For my 8 logical cores, the panel applet doesn't show anything
when only 1 or 2 of them have throttled up to full speed.
But I do keep it around anyway, to make sure my system is never
accidentally switched to the "maximum performance" profile.
Might as well call that the "heat pump" profile.
"heat pump" profile:P I did like that one! hehe..:popcorn:

---

