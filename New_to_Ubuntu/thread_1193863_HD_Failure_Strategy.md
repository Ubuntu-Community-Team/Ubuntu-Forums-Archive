---
title: "HD Failure Strategy"
date: 2009-06-22
forum: New to Ubuntu
---

### Post by mesmith on 2009-06-22
I'm new to Linux, and trying to develop a strategy to recover from HD failure if it occurs. I have two HD's. On my primary HD I have two partitions, Linux and Swap. My backup HD is a single partition. I have captured and saved the primary drive's MBR to my backup HD, along with an image of my primary Linux partition (using partimage).

In the event of primary HD failure, I would install, partition and format a new HD using RescueCD (two partitions, Linux and Swap). This disk would likely be larger than my old disk. I would restore the MBR, then restore the Linux image.

Would this procedure work, or would all hell break loose?

---

### Post by mgranet on 2009-06-22
Might I suggest clonezilla? It does pretty much the same thing, but does the hard work for you after a few questions.

[http://clonezilla.org/](http://clonezilla.org/)

EDIT: and compresses the resulting image. That might be helpful for your space concerns.

---

### Post by earthpigg on 2009-06-22
putting a failed hard drive in the freezer overnight can sometimes give you an additional hour or so of use to copy stuff of it... horrible as a 'backup strategy', of course, but fun to know nonetheless.

---

### Post by freak42 on 2009-06-22
> **mesmith said:**
> 
In the event of primary HD failure, I would install, partition and format a new HD using RescueCD (two partitions, Linux and Swap). This disk would likely be larger than my old disk. I would restore the MBR, then restore the Linux image.

Would this procedure work, or would all hell break loose?

I am no expert, so I can't tell you whether this works or not. But I know that if you replace harddisks and copy over another system you need to update the disks uuid (a long identifier string) in various places in the system, or otherwise it won't boot. I know there are uuid's set in /etc/fstab and in /boot/grup/menu.lst and there are probably other places.

Just so you know.

---

### Post by The Cog on 2009-06-22
> **freak42 said:**
> I am no expert, so I can't tell you whether this works or not. But I know that if you replace harddisks and copy over another system you need to update the disks uuid (a long identifier string) in various places in the system, or otherwise it won't boot. I know there are uuid's set in /etc/fstab and in /boot/grup/menu.lst and there are probably other places.

Just so you know.

I think that using partimage should overcome this problem because it would also re-write the UUID on the partition. 

I have succesfully restored a working Linux from a partimage backup in the past. So I know it can work. 

I have also also restored from a .tar backup of the system disk. This has the benefit of allowing you to restore to a bigger disk, but the disadvantage of having to manually partition, format and maybe fix the partition UUID in fstab afterwards.

To be honest, these days I just keep an rsync copy of /home, and a list of the packages I installed after the main OS install. But that relies on having internet to be able to complete the re-install of course. Maybe I ought to also keep full images of the system, hmm...

---

### Post by Herman on 2009-06-22
> To be honest, these days I just keep an rsync copy of /home, and a list of the packages I installed after the main OS install. But that relies on having internet to be able to complete the re-install of course.If you make a backup of all the .deb files in /var/cache/apt/archives and restore those packages to your new installation's /var/cache/apt/archives you would be able to reduce your internet bandwidth and also the time taken for re-downloading the added software to almost nothing. You can only use the same packages again if you're using them for the same version of Ubuntu though. :D

---

### Post by t0p on 2009-06-22
I dunno... Maybe it's just me, but this all seems OTT.  I just make regular back-ups of my files, and that makes me happy.  Exact copies of disk images doesn't seem necessary, so long as the *data* is backed up.

---

### Post by mesmith on 2009-06-22
I guess I need to know definitively if a partimage restore will eliminate a potential uuid problem.  If the uuid is picked up from the actual hard disk, and is a "hard" identifier, then probably not.  Anybody know for sure?

---

### Post by Herman on 2009-06-22
Yeah, I have used Partimage quite a lot, and it works great. You won't have any UUID problems.

Sometimes it's quicker just to make a backup and re-install and other times you can't beat Partimage or a good 'dd' command. Partimage is safer for most people.

It depends on how good you are at making a backup and re-installing, it only takes half an hour to re-install, and a little while to copy your files back. Some people, (like me), run a script to install added software and settings, and that way it is very quick. I install for other people quite often, (my friends), so a script is very helpful. I can probably install and set a system up faster that way than using Partimage. (I use the same .deb files again too, saving a lot of download time).

Partimage is very good for most people, it is quite quick, and can also restore non-linux systems. One of my freinds prefers a non-Linux system and every once in a while I restore it for them from a Partimage backup I keep in their Ubuntu partition, (when it gets too full of viruses).

---

### Post by Herman on 2009-06-22
You should still have a separate backup of your important files, once or twice I had errors when trying to restore from a Partimage backup, but that was a while ago now and there's a possibilty I might have been doing something wrong, possibly with file permissions.

My point is, don't just put all your faith in any one single backup strategy. Have at least one or two fall-back methods as well.

---

### Post by mesmith on 2009-06-22
Thanks for all the help.  In my case I would likely be restoring the partition to a new drive with a larger linux partition as it's probably impossible to find a 20gb hard disk anymore.  There seems to be a problem of "losing partition space" when restoring to a partition larger than the one backed up, but I assume I could adjust that after the fact with gparted.

---

### Post by nothingspecial on 2009-06-22
> **t0p said:**
> I dunno... Maybe it's just me, but this all seems OTT.  I just make regular back-ups of my files, and that makes me happy.  Exact copies of disk images doesn't seem necessary, so long as the *data* is backed up.

I agree. It`s the data that`s important. Have 2 copies (as in 3 - original + 2 backups). Everything else is recoverable, but don`t loose your data.

---

### Post by The Cog on 2009-06-23
> **mesmith said:**
> Thanks for all the help.  In my case I would likely be restoring the partition to a new drive with a larger linux partition as it's probably impossible to find a 20gb hard disk anymore.  There seems to be a problem of "losing partition space" when restoring to a partition larger than the one backed up, but I assume I could adjust that after the fact with gparted.

By the time you've done that, you might as well have just restored from a .tar file and then corrected the fstab file from a live CD. I feel that correcting fstab is probably quicker and safer than re-sizing a partition and its contained filesystem.

---

### Post by wizard10000 on 2009-06-23
> **t0p said:**
> I dunno... Maybe it's just me, but this all seems OTT.  I just make regular back-ups of my files, and that makes me happy.  Exact copies of disk images doesn't seem necessary, so long as the *data* is backed up.

Same here - I just rsync /etc and /home to an external drive.  When I clean installed Jaunty I was running at 90% within an hour and had the rest of the applications installed and running within another hour.

I did like the idea of backing up apt's cache, though.

---

### Post by wizard10000 on 2009-06-23
> **Herman said:**
> ...My point is, don't just put all your faith in any one single backup strategy. Have at least one or two fall-back methods as well.

Meh.

An untested backup strategy isn't a backup strategy - you can maintain one copy if you're certain you can restore it.

---

### Post by Herman on 2009-06-23
> An untested backup strategy isn't a backup strategy - you can maintain one copy if you're certain you can restore it. "if you're certain you can restore it" - magic words!
You're right.
Just don't come and blame me if you wrap up your entire thesis in a Partimage backup and when you go to restore it it fails to decompress like it usually does and gives you an ugly error message. You try googling the error message and all you get are other people with the same error message and no solution. Then what?

I think Partimage is a great program and I have used it quite a lot, I don't mean to criticise the program. Possibly I did something wrong myself, I can't remember now. I do know I have had trouble restoring the partimage backups on more than one occasion.
Most of the time, Partimage has worked very well for me and saved me a lot of time.
It's safer to recommend to new users than the dd command. I still think Partimage is a great program if used in the right way.

Unfortunately, I can't recommend Partimage, (or any other program) as a complete backup solution that anyone can put all of their faith in.

It's up to you guys though, do whatever makes you happy! :D

---

### Post by LewRockwell on 2009-06-23
> **mgranet said:**
> Might I suggest clonezilla? It does pretty much the same thing, but does the hard work for you after a few questions.

[http://clonezilla.org/](http://clonezilla.org/)

EDIT: and compresses the resulting image. That might be helpful for your space concerns.

Actually I use Clonezilla and PartedMagic now has Clonezilla built in!

[http://www.partedmagic.com/](http://www.partedmagic.com/)

how cool is that!

---

### Post by LewRockwell on 2009-06-23
Also note, files that are not subject to change(most often music/video/photos/etc) might well be burnt to optical storage media(I prefer duplicates which are stored in separate locations to guard against fire and theft).

If you still want easy access to these then you could use an external hard drive or network drive for that purpose.

As always, your mileage may vary...buyer be aware and beware...do due diligence!

---

