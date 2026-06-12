---
title: "Ext3? Ext4?"
date: 2009-04-26
forum: New to Ubuntu
---

### Post by Spiritous on 2009-04-26
Whats up with this "Don't go to EXT4!!! ITS BAD! VIRUSES \_ O _/!!!1one!" Rubbish? I don't know what the difference in Ext3 and 4 is but... I guess its big enough for all the trolls to come out?

---

### Post by aaronp on 2009-04-26
I haven't heard anything about viruses. What I did read while Jaunty was in alpha and beta was that ext4 had caused some issues with data loss so they decided to put the default selection back to ext3. You can see the details in the jaunty release notes.

---

### Post by Spiritous on 2009-04-26
> **aaronp said:**
> I haven't heard anything about viruses. What I did read while Jaunty was in alpha and beta was that ext4 had caused some issues with data loss so they decided to put the default selection back to ext3. You can see the details in the jaunty release notes.

Ahh, Thanks... Because when I was partitioning I considered EXT4 But people went on about it being bad etc... So i just used EXT3

---

### Post by 4Orbs on 2009-04-26
I've installed Jaunty 4 times, twice on ext4 and twice on ext3. Ext4 was fabulous as long as I kept all my work within Ubuntu. But when I began moving large numbers of files between external partitions (storage Fat32 transferred to NTFS, for example) ext4 caused my NTFS storage to become unreadable and unrecoverable. Also, emptying large files from the trash would sometimes lock up the system.

I'm currently very happy with Jaunty on ext3. But I'm looking forward to using ext4 once the bugs are squashed.

---

### Post by talsemgeest on 2009-04-26
> **Spiritous said:**
> Whats up with this "Don't go to EXT4!!! ITS BAD! VIRUSES \_ O _/!!!1one!" Rubbish? I don't know what the difference in Ext3 and 4 is but... I guess its big enough for all the trolls to come out?
Ext4 is the newest, but is also less stable than ext3. For most users (i.e. you don't have millions of small files on your system), you will see no difference between ext3 and ext4. Until they get all the bugs sorted out, it is better to stick with ext3.

---

### Post by alphacrucis2 on 2009-04-26
> **4Orbs said:**
> I've installed Jaunty 4 times, twice on ext4 and twice on ext3. Ext4 was fabulous as long as I kept all my work within Ubuntu. But when I began moving large numbers of files between external partitions (storage Fat32 transferred to NTFS, for example) ext4 caused my NTFS storage to become unreadable and unrecoverable. Also, emptying large files from the trash would sometimes lock up the system.

I'm currently very happy with Jaunty on ext3. But I'm looking forward to using ext4 once the bugs are squashed.

Sounds very odd since EXT4 has nothing to do with reading, writing or updating NTFS or fat32 file systems.

---

### Post by alphacrucis2 on 2009-04-26
> **talsemgeest said:**
> Ext4 is the newest, but is also less stable than ext3. For most users (i.e. you don't have millions of small files on your system), you will see no difference between ext3 and ext4. Until they get all the bugs sorted out, it is better to stick with ext3.

Actually you will notice the difference. Ext4 is quite a bit faster at most disk operations. I would say use with caution. Some people who have their /home on a separate partition to the root file system have / as ext4 and home as ext3. I do that but have both as ext4 as I'm not worried about a glitch as all the important data is backed up elsewhere. I don't mind being a guinea pig:P

---

### Post by 4Orbs on 2009-04-26
I was simply copy and pasting many files from a fat32 storage partition over to the ntfs storage partition. Got an error after pasting a 2GB folder that Ubuntu's ntfs support had broken and needed fixing. After that I couldn't mount the partition from Ubuntu or Windows. Even did a (slow) Windows disk check and could not recover the partition.

---

### Post by talsemgeest on 2009-04-26
> **alphacrucis2 said:**
> Actually you will notice the difference. Ext4 is quite a bit faster at most disk operations. I would say use with caution. Some people who have their /home on a separate partition to the root file system have / as ext4 and home as ext3. I do that but have both as ext4 as I'm not worried about a glitch as all the important data is backed up elsewhere. I don't mind being a guinea pig:P
Oh really? I have been told time and time again that only people with an unusual amount of files on their system will notice and difference. But, since I haven't tested it myself, I could be wrong...

---

### Post by wizard10000 on 2009-04-26
Benchmarking the two ext4 systems I have here doesn't show any improvement but I have noticed a difference when deleting large files.

I will say that I originally had some weirdness installing Jaunty - the release notes say that you have to run grub-install if you upgrade to an ext4 partition or grub'll choke.

Anyway, I blew away all my partitions except for an ext3 /home and told the partitioner to format / as ext4.  Install went fine, grub choked on the filesystem.  I decided not to screw with it since I had a backup of /home that was only about four hours old, so I wiped the drive and installed everything on ext4 partitions and it worked fine.

Go figure.

---

### Post by alphacrucis2 on 2009-04-26
> **talsemgeest said:**
> Oh really? I have been told time and time again that only people with an unusual amount of files on their system will notice and difference. But, since I haven't tested it myself, I could be wrong...

Phoronix did a comprehensive benchmark test of ext3, ext4, xfs & resierfs. ext4: 

[Comparitive benchmark]("http://www.phoronix.com/scan.php?page=article&item=ext4_benchmarks&num=1")

The main difference I notice (subjective) is that programs seem to load faster.

---

### Post by Spiritous on 2009-04-26
So... bottom line stick to EXT3 Till its fixed?

---

### Post by talsemgeest on 2009-04-26
> **alphacrucis2 said:**
> Phoronix did a comprehensive benchmark test of ext3, ext4, xfs & resierfs. ext4: 

[Comparitive benchmark]("http://www.phoronix.com/scan.php?page=article&item=ext4_benchmarks&num=1")

The main difference I notice (subjective) is that programs seem to load faster.
Ah, ok, thanks for that. I think I might have to give ext4 a spin, see what it is like. However, for most users, the stability of ext3 is preferable to the speed increase from ext4.

---

### Post by alphacrucis2 on 2009-04-26
> **Spiritous said:**
> So... bottom line stick to EXT3 Till its fixed?

Depends on how bleeding edge you like to be. It hasn't bitten me yet.....:lolflag:

---

### Post by talsemgeest on 2009-04-26
> **Spiritous said:**
> So... bottom line stick to EXT3 Till its fixed?
Basically. The extra speed is great, but if it puts my data at risk...

---

### Post by alphacrucis2 on 2009-04-26
> **talsemgeest said:**
> Ah, ok, thanks for that. I think I might have to give ext4 a spin, see what it is like. However, for most users, the stability of ext3 is preferable to the speed increase from ext4.

Yep. I definitely wouldn't use it on a production server either!. You can convert existing ext3 partitions to ext4 using tune2fs.

---

### Post by Spiritous on 2009-04-26
> **talsemgeest said:**
> Basically. The extra speed is great, but if it puts my data at risk...

Yep... Because I've got 3,000 worded S.A's On here with no backup... Need another hard drive ](*,)

---

### Post by talsemgeest on 2009-04-26
> **alphacrucis2 said:**
> Yep. I definitely wouldn't use it on a production server either!. You can convert existing ext3 partitions to ext4 using tune2fs.
I think I heard that simply converting wont give you all the benefits. I will just do a format and try it nice and cleanly.

---

### Post by alphacrucis2 on 2009-04-26
> **talsemgeest said:**
> I think I heard that simply converting wont give you all the benefits. I will just do a format and try it nice and cleanly.

I think that is right for files that already existed in the ext3 partition prior to conversion.

---

### Post by wizard10000 on 2009-04-26
More slight grumbling...

From the release notes -

> Switching to ext4 requires manually updating grub

If you choose to upgrade your / or /boot filesystem in place from ext2 or ext3 to ext4 (as documented on the ext4 wiki), then you must also use the grub-install command after upgrading to Ubuntu 9.04 to reinstall your boot loader. If you do not do this, then the version of GRUB installed in your boot sector will not be able to read the kernel from the ext4 filesystem and your system will fail to boot.

As I said in an earlier post I clean-installed but kept /home as ext3 and ran into the same problem.  Can't bug it because I've already repartitioned the drive and can't reproduce it, though.  The strange thing was that when I deleted *all* partitions and installed with / and /home as ext4 the thing worked fine.

Strange.

---

### Post by lukjad on 2009-04-26
> **Spiritous said:**
> Whats up with this "Don't go to EXT4!!! ITS BAD! VIRUSES \_ O _/!!!1one!" Rubbish? I don't know what the difference in Ext3 and 4 is but... I guess its big enough for all the trolls to come out?
I've never hear anything about viruses, but I have hear tales of people losing, or almost losing all their data because of EXT4, especially if they converted a drive from EXT3 to EXT4 with the data. I think that it's better to be safe rather than sorry, so I just will keep on recommending that people who have something to lose do not use EXT4. It may be stable for most people, but until more people use it, I'm staying clear, except maybe in a test box. If you have nothing valuable on your hard drive and just want to try it out, go ahead. Most likely, nothing bad will happen. But I don't want to tell someone to use it and hear that it blew up in their faces. ;)

---

### Post by talsemgeest on 2009-04-26
> **lukjad007 said:**
> I've never hear anything about viruses, but I have hear tales of people losing, or almost losing all their data because of EXT4, especially if they converted a drive from EXT3 to EXT4 with the data. I think that it's better to be safe rather than sorry, so I just will keep on recommending that people who have something to lose do not use EXT4. It may be stable for most people, but until more people use it, I'm staying clear, except maybe in a test box. If you have nothing valuable on your hard drive and just want to try it out, go ahead. Most likely, nothing bad will happen. But I don't want to tell someone to use it and hear that it blew up in their faces. ;)
Very nice way of putting it. Like I said, the speed is cool, but data loss certainly isn't...

---

### Post by SunnyRabbiera on 2009-04-26
> **Spiritous said:**
> So... bottom line stick to EXT3 Till its fixed?

Just about, but its up to you really, there is nothing forcing you to use one or the other.
But EXT4 is still new so I am not expecting perfection yet, but it will probably be a standard in a few years time.

---

### Post by Sef on 2009-04-26
[Ext3 and ext4 sticky]("http://ubuntuforums.org/showthread.php?t=1133719").

---

### Post by Laibcoms on 2009-04-26
I use ext4 for my Ubuntu64 desktop, and it's my main machine.  I use it for site development, office related work, UL/DL, almost everything even LAN and online gaming.  I haven't had problems like data loss so far, even after twice hanging my system because of what I was experimenting that time.

I also mount NTFS partitions and drive (some of my games are there).  But for a server, I will stick with ext3, for a desktop I'm cool with ext4.

---

### Post by talsemgeest on 2009-04-26
> **Laibcoms said:**
> I use ext4 for my Ubuntu64 desktop, and it's my main machine.  I use it for site development, office related work, UL/DL, almost everything even LAN and online gaming.  I haven't had problems like data loss so far, even after twice hanging my system because of what I was experimenting that time.

I also mount NTFS partitions and drive (some of my games are there).  But for a server, I will stick with ext3, for a desktop I'm cool with ext4.
Well, thats all well and good until you lose data... ;)

It really depends on whether you want to take the risk. If you back up regularly, then go for ext4. But if you haven't got a fallback plan, and you need your data, stick with ext3.

---

### Post by belikralj on 2009-04-26
Since I joined ubuntu in 2006 there were all sorts of bugs with ntfs and now after a bit of work, we've got it sorted. By all means use Ext4 but make sure you are wise about how you utilize your disk space to make sure your data is safe. I never put my data on the same partition as the OS for two reasons:

1. The OS will be replaced sooner than the data.
2. The data can't be destroyed by random glitches.

Especially not if the FS is in it's infancy. Before ntfs-3g I used FAT32 as did we all.

And correct me if I'm wrong but I think that is what most of you guys do anyway, so we shouldn't worry that much about ext4 since we are used to being "on the bleeding edge"!

---

### Post by lnxnut on 2009-04-26
Here's an interesting link to ext3/4 benchmarking and performance.
[http://www.linux-mag.com/id/7271](http://www.linux-mag.com/id/7271)

---

### Post by whoop on 2009-04-29
I think it has mainly to do with the issues that some people where having with ext4, namely the problems caused by delayed allocation. The patches that where released for these problems will be part of the 2.6.30 kernel and they are already backported to jaunty's current kernel (2.6.28).

So (for people waiting until karmic) I wouldn't expect any major changes for ext4 in the upcoming karmic.

It's a new file system if you don't like/need bleeding edge don't use it. I think it's a bit overkill to warn people to NOT use ext4 because it's dangerous! Ext4 is stable, there's no discussion, but it's new.
Then again allot of people are switching to ext4 because it's that much faster (this is overkill too IMO). 

I've been running ext4 (converted from ext3, HOWTO: [http://ubuntuforums.org/showthread.php?t=1118295](http://ubuntuforums.org/showthread.php?t=1118295)) on a production machine since jaunty alpha6 and I have had no problems.

So, bottom line: you definitely don't have to use ext4, but you can :guitar:

---

