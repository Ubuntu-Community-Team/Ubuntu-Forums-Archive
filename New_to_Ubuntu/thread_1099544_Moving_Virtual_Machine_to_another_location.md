---
title: "Moving Virtual Machine to another location"
date: 2009-03-18
forum: New to Ubuntu
---

### Post by anigodin on 2009-03-18
Hi,

I'm using Ubuntu 8.10 and my /home size is only 6GB. it's a mistake I must have done when I isntalled ubuntu but I store all my data on another disk.

The problem is that all the software is installed there including the Virtual Machine I'm using to run windows XP (only becuase my bank website does not support firefox..). the xp installation takes almost 4.5 gb of the /home and becuase of that i keep getting error messages that my /home is full/

Is there a way to move the current XP installation to another location as it is or do I need to delete it and install again and save it on another disk?

---

### Post by Kareeser on 2009-03-18
Everything is stored on a "virtual hard drive" in your home folder. It's a .vdi file you can move to wherever you'd like.

It is typically stored in ~/.Virtualbox/Machines/[MACHINE NAME]

---

### Post by Sealbhach on 2009-03-18
Depends is it VMware, Virtualbox or soemthing else?

But yes, you can just copy and paste the .vdi file.

.

---

### Post by anigodin on 2009-03-18
Thanks for the replies.

I'm using VirtualBox by Sun.

Let me see if I understand correctly: I just copy the vdi, start the VB and the windows will work?

A few days ago I copied the vdi file to another location and then tried to redirect the hard disk setting on the xp in the Virtual machine to the new location. it did not let me redirect it. I try what you suggested.

One more thing: the total size of the VirtualBox directory is 4.5GB. however, the vdi file is only 1.5Gb. what it the rest 3Gb?

---

