---
title: "Hard drive partition reported as picture CD."
date: 2009-06-07
forum: New to Ubuntu
---

### Post by Bearly Able on 2009-06-07
Hi,

I have two SATA hard drives, one with Windows XP and the other with Ubuntu.  When I first installed Ubuntu (Hardy), I could mount my five Windows partitions with no problems.  Three weeks ago, I upgraded to Jaunty, I still had no problem with the partitions.  Unfortunately, I had a lot of other problems, so yesterday I did a fresh install of Intrepid.  Now three of my partitions mount OK, but the other two show a message at the top of the file browser stating "These files are on a picture CD", with an option of opening F-spot.

Can anyone explain why this has happened and help me fix it, please?

Thanks in advance.

---

### Post by LewRockwell on 2009-06-07
not sure on the answer to your difficulties but thought that while you wait you could do current back-ups/clones of the drives if you don't have them already.

(and also posting this so you know there are folks out here reading and thinking about your problem)

---

### Post by TheLions on 2009-06-07
> **Lesley Lutomski said:**
> Hi,

I have two SATA hard drives, one with Windows XP and the other with Ubuntu.  When I first installed Ubuntu (Hardy), I could mount my five Windows partitions with no problems.  Three weeks ago, I upgraded to Jaunty, I still had no problem with the partitions.  Unfortunately, I had a lot of other problems, so yesterday I did a fresh install of Intrepid.  Now three of my partitions mount OK, but the other two show a message at the top of the file browser stating "These files are on a picture CD", with an option of opening F-spot.

Can anyone explain why this has happened and help me fix it, please?

Thanks in advance.

I thing its just a typo...

F-spot detected that on removable drives are some pictures and asking if you want see them.

you should report this as a bug.

---

### Post by Bearly Able on 2009-06-07
Thanks for the replies, guys.

Thanks for the encouragement, LewRockwell.  Don't worry - I've had so many problems of late I have backups of my backups!

TheLions: I'm not sure it's a typo.  Firstly, it's never happened before.  Secondly, there are pictures on two of the other partitions that don't come up with this message.  I've tried to attach a screenshot to show what I mean.  It's my first attempt at that, so I hope it works!

---

### Post by mikechant on 2009-06-08
I'm sure I saw another post about this and it turned out to be related to the fact that the partition had a folder called 'pictures' in the root directory! Try renaming this folder.

---

### Post by Bearly Able on 2009-06-08
Hi mikechant - you are a star.  That's solved the problem.  I don't know why it's only just started happening - unless the issue only affects Intrepid?  Never mind, that's it fixed. :D  Thank you for your help.

---

