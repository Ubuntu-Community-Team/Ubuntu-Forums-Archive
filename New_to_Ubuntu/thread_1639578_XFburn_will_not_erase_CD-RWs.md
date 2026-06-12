---
title: "XFburn will not erase CD-RWs"
date: 2010-12-06
forum: New to Ubuntu
---

### Post by Ahunt on 2010-12-06
I am working with Lubuntu 10.10 installed on a Dell Dimension 2400 PC. Lubuntu runs almost perfectly, with the one exception of blanking CD-RWs using XFburn.

The CD drive is a brand new LG 22X internal IDE CD/DVD reader/writer, although this error occurred with an older Sony CD reader/writer that I had installed previously as well, so I don't believe it is hardware related. Other than this one problem XFburn and this new reader/writer work flawlessly reading CDs and DVDs and burning data and ISO CDs.

Here is the problem: When XFburn is opened and a CD or CD-RW that is already written is inserted into the drive it automatically returns the error:

```
Failed to unmount media/disk. Drive cannot be used for burning.
```

I have used a number of CD-RWs and they all return the same error. The same thing occurs when inserting a non-blank CD when XFburn is open as well. I have checked the CD-RWs that I am using by blanking them on another PC running Ubuntu 10.04  using Brasero and they blank just fine on that box.

This looks like a failure to unmount the CD so it can be erased. I have checked Launchpad to see if this is a bug and [nothing is filed there]("https://bugs.launchpad.net/ubuntu/+source/xfburn") that I found. Is there something that can be done to fix this?

---

### Post by amjjawad on 2010-12-08
OK so XFburn is a burning tool, right? how about trying another tool just to make sure at least there's nothing wrong with the Hardware?!

:)

Edit:
Is that problem has anything to do with your other thread about burning CDs or it's another separated issue?

---

### Post by conradin on 2010-12-08
Not sure if you wan to try brasero.
I've had some issues earlier versions of linux where if a disk wasn't finished, doing anything with it later would be troublesome. I haven't had that issue since Hardy Heron though.

---

### Post by Ahunt on 2010-12-08
Trying another burning tool is a good idea. I have tried Brasero on Lubuntu but it just crashes when asked to do anything. K3B seems to install and work okay, but it has outstanding [Bug 581926]("https://bugs.launchpad.net/ubuntu/+source/k3b/+bug/581926") and won't currently blank CD-RWs (I have tested it and it doesn't blank on both Ubuntu and Lubuntu), so it doesn't give any better functionality than XFburn does at present.

I like the idea of a command line tool for CD burning. Does anyone know the commands to blank a CD-RW? That would really indicate if the problem is related to the GUI front end or not.

---

### Post by amjjawad on 2010-12-08
> **Ahunt said:**
> I like the idea of a command line tool for CD burning. Does anyone know the commands to blank a CD-RW? That would really indicate if the problem is related to the GUI front end or not.

I don't know about that command but you can start any program from CLI and keep monitoring it.
For example, you could simply just write:

```
k3b

```
In the Terminal and in case of errors, the terminal will show it there.

I haven't tried k3b with RW media but so far it's so good for me.

---

### Post by Ahunt on 2010-12-08
Incidentally I started [a new thread]("http://ubuntuforums.org/showthread.php?p=10217260") to deal with the question of erasing CD-RW from the command line.
:D

---

### Post by Ahunt on 2010-12-09
Problem fixed!

As described on the [other thread on blanking by command line]("http://ubuntuforums.org/showthread.php?p=10219025#post10219025") I was able to put a CD-RW in the drive and then use:

```
sudo umount /media/disk
```

to unmount the disk before opening XFburn. When XFburn was then opened it did not crash and I was successfully able to blank the disk. It looks like XFburn has a bug in it - it should unmount the CD when it opens and it doesn't, otherwise it works fine.

I want to thank everyone who contributed here. As usual the Ubuntu Forums are an amazing source of information and everyone here is amazingly patient and polite to those of us who are still learning!

---

### Post by amjjawad on 2010-12-09
Very glad you managed to sort it out, my friend :)
Well done and I share the same opinion with you about this forum.

Did we say Linux Rules? :D

---

