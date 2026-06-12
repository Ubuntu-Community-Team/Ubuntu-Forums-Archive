---
title: "I want to install wubi but 30 gb is not enough"
date: 2011-05-29
forum: New to Ubuntu
---

### Post by joe0134 on 2011-05-29
Ok so i want to install wubi but 30 gb is not enough so is there away to get more space i don't have a spare disk i have tried it befor and i love it but i uninstalled it because i need alot more space so if you could help me please.

---

### Post by duke.tim on 2011-05-29
There should be a cleanup tool on windows under erm accessories? You will want to uninstall programs you don't need. Delete files you don't want. Empty you recycling bin (Right click and you can make the amount it stores less) clear you internet history, cache, temp folder. 

Ccleaner will help but it takes up extra space on your HD
[http://www.piriform.com/ccleaner](http://www.piriform.com/ccleaner)

Wubi should only require 5Gb of memory
[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

I would suggest running it with this argument as the wiki says
```
--skipspacecheck
```

---

### Post by 3rdalbum on 2011-05-29
Wubi is only really applicable if you want to try out Ubuntu for a couple of days or weeks until you decide if you really want it. 30 GiB is plenty of space for that kind of use.

I'd suggest **backing up all your data** and booting up your computer from the CD, and installing Ubuntu as a dual-boot. You'll be able to allocate as much hard disk space to Ubuntu as you want and in the end you'll have a real, permanent dual-boot setup.

A reminder: BACK UP ALL YOUR IMPORTANT DATA FIRST. Usually Ubuntu's installer is pretty good with the partitioning, but there's always a slight chance of data loss.

---

### Post by joe0134 on 2011-05-29
there must be a way with out using a disk

---

### Post by Thewhistlingwind on 2011-05-29
> **joe0134 said:**
> there must be a way with out using a disk

AFAIK there isn't.

It's not important in the long run, a real install will be much more interesting, when you finally do one.

---

### Post by bcbc on 2011-05-29
> **joe0134 said:**
> there must be a way with out using a disk

It's possible... but why bother. You can run wubi with 5GB and then just store your data on the /host partition. It's not required to store all your data on the Wubi 'virtual disk'. I wouldn't recommend it either since if there is a power loss/hard shutdown you can corrupt the virtual disk and lose everything.

Wubi works well in general - but every now and then there's a thread about the root.disk going missing. It's not something you'd want to put all your important data on.

---

### Post by joe0134 on 2011-05-29
the only other think i have is a 4gb memory card would that work

---

### Post by wog on 2011-05-29
So...30gb isn't enough but you're suggesting 4gb might work?

Did you perchance mean 30mb instead of 30gb?

---

### Post by bcbc on 2011-05-30
> **joe0134 said:**
> the only other think i have is a 4gb memory card would that work

Wubi can install to your C: drive. That's the easiest place unless you don't have enough space there. Whatever you install it to has to be visible to the BIOS - otherwise it won't be possible to boot.

---

### Post by joe0134 on 2011-05-30
no i mean when you install wubi it only goes to 30gg now i have 500gg so why can i slect bigger

---

### Post by joe0134 on 2011-05-30
> **wog said:**
> So...30gb isn't enough but you're suggesting 4gb might work?

Did you perchance mean 30mb instead of 30gb?

ok so what im saying could i burn the iso to a 4gb sd card

---

### Post by joe0134 on 2011-05-30
Nevermind i got a disk im burning it now thanks anyway guys.

---

