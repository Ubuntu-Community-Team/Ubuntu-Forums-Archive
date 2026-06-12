---
title: "Let the hair pulling begin..."
date: 2009-04-23
forum: New to Ubuntu
---

### Post by dckrooney on 2009-04-23
I originally started with a Toshiba Satellite A305 with vista(64) installed.

I then tried to install ubuntu to dual boot. After a little trouble getting the installer to stop freezing at the partition editing phase, I managed to get it up and running.


I then logged out to try and boot into vista, but there was no menu to select an OS... just loaded straight into ubuntu.

So I then followed a few threads here, and eventually i was able to at least SEE a menu listing vista as an option.

But as soon as i would select it, it would just re-load the menu.

To make a long story short, I finally tried just formatting the damn drive and re-installing vista using my OEM recovery discs.

I made it all the way through the re-install, only to get a blue screen error that said "Device driver caught attempting to corrupt..." I was then told that I could not complete installation.

At this point, I died a little on the inside.

I went through this 3 more times, with a few disk checks/recoveries thrown in.

Still stuck at the same spot.

Any of you resident geniuses have some clues as to what the hell is going on? :)

---

### Post by RetchingRabbit on 2009-04-23
just to be clear, it sounds like you are trying to install vista at this point, and with the OEM discs. If that's the case, then you may need to seek support from them just because the possibilities are almost infinite as to what sort of discs you have...
A word of advice here: most OEM support staff know nothing about linux. Just start your story with "I'm trying to reinstall vista..." and you will probably have better luck than explaining all about your adventures with Ubu.

---

### Post by aloshbennett on 2009-04-23
When my friends call up telling that they've been thinking about installing ubuntu, I say 'Go ahead. You can do it yourself. Just call me when it comes to the disk partitioning.'

How did you do your partitoning?

If your vista installation has screwed up (looks like it has), the way out is clean up all the partitioning, and install vista once more from the recovery disk.

---

### Post by dckrooney on 2009-04-23
Well, I've managed to get Ubuntu working. That was actually easy.

Now I'm trying to get Vista back again. I hate it SO much, but I need to have access to it.

Originally (prior to formats/recovery attempts) I partitioned everything manually, which is probably where I screwed everything up. I went into vista, shrank the NTFS partition, loaded the Ubuntu installer, and installed it to the unallocated free space (/ with ext3 and a 1GB swap).

And in answer to the previous question, I did finally call tech support... They're answer was send it to us and we'll have it back in two weeks. Hopefully.

Also, I burned a copy of the vista install/startup utilities disc and have run the various scan/repair functions. Everything comes up clean.

---

### Post by HazzaJ on 2009-04-23
How did you fix it and stop it freezing at the partitioning stage. Mine always gets stuck at 5%.

---

### Post by tripolitan on 2009-04-23
Chances are, your MBR (master boot record) needs to be cleared.
You need to be at the DOS command line (use DOS diskette or Win2000/XP CD to reach the c:\ prompt), at the prompt, type "fdisk /mbr" then reboot. Your MBR will be cleared and you'll be able to re-install Vista. Don't bother with the store's tech support, they'll probably tell you the HD is shot...

Clearing MBR means that you will have to re-install Vista, then re-install Ubuntu. (partition your HD before you install anything)

---

### Post by tripolitan on 2009-04-23
now that you have a clean system, take some time to think about partition sizes so you wont have to shrink/expand partitions. Remember to always defragment windows BEFORE partitioning and installing Ubuntu. I would even suggest partitioning your drive before installing Vista. Always install Windows first, then Linux.

---

### Post by nml on 2009-04-23
> Always install Windows first, then Linux.

Since this is the 'Absolute Beginner's' area, could tell me why this is so (or maybe point me to a source on the importance of installation order)?

thanks,

Mick
(an absolute beginner, but I did just get a Lenovo T42 multibooted---starting with Ubuntu 8.10, then XPpro and subsuquently added PuppyLinux and the latest version of OpenSusie)

---

### Post by lisati on 2009-04-23
> **nml said:**
> Since this is the 'Absolute Beginner's' area, could tell me why this is so (or maybe point me to a source on the importance of installation order)?

thanks,

Mick
(an absolute beginner, but I did just get a Lenovo T42 multibooted---starting with Ubuntu 8.10, then XPpro and subsuquently added PuppyLinux and the latest version of OpenSusie)

One difference between the installer that comes with Windows and that which comes with Ubuntu is that the Windows installer assumes that Windows will be the only OS on the system and doesn't take into account any other OS that might be on your system when setting up the boot loader.

On the other other hand, Ubuntu's installer normally recognizes the presence of another OS (such as Windows) and adjusts what it puts on your system accordingly.

---

### Post by D1ZZ4ZZT3R on 2009-04-23
1 GB swap? that seems like an awful lot to me. excessive, i mean.

also, yeah, windows first, then. linux. if ubuntu is still working on your comp and you're trying to get vista back on, that might be your problem, there. i think you'll have to start from scratch - install vista, reformatting the whole drive, then, install ubuntu. i'm not an expert but, i haven't seen that suggested yet and, that's my understanding of it.

---

### Post by HittingSmoke on 2009-04-23
> **tripolitan said:**
> Chances are, your MBR (master boot record) needs to be cleared.
You need to be at the DOS command line (use DOS diskette or Win2000/XP CD to reach the c:\ prompt), at the prompt, type "fdisk /mbr" then reboot. Your MBR will be cleared and you'll be able to re-install Vista. Don't bother with the store's tech support, they'll probably tell you the HD is shot...

Clearing MBR means that you will have to re-install Vista, then re-install Ubuntu. (partition your HD before you install anything)

Unfortunately you can't do this with any recovery disk I've ever come across. You might have to get your hands on a retail XP disk from a friend.

Also, as of XP and later the command is "fixmbr". If you're booting to the XP recovery console use this command instead.

---

### Post by nml on 2009-04-23
> On the other other hand, Ubuntu's installer normally recognizes the presence of another OS (such as Windows) and adjusts what it puts on your system accordingly.

Can't disagree and I had to restore the Ubuntu bootloader after the XPpro install, but once you realized (found simple instructions) on how to do that, it wasn't a problem...

When I first started trying to multiboot that laptop, I ran into real problems when I adjusted the size of the Windows partition (post windows install)....now maybe I didn't do it right (or the sun was in my eyes, gravity was all wrong or something else), but my take away was that:  

You really need to decide your partition sizes first, THEN do the install(s).........I don't like messing with the Windows partion...it's flakey.  

GParted (or the Ubuntu live cd) is a great program and is easy to use, but I think it's much easier to totally partition first and install later...

Mick

---

### Post by starcannon on 2009-04-23
Heres a couple of guides that may be of use once you figure out the vista install issue:

[Dual Boot Vista and Ubuntu, Vista installed first.]("http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm")

and

[Dual Boot Vista and Ubuntu, Ubuntu installed first.]("http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm")

GL and have fun.

---

### Post by raymondh on 2009-04-23
> **HittingSmoke said:**
>  Also, as of XP and later the command is "fixmbr". If you're booting to the XP recovery console use this command instead.

bootrec.exe/FixMbr

HittingSmoke's right, you'll need a retail disc.

Gparted is a great partitioning software.  Although, I have not had any problems with win's disk management.

If OP decides to re-do:

-Re-install Vista as the sole OS (that'll also clean up/reformat the whole HD)
-Defrag
-Decide if he wants a guided install or do a manual
--If guided, he can adjust the partition sizes accordingly by dragging the bar
--If manual, he can dicate all partitions (primary and logical) as well as have separate home, var, etc partitions (if so desired) and choose the file system as well.  May sound complicated now but will save tons of "hair" later on
-Check MD5 of Ubuntu CD and/or check CD for defects
-Install Ubuntu

Re: install disc hanging on partioning .... I've experienced that problem until someone in the forum advised me to re-burn AT SPEED AS SLOW AS POSSIBLE (4x, i did).  Have not had problems since. If you do re-burn, try at a slow speed as possible.  I don't know why burning speed matters....I just classify this as "working-witchcraft" :)

Best of luck

---

### Post by ttilberg on 2009-04-23
I recently had some problems trying to fix my dad's computer after he went all willie nillie with his installations. A few people have commented on the order of installation because windows will hijack GRUB. Just wanted to share this link that I found extraordinarily helpful. This is likely the process NML was mentioning above:

What to do when a Windows install hijacks the MBR? 
[http://remmirath-en.blogspot.com/2007/10/linux-how-to-reset-grub-mbr.html](http://remmirath-en.blogspot.com/2007/10/linux-how-to-reset-grub-mbr.html)

This will reconfigure GRUB to be the OS selection tool at boot. It was incredibly easy to use as well. A few commands that took 0 time to process, it felt sort of like "That's it?" --- but that's it :D

---

### Post by dckrooney on 2009-04-23
> **HazzaJ said:**
> How did you fix it and stop it freezing at the partitioning stage. Mine always gets stuck at 5%.

I'm not sure I had the same problem as you... my gparted would display the "Resizing Partition" Dialogue box, but would never even start. Moreover,, it actually froze the machine.

My totally amateur speculation is that Vista wasn't happy with Ubuntu adjusting it's partition size at all. After I booted into windows, used MS's partition editor to shrink the vista partition, I then manually installed ubuntu to the free space. This didn't freeze.

>  
also, yeah, windows first, then. linux. if ubuntu is still working on your comp and you're trying to get vista back on, that might be your problem, there. i think you'll have to start from scratch - install vista, reformatting the whole drive, then, install ubuntu. i'm not an expert but, i haven't seen that suggested yet and, that's my understanding of it. 

I've tried this (repeatedly :( ), but I'm almosst positive something in the original ubuntu install screwed up the windows boot sequence.

Right now I'm going to try a variation of the fixmbr suggestions, as outlined by this link I found. Any input?

[http://www.planetmy.com/blog/how-to-fixmbr-using-windows-vista-bootable-disk/](http://www.planetmy.com/blog/how-to-fixmbr-using-windows-vista-bootable-disk/)

---

### Post by Saint_ on 2009-04-23
Personally that HowTo looks like it might be a solid way to fix it. Now, i saw earlier that you mentioned needing vista, so my question is have you tried windows 7? it's essentially vista...only not shitty. It's much more efficient, runs and boots a hell of a lot faster than vista and is more stable. So thats a route you could take, but if you can't/don't want to, then no harm done. But yes, that HowTo should do the trick, because after formatting/repairing XP/Vista countless times, that's always been how I've done it.

---

### Post by dckrooney on 2009-04-23
Hmm haven't thought about windows 7... i might upgrade at some point.

I just have a problem actually giving MS my money. The only real reason I need vista is for compatibility with everyone else... :(

Have they released the windows 7 release candidate yet?

---

### Post by Saint_ on 2009-04-23
Windows 7 is still in the Beta stage, so it's a free download at [http://microsoft.com](http://microsoft.com). The only rub there is the beta expires august 1st or 11th or some garbage like that. Yeah I can't say I blame you there man, they release a shitty OS and instead of patching it or updating it, they just release and entirely new one. Capitalism at it's finest. 

Edit: Though, maybe microsoft quit hosting the beta, in which case I'm sure you can find a windows 7 torrent with ease.

But, have you tried that HowTo yet?

---

### Post by crjackson on 2009-04-23
Here [http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/]("http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/")

Go to this page and download the recovery disc of your choice (32bit/64bit) and fix your mbr.

If I were in your shoes (and i have been).  I would use the Ubuntu LiveCD. Go to System>Administration>Partition Editor.

Delete ALL partitions and don't format. Then use your Vista Recovery Disc and restore your Vista install.

Once that's working, use the Ubuntu LiveCD again and go to the partition editor to resize the Vista partition to the desired size.

Once that's done, Install Ubuntu and let it use all UNALOCATED space on that drive as it sees fit.

When it's all done you should have a good dual boot system.

The first time you run Vista however, it will see an unclean partition / size mismatch. It will run it's own disk utility to clean up the mismatch and you should have no more problems.

---

### Post by dckrooney on 2009-04-23
YES!!!

OK so the how-to link I referenced earlier worked out. Vista installed successfully, and now I'm going back to reinstall ubuntu.

Thanks so much to everyone for the help!

---

### Post by D1ZZ4ZZT3R on 2009-04-23
yay!

---

### Post by tripolitan on 2009-04-24
> **raymondhenson said:**
> Re: install disc hanging on partioning ....

Without failure, in gparted, everytime I un-ticked (unselected) the box that references (rounding off cylinders) Ubuntu hung on install. So, I learned to keep the box ticked!

---

