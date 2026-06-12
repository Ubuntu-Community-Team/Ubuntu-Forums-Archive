---
title: "Dual-booting Vista and Ubuntu"
date: 2010-10-08
forum: New to Ubuntu
---

### Post by Tawrtoise on 2010-10-08
First off, I'd like to let you know that I'm very new to Ubuntu, or any Unix based OS for that matter. I have read lots but I still don't understand a lot, and I have not used Unix at all. 

Also, I am posting this because all of the threads that I found after searching were about Windows not booting on a dual-boot, however, I am posting this to hopefully find a detailed guide to dual-booting Ubuntu and Vista upon installation. Currently, I have Vista installed and I want to start using Ubuntu. I want to dual-boot so that I can learn and get used to Linux but still complete certain tasks that I may need Windows for. Any help on this is greatly appreciated and I apologize in advance if this is posted elsewhere.

---

### Post by SnakeEye on 2010-10-08
Firstly you have to download Ubuntu
from this link : [http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)

then when you get your ISO image mount it using any mounting software as

ultra ISO or Power ISO

then run wubi installer  that is a software let you install ubuntu in windows 

without any changes .

or you can burn the ISO image on a CD and boot from it using the live property

of the burned CD

just reply if you want any help

---

### Post by slooksterpsv on 2010-10-08
> **Tawrtoise said:**
> First off, I'd like to let you know that I'm very new to Ubuntu, or any Unix based OS for that matter. I have read lots but I still don't understand a lot, and I have not used Unix at all. 

Also, I am posting this because all of the threads that I found after searching were about Windows not booting on a dual-boot, however, I am posting this to hopefully find a detailed guide to dual-booting Ubuntu and Vista upon installation. Currently, I have Vista installed and I want to start using Ubuntu. I want to dual-boot so that I can learn and get used to Linux but still complete certain tasks that I may need Windows for. Any help on this is greatly appreciated and I apologize in advance if this is posted elsewhere.

It is, but not a problem, now how do you want to dual-boot - haha.

1. Is you can partition your hard drive (Ubuntu will walk you through it) and give Ubuntu x amount of space.
2. You can install Ubuntu via Wubi, which will allow you to have Ubuntu installed like a program on Windows, but you reboot to boot into it - maximum file (partition is on a file) size is up to 30GB. - Slower, but better until you're sure you want to transition further.

Now I'd boot off of the Live CD and make sure your stuff works, e.g. Wireless (if it's a laptop or has a wireless card), display, will actually boot, etc.

Let me know which option, 1, uses a grub boot loader that you select what you want to boot into, looks really unix like. 2 uses with Vista bootloader and looks like when you go into the options for like safe mode on vista.

---

### Post by arochester on 2010-10-08
Look at "How to dual-boot Vista with Linux (Vista installed first) -- the step-by-step guide with screenshots" - [http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm)

---

### Post by sandyd on 2010-10-08
> **Tawrtoise said:**
> First off, I'd like to let you know that I'm very new to Ubuntu, or any Unix based OS for that matter. I have read lots but I still don't understand a lot, and I have not used Unix at all. 

Also, I am posting this because all of the threads that I found after searching were about Windows not booting on a dual-boot, however, I am posting this to hopefully find a detailed guide to dual-booting Ubuntu and Vista upon installation. Currently, I have Vista installed and I want to start using Ubuntu. I want to dual-boot so that I can learn and get used to Linux but still complete certain tasks that I may need Windows for. Any help on this is greatly appreciated and I apologize in advance if this is posted elsewhere.
[https://help.ubuntu.com/community/RecoveringWindows#Resizing%20a%20Windows%20Partition%20in%20Windows](https://help.ubuntu.com/community/RecoveringWindows#Resizing%20a%20Windows%20Partition%20in%20Windows)
Follow the section here (only the resizing a windows partition in windows section)

then, boot from the ubuntu cd. When you get to the partitoning stage of the installation, choose "use largest block of free space" (or similar, I havnet opened the installer for some time...)

---

### Post by Tawrtoise on 2010-10-08
> **slooksterpsv said:**
> It is, but not a problem, now how do you want to dual-boot - haha.

1. Is you can partition your hard drive (Ubuntu will walk you through it) and give Ubuntu x amount of space.
2. You can install Ubuntu via Wubi, which will allow you to have Ubuntu installed like a program on Windows, but you reboot to boot into it - maximum file (partition is on a file) size is up to 30GB. - Slower, but better until you're sure you want to transition further.

Now I'd boot off of the Live CD and make sure your stuff works, e.g. Wireless (if it's a laptop or has a wireless card), display, will actually boot, etc.

Let me know which option, 1, uses a grub boot loader that you select what you want to boot into, looks really unix like. 2 uses with Vista bootloader and looks like when you go into the options for like safe mode on vista.

I would prefer to use the first option you said, so that I can have more space for Ubuntu. I'm downloading Ubuntu 10.04 right now to burn to a disc. By the way, the last time I tried to do this, I believe I lost everything that was on my HDD. I would like to avoid that this time.

---

### Post by sandyd on 2010-10-08
> **slooksterpsv said:**
> It is, but not a problem, now how do you want to dual-boot - haha.

1.** Is you can partition your hard drive (Ubuntu will walk you through it) and give Ubuntu x amount of space.**

[B]NOOOOOOOO. don't use the ubuntu installer to give ubuntu x amount of space. this will fry windows vista/7 bootloader if your cylinders aren't aligned, and will fry windows vista/7 if you resize the disk

[/B] 2. You can install Ubuntu via Wubi, which will allow you to have Ubuntu installed like a program on Windows, but you reboot to boot into it - maximum file (partition is on a file) size is up to 30GB. - Slower, but better until you're sure you want to transition further.

Now I'd boot off of the Live CD and make sure your stuff works, e.g. Wireless (if it's a laptop or has a wireless card), display, will actually boot, etc.

Let me know which option, 1, uses a grub boot loader that you select what you want to boot into, looks really unix like. 2 uses with Vista bootloader and looks like when you go into the options for like safe mode on vista.
.

---

### Post by slooksterpsv on 2010-10-08
> **sandyd said:**
> .

I manually resize my partitions, like a pro haha jk. I usually resize windows partition in windows (when I had/used windows), then had ubuntu create the partition from the free space specifying how I wanted it. Usually Windows had to run a chkdsk to fix itself afterwards (windows 7 and vista, xp never had a problem...) but yeah.

---

### Post by wilee-nilee on 2010-10-08
Op here is a link to a very comprehensive site that covers just about anything you can imagine.
[http://members.iinet.net.au/~herman546/p23.html](http://members.iinet.net.au/~herman546/p23.html)

If you come to a forum that helps people fix stuff it looks like there are more problems then there actually are, you have to recognize the source of this impression.

I would avoid wubi, it is a option, but much harder to fix, and problematic in several ways. I can appreciate the developers intentions with wubi, but I think it can leave a bad impression and inaccurate impression of the stability of many open source OS.

---

### Post by jtarin on 2010-10-08
> **Tawrtoise said:**
> By the way, the last time I tried to do this, I believe I lost everything that was on my HDD. I would like to avoid that this time.Then make sure you have a way to recover Windows before you start and backup your data.

---

### Post by Quackers on 2010-10-08
Also if you don't have a Windows system disc or Recovery disc I would find one :-)

---

### Post by Tawrtoise on 2010-10-08
> **arochester said:**
> Look at "How to dual-boot Vista with Linux (Vista installed first) -- the step-by-step guide with screenshots" - [http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm)

This tutorial is for installing 9.04. Will this method work with 10.04 too?

---

### Post by jtarin on 2010-10-08
> **Tawrtoise said:**
> This tutorial is for installing 9.04. Will this method work with 10.04 too?
Yes...that's a fine tutorial.

---

### Post by Tawrtoise on 2010-10-08
> **jtarin said:**
> Yes...that's a fine tutorial.

Alright, thank you. I just wanted to make sure, I'm a bit worried because of my past experience with installing ubuntu :P

---

### Post by Tawrtoise on 2010-10-08
Sorry for the double post. But I'm doing this tutorial and when I shrink the volume of my main partition, it is only allocating 14mb. I have a feeling this is not very good.

---

### Post by slooksterpsv on 2010-10-08
> **Tawrtoise said:**
> Sorry for the double post. But I'm doing this tutorial and when I shrink the volume of my main partition, it is only allocating 14mb. I have a feeling this is not very good.

Yeah umm... yeah 14MB is small, you'll need at least 200x that just to install Ubuntu. Defrag your windows partition, delete unneeded restore points, remove shadow copies, disable the page file, and delete the hiberfil.sys. If none of that helps let me know.

---

### Post by jtarin on 2010-10-08
Check your drive in Gparted to see if your disk is tagged as "Dynamic".If so you will not be able to install Linux until it is converted to a Basic drive. Converting will lose all Windows data.

---

### Post by sandyd on 2010-10-08
> **Tawrtoise said:**
> Sorry for the double post. But I'm doing this tutorial and when I shrink the volume of my main partition, it is only allocating 14mb. I have a feeling this is not very good.
defragg time.
how much free space do you have on the main partition

---

### Post by Tawrtoise on 2010-10-08
> **sandyd said:**
> defragg time.
how much free space do you have on the main partition

I defragged, disabled hibernation, deleted shadow copies, as well as old system restores and disabled paging. Same thing, only 14mb can be allocated. I was going to use Gparted but I'm not positive I have a vista boot disk.

---

### Post by slooksterpsv on 2010-10-08
> **Tawrtoise said:**
> I defragged, disabled hibernation, deleted shadow copies, as well as old system restores and disabled paging. Same thing, only 14mb can be allocated. I was going to use Gparted but I'm not positive I have a vista boot disk.

What kind of a computer is it?

---

### Post by Tawrtoise on 2010-10-08
> **slooksterpsv said:**
> What kind of a computer is it?

Toshiba Sattelite L305D

---

### Post by corcomp84 on 2010-10-08
yea well it has came a long way since the last time you installed it i am sure, I find it faster and simpler to install Ubuntu then it is to install windows,, LOL.. IL tell you what you should be able to do everything and more with your Ubuntu computer.. a few things it cant do is -- yahoo messenger, I tunes, Magic jack and of course Net-flix.. other than that it should be fine..

---

### Post by corcomp84 on 2010-10-08
Is your hard drive full? It sounds like you are mounted on one of the partitions.. before you can resize it you have to unmount it.. so long as you are using the live CD.. how much free space does your drive actually have? you might also be trying to resize the system restore partition which is normally full.. I would make sure you are resizing and partitioning the right one.

---

### Post by MisterGaribaldi on 2010-10-08
There is great utility in being able to resize partitions. However, you can potentially lose data that way.

My preferred way is a completely clean from-scratch install.

1. Boot from the Windows DVD and use it to split your HDD however you want. (For me, usually in half.)

2. Set up Windows however you like on the first half of the space.

3. Leave the rest unallocated.

4. Boot off your Ubuntu CD. Tell it to use all available unallocated space.

5. Reboot


That's about it. This way, you're assured you're starting with no fragmentation, no files scattered such that resizing might trample on them, and with no lingering ghosts from your existing Windows install (which probably at this point has a bit of rust anyhow.)

---

### Post by lisati on 2010-10-08
To free up more space, you might want to clean out the files in the Windows %temp% folder as well. The "Disk Clean up" utilities that have come with the versions of Windows I've used (98SE, XP, Vista) don't get rid of **all** the clutter there, so you might have to do it manually. 

(Unashamed plug for some "freeware" to help with this, but be aware of the caveat: [http://lisati.serveblog.net/?p=104](http://lisati.serveblog.net/?p=104))

---

### Post by Tawrtoise on 2010-10-09
Right now, I'm a little confused as to what it is I need to do. I have a pretty good tutorial (that is on the first page, I believe), and I get a problem on the first step and have gone through several forks in the road. I really have no idea what to do.

---

### Post by jtarin on 2010-10-09
> **Tawrtoise said:**
> I defragged, disabled hibernation, deleted shadow copies, as well as old system restores and disabled paging. Same thing, only 14mb can be allocated. I was going to use Gparted but I'm not positive I have a vista boot disk.Gparted is located on your Ubuntu Live CD. Boot the CD into the "TRY" mode and get to the Gnome desktop. Then in the main menu>system>administration you will find Gparted. Execute and view only your disk information.....see if it is labeled "Dynamic". If your disk is dynamic no amount of cleanup will help.

---

### Post by jtarin on 2010-10-09
> **corcomp84 said:**
> yea well it has came a long way since the last time you installed it i am sure, I find it faster and simpler to install Ubuntu then it is to install windows,, LOL.. IL tell you what you should be able to do everything and more with your Ubuntu computer.. a few things it cant do is -- yahoo messenger, I tunes, Magic jack and of course Net-flix.. other than that it should be fine..You can do [Yahoo messenger]("http://in.docs.yahoo.com/messenger/download/unix.html") but its not the optimal version you see for Windows.I've installed this on more Linux distros than you can shake a messenger at.You might have to soft-link to new version numbers for libs in some cases.

---

### Post by Tawrtoise on 2010-10-09
Oh dear. I seem to have downloaded wubi instead of the Ubuntu iso to run the live cd?? That's weird. Where is the iso download link now?

---

### Post by jtarin on 2010-10-09
No...just boot from the CD.....choose it as your first boot device. Don't run it from Windows.
[You should see this menu.]("http://www.trainsignaltraining.com/wpnew/wp-content/uploads/2009/02/3.jpg") Choose the try selection. If you have the wrong CD then we can still check possibly from within Windows.

---

### Post by Tawrtoise on 2010-10-09
> **jtarin said:**
> No...just boot from the CD.....choose it as your first boot device. Don't run it from Windows.

What do you mean my first boot device?

I have the iso for 10.04 burnt to a dvd. I put the disk in and restart my computer, but it just boots windows like normal.

---

### Post by MisterGaribaldi on 2010-10-09
Two issues on that:

1. What's your boot order set to in BIOS? Unless your DVD/CD drive is first, you'll never get anywhere.

2. How did you burn the image to disc? What did you use to do this?

---

### Post by Tawrtoise on 2010-10-09
Okay. Smart me, didn't even know about the boot order. But that's fixed now. I'm working on resizing my partition via DiskPart.exe and then I'll continue with the tutorial that was posted at the beginning of this thread.

---

### Post by Tawrtoise on 2010-10-09
If there are any suggestions on this, please let me know.

---

### Post by Jetso on 2010-10-09
I had the same problem, but got it fixed! When you first turn the computer or laptop on, and it shows the type of computer (In my case Dell) Press F12 and Choose your CD-R/DVD+RW/DVD-RW and then it will boot Ubuntu, without making *any* changes to your current system.

---

### Post by Tawrtoise on 2010-10-09
> **Jetso said:**
> I had the same problem, but got it fixed! When you first turn the computer or laptop on, and it shows the type of computer (In my case Dell) Press F12 and Choose your CD-R/DVD+RW/DVD-RW and then it will boot Ubuntu, without making *any* changes to your current system.

I've already fixed that problem, right now I am trying to shrink a partition and it's still not working.

---

### Post by Jetso on 2010-10-09
Oh, I'm sorry. Are you trying to shrink it inside Windows or while booting the Ubuntu LiveCD?

---

### Post by Tawrtoise on 2010-10-09
> **Jetso said:**
> Oh, I'm sorry. Are you trying to shrink it inside Windows or while booting the Ubuntu LiveCD?

I'm trying to shrink it inside Windows. The disk management will only let me shrink it by 14mb (obviously not enough), and now diskpart.exe won't do it either. I didn't want to use Gparted because I don't think I have a bootable vista disk.

---

### Post by Jetso on 2010-10-09
Mmm... I'm sorry, but I don't know how to help you there, I had someone show me how to shrink it, * in person * and I don't think that was a problem...

---

### Post by oldfred on 2010-10-09
You should always have a bootable repair/live cd/USB for any installed system:

If your PC did not come with a complete Vista or Win7 installation CD, you can download a Recovery Disc at the following links:
Windows Vista/7 Recovery Disc - for repairs only
[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)
Vista will not repair XP (they create the boot sectors differently) but can run chkdsk.
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

If you have to use gparted be aware of the checkbox, That often prevents any major boot issues. You still have to run chkdsk on any resize of Vista.

starting with Vista - MSoft made some changes to the way it installs itself in a partition. Gparted can deal with it but should have the round to cylinder unchecked.
Herman on checkbox
[http://www.uluga.ubuntuforums.org/showpost.php?p=7816261&postcount=17](http://www.uluga.ubuntuforums.org/showpost.php?p=7816261&postcount=17)
Vista and Partitioning - details
[http://www.multibooters.co.uk/partitions.html](http://www.multibooters.co.uk/partitions.html)

---

### Post by migs73 on 2010-10-09
> **jtarin said:**
> Gparted is located on your Ubuntu Live CD. Boot the CD into the "TRY" mode and get to the Gnome desktop. Then in the main menu>system>administration you will find Gparted. Execute and view only your disk information.....see if it is labeled "Dynamic". If your disk is dynamic no amount of cleanup will help.

OP, JTarin's Gparted request will not resize or alter your partitions at all, he just wants you to use that tool from the live CD to check to see if the HDD partition is marked as 'dynamic', and not to make any changes.
It is safe to do so.

---

### Post by Tawrtoise on 2010-10-09
> **migs73 said:**
> OP, JTarin's Gparted request will not resize or alter your partitions at all, he just wants you to use that tool from the live CD to check to see if the HDD partition is marked as 'dynamic', and not to make any changes.
It is safe to do so.

Is resizing the partition using the Gparted live cd a good option? 

Also, partition is basic, and not dynamic, it's also an NTFS if that changes anything.

---

### Post by Tawrtoise on 2010-10-09
Well friends, I found a vista installation disk and shrinked the partition using Gparted and got Ubuntu installed. It's running amazingly smooth in comparison to Vista and the wireless has yet to give me any problems. Thank you for all your help, and do I need to change the tag to SOLVED? Or will a mod do that?

Thanks again, this thread was a big help.

---

### Post by oldfred on 2010-10-09
You can use gparted but see my post #40 on caveats. Make sure you have the Vista repair CD as at the very least after any resizing it will want to run chkdsk. Reboot Vista several times before installing Ubuntu to make Vista is ok.

Windows NTFS partitions need at least 20% free and more like 30% free to allow it to write without major slowdowns. So houseclean windows before and then do not shrink too much. Supposedly defrag is not required but it does speed up resizing.

---

### Post by RJ12 on 2010-10-09
No problem, hope you enjoy your time! And remember there is no dumb question :)


You might want to mark this thread as solved, go to your first post and above it on the top right should be something that says thread tools. Click it and then click "Mark as Solved" it helps us out a lot when you do this :)
:P

---

### Post by lisati on 2010-10-09
Backtracking to repair/restore disks for a moment: my main desktop (currently in use as a server) and my current laptop didn't come with Windows repair or installation disks of any sort, but they did come with software that allowed me to create a set.

---

### Post by Tawrtoise on 2010-10-09
> **RJ12 said:**
> No problem, hope you enjoy your time! And remember there is no dumb question :)


You might want to mark this thread as solved, go to your first post and above it on the top right should be something that says thread tools. Click it and then click "Mark as Solved" it helps us out a lot when you do this :)
:P

Thanks I wasn't sure if a mod had to do it or not.

---

### Post by corcomp84 on 2010-10-11
> **jtarin said:**
> You can do [Yahoo messenger]("http://in.docs.yahoo.com/messenger/download/unix.html") but its not the optimal version you see for Windows.I've installed this on more Linux distros than you can shake a messenger at.You might have to soft-link to new version numbers for libs in some cases.

yea messenger works but the screen sharing didn't last time i tried.. and the program was a little glitchy.

---

