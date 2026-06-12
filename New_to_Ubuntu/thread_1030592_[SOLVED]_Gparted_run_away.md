---
title: "[SOLVED] Gparted run away"
date: 2009-01-04
forum: New to Ubuntu
---

### Post by Andy06 on 2009-01-04
Isn't Gparted installed on a full 8.10 installation by default? It's there on the live CD so it should be there on the full install but I don't see it. I know I can just get it in 5 seconds from the repos but I've been having trouble with programs doing a houdini on me and Gparted is something I'm SURE I did not uninstall.

---

### Post by louieb on 2009-01-04
Can't say about v8.10. but earlier versions of Ubuntu do not include Gparted on the default hard drive install.  I assume Intrepid is the same.

---

### Post by oldos2er on 2009-01-04
> **Andy06 said:**
> Isn't Gparted installed on a full 8.10 installation by default? 

 No.

---

### Post by ranch hand on 2009-01-04
If you are using one HDD you should use Gparted from the live CD anyway

---

### Post by kansasnoob on 2009-01-04
It's not installed by default but it has to be present in the Live CD for installation purposes. To install just go to terminal and:

```
sudo apt-get install gparted
```

I'll assume you know how to use it safely!

---

### Post by kansasnoob on 2009-01-04
> **ranch hand said:**
> If you are using one HDD you should use Gparted from the live CD anyway

I find it useful for a number of reasons. 

Reason #1: I'm a gui guy:)

The gparted graphic tells me much more than the output of fdisk -l:D

---

### Post by Andy06 on 2009-01-04
> Reason #1: I'm a gui guy. The gparted graphic tells me much more than the output of fdisk

You know that's an excellent point. Whenever my friends ask me how to install something, I ALWAYS ALWAYS tell them how to do it via add/remove, synaptic or whatever GUI method is there. The reason is that if you give them a terminal command, they will come back to you in the future, but if you teach them the GUI way, they find it easier to remember it and are less likely to approach you for future help. Call it the windows effect but people find it much easier to remember multiple GUI interaction then a single terminal/sudo command.

BTW, Thanks for the replies guys, I installed it (via add/remove;))

---

### Post by ranch hand on 2009-01-04
Gparted is certainly a tool that i like to have on hand too.  It is still safer to use it for partitioning from the Live CD.

I have 3 partitions with different Ubuntu installations.  They all have Gparted installed.

---

