---
title: "Installation crash with Win 7"
date: 2010-06-08
forum: New to Ubuntu
---

### Post by Shahram A on 2010-06-08
I like to change my operating system, I looked for information in the Internet and it appeared that right now Ubuntu is the easiest for learning and also the most developed to transfer from windows, but I am not sure if my conclusion is correct.
I am new to Internet and at most can be considered an advanced user in windows, i.e. I don't have a lot of technical knowledge.
When I transfer I would need to transport my Microsoft office documents including databases, word, excel, notebook etc. but would it work?

Please if anyone has other guide lines let me know.

I have tried trial installations with the following results and questions:
Installing Ubuntu on Packard Bell laptop (Easy Note MH36)
Using 250 GB Hard Disk
Windows 7 - 32 bit
Not able to use optical (CD) installation
Downloaded Ubuntu 10.04 ISO
Installed successfully inside windows

For hard disk trial installation
Installed the software in USB once with unetbootin-windows442
Next time with Universal-USB-Installer-v1.6.0
It booted correctly with booth and showed the following crash problem with both:
 It carried quickly up to language selection, I choose English and clicked on the forward button, but at this stage the circular progress icon keeps going without stop and a white crash icon appears on the taskbar
Once I left it to work in this condition for half an hour but nothing happened.
Once I deleted partition D to install Ubuntu on the that partition,
Next I have changed the partitioning and opened a roughly 50 GB slot as free space as the last partition, while there are three windows partitions plus the small system partition that windows 7 makes (four windows partitions in all).
I have the following questions:
Can Ubuntu be installed on the last partition
Is it better to be there or is it better to be on the second partition
Can the partition be NTFS formatted so Ubuntu can see and use files on other partitions…
If it cannot be NTFS should it be ext3 or ext4 and would that come up in the installation questions or not?

How can I solve the Crash problem, why is it crashing, could it be incompatibility with the hardware, I have seen a dialog box appearing saying that you can install or update with commercial drives – might the cause of the crash be related to drivers?

I can only check the Internet once a day, so if anyone answers it would at least take 24 hours for me to try the answer.

---

### Post by Mark Phelps on 2010-06-09
It is generally a BAD idea to force an Ubuntu installation onto a new machine before you've tried it out first.  A much better approach is to boot from the LiveCD and see how well it works.  That way, if you run into problems, you can post them here and see what is involved in solving them before you do the install.

As to crashing, it can be almost anything.  And, since the system is unstable, it's going to be very difficult trying to diagnose the problem.

Drives can only support four primary partitions -- which it appears you already have -- so you can't just create another partition. Plus, Ubuntu can't be installed in native mode to an NTFS partition; it can only use that when installed via Wubi -- which, as you have seen, brings with it its own problems.

Don't use the Ubuntu installer to shrink any existing partitions.  That runs the risk of corrupting the MS Windows OS and rendering it unbootable.  Use the Win7 Disk Management utility to shrink the partitions instead.

I should warn you, though, that without the use of an optical drive, you're really asking for problems.  Why? Because solving such problems typically involves booting OUTSIDE the OS from one or more different CDs -- and since you can't do this, you will have a very hard time doing such repairs.

---

### Post by Shahram A on 2010-06-09
> **Mark Phelps said:**
> It is generally a BAD idea to force an Ubuntu installation onto a new machine before you've tried it out first.  A much better approach is to boot from the LiveCD and see how well it works.  That way, if you run into problems, you can post them here and see what is involved in solving them before you do the install.

As to crashing, it can be almost anything.  And, since the system is unstable, it's going to be very difficult trying to diagnose the problem.

Drives can only support four primary partitions -- which it appears you already have -- so you can't just create another partition. Plus, Ubuntu can't be installed in native mode to an NTFS partition; it can only use that when installed via Wubi -- which, as you have seen, brings with it its own problems.

Don't use the Ubuntu installer to shrink any existing partitions.  That runs the risk of corrupting the MS Windows OS and rendering it unbootable.  Use the Win7 Disk Management utility to shrink the partitions instead.

I should warn you, though, that without the use of an optical drive, you're really asking for problems.  Why? Because solving such problems typically involves booting OUTSIDE the OS from one or more different CDs -- and since you can't do this, you will have a very hard time doing such repairs.

 Thank you Mark Phelps I shall have to see if I can arrange for an optical drive option - its somewhat difficult in my situation and might take some time. I understood the Partitioning notes. Thanks again  Shahram

---

### Post by Phillip Spencer on 2010-06-09
> **Shahram A said:**
> 
Once I deleted partition D to install Ubuntu on the that partition,
Next I have changed the partitioning and opened a roughly 50 GB slot as free space as the last partition, while there are three windows partitions plus the small system partition that windows 7 makes (four windows partitions in all).
I have the following questions:
Can Ubuntu be installed on the last partition
Is it better to be there or is it better to be on the second partition
Can the partition be NTFS formatted so Ubuntu can see and use files on other partitions…
If it cannot be NTFS should it be ext3 or ext4 and would that come up in the installation questions or not?

I can only check the Internet once a day, so if anyone answers it would at least take 24 hours for me to try the answer.

Having screwed up my own Windows 7 partitions and subsequently had horrendous problems I endorse the Mark's comments about finding better ways to sort out partitions!

I have had a lot of help from this forum over the last couple of weeks.  While I do not know if it will help you directly, you may find it helpful to check the thread I started around my own partitioning problems, particularly the advice given by ranch hand and oldfred, which has greatly increased my knowledge.  A couple of CD tools have been very helpful - Windows 7 32-bit repair kit and Ubuntu rescue remix.  Links to these are in the thread. See
[]("http://ubuntuforums.org/showthread.php?t=1491232")[http://ubuntuforums.org/showthread.php?t=1491232](http://ubuntuforums.org/showthread.php?t=1491232)

Good luck!
Phillip

---

### Post by Mark Phelps on 2010-06-09
Along the same lines as Phillip ... if you're going to arrange for an optical drive, one of the first things you should do with it is use the Win7 Backup feature to create and burn a Win7 Rescue CD.  That will be invaluable later should you need to repair the Win7 boot loader.

Another really valuable CD you can make would be a GParted LiveCD -- which you can get from distrowatch.com.

---

### Post by Shahram A on 2010-06-18
Thank you Mark and Phillip for your help and care
Due to certain social obligations to help someone else, I haven't tried anything new yet, but I hope to be back on this in the future.
I just want to thank you
Shahram

---

### Post by Shahram A on 2010-07-06
I installed Ubuntu with the optical drive
There were three primary partitions for windows 7 with roughly
100 MB automatic partition reserved by system
50 GB system partition
50 GB documents partition
I gave the other half of the disk to Ubuntu, it installed properly.
The interesting thing is that we read only four primary partition are allowed. Well Ubuntu created two partitions, one large Ext4 and a smaller one (roughly 4.5 GB) that I guess must for cash.
In the windows 7 disk management tool, both are shown as primary. So all together now the disk shows five primary partitions.

---

