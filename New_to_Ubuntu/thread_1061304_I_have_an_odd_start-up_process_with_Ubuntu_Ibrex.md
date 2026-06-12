---
title: "I have an odd start-up process with Ubuntu Ibrex"
date: 2009-02-05
forum: New to Ubuntu
---

### Post by listerdl on 2009-02-05
Hi I am running Ubuntu Ibrex and it seems that, (for some reason) every time I boot my laptop, it decides to (I think) start a health check....

This lasts for like about a minute, and the start of the dialogue quotes this:

/dev/sdal1: clean, 121121/14537431 files 3542545/blocks

Fsck 1.
Checking file system 
1053 
fsck 1.41.3 12 Oct 2008

---

And then it lists lots of programs and applications....all with <OK> at the end of the words, which are all written in black and white

---

Have I set the ubuntu to check the system each time it reboots?

NB, All of the processes had <OK> next to them except for the firewall, that had red font saying something like <Repair>

I uninstalled FIRESTARTER and it doesnt list that application anymore.

My hunch is that I have (by accident) activated a setting to check all programs on start-up. Any thoughts?

THANKS !!!!!!!!!!!!!!!!

---

### Post by gettinoriginal on 2009-02-05
You are getting a text boot instead of the boot splash. Install startup-manager (Synaptic), after install it is under System, Administration.  From that you can choose text or splash plus other options.   :p

---

### Post by ajgreeny on 2009-02-05
I suggest you boot to the ubuntu live CD and run ```
sudo fsck /dev/sda,1
```  A manual check may help solve something that is not dealt with properly at a boot time check, though you would normally be prompted to do this if it was needed.  It can do no harm so is worth trying.

You can also run ```
sudo tune2fs /dev/sda1 -l
``` and look towards the end where the output says something like
```
Mount count:              34
Maximum mount count:      80
```which shows that the system has booted 34 times since the last check and can get to 80 boots before the next, unless there is a problem which over-rides this auto-check.  This will, at at the very least, show you your default setting, and you can, if necessary, change it to something more appropriate using another command.  See ```
man tune2fs
``` for more details.

---

### Post by listerdl on 2009-02-06
Wow - thanks. 

Very useful replies.

Thanks.

---

