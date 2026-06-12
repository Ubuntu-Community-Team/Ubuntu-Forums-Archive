---
title: "Program Killed"
date: 2010-12-06
forum: New to Ubuntu
---

### Post by newport_j on 2010-12-06
I had a haad drive crash and had to moved my software to another computer. A laptop. I backed everything up so I was not inconvenienced by losing any code, data inputs, etc.
 
The program compiles perfectly.
 
When I run it, I get the one line message:
 
Killed
 
The program does not run. I tried to go to a nemiver code debugger and see if I can find the line on which the program was killed by stepping through the code line-by-line. The nemiver debugger froze. It simly did not operate.
 
Was could possibly be going wrong? The program oviously does not run, but the unique one word message:
 
Killed
 
is cryptic.
 
Any help appreciated, thanx in advance.
 
Newport_j

---

### Post by uRock on 2010-12-06
What is the program that is being killed?

---

### Post by talonmies on 2010-12-06
> **newport_j said:**
> 
 
When I run it, I get the one line message:
 
Killed

That usually means that the linux kernel OOM (out of memory) mechanism killed the program because it tried to alloc or consume more memory than the system has available. There should be a message in the kernel ring buffer to that effect. The dmesg command should show the message if the kernel was responsible.

I presume your laptop has less memory (either physical and/or virtual) than the machine you migrated the software from.

---

### Post by newport_j on 2010-12-06
Is there anything that I can do about it? I have read a couple of messages on the internet that one can free up memory resources and hopefully that would help.
 
If the Linux OS (in my case 10.04) is using more memory than required, then how do I reduce it?
 
 
 
Newport_j

---

### Post by talonmies on 2010-12-06
Until you can quantify the memory usage of the program in question and how much memory you have on the laptop, it is hard to say. If you are only 5-10% off being able to run, there might be counter measures to reduce the memory footprint of the OS, but if it is more, then you are probably out of luck. Hitting the OOM limit usually means you are way over the useful memory capacity of the machine, and there usually isn't much to be done except to restrict the code in question to smaller cases, or install more memory/move to a machine with more memory.

---

### Post by sgosnell on 2010-12-06
Haven't seen the code, have no idea what it does, but I would think it requires better coding to reduce the memory required.  Deallocate memory in your functions, and release anything not immediately required to be in memory.  Code optimization is a black art, and requires experience and practice.  There is always a tradeoff, since it takes time to allocate and deallocate memory, but performance may actually increase by doing it, depending on the situation.

---

### Post by no2498 on 2010-12-06
? can he not allow more swap memory
it would be a bit slower but should run

---

### Post by talonmies on 2010-12-06
> **no2498 said:**
> ? can he not allow more swap memory
it would be a bit slower but should run

"allowing" more swap memory would imply either making an additional swap partition or enlarging and existing one. Unless there is free space on a disk somewhere, that isn't such a simple proposition.

---

