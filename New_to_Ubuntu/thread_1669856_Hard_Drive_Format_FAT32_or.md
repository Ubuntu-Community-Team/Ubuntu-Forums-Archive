---
title: "Hard Drive Format FAT32 or ?"
date: 2011-01-18
forum: New to Ubuntu
---

### Post by henry cow on 2011-01-18
This question gets asked in different ways, and I know that there is not a definitive answer, but here it comes again.

I use and maintain 6-8 computers for myself, family, friends, and business. They are a mixture of XP, 7, Lucid, and Maverick. My personal desktop and laptop are dual-boot, there are even straight-Ubuntu and straight-Windows machines in the mix. I am extremely diligent about keeping software up-to-date.

Also, I have at least a half-dozen loose hard drives that are used for storage and transfer. Long-term, I would like to migrate away from Windows, but that will most likely take years.

My question is how to format hard drives for maximum compatibility. It is imperative that they operate across OS and file system boundaries as much as possible.

There is a mix of documents, pictures, and music files. The drives range from 10GB to 1.5TB. 

I understand that FAT32 chokes on larger drives. I seem to have experienced some of that, I think, but not consistently. NTFS works well but I feel like I am being challenged, and/or locked out, of drives due to "permissions" and "mounting" issues which remain mysterious to me, as a relative newbie.

Furthermore, Windows and Linux seem to be reluctant, sometimes, to see or read drives formatted or partitioned by the "other team" however you want to say it.

Maddeningly, these mounting and permission issues do not occur consistently, but seem to be almost random. For instance, with my dual-boot desktop, I have a dedicated 80GB hard drive for Ubuntu and 2 NTFS drives for Windows. About every third Ubuntu boot, I get an error message that one or the other NTFS drives would not mount. All these drives are relative clean and new, and I maintain them pretty well.

Long rambling monologue, my simple underlying question is what file system to use, even on large drives, for maximum compatibility across platforms.

Thanks in advance for your help and opinions.

---

### Post by CharlesA on 2011-01-18
I'd stick with NTFS if you've got a mix of Windows/Linux machines.

There is also an ext driver for Windows, but I haven't tried it, so I don't know how well works.

---

### Post by sydbat on 2011-01-18
NTFS for sharing between Windows-based computers and Linux-based computers. 

Remember, you can only read / write to Windows-based file systems from your Linux boxen, not the other way round (cannot read / write Linux file systems from Windows). That is why you have the NTFS share.

Also, FAT32 is fine for small flash / thumb drives because it is pretty universal and you won't be putting huge files onto a thumb drive.

EDIT - CharlesA just beat me to it...and I would not suggest the ext Windows driver. Had it corrupt a couple of Linux test boxen.

---

### Post by CharlesA on 2011-01-18
> **sydbat said:**
> 
EDIT - CharlesA just beat me to it...and I would not suggest the ext Windows driver. Had it corrupt a couple of Linux test boxen.

In that case, I'd just stick with NTFS. It's usually better to stick to a file system your OS supports natively.

---

### Post by henry cow on 2011-01-19
Thank you for your responses, but I am not sure that I understand the underlying concepts that you are proposing.

I would love to use FAT32 but worry that it will not handle larger drives.

As I move from Windows to Linux, I have to be able to manipulate all my old files, some of which are quite large (>200MB for .WAV files) but if I have to drop back to (<100MB) .MP3 files then I will just have to learn deal with it.

Why won't kb3 handle burning audio CDs from .MP3 files, even though it acts like it will?

---

### Post by CharlesA on 2011-01-20
The max file size for files on a FAT32 partition is 4GB. FAT32 is really only used for small devices, such as thumb drives and I haven't seen it used on anything like an external hard drive (those are formatted NTFS by default).

If I had to pick between FAT and NTFS, I'd pick NTFS every time.

Also, note that sometimes NTFS gets marked as "dirty" if there was an unclean shutdown, you need to boot into Windows, run chkdsk on the drive, and then shut it down again. That'll allow it to be mounted.

---

### Post by CharlesA on 2011-01-20
The max file size for files on a FAT32 partition is 4GB. FAT32 is really only used for small devices, such as thumb drives and I haven't seen it used on anything like an external hard drive (those are formatted NTFS by default).

If I had to pick between FAT and NTFS, I'd pick NTFS every time.

Also, note that sometimes NTFS gets marked as "dirty" if there was an unclean shutdown, you need to boot into Windows, run chkdsk on the drive, and then shut it down again. That'll allow it to be mounted.

---

### Post by Paqman on 2011-01-20
> **CharlesA said:**
> 
If I had to pick between FAT and NTFS, I'd pick NTFS every time.


Ditto. The only reason to use FAT32 is if you needed compatibility with OS X. NTFS is a much better filesystem.

---

### Post by steve7777777 on 2011-01-20
Do not use FAT32 on a hard drive with important data. It's much less robust than NTFS. With FAT32 there is a greater risk of corrupted data. I would only use FAT32 for small USB drives.

Wouldn't it be useful to have a SAMBA share as well?

---

### Post by srs5694 on 2011-01-20
> **CharlesA said:**
> The max file size for files on a FAT32 partition is 4GB. FAT32 is really only used for small devices, such as thumb drives and I haven't seen it used on anything like an external hard drive (those are formatted NTFS by default).

If I had to pick between FAT and NTFS, I'd pick NTFS every time.

Although NTFS does have its advantages, and although they are significant for many situations, I wouldn't *always* pick NTFS....

> Also, note that sometimes NTFS gets marked as "dirty" if there was an unclean shutdown, you need to boot into Windows, run chkdsk on the drive, and then shut it down again. That'll allow it to be mounted.

This is one of the problems with NTFS: There are no Linux utilities to check and repair NTFS. (Such utilities do exist for FAT.) Thus, if there's much chance that you'll need to run a filesystem check on a disk when you don't have ready access to a Windows system, NTFS is a poor choice. Examples include a computer that boots between multiple OSes that do *not* include Windows NT/200x/XP/Vista/7 (say, Linux and FreeBSD, NetBSD and Windows Me, or Linux and OS X), a removable disk that's transported between a Windows-only computer at one location and a Linux-only computer at another, or a disk intended for long-term archival storage (you don't know what OSes you may have available in a year or two or five).

Another issue with NTFS is that the NTFS-3g driver that Ubuntu uses is a user-space driver, vs. a kernel-space driver for FAT. This imposes a performance penalty on NTFS under Linux, but not on FAT; and it makes for a more complex software path that is at least theoretically more susceptible to bugs. That said, FAT is inherently slower, and many say less reliable, than NTFS, so in practice I don't know which is faster or more reliable under Linux. Somebody must have run benchmarks, but I don't recall seeing them. Do not assume that because NTFS is faster or more reliable under Windows that the same is true under Linux, though.

IMHO, the single biggest problem with FAT as a cross-platform filesystem is its 4 GiB file-size limit. If it weren't for that, FAT would be superior to NTFS simply because almost everything, from cell phones to supercomputers, understands FAT. NTFS is much less well-supported, and even when it is supported, it tends to be supported in a more limited way. (OS X provides mere read-only support for NTFS out of the box, for instance, although NTFS-3g can be added to rectify that situation.) NTFS is more technically advanced than FAT, but for a cross-platform filesystem, it's the breadth and quality of support, not technical wizz-bangery, that's important.

---

### Post by srs5694 on 2011-01-20
Duplicate post.

---

### Post by srs5694 on 2011-01-20
> **CharlesA said:**
> The max file size for files on a FAT32 partition is 4GB. FAT32 is really only used for small devices, such as thumb drives and I haven't seen it used on anything like an external hard drive (those are formatted NTFS by default).

If I had to pick between FAT and NTFS, I'd pick NTFS every time.

Although NTFS does have its advantages, and although they are significant for many situations, I wouldn't always pick NTFS....

> Also, note that sometimes NTFS gets marked as "dirty" if there was an unclean shutdown, you need to boot into Windows, run chkdsk on the drive, and then shut it down again. That'll allow it to be mounted.

This is one of the problems with NTFS: There are no Linux utilities to check and repair NTFS. (Such utilities do exist for FAT.) Thus, if there's much chance that you'll need to run a filesystem check on a disk when you don't have ready access to a Windows system, NTFS is a poor choice. Examples include a computer that boots between multiple OSes that do not include Windows NT/200x/XP/Vista/7 (say, Linux and FreeBSD, NetBSD and Windows Me, or Linux and OS X), a removable disk that's transported between a Windows-only computer at one location and a Linux-only computer at another, or a disk intended for long-term archival storage (you don't know what OSes you may have available in a year or two or five).

Another issue with NTFS is that the NTFS-3g driver that Ubuntu uses is a user-space driver, vs. a kernel-space driver for FAT. This imposes a performance penalty on NTFS under Linux, but not on FAT; and it makes for a more complex software path that is at least theoretically more susceptible to bugs. That said, FAT is inherently slower, and many say less reliable, than NTFS, so in practice I don't know which is faster or more reliable under Linux. Somebody must have run benchmarks, but I don't recall seeing them. Do not assume that because NTFS is faster or more reliable under Windows that the same is true under Linux, though.

IMHO, the single biggest problem with FAT as a cross-platform filesystem is its 4 GiB file-size limit. If it weren't for that, FAT would be superior to NTFS simply because almost everything, from cell phones to supercomputers, understands FAT. NTFS is much less well-supported, and even when it is supported, it tends to be supported in a more limited way. (OS X provides mere read-only support for NTFS out of the box, for instance, although NTFS-3g can be added to rectify that situation.) NTFS is more technically advanced than FAT, but for a cross-platform filesystem, it's the breadth and quality of support, not technical wizz-bangery, that's important.

---

### Post by CharlesA on 2011-01-20
> **srs5694 said:**
> Although NTFS does have its advantages, and although they are significant for many situations, I wouldn't always pick NTFS....

That's true. I think the largest drive I have with FAT32 is a 16GB thumb drive. Everything else that I use with Windows is NTFS (which isn't much, as almost all of my external drives are formatted as EXT4)

---

### Post by henry cow on 2011-01-25
Thanks, folks.

This is interesting and enlightening. Also, it clarifies the situation and helps to zero in on the problem that is/was the basis of my inquiry.

In an indirect way, you answered my indirect question about NTFS mounting problems at boot-up. A bad Windows shutdown can somehow "dirty" my NTFS drive(s) so that it(they) will not be recognized when I boot into Linux. I get it, but don't understand it.

My big "mac daddy" personal desktop has 4 hard drives (3 are NTFS and 1 is ext4, totaling an obscene 2.33TB) and I use Windows XP 80% of the time and Ubuntu 10.10 20%. That is where I have been plagued with the random < "press S to "Skip" mounting this drive" > hang-up on the Ubuntu boot.

My desktop computer at work, on the other hand, is a re-purposed Unbuntu-only box of very modest capabilities. I also have a strong but un-spectacular 7/10.10 laptop.

I have a handful of loose hard drives that I want to use for long-term storage and also transfer between my machines and those of co-workers and family members.

So, I need it all. But what really keeps me up at night is that long-term storage bit. Aside from hardware failure, how can I be assured that I can retrieve my data in coming years/decades? I don't give a damn how slow it is or how many hoops I have to jump through - I need something that will safely hold hundreds of GBs of documents and pictures and music in a form that can realistically be retrieved, by hook or by crook, somehow, sometime in the future.

Thank you, srs5694, you gave me the lowdown on the negatives but not the positives. You spoke directly to my concern about avoiding NTFS, the obvious choice, in setting up these ancillary drives.

But what is the answer? This is probably a philosophical/existential question, but if it gets bumped into "ongoing discussions" it will languish, I'm afraid.

I would love to hear one more round of comments on this, especially if someone has something encouraging to offer. 

Thanks again !

---

### Post by srs5694 on 2011-01-25
> **henry cow said:**
> In an indirect way, you answered my indirect question about NTFS mounting problems at boot-up. A bad Windows shutdown can somehow "dirty" my NTFS drive(s) so that it(they) will not be recognized when I boot into Linux. I get it, but don't understand it.

With most modern OSes, when a disk is mounted, the OS writes a special piece of data to the disk that says, essentially, "this disk is in use." The OS can then cache writes to the disk, meaning that data might not be written to disk immediately; they might be kept back and written out of order so as to improve performance. The result could result in something like allocating disk space before linking it to a filename; the disk space would be used but there'd be no way to access it until the cache is flushed. When the disk is unmounted, all the pending operations are committed to the disk, so it will be in a consistent state. The in-use flag is then cleared, so it reads, essentially, "this disk is not in use." When the OS next mounts the disk, it looks for that flag. If the flag isn't present, the OS goes ahead and mounts the filesystem. If the flag is present, the OS can perform a disk check (with fsck under Linux or CHKDSK under Windows), which looks for (among other things) the sorts of inconsistencies that can result when cached disk operations aren't completed. The disk check utility then fixes the problem as best it can. The result may be lost data, but at least the disk structures will be in a consistent state. Since Linux lacks good filesystem check programs for NTFS, though, it can't perform such checks. Therefore, Linux typically refuses to mount an NTFS volume with the "in-use" flag set. If it ignored the flag, it would run the risk of damaging the data on the disk, since the data structures might not be in a consistent or even a legal state.

> So, I need it all. But what really keeps me up at night is that long-term storage bit. Aside from hardware failure, how can I be assured that I can retrieve my data in coming years/decades? I don't give a damn how slow it is or how many hoops I have to jump through - I need something that will safely hold hundreds of GBs of documents and pictures and music in a form that can realistically be retrieved, by hook or by crook, somehow, sometime in the future.

Hardware failure should not be ignored. Unfortunately, higher capacity media seem to be less archival. Your best bet for long-term storage might be punched cards, but of course that's not very practical. For anything really important, I think I'd opt for two or three media -- say, magneto-optical disks, DVDs, and tapes.

In terms of filesystem choice, I'd say FAT or ISO-9660 would be good, simply because they're so common today. That means that they're likely to be supported well into the future, and even if they're abandoned by Year X, you might need fewer steps to "translate" them, in terms of the number of intermediate systems that understand (say) FAT and Format A, and another than understands Format A and Format B, and so on to whatever's current.

Beyond FAT or ISO-9660, my second choices would be NTFS or ext2fs. Despite its popularity on Windows, NTFS is not as well-supported by third parties as FAT, so it doesn't get top honors. Still, it's very common on Windows, and there are third-party drivers for it in other OSes. Similar comments apply to ext2fs, but with the twist that it's less common but source code is available, which could help if you need to implement a driver for it in the future.

Broadly speaking, in terms of archival qualities, digital is suspect. We've got clay and stone tablets from millennia ago that are still readable to the naked eye (assuming knowledge of the language), and paper from centuries ago. Even B&W photos can last over a century, although color photos tend to fade a lot before then. (All of this assumes proper storage, of course.) Digital media aren't designed for that sort of longevity; even with optimum storage, recordable CDs and DVDs tend to become unreadable after just a few years, hard drives fail randomly, mangetic tape flakes away and fails, and so on. If I wanted to leave messages for people to read in a millennium, I'd carve it in stone. If I had to use digital formats, I'd put procedures in place to copy the data to new media at regular intervals, to guard against both physical deterioration and changing data structures. Even over your suggested time scale of a few decades, that's your best bet: Write it to a couple of different media and plan to copy it again to whatever's current in a few years.

---

### Post by RedRat on 2011-01-25
Since you have a mix of Windows and Linux, stick with NTFS. Your Linux system will be able to read those disks. Windows, can read some Linux partitions, but I don't know if it can read the latest format for Linux. NTFS is just more practical for your situation.

---

### Post by henry cow on 2011-01-26
Thanks again folks. I could not agree more about digital longevity. A few years ago my sister told me that she would really like to have a CD of the Christmas records we listened to as kids, and loaned them to me, since I still collect vinyl and have a great sound card.

These were mostly Hi-Fi records, the favorite was pressed in 1955 and the youngest was (actually in stereo) pressed in 1968. In those days if a record skipped you just stacked additional nickels onto the tonearm until it played.

There was a good deal of surface noise, but the records played magnificently with a total of only 2 one-time skips in 4 discs!

NTFS seems to be the obvious choice, but that boot/mount problem is vexing to say the least. At the office we are Ubuntu-only on our desktops, although I dual boot my laptop. 

Not having a good way around an NTFS problem on an all-Linux box is serious indeed, if not a deal-killer. In theory, I would love to leave Microsoft, but until I get a good CAD program and online database that probably won't happen anytime soon.

I would gladly sacrifice most performance issues to use FAT32, but these drives are from 10GB to 250GB (mostly 40s) and when I "partition and format" them as FAT32 with gparted my Windows computer will not even recognize their existence. And Windows no longer offers a FAT formatting option, as far as I can tell.

So, there does not seem to be a solid answer here, and I guess I should take my chances with NTFS on the assumption that I will have access to at least 1 Windows box for the foreseeable future.

Thanks again.

---

### Post by srs5694 on 2011-01-26
> **henry cow said:**
> I would gladly sacrifice most performance issues to use FAT32, but these drives are from 10GB to 250GB (mostly 40s) and when I "partition and format" them as FAT32 with gparted my Windows computer will not even recognize their existence.

Then something is wrong. I just did a test using virtual machines: I created a 300 GiB virtual disk, booted Linux (I had Fedora 14 installed so I used that rather than Ubuntu), created a FAT-32 partition on the 300 GiB virtual disk, copied a file to it, and shut down. When I made the disk available to my Windows 7 installation and booted, it had no problems recognizing the disk or reading the file.

Perhaps there's something wrong with the version of GParted you're using, or one of the libraries or utilities it relies upon; or maybe you're doing something wrong in creating the FAT-32 partition; or maybe the Windows system you're using for testing is damaged in some way.

> And Windows no longer offers a FAT formatting option, as far as I can tell.

Try this in a Windows command prompt:

```

format E: /fs:fat32

```

Change "E:" to the drive letter associated with the disk you're using. Unfortunately, adding the "/q" option (which does a quick format) produces an error message, and the non-quick format causes my virtual disk to expand in size, and I don't have enough free space on my partition to let it get up to 300 GiB, so I can't verify that it will actually work rather than fail partway through. The documentation for the Windows "format" command ("help format") suggests there's a size limit of just under 255 GiB for FAT-32; however, that seems to be a limit of the Windows FAT filesystem creation tools, since the Linux tools have no problems with it, and Windows can handle the Linux-created larger FAT partitions.

I bet there's a third-party utility that'll do the job in a more GUI way, too, but I've never searched for one.

---

### Post by henry cow on 2011-02-17
You are right in your response and I have since formatted 3 of the drives (2 - 40s and a 10) using FAT32, which have been recognized properly wherever I plugged them in.

I do feel more comfortable with the FAT32 formatting and do not anticipate problems, especially since, barring hardware failure, the future box will likely have more backwards compatibility.

Also, as archives, editing them will be less important than simply getting one clean read, onto whatever gigantic storage system we have in a few more years.

Thanks again for your help.

---

### Post by grahammechanical on 2011-02-17
Hi henry cow

You spoke of > Long-term, I would like to migrate away from Windows, but that will most likely take years.

So, think long term. What will you do when the machines get a bit old and need replacing? Will you buy new machines with an OS pre-installed? We know what brand of OS that will be, do we not?

Will you consider building the machines yourself? Would it be wise to install one the hard drives that you are now using? Would it not be better to install new?

So, assuming that you install a Linux distribution and Ubuntu at that, your concern should be that you can transfer your data on to the new machines that have the Linux disc format.

As others have pointed out, Linux reads and writes to Windows formats but the same is not true of Windows Operating systems.

So, my advice is this: When you need to upgrade a machine then install Ubuntu on it, connect it to the network, and transfer the files that need to be transfered. Over time the present machines will become old and pass way. The new ones will, hopefully all be running Ubuntu.

Regards.

---

### Post by Arikaree105 on 2011-02-28
re NTFS vs. F32:

my home network has a mix of Linux and Windows, mostly because I dabble in these things. My "share" drives on the Linux sides are either F32 or NTFS. I have used this mix for several years now, without difficulty or issues. I have formated a 2TB drive in F32 format (just for fun), though using Gparted, and never (!) rely on Bill Gate's format software. I remain confused about the reported 4GB limit on F32, and here's why. My F32 partitions range from 40 to 150 GB. They all work, and (famous last words) never had any issues. A quick search on Microsoft produces this:

"The maximum possible number of clusters on a volume using the FAT32 file  system is 268,435,445. With a maximum of 32 KB per cluster with space  for the file allocation table (FAT), this equates to a maximum disk size  of approximately 8 terabytes (TB)."

They further state that Win95 and Win98 (yuck!) have a limit of 127GB capability, but there are other limiting factors, such as a really, really old BIOS, and 16-bit architecture.

In my wandering thru the Ubuntu forums and software repository, I've found nice NTFS service programs, and will probably stick with that as my "share" standard.

Now, if someone could help me solve my idiot problems getting 2 Linux systems to talk, that would be AWESOME.

---

### Post by coffeecat on 2011-02-28
> **Arikaree105 said:**
> I remain confused about the reported 4GB limit on F32, and here's why. My F32 partitions range from 40 to 150 GB. They all work, and (famous last words) never had any issues.

Your confusion is between partition size and file size. The maximum **file** size in FAT32 (not F32) is 4GB - in fact 4GB, less one byte. Maximum partition size is much greater.

---

### Post by henry cow on 2011-03-08
Thanks for all the help. I have a dozen hard drives in and out of cases, and build my own computers for myself and my kids.

I like having something that I can hold in my hand with 10s of thousands of songs or pictures in it, and want to keep that long-term.

I have little faith that anything (except paper books or vinyl LPs) will last beyond a decade (or perhaps 2 if I am very lucky) so leaping formats from time to time is part of the game.

Maybe storing a few hundred gigs in a cloud will be no big deal a couple of presidents from now.

As always, there were tips to be picked up from all your answers, above and beyond my original question.

Thanks again!

---

