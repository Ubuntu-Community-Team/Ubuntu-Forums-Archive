---
title: "Seeking suggestions about how to mount partitions"
date: 2009-03-19
forum: New to Ubuntu
---

### Post by webwiller on 2009-03-19
Hi all!
I have newly repartitioned my hard drive. For a dualboot I made 4 primary partitions. One for win, one for ubuntu, a swap and a "data" partition to store my staff from both win/linux.

Last time I mounted this last shared partition as "media/data" and I had my partition showing up in ubuntu as a hard drive. As I store all of my staff in it, I didnt want to use my /home folder in ubuntu filesystem but I had to change all "places" menu and create symbolic links to point to that /media/data partition.

My question is...

Can I mount the shared partition(fat32) as /home in order to have my places menu perfect right away?

Is it best to keep it as /media/data?

What if I call it just /media? Would I be able to create any directory I like in it later?

Any other different suggestions??

Ty in advance;)

---

### Post by vanadium on 2009-03-19
> Can I mount the shared partition(fat32) as /home in order to have my places menu perfect right away?
Not at all! Your current approach, using links, is perfect.

> 
Is it best to keep it as /media/data?

It is your choice. I would rather mount a fixed internal drive under /mnt, so that it does not show on the desktop like removable media, but again: it is your choice.

> 
What if I call it just /media? Would I be able to create any directory I like in it later?

No.

> 
Any other different suggestions??

Mount your shared data drive the "old" way, i.e. using /etc/fstab. That way, it will be automatically available during start-up.

---

### Post by jacksaff on 2009-03-19
If you haven't done too much with your new system I would suggest repartitioning.
You can only have 4 primary partitions, so your system is very inflexible.
I'd suggest 1 primary for win,
1 primary for data in fat32
1 primary extended with 1 partition for swap, 1 for root and another for home. 
5 partitions in all, and with this system you can add partitions to your extended partition and you can still add another primary partition if you need to.

I wouldn't advise mounting the fat partition as /home. For one thing, I wouldn't want windows to have access to my home partition which contains a lot of configuration data. Windows doesn't respect unix permissions and it also likes to dump lots of little files all over the place wherever it finds graphics and other documents it can index. I suppose this is configurable but I don't know how to do it. It also doesn't understand that .files are supposed to be hidden so if you're browsing /home in windows you'll see loads and loads of stuff of little interest.

---

### Post by webwiller on 2009-03-19
> **vanadium said:**
> It is your choice. I would rather mount a fixed internal drive under /mnt, so that it does not show on the desktop like removable media, but again: it is your choice.


Ok, I got your point. If I call the mount point of that shared partition just /mnt, where does it show up? And does it show up as a hdd or as a directory? (sry 4ignorance...)

> **vanadium said:**
> Mount your shared data drive the "old" way, i.e. using /etc/fstab. That way, it will be automatically available during start-up.


Sry..but I'm not confident with what you are talking about..if you would be so kind to explain it step-by-step for dummies:) I'll be pleased...

ty

---

### Post by webwiller on 2009-03-19
> **jacksaff said:**
> I wouldn't advise mounting the fat partition as /home. For one thing, I wouldn't want windows to have access to my home partition which contains a lot of configuration data. Windows doesn't respect unix permissions and it also likes to dump lots of little files all over the place wherever it finds graphics and other documents it can index. I suppose this is configurable but I don't know how to do it. It also doesn't understand that .files are supposed to be hidden so if you're browsing /home in windows you'll see loads and loads of stuff of little interest.

Thx for making it easy&clear! Mhmm...I hope this wouldnt create more difficulties later on..as I am a newby. I understand your point...but...if I'll ever need to repartition the hdd, I would surely repartition the shared/primary/fat32, as it's the biggest, would I be able to do that with your planning, or I would be able to repartition only the extended one?

My disk now looks like this:
30gbNTFS/Win - 40gbEXT3 - 1gb swap - 160gbFAT32 (4primary part's)

How would you make it than? (For the time being I have only win installed, therefore I am still able to make changes to the other 3partitions)

---

