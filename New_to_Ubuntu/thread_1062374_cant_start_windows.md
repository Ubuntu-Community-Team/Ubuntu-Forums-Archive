---
title: "cant start windows"
date: 2009-02-06
forum: New to Ubuntu
---

### Post by doghand on 2009-02-06
hi hope u can help. my friend has asked me to look at his system. hes running vista and installed ubuntu without checking things and now he cant access his windows files. tried to boot into windows restore(f11) but just continued starting ubuntu. is there a way to get into windows to solve his problems?

---

### Post by caro on 2009-02-06
When he installed Ubuntu, did he create a new partition or install Ubuntu over Windows?  If he didn't partition, he overwrote Windows.  I don't know of any way to recover his files and he will have to reload Windows if he wants to use that OS.

---

### Post by mvalviar on 2009-02-06
How did he install ubuntu? wubi? Live CD? Please give a little more detail.

---

### Post by Doug11 on 2009-02-06
> **doghand said:**
> hi hope u can help. my friend has asked me to look at his system. hes running vista and installed ubuntu without checking things and now he cant access his windows files. tried to boot into windows restore(f11) but just continued starting ubuntu. is there a way to get into windows to solve his problems?
I ran into this problem a long time ago. trying to remember what I did. Try a search on "restore grub" or 'fix mbr" I can't remember which was my solution. I'll have a look to and see what i can find.

---

### Post by doghand on 2009-02-06
he did it when he was drunk.....so he aint sure...lol
ill just need to take out his drive and run it as a slave to get a good look at it.
thanks

---

### Post by doghand on 2009-02-06
> **mvalviar said:**
> How did he install ubuntu? wubi? Live CD? Please give a little more detail.

he downloaded onto a disc and ran from that.
still got the disc at his.

---

### Post by Spherical on 2009-02-06
Boot an Ubuntu live-disk

Check your menu.lst by mounting your linux-disk.
Correct all problems.

You should be able to fix it that way, I think.

Unless offcourse, he overwrote the Windows installation...

---

### Post by doghand on 2009-02-06
> **Spherical said:**
> Boot an Ubuntu live-disk

Check your menu.lst by mounting your linux-disk.
Correct all problems.

You should be able to fix it that way, I think.

Unless offcourse, he overwrote the Windows installation...


hi i know nothing of linux at all so the above doesnt mean much. sorry

---

### Post by Doug11 on 2009-02-06
Get or make a GParted Live cd and run that. It will show you for sure if he deleted the windows partition. It is a small program that you run that edits your partitions. Do a search for it and you should find it fairly easily. Stick it on a cd and you should be able to boot from it.

---

### Post by jimmy the saint on 2009-02-06
You don't need to get any livecd except for the one you already have.  Put in the Ubuntu cd.  When it boots into Ubuntu (from the cd) go to System>Administration>partition manager and see if he still has the Windows partition.  If it is there, it is just a matter of fixing the Grub (bootloader) menu.  If it is gone, he will learn not to do destructive operations drunk and with no backup!

---

