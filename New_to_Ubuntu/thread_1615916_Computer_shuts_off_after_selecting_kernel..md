---
title: "Computer shuts off after selecting kernel."
date: 2010-11-07
forum: New to Ubuntu
---

### Post by asuastrophysics on 2010-11-07
Hi guys,

I've been running ubuntu studio 10.04 for 6 months now with no issues.

This morning, after coming back home, I noticed that my computer (weirdly) was off. I turned it on, and right after I select the kernel in the boot menu, the whole computer shuts off. I tried recovery mode, and it still shuts off.

I tried to boot from the livecd, and right after I select "try ubuntu without making changes to your computer", it shuts off.

How do I fix this?? What is wrong with it? I suspect an update did this. I'm running the "stable" LTS version with only canonical-approved updates selected. 

Can anyone help me?? Any help would be greatly appreciated!

---

### Post by asuastrophysics on 2010-11-07
Update: My computer seems to only be able to boot into the "Preempt" kernels. Upon booting into preempt and logging in, I got a "logging out of gnome" dialogue window that said something like this:

"Some programs are not responding, and ubuntu is waiting to shut down your computer until the following programs close: 
Gnome-Power-Manager (not responding)"

Upon rebooting and selecting the same preempt kernel, I was able to log in without issues abd install the nvidia graphics driver. Any suggestions?

---

### Post by Karakh on 2010-11-07
This makes me suspect that you have a hardware problem:

> I tried to boot from the livecd, and right after I select "try ubuntu without making changes to your computer", it shuts off.

First I would check the BIOS. Anything obviously bad? Then fix it. Everything looking fine? Load fail-safe defaults and try again.

Still no luck? If you have a spare PSU, first try swapping that out. If not, try removing everything in the system that you don't need (sound cards, net cards, fans, HDD) and boot from a live disk.

---

### Post by asuastrophysics on 2010-11-07
Thanks for your response. I selected the "load fail-safe defaults" option in the bios earlier today, but what gets me is that nothing (to my knowledge) has been changed in the bios recently.

Also, I did initially suspect a PSU issue, however, the computer boots fine into any preempt kernel I choose. It's running the 2.6.32-25-preempt kernel right now. However, I cannot boot into any "generic" kernel, or a generic recovery mode kernel. If this were a power supply issue, wouldn't it not matter which kernel I chose?

---

### Post by asuastrophysics on 2010-11-10
I restarted it (stupid mistake - should've never done that) and now it won't boot into anything. No preempt kernel, no recovery, nothing. I unplugged the power cord from every hardware piece except the motherboard and hard drive. Same thing. 

UPDATE: My power supply went out. When it did, as a kind gesture, it completely fried my motherboard. Computer is dead. 

RIP my machine.

---

