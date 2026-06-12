---
title: "harddrive"
date: 2009-11-29
forum: New to Ubuntu
---

### Post by pvplahing138 on 2009-11-29
i know its wrong forums for this but i have serious problem
ok installed win 2000
and it doesnot regonize half my harddrive
i have 250 gb harddrive and now i have 150gb it says maxium
how to fix it,or is it dangerous?

---

### Post by Mark Phelps on 2009-11-29
Yeah, it's the wrong forums...

If your machine is the same age as Win  2000, then it's probably that the BIOS on the motherboard is so old that it won't recognize a drive that large.  If that's the case, unless you can upgrade the BIOS (which you would have to get from the motherboard manufacturer), there's nothing you can do to fix this -- you can't fix BIOS problems, either with MS Windows, or with Ubuntu.

---

### Post by pvplahing138 on 2009-11-29
> **Mark Phelps said:**
> Yeah, it's the wrong forums...

If your machine is the same age as Win  2000, then it's probably that the BIOS on the motherboard is so old that it won't recognize a drive that large.  If that's the case, unless you can upgrade the BIOS (which you would have to get from the motherboard manufacturer), there's nothing you can do to fix this -- you can't fix BIOS problems, either with MS Windows, or with Ubuntu.
  its somewhere 2007 years
its new and not then where 2000 was made
so its not bios problem i suspect that this is win 2000 mistake that i have new pc and harddrive and win 2000 is old  enough and dont regonize it fully
anyways thats my theory

---

### Post by howefield on 2009-11-29
Try booting up with your Ubuntu live cd and fire up gparted from the System > Administration menu. Does gparted see it all ?

Maybe you have some unallocated space.

---

### Post by halitech on 2009-11-29
> **Mark Phelps said:**
> Yeah, it's the wrong forums...

If your machine is the same age as Win  2000, then it's probably that the BIOS on the motherboard is so old that it won't recognize a drive that large.  If that's the case, unless you can upgrade the BIOS (which you would have to get from the motherboard manufacturer), there's nothing you can do to fix this -- you can't fix BIOS problems, either with MS Windows, or with Ubuntu.

Not entirely true. Its not a true "fix" persay but there are Drive overlay programs that will allow the OS to use the entire drive even if the BIOS doesn't support drives over say 137gig (just an example)

[http://en.wikipedia.org/wiki/Dynamic_drive_overlay](http://en.wikipedia.org/wiki/Dynamic_drive_overlay)

I've used them before when I had a large disk that the BIOS didn't support and the motherboard manufacturer didn't have a BIOS update.

Info from MS knowledge base: [http://support.microsoft.com/kb/186057](http://support.microsoft.com/kb/186057)

---

### Post by oldfred on 2009-11-29
Windows will not see any of the Ubuntu partitions that are formated ext3 or ext4. If the missing space just your Ubuntu install?

---

### Post by teward on 2009-11-29
[QUOTE=oldfred]Windows will not see any of the Ubuntu partitions that are formated ext3 or ext4. If the missing space just your Ubuntu install? 	[/QUOTE]

Actually, what Windows sees is an unknown partition that it can't read.  It sees the partition, and it sees that it has X amount of space (X being how much space it takes up), but it won't be able to recognize, read, access, or do anything with that partition.

---

