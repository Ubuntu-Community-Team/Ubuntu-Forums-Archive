---
title: "Source kernel refuses to be recognized"
date: 2011-08-13
forum: New to Ubuntu
---

### Post by skr5e on 2011-08-13
(NOTE: I'm running BT5 with an NVIDIA GeForce GT130M)

I've run into the apparently common problem of trying to install NVIDIA drivers and getting the problem:

> 
Error: unable to find the kernel source tree for the currently running  kernel. Please make sure you have installed the kernal source files for  your kernel and that they are properly configured Based on proposed solutions by other people, this is what I've been trying:

uname -r
> 2.6.38apt-cache search linux-source
> linux-source-2.6.38 - Linux kernel source for version 2.6.38
linux-source-2.6.38-rc8 - Linux kernel source for version 2.6.38-rc8
linux-source - BackTrack Linux Kernel Source Virtual Package
source-linux-source - BackTrack Linux Kernel Source Virtual Packageso there I see the linux source file I was supposedly supposedly missing, linux-source-2.6.38

> apt-get install linux-source-2.6.38this appeared to install fine. (typing the command again into the terminal shows this: linux-source-2.6.38 is already the newest version."

reboot 
so it seems the kernel is installed properly...

sudo sh NVIDIA-Linux-x86-280.13.run

same problem. "Error: unable to find the kernel source tree for the currently running  kernel."


I also tried 
apt-get install linux-headers -'uname -r'
based on someone's suggestion, no luck. "linux-headers-2.6.38 is already the newest version."

I've been trying to fix this problem for almost a month to no avail, it's so frustrating. Maybe I need to specify the path that the linux source is stored in? Maybe I should  install linux-source-2.6.38-rc8 instead of linux-source-2.6.38?

Any suggestions are appreciated.

---

### Post by skr5e on 2011-08-13
sorry to bump this, it got buried to the second page without any replies. Is there really no one who knows how to solve this?

---

### Post by kimda on 2011-08-14
The last time I installed nvidia from source you could give the location of the kernel headers. 

something like this:
sudo sh NVIDIA-Linux-x86-280.13.run --kernel-source=/usr/src/linux-headers

Its in the INSTALL file probably. Or maybe you can do a 

sudo sh NVIDIA-Linux-x86-280.13.run --help to get all the available switches.

---

### Post by skr5e on 2011-08-17
thanks, that really helped get me towards the right solution. I just had to use a command to specify the kernel source path. This is what worked for me:

sudo sh NVIDIA-Linux-x86-280.13.run --kernel-source-path=/usr/src/linux-source-2.6.38

That's one problem down...thanks so much!!

---

### Post by blueicewater on 2013-02-12
> **skr5e said:**
> thanks, that really helped get me towards the right solution. I just had to use a command to specify the kernel source path. This is what worked for me:

sudo sh NVIDIA-Linux-x86-280.13.run --kernel-source-path=/usr/src/linux-source-2.6.38

That's one problem down...thanks so much!!

Anyone know how to fix this error?

ERROR:  The 'version.h' kernel header file doesn't exist.

---

### Post by oldos2er on 2013-02-12
If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

---

