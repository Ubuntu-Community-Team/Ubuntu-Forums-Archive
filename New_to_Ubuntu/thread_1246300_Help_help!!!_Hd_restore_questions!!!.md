---
title: "Help help!!! Hd restore questions!!!"
date: 2009-08-21
forum: New to Ubuntu
---

### Post by NukeLuke on 2009-08-21
So, I was trying to load OSx86 on my Dell and I forgot to partion a space for the new OS, so I tried to do it from the disk and... Well, needless to say, Disk Utility had an issue (never finished) seems to have wiped everything, so I have a "blank" HD.
Now I've been told I can use my boot disk to restore Ubuntu and maybe save my files, but here's the issue, I only have the last (Jaunty?) on disk and I had updated w/o a disk to Intrepid. So, Do I need a new Intrepid disk or can I use my Jaunty? Is there a better way to go about the whole thing? I tried to load OSx86 onto an SD card so I had SOMETHING, but that seems a bust as well.

Huge Brick of an Insprion here right now... HELP!

---

### Post by wizard10000 on 2009-08-21
If the data hasn't been overwritten you may be able to recover the partitions - I've done this a couple times with good results.

Look here -

[http://www.faqs.org/docs/Linux-mini/Partition-Rescue.html](http://www.faqs.org/docs/Linux-mini/Partition-Rescue.html)

Hope this helps -

---

### Post by moocow1452 on 2009-08-21
To directly answer your question, doesn't matter. If you can see the hard drive on a live cd, regardless of Jaunty or Intrepid, you can transfer off files. Good luck, man.

---

### Post by NukeLuke on 2009-08-21
So I booted from disk and m stuck.
Rescue Mode confuses me! Should I do "partition Disk" instead?
That FAQ was totally over my head!

---

### Post by NukeLuke on 2009-08-21
Ok, So Now I'm at "Partition Disks"
and I chose: "Guided- resize... and use freed space"
Now it says that it has to "Before you select a new partition size, any previous changes have to be written to the disk
You cannot undo this operation." 
That sounds correct, b/c the other option warned it would erase everything and this seems to say it will find the old info, but I'm not sure if I understood that correctly and I'm scared of the "cannot undo" part. Is this the option I want???
Please please help

---

### Post by LewRockwell on 2009-08-21
You should stop right this instant!

.

---

### Post by LewRockwell on 2009-08-21
stop

stop

stop

just stop

.

---

### Post by LewRockwell on 2009-08-21
[http://ubuntu-rescue-remix.org/](http://ubuntu-rescue-remix.org/)

I post this so you can read through it and also visit the links provided on that webpage

still, do not do anything until you know what you are doing


unless, of course, you just want to disgard everything as lost and just reformat and do a fresh install of some operating system(s)


.

---

### Post by LewRockwell on 2009-08-21
You will need to read and understand enough of this to recover your data

or not, your choice...you can always pay a couple hundred for a tech to do it

[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

Parted Magic LiveCD utilities disk has Testdisk and Photorec amongst other fun stuff

[http://partedmagic.com/](http://partedmagic.com/)

[http://en.wikipedia.org/wiki/TestDisk](http://en.wikipedia.org/wiki/TestDisk)

[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

[http://en.wikipedia.org/wiki/PhotoRec](http://en.wikipedia.org/wiki/PhotoRec)

[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)

.

---

### Post by NukeLuke on 2009-08-21
Thank you so Much, plugging away at it, doing my best.
Sorry to bother you with all my stupidity.

---

### Post by NukeLuke on 2009-08-23
Ok, so i rad everything you sent, Len and i went throught it all very carefully and did it.
but i get: 1234f when i try to boot. Now, I know that this is a booting issue , but i just can't see how to fix it. 
i WAS running a dual-boot with windows and ubuntu, but that shouldn't be an issue.
the only other thing i understand is that at the start of recovery-remix's boot it flashes it could not find "b43/ucode.fw" and i should d/l it, but then it goes right past and seems to work.
more help for a total n00b??

---

### Post by NukeLuke on 2009-08-23
Ok, that was dumb, that's just my stupid wireless card error which i can fix later.
just re-started testdisk and it says "no partitions are bootable."
siiiiiiiigh
maybe my lack of understanding will just mean i have t pay for data recovery.

---

