---
title: "Hard drive plugged in not recognized"
date: 2010-01-02
forum: New to Ubuntu
---

### Post by wyatt roberts on 2010-01-02
I apparently learn best by making mistakes.  I was patitioning the drive manually to install ubuntu.  It's a big drive.  I changed my mind about my choices and the partitioner just kept plugging away so I restarted.  Now the hard drive is not recognized.  It asks for a driver or something to mount the drive.  I have another drive of the same type bought at approximately the same time if that would help but I don't see how I can even dd one drive to the other since the first is not recognized.  I hope there is an answer to this one.  I don't know where to go with this?  How do you fdisk a drive that is not visible?  Ideas?
wr

Gparted was able to see the drive when booting into several diskrescue programs didn't... So, I am repartitioning the drive there.  I suspect that will be the answer.  It's a big drive.  It will be a while.  I will report back but think this may well do it...

---

### Post by Zeedok on 2010-01-02
You've probably already sorted this out, but yes I would repartition the drive with Gparted and try again.

EDIT: If this doesn't work, boot into Windows (if you can) and reformat the drive there.

---

### Post by wyatt roberts on 2010-01-03
> **Zeedok said:**
> You've probably already sorted this out, but yes I would repartition the drive with Gparted and try again.

EDIT: If this doesn't work, boot into Windows (if you can) and reformat the drive there.

 Thanks, Gparted worked.  I am now happily partitioning my now recognized drive.    Solved.  Thanks again wyatt

---

