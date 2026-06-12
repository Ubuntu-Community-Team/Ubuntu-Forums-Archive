---
title: "A couple issues I can't sort myself. Ubuntu 9.04"
date: 2009-06-12
forum: New to Ubuntu
---

### Post by T4K3Z0U on 2009-06-12
I got a new laptop a few days ago and installed 8.10 then a mate recommended 9.04, so I installed the desktop version since it appears 9.04 does not exist for laptops. I think this may be my main problem, but here are the issues I have experienced.

First was with 8.10, I couldn't get wifi to work. But thankfully when I upgraded to 9.04 this issue was resolved.

So moving onto the problems with 9.04.

My laptop won't restart or shutdown 99% of the time, it just sits there as a black screen with a little blinking dash, so I have to force it to shutdown.

With vista after installing 8.10 and now with 9.04, it keeps either taking me to the disk recovery center, or trying to do a disk scan, each and every time. Not too big of deal since I don't want to use vista.

Next is sound problems, though I discuss that in [this]("http://http://ubuntuforums.org/showthread.php?p=7444547#post7444547") thread the other day.

There were a few others but they slip my mind right now, but the latest and greatest problem which p!ss me right off. I had to restart for whatever reason and then I got this message.

> GRUB loading stage 1.5.

GRUB loading please wait...

Error 17

Now what the heck is that? And why or how does this happen in just a few days?

I'm assuming I will need to reinstall, so here are some questions. I take it I should use 8.10 for my laptop, but since wifi won't work, is there a way to fix this?
I couldn't figure how to remove 8.10 when I installed 9.04 so just shrunk that partition. How can I completely remove both partitions and start again from scratch.

Please help a complete dunce out here. I simply am still too green with Ubuntu even after all this time.

---

### Post by labinnsw on 2009-06-12
I can help with one of the issues you have. Removing the Ubuntu Partitions.
(I can probably help with the grub, but since I am not confident, I will leave it until I review my notes or for someone else with more knowledge and experience.)

To remove the Ubuntu partitions:

Boot up into Ubuntu with the live CD.
Start up the Partition Editor (System >> Administration >> Partition Editor)
Delete the Ubuntu Partition. (you can delete any partition you want from here.)

[See video tutorial]("http://www.youtube.com/watch?v=NefYp80dUkY")

---

### Post by T4K3Z0U on 2009-06-12
> **labinnsw said:**
> I can help with one of the issues you have. Removing the Ubuntu Partitions.
(I can probably help with the grub, but since I am not confident, I will leave it until I review my notes or for someone else with more knowledge and experience.)

To remove the Ubuntu partitions:

Boot up into Ubuntu with the live CD.
Start up the Partition Editor (System >> Administration >> Partition Editor)
Delete the Ubuntu Partition. (you can delete any partition you want from here.)

[See video tutorial]("http://www.youtube.com/watch?v=NefYp80dUkY")

I was going to reinstall before, but when it came time to do the partitions, there are 6. 2 windows, 1x10gb, 1x50gb (I made the 50gb one, know nothing about 10gb) 2 Ubuntu, and two swap partitions. I have no idea what the swap partitions are for, perhaps Ubuntu, but I left everything alone coz I don't want to bugger the entire thing. I don't think warranty would cover me now I have tried changing OS.

I just noticed the link now, will check it out. Also right now am using live cd. If possible fixing the grub would be much more convenient.

Won't let me watch the video for some reason. Asks to instal flash which I can't do because 64bit. Before this grub issue, I was able to watch youtube....

---

### Post by Miljet on 2009-06-12
Perhaps I can clear up some misconceptions.

> so I installed the desktop version since it appears 9.04 does not exist for laptops
There is not a specific version of Ubuntu for laptops. The desktop version is to differentiate between the desktop edition (with Gnome) and the server edition (with no desktop environment.)

The smaller Windows partition is probably a recovery partition that was in place when you got your computer. The main Windows system will be on the larger partition.

It sounds like you installed Ubuntu 9.04 alongside the other operating systems instead of overwriting the 8.10 version. That would mean that you have both Ubuntu 8.10 and Ubuntu 9.04 installed. It also seems that you installed a second swap partition at the same time.

There should not be a reason to completely reinstall, unless you just want to clean up your partitions.

Please open a terminal (Applications -> Accessories -> terminal) and post the output of ```
sudo fdisk -l
```
That will give us a better idea of what you are dealing with.

---

### Post by T4K3Z0U on 2009-06-12
First some good news, I reinstalled grub and that has fixed the grub error for now.

> **Miljet said:**
> 
It sounds like you installed Ubuntu 9.04 alongside the other operating systems instead of overwriting the 8.10 version. That would mean that you have both Ubuntu 8.10 and Ubuntu 9.04 installed. It also seems that you installed a second swap partition at the same time.

Turns out it was only 8.04 not .10 not sure why but there it is. The disk must have installed the second swap coz it wasn't me directly. So swap is related to uBuntu?


> **Miljet said:**
> There should not be a reason to completely reinstall, unless you just want to clean up your partitions.

Please open a terminal (Applications -> Accessories -> terminal) and post the output of ```
sudo fdisk -l
```
That will give us a better idea of what you are dealing with.

I want to get rid of 8.04, its taking up about 5gb space and it is useless to me. 

As requested, here is a picture of terminal output from above code. Notice sda4 is missing?

---

### Post by Miljet on 2009-06-12
> So swap is related to uBuntu?
Correct. Ubuntu creates a swap partition that it uses to swap data from the memory when the memory gets full. In other words, the swap space stores information that normally would be kept in memory if there is not enough room in memory. There is no reason to have two swap partitions. Also your swap partitions seem excessive. It only needs to be slightly larger than the amount of memory installed in your computer.

> Notice sda4 is missing? 
That is perfectly normal. sda3 is an extended partition and sda5, sda6, and sda7 are all logical partitions within sda3. Since a disk can contain up to 4 primary partitions, logical partitions start numbering a sdx5.

You can fix the partitions by booting from a live CD and using gparted to change partition sizes. You cannot change partitions while mounted so you have to use the live CD. If you are going to make changes to either of the swap partitions, which I recommend, you should open the terminal and issue the command "swapoff -a". The reason is that when you boot from a live CD, if there is a swap partition available, it will activate it.

Although resizing partitions is a relatively safe operation, it is always a good idea to back up any critical data BEFORE proceeding.

If you have any questions or anything is not clear, please ask.

---

### Post by T4K3Z0U on 2009-06-13
> **Miljet said:**
>  There is no reason to have two swap partitions. Also your swap partitions seem excessive. It only needs to be slightly larger than the amount of memory installed in your computer.

So I should delete one, and resize the other? Sounds simple enough.


> **Miljet said:**
> 
You can fix the partitions by booting from a live CD and using gparted to change partition sizes. You cannot change partitions while mounted so you have to use the live CD. If you are going to make changes to either of the swap partitions, which I recommend, you should open the terminal and issue the command "swapoff -a". The reason is that when you boot from a live CD, if there is a swap partition available, it will activate it.

Although resizing partitions is a relatively safe operation, it is always a good idea to back up any critical data BEFORE proceeding.

If you have any questions or anything is not clear, please ask.

Is it possible for me to delete 8.04 and the swap partition, as well as shrinking the other swap partition using gParted in Ubuntu without the live cd? And of course then to add the free space to 9.04?

---

### Post by michy99 on 2009-06-13
> **T4K3Z0U said:**
> So I should delete one, and resize the other? Sounds simple enough.




Is it possible for me to delete 8.04 and the swap partition, as well as shrinking the other swap partition using gParted in Ubuntu without the live cd? And of course then to add the free space to 9.04?

You can't make changes to a partition while it is mounted. That is why you need to do it from the Live CD.

---

### Post by T4K3Z0U on 2009-06-13
> **michy99 said:**
> You can't make changes to a partition while it is mounted. That is why you need to do it from the Live CD.

OK that makes sense. 

So how do I access gparted in the live cd? Is that ```
sudo aptitude install gparted
sudo gparted
``` or some other way?

---

### Post by Bradtek on 2009-06-13
Gparted should already be installed on the Live CD

System Menu | Administration | Partition Editor

---

### Post by T4K3Z0U on 2009-06-15
> **Miljet said:**
>  If you are going to make changes to either of the swap partitions, which I recommend, you should open the terminal and issue the command "swapoff -a". The reason is that when you boot from a live CD, if there is a swap partition available, it will activate it.

Used that command and got the following message > Not super user

Tried to delete 8.04 and got this following message.

> Unable to delete /dev/sda5!
Please unmount any logical partitions having a number higher than 5.

Yes, I did try this using the live cd.

---

### Post by Elfy on 2009-06-15
You need to swapoff - it will likely be in the extended partition - hence the logical partitions having a number higher than 5 warning.

When you are in partition editor of the livecd you can right click and swapoff - all swaps need to be turned off. In the terminal you need sudo for it to work

```
sudo swapoff -a
```

---

### Post by T4K3Z0U on 2009-06-15
OK things have worked a little, I have deleted 8.04, deleted 1 swap partition and shrunk the other. Now I am trying to enlarge my 9.04 partition but something seems a bit off. It was going to take about an hour to shift to the left and grow to the desired size, it was about halfway done when I left home, when I returned however it was back to less than 25% complete saying its going to take about 3hrs.

Does it normally redo the growing or have I buggered something already? It still says 0 of 1 operations completed, so I figure it hasn't moved onto the second part of any task.

---

### Post by T4K3Z0U on 2009-06-15
I got there in the end. Wasn't expecting it to take 7hrs, but oh well.

I still have one problem left regarding partitioning. I'm not sure how, but for some reason I have a 1MiB unallocated slot at the beginning of my partitions and a 6.33GiB unallocated slot at the end. The 6.33G one is from when I reduced a swap, my problem is, I don't know how to add it to my main partition, gparted won't let me use it to grow the partition. The only option I see available is to turn it into a new partition.

Oh and there is an exclamation mark beside the vista partition, is that normal, or is that indication an issue? That might explain why it wants to do either a disk check or disk scan every time I use it.

Here's a screenshot too.

---

### Post by sandyd on 2009-06-15
> **T4K3Z0U said:**
> I got there in the end. Wasn't expecting it to take 7hrs, but oh well.

I still have one problem left regarding partitioning. I'm not sure how, but for some reason I have a 1MiB unallocated slot at the beginning of my partitions and a 6.33GiB unallocated slot at the end. The 6.33G one is from when I reduced a swap, my problem is, I don't know how to add it to my main partition, gparted won't let me use it to grow the partition. The only option I see available is to turn it into a new partition.

Oh and there is an exclamation mark beside the vista partition, is that normal, or is that indication an issue? That might explain why it wants to do either a disk check or disk scan every time I use it.

Here's a screenshot too.
ubuntu sometimes can't allocate the entire disk. just leave the 1mb there, create a new partition in the 6GB and use it as a backup place.
That exclamation mark means youll probably want to start backing up your data. you also might want to run testdisk, but i guess it doesn't matter since your not really using vista.

---

### Post by T4K3Z0U on 2009-06-15
> **carlee said:**
> ubuntu sometimes can't allocate the entire disk. just leave the 1mb there, create a new partition in the 6GB and use it as a backup place.
That exclamation mark means youll probably want to start backing up your data. you also might want to run testdisk, but i guess it doesn't matter since your not really using vista.

Guess Vista really hates other operating systems on the same disk. Nothing there to backup I don't think, plus at the moment it was not able to tell me how much of the 50GiB was in use.

After just rebooting now, I got the damn error 17 message again, so reinstalled the grub. Last time the grub was (h0,5), now it was (h0,4) and the grub page still shows 8.04. Is that normal?

---

