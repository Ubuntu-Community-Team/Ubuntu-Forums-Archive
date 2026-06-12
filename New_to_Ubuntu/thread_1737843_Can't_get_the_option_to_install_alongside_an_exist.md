---
title: "Can't get the option to install alongside an existing OS"
date: 2011-04-23
forum: New to Ubuntu
---

### Post by BTXNick on 2011-04-23
I had three options when installing ubuntu earlier, 

1. install alongside an existing os
2. reformat entire disk
2. manually partition


Not the exact wording but you get the idea.

However, I had a problem with getting past the part where it says "waiting on you" or something of that sort. I figured quit the installation process and figured out the problem. 

But now when I try it again I don't have the option to install ubuntu alongside my existing OS (windows 7 starter).

This is really annoying, and I appreciate the help.

EDIT: I just noticed I have 4 primary partitions, could it be because of this? I read somewhere that you can only have 4 or something...

---

### Post by maverick555 on 2011-04-23
yes ! you can only have 3 primary partitions. Better just wipe out the existing Ubuntu partitions and create all logical ones.then install once again.Use manual partition this time.

---

### Post by BTXNick on 2011-04-23
> **maverick555 said:**
> yes ! you can only have 3 primary partitions. Better just wipe out the existing Ubuntu partitions and create all logical ones.then install once again.

Uh, how do I know which ones are ubuntu partitions?

Here's what I'm looking at:

[http://i13.photobucket.com/albums/a259/Btxnick/partition.png](http://i13.photobucket.com/albums/a259/Btxnick/partition.png)

---

### Post by maverick555 on 2011-04-24
what are these two partitions are? 2.67gb and 186mb partition.Seems other 3 are important.Can you delete those two ones i mentioned?

---

### Post by samacaster on 2011-04-24
You seem to have a partition nightmare on your hands! 

DO NOT delete your Recovery OR System Reserved partitions! You can remove the 2.76GB and 186MB partitions safely. Once these are gone leave the space unallocated. You've got some moving around to do. Your Windows Partitions need to be together in this order 
1. Recovery Partition
2. System Reserved (Primary)
3. Windows (Primary)

Once you have done that, expand your Windows partition to fill the rest of the drive. Keep in mind that Ubuntu will install and extended container around the actual Ubuntu itself and the swap drive. This Extended Partition will be your 3rd Primary and Ubuntu will be the 4th.

Another option would be to use the recovery options to burn recovery disc of your factory image. Once that's done you can remove the Recovery Partition is you so desire. Just don't lose those disc!

---

### Post by BTXNick on 2011-04-24
> **samacaster said:**
> You seem to have a partition nightmare on your hands! 

DO NOT delete your Recovery OR System Reserved partitions! You can remove the 2.76GB and 186MB partitions safely. Once these are gone leave the space unallocated. You've got some moving around to do. Your Windows Partitions need to be together in this order 
1. Recovery Partition
2. System Reserved (Primary)
3. Windows (Primary)

Once you have done that, expand your Windows partition to fill the rest of the drive. Keep in mind that Ubuntu will install and extended container around the actual Ubuntu itself and the swap drive. This Extended Partition will be your 3rd Primary and Ubuntu will be the 4th.

Another option would be to use the recovery options to burn recovery disc of your factory image. Once that's done you can remove the Recovery Partition is you so desire. Just don't lose those disc!


Ok, I deleted the two and I still got the same problem.

So how do I do that? How do I "move" them around? Can I do this with control panel? And why do they need to be in that order? How do I order them?

---

### Post by samacaster on 2011-04-24
Forgot to add that System Reserved contains:

[IMG]http://www.mydigitallife.info/wp-content/uploads/2009/08/windows-7-system-reserved-100mb-content.png[/IMG]

It is used by Bitlocker if you have it enabled. If not, you can remove it with Disk Management in Windows.

---

### Post by BTXNick on 2011-04-24
> **samacaster said:**
> Forgot to add that System Reserved contains:

[IMG]http://www.mydigitallife.info/wp-content/uploads/2009/08/windows-7-system-reserved-100mb-content.png[/IMG]

It is used by Bitlocker if you have it enabled. If not, you can remove it with Disk Management in Windows.

All I see is an advertisement for my digital life, is there supposed to be something else there?

---

### Post by BTXNick on 2011-04-24
bump

---

