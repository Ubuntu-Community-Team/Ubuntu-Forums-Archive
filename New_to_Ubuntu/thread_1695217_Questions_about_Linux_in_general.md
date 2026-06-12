---
title: "Questions about Linux in general"
date: 2011-02-25
forum: New to Ubuntu
---

### Post by Infiniti359 on 2011-02-25
Hello all, It's my first post, and first real venture into Linux, so please go easy on me :P

I was mainly looking to have a few questions answered if possible.

I have ZERO experience with Linux, beyond basic navigation on a free Live CD
The only real question I would like a simple honest answer to is this (below)

I've heard that Linux can access Fat32 file systems and was told if I wanted to make use of my current data (NTFS drives) I should create a Fat32 partition, and copy my data to it. BUT we all know of the 4GB file size limit Fat32 has, so it becomes a bit pointless If i needed to download a 5GB ISO or larger, right?

So my question is: Is there a Linux distro or a way to install to NTFS OR make them visible to a Linux install?
I'm NOT totally clear on the many file systems involved with Linux, like /dev/hda1 or Hpfs etc. I'm sorry to say I've been spoiled by windows for many years now, NTFS/FAT32.

Bonus questions:
Are there any good DVD/CD data backup burning tools on Linux?
How good is Wine? Can it really make use of many windows programs/games?
I know this is a Ubuntu based forum, and please don't bite my head off for asking this but are there any other distro's you can suggest? Mainly to see what else is on offer...

Many thanks in advance

---

### Post by Simian Man on 2011-02-25
> **Infiniti359 said:**
> So my question is: Is there a Linux distro or a way to install to NTFS OR make them visible to a Linux install?
I'm NOT totally clear on the many file systems involved with Linux, like /dev/hda1 or Hpfs etc. I'm sorry to say I've been spoiled by windows for many years now, NTFS/FAT32.
Linux has been able to access NTFS just fine for years now.  No worries :).

> **Infiniti359 said:**
> Are there any good DVD/CD data backup burning tools on Linux?
I use K3B which works well.

> **Infiniti359 said:**
> How good is Wine? Can it really make use of many windows programs/games?
It's really hit or miss.  Mostly miss in my experience.  The outlook I have is to assume it will fail and be pleasantly surprised when it doesn't.

> **Infiniti359 said:**
> I know this is a Ubuntu based forum, and please don't bite my head off for asking this but are there any other distro's you can suggest? Mainly to see what else is on offer.
Fedora is the only distro I use any more.  It all comes down to preference though.

---

### Post by kellemes on 2011-02-25
> **Infiniti359 said:**
> I know this is a Ubuntu based forum, and please don't bite my head off for asking this but are there any other distro's you can suggest? Mainly to see what else is on offer...

Lots of options.. [DistroWatch.com]("http://distrowatch.com/")
Too many to suggest any one particular. Just browse, read and try (most of them offer livedisks).

---

### Post by Arthur_D on 2011-02-25
Hi and welcome; I'll try answer a couple of your questions.

Firstly, you can access your NTFS partitions just fine with Linux. I have Windows XP and Debian (of which Ubuntu is based on), and I haven't had any real issues concerning NTFS for many years. However, transfer speed between NTFS and ext4 is not too good, so moving large amounts of data from NTFS to ext4 takes quite some time. But you can even automount your NTFS partition when starting Linux, so no need to move all your DVD's and music over. ;)

Yes, there are several useful burning applications for Linux. My personal favorite is k3B, which can burn just about anything (CD-R, CD-RW, DVD-R, DVD-RW, DVD-R DL, etc etc).

Wine, depending on who you ask, is either quite good or really bad. ;)
This is because support is mostly on a program to program basis, and thus some programs and games work excellent while others don't. I have successfully run Spotify, StarCraft and more in Wine. Check [http://appdb.winehq.org](http://appdb.winehq.org) for a database on program support (some of the entries might be a bit old though, or doesn't apply to all versions of Wine).

---

### Post by nikefalcon on 2011-02-25
> **Simian Man said:**
> :).
It's really hit or miss.  Mostly miss in my experience.  The outlook I have is to assume it will fail and be pleasantly surprised when it doesn't.


I'll swear by that! The only reason I install wine after a clean install is hope, apart from the fact that it can run a few small apps.

---

### Post by Infiniti359 on 2011-02-25
> Firstly, you can access your NTFS partitions just fine with Linux. I  have Windows XP and Debian (of which Ubuntu is based on), and I haven't  had any real issues concerning NTFS for many years. However, transfer  speed between NTFS and ext4 is not too good, so moving large amounts of  data from NTFS to ext4 takes quite some time. But you can even automount  your NTFS partition when starting Linux, so no need to move all your  DVD's and music over.

Sounds good to me, but the reason I asked was, I'm not able to do this on Ubuntu 8 Live CD. Is it a limitation of the live CD? Would I have to install it to the Hard drive first, then try to access my D-drive partition?

I took this '[Screen print]("http://i751.photobucket.com/albums/xx151/infiniti359/IMAG1015.jpg")' via mobile, because the live cd would not even accept my USB stick, preventing me from copying to my windows pc.

---

### Post by hansolo4949 on 2011-02-25
To answer your questions, yes, you can do everything just fine except for using wine, which as another person said is a hit and miss. Quite frankly, I have loved Ubuntu, and the only ones I would recommend are Xubuntu, a lighter version of Ubuntu, and Lubuntu, if you want to get really light. Puppy Linux is also great and fast, since jt loads itself into the systems ram.

---

### Post by mastablasta on 2011-02-25
i suggest you create a side by side boot that way you still have windows to go back to if necessary. For beginnersd Ubuntu (more or less the whole buntu familly) is very newbie friendly. another newbie friendly distro is Ubuntu based Linux Mint while PinguyOS is Ubuntu with plenty stuff preinstalled - a guy that makes it actually made it based on what applicaitons his friends used most. so maybe it's a bit overloaded here and there.

---

### Post by Paqman on 2011-02-25
> **Infiniti359 said:**
> Sounds good to me, but the reason I asked was, I'm not able to do this on Ubuntu 8 Live CD. Is it a limitation of the live CD?

That's a pretty old version, but Ubuntu has had full read/write support for NTFS since 7.10, so either 8.04 or 8.10 (whichever you have) should work fine. If you have 8.10 I would advise against installing it, as that version is no longer supported, so it can't be considered secure. TBH, I wouldn't install 8.04 either, as that is end-of-life in April as well. I'd advise downloading either 10.04 or 10.10. Both are supported for at least another year.

You should be able to access your NTFS partition from the LiveCD, but it isn't mounted by default. Simply go to Places and click on the drive and it will become accessible.

---

### Post by Infiniti359 on 2011-02-25
> **Paqman said:**
> 
You should be able to access your NTFS partition from the LiveCD, but it isn't mounted by default. Simply go to Places and click on the drive and it will become accessible.

That's what I tried, (see the picture link in my last post) and it did not mount it :(
I downloaded the [manual]("http://ubuntu-manual.org/") and will be reading it tonight/tomorrow.

---

### Post by ppv on 2011-02-25
> **Infiniti359 said:**
> Sounds good to me, but the reason I asked was, I'm not able to do this on Ubuntu 8 Live CD. Is it a limitation of the live CD? Would I have to install it to the Hard drive first, then try to access my D-drive partition?

I took this '[Screen print]("http://i751.photobucket.com/albums/xx151/infiniti359/IMAG1015.jpg")' via mobile, because the live cd would not even accept my USB stick, preventing me from copying to my windows pc.

You could boot into Windows and run chkdsk on D: drive, shutdown the system using shutdown menu and then try to access the drive again in Ubuntu.

---

### Post by alexis44 on 2011-02-25
I'm an absolute newbie to Ubuntu.  I was having serious problems with my Windows computer.  I'm not a nerd in the least.  I was getting Boot Failures.  Fortunately about three years ago I downloaded a Live CD just out of curiosity.[/SIZE]  [SIZE=2]I was able to access the internet.  After more frustrating Boot Failures, it came back.  I found and downloaded the new Live CD.  I partitioned the hard drive with both Vista and Ubuntu.  The Ubuntu side was fine, it was stable.  The Windows side was less so.  I had error messages for NVidia and Windows would not shut down correctly.  Even though I had never used a Linux system as my OS, I decided to go for it.  It's certainly an adjustment.  I loaded it.  Now Ubuntu is my only Operating System.  I don't know what the problem was before.  Maybe Windows had just become too corrupted.  That's confusing since I did format and re-install it.  I don't know.  Did Ubuntu save my computer?  I don't know.  All I know is that it works now. :D

---

### Post by n-n-nebbl on 2011-02-25
About the NTSF-Support...

It works great if you handle it right.
But you really should unmount your NTFS ressources before you shut down or make something risky.

In my experience, ubuntu is writing the file journal just when you unmount it.
Example:
I moved data from my ext4 partition to the ntfs partition to use it in windows.
After reboot the data was lost!
I'm sure it wrote it to the partition, but didn't unmounted it right during shutdown --> no entries for the new files...

Another thing are file permissions:
ntfs has it's own permission handling which is not implemented...

---

### Post by alexis44 on 2011-02-25
> **alexis44 said:**
> I'm an absolute newbie to Ubuntu.  I was having serious problems with my Windows computer.  I'm not a nerd in the least.  I was getting Boot Failures.  Fortunately about three years ago I downloaded a Live CD just out of curiosity.I was able to access the internet.  After more frustrating Boot Failures, it came back.  I found and downloaded the new Live CD.  I partitioned the hard drive with both Vista and Ubuntu.  The Ubuntu side was fine, it was stable.  The Windows side was less so.  I had error messages for NVidia and Windows would not shut down correctly.  Even though I had never used a Linux system as my OS, I decided to go for it.  It's certainly an adjustment.  I loaded it.  Now Ubuntu is my only Operating System.  I don't know what the problem was before.  Maybe Windows had just become too corrupted.  That's confusing since I did format and re-install it.  I don't know.  Did Ubuntu save my computer?  I don't know.  All I know is that it works now. :D[
My question seems to have gotten lost in the confusion! :P

---

### Post by jerenept on 2011-02-25
> **Infiniti359 said:**
> Sounds good to me, but the reason I asked was, I'm not able to do this on Ubuntu 8 Live CD. Is it a limitation of the live CD? Would I have to install it to the Hard drive first, then try to access my D-drive partition?

I took this '[Screen print]("http://i751.photobucket.com/albums/xx151/infiniti359/IMAG1015.jpg")' via mobile, because the live cd would not even accept my USB stick, preventing me from copying to my windows pc.

Allright, first recommendation: Use Ubuntu 10.04 or 10.10. Ubuntu 8.04/8.10 are really old now. Most likely, the problem has been fixed already.

Now, your screenshot: it appears that the flash drive was not safely removed of unmounted correctly. It's really recommended to Safely Remove/ Unmount removable drives after use.

---

### Post by alexis44 on 2011-02-25
Forget it.  Apparently you just don't care.  Goodbye. :confused:

---

### Post by alexis44 on 2011-02-25
I'm not being difficult.  I'm just a woman who has a few questions to be answered.  Please help me in this. :)

---

### Post by oldos2er on 2011-02-26
It's considered rude to hijack someone else's thread. Please start your own thread and I'm sure you'll get some help.

---

### Post by centaurusa on 2011-02-26
Bonus questions:
How good is Wine? Can it really make use of many windows programs/games?

Hit and miss is a fairly good description.  Some Windows programs work flawlessly under Wine, some won't run at all, and others run most of the time but then crash unexpectedly.  Wine HQ has a database of many applications ([http://appdb.winehq.org/](http://appdb.winehq.org/)) that provide an indication of how well they run under Wine.  If you have a specific program in mind, it's worth checking it out under Wine HQ's AppDB.

If all else fails, another option for that must-run Windows app (short of running a dual-boot system) is to try Virtualbox ([http://www.virtualbox.org/](http://www.virtualbox.org/)).  This will allow you to run a virtual Windows machine under the base Linux system.  All of the Windows software I have tried has worked perfectly in this system.  However, you do need a licensed copy of Windows to be able to create the virtual machine and install the desired flavour of Windows (e.g. XP, Vista, 7).

---

### Post by Arikaree105 on 2011-02-26
I've been using Ubuntu (9.04 thru 11.04 Narwal) on a home network for several years, and have accessed NTFS and F32 on other systems' drives, and NTFS and F32 on my Ubuntu host drives (just to see how it all works).

It all works. it all works fine. 

I'm puzzled about your comment that F32 is limited to 4GB: my F32 partitions sizes are 40 to 150 (one hundred fifty) GB. I used Linux Gparted (disk partitioner) to create and format these, not Microsoft.  I searched Microsoft ("F32 Limitations") and found this:

"The maximum possible number of clusters on a volume using the FAT32 file  system is 268,435,445. With a maximum of 32 KB per cluster with space  for the file allocation table (FAT), this equates to a maximum disk size  of approximately 8 terabytes (TB). "

Further info refers to limitations on ScanDisk, Win95 and Win2K as having F32 limits. 

I made sure on my XP systems to allow file sharing, and have never hit a snag. Hope you'll try this on your Ubuntu. For starters it offers lots of utilities (eg: NTFS file management via Ubuntu, yada yada),  tons of documentation and this forum. Of all the distros, this seems the most robust.

---

### Post by VOT Productions on 2011-02-26
> **Arikaree105 said:**
> 
"The maximum possible number of clusters on a volume using the FAT32 file  system is 268,435,445. With a maximum of 32 KB per cluster with space  for the file allocation table (FAT), this equates to a maximum disk size of approximately 8 terabytes (TB). "

That's partition size. There's a limit on copying: Only 4 GB per file.

---

