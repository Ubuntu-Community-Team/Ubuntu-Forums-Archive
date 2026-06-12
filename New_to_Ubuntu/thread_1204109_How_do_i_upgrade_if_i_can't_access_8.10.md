---
title: "How do i upgrade if i can't access 8.10?"
date: 2009-07-04
forum: New to Ubuntu
---

### Post by random turnip on 2009-07-04
On the website it says to do it through 8.10, but mine doesn't boot at all, so if i download and mount a CD with 9.04 will i be able to simply reduce the partiton of 8.10 to 0% and it will remove it?

---

### Post by Idefix82 on 2009-07-04
If you want to install 9.04 on top of 8.10, you don't need to resize partitions. Just tell Ubuntu during the installation to use the partition on which 8.10 is residing.

---

### Post by howefield on 2009-07-04
Boot with the 9.04 Live CD and at the disk partitioning step, choose manual setup and mark your 8.10 partition for formatting and mount as /  then install.

---

### Post by random turnip on 2009-07-04
I have gotten to the "prepare disk space" bit of the installation and on the slidy thing at the bottom it will only let move the slider over the Vista but not over the top of the old Ubuntu partition.
But, if i click on the "specifiy partitions manually" it turns the entire disk to the orange ubuntu colour, but if i click next will it let me specify them to get rid of the 8.10?

Shouold i click on "specify partitions manually" and click next, or will it delete everything?

---

### Post by howefield on 2009-07-04
> **random turnip said:**
> Shouold i click on "specify partitions manually" and click next, or will it delete everything?

Yes it will allow you to choose the partitions, but won't delete anything UNLESS you tell it to.

However if you are a bit unsure, you might consider getting a copy of Clonezilla and creating an image of your drive as it stands, so if you do mess it up, you have a contingency plan to get back to where you started.

Goes without saying, but as a minimum you want to back up all your documents, ect.

---

### Post by random turnip on 2009-07-04
Thank you.

I've also gotten to the prepare partitions bit, sda5 is now the new ubuntu (i formatted the old ubuntu one), do i keep the "use as" box as "swap area" and make it to the size that i want?


[edit]
Ok, it won't let me have any more than 2928MB for the new "swap area", wtf?

---

### Post by Iowan on 2009-07-04
It's unlikely you'll need more than 3G of swap.

---

### Post by earthpigg on 2009-07-04
> **random turnip said:**
> 
[edit]
Ok, it won't let me have any more than 2928MB for the new "swap area", wtf?

this wont answer your question, but.... why do you want more than 3 gigs of swap space?!

---

