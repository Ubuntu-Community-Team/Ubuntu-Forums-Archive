---
title: "well this might be a big one...how do I change/remove the ubuntu partition?"
date: 2009-05-15
forum: New to Ubuntu
---

### Post by charon2112 on 2009-05-15
I just installed Ubuntu on a dual boot setup, but the partition defaulted to 2 gigabytes (even though I had 75 gigs free).  Now I don't even have enough room to install the Ubuntu updates.  How can I change the partition size or remove everything and start over...this info doesn't seem to be in the beginner's guide.

---

### Post by Cam42 on 2009-05-15
> **charon2112 said:**
> I just installed Ubuntu on a dual boot setup, but the partition defaulted to 2 gigabytes (even though I had 75 gigs free).  Now I don't even have enough room to install the Ubuntu updates.  How can I change the partition size or remove everything and start over...this info doesn't seem to be in the beginner's guide.

mmk, get [this]("http://gparted.sourceforge.net/") burn to disc, reboot compy with GParted in disc drive, resize ubuntu partition

---

### Post by kansasnoob on 2009-05-15
You can run Gparted from the Ubuntu live CD, just boot the Live CD (select run without changes to hard drive) and go to system > administration > partition editor.

Of course you **MUST** know what you're doing!

The most helpful thing would be to see a screenshot of Gparted like this:

[ATTACH]113960[/ATTACH]

---

### Post by charon2112 on 2009-05-16
I have gparted up with livecd, but I'm not sure what to do with it, can anyone help??

Thanks so much.

> **kansasnoob said:**
> You can run Gparted from the Ubuntu live CD, just boot the Live CD (select run without changes to hard drive) and go to system > administration > partition editor.

Of course you **MUST** know what you're doing!

The most helpful thing would be to see a screenshot of Gparted like this:

[ATTACH]113960[/ATTACH]

---

### Post by Don1500 on 2009-05-16
I suggest you download Gparted from [http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)
I found it's more independent and you can do what you want.

Study what it shows you, Find your Windows partition, and your Ubuntu partition. 
You should not touch that Win partition unless you want to lose windows. if you only have two partitions (1 windows and 1 ubuntu) then make a small swap partition (about the size of your RAM. then adjust your ubuntu to the size you want. Hit apply and sit back and watch all your windows go down the drain. (Opps, didn't mean that)

If you have more than one drive, click in the upper right to show your other drives. If you want to change stuff there you can. Just remember there's no going back once you format, your data is gone.

---

### Post by charon2112 on 2009-05-16
> **Don1500 said:**
> I suggest you download Gparted from [http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

Thank you Don.  gparted I have, I'm just trying to figure out the best way to shrink one partition and make another bigger.

---

### Post by Regenweald on 2009-05-16
> **charon2112 said:**
> I have gparted up with livecd, but I'm not sure what to do with it, can anyone help??

Thanks so much.

Through gparted, find the 2gig partition. Right click on it and select unmount. (if unmount is not available then it's not mounted already). IF the 75 gigs is free space, right click on the 2gig partition again and select 'resize/move'. In the resize window, you can drag the slider to resize the partition. Apply Changes.

Like so:

---

### Post by charon2112 on 2009-05-16
> **Regenweald said:**
> Through gparted, find the 2gig partition. Right click on it and select unmount. (if unmount is not available then it's not mounted already). IF the 75 gigs is free space, right click on the 2gig partition again and select 'resize/move'. In the resize window, you can drag the slider to resize the partition. Apply Changes.

Thanks, doesn't work though.  when I resize the 2.5 gig (which had unmount grayed out) it only lets me size it between the used and the free space within the 2.5 gig, which is only about 88 megabytes.  I did manage to shrink  the large partition and now I have about 15 gigs of unallocated space...but how do I get that space into my Ubuntu partition.  It's right next to it in the graphic viewing window...

Thanks guys.

---

### Post by Regenweald on 2009-05-16
is the other partition unmounted also ?
What is the other OS ? whether it's XP or Vista can make your life very easy :)

---

### Post by charon2112 on 2009-05-16
> **Regenweald said:**
> is the other partition unmounted also ?

yes,  they are all unmounted.  I have two ext3 partitions right now, one 2.5 gig that has ubuntu on it, and an empty 15 gig, can I combine them?

---

### Post by charon2112 on 2009-05-16
> **Regenweald said:**
> is the other partition unmounted also ?
What is the other OS ? whether it's XP or Vista can make your life very easy :)

it's XP

---

### Post by Regenweald on 2009-05-16
> **charon2112 said:**
> it's XP

Crap. Vista has a great partitioning utility...Could you post a shot of the partitions ? if not, and you are sure that the 15gig is just free space, you can first delete the 15gig partition then expand the 2.5 into the available space. (as long as they are right next to each other)

---

### Post by charon2112 on 2009-05-16
> **Regenweald said:**
> Crap. Vista has a great partitioning utility...Could you post a shot of the partitions ? if not, and you are sure that the 15gig is just free space, you can first delete the 15gig partition then expand the 2.5 into the available space. (as long as they are right next to each other)

I've attached a screenshot. the little blue sliver just next to the gray unallocated piece is the 2.33 Ubuntu partition.

---

### Post by Falchion on 2009-05-16
That looks like the problem. sda5 and sda6 are logical partitions within the extended partition of sad2. 

From what I know, the only way to make use of that space now is to delete sda5 and sda6, extend sda2 into that 15gigs of free space, then re-create the 2 logical partitions, one for / and the other for swap.

---

### Post by Regenweald on 2009-05-16
> **Falchion said:**
> That looks like the problem. sda5 and sda6 are logical partitions within the extended partition of sad2. 

From what I know, the only way to make use of that space now is to delete sda5 and sda6, extend sda2 into that 15gigs of free space, then re-create the 2 logical partitions, one for / and the other for swap.

I agree, but then how would Charon recover the data from the old '/' . If this is a totally fresh install, I hate to suggest it, if you do choose to delete the logical partitions you may as well simply do a fresh install utilizing the freed 17odd gigs. As always, back up relevant docs etc first.
Let us know what you think.

---

### Post by louieb on 2009-05-16
> **charon2112 said:**
> I've attached a screenshot....


[LIST]
[*]Click on the swap partition. Select swapoff. that will remove the lock from sda2 and sda6.
[*]resize sda2 to fill the unallocated space. (this is an extended partition)
[*]now you can resize sda5 to use the unallocated space.
[/LIST]

good luck

---

### Post by charon2112 on 2009-05-16
this worked perfectly, thank you!  Should I click 'swapon' now that I'm done??

> **louieb said:**
> 
[LIST]
[*]Click on the swap partition. Select swapoff. that will remove the lock from sda2 and sda6.
[*]resize sda2 to fill the unallocated space. (this is an extended partition)
[*]now you can resize sda5 to use the unallocated space.
[/LIST]

good luck

---

