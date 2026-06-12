---
title: "opinions/help on/with this newbs (me) partition plan"
date: 2010-02-12
forum: New to Ubuntu
---

### Post by hortstu on 2010-02-12
I've already got linux set up in this computer but I only have 3 partitions the boot which also seems to have all my personal settings etc, the swap, and one labeled extended.

The main boot was 140 of the 155 available.  I'm in the process of shrinking it to about 37 with about 29 in use.  I imagine that most of that is what I want to make /home.  

So here it is... 

37+  for sda1 boot/ hardy heron os  ext3
30   sda?  set aside for the next LTS version of linux 
     what format should I use?
4    for swap 2x my RAM
4    for sda2  extended... currently is the same size as my swap
     what does it do?
80   or the approximate remainder set aside for /home
     What file system should I use for best results with hardy and the next LTS version?

Thanks
Mike

---

### Post by jken146 on 2010-02-12
There is a limit of four primary partitions on one disk. This is overcome by having extended partitions, which act as containers for a (potentially large) number of logical partitions. In short, you use extended partitions to increase the number of actual partitions you can have on a disk.

---

### Post by hortstu on 2010-02-12
> **jken146 said:**
> There is a limit of four primary partitions on one disk. This is overcome by having extended partitions, which act as containers for a (potentially large) number of logical partitions. In short, you use extended partitions to increase the number of actual partitions you can have on a disk.

So are you saying that my swap section is actually contained within an extended partition?  So it isn't, at the moment,2 5.8gb sections but 1 that is labeled twice in the list?

Let me know if I have that wrong.

So a few questions that I'm getting at with this thread...

Is 30gb the right size to set aside for lucid lynx?  Is it too small?  Will I be able to get away with less without performance issues?

Can I make my hardy boot partition smaller after I move all my /home stuff into the new/home partition?  If so what is a good size?

What file system should I use for my /home file if I want lucid and hardy to work flawlessly from it? 

Is there an idiots guide somewhere on how, and what, to move the appropriate files into my /home partition?

---

### Post by louieb on 2010-02-12
> **hortstu said:**
> ...
Is 30gb the right size to set aside for lucid lynx?  Is it too small?  Will I be able to get away with less without performance issues?
Since my /home and data are on separate partitions I make my / (root) partiton around 15 GB  - you could get by on less 7 - 10 GB

> Can I make my hardy boot partition smaller after I move all my /home stuff into the new/home partition?  If so what is a good size?Hardy, Jaunty, Lucid - makes no difference all use about the same amount of space. 
> What file system should I use for my /home file if I want lucid and hardy to work flawlessly from it? Have to go with ext3 - Hardy does not support ext4. -  Due to different versions of some programs such as Firefox -  not a good idea to have both use the same /home partition. Unless you use a different user for each.  
> Is there an idiots guide somewhere on how, and what, to move the appropriate files into my /home partition?[Psychocats Ubuntu Linux Resources]("http://www.psychocats.net/ubuntu/index.php")  has a guide for creating a separate home

---

### Post by jken146 on 2010-02-12
> **hortstu said:**
> So are you saying that my swap section is actually contained within an extended partition?  So it isn't, at the moment,2 5.8gb sections but 1 that is labeled twice in the list?

Yes.

---

### Post by hortstu on 2010-02-12
[QUOTE=louieb]Have to go with ext3 - Hardy does not support ext4. - Due to different versions of some programs such as Firefox - not a good idea to have both use the same /home partition. Unless you use a different user for each.[/QUOTE]

Thanks louie,

I appreciate the answers... I have some questions about the one above...

What is the advantage to ext4 over ext3?

Doesn't making a different user for each OS defeat the purpose of sharing the /home partition?

---

### Post by hortstu on 2010-02-12
Also should the partition for lucid lynx also be ext3 or should I just leave that unallocated right now?

---

### Post by jken146 on 2010-02-12
> **hortstu said:**
> What is the advantage to ext4 over ext3?
Not very much.


> **hortstu said:**
> Doesn't making a different user for each OS defeat the purpose of sharing the /home partition?
Not entirely. You can re-format the / (root) partition without touching your users' files, and you can expand/move /home as needs be in future without having to touch root.


> **hortstu said:**
> Also should the partition for lucid lynx also be ext3 or should I just leave that unallocated right now?
You can put that off until you install it. It makes no difference really.

---

### Post by hortstu on 2010-02-12
thanks jken

---

### Post by louieb on 2010-02-12
> **hortstu said:**
> ..What is the advantage to ext4 over ext3?
like jken146 - I've not found much difference. ext4 is reported to be faster - I can't tell the difference, also its suggested its  more prone to errors - I have not had a problem with ext4 yet.  
> 
Doesn't making a different user for each OS defeat the purpose of sharing the /home partition?I don't share my /home partition - have Jaunty and Lucid Alpha on the laptop. Both have a small 3GB /home partition.   Anything I want to have access to from both I keep in a separate partition - music , documents -stuff like that - the data partition takes up most of the space on the laptop.

BTW: Lucid looks pretty nice - its the fastest Ubuntu yet. Still has a lot of bugs to be worked out. If you decide to try the Alpha be sure to Google "Raising skinny elephants  is utterly boring"  - lol - its just a nicer way to reboot - that is nicer than pressing the power button.

---

### Post by hortstu on 2010-02-12
> **louieb said:**
>   
I don't share my /home partition - have Jaunty and Lucid Alpha on the laptop. Both have a small 3GB /home partition.   Anything I want to have access to from both I keep in a separate partition - music , documents -stuff like that - the data partition takes up most of the space on the laptop.


What is the difference between /home and data?  I'm kinda lost now... sorry answers always seem to make new questions.

---

### Post by jken146 on 2010-02-12
/home contains a directory for each user, which is used to store user-specific config files for many programs. This is where, for example, you firefox bookmarks and history live (in ~/.mozilla). So you can see how two OSs with the same usernames trying to share the same /home could result in config files being overwritten.

By a 'data' partition, I think louieb means that he has a separate partition not tied to any users of any OS, where he keeps files he wants to share between them.

---

### Post by louieb on 2010-02-13
[QUOTE=jBy a 'data' partition, I think louieb means that he has a separate partition not tied to any users of any OS, where he keeps files he wants to share between them.[/QUOTE]
Thats it! I do all my dual boot PCs that way.
For example my desktop is partitioned like this.  (160 GB HDD)

[LIST]
[*]Hardy root 15 GB
[*]Hardy home 3 GB
[*]Lucid root 15 GB
[*]Lucid home 3GB
[*]Data partition 120 GB
[*]Swap 2 GB
[/LIST]
> sda2  extended... currently is the same size as my swap what does it do? Might help explain what an extended / logical partition is  and how you can use it to have more that 4 partitions.  [Nuts n Boldt: Partitions 101]("http://louboldt.com/ilinuxpart.htm")

---

### Post by hortstu on 2010-02-13
Thanks louie,

I just happened to read this before you posted.
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

So I have a better grasp of partitions.

I see you have 6 partitions there... so which ones do you put into an extended partition?

By the way I'm still having major problems booting since trying to create a separate home partition... if anyone has any ideas I'm seeking help here

[http://ubuntuforums.org/showthread.php?t=1405648](http://ubuntuforums.org/showthread.php?t=1405648)

---

### Post by louieb on 2010-02-14
> **hortstu said:**
> ...I see you have 6 partitions there... so which ones do you put into an extended partition?

Since Linux does not care if it installed in a primary or logical partition it makes not difference.

On that PC - Hardy's home and root are in primary partitions. The other 4 are logical partitions.

---

