---
title: "Help help help please read you might know something"
date: 2010-05-18
forum: New to Ubuntu
---

### Post by anemodourios on 2010-05-18
Hi everyone. I Have a sony vaio vgn-fw520f i got it at january 2010.
The os of my computer was windows 7 home premium.
Everything was fine until my computer was not responding and when i restarted it i got a black screen and white letters giving my two options: 
Start startup repair (recomended) .....[smth like that] and
Start windows normally. from that time i never got into windows again.
Neither of the two options solves the problem.
I went to vaio recovery center witch had 4 options
1) diagnosis (smth) witch starts and never completes
2 and 3 says it will recover from a point but my files will be erased. (i havent made a point.)
(THE POINT IS THAT I WANT TO SAVE MY FILES.)
4th option is rescue data but i am afraid i might not rescue all my files. I Have tried several things but nothing works. At this point if someone has a qlue what might be the problem please help my. Allthough i started my computer using the ubuntu 10.04 os from a live cd with the hope i can access my hard disc and save my files from there. Then format my computer and have my files saved. The problem now is that i cannot access the hard disc. It says something about mounting it first. I tried the ntfs comfiguration tool but it didnt work.
I AM VERY TIRED OF THE STORY I CANT STATD IT NO MORE I AM FED UP AND DONT KNOW WHAT TO DO. I HAVE READ SEVERAL FORMUS ASKED SEVERAL PEOPLE ABOUT IT AND FINALY I DESIDED TO POST MY OWN THREAD. SOMEBODY PLEASE HELP MY I WILL REALLY APRICIATE IT. PLEASE HELP PLEASE!!!!!!!!!!!!! 
P.S.  if someone knows the problem some advise for preventing this from happening again will be much more that fine.
THANK YOU

---

### Post by utnubuuser on 2010-05-18
Have you tried using gparted from the liveCD to see what it comes up with about the windows partitions?

---

### Post by pcura on 2010-05-18
i would go with utnubuuser, using live CD will see all your files even your windows partition but the only problem you might encounter is it might open the windows partition though because its running only on live CD.

another option would be is get a sata/ide adapter cable and connect it to another computer you MIGHT be able to retrieve your files that way (it would treat it as an external cable)

---

### Post by theozzlives on 2010-05-18
I would boot with an Ubuntu Live CD and access your NTFS partition. Save your files to removable media, and re-install with what OS you want (hopefully Ubuntu).

---

### Post by anemodourios on 2010-05-18
[utnubuuser]("http://ubuntuforums.org/member.php?u=370166") : i am teribly sorry but i have no idea what you are talking about
[pcura]("http://ubuntuforums.org/member.php?u=1027265") : same as above. for the other option how exactlly do i do that i dont understand

sorry if i am making you tired but i dont know.


[theozzlives]("http://ubuntuforums.org/member.php?u=420456") : i am booting from ubundu live cd but how do i access the ntfs partition? as you say...

---

### Post by bigsmitty64 on 2010-05-18
> "i started my computer using the ubuntu 10.04 os from a live cd. The problem now is that i cannot  access the hard disc. It says something about mounting it first."

Right click the drive icon and choose "mount". Mounting it, lets you have access to the drive.

---

### Post by anemodourios on 2010-05-18
[bigsmitty64]("http://ubuntuforums.org/member.php?u=966097") : my friend i have allready done that before i posted the thread and i got this  message:

[U]Unable to mount location
Error mounting: mount exited with exit code 13: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Failed to read NTFS $Bitmap: Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.
[/U]

---

### Post by bigsmitty64 on 2010-05-18
> **anemodourios said:**
> [utnubuuser]("http://ubuntuforums.org/member.php?u=370166") : i am teribly sorry but i have no idea what you are talking about
.

gParted is a partitioning software on the live cd.

---

### Post by anemodourios on 2010-05-18
what do i do with it?

---

### Post by bigsmitty64 on 2010-05-18
When you open gparted it will show you all the drives/partitions on your system, in the upper right hand corner there is a drop down list,  find the one that says ntfs, and report back here with the info it gives you about that drive. Maybe with a screenshot would be cool. There are enough people in here that this will get fixed, but be patient. I may (more than likely :)  )  not be the one who can help you,but I'll try to get you started in the right direction.

---

### Post by anemodourios on 2010-05-18
there is a little problem at the moment i am accessing to the net by using the ubuntu os from a live cd.
how do i use gParted?

---

### Post by Tholley on 2010-05-18
> **anemodourios said:**
>  
_Unable to mount location_
_Error mounting: mount exited with exit code 13: ntfs_attr_pread_i: ntfs_pread failed: Input/output error_
_Failed to read NTFS $Bitmap: Input/output error_
_NTFS is either inconsistent, or there is a hardware fault, or it's a_
_SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows_
_then reboot into Windows twice. The usage of the /f parameter is very_
_important! If the device is a SoftRAID/FakeRAID then first activate_
_it and mount a different device under the /dev/mapper/ directory, (e.g._
_/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation_
_for more details._

 
Sounds like to me "possibly" the Hard Drive may have taken a dump, gone kaput, said adiós, etc...:(

---

### Post by anemodourios on 2010-05-18
can i save my files ?
is there a hope?
how can it be like the way you said i have had it for only 3 months its brand new..

---

### Post by Tholley on 2010-05-18
> **anemodourios said:**
> can i save my files ?
is there a hope?
how can it be like the way you said i have had it for only 3 months its brand new..
 
If you have only had it for 3 months, I would think the HDD would still be under warranty.
 
I could be wrong, but one way to find out, whomever the manufacturer of the hardrive is, (Seagate, Western Digital, etc...) you can go to their website (on a diff computer), download and burn a HDD Diagnostic CD. I think it should be bootable, like Live CD, and you cab run it to test your HDD.
 
If it is bad... options to save your data could be limited.

---

### Post by Tholley on 2010-05-18
also, when you first bought the computer, it probably asked you if you wanted to make Recovery Discs, hopefully you did, and then you could access a command prompt, and run chkdsk.
 
If you can get to a prompt, run this...
 
CHKDSK C: /F /R
 
Assuming you Hard Drive is your C drive, if not, change the C to whatever drive letter it should be.

---

### Post by oldefoxx on 2010-05-18
gparted (short for gnome partition editor) comes enabled on the LiveCD. To use it, you have either of two choices:  The command line mode (use Applications/Terminal to enter this mode) and enter the following:

sudo -s
gparted

Otherwise, use System/Administrative to find either Partition Editor or GParted.  It checks your hard drives and partitions, then shows you what it sees on the first drive.  Other drives can then be designated by going to the upper right corner and scrolling through the list.

If you want gparted to be part of your install, just do the following later after the install is finished:

$ sudo -s
# apt-get install gparted

You can do quite a bit with gparted, but as to the integrity of the drive or partition, you need to use other tools from the command line.  Each file system (fs) pretty much involves its own set.  For FAT and NTFS partitions, you are pretty much directed to use CHKDSK, which is a DOS or Windows tool.  It's not perfect, but it goes further than any other tool that I know of.  If it seems to lock in a cycle of fixing or removing the same index entry, just let it go.  At some point it will finish on its own.

If offered a chance to create a new Partition Table, beware.  This is a total wipeout of the whole drive in question.  It can be necessary and useful, but that is all part of what it does.

Once done with gparted, and we are talking about the LiveCD approach here,
you want to see if Ubumtu will go the distance for you.  This means mounting and accessing each partition.  There are three approaches to doing this.  With the command line method, we can use a command like mount -t ntfs-3g /dev/sda1 /media/a1.  This would work, except we need to first create an a1 folder in /media.  To do that, we just use this command first:  mkdir /media/a1, then the mount command.

Another way is to just go under Places and check for drives and partitions either under /Computer or /Removable media, or which are listed there individually.  If you can mount it by clicking on it, then you are generally good to go.  If Ubuntu can read it, it will open a window and show you folders and files as identified from the base or root of that drive or partition.

A third way can be useful if you want this to repeat each time you start up the machine, and that would be to make some additional entries into /etc/fstab so that the mount operation is automatic on bootup.  That would be more in keeping with follow up work after an actual install.  An entry there might look like this:

/dev/sda1     /media/a1     ntfs-3g   defaults,rw,exec,user  0    0

Of course, being an NTFS volume and currently running under Ubuntu, you could leave out the esec, since windows executive files don't run under Linux.  Here again, you need to make sure there is a /media/a1 folder or this instruction will fail to work when executed.

In general, if you make changes to /etc/fstab that involve the mountin of drives or images, you do not have to reboot to see them go into action.  Just use these two commands instead:

umount -a     # unmount all drives specified in /etc/fstab (note dropped n)
mount -a      # now try to mount all drives specified in /etc/fstab

You likely will find your NTFS partition in an error state.  To fix it, you really only have CHKDSK.  Beyond that, it would take some special repair software that you can hope to find somewhere online.

That's pretty much all I know to pass on to you.

---

### Post by stormchaser2063 on 2010-05-18
I hate to be the bearer of bad news.... it kinda sounds like your hard drive died. just because it is only 3 months old, that doesnt mean it was any good when it was made... ive seen plenty pf componets fail within even a day when they are new. depending on where you got it from maybe they will fix it or replace the unit

---

### Post by anewguy on 2010-05-18
+1 on the bad drive, and +1 on trying the diagnostic disk on it.  I would bet it will fail.  File recovery options?  Probably none.  You did back up your important data every once in a while, right? (he says grinning not at you, but at the idea that a LOT of us have gotten caught without a backup when we needed it!).

Dave ;)

---

### Post by mkvnmtr on 2010-05-18
It sounds like you need to make use of the warranty that came with your computer. If you keep messing with it without the knowledge of what you are doing you will lose what ever warranty it has,

---

### Post by daimaru on 2010-05-18
> **anewguy said:**
> +1 on the bad drive, and +1 on trying the diagnostic disk on it.  I would bet it will fail.  File recovery options?  Probably none.  You did back up your important data every once in a while, right? (he says grinning not at you, but at the idea that a LOT of us have gotten caught without a backup when we needed it!).

Dave ;)
a bad shutdown of windows (crash, unclean shutdown) normally prevents ubuntu from mounting the ntfs drive. you can only mount it after successfully shutting down windows again. ( had that problem several times ) Since you can't do that you will have to use the ntfs tools, "ntfs-fix" or something like that to clean up your drive again and maybe then you will be able to boot again. Sorry not running ubuntu right now (windowzing it) but don't wipe your hardrive yet. Try the ntfs fix thing first.

Is your drive at least recognize somewhere , as in /dev/sda1 ? if so you should make an image of it to an external usb drive using the dd command, ```
sudo dd /dev/sda1
```at least then you could maybe rescue some data using forensic tools such as test-disk,photorec, scalpel etc. --> check this [link ]("http://lifehacker.com/5525534/recover-data-like-a-forensics-expert-using-an-ubuntu-live-cd")(didn't read much of it, but it looks promising) if not i have a simpler tutorials, but i don't know the bookmark by heart, so i will have to check on my ubuntu system when i reboot. 

i'm not sure if your drive is even shown in the /dev directory (which, if not, would probably mean that it is actually broken), but if it is then you should be able to recover data from it.

---

### Post by RedRat on 2010-05-18
I would suggest that you contact Sony or the dealer that sold you the computer before attempting to run Linux software that you are uncomfortable using or if you feel you don't know how. This computer ought to be under warranty. If you are not careful running or playing with gpartd you run the risk of losing everything permanently.

---

### Post by lkraemer on 2010-05-19
Check your PM (Private Mail).

lk

---

### Post by stormchaser2063 on 2010-05-19
if it is still under warranty which it should be... maybe you can call the sony tech support number and see what they say about it being unresponsive and cant find any operating system. I still think the hard drive took a dive.

---

### Post by 3rdalbum on 2010-05-19
The message "Input/Output Error" is very bad. It means that one or more of the drives that you are dealing with has unreadable or unwritable parts.

Since you're just trying to mount the hard disk, the message is definitely referring to your hard disk. Hard disks will usually have spare blocks, and if they encounter a spot that is starting to go bad, they'll automatically copy the data to one of the spare blocks, and flag the bad spot. When you run out of spare blocks (that is, the number of flagged blocks exceeds the number of original spare blocks) you'll start getting Input/Output errors, and the disk becomes a liability.

This shouldn't happen for years, but maybe your disk was a dud to begin with. And you were especially unlucky - one of the bad blocks is right where the filesystem is, which has prevented both Windows and Linux from being able to read the disk.

The disk is still under warranty, so contact Sony as soon as you can and get it in for repair. If you had some command-line knowledge you might have been able to use some little-known tools in the "ntfsprogs" package to possibly get access to some non-binary files on your disk (like the text from a word processor document), but it's not easy enough for me to walk you through it, and I've never done it before anyway.

---

