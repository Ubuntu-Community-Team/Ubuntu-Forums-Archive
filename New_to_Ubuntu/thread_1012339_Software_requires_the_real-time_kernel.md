---
title: "Software requires the real-time kernel?"
date: 2008-12-15
forum: New to Ubuntu
---

### Post by User X on 2008-12-15
I am trying to run a program called EMC2.  It stands for Enhanced Machine Controller and is available from [www.linuxcnc.org](www.linuxcnc.org).  When I installed it on 8.04 it asked if I wanted to re-write the entries in grub, or leave them the way they were set.  I had to tweak the entries initially and I can't remember what I did to them so I chose to leave them the way they were set, but it may have been the wrong choice.  Can anyone tell me how to boot into the "real time kernel 2.6.24-16-rtai" It's not currently an option when I turn the power on...?

---

### Post by jerome1232 on 2008-12-15
Well you should be able to install a real time kernel via synaptic/apt-get if you type the following into a terminal it should install the latest real time kernel.

```
sudo apt-get install linux-rt
```

---

### Post by User X on 2008-12-15
How do I know what kernels are already installed?  I have a feeling EMC has loaded a real time kernel I just don't have the grub option to boot into it...?  Thanks...

---

### Post by User X on 2008-12-15
so I figured it out...

If I look in /boot I see that all my kernels are listed there.  Most of them are 2.6.24-16-generic, which is not a real time kernel.  I also noticed a new kernel listed as 2.6.24-16-rtai.  This last kernel was not showing up in grup when I started the PC so I used:

sudo gedit /boot/grub/menu.lst

to modify the kernels appearing on startup and added a duplicate entry near the end of the .lst file. I changed the -generic to -rtai.  Then when I rebooted the computer I was able to boot into the rtai real time kernel. I hope this makes sense for anyone that comes across this post looking for answers...

---

### Post by rustik on 2009-11-15
Can I make it work emc2 on kubuntu 9.4, 9.10

---

