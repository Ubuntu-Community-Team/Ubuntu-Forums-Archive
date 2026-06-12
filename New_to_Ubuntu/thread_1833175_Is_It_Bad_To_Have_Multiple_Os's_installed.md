---
title: "Is It Bad To Have Multiple Os's installed?"
date: 2011-08-25
forum: New to Ubuntu
---

### Post by PirateKarma on 2011-08-25
So I just got a new laptop, and I want to be really really careful with this one. So I was wondering if there was any flaws to having two os's installed? I need Microsoft Office, so I need to keep Windows installed. Plus I might play some games here, and there. The thing is I really want to install Ubuntu onto my computer, and a friend told me that if I install both my computer is going to lagg, and the registry is going to be really fragmented. And the hard drive gets more stressed with two os's so it burns out more quickly. Are these things true? I really cannot afford to loose this laptop, so I'm really worried.

---

### Post by pqwoerituytrueiwoq on 2011-08-25
dual boot will not cause issues unless widows does not have the needed space for all it's stuff (eg paging file)
if it was running in side a virtual box it may lag windows but not as a dual boot

---

### Post by Basher101 on 2011-08-25
Well you would void your warranty if you install linux on it. But i would not worry that much, since the "normal" warranty is waaay to short for you to care. Unless you play Football with your laptop outside... (not a video game)

---

### Post by Matt__ on 2011-08-25
respectfully: your friend is talking out of his or her A**

of course try ubuntu from a live cd/usb to see how it likes your hardware first.
then follow one of the many install guides you will find online.

also if you dont have a windows install disk make a repair disk for windows NOW before you start doing anything, for your own peace of mind.



//edit: bah...slow to type and beaten to post again lol

---

### Post by PirateKarma on 2011-08-25
I have made a recovery cd, however I remember when you install Ubuntu it gives you the option to install on the entire hard drive. Which means it would erase the recovery partition. Do the recovery cd's need the recovery partition to work? Also does installing Ubuntu really void my free 1 year warranty? I kinda would like to keep that.

---

### Post by Basher101 on 2011-08-25
What for? unless you toss your laptop around (which i doubt you do) nothing will happen. Ubuntu is much more resource efficient, thus using only 400mb RAM on system idle (thats in my case, a fresh install has less probably) and this should make your system live longer. I do not see why you would need a warranty if you care for your laptop

If you delete windows a mere recovery CD wont cut it. You will need the partition to restore it. I use my whole disk and have a system image from windows and linux on an external hard disk, so when my internal drive gets fried i got my backups.

---

### Post by PirateKarma on 2011-08-25
Good Point, I guess the warranty is useless, but I mean I kinda still want to keep the recovery cd partition, and I read a bunch of guides on how to partition a drive, but for some reason I couldn't understand them :(. I wanted to learn how to partition so that I could halve the Windows Partition, and use the other half to install Linux.

---

### Post by mikewhatever on 2011-08-25
The recovery CDs usually don't need the recovery partition. What your friend had told you is absolute nonsense. Ubuntu will run fast if the hardware is compatible, and it doesn't use the registry.
As for the warranty, you don't have to tell anyone the Ubuntu is installed.

> **PirateKarma said:**
> Good Point, I guess the warranty is useless, but I mean I kinda still want to keep the recovery cd partition, and I read a bunch of guides on how to partition a drive, but for some reason I couldn't understand them :(. I wanted to learn how to partition so that I could halve the Windows Partition, and use the other half to install Linux.

You can keep both the Windows and the recovery partition, depending on the current layout. Can you provide some info on that.
Learning usually takes some time. If you don't understand something in a guide, ask.

---

### Post by Basher101 on 2011-08-25
argh im currently on ubuntu and not windows 7 to show you in screenshots how  you can free up space for ubuntu...and i cant switch right now as i do not want to interrupt my downloads :/

---

### Post by PirateKarma on 2011-08-25
Thank You so much for replying. So right now I have a Windows Partition which contains 581 gb of space, and a Recovery Partition that that uses 13.8 gb of space. So I figured I would half the 581 into two 290 gb partitions one for Windows, and one for Ubuntu. However I don't understand the tho concept of swap,logic,root, and all the other partition obptions. I don't know how much to give each one or, what they mean.

Edit: I know how to half the Windows Partition, what I meant is how do I do the Ubuntu Partitioning at the install screen. Like the root partition, and logic, and all the other ones I need. Like I said I should have 290 gb to mess around with if I half the WIndows Partition. Thank for all the help guys!

---

### Post by oldfred on 2011-08-25
There is vendor recovery partition which is just an image of your hard drive as purchased. If you copy it to DVDs it should be multiple DVDs. You may never use this unless you have to totally recover system or want to eventually sell it and have it back to like new without any of your data.

The windows repair CD is just one CD for repairing your windows if you have problems and cannot boot into windows repair mode directly. Best to have this first.

Make your own Windows recoveryCD/repair:
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

Windows 7 repair USB
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)


If you are a belt & suspenders type you may also want a full backup of your system:

The vendor recovery DVDs are just an image of your drive as purchased. If you have housecleaned a lot of cruft normally included, run many updates with many reboots, and added software you may want a full back up.
Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=1626990](http://ubuntuforums.org/showthread.php?t=1626990)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

Good advice on how to handle all four primary partitions used. - srs5694
[http://ubuntuforums.org/showthread.php?t=1686440](http://ubuntuforums.org/showthread.php?t=1686440)
Besure to create recovery DVD(s) first. And a Windows repair CD.
HP tools partition discussion - similar for other vendor partitions:
[http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360](http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360)
Shrinking a Windows 7 partition is best done in Windows. But do not create new partitions with Windows.
[http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/](http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/)

---

### Post by PirateKarma on 2011-08-25
Okay that Link of your's helped a lot, but I still have a question. It says the Swap partition should be twice of what your memory partition is. Idk if i'm just slow, but I don't understand What that means. Like I know it has to be twice my memory partition, but idk how much my memory partition is. I have 290 gb to play with as I mentioned in my last post.

EDIT: When they say the swap partition is twice your memory, do they mean Ram? I have 4b of Ram, so does that mean that the swap partition will be 8gb?

---

### Post by oldfred on 2011-08-25
The old rule was swap twice RAM, but that was when you had only 256KB or 512KB. Now with GB of RAM you rarely use swap at all (and do not want to at it is slow compared to RAM). I usually suggest 2GB unless you want to hibernate then it needs to be equal to RAM or 4GiB not GB to have room for all of RAM. 

But if dual booting you do have to be careful hibernating. If for example have a file open, then reboot and edit it in the other system you have just damaged the hibernation as the file has changed.

[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

---

### Post by srs5694 on 2011-08-25
> **PirateKarma said:**
> So I just got a new laptop, and I want to be really really careful with this one. So I was wondering if there was any flaws to having two os's installed? I need Microsoft Office, so I need to keep Windows installed. Plus I might play some games here, and there.

Most versions of MS Office run pretty well under WINE, which is Linux software for running Windows applications. Some games also run well under WINE, although others don't, so that's more of a crap shoot.

> The thing is I really want to install Ubuntu onto my computer, and a friend told me that if I install both my computer is going to lagg,Unlikely. If anything, if you partition the disk correctly, there may be a (probably unnoticeable, but measurable) performance improvement because you'll reduce hard disk seek times within each OS. Other factors that could influence performance, like memory access or CPU load, are irrelevant, since in a dual-boot configuration, only one OS at a time has access to memory and CPU, so there can be no drain on these resources in a dual-boot configuration.

Running one OS in a virtual environment (using VMWare, VirtualBox, QEMU, or similar software) is another matter; the OS running inside the virtual machine will run more slowly and will consume resources that might otherwise be used by the other OS, so the host OS's performance may be degraded, too.

> and the registry is going to be really fragmented.Linux won't touch the Windows Registry, so this is complete nonsense.

> And the hard drive gets more stressed with two os's so it burns out more quickly.If you use the computer more because you've got two OSes on it, there might be some truth to this claim. Likewise if you shut down and reboot more often (which puts stress on the disk because of the power-off/power-on cycles, much like switching off a light bulb and then back on again). If you use the computer for roughly the same amount of time and don't radically alter your shutdown/reboot practices, though, it won't make any difference.

[quote=Basher101]Well you would void your warranty if you install linux on it.[/quote]

Please check your warranty before assuming this claim is true. I've seen similar claims in the past, but I don't recall anybody actually posting information on a warranty with terms that void the warranty if Linux is installed. Even if such terms exist, they might be illegal, although that depends on where you are who interprets the law.

That said, it's entirely possible that some clueless or greedy repair shop manager would *try* to deny warranty service if Linux is installed. That could turn into a hassle -- but there's always a risk of being "taken" in this way, for whatever reason the person would like to dream up.

[quote=Matt__]also if you dont have a windows install disk make a repair disk for  windows NOW before you start doing anything, for your own peace of mind.[/quote]

Most computers come with a utility you can run to do this. Once you've got the backup disks, they can be used instead of the recovery partition on your hard disk.

Another option is to download a "generic" Windows installation disc, or use one if you have a retail copy of the same version of Windows for another computer. [This site]("http://www.mydigitallife.info/download-windows-7-iso-official-32-bit-and-64-bit-direct-download-links/") has links for this purpose, which it claims are Microsoft-approved. Be sure to get the version you've got installed on your laptop. If you need to re-install Windows in the future, you'll need your license number, which probably appears on a sticker on the bottom of the laptop. This may be a better option than using a recovery disc set provided by the manufacturer because recovery disc sets often wipe everything on the hard disk, including your Linux installation, in order to restore Windows. A "generic" disc, by contrast, can install alongside Linux, although it may overwrite GRUB and therefore render Linux temporarily unbootable until you restore GRUB.

[quote=PirateKarma]Okay that Link of your's helped a lot, but I still have a question. It  says the Swap partition should be twice of what your memory partition  is. Idk if i'm just slow, but I don't understand What that means. Like I  know it has to be twice my memory partition, but idk how much my memory  partition is. I have 290 gb to play with as I mentioned in my last  post.[/quote]

"Memory" normally means random access memory (RAM), which is volatile memory held in chips on your computer's motherboard. Computers run programs in RAM and store currently-loaded documents in RAM while you're working on them. When you turn off a computer, the contents of RAM disappears. Most modern computers have 2-8 GiB of RAM. RAM is conceptually distinct from disk space and disk partitions, and you can't tell how much RAM you've got by examining your disk drive.

Disk drives are slower than RAM but larger. Most modern hard disks are 300 GB to 3 TB (3,000 GB) in size -- so normally hundreds of times the size of the RAM in the same computer. Programs and data files are stored on hard disks for long-term storage. When you turn off a computer, the data on the hard disk remains intact. When you boot, the computer reads the hard disk to load basic OS programs into RAM to be executed.

Swap space joins the two: It's disk space that's used as a sort of adjunct to RAM. If you run enough programs, or programs that are memory-hungry enough, to run out of RAM, the OS stores some of the data it normally keeps in RAM on the hard disk. This keeps programs from shutting down, but if more than a small amount of swap space is used, the system gets slower. Linux also uses swap space for its suspend-to-disk feature; when you use this feature, all the contents of RAM are stored to swap space, and when you power back up, the computer loads everything from swap space, which can be quicker than booting up normally, logging in, and re-launching all your programs.

In the past, the rule of thumb was to have 2x as much swap space as you've got RAM. Today, that's usually overkill; modern computers have enough RAM that you seldom need twice as much swap space as RAM. Having at least as much, though, enables you to use the suspend-to-disk feature, so I recommend setting your swap space to something over your RAM size -- perhaps 1.1x as much, just to be sure you don't run into rounding errors that mean you've actually got less than you think you do.

You can learn how much RAM you have by examining the specs for the computer printed on its box or by running various diagnostic utilities. In Linux, "free -m" does the job:

```
$ **free -m**
             total       used       free     shared    buffers     cached
Mem:          1938       1923         15          0          1       1426
-/+ buffers/cache:        494       1443
Swap:         3071        126       2945

```This shows, among other things, that the computer has 1938 MiB of RAM (the "total" column on the "Mem:" line). In fact, some memory is consumed in ways that don't show up here -- this computer actually has 2 GiB (2048 MiB) of RAM.

---

### Post by PirateKarma on 2011-08-25
Thanks for all the help guys! I'll try installing it tomorrow, and if it works out I'll let you guys know, and close the thread. I appreciate everyone's help.

---

### Post by mikewhatever on 2011-08-25
> **PirateKarma said:**
> Thank You so much for replying. So right now I have a Windows Partition which contains 581 gb of space, and a Recovery Partition that that uses 13.8 gb of space. So I figured I would half the 581 into two 290 gb partitions one for Windows, and one for Ubuntu. However I don't understand the tho concept of swap,logic,root, and all the other partition obptions. I don't know how much to give each one or, what they mean.

Edit: I know how to half the Windows Partition, what I meant is how do I do the Ubuntu Partitioning at the install screen. Like the root partition, and logic, and all the other ones I need. Like I said I should have 290 gb to mess around with if I half the WIndows Partition. Thank for all the help guys!

The thing is, if you really only have two partitions, Ubuntu will offer to do all the work for you, that is, resize the Windows partition and create it's own partitions, including swap.

---

### Post by PirateKarma on 2011-08-25
Yeah Thanks for that, but I needed to keep three partitions one was an important Hp one. Anyhow I managed to do it the other way, and it worked! Well almost the internet wont work, but I'll start a new post for that.

---

### Post by F.G. on 2011-08-25
hey, i just wanted to agree wholeheartedly with srs5694's massive post.
dual booting should not effect windows registry, or performance.  and i've never heard of a warranty that is voided by linux, that sounds very suspicious.

so, i've got a toshiba laptop with a recovery disk, it doesn't require a recovery partition at all.  i always thought that you either used one or the other to reinstall windows (although many computers come with both). I know that a lot of modern laptops you can 'recover' without any disk, just with the partition.

ps i just realised that i completely wiped my netbook's recovery partition and don't have any other recovery medium (so you probably shouldn't listen to me).  oh well, i hated windows7 'starter', anyway.

edit: actually i don't completely agree with srs5694's reference to 'read-only memory, (RAM)'... apart from that srs5694's post seems pretty comprehensive.

---

### Post by theozzlives on 2011-08-25
> **PirateKarma said:**
> Yeah Thanks for that, but I needed to keep three partitions one was an important Hp one. Anyhow I managed to do it the other way, and it worked! Well almost the internet wont work, but I'll start a new post for that.
Create an extended partition and create your logical ones after that. You want to use disk manager in Windows to resize drive c:\.

---

### Post by sbraz on 2011-08-25
> **PirateKarma said:**
> flaws to having two os's installed?
none. you could have like 30 installed with no consequences other than a bit of confusion while choosing which one to boot. :)

> a friend told me that if I install both my computer is going to lagg, and the registry is going to be really fragmented.
please, ask your friend to post an article here about this, explaining in detail how something like this might happen.
honestly, technically.

> And the hard drive gets more stressed with two os's so it burns out more quickly.
given the previous quote i assume it's based on personal beliefs instead of scientific methods but this is indeed partially true.

there is a package called laptop-mode-tools and possibly some other packages/settings applied when installing on a battery-equipped computer, which applies some powersaving oriented tweaks when the laptop is on battery. while it actually lowers the power consumption, the aggressive harddisk stanby policy (i think it's like 10 seconds timeout), makes constantly spindown/up your drive, which actually it's a big stress for both the brushless motor which has to go "full power" to accelerate the disk to its target rotation speed, and stresses the head's actuator motor too, due to park/unpark heads operations, unless the system is heavily customized to aggressively cache files for example during mp3 playback (aka load the whole audio file on ram then idle while it's playing) and rely on a ramdisk for every possible kind of temporary file to reduce disk usage to a minimum.
in my case, i've removed disk standby entirely.. i don't see the point in spinning down the disk: if i have to both leave my laptop idling with an open session and save battery i simply hit standby or hibernate according to the situation.

on the other hand, windows 2k and later versions keeps using the drive for unknown reasons while idling, so hard drive tearing is somewhat an issue for windows too.

windows vista is by far the king of unexplicable high disk usage when idle: it's so high that when a customers says "my computer doesn't feel right" or "windows doesn't boot" and there's vista installed i simply say "imho, your disk is faulty" and most of the times i'm right. :)

---

### Post by sbraz on 2011-08-25
> **F.G. said:**
> i've never heard of a warranty that is voided by linux, that sounds very suspicious.
i think that if you mess around with preinstalled partitions you lose your _software_ warranty. :(

---

### Post by Megaptera on 2011-08-26
Once you've got dual boot sorted you could try this!:lolflag:

How to install and boot 145 operating systems in a PC
[http://www.justlinux.com/forum/showthread.php?t=147959](http://www.justlinux.com/forum/showthread.php?t=147959)

The 145 systems are:-

3 Dos
5 Windows
137 Linux

---

### Post by srs5694 on 2011-08-26
> **F.G. said:**
> edit: actually i don't completely agree with srs5694's reference to 'read-only memory, (RAM)'... apart from that srs5694's post seems pretty comprehensive.

Oops... that's an embarrassing error! I've gone and corrected it in the original post....

---

