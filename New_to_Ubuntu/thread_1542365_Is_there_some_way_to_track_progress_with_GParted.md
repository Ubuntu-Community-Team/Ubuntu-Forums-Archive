---
title: "Is there some way to track progress with GParted?"
date: 2010-07-30
forum: New to Ubuntu
---

### Post by giddyup306 on 2010-07-30
Hello.  I bought a new HD, and I used GParted to create 4 partitions and format it.  It's a 320 GB hard drive, and It's been running for two hours.  I thought it would be done by now, but it's not.  Is there a way to check what percentage is done?  I see some numbers like [14479.191612].  Do these mean anything?

---

### Post by gordintoronto on 2010-07-30
Gparted should take a few seconds or a few minutes, depending on how fast your computer is.

I never stack up everything to be done at once. I say, "create a partition, do it now. Format a partition, do it now."

---

### Post by Paqman on 2010-07-30
> **giddyup306 said:**
> Is there a way to check what percentage is done?

Not so much percentage, but you can see exactly what step of the process it has got to by expanding the items in the lower window.

---

### Post by giddyup306 on 2010-07-30
That's what I thought that it should only take a few seconds.  For some reason windows doesn't like the partitions that it makes.  I have a 320 GB drive that I need to put 2000 then Xp on before Linux.  I don't know why it's not recognizing the 10 GB partition for it.  It says it's corrupt or damaged, yet I can install Linux on it fine.  It even passed with TestDisk.  Oh well I'm not going to worry about it.  Yet another Windows fail...  Thanks anyways.

---

### Post by theozzlives on 2010-07-30
> **giddyup306 said:**
> That's what I thought that it should only take a few seconds.  For some reason windows doesn't like the partitions that it makes.  I have a 320 GB drive that I need to put 2000 then Xp on before Linux.  I don't know why it's not recognizing the 10 GB partition for it.  It says it's corrupt or damaged, yet I can install Linux on it fine.  It even passed with TestDisk.  Oh well I'm not going to worry about it.  Yet another Windows fail...  Thanks anyways.

2000 is yesterdays news, why even bother. XP is quickly becoming the same. To many hackers know how to infiltrate it. Vista is garbage. If you HAVE to have Windows, use 7.

---

### Post by Mark Phelps on 2010-07-31
> **gordintoronto said:**
> Gparted should take a few seconds or a few minutes, depending on how fast your computer is.

Not necessarily true ... Depends on WHAT you're doing.

Telling folks it's only going to take seconds or minutes will tempt them to turn of the machine when they exceed that time -- leading to disastrous results.

GParted does the major stuff twice -- once in read-only mode, and a second time in write-mode.

I have actually had GParted take HOURS to expand and move a 20GB partition.

---

### Post by willjammn on 2010-07-31
I have had GParted take a long time as well, even with the Parted Magic CD.  So now I used GParted that comes withPuppy Linux.  And on my computer which is an Intel Celeron it does create a partition in a matter of seconds.

---

