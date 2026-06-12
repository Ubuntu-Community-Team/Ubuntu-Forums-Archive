---
title: "Windows and Linux Mint"
date: 2010-06-08
forum: New to Ubuntu
---

### Post by decrow06 on 2010-06-08
Okay, so I've done this before...I know that this is a Linux Mint question but these forums are so much better.

I have an Acer Aspire One netbook and it came with windows 7 basic whatever.  

I originally wiped windows and ran linux mint exclusively.  I now need windows back.  So, I got the restore disks from Acer.  I put the disks in expecting they would just reformat and reinstall.  However, they didn't even recognize the drive.  So, using a liveusb, I reformatted the entire hard drive as ntfs.  This allowed me to restore windows, mostly.  

After the restore, windows still wouldn't boot.  I got "Error 22" and that was all.  Google led me to realize that this was a Grub error...apparently the windows restore didnt fully restore everything.  So, I decided to simply reinstall linux mint.  I set up a linux partition and the dual boot was initially quite successful.  After this was done, grub recognized both operating systems.  

I went through the windows setup, and everything seemed fine.  windows started installing its updates.  Halfway through, it decided it needed a restart.  After doing so, everything failed.  The computer couldn't even make it to the grub screen, just cycling through the bios screen and restarting.  

I essentially repeated the above process twice just to make sure nothing completely glitchy had occurred.  Does anybody know whats going on?

More importantly, does anybody know how I can fix this?  I need windows working and dual booting would be fantastic.

---

### Post by beastrace91 on 2010-06-09
The simplest solution would be to do a clean reinstall of Windows (Format of the entire drive back to Windows) and then adding Mint back afterwards in a dual boot setup.

~Jeff

---

### Post by decrow06 on 2010-06-09
That's what I was trying to do, I think, but I can't do a clean reinstall of windows.  After reformatting the entire drive to ntfs, I can install windows, but even after that windows won't boot because for some reason grub still exists.

---

### Post by rijidij on 2010-06-09
You will need to write a new boot record to your hard drive.
For Win7, follow the instructions [here]("http://support.microsoft.com/kb/927392").

HTH

---

### Post by mikewhatever on 2010-06-09
This a a purely Windows related problem, and so your best short is a Windows help and support forum or Acer customer service.

---

### Post by PinchedNerve on 2010-06-09
Did you do a quick or long NTFS reformat?

If you did the quick, then try the long version.  You'll know the difference because the quick version takes about 30 seconds & the long takes a very loooooooong time reformat.

---

### Post by HeirPixel on 2010-06-09
> **mikewhatever said:**
> This a a purely Windows related problem, and so your best short is a Windows help and support forum or Acer customer service.
I wouldn't send our friend to a Window$ forum with this one. Most of that lot will either not know how to dual-boot anything or they'll just make fun of "another Linux geek who can't figure out his own operating system, blah, blah, blah."

---

### Post by Mark Phelps on 2010-06-09
> **PinchedNerve said:**
> Did you do a quick or long NTFS reformat?


This should NOT affect the problem in any way.  The OP is unable to boot without GRUB; it's not a partition problem.  They need to remove GRUB from their MBR. Reformatting the NTFS partition will not affect that.

---

### Post by Mark Phelps on 2010-06-09
> **rijidij said:**
> You will need to write a new boot record to your hard drive.
For Win7, follow the instructions [here]("http://support.microsoft.com/kb/927392").

HTH

Excellent advice, but in my experience, "restore" media (the disks provided by OEMs) don't allow you to boot into them to do anything other than complete OS restoration.

If the OP does NOT have a Win7 Installation DVD, they can download and burn one from the following location:

[http://neosmart.net/blog/2009/windows-7-system-repair-discs/]("http://neosmart.net/blog/2009/windows-7-system-repair-discs/")

They can then use that Repair CD to run the command you mention.

---

### Post by mikewhatever on 2010-06-09
> **HeirPixel said:**
> I wouldn't send our friend to a Window$ forum with this one. Most of that lot will either not know how to dual-boot anything or they'll just make fun of "another Linux geek who can't figure out his own operating system, blah, blah, blah."

As I pointed out earlier, there was no problem with dual booting, and I truly believe that the OP should get more focused replies at a Windows forum. As for your opinion of Windows forums participants, consider that arrogance and ignorance are not uncommon even among the users of these forums.

---

### Post by decrow06 on 2010-06-09
well dual booting worked just because grub would recognize both partitions

I don't really want to deal with windows forums or acer service because those people are typically incompetent.

How do I do a long NTFS format?

Thanks for all of your help everybody.

---

### Post by rijidij on 2010-06-09
I wouldn't bother with a long reformat - it probably isn't necessary...
If you don't have the system disks, download and burn a repair disk from the link Mark Phelps suggested:> If the OP does NOT have a Win7 Installation DVD, they can download and burn one from the following location:

[http://neosmart.net/blog/2009/window...-repair-discs/](http://neosmart.net/blog/2009/window...-repair-discs/)

Then follow the instructions to write a new MBR that I posted earlier 
here: [http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

---

### Post by decrow06 on 2010-06-09
Do I want to use the /FixMbr command, or /FixBoot?

---

### Post by grantoos on 2010-06-09
Wipe the drive clean with KillDisk. [http://www.killdisk.com/downloadfree.htm](http://www.killdisk.com/downloadfree.htm)

1. Killdisk
2. Install Windows
3. Install Linux

Enjoy dual booting!

---

### Post by rijidij on 2010-06-09
> **decrow06 said:**
> Do I want to use the /FixMbr command, or /FixBoot?

I would use /FixBoot because, at this point, we are not too bothered about the partition table.
After you have cleanly installed Windoze, you can then re-install Linux.
This will take care of the partitioning and will write Grub(2?) to the MBR.
Then everybody should be happy.. 

Have a look at [this excellent site]("http://members.iinet.net.au/~herman546/index.html") for more information about dual-booting.
You might find the [MBR page]("http://members.iinet.net.au/~herman546/p6.html") of particular interest.

---

### Post by decrow06 on 2010-06-09
Thanks everyone, I have now successfully managed to get Windows working (so far) without Linux.

---

