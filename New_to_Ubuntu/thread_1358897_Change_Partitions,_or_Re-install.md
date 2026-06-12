---
title: "Change Partitions, or Re-install?"
date: 2009-12-18
forum: New to Ubuntu
---

### Post by LegendarySandwich on 2009-12-18
I had Windows XP first, then I installed Ubuntu. When installing Ubuntu, I shut down my computer on accident, leaving an unusable operating system taking up space on my small hard drive. I installed Ubuntu and finished the installation this time, however I was only able to use forty giga-bytes. So now I want to increase the Ubuntu partition, decrease the Windows partition, and delete the unusable Ubuntu partition.

    Is there a program or something that I can use to change the partitions, or should I re-install Windows XP and Ubuntu? And if I should re-install the operating systems, which should I install first?

---

### Post by unmole on 2009-12-18
Boot into the Ubuntu Live cd and use Gparted from the System>Administration menu and see if you can fix it from there. If you want to reinstall, installing XP first and Ubuntu later would be better.

---

### Post by Extract_Here on 2009-12-18
I would use a live session from your iso boot and then go to (system>admin>partition editor or >Gparted) this should be the best way to do so. then  save yourself the trouble xp first and then ubuntu like the guy said above.

---

### Post by LegendarySandwich on 2009-12-18
Argh, I hate using the Live CD, it's super slow. But I will do it and see if I can figure out how to edit my partitions.

If that doesn't work, it's a re-install for me.

---

### Post by TironN on 2009-12-18
You don't need the live cd. You can install Gparted to your computer. just open terminal (or synaptic) and:
```
sudo apt-get install gparted
```

---

### Post by ezsit on 2009-12-18
> You don't need the live cd. You can install Gparted to your computer. just open terminal (or synaptic) and:

If the user wants to edit partitions they will not be able to do so from a booted system with mounted partitions. The liveCD is the only way to safely shrink/expand/delete/create partitions. Even so, I would reinstall and do Windows XP first.

---

### Post by TironN on 2009-12-19
> **ezsit said:**
> If the user wants to edit partitions they will not be able to do so from a booted system with mounted partitions. The liveCD is the only way to safely shrink/expand/delete/create partitions. Even so, I would reinstall and do Windows XP first.

Whoops yeah. I completely forgot. So yeah live cd is the go then :)

---

### Post by LegendarySandwich on 2009-12-20
I tried deleting the unusable Ubuntu partition, but it said I couldn't. What should I do?

---

### Post by -kg- on 2009-12-20
> **LegendarySandwich said:**
> I tried deleting the unusable Ubuntu partition, but it said I couldn't. What should I do?

What I would check first is to make sure it is unmounted.  You can't perform partition operations on a mounted partition.  Launch the partition editor from the Live CD, highlight the partition you wish to delete, right click it, and see if the "Unmount Volume" selection is available.  If it is, click it and then you should be able to delete the partition.

If that doesn't work, I would suggest downloading the [GPartEd Live CD]("http://gparted.sourceforge.net/livecd.php").  This is an excellent tool without the overhead of the Ubuntu Live CD.  I always use it and it works quite well for me.

---

### Post by LegendarySandwich on 2009-12-20
Okay, thanks. I will try that right now.

---

