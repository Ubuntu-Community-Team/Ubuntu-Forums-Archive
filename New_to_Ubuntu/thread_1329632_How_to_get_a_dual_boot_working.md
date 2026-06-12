---
title: "How to get a dual boot working"
date: 2009-11-17
forum: New to Ubuntu
---

### Post by da burger on 2009-11-17
I have a laptop that runs vista currently. I want to get it running a dual boot with ubuntu 9.10 and have the appropriate live cd.  
However I just wanted to check I have this right. If I shrink my vista partition using [this]("http://www.vistarewired.com/2007/02/16/how-to-resize-a-partition-in-windows-vista") method then have the live cd install in the free space that is created will that give me a working dual boot or is there anything else I need to do.
My other question is will the live cd create primary or logical partitions.
If primary: how many will it make because I only have one left
If logical do I need to create the extended partition or will it do that as well.
Thanks in  advance.
Angus

---

### Post by wrgb2 on 2009-11-17
da burger, the Guided Partitioning in Ubuntu will take care of shrinking the partition, defining the new partitions and everything for you.  Just select the option to install Ubuntu side-by-side along with Vista.

---

### Post by kansasnoob on 2009-11-17
Yes, it's always best to resize Vista using it's own tools. This is also a nice, simple guide:

[http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm?page=1](http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm?page=1)

---

### Post by da burger on 2009-11-17
Thanks for the very quick reply, just wanted to check before I break my pc. I do still need to know about the partions though.
Thanks again.
Angus

---

### Post by Cheesemill on 2009-11-17
The install will create 2 partitions. One for / and one for swap. Unlike Windows neither of these have to be primary, if you already have 3 partitions the installer will recognise this and create an extended partition to hold these Ubuntu partitions.

---

### Post by da burger on 2009-11-17
Thanks a lot. Wow they seem to have made this almost idiot proof. Fantastic.

---

### Post by RJ12 on 2009-11-17
Glad we solved your problem
Also like kansasnoob said Vista's partition **_MUST_** be shrinked using its **_OWN_** utility
Also it might be a good idea to use the Live CD to test your hardware. If you have any questions/problems feel free (Dont you just love that word) to post here



-Welcome to Linux, Life without Walls,Gates,or Windows:P

---

### Post by wilee-nilee on 2009-11-17
> **da burger said:**
> Thanks a lot. Wow they seem to have made this almost idiot proof. Fantastic.

If you choose the install partition-er and choose side by side without having a free space notice the slider on the bottom to adjust the partition sizes, it should default to half vista half Linux but be sure of that.

---

### Post by Bartender on 2009-11-17
Did you make your recovery DVD's yet?  Don't try to install Ubuntu before you do that!!

---

### Post by lkraemer on 2009-11-17
You really should run Disk Clean, then Defrag the Drive that has Vista
loaded before attempting any changes.  Like those have posted you should
use Vista to shrink the existing partition.  Be aware that if you have
a Recovery partition that is immediately after the Vista partition,
I's suggest moving it so that it stays immediately after Vista, before
you install Ubuntu.  I have done this before and it works good.

Also, there is a LIMIT of FOUR Primary Partitions on any Physical Hard
Drive.  If Vista and the Recovery Partitions are existing that only leaves
two, one for / (ext3 or ext4) and another for linux-swap.  You can use
a Logical (Extended) partition and install on the Logical, but I prefer
not to go that route.  Just my preference......

Burn your LiveCD as Disk-at-Once (DAO) and at a slow speed, then VERIFY the
MD5SUM of the LiveCD.  If it all checks out good boot the LiveCD and give
Ubuntu a trial.  I think you will be impressed, and will never look 
back. In fact most stop using the dual boot as time goes by and just boot
into Linux.  Time will tell in your case......

Make a list of the MUST HAVE software that is keeping you from making a
total conversion to Ubuntu.  Then find some equivalent software, or better
software that runs under Linux.  There are lots of sites with this info.

Google search the Fourm for help with a specific problem, as someone has been
there before.
 
Good Luck on the transition......

lk

---

### Post by da burger on 2009-11-18
> **Bartender said:**
> Did you make your recovery DVD's yet?  Don't try to install Ubuntu before you do that!!

I did that as soon as I got the laptop!






> **lkraemer said:**
> 
Also, there is a LIMIT of FOUR Primary Partitions on any Physical Hard
Drive.  If Vista and the Recovery Partitions are existing that only leaves
two, one for / (ext3 or ext4) and another for linux-swap.  You can use
a Logical (Extended) partition and install on the Logical, but I prefer
not to go that route.  Just my preference......

Burn your LiveCD as Disk-at-Once (DAO) and at a slow speed, then VERIFY the
MD5SUM of the LiveCD. 

I already have my live cd and I have tested it!
I have no choice but to use Logical and Extended partitions as my harddrive came with 3 partitions. (C drive S drive and recovery).


To check I have everything right these are the final instructions:
1. Run file cleanup and Disk Defragmenter
2. Shrink the vista partion an appropraite ammount using it's own tools.
3. Reboot with the live cd in and tell it to install in the free space.

Thank a lot, particularly given the speed of the responses (most forums I have been on it would be about a month before I got this much help)

---

### Post by da burger on 2009-11-28
Hi sorry to open up this thread again but I have just started doing this (I had some important stuff going on with my laptop recently so I didn't want it out of action). Anyway after running both defragmenter a and dish cleanup I tried to make the partition smaller. The partition claims to have 60 gb free yet I could only shrink it by 16. Why is this. I really want to get this sorted now. Thanks in advance for any help.
Angus

---

### Post by Bartender on 2009-11-28
Windows operating systems have an annoying habit of placing some data way out there in the free space of a HDD, then marking it unmovable.

I suspect MS does it that way on purpose.  

60 GB "free" means there's 60 GB of disk space that doesn't have data written to it.  Most of that disk space is probably trapped between Windows data, which means it's not helping you get Ubuntu installed.

Google "defrag windows" or "shrink windows" or "windows move unmovable" etc.  I don't remember where I read it but have seen some interesting ideas for unsticking that "unmovable data" and shoving it to the left.

---

### Post by Shazaam on 2009-11-28
AFAIK the "unmovable files belong mostly to "System Restore" (restore points). Does Vista still have "Safe Mode"? You might be able to do the old trick that worked for XP...
1. Go to wherever Vista has it's setting for the page (virtual memory) file and change it to "none". Hit "set" then "Apply".
2. Go to "System Restore" settings. Delete all but the last one if you can.
2. Reboot into Safe mode and disk cleanup/defrag from there.
3. When done reboot back into Safe mode and see if you can gain more space with the partitioner.
4. If it lets you shrink Vista reboot into normal mode when done and re-enable the page file.
5. Install Ubuntu.

---

### Post by mt1234 on 2009-11-28
> **lkraemer said:**
> You really should run Disk Clean, then Defrag the Drive that has Vista
loaded before attempting any changes.  Like those have posted you should
use Vista to shrink the existing partition.  Be aware that if you have
a Recovery partition that is immediately after the Vista partition,
I's suggest moving it so that it stays immediately after Vista, before
you install Ubuntu.  I have done this before and it works good.

 lk

How can I move the Recovery partition? Should this be done using the Windows Disk Management tool (I have Windows 7)? There doesn't seem to be an option in that tool to move.  I performed all of the suggested steps in this thread (prior to reading it), except for the moving the Recovery partition. Now I have trouble booting Windows. It seems like I should remove Ubuntu, move the Recovery partition, then reinstall Ubuntu. However, I already have GRUB2 installed and I'm not sure if it will allow me to continue to boot if I make these changes. Any suggestions?

---

### Post by steveneddy on 2009-11-28
> **da burger said:**
> I have a laptop that runs vista currently. I want to get it running a dual boot with ubuntu 9.10 and have the appropriate live cd.  
However I just wanted to check I have this right. If I shrink my vista partition using [this]("http://www.vistarewired.com/2007/02/16/how-to-resize-a-partition-in-windows-vista") method then have the live cd install in the free space that is created will that give me a working dual boot or is there anything else I need to do.
My other question is will the live cd create primary or logical partitions.
If primary: how many will it make because I only have one left
If logical do I need to create the extended partition or will it do that as well.
Thanks in  advance.
Angus

I didn't read the entire thread, but I would like to offer an alternative to dual booting, which is using a virtual machine.

[VirtualBox]("http://www.virtualbox.org/wiki/Downloads") will allow you to run other operating systems while Windows is running. Windows will "host" the other OS, so to speak.

I run Ubuntu but use Vista and Windows7 in a VM and it is a great alternative to a dual boot. Of course if you are gaming on Windows you may prefer to run a dual boot setup.

---

### Post by mysticdragon on 2009-11-28
Good Morning;
I recently installed Ubuntu 9.10 on my school computer, so my system is now a dual boot (Vista/Ubuntu).  Because nearly all my classes are Windows based, I was going to restore the Vista Bootloader as the primary bootloader and have Ubuntu as the secondary OS on the system.

I have been searching for information on resetting Vista as the primary bootloader, including referencing the article included here.  However, when I attempt to bring up the file mentioned in the article, it is nowhere to be found.  Could it be listed as a different name?  For those not familiar with the particular part of the article I'm referring to, here is an excerpt:

[COLOR=Red]*If however you prefer to keep Vista in charge of things, then you'll need to do a little bit of tweaking.*[/COLOR]
 [COLOR=Red]*Firstly, boot into Ubuntu and go to Applications --> Accessories --> Terminal. Then, type in **sudo gedit /boot/grub/menu.lst**.*[/COLOR]

Any help would be appreciated, whether it be clarifying the above information, or offering another method.  Thank you!

---

### Post by Some Penguin on 2009-11-28
> **mysticdragon said:**
> Good Morning;
I recently installed Ubuntu 9.10 on my school computer, so my system is now a dual boot (Vista/Ubuntu).  Because nearly all my classes are Windows based, I was going to restore the Vista Bootloader as the primary bootloader and have Ubuntu as the secondary OS on the system.

I have been searching for information on resetting Vista as the primary bootloader, including referencing the article included here.  However, when I attempt to bring up the file mentioned in the article, it is nowhere to be found.  Could it be listed as a different name?  For those not familiar with the particular part of the article I'm referring to, here is an excerpt:

[COLOR=Red]*If however you prefer to keep Vista in charge of things, then you'll need to do a little bit of tweaking.*[/COLOR]
 [COLOR=Red]*Firstly, boot into Ubuntu and go to Applications --> Accessories --> Terminal. Then, type in **sudo gedit /boot/grub/menu.lst**.*[/COLOR]

Any help would be appreciated, whether it be clarifying the above information, or offering another method.  Thank you!

Actually, yes, it could be listed as different name.  Either 'menu.lst' or 'grub.conf' may be used.  The same edits will apply.

---

### Post by Bartender on 2009-11-28
mt -
I have a different opinion on the recovery partition.  If you've made your recovery discs you probly don't need the partition at all.  I helped some friends burn their recovery discs with two different HP machines about a year ago.  HP said right in their user manual that the recovery partition is inaccessible after you've made your discs and could be deleted!

I always try to get rid of unnecessary partitions

---

### Post by ed-koala on 2009-11-28
da burger, what exactly are you using Vista for?  Really, unless you run graphic intensive games, you don't need it.  VirtualBox is a great solution for *most* of those favorite apps you want to hang on to, but otherwise you may want to consider doing away with Vista and using all that valuable space for programs instead of spyware (hehehehe).

I'm an Ubuntu user ... I do have to run XP in VirtualBox for a couple of old games Wine won't run, but otherwise, screw Microsoft.

---

### Post by mysticdragon on 2009-12-15
Hello Again;

I've just updated my windows partition to Windows 7, but still have an issue that has been there since I first set the computer up as a dual boot.

I am running Win 7/Karmic Koala, and currently have two bootloaders.  When the system boots up, it starts with Grubloader, which gives me the option of Ubuntu or Windows 7 (Windows 7 is my school account, with all my school information, certificates, etc.).  I have tried previously to reduce it down to one bootloader, but ended up losing both.  Is there a way of just getting it back down to one bootloader, or would I just be better of leaving things be, as it does not appear to have hampered system performance at all?

Any help would be great.  Thanks in advance.

---

