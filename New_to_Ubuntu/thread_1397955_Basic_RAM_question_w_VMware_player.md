---
title: "Basic RAM question w/ VMware player"
date: 2010-02-03
forum: New to Ubuntu
---

### Post by tibex on 2010-02-03
I have Ubuntu 9.1 running through VMware player on a Windows Vista machine with 4GB RAM. The VMware player has been configured to allow virtual machines to use 2+ GB RAM. However, the Ubuntu that I have installed only uses (sees, detects, is configured for.. ?) 512MB. This is verified by looking under System monitor (RAM = 497) and by typing the 'free' command (also 497). How do I get Ubuntu to see the additional RAM that I have allocated to the virtual machine?

---

### Post by samantha_ on 2010-02-03
I think your simply looking in the wrong place for the amount of ram thats detected.....

what happens if you run "top" in terminal, and at the top right (I think)
on the line that says "physmem", at the end of the line should be "used" and "unused"
add them together and see what youve got :)

---

### Post by tibex on 2010-02-04
running top shows 509336K total (512 MB). Is there something I press when Ubuntu is starting up perhaps to get to the equivalent of a BIOS to change the amount of RAM seen by the OS ?

---

### Post by theozzlives on 2010-02-04
I don't know much about VMware, but in VirtualBox you configure each virtual machine separately. I believe VirtualBox default to 512 MB RAM for Ubuntu.

---

### Post by Paqman on 2010-02-04
I agree with theozzlives. Ubuntu will use all the RAM that's available, it's your virtual machine software that's only assigning 512MB to it.

---

### Post by spongypants23 on 2010-02-04
I believe you've only told VMware to allocate 2+ GB of RAM for ALL virtual machines. You must still configure each VM seperately, telling VMWare how much RAM to give it.

---

### Post by anaconda on 2010-02-04
open vmware, and select the virtualmachine, and then select the 
"edit virtual machine settings" 
tab, and from there move the RAM slide bar to whatever you want.

PS. I dont think there is a setting for limiting the amount used for ALL virtual machines. Each virtual machine has its own allocated ram.

PSS. 512MB is a good amount for running ubuntu 9.10 in virtual machine. Do you have problems with not having enough ram in ubuntu? Or why do you want to give it more?

---

### Post by tibex on 2010-02-04
Ahhh! You are basically correct (theozzlives, spongypants23, paqman, and anaconda).
 
The VMware was resetting to 512MB because I didn't use the "power off" option under 'troubleshooting' after using the slide bar, but simply used "restart." Turns out this wasn't Ubuntu at all, but a VMware issue. Ubuntu adjusted immediately. 
 
To answer your question, anaconda, I need to use some proprietary data analysis software in Ubuntu that requires 1 GB RAM minimum.
 
Thanks all !

---

