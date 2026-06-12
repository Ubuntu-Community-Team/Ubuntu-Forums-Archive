---
title: "upgrade 8.10  to 9.04"
date: 2009-07-08
forum: New to Ubuntu
---

### Post by ADH on 2009-07-08
I have Ubuntu 8.10 on my drive (I'm looking at it, trying to learn.  I also have eComStation - OS/2 and XP.)  I have saved 9.04 to a CD.  If I use the CD to upgrade, will it place the UBuntu files on the partitions where they belong, and not interfere with the other operating systems and IBM boot manager?

Thank you.

---

### Post by philinux on 2009-07-08
You could have just got 8.10 to upgrade itself to 9.04. 

Using

```
update-manager -d
```

Never used a later livecd to upgrade. I think you would have to modify your software sources to point to the cd.

---

### Post by Revolutionary101 on 2009-07-08
I would suggest you delete the partition that Ubuntu is on then install Ubuntu on the partition you deleted. I don't know if the Ubuntu installer will let you install over an existing Ubuntu partition. 

But either way it should not mess up your boot manager or other operating systems.

---

### Post by ADH on 2009-07-08
There apparently isn't enough room on the partition to
use the update manager.  When I try, it gives me a message that I need to make more space on the drive.

---

### Post by pizza-is-good on 2009-07-08
> **philinux said:**
> You could have just got 8.10 to upgrade itself to 9.04. 
 
Using
 
```
update-manager -d
```
 
Never used a later livecd to upgrade. I think you would have to modify your software sources to point to the cd.
 
 
I'll just like to add that you will have to run the Update Manger as root. At least I had to.
```
sudo update-manager -d
```
 
Thenk click on the Upgrade button on the update manager, and you should be on your way.
 
No need to use the liveCD for anything.
 
Good luck
 
Edit - I posted this at the same time as the previous post, look at my next post for new info

---

### Post by philinux on 2009-07-08
Sounds like a serious clean up is needed.

what does 

```
df -h
```

give

---

### Post by pizza-is-good on 2009-07-08
> **ADH said:**
> There apparently isn't enough room on the partition to
use the update manager. When I try, it gives me a message that I need to make more space on the drive.
 
 
Try using gparted
```
sudo apt-get install gparted
```
to enlarge your partition.
 
This you'll have to use the Live CD for, as I don't think it gparted can work on active partitions.

---

### Post by philinux on 2009-07-08
> **pizza-is-good said:**
> I'll just like to add that you will have to run the Update Manger as root. At least I had to.
```
sudo update-manager -d
```
 
Thenk click on the Upgrade button on the update manager, and you should be on your way.
 
No need to use the liveCD for anything.
 
Good luck

You dont need sudo to run it but at the point of upgrade it will prompt for your password.

---

### Post by pizza-is-good on 2009-07-08
> **philinux said:**
> You dont need sudo to run it but at the point of upgrade it will prompt for your password.
 
It didn't when I upgraded, but then again, it could have been something that was wrong with my computer. It should work either way tho.

---

### Post by Cheesemill on 2009-07-08
> **ADH said:**
> If I use the CD to upgrade, will it place the UBuntu files on the partitions where they belong, and not interfere with the other operating systems and IBM boot manager?

You can only do an upgrade with the alternate install CD anyway, the Live CD doesn't have any packages on it so you'll have to re-install or download the Alternate CD.

---

### Post by philinux on 2009-07-08
> **Cheesemill said:**
> You can only do an upgrade with the alternate install CD anyway, the Live CD doesn't have any packages on it so you'll have to re-install or download the Alternate CD.

Good heads up. forgot that one.

---

### Post by ADH on 2009-07-22
> **Cheesemill said:**
> You can only do an upgrade with the alternate install CD anyway, the Live CD doesn't have any packages on it so you'll have to re-install or download the Alternate CD.

I thought I downloaded the proper CD, but when I tried to install, it didn't attempt to go to my Linux partition - it asked if I wanted to overwrite my XP partition (I said no.)  So, I'm not at 9.04.

---

