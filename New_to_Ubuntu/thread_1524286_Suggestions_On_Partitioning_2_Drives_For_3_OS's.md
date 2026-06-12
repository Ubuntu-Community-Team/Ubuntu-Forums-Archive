---
title: "Suggestions On Partitioning 2 Drives For 3 OS's?"
date: 2010-07-05
forum: New to Ubuntu
---

### Post by walkerchuckwalker on 2010-07-05
I have just bought a Dell computer and then bought a new hard drive. I now have 2 500GB hard drives installed. I want to put Windows 7, Ubuntu and Backtrack 4 on my computer. I was wondering what some ideas for how I should set them up? Things I want:
1. Windows 7: I want this to have most of the space 250GB+
2. Ubuntu: I want this to be able to edit GRUB2 for all the OS's ~100GB
3. Backtrack 4: I want to have a good amount of space ~100GB 

So which drives should I put these on and what order should I put them on?

---

### Post by Darkness Des on 2010-07-05
Windows first. It makes your life MUCH easier. Then Ubuntu, and install the boot loader to the MBR (Windows may erase this, I'm working on a solution right now), then Backtrack4.

---

