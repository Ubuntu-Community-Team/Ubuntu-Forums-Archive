---
title: "Partitioning A Drive With Windows On"
date: 2009-01-02
forum: New to Ubuntu
---

### Post by joey-elijah on 2009-01-02
I have a partition on a drive ready to install ubuntu, but i have a windows installation taking up an entire 80GB partition when it's only using 24GB. All files etc are saved to a shared partition, so it's being a bit greedy. However i can't resize it. 

I've tried from within Windows via Computer > Manage but it will let me free up 3MB. oooh! lol

Same goes for my Vista drive (a whole 80Gb drive taken up with vista, but only using 27GB.) I'd ideally like to reize it and install Ubuntu on this drive, however, again, the most 'Manage' will let me shrink it by is a few MB.

I really miss having ubuntu already cos gParted made this so simple. I'm worried of using a live disc etc to resize these drives, cos if windows is saying it need all excessGB, then does it?

Just to break down: -

**80GB** - One Partition - Windows Vista Ultimate x64 (*60GB Free*)
**160GB** - 80Gb Windows 7 (*50GB Free*);  25GB Shared Space (*2Gb Free*); 15GB Ubuntu (*Empty Currently*)

I want to shrink the Vista drive and install Ubuntu to that but i don't want to ruin (isn't it already ruined?! lol) vista - especially since the built in windows partitioner says it can't free any space.

---

### Post by Brafil on 2009-01-02
Defrag it, but not with the windows defragger, id recommend ccleaner. Then, use ubuntu live, start Ssytem -> Administration -> Partition Editor and resize. (dont forget to BACKUP your files)

---

### Post by joey-elijah on 2009-01-02
ok i'll try that. 

it's just slightly ludicrous that given it has 60GB FREE yet refuses to free up anything.

---

### Post by handydan918 on 2009-01-02
> **Brafil said:**
> Defrag it, but not with the windows defragger, id recommend ccleaner. Then, use ubuntu live, start Ssytem -> Administration -> Partition Editor and resize. (dont forget to BACKUP your files)
NO!
Vista MUSTA be resized with the Vista partition resizing tool!
Defrag first, resize from within vista, then let gparted build the new partitions you need.

---

### Post by mikewhatever on 2009-01-02
> **Brafil said:**
> Defrag it, but not with the windows defragger, id recommend ccleaner. Then, use ubuntu live, start Ssytem -> Administration -> Partition Editor and resize. (dont forget to BACKUP your files)

And since when does ccleaner does defragging?

---

### Post by matt79 on 2009-01-02
Well when I did my computer (and other peoples computers) I let ubuntu resize the hard disk when I installed ubuntu. I simply booted from the ubuntu cd and followed the steps to resize. It works great for me, Now I have windows and ubuntu and can load either from the grub menu.

---

### Post by -kg- on 2009-01-02
I did a little research on your problem and found a couple of things I have done but had forgotten about.

First, I don't know whether you use it or not, but you need to disable Hibernate in your Vista installation.  Micro$oft, in it's *"infinite wisdom,"* has removed the ability to disable hibernation from the "Power Options" GUI, as it was with XP. [Here is the way to turn it off]("http://www.mydigitallife.info/2007/10/25/how-to-turn-off-and-disable-hibernation-in-windows-vista/") in Vista.

Hibernate creates a file called hiberfil.sys which can get quite large.  When you disable Hibernation, this file is eliminated upon reboot after disabling Hibernation.

Second, you likely have Windows handle your Paging file.  This file also isn't included in the "Used" information.  When Windows handles the paging file, it is a dynamic file, part of which is created on every available partition.

You need make sure this is not maintained on the partition you wish to shrink (that would be the 80 GB drive, am I right?).  In any case, you need to be sure that Vista doesn't maintain a Paging file on the partition you want to shrink.  [Here is the  Microsoft page]("http://support.microsoft.com/kb/307886") which shows you how to do this.

If you intend to install Ubuntu on the 80 GB drive, then you could either configure Vista to put the static Paging file on the Windows 7 partition, or extend your shared partition into the free space enough to put your static Paging file on that.

Then reboot into Vista, defrag it, and see how much you are able to shrink it from that point.

<edit> I didn't know that ccleaner did defragmentation, either.  I always (bought and) used Executive Software Diskeeper, and I don't know if there are any free defragmentation tools out there.  The Windows defragger is a simplified version of the Executive Software tool, though.

---

### Post by BuGleb on 2009-01-02
It seems I have a similar problem (:

I'd like to install ubuntu. I've also tried to resize Vista partition using its tool and vista doesn't want to make it less then 123 GB (:

I don't want to resize that partition using some external tools because after that I have to repair Vista as far as I know. I can do that, but I think that this problem can be solved without repairing (:

I've already disabled Hibernation, removed Paging file, rebooted and defraged, but Vista don't want to shrink its partition.
What can you advise?

---

### Post by handydan918 on 2009-01-02
> **BuGleb said:**
> It seems I have a similar problem (:

I'd like to install ubuntu. I've also tried to resize Vista partition using its tool and vista doesn't want to make it less then 123 GB (:

I don't want to resize that partition using some external tools because after that I have to repair Vista as far as I know. I can do that, but I think that this problem can be solved without repairing (:

I've already disabled Hibernation, removed Paging file, rebooted and defraged, but Vista don't want to shrink its partition.
What can you advise?

not sure about vista, but defrag under xp was cumulatively effective. IOW, 12 runs of defrag were a lot better than 1 run. You might try it before you shell out for diskkeeper, which is supposed to be pretty good.

---

### Post by BuGleb on 2009-01-02
I've downloaded Vopt to defrag vista partition and found some undefragable files at the last clusters of the partition. It was $UsnJrnl:$J ~69,2 MB.

Following this article: [http://it.megocollector.com/?p=26](http://it.megocollector.com/?p=26)
I've deleted journal, then defraged the partition again and found System Volume Information folder, $MFTMirr, $Bitmap and $UsnJrnl:$J which is 256 kb now at the end of partition.

It seems I must repair this journal using "chkdsk /f": [http://support.microsoft.com/kb/311724](http://support.microsoft.com/kb/311724)

I've no idea what are these other files, what should I do to remove them and why $UsnJrnl hasn't gone. Maybe I can resize the partition from other program without any harm?

I'll continue tomorrow (: Thanks for help (:

---

### Post by -kg- on 2009-01-02
> I've already disabled Hibernation, removed Paging file, rebooted and defraged, but Vista don't want to shrink its partition.
What can you advise?

Well, this is for those who have their Vista installation disks:

Yes, there are times that you will have to repair their Vista installations after using GPartEd to resize their Vista partitions, but it doesn't seem quite so complicated as all that.

Read this page: [http://www.howtogeek.com/howto/windows-vista/using-gparted-to-resize-your-windows-vista-partition/]("http://www.howtogeek.com/howto/windows-vista/using-gparted-to-resize-your-windows-vista-partition/")

It doesn't seem too complicated to recover your installation, as long as you have your installation DVD to repair the installation with.  But do read down into the comments below the article.  It sometimes doesn't work.  Which leads me to:

I know we shouldn't "OS Bash" in these forums, but I just can't help it:

MAN, I HATE WINDOWS!!

There, I feel better.  Quoting from the comments on the preceding page:

> I seem to remember starting about WinXP, the last MB or so of a drive is used to store some additional information, without doing anything to allocate it to any partitions.

Important: quotes and commentary from kb/931854: The partition that hosts Windows Vista may disappear if you use Windows XP to create a partition on a computer that has both Windows XP and Windows Vista installed. CAUSE: This problem may be caused by a [sic] error in Logical Disk Manager. If the partition that hosts Windows Vista was created during the installation of Windows Vista, a 1-megabyte (MB) alignment boundary is created on the partition. This alignment boundary differs from the alignment boundary that is created by Windows XP. Therefore, when you use Windows XP to create a new partition, the different alignments may cause this problem.

and...

> From past experience hibernate could be using a preallocated file or a hidden disk area.

(which is one of the reasons I suggested turning off hibernation) and...

> Within those limits, I have already shrunk the preinstalled C and D partitions. I planed to slide the D partition to the end of the drive and place two additional partitions in between: F & E. The resulting partition order will be C, F, E, and D. C is the OS partition, D is a Data Partition used by some of the vendors system backup tools. I don't expect it to have much access. Historically F has been the drive with the family's files. (I don't use "my documents"), and E is an alternate application install and scratch partition.

Since Vista did not offer a partition mover, II decided to target a partition order of C, F, D, and E with Vista disk manager so that I would not have to move any partitions. However, VISTA refused to add my planned E partition, saying that space was not available on the drive, despite the ~ 50GB chunk at the end of the drive.

After thinking about it, I realized that the hidden partition and partitions C, F and D are probably all primary partitions that completely fill the 4 available entries in the master partition table (the partition table in the master boot record), and the "not enough space on the drive" was probably master partition table space.

However, [http://windowshelp.microsoft.c.....3.mspx#EFB](http://windowshelp.microsoft.c.....3.mspx#EFB) says "When you create partitions on a basic disk using Disk Management, the first three volumes you create will be formatted as primary partitions. Beginning with the fourth volume, each volume will be configured as a logical drive within an extended partition." If this is the case I don't understand why VISTA refused, saying that 50GB wasn't enough space on the drive. 

I think (no, I'm SURE) that Micro$oft does this stuff on purpose.  No other partition editor in the WORLD is that screwed up, and the fact that Vista's is, plus the fact that you can't resize a Vista partition without breaking it, is unconscionable.

Now, feeling much better:

There is one more thing that's possible (well, technically two).  After backing up your valuable data (and once again, having an installation disk, not just a recovery disk), you could either 1) delete the OS partition, then recreate it to a minimal size and reinstall Vista into that smaller partition or 2) get another larger hard drive and install everything on it.

#1 would gain you space without the need to buy a larger hard drive.  But I know there is a minimal size to a Vista installation partition, so it might not gain you much room at all.

#2 would gain you much more hard drive space in which to install Vista *and* Ubuntu to an acceptable size.  Of course, you have to buy the hard drive, but the smaller ones (of which 300 or 400 GB is kind of small these days) shouldn't set you back too much.  You could even buy a lower end one (like another 160 GB like your secondary) and still create a minimal Vista partition to install into.

There is a #3, actually...if you are using IDE drives (which I assume you are) and one IDE CD/DVD drive, you could add that extra drive as a 3rd drive.

I don't know what to say.  Check out the instructions at the link above, with some attention to the comments below the article, then you'll have to make your decision from there, based on your situation.  I noticed that one or two had used GPartEd to shrink a Vista partition without having to repair it, but you'll need to be able to do it if it becomes necessary.

---

### Post by BuGleb on 2009-01-03
I saw the page you mentioned. I have no installation disk only recovery disk (: Also I cannot add HD because vista is on HD of my laptop (:

I've found some information about some of that metafiles at the end of partition listed in my previous post. It's really hard to move them (practically impossible for me: I don't know and don't want to learn how NTFS works). Also I've found information that I can get some errors during vista launching if I corrupt some of these files.

Never the less I've resized vista partition using GParted (: And got a error (: Using recovery disk choosed "To restore on the first existing partition". Well, the partition is resized and there is vista on it..

Unfortunately, it seems that it's the only solution of resizing vista partition if you have MFTMirror at its end \=

---

### Post by aleangelico on 2009-01-04
What -kg- says about disabling the hibernations is only for been able to resize the partition, but you can enable the hibernation when the lnx is running.

If you cannot resize the partition is because there are occupied clusters at the end of it, so the only way to solve this is defragmenting the disk. 

This is a very good tool, and GNU (free), you can use:
[http://www.kessels.com/JkDefrag/index.html](http://www.kessels.com/JkDefrag/index.html)

And as somebody said before, the defragmentation is acumulative, keep it running for a while (a whole day at least).

By the way, I recommend you to delete and uninstall all the old stuff you don't use anymore, and run a chkdsk before defragmenting.

.alex

---

### Post by joey-elijah on 2009-01-04
No offence to vista (i.e lots) but frak that! I'll just scrub, resize and reinstall. Same with windows 7. I'm not spending years defragging etc just to fee up what should (under linux) be available space. 

thanks for the help though, i'm sure these suggestions will help others. (if they do, be sure to comment so in this thread to let others know!)

---

### Post by BuGleb on 2009-01-05
> **aleangelico said:**
> 
If you cannot resize the partition is because there are occupied clusters at the end of it, so the only way to solve this is defragmenting the disk. 

This is a very good tool, and GNU (free), you can use:
[http://www.kessels.com/JkDefrag/index.html](http://www.kessels.com/JkDefrag/index.html)


At this page at "Known problems" I've found that
"The Microsoft defragmentation API on Vista can defragment and move the MFT, but JkDefrag cannot use this capability yet."
So I'm not sure at all, that this program can move MFTMirror. 

Anyway, thanks for usefull link (:

---

