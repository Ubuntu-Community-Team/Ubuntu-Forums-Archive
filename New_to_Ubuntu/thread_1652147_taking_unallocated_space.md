---
title: "taking unallocated space?"
date: 2010-12-24
forum: New to Ubuntu
---

### Post by gmenfan83 on 2010-12-24
ok i deleted a windows partition and would like to extend my ubuntu partition to take up my whole hard drive but cant seem to be able to resize it and take up the unallocated space ...i am currently booted in a live cd using gparted ,heres a screenshot

---

### Post by Quackers on 2010-12-24
As your Ubuntu partitions are inside an extended partition you would need to extend that extended partition first. Then you can extend your ext4 partition.
I suggest you right-click on the swap partition first and select swapoff (I'm not sure it's necessary from the live cd but better safe than sorry).
You should only do one job at a time as well.
Don't forget to turn swap back on when you've finished :-)

---

### Post by Zzl1xndd on 2010-12-24
Quackers beat me to it :)

---

### Post by Quackers on 2010-12-24
Damn that Quackers :-)

---

### Post by gmenfan83 on 2010-12-24
ok i swapped off and unmounted so now i have to extend  my ext 4 partition and then the others?

---

### Post by gmenfan83 on 2010-12-24
ok i did that and then tried to resize /move the others but i still cant get it to take up the unallocated space?

---

### Post by Quackers on 2010-12-24
No, the extended one first - sda3, then sda4. Just drag the left corner of sda3 as far left as it will go then click on the apply button. Then do the same for sda4.
Then swapon.

---

### Post by Quackers on 2010-12-24
In that screenshot you just used don't click on the green tick in the toolbar! Cancel everything there and start again.
Just do one thing at a time and then click on the green tick in the toolbar to apply the change.

---

### Post by gmenfan83 on 2010-12-24
yes i had already backed out of what i did and reset everything i could tell it was wrong ...so i think i ggot it ...heres a screenshot

---

### Post by Quackers on 2010-12-24
That's what you need to do, but I would really recommend only doing one thing at a time then clicking on the green tick to apply the change.
It would probably be ok to do 4 things at once, but it has gone badly for me in the past.

---

### Post by gmenfan83 on 2010-12-24
> **Quackers said:**
> That's what you need to do, but I would really recommend only doing one thing at a time then clicking on the green tick to apply the change.
It would probably be ok to do 4 things at once, but it has gone badly for me in the past.
ok thank you for all you help!

---

### Post by Quackers on 2010-12-24
You're welcome :-)
Be careful, partition changing is a serious business!

---

### Post by gmenfan83 on 2010-12-24
> **Quackers said:**
> You're welcome :-)
Be careful, partition changing is a serious business!
i see! well i did not need windows there anymore as i never use it so i deleted it and i had to learn either way!

---

### Post by Quackers on 2010-12-24
It may be that after the expansion of the Ubuntu partition the free space is not reported correctly. It may be necessary to expand the file system to fill the new space. If that's the case have a look at post #2 in the link below. You would need to change sda2 in that post to sda5

[http://ubuntuforums.org/showthread.php?t=1242394&highlight=resize2fs](http://ubuntuforums.org/showthread.php?t=1242394&highlight=resize2fs)

---

### Post by gmenfan83 on 2010-12-24
> **Quackers said:**
> It may be that after the expansion of the Ubuntu partition the free space is not reported correctly. It may be necessary to expand the file system to fill the new space. If that's the case have a look at post #2 in the link below. You would need to change sda2 in that post to sda5

[http://ubuntuforums.org/showthread.php?t=1242394&highlight=resize2fs](http://ubuntuforums.org/showthread.php?t=1242394&highlight=resize2fs)
how can i tell if the file system is not correct?

---

### Post by Quackers on 2010-12-24
It would still report the old size for sda5 after the changes.
Did you turn swap back on?

---

### Post by gmenfan83 on 2010-12-24
> **Quackers said:**
> It would still report the old size for sda5 after the changes.
Did you turn swap back on?
not yet it is still copying and extending sda 5

---

### Post by Quackers on 2010-12-24
Yes, it can take a while. It's copying then moving all your stuff. Maybe 2 hours or so :-(

---

### Post by gmenfan83 on 2010-12-24
> **Quackers said:**
> Yes, it can take a while. It's copying then moving all your stuff. Maybe 2 hours or so :-(
yeah it has 17 min left and started out at about 45...so once its done i can extend sda6 which is swap then thats it huh?

---

### Post by Quackers on 2010-12-24
That's only part 1. It's got to move it all yet :-(
swap should be ok left where it is. It's at the end of the disc isn't it?

---

### Post by gmenfan83 on 2010-12-24
> **Quackers said:**
> That's only part 1. It's got to move it all yet :-(
swap should be ok left where it is. It's at the end of the disc isn't it?
yes swap is at the end ,so i will just leave it be then

---

### Post by gmenfan83 on 2010-12-24
i dont think i will have to worry about the file system ,it just got done copying and moving and now is going through a process where it says its growing the filesystem to fill the partition

---

### Post by Quackers on 2010-12-24
That sounds good.

---

### Post by gmenfan83 on 2010-12-24
> **Quackers said:**
> That sounds good.
awesome ,again thank you for all your great help:p
merry christmas:D

---

### Post by Quackers on 2010-12-24
You're welcome:-)
You too!

---

