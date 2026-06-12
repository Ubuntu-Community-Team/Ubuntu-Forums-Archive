---
title: "Windows7 not booting after GParted resize"
date: 2009-09-08
forum: New to Ubuntu
---

### Post by sneakytiki22 on 2009-09-08
Hi all,
 
I am new to ubuntu, I've been a windows user all my life. I had a bit a problem with dual booting 9.04 with windows 7. My first mistake was not consulting the resources on this site before I blindly dove in to Ubuntu.
 
It is pretty much the same story I'm sure you have heard a thousand times. I recently upgraded to windows 7 64-bit from vista. I decided I also wanted to dual boot ubuntu 9.04. Through the ubuntu installer I allocated 150gb to ubuntu. It installed successfully, only I discovered the partition only had about 2.5gb. I was successfully dual booting ubuntu and windows 7, but I needed more space on my ubuntu partition. So, I used GParted to shrink the windows partition and grow the ubuntu partition... and guess what! Windows 7 won't boot. When I go into GParted now, the windows partition is still there, only it is not recognized anymore. It is "Unknown". I have tried booting with the windows 7 disk and having it do the "Mr. Fix-it" autorepair windows does, but it did not work.
 
I only blame myself because if I had tried reading up on what I was doing before I did it, I wouldn't be in this mess. My question is if there is anything I can do to get windows to boot again, or perhaps recover the data. Out of impatience and misplaced confidence I only backed up some of my more important documents and didnt backup music, photos, all that stuff.
 
I am at my work computer right now, so I won't be able to paste fdisk or menu.lst outputs until I get home in a couple hours.
 
Thank you in advance!

---

### Post by Bucky Ball on 2009-09-08
I'm not sure if 7 is the same but with XP you could stick the installation disk in and go to 'Repair'. In there you can run help I think and there is a command containing 'chkdisk'. Run that. Then 'fixboot' and 'fixmbr'.

Of course, none of this might work in 7 but fixed things when I did exactly the same thing as you running XP.

---

### Post by alejaaandro on 2009-09-08
you might be able to boot into windows from a live cd and repairing the partition (not sure if possible), or you can try testdisk ans see if it can fix the problem.. i've used it successfully a couple of times to fix ntfs partitions...

if you have valuable data, you might want to make an image of your partition, in case something goes wrong, you might be able to give it another shot if you have a backup image

---

### Post by Razz27 on 2009-09-08
Hmm. What I'm thinking is that when you tried to resize the partition, gParted did something stupid, and your partition entry for windows was removed.  Assuming you havn't used the pc since that happened, you should be able to recover all the data using testdisk.  I would run it off an Ubuntu live cd.  It should scan your hard disk and detect the windows partition.  You can then re-write the partition table, and check that it's all there again with gParted.
I had a similar problem a while ago, where the windows installer decided to delete my partition table...  A night of messing with testdisk and sfdisk fixed it.
I would DEFINITELY advice, if possible, image your hard disk, and save it somewhere safe, so that if anything goes wrong you have a fall-back :)
If you could possibly post a screenshot of gParted, or the output of fdisk when you run them from a live cd, it would help work this out...

---

### Post by sneakytiki22 on 2009-09-08
> **Razz27 said:**
> Assuming you havn't used the pc since that happened, you should be able to recover all the data using testdisk. I would run it off an Ubuntu live cd. It should scan your hard disk and detect the windows partition. You can then re-write the partition table, and check that it's all there again with gParted.
 
I will try this when I get home.  What do you mean by 
> **Razz27 said:**
> "Assuming you haven't used the pc since..."?
 
I have been running Ubuntu since it happened last thurday.  Would that foil the plan?  What kind of use would close this option to me?

---

### Post by Jerry N on 2009-09-08
When you used gparted on the Win 7 partition, you might have wiped out files at located near the high end of the partition. I have observed that XP will sometimes have files near the high end even after defragmentation.  Somewhere on these forums I have read that shrinking the Vista partition with anything but it's own "shrink volume" utility is a no-no.  

Jerry

---

### Post by louieb on 2009-09-08
Starting with Vista - MSoft made some changes to the way it installs itself in a partition.  Gparted can deal with it but should have the **round to cylinder  **unchecked.      

From the [Gparted FAQ]("http://gparted.sourceforge.net/faq.php")
> 9 : After resizing my Vista partition, Vista won't boot.  How can I fix this?  

The following article by *the How-To Geek* contains useful information regarding resizing your Vista partition, and getting it to boot again. 
[Using GParted to Resize Your Windows Vista Partition]("http://www.howtogeek.com/howto/windows-vista/using-gparted-to-resize-your-windows-vista-partition/") 

If your PC did not come with a complete Vista installation CD, you can download a Vista Recovery Disc at the following link: 
[Windows Vista Recovery Disc]("http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/")

---

### Post by Jerry N on 2009-09-08
Great reference (how-to-geek)!!  I have bookmarked it for future reference.  I am assuming that Win 7 has similar requirements.

Jerry

---

### Post by sneakytiki22 on 2009-09-08
> **louieb said:**
> Starting with Vista - MSoft made some changes to the way it installs itself in a partition. Gparted can deal with it but should have the **round to cylinder **unchecked. 
 
From the [Gparted FAQ]("http://gparted.sourceforge.net/faq.php")
 
I have put in the windows 7 boot disk and tried a system recovery "Repair and Restart". It didn't help. I can't remember exactly what it said when it failed. I will try that again and see exactly what it says, but that was the first thing I tried. If the "round to cylinder" checkbox is checked by default I definately did not have it unchecked when I shrunk the windows partition.

---

### Post by jsoellner on 2009-09-08
How big was the windows partition before you started?  How much did you resize it by?

The problem with resizing windows partitions is that windows sticks the master file table data, hibernation data and pagefiles in wierd places.  I guess there may be a bonafide reason for it but it seems odd.

You can have a 100gb partition, with only the first few gigabytes used, but windows will put the MFT files right at the end of that partition.

So, by resizing it you are erasing some stuff that's pretty important to make windows work.

Sorry I know this isn't actually any help for you but if anybody else is reading this, please be careful and back up your important data before doing anything like this!

Even the partition resizing utility built into windows is pretty weak, I normally use a non-free 3rd-party program on the trial period for doing the job.

---

### Post by sneakytiki22 on 2009-09-08
> **jsoellner said:**
> How big was the windows partition before you started? How much did you resize it by?
 
It started at probably around 950gb (it is a 1000gb drive) I shaved 150gb off the end. It seems rediculous to me that windows couldn't just stick to the first 800gb... :-?

---

### Post by louieb on 2009-09-08
When i go searching for answers - alway enjoy finding something written by Herman. he does his research.  Part of this post [**Dual boot with Windows 7 RC**]("http://www.uluga.ubuntuforums.org/showpost.php?p=7816261&postcount=17")
> 
There was a bug in GParted Live CD quite some time back which had nothing at all to do with GParted in Ubuntu. Apparently the GParted LiveCD was made with a small program omitted which was for updating the Windows boot sector if the start of the Windows partition is moved.
The OP did not mention which version of Gparted he used. But it appears problems like his are fixable. 

Another post of intrest in the same thread has this to say:
> Here's an image to show the 'Round to cylinders' checkbox.
This is what is not shown in the how-to geek's site.
If people would remove the checkmark from that checkbox before resizing their Windows 7 or Vista partition then GParted will leave the start point of that partition at sector number 2048 instead of moving it to sector number 63.
That's what we should be telling people.
Then their partition resize would be faster and they would not need to go through the additional inconvenient procedures advised in the how-to geek's site.
That site is good for helping people after they have already made the mistake, but it's not helpful and may even be misleading for people who want to use up to date versions of GParted for resizing Windows.

There's no need to look for any checkbox to clear in the Ubuntu installer's partitioner though, and it doesn't move the partition, so it's quite safe and has been all along.

---

### Post by sneakytiki22 on 2009-09-08
> **louieb said:**
> When i go searching for answers - alway enjoy finding something written by Herman. he does his research. Part of this post [**Dual boot with Windows 7 RC**]("http://www.uluga.ubuntuforums.org/showpost.php?p=7816261&postcount=17")
The OP did not mention which version of Gparted he used. But it appears problems like his are fixable. 
 
Another post of intrest in the same thread has this to say:
 
I downloaded and burned a Ubuntu 9.04 install disk/livecd, the Gparted I used was whatever was on the ubuntu livecd.  I originally tried the ubuntu install method (the slider bar) to create a 150gb partition for ubuntu right off the bat, but like I said, it only partitioned 2.5gb for some reason.  So after that I used the livecd to boot ubuntu so that I could resize the partitions with the gparted that came on the livecd.  I can check what version of gparted it is when I get home.

---

### Post by LewRockwell on 2009-09-08
so what has happened is that your previous windows partition began at 2048 and gparted changed that to 63.

our inclination is that you have not lost all your data(especially given the size of the drive and windows partition overall).

your windows recovery/repair fails because from it's perspective, what it "sees" is a completely goofed partition which might contain big nasties(how else could it get that way...windows "thinks")

on our tech bench we would boot up a Puppy Linux LiveCD and rescue anything we could find

then, if necessary, we could use Testdisk and/or Photorec to attempt any further rescuing required

once you've retrieved everything you want then your best bet would be to do a complete fresh install

this probably isn't the silver bullet you were looking for but...hey, that's life at the tech bench

****It should also be noted that if you have very valuable data on the drive and you feel uncomfortable attempting the recovery yourself, there are commercial/retail recovery services to do this for you but you'll probably spend a couple Bennys on it****

keep us posted on how it goes for you

.

---

### Post by Razz27 on 2009-09-08
> **sneakytiki22 said:**
> 
I have been running Ubuntu since it happened last thurday.  Would that foil the plan?  What kind of use would close this option to me?

No, I doubt this will ruin anything.  The only concern is that since the windows partition doesn't exist according to Ubuntu, it might try use the disk where windows used to be, and overwrite some of the data.  It's unlikely though, as the Ubuntu partition shouldn't overlap anything.  The only things that may have been damaged is anything that windows might have stuck at the end of the partition -.-, as jsoeellner said.

Anyway, keep us posted on how the testdisk goes, and if you ever need to do anything related to windows partitions, that How-to-geek reference is great.

---

### Post by jsoellner on 2009-09-08
> **LewRockwell said:**
> 
on our tech bench we would boot up a Puppy Linux LiveCD and rescue anything we could find

then, if necessary, we could use Testdisk and/or Photorec to attempt any further rescuing required

once you've retrieved everything you want then your best bet would be to do a complete fresh install
.

I agree with LewRockwell.  Try Testdisk it's pretty snappy.  Check this page - [https://help.ubuntu.com/community/DataRecovery]("https://help.ubuntu.com/community/DataRecovery")

---

### Post by sneakytiki22 on 2009-09-08
Attached is a screenshot of GParted screen

Here is the output of the TestDisk analysis

```
TestDisk 6.10, Data Recovery Utility, July 2008
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org

Disk /dev/sda - 1000 GB / 931 GiB - CHS 121602 255 63
     Partition               Start        End    Size in sectors
L HPFS - NTFS              0  32 33 101144 254 63 1624892377
L Linux                121276   1  1 121578 254 63    4867632
L Linux Swap           121579   1  1 121600 254 63     353367










Structure: Ok.  Use Up/Down Arrow keys to select partition.
Use Left/Right Arrow keys to CHANGE partition characteristics:
*=Primary bootable  P=Primary  L=Logical  E=Extended  D=Deleted
Keys A: add partition, L: load backup, T: change type, P: list files,
     Enter: to continue
NTFS, 831 GB / 774 GiB
```

I went ahead and wrote to disk.  Now I have to reboot, and we will see what happens.

---

### Post by sneakytiki22 on 2009-09-08
So now my GParted screen looks like the attached.  I'm not sure if what happened is good or bad, but at least now I can mount sda5 on the liveCD and SEE that my files still exist.  Also, the partition I originally grew to 150gb shrunk back down to 2.32gb, and the 150gb is now unallocated.  

I tried booting from drive and Grub won't load.  Gives error 17.

---

### Post by louieb on 2009-09-08
The 2nd Gparted screen-shot looks like a mix of good and bad. 
The good part is the 1st partition is now recognized as NTFS and you can see your data.

The bad part is its now a logical partition.  In order to make it so windows will boot - You should have chosen Primary - boot-able in testdisk for the 1st partition. 

What I would have expected to see is the 1st partition (the 700+GB one) be a primary partition with the boot flag on. 

The other two probably should have been logical but it really does not matter if their primary or logical.

At this point looks like it time to copy the data off. and your probably looking at a reinstall. 

But if you want to try - use testdisk to change partition 1 back to a primary bootable. Then get a [Super Grub Disk ]("http://forjamari.linex.org/projects/supergrub/")   or a [PartedMagicCD]("http://partedmagic.com/wiki/PartedMagic.php?n=Main.PartedMagic") - it has Super Grub also.  Super Grub has super cow powers and you may be able to get it boot windows - and it should be able to boot your linux install.  doesn't hurt to try.

---

### Post by Bucky Ball on 2009-09-09
> **Bucky Ball said:**
> I'm not sure if 7 is the same but with XP you could stick the installation disk in and go to 'Repair'. In there you can run help I think and there is a command containing 'chkdisk'. Run that. Then 'fixboot' and 'fixmbr'.

Of course, none of this might work in 7 but fixed things when I did exactly the same thing as you running XP.

I said this in post #2! If your Windows install disk can get you to a 'Repair' screen, these commands would have fixed your original situation 99% guaranteed.

The really easy way is to download supergrubdisk iso, burn a cd and boot from it. That will sort things out quick smart as far as booting goes unless the important bits are now irrevocably moved about (and you might even learn something about grub along the way as it can be educational).

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

One other thing: ALWAYS defrag your windows drive before shrinking. The way data is handled 90Gb of data can be scattered all over a 200Gb partition with gaps everywhere. That will give you VERY inaccurate readings of how much you can shrink.

---

### Post by sneakytiki22 on 2009-09-09
The NTFS partition is now primary.  I used TeskDisk again and fixed it.  Now my big problem is I can't boot without using a live cd and I don't have a separate disk drive that can burn the super grub disk.  I'll have to burn it at work or boot from USB.  And you are right, I have already learned a lot about grub and I haven't even fixed anyhting.  I guess the best way to learn is to fail, over and over again (as long as something is acomplished in the end :P).
 
So I will boot from a SGD and see if I can fix grub, otherwise I will just copy the windows files and reinstall.  I could just do that now and skip the SGD, but as you said, I might just learn something if I carry this through to the end.

---

### Post by Bucky Ball on 2009-09-09
> **sneakytiki22 said:**
>  I have already learned a lot about grub and I haven't even fixed anyhting.  I guess the best way to learn is to fail, over and over again (as long as something is acomplished in the end :P).
 
So I will boot from a SGD and see if I can fix grub, otherwise I will just copy the windows files and reinstall.  I could just do that now and skip the SGD, but as you said, I might just learn something if I carry this through to the end.

+1

... and knowledge is freedom ... good luck with it. Remember when working with grub if you don't already know:

sda = hd0
sda1 = hd0,0
sdb1 = hd1,0
sdb2 = hd1,1

etc.

---

### Post by LewRockwell on 2009-09-09
> **sneakytiki22 said:**
> The NTFS partition is now primary.  I used TeskDisk again and fixed it.  Now my big problem is I can't boot without using a live cd and I don't have a separate disk drive that can burn the super grub disk.  I'll have to burn it at work or boot from USB.  And you are right, I have already learned a lot about grub and I haven't even fixed anyhting.  I guess the best way to learn is to fail, over and over again (as long as something is acomplished in the end :P).
 
So I will boot from a SGD and see if I can fix grub, otherwise I will just copy the windows files and reinstall.  I could just do that now and skip the SGD, but as you said, I might just learn something if I carry this through to the end.

[http://ubuntuforums.org/showthread.php?t=1030786](http://ubuntuforums.org/showthread.php?t=1030786)

.

---

### Post by sneakytiki22 on 2009-09-09
> **LewRockwell said:**
> [http://ubuntuforums.org/showthread.php?t=1030786](http://ubuntuforums.org/showthread.php?t=1030786)
 
.
 
Tried that.  When I tried it, it was after I had TestDisk write the partition tables, and because of that it was giving me error 17, corrupt stage1/stage2.  As I understand it (which could be wrong) it was because the partitions were renamed by TestDisk from what GRUB had seen when it was installed, or something about the order of the partitions being wrong.  
 
After that I tried something i saw in [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351). I did a mount proc and undev.  It didn't work at the time, but I haven't tried it again since I rewrote the partition tables.

---

### Post by sneakytiki22 on 2009-09-09
So, I am posting from Windows 7.  I booted windows with a SGD, and all my files are here!!!  Now, does this mean the windows boot is "fixed" or does it still depend on SGD to boot it?  I wasn't sure if SGD was healing or acting as a crutch/bridging the gap or filling the gap in.  Is it fixed?

I guess the next step is to back this up as fast as possible :-$.  Then fix ubuntu.  Or perhaps a fresh install would be better?  My situation now is, i have windows on the first 800gb or so, 150gb free space, then ubuntu 9.04 with like 2.3gb to work with.  Would it be better to grow the ubuntu partition or just get rid of it and install fresh on the 150gb free space?

---

### Post by louieb on 2009-09-09
> So, I am posting from Windows 7 [COLOR=Blue]Cool[/COLOR] - More that likely SGD just booted window for you. Won't know for sure until you try.  But if you look around the Super Grub menu (forgot just where) you will find the option to repair (change)  the MBR to boot windows without using the Super Grub Disk.

---

### Post by Bucky Ball on 2009-09-10
> **sneakytiki22 said:**
> So, I am posting from Windows 7.  I booted windows with a SGD, and all my files are here!!!  Now, does this mean the windows boot is "fixed" or does it still depend on SGD to boot it?  I wasn't sure if SGD was healing or acting as a crutch/bridging the gap or filling the gap in.  Is it fixed?

I guess the next step is to back this up as fast as possible :-$.  Then fix ubuntu.  Or perhaps a fresh install would be better?  My situation now is, i have windows on the first 800gb or so, 150gb free space, then ubuntu 9.04 with like 2.3gb to work with.  Would it be better to grow the ubuntu partition or just get rid of it and install fresh on the 150gb free space?

SGD has no doubt re-written your fstab file. Try:
```

nano /etc/fstab

```
... and post that here. :) It really is a cool thing and thanks Herman and pals for making it so!

---

### Post by sneakytiki22 on 2009-09-19
I reinstalled ubuntu, and this time i had plenty of free space to install it on.  So I am up and running just fine now.  I think all I have left to configure is my graphics card (ATI Radeon 4870), which from skimming through the forums looks like it might not be the easiest.  

Thanks again for your help!  \\:D/

---

### Post by edcompsci on 2011-10-17
This is a hypothesis only, but I was able to shrink my XP partition on my laptop in order to dual boot Ubuntu, and still boot Windows. Always Defrag and Defrag again and again until you can't anymore before shrinking a Windows partition, and on the defrag screen look at where the system files are. I'm not sure where to see this on W7 but on XP and older it's the green portion. If you shrink past that green portion, chances are that you will wipeout important files needed to boot the system. Yes if you have the XP install cd you can try a repair, and even reinstall it. If you have data on it, you can boot into your ubuntu, mount the Windows drive, and save your data from it onto a flash drive before reinstalling. You will probably then have to reinstall Ubuntu again to, because the Windows boot loader will probably write over GRUB (or LILO, etc.)

---

### Post by Mark Phelps on 2011-10-17
> **edcompsci said:**
> This is a hypothesis only, but I was able to shrink my XP partition on my laptop ...

Maybe you didn't notice ... but the title clearly indicated Windows 7 -- not XP.

The GParted-related problems do not affect Windows XP; instead, they affect Windows 7 (and, to a lesser degree, Windows Vista).

---

### Post by wallydallas on 2013-03-11
Thanks for all the advice everyone. What fixed things for me is booting from the windows 7 cd, then clicking repair.

Then I ran command line 
bootrec.exe /FixMbr
bootrec.exe /FixBoot
bootrec.exe /RebuildBcd

In my case I used an old gparted by accident, and then shrunk my windows 7 partition with Gparted.   It would not boot, I googled the problem and found this forum.  Fixed in 5 minutes.   

I don't really think gparted was the cause, but Microsoft has this handy KB article.

[URL="http://support.microsoft.com/kb/927392"]http://support.microsoft.com/kb/927392
[/URL]

---

### Post by Bucky Ball on 2013-03-11
Gparted probably was the cause. Fine with XP but use Windows software for resizing any newer Win install (the partition where Windows is installed that is). Your problem is a common result of resizing a Win7 partition with Gparted. ;)

---

