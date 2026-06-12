---
title: "Help I'm stuck!"
date: 2008-12-23
forum: New to Ubuntu
---

### Post by orangeinapod on 2008-12-23
I just reformatted my 40GB HDD, created partitions, C: 25GB and D: 15GB. I installed Windows XP and some programs in C:

I wanted to use D: to install Ubuntu.

I used the Live CD but when it comes to the partition thingie, it's trying to partition the 25GB C: drive furthermore (the D: drive is nowhere in sight).

How should I go about installing Ubuntu in the second partition (D:) and not touching C: because I allocated that for Win XP.

Thanks a lot.

---

### Post by ugm6hr on 2008-12-23
Delete the D: partition.

Then try installing again, using the "Guided - Use largest free space"

For future reference, partitions created in Windows cannot be used to install Linux.  They need to be created as Linux partitions (& swap).

---

### Post by Duck2006 on 2008-12-23
[http://www.psychocats.net/ubuntu/dualboot](http://www.psychocats.net/ubuntu/dualboot)

---

### Post by logos34 on 2008-12-23
select 'manual' partitioning, then make a new 1 GB Primary swap partition, linux-swap, mounting at '/swap'.  Give the remaining space to ubuntu root, primary ext3, mounting at '/'

edit: I see 10 people have already responded...I'm such a slow typer!

---

### Post by orangeinapod on 2008-12-23
How do I delete the D: partition? From WinXP or from Ubuntu using the manual partition?

---

### Post by Kevbert on 2008-12-23
When you get to partitioning using the Ubuntu live CD, select manual, delete the 15Gb drive then make a new partition for swap (twice your RAM) and the rest for your main partition mounted / and formatted ext3.

---

### Post by ugm6hr on 2008-12-23
> **orangeinapod said:**
> How do I delete the D: partition? From WinXP or from Ubuntu using the manual partition?

Either.  Whichever you are comfortable with.

If you are going to mess with manual partitioning, I'd recommend a separate /home while you're at it.

---

### Post by SuperSonic4 on 2008-12-23
Is there enough room for /home and / together on 15gb. I always thought to make / at least 15gb alone

---

### Post by orangeinapod on 2008-12-23
Hi Kevbert... I'm new to Ubuntu, I'm sorry... If you could be more detailed in this area please... in the partition options, yup I found the Manual option, then I delete the 15GB, then New Partition... (now I don't understand anymore the swap, mounted /, ext3. More detailed info please.

Thanks you've been very helpful really...

---

### Post by orangeinapod on 2008-12-23
This is what I really like about the Ubuntu forum, everyone's helping each other. I really appreciate you guys taking the time answering all my questions. 

I'm new to all these terms in Linux so I hope you'll bear with me.

Thanks again.

---

### Post by ugm6hr on 2008-12-23
Read this: [http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

Decide whether you want to use a separate /home partition.

If yes: reply here.

If no: follow my earlier advice (use the Guided option after deleting D: ).

---

### Post by balaknair on 2008-12-23
Both can work. 
Depending on which version pf XP you have installed(works in XP Pro, not in Home AFAIK), you can use the disk management tool in XP(Control panel> System Management--> Disk management or manage disks or something like that) to delete the D:\ drive(which in your case is apparently an extended partition- the problem here is that we cannot boot from an extended partition, it has to be a primary partition).

Alternatively, choose the 'Manual partition' option in the Ubuntu installer, and delete and then format the extended partition with it. You will now have to decide

In this case remember that Ubuntu needs at least two partitions to be created- 
1) the root partition / (at least 5 GB)
2) the Swap partition(sized approx twice the RAM you have installed, so if you have 1 GB RAM, make the Swap partition 1.5-2 GB)

With just 15 GB for the entire install, I'd go with what logos34 suggests

---

### Post by Cannaregio on 2008-12-23
> **orangeinapod said:**
> Hi Kevbert... I'm new to Ubuntu, I'm sorry... If you could be more detailed in this area please... in the partition options, yup I found the Manual option, then I delete the 15GB, then New Partition... (now I don't understand anymore the swap, mounted /, ext3. More detailed info please.

Thanks you've been very helpful really...

To keep it simple: you need a (smaller) partition for swap (twice the size of your RAM memory) and a (bigger) partition for everything else, formatted for simplicity (if you don't really really need a different organisation) as ext3.

You must then choose where you mount the [COLOR="#0000ff"]swap[/COLOR] and where you mount [COLOR="Blue"]/[/COLOR], which means everything else.

Understand "Mounting" as "assigning". 
In GNU/Linux there are no "letter" drives, like in windows (C:, D: etc.).

Also remember that the two most important "directories" in GNU/Linux will be home (all your stuff) and media (all your disks and USB ports).

Of course you could create MORE partitions (for instance for your home directory), but you can always do that later, once you get the grip of it.

Cheers!

---

### Post by balaknair on 2008-12-23
As ugm6hr suggested, just use the 'guided' option after deleting the D:\ drive.
The Ubuntu installer will automatically take care of the rest.

---

### Post by orangeinapod on 2008-12-23
thanks guys, i'll be posting back as soon as I get this up and running. Meanwhile, i'll follow your advice to delete D: thru the partition options in Ubuntu, then just use Guided...

---

### Post by egalvan on 2008-12-23
> **balaknair said:**
> the D:\ drive(which in your case is apparently an extended partition- the problem here is that **we cannot boot from an extended partition, it has to be a primary partition).**


Are you talking about Linux?

I've got at least three dual-boot computers with a primary for Win-XP, and an extended for Linux.

Even have one machine triple-booting XP, Ubuntu & Puppy.
Ubuntu and Puppy all reside completely in the extended partition.

If you mean WinXP cannot boot from an extended...
I honestly do not remember...
Others will have to chime in.

ErnestG

---

### Post by Duck2006 on 2008-12-23
> If you mean WinXP cannot boot from an extended...
I honestly do not remember...
Others will have to chime in.

Windoze like to be on a primary partition to boot from.

---

### Post by Kevbert on 2008-12-24
The swap is used for such things as hibernation (suspend to hard disk), so that when you turn back on you don't have to go through booting up the PC from cold. It may also be used if you have large memory hungry programs running and temporarily go over your RAM memory limit (see [[COLOR="Red"]this[/COLOR]]("https://help.ubuntu.com/community/SwapFaq")).
Your swap partition does not need to be formatted and does not have a mount point.
What's left of the hard disk can be used for the root (main) partition which will store all your system and data files. The root (as it is known) is normally mounted with a mount point of / and ext3 is the standard formatting scheme. The data file part (of root) is called home and will store all your personal data and settings (more info [COLOR="Red"][here]("http://ubuntuforums.org/showthread.php?t=282018")[/COLOR], the post seems complicated at first but if you scroll down you'll see what you're after).

---

### Post by hyper_ch on 2008-12-24
It is advised to use a descriptive topic title, that means a topic title that gives some clue about the content in the thread itself...

A generic topic title like "noob here" or "need help" does not help at all. As you may have noticed, just about everyone posting in here has some kind of a problem or issue or question ;)

And it is also adviced to use seperate threads for unrelated problems so that you can mark each one individually as solved.

Or in short terms: Help others to help you ;)

Also, when you are asked to post output from (config) files or from a command, use [noparse]```

```[/noparse] brackets around (each) output. That makes it also easier to read.

---

