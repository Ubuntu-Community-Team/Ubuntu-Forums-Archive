---
title: "4GB on 64 bit OS?"
date: 2009-08-04
forum: New to Ubuntu
---

### Post by AaronD on 2009-08-04
Hello all - I have a laptop with a 64 bit proc.  I have 4 GB of memory.  I installed Ubuntu 9.04 Desktop, 64 bit.  I am only seeing 3.1 GB available in the OS, much like a 32 bit OS.

How do I get the system to recognize the full 4GB?  It is seen as 4 GB in the BIOS.  I'm surprised I can' see it out of the box at install.

Any ideas?

Thank you!

Aaron

---

### Post by Hospadar on 2009-08-04
Are you sure the laptop supports the full 4GB? Motherboards typically have a limit to what they will support, especially laptops.

And how are you looking at the memory?  I usually use "top" or better, "htop" from the terminal to check these things.

---

### Post by Cypher on 2009-08-04
First things first, regardless of what Ubuntu sees. What is your BIOS seeing for total memory? if it's seeing 4GB, you can further debug why Ubuntu isn't seeing all of it..

---

### Post by AaronD on 2009-08-04
Yes - The machine sees 4096 GB in the BIOS.  I just used the System Information Widget you can add to the top bar.  I will do a top later today (I have to swap the drive back into it that has Ubuntu on it).

Does the 64 bit kernel support 4 GB without recompiling the kernel?  You would think that it would but I did a few google searches and old results (2006-2007) stated you had to recompile the kernel, even with 64 bit.  That has to be old information, right?

---

### Post by halitech on 2009-08-04
the newer kernels are supposed to see 64gig (I think) and shouldn't need to recompile the kernel to see it. You can also use ```
free -m
``` to see your memory amounts.

---

### Post by AaronD on 2009-08-04
Here are the results:

From top: 3302908k total
From free -m: 3225 total used 649 free 2576

---

### Post by LowSky on 2009-08-04
does your computer share it memory with the graphics chip? If yes than that's the reason

---

### Post by AaronD on 2009-08-04
It does, but it is variable (at least it is under XP) and 256MB max.  That still leaves me a good bit short.  While that is part of it, I can't see how it is taking 700MB or so.

---

### Post by niteshifter on 2009-08-04
> **AaronD said:**
> It does, but it is variable (at least it is under XP) and 256MB max.  That still leaves me a good bit short.  While that is part of it, I can't see how it is taking 700MB or so.

Depends upon how that 'aperture hole" for video mem is mapped. On some systems, when it is mapped (via BIOS setup) all memory from the mapped base upward disappears from the OS' view of memory. Check your BIOS setup and see if you can move the aperture upward.

---

