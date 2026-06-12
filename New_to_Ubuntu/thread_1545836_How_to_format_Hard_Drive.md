---
title: "How to format Hard Drive"
date: 2010-08-04
forum: New to Ubuntu
---

### Post by Krabby.Linux on 2010-08-04
Hey,

i want to change the partitions. I have installed :

Ubuntu 10.04 LTS
Ubuntu 9.10
Windows 7
Windows XP


Now i want to FORMAT (Erase) Ubuntu 9.10 completely and use the space for Ubuntu 10.04. Just found the Disk Utility but this does not work or i do not understand how this works.

Another question is ... how can i get some HD Space from Windows 7 moved to Ubuntu 10.04?

---

### Post by lukeiamyourfather on 2010-08-04
Check out GParted. Its in the repositories but not installed by default anymore.

---

### Post by Krabby.Linux on 2010-08-04
Good, Gparted, that was what i was lookign for. Used it a few month ago. Thanks

---

### Post by 23dornot23d on 2010-08-04
Can you run gparted and do a screen shot .....

Also run and post the bootscript in my footer .....

will give people a better chance ...... of working out a solution.

I do not recognise the one that you have posted (so nothing is clear to me).

( My initial thoughts .... after seeing lots of people having boot problems with 2 versions of
Windows and Linux ....... resizing and moving a windows partition has caused me to lose the boot option for it ..... but that was with Vista ... guess it depends on how much you value Windows )

You might be better off getting another hard drive as mess up something that works ok
at the moment .... 

Also are you using a 

laptop (USB drives are a good option)

or a 

desktop computer ( add a internal drive to match whatever you already have )

If adding a drive is not the option you want ...... 

Just post the gparted screenshot and the bootscript info I am sure someone will help.

**I am not keen on altering Windows any more ..... but Linux alone no problems ....**

---

### Post by Mark Phelps on 2010-08-05
> **Krabby.Linux said:**
> Another question is ... how can i get some HD Space from Windows 7 moved to Ubuntu 10.04?

Last item ... glad you're not keen on messing with Win7 anymore because using GParted to shrink that OS partition is asking for trouble.  Unless you use the Win7 Disk Management utility to shrink Win7 OS partition, you run the risk of corrupting the partition and rendering Win7 unbootable.

Also, since you have a multiboot machine, would be a good idea to boot into Win7 and use the Backup feature to create and burn a Win7 Repair CD.  That will come in handy later should you need to repair the Win7 boot loader.

---

