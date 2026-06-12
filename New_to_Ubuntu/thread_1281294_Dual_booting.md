---
title: "Dual booting"
date: 2009-10-03
forum: New to Ubuntu
---

### Post by Wrathe on 2009-10-03
Hey guys,

I understand there has been many many................. threads on dual booting.
The purpose of this thread is to confirm that this is the correct process. (Vista Business is pre-installed)

1. Go to Disk management (right click computer > manage) and right click the largest partiton.
2. Click 'shrink volume' and enter the amount of space you wish for the Ubuntu OS to have.
3. Put in Ubuntu CD and restart
4. Go to BIOS (F2 in my case.  ^.- took ages to finally find it was F2) and put CD above the HDD in boot order. Save & exit
5. Go through the Ubuntu installation.  When you get to 'how to partition the disk' click on 'use largest continous free space. Finish installation.
6. Complete

This is the correct process, yes?

Also, I have a question.

The boot manager used now is GRUB, since Ubuntu was installed last, correct? How would you safe boot etc. the Windows OS?

Thanks,
Wrathe

> **_[SIZE=3]Solved - View last post[/SIZE]_**

---

### Post by ermeyers on 2009-10-03
Set BIOS for CD boot first, and boot the CD.  The Ubuntu install can do the repartitioning with a side-by-side install selection where you can choose the amount of disk for Ubuntu there.  After the install, using grub, make sure the default boot works okay for Ubuntu.  After you've got it, then boot windows, and let chkdisk adjust for the repartitioning on the windows side.

For completeness, I'll  include here that the Ubuntu Live CD has GParted available in System->Administration->Partition Editor for resizing partitions.  Anytime you resize the Windows partition, you'll see a chkdisk scan run at the next Windows boot to verify the Windows partition.

---

### Post by jarrah-95 on 2009-10-03
what you have said is correct to my knoledge exept for the shrinking to the partition you where talking about from my expierence the best way to do that is by using the partitioner inbuilt into the installer (gparted) witch is pritty straght forward if you know a little bit about computers (witch from your post it sounds like you do) and to your question after you chainload into the windows bootloader you can use safemode as you normaly whould as it is the same as booting into the windows boot loader like you whould if ubuntu wasent there.
hope this helps

---

### Post by Paqman on 2009-10-03
> **Wrathe said:**
> 
The boot manager used now is GRUB, since Ubuntu was installed last, correct? How would you safe boot etc. the Windows OS?

That's right. Once you pick the Windows option in Grub it loads up the normal Windows bootloader, NTLDR. So from that point on it's a normal Windows boot. I think it's F8 for options during a Windows boot, isn't it?

---

### Post by yanceypd on 2009-10-03
If you haven't done it yet , defrag windows to compact files befor doing the Ubuntu install.  May make things a little smoother.:)

---

### Post by Wrathe on 2009-10-04
> I shrunk my Vista by 120,000 MB (117.2 GB).  Loaded the Ubuntu CD and went through the installation progess. I started to install but eventually quit the installation.  

At the Partitioning part I selected the 'use largest continuous free space.' The graphical preview (refering to the diagram showing the partitions on the disk) of the partitions then appeared 'weird.'  It said that Vista/loghorn1 had 11.5GB (recovery partition), Vista/loghorn2 had 286.7 and Ubuntu had 2.5GB.  Is this a bug? 

Should I just install it via specifying them manually?  Is this how it is done? [http://neosmart.net/wiki/display/EBCD/Ubuntu?](http://neosmart.net/wiki/display/EBCD/Ubuntu?)


Awaiting replys. :D


**[Solved]:**
_I selected 'manually partition.'  Made root (/) 23GB, /home 115GB, swap 4.3GB.  All logical partitions._

---

