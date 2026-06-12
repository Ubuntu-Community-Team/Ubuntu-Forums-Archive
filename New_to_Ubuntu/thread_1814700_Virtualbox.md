---
title: "Virtualbox"
date: 2011-07-29
forum: New to Ubuntu
---

### Post by Inodoro Pereyra on 2011-07-29
Ok, today I spent most of the day installing Ubuntu and Windows 7 in a dual boot setup, in 2 different drives. Then I got to thinking...could it be possible to run Windows inside Ubuntu, instead of the opposite?
So I did some googling, and found out about virtualbox.

Now, I have a few questions about it.

1. Would I be able to install virtualbox, and run the Windows I already installed, inside the Ubuntu I have in the other drive, or this is only a "drive inside drive" deal, pretty much like wubi?

2. If I do the virtualbox install (either way), should I expect the same kind of "instability" I was told wubi has?

3. Is there any noticeable performance loss, running Windows like that?

4. Where can I find a step by step, "virtualbox for dummies" kind of tutorial?

BTW: I'm running 10.04, and Windows 7 ultimate.

Thanks in advance. :)

---

### Post by Redblade20XX on 2011-07-29
Idk about questions 1 and 2,

3) There is always a performance loss when emulating a os within an os when compared to separate installation. It also depends on your hardware specs.

4) Check this out,
[https://help.ubuntu.com/community/VirtualBox](https://help.ubuntu.com/community/VirtualBox)

---

### Post by jerrrys on 2011-07-29
answer #4

[http://www.virtualbox.org/manual/UserManual.html](http://www.virtualbox.org/manual/UserManual.html)

---

### Post by mikewhatever on 2011-07-29
1. Check out the howto: [http://forums.virtualbox.org/viewtopic.php?t=9697#37936](http://forums.virtualbox.org/viewtopic.php?t=9697#37936)
2. Don't know what you are talking about, anyway, wubi is not the same as visualization.
3. Yes.
4. Read the manual.:)

---

### Post by Paqman on 2011-07-30
> **Inodoro Pereyra said:**
> 
1. Would I be able to install virtualbox, and run the Windows I already installed, inside the Ubuntu I have in the other drive, or this is only a "drive inside drive" deal, pretty much like wubi?

You can, but it's not straightforward at all. The normal way to use Virtualbox is to install a fresh copy of an operating system into it. Doing anything else will get very complicated very quickly.

> 
2. If I do the virtualbox install (either way), should I expect the same kind of "instability" I was told wubi has?

No. Wubi and virtualisation are completely different things. Wubi is a bit of on-disk trickery that removes the need for partitioning, but is otherwise a fairly normal dual-boot.

> 
3. Is there any noticeable performance loss, running Windows like that?

Yes, absolutely. This is because:
[LIST=1]
[*]You're running two operating systems at once. They will both share CPU cycles, RAM and disk activity. On a modern multi-core machine with plenty of RAM you can get pretty good performance, but it will push your machine.
[*]Support for hardware graphics acceleration is still quite poor in VMs. At the most you will get very limited 3D performance, don't expect to be doing any 3D gaming.
[/LIST]

> 
4. Where can I find a step by step, "virtualbox for dummies" kind of tutorial?


[http://www.virtualbox.org/wiki/End-user_documentation](http://www.virtualbox.org/wiki/End-user_documentation)

---

### Post by Inodoro Pereyra on 2011-07-30
Thanks everybody for he replies. :D

So I guess it's not gonna happen then. I have a single core Pentium 4, with only 2 gigs of RAM, and I need Windows to run Solidworks. I can't afford a performance loss. As it is, rendering with Keyshot already takes forever... 
Besides, I'm not ready to give up my sphere, just now...:biggrin:

---

### Post by Marlonsm on 2011-07-30
Virtualization (what VirtualBox does) reduces the performance in some areas, mainly with graphics, so running SolidWorks in Virtual Box wouldn't be good. You'd need either to dual boot or find an alternative for it in Linux.
And in case you do find an alternative, I'd be interested to know it also.

---

### Post by Inodoro Pereyra on 2011-07-30
> **Marlonsm said:**
> 
And in case you do find an alternative, I'd be interested to know it also.

Yeah, who wouldn't?
Unfortunately, so far, I don't know of any Linux CAD program that'd come even close to Solidworks. 

Oh, well. Dual boot it is. :neutral:

---

