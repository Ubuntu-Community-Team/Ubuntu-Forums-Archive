---
title: "Vista partition problems"
date: 2009-10-02
forum: New to Ubuntu
---

### Post by aa4bb on 2009-10-02
Installed 9.04 from Live CD in Vista on Dell 1525 Inspiron after using Computer Management / Disk Management in Vista to shrink the C:. 

Before the shrink, there was a 39 MB EISA partition, 2.32 GB and 173 MB primary partitions whose use I have no idea about, a 62.23 GB primary partition for C:, and a 9.71 GB Recovery primary partition D:.

Disk Management said the amount available for shrink was 7950 MB, and I chose that for the shrink, although defrag C: -a -v had reported 22.36 GB as largest free space extent, which I was expecting as the amount I could shrink. After shrink, it reported 7950 MB free, and everything else as expected.

I started a Live session and clicked on Install on the Desktop. I think I chose "Install in the largest free space", which I was expecting to be the 7950. Instead it put it in the 2.32 GB partition.

I'm guessing that since it had four primary partitions, it couldn't make the 7950 MB into a primary partition, and thought it had to use the 2.32 GB. Ubuntu is there but doesn't have enough remaining disk space to do anything useful !?!

I went back into Vista to Disk Management. Lo and behold, the C: now is back up to 62.23 GB and the space I freed up with shrink has vanished.

Where should I go from here? I'm thinking to "somehow" get rid of the 2.32 GB primary partition that Ubuntu is in, shrink C: and hope that the free space somehow merges with the 2.32 GB free space, make that into a partition and install Ubuntu. But I really don't know how to pull all that off.

---

### Post by Zoot7 on 2009-10-02
The Vista partitioner is the definition of useless, you'd be much better off you avoid it like the plague.
I think the best thing for you to do is use an external tool to partition the hard drive such as the gparted liveCD
**[http://gparted.sourceforge.net/livecd.php]("http://gparted.sourceforge.net/livecd.php")**
or the ubuntu liveCD itself.
Just bear in mind you'll have to repair the boot process because Vista won't boot if you partition the hard drive with anything other than that useless partitioner. Hey Microsoft don't care about their customers.. what's new?
To do that just use the Vista setup CD to repair the boot process. you'll then have to re-install grub to the MBR.
**[http://ubuntuforums.org/showthread.php?t=24113]("http://ubuntuforums.org/showthread.php?t=24113")**
It's a bit of a roundabout way but you can thank Vista and Microsoft for that. 
There may also be a more "Vista Friendly" tool out there but I've no experience of it.

---

### Post by aa4bb on 2009-10-02
Thanks, and I may try what you recommend, but I'm still interested in solving this within Vista if possible. Any other ideas out there?

---

### Post by Bartender on 2009-10-02
More details, please - I tried counting up what you described but not sure I got it right.  Do you have four primary partitions?  

If so, you're stuck and will have to get rid of at least one of them, like the recovery partition.  Have you burned recovery DVD's yet?

If you can, a screenshot from the Ubuntu LiveCD partitioner would help give a picture.  Boot from the LiveCD, click on "Try Ubuntu without changes", plug in a thumb drive and wait for it to show up on the desktop.  Then go into System>Partition Editor and take a screenshot.  Save the screenshot to the thumbdrive, get out of the LiveCD, boot back into Windows, post the screenshot here.

EDIT:  I have to disagree about the vista partitioner.  Many consider it more reliable than GParted LiveCD.  herman's website sez as long as you click on the "Round to Cylinders" radio button in GParted it can shrink vista reliably.  I haven't tried that so can't say one way or another.  I tried shrinking vista with a GParted LiveCD once and it made a mess of things.  But I didn't click the "Round to Cylinders" button.  After reinstalling vista from recovery discs I used the vista partitioner and it did successfully shrink vista.

---

### Post by linux4life88 on 2009-10-02
If you are wanting to get rid of the Ubuntu partition, right click on that partition and chose delete. Now that space will have a black bar and say unallocated. Now right click on the Vista partition and chose shrink. If it says the max you can shrink it is 0 then you can not shrink the partition any more. I have heard people say that defragement your computer will allow you to shrink your Vista partition more but this tip did not work for me.

I hope I understood your problem and I hope this helps out.

---

### Post by dave WB3DWE on 2009-10-02
[SIZE=3][FONT=Lucida Sans Unicode]Be cautious with the sourceforge gparted-live-0.4.6-1.iso[/FONT][/SIZE] .
[SIZE=3][FONT=Lucida Sans Unicode]Burned a CD with the image. It booted and produced a window with menu. I selected the drive, deleted the existing partition, but the program would not repartition. Those selections were faint (unusable).
Luckily I had a working Ubuntu on another drive. Via Synaptic Package Manager I went to category Gnome Desktop Environment and downloaded gparted 0.4.3-0 .  This worked and I was able to repartition and format the drive.
This happened last evening and I contacted source-forge today.
If you have to have a live bootable CD I would choose one of the earlier versions of gparted.
[/FONT][/SIZE]

---

### Post by aa4bb on 2009-10-02
Thanks! These ideas make sense and I will try them and report back.

---

### Post by aa4bb on 2009-10-02
Bartender, You're right. I have four partitions and I need to free one up. So I have no idea what the EISA partition is for, or the 173 MB partition not otherwise labeled. Do I dare delete one or other of these?

Or if I can make Recovery DVDs and delete the Recovery partition, that would be fine. How do I make Recovery DVDs, or find out how to do so?

---

### Post by JC Cheloven on 2009-10-02
Well, ... vista... how to say... well, doesn't matter. First of all, a few things:
- Check out [this recent post]("http://ubuntuforums.org/showthread.php?t=1276348") of mine. You may find it an interesting reading.
- Dell likes to ship the HD with a mess of partitions, yes. This is in fact cumbersome when you want to create new ones, as there is a llimit of four primary partitions.
- That shrink tool shipped with vista simply works badly, as you have seen. Even so, is better using it (provided you don't want to put your current vista install at risk), and manage to do linux things in the scarce space it gives you. So you were in the safe side in this aspect, although I've shrinked vista from ubuntu live cd with no issues.
- As a matter of fact, you can't expect to obtain a working ubuntu installation in 2.32Gb, if it installs at all.

Let's try to solve your problem. As bartender said, we would need more precise info: 
* If I understood what you did, either you shouldn't be able to boot vista at this time, or you boot it via a grub menu. Please clarify.
* Please start the ubuntu live cd, and post the output of "sudo fdisk -l". The screenshot bartender asked for would be nice too.

In the meanhwile (to get you prepared), your choices depend on the answers of the above, and may involve:
** Deleting one of the partitions dell deployed on your disk. To be exact, if there are four partitions, you have to delete one of them (no lost love here, except for warranty issues), and set up and extended partition, which will be able to include your future ubuntu partition and an small swap partition. Perhaps would be worth deleting the recovery partition (provided you have recovery cd's), or moving partitions around (which is slow and a bit risky).
** If your interest in ubuntu is only moderate, you can install it inside windows via wubi, and try it out that way. Very easy indeed, although not a true ubuntu install.
** (... many more may be, let's see your answers)

EDIT (update in view of previous post while I wrote this one):
- Read your dell manual for how to make recovery cds from the recovery partition. I think it involves pressing f5 at boot time or something similar.

---

### Post by Bartender on 2009-10-03
jccheloven's advice sounds pretty good to me.  

Seems like every manufacturer intentionally clutters up the HDD with too many primary partitions nowadays.  It's enuf to make you pull your hair out.

My Acer 5920 laptop came with 4.  The _first_ thing I did after buying the lappy was make the recovery discs.  Then I botched up vista by trying to shrink with a GParted LiveCD.  Then I ran the recovery DVD's.  I got vista back, and all the other partitions were gone!  There was just one big C:/ partition.  Installing Ubuntu was easy then.

I don't know what the HDD looks like after running the Dell recovery discs.  I don't know exactly what's on the Dell EISA partition, nor whether you can safely delete the recovery partition after making recovery discs.  But that information should be readily available by googling your model of Dell on this forum, joining the Dell forums, searching a few enthusiast websites such as [Notebook Forums]("http://forum.notebookreview.com/index.php") which has a Dell section, etc.

Making the recovery discs should be very straightforward.  I guarantee you there's a guide somewhere in that Dell that tells you step-by-step.

EDIT:  I'm on dial-up so it's just too much of a hassle for me to dig into this.  But I googled "ubuntu Dell 1525 partitions" and it looks like lots of info is available.

Make the DVD's first.  Then do some homework and figure out exactly how you want to get get rid of at least one of those primary partitions.  Maybe running the recovery discs like I did clears out some of the partitions? I don't know.  Need to find out how Dell's recovery process behaves, which shouldn't be hard.

For now, set aside the idea of *installing* Ubuntu.  You need to figure out how to make a *home* for Ubuntu first.  Plenty of folks have installed Ubuntu to those Inspirons, you just need to find out what they did.

---

### Post by JC Cheloven on 2009-10-03
> **Bartender said:**
> 
I don't know exactly what's on the Dell EISA partition, nor whether
 you can safely delete the recovery partition after making recovery discs.
Neither I do. Can't tell what dell exactly puts on that eisa partiton. I can tell you that the inspiron 1720 I worked recently on, had one "dell utilities" partition, one "recovery partition", and one OS partition. Not sure if a fourth one. I wiped all of them except the very small utilities partiton (because if you call dell support, the first thing they'll ask you is to run the diagnostics inside that). 
As I said, removing these partitions should't affect the posibility of installig a different OS (win2 or linux, or both). Bioses doesn't look for anything in the hard disk except mbr and boot marks, as far as I know. 
However I'm not 100% sure whether deleting one or another of these partitions would affect the *current* vista installation or not (I think don't, but prepare your recovery media just in case). 
Finally I can confirm you that deleting these may affect the warranty, if the pc is in period of that. Please note this.

> **Bartender said:**
> 
Make the DVD's first.  Then do some homework and figure out exactly how you want to get get rid of at least one of those primary partitions.  Maybe running the recovery discs like I did clears out some of the partitions? I don't know.  Need to find out how Dell's recovery process behaves, which shouldn't be hard.
I couldn't say it better.
@ the OP: please follow bartender's advice if you plan to make a true ubuntu instal, or consider wubi as a much easier (although not genuine) option.

---

### Post by theozzlives on 2009-10-03
I would venture to assume that EISA would be drivers and such. Luckily Dell was kind enough to put all my stuff on DVD/CD. I just wiped my Vista, but be forewarned Dell support will have you jumping through hoops if you alter the OS. May even deny support.

---

### Post by Mark Phelps on 2009-10-03
> **Zoot7 said:**
> The Vista partitioner is the definition of useless, you'd be much better off you avoid it like the plague.


So, let me get this straight -- Vista created the free space OK and Ubuntu installer failed to use the space requested -- and somehow this renders the Vista partitioner "the definition of uselessness"??

There are links with workarounds to the Vista tool not allowing as much shrinkage as folks want -- but the tool's unwillingness to allow as much shrinkage as GParted is to prevent damage to the partition.

Don't get me wrong, I think it's a lame tool, too, but every time I've used it (and that's been quite a few), it had done EXACTLY what I requested -- and nothing more. That's not "the definition of uselessness" to me.

---

### Post by donaldt on 2009-10-03
OK, this is slightly off target, but Vista originated the problem.  I have been successfully running Ubuntu 9.04 from an external hard disk drive for about 8 months.  The two windows computers I use are configured to go to the USB drive first, so if the external HD drive is plugged in, Ubuntu starts.  If not, one boots XP and one Vista.

Also on the same HD (232 GB) is a windows NTFS section used to back up one of the computers.  Still with me so far?

I needed more space for the back up and there was a lot of space unused on the disk, so I went to windows XP disk management and tried to expand the NTFS section.  No luck.  I had free space nearby and chose 70 GB to change to logical and reformat to NTSF.  When I did that I didn't see it but the rest of the disc was apparently all an extended partition and it changed the Linux partitions all to logical as well...so Ubuntu would no longer boot.  The logical partition covered my two Linux swap partitions and one EXT3 and apparently killed my grub loader.  Ubuntu gave error 17 after an attempt to launch.

So, I thought I had killed all my Ubuntu partitions.  However, I plugged in and fired up a Linux CD and loaded Linux, opened Gparted and there are all my partitions still labeled EXT3 and Swap; all on the extended partition. Now, is there a way for me to get the grub loader to work again so I can recover my Linux system and my files, or am I still dead in the water?

Any assistance will be greatly appreciated.  I love Linux, but certain navigation software I need in my aircraft will not run (yet, they say it is coming) on Linux.

donaldt

---

### Post by Bartender on 2009-10-03
donaldt, you're hijacking this thread with an unrelated problem.  We owe it to the original poster to stick to his situation.

EDIT:  I googled "what is EISA partition"?  First hit went back to Notebook Forums -

*"That partition contains the Dell diagnostic utility...you can safely delete it, but only if you have the Dell system tools disc for your laptop"*

---

