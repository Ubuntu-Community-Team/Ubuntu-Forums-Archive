---
title: "Stuck with partitioning :/"
date: 2009-01-18
forum: New to Ubuntu
---

### Post by multiman on 2009-01-18
I thought that partitioning would be as easy as with XP, I found it is something like Win98 days.

I search using the live CD. I read a really impressive thread here for the newbies like me, the writer talked about partitioning, the primary and extended partitions.

I tried to make my partitions using Gparted, but ubuntu always chooses to be within the range of the extended partitions! and it seems to install itself on more than one partition. I then tried the manual partitioning, the setup insists that I have to make "Mount Point" for the logic partition, too.

I really cannot do anything, and didn't find a specific topic for my situation... Here what I'm willing to do, and please give some ABC steps, or give me a helpful links:

1) I'm a moderate desktop user. Never used linux as a standalone OS... Just tried dual boot for a while, but I made my choice to leave Windows.

2) I want 4 partitions; one for "Filesystem", and three for my files.

3) If I want to install XP using virtual box, can I install it on EXT3 system?


I'm talking about ubuntu 8.10

---

### Post by diablo75 on 2009-01-18
It sounds like you're trying to install Ubuntu along side windows.  In order for that to happen, the guided partitioner is trying to allow you the ability to shrink your extended partition down so it can create two new partitions.  One for your root folder and one for your swap.

The partitioning tool that is included with Ubuntu is not the best.  You should try downloaded a gparted live CD and burn that off, then boot from it.  There is little that this utility can't do.  You could use it to prep your hard drive with all the partitions that you want, then use the manual option when installing Ubuntu to set the mount points for your root (/), home (~/) and swap partitions.  Your swap partition should be made at about 2.5 times the amount of RAM you have in your PC.

---

### Post by fuser312 on 2009-01-18
do you have ubuntu preinstalled or you are trying to install a fresh ubuntu

---

### Post by cmnorton on 2009-01-18
I believe XP or almost any other Windows OS has to be installed on a supported native file system. NT through XP can be installed on FAT32 or NTFS. You might be able to install these OSs on FAT, but who would want to? I do not know what Vista's requirements are.

I believe Windows has to be installed first, or you have to doctor up the boot sector correctly, if you do not install Windows first.

Even though each Ubuntu release requires a little more system "oomph", you still can run a nice email, browser, desktop system on fairly old hardware -- you need a fair amount of RAM, but many old boxes can be maxed out to 1 or 2 GB RAM. You cannot easily run a Vista or XP system on such hardware.

Is all this work worth it to have multi-boot?

---

### Post by multiman on 2009-01-18
> **diablo75 said:**
> Your swap partition should be made at about 2.5 times the amount of RAM you have in your PC.

I have 4 GB RAM, should the swap be 8 GB?!!

[QUOTE=fuser312]do you have ubuntu preinstalled or you are trying to install a fresh ubuntu?[/QUOTE]

I'm installing fresh ubuntu

---

### Post by diablo75 on 2009-01-18
> **multiman said:**
> I have 4 GB RAM, should the swap be 8 GB?!!


Well it doesn't HAVE to be that big.  A 4 GB swap should be enough in your case.

---

### Post by mikewhatever on 2009-01-18
> **multiman said:**
> 
I tried to make my partitions using Gparted, but ubuntu always chooses to be within the range of the extended partitions! and it seems to install itself on more than one partition. I then tried the manual partitioning, the setup insists that I have to make "Mount Point" for the logic partition, too.

I really cannot do anything, and didn't find a specific topic for my situation... Here what I'm willing to do, and please give some ABC steps, or give me a helpful links:

Ubuntu usually needs at least two partitions named root and swap, and appropriate mount points must be specified for both, / and swap respectively

> 1) I'm a moderate desktop user. Never used linux as a standalone OS... Just tried dual boot for a while, but I made my choice to leave Windows.

You must be a moderate Windows user, which doesn't count, but welcome anyway.:)

> 2) I want 4 partitions; one for "Filesystem", and three for my files.

Well, that means you'll need to use an extended one, since you can't have more then 4 primary partitions on one hdd.

> 3) If I want to install XP using virtual box, can I install it on EXT3 system?

Yes, VirtualBox will create a virtual drive on the ext3 file system and install Windows there.

> **multiman said:**
> I have 4 GB RAM, should the swap be 8 GB?!!

In this case you may consider not making a swap partition, unless planning to suspend to disk, aka hibernate.

---

### Post by multiman on 2009-01-18
> **cmnorton said:**
> Is all this work worth it to have multi-boot?

Lol, that's right. And that was the reason I decided to threw XP away, and then I made my siblings do. All we need now is to patition our hard drives.


 I'm using live CD right now, and by the way I tried to use Gparted,. But, what should I do next? restart?

---

### Post by fuser312 on 2009-01-18
then there is really no need for parted
you must have windows installed. so, all you do is run the installation cd, and make three different drives and format it with ext3 (it do gives you the option of choosing the size while formatting, just pay attention to that). i will recommend make one drive as /home and then format your fourth drive and simply mount it with /. thats it.
and your swap is sufficient, it is required to be just a little more than ram but yes the more the merrier.

i am getting a feeling that i have not comprehended your problem completely but this is what i would have done.

---

### Post by multiman on 2009-01-18
mikewhatever,
Yeah, I'm just a moderate XP user :)

Well, I made two partitions for filesystem and a swap, then extended partitions. I then double click on "install", is it right? or I should restart?


> you must have windows installed
Sorry sir, but I don't have any thing on my hard disk now :(
I already made it one block.

---

### Post by cmnorton on 2009-01-18
If everything is/was backed up, you have a perfect opportunity to get the partitions created the way you want them. Given the way Ubuntu creates partitions during the install (sparingly, which I like), I'd take their default partitions. You can restrict disk access through the creation of users and privileges. You can also mount portions of hard-drives as other partitions, if you need to do that. 

The thing I do not like about partitions is you have to have a lot of experience on how much a partition needs to grow. I started out taking the default on Ubuntu. On Red Hat systems, I created /boot swap and /. There are disadvantages to that, but I've never been bitten by a loss of power problem with everything under /. I've seen instances with commercial vendors' need to have tons of partitions, and they fill up quickly, and the hardware and HDs purchased were to their specs.

---

### Post by mikewhatever on 2009-01-18
> **multiman said:**
> mikewhatever,
Yeah, I'm just a moderate XP user :)

Well, I made two partitions for filesystem and a swap, then extended partitions. I then double click on "install", is it right? or I should restart?


Yes, that's right, there is no need to reboot.

---

### Post by Moop on 2009-01-18
After you create the partitions you need to assign them mount points. I think you do that by choosing edit partition (something like that). 

There's no need to restart the pc if you created the partitions using the live cd.

---

### Post by multiman on 2009-01-18
> **mikewhatever said:**
> Yes, that's right, there is no need to reboot.

OK, now I have this problem with the two parallel coloured lines, ubuntu's percentage is in the extended partitions region. So, I choose "Manual", and the setup starts asking to make mount points, even for the logic ones, It forgets that they are extended or what?... This is my problem, which I can't even explain it... What should I do please?

---

### Post by mikewhatever on 2009-01-18
> **multiman said:**
> OK, now I have this problem with the two parallel coloured lines, ubuntu's percentage is in the extended partitions region. So, I choose "Manual", and the setup starts asking to make mount points, even for the login ones, It forgets that they are extended or what?... This is my problem, which I can't even explain it... What should I do please?

As said, you need to specify the mount points for both the system partition and for swap. The mount point for the system partition is **[B]/**[/B] and for the swap is **swap**. You have to choose those from the drop down menu.
I am not quite sure what you mean by ubuntu's percentage, you're more then welcome to post a screenshot. An application for that is under Applications->Accessories->Take Screenshot.

---

### Post by multiman on 2009-01-18
I'm sorry, really, I know I look like a goofy :$

This is when I partitioned:
[[IMG]http://img155.imageshack.us/img155/6739/29634918pl8.th.png[/IMG]](http://img155.imageshack.us/my.php?image=29634918pl8.png)

This is the "ubuntu percentage" :D
[[IMG]http://img407.imageshack.us/img407/880/56025267rz2.th.png[/IMG]](http://img407.imageshack.us/my.php?image=56025267rz2.png)

Ubuntu is trying to share the space with sda/dev7, which is an extended partition.

---

### Post by mikewhatever on 2009-01-18
So, where do you want your Ubuntu (system) partition? It looks like you have shrank sda7 to make space for Ubuntu, why not just use it?

---

### Post by multiman on 2009-01-18
I want it in sda/dev1, on the far left.

---

### Post by mikewhatever on 2009-01-18
Did you specify the mount point for sda1?

---

### Post by multiman on 2009-01-18
No, Can I specify it from Gparted?
I did it before by selecting "manual" from image 2, but then when I click forward, a message appears to tell me that if I didn't specify mount point for the other partitions, they will not be used at all.

---

### Post by mikewhatever on 2009-01-18
> **multiman said:**
> No, Can I specify it from Gparted?
I did it before by selecting "manual" from image 2, but then when I click forward, a message appears to tell me that if I didn't specify mount point for the other partitions, they will not be used at all.

That's perfectly ok, you don't need to use them right now. Once Ubuntu is successfully installed they'll be available.
You have to specify the / mount point, however. Go into Manual again, right click on sda1, select Edit, and then select the / sign for the mount point.

---

### Post by multiman on 2009-01-18
Done :)

Thank you mikewhatever, you saved me :)

---

### Post by kansasnoob on 2009-01-18
> **multiman said:**
> I thought that partitioning would be as easy as with XP, I found it is something like Win98 days.

I search using the live CD. I read a really impressive thread here for the newbies like me, the writer talked about partitioning, the primary and extended partitions.

I tried to make my partitions using Gparted, but ubuntu always chooses to be within the range of the extended partitions! and it seems to install itself on more than one partition. I then tried the manual partitioning, the setup insists that I have to make "Mount Point" for the logic partition, too.

I really cannot do anything, and didn't find a specific topic for my situation... Here what I'm willing to do, and please give some ABC steps, or give me a helpful links:

1) I'm a moderate desktop user. Never used linux as a standalone OS... Just tried dual boot for a while, but I made my choice to leave Windows.

2) I want 4 partitions; one for "Filesystem", and three for my files.

3) If I want to install XP using virtual box, can I install it on EXT3 system?


I'm talking about ubuntu 8.10

I looked at your screenshots and you are super over complicating things!

First I'd like to comment on what you said above, "ubuntu always chooses to be within the range of the extended partitions!"

Uh, yeah! To some degree that has nothing to do with Ubuntu. No hard drive, regardless of size, will allow more than four Primary partitions. One extended partition counts as one primary and each extended partition can contain many, many logical partitions.

I'm quite unclear about just what you're trying to achieve:confused:

I see no Windows partitions in play, so if this is a pure Ubuntu install I'd simply undo everything you've done and create one Primary for Ubuntu "/" (6 GB is enough - any more than 10 GB would be overkill).

Then make 2 extended partitions: One for the rest of Ubuntu ("/home" and SWAP), and the other for whatever storage you want (you can break it up into many, many separate logical partitions).

---

### Post by mikewhatever on 2009-01-18
Is it installed, still installing?
You know, I was in the same place you are not too long ago. It is confusing and intimidating, especially the mount points. :) I also got great help back then.

---

### Post by multiman on 2009-01-18
Just 10 GB for the OS?

I don't know, I thought that I need more space. Maybe I'll redo the hole thing again later, but for now, I have work tomorro, and I need to get some sleep.

thanks again guys, you were extra helpful :)

---

### Post by multiman on 2009-01-18
> It is confusing and intimidating, especially the mount points
Yeah, tell me about the mounting points, lol

Still installing by the way, reached 82% it says "scanning the mirror", I think I'll check on it tomorrow morning before I go to work.

---

