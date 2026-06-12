---
title: "Help me throw Microsoft Windows, OUT THE WINDOW!"
date: 2011-06-29
forum: New to Ubuntu
---

### Post by Prince_Peculiar on 2011-06-29
Hello,
   I'm fairly new at OS switches and coding, and, well, pretty much everything computer related (so please be slow and descriptive with me.) Today I installed the latest version of Ubuntu along side my default Windows 7 starter edition. Everything seems to be working beautifully - and I'm completely satisfied. So satisfied, that I no longer want to duel boot the two systems and would much rather ONLY run Ubuntu. If this is not an option (though I really, REALLY hope it is) I at least do not want the two partitioned evenly and I want to (quite obviously) give the Ubuntu portion more ram/room etc etc. Like I said, I'd much rather remove windows in a safe and easy manner, and would prefer not to do any extensive coding right off the bat. Any help would be GRAND! :)

---

### Post by e79 on 2011-06-29
Hi and welcome to Ubuntu Forums :)

If you are comfortable with Ubuntu only and you are sure you want to wipe Windows completely, here is the easiest/fastest ways :

1. Backup all your important files from Windows/Ubuntu (if any)
2. Download and burn the latest Ubuntu iso
2. Reinstall Ubuntu choosing the 'Erase and use the whole drive'

or

1. Backup all your important files from Windows/Ubuntu
2. Boot in Ubuntu
3. Install 'gparted' if not there already (sudo apt-get install gparted)
4. Delete yor windows partition and format it as 'ext4'
5. resize your current Ubuntu partition to take the whole drive.

Hope this helps

---

### Post by Ozymandias_117 on 2011-06-29
Two things to note from the previous poster's comments. If going with method two, after deleting the Windows Partition, there is no need to format it as EXT4 before resizing the Ubuntu Partition, and you will have to boot to a LiveCD to be able to resize the Partition. (Ext4 does not support online resizing) - Also, please note that method two would probably take a lot longer to complete.

---

### Post by dFlyer on 2011-06-29
Cloning your windows is better than a simple back, should you change you mind.

---

### Post by e79 on 2011-06-29
> **Ozymandias_117 said:**
> Two things to note from the previous poster's comments. If going with method two, after deleting the Windows Partition, there is no need to format it as EXT4 before resizing the Ubuntu Partition, and you will have to boot to a LiveCD to be able to resize the Partition. (Ext4 does not support online resizing) - Also, please note that method two would probably take a lot longer to complete.

Thanks for correcting me :)

---

### Post by Prince_Peculiar on 2011-06-29
Hey folks,
   Thanks so much for your speedy replies. Unfortunately for me, I have a EeePc Netbook that does NOT have a cd disc drive!!! Is the first option a cd-less option? If so, I think I'll follow that advice. I just want to make sure by doing so, I'll still be able to resize Ubuntu's partition to fully maximize my experience. I'm really feeling this OS, and am completely sure I'm ready to "throw windows, out of the window!" Thanks again for your replies and I hope to hear back soon!
-Prince_Peculiar-

---

### Post by Prince_Peculiar on 2011-06-29
On a second note, I think I'd like to try resizing the Windows partition ALL the way down. Would it be safe to just hop onto windows and delete all of the programs in my uninstall list and clean it completely out, then is there a way (in Ubuntu) to partition it all the way down to the last drop? I want as much room on Ubuntu as possible!!! :D thanks again!

---

### Post by Ozymandias_117 on 2011-06-29
You will still have to boot to a livecd environment to be able to resize the filesystem.  If you don't have a CD drive, Ubuntu has the option to take the .iso and make a LiveUSB from it that you can then boot from a flash drive. (Please note that this will ERASE the flash drive)

Go to Ubuntu's Download page, download the .iso, then look at step 2 (On the download page) select "USB Stick" and "Ubuntu" and it will explain the steps.

---

### Post by nzjethro on 2011-06-29
> On a second note, I think I'd like to try resizing the Windows partition ALL the way down. Would it be safe to just hop onto windows and delete all of the programs in my uninstall list and clean it completely out, then is there a way (in Ubuntu) to partition it all the way down to the last drop?

Yes, if you don't want any programmes, you should be fine to delete them. Although if you are that confident that you will no longer need your Windows programmes, why keep the OS around? ;)

As for shrinking your Windows partition from Ubuntu, I would recommend against that, and say to resize your Windows partition from Windows. If you want to keep your Windows install around, boot into Windows, right click "My Computer", then select Manage > Disk Management, and you should be able to "shrink" you Windows partition, thus freeing up creating  a partition for Ubuntu. You should probably defragment your Windows drive at least 2 or 3 times before this, to free up space.

And to your previous post, if your laptop has a USB drive you can use [unetbootin]("http://unetbootin.sourceforge.net/") to create a Live USB stick, which has all the functionality of the Live CD.

---

### Post by amjjawad on 2011-06-30
Hello and Welcome :)

Two advices I would share with you:

1) Better NOT to hurry up and throw Windows out of the window, yet ;)

2) If you're 100% sure you don't really want that so ignore my 1st advice and format the whole HDD and install a fresh copy again. Ubuntu Installation doesn't take much time anyway.

Good luck!

---

### Post by donny.davis on 2011-06-30
my opinion is that dont make a hurry
also dont throw windows so soon..... instead just keep it with little Gigabytes (eg. 25GB)

some softwares require windows platform...(also needed to mention to use these kind of softwares we have WINE here).... but just wait

---

### Post by Derxst on 2011-06-30
Another suggestion: you can use Windows in a virtual machine via Virtual Box. If you need Windows for a particular program, fire up the VM, do your thing and shut down the virtual.

---

### Post by walt.smith1960 on 2011-06-30
> **donny.davis said:**
> my opinion is that dont make a hurry
also dont throw windows so soon..... instead just keep it with little Gigabytes (eg. 25GB)

some softwares require windows platform...(also needed to mention to use these kind of softwares we have WINE here).... but just wait

That would be my advice as well.  There is more than one thread on this forum where the lament is "I need Windows for (X) but I deleted it and have no way to restore it". Is this machine still under warranty?  If so and you have to call the manufacturer, they are going to want you to load Windows, not Linux. If the above don't apply,  I would clean up the windows partition as much as possible, shrink it so the Windows partition is 75% used then clone it using something like clonezilla.  You'd have to copy to cloned partition to either an external USB drive or external hard drive if you choose to go that route.  

Did your machine come with a restore disc?  My EeePC did even though it had no internal drive. If you have a restore disk, you can indeed "Throw Windows out the window" because you could restore to factory configuration if necessary.

---

### Post by androssofer on 2011-06-30
i agree with Derxst i run windows in virtual box (for uni work, f**kin uni! but i guess linux doesnt pay uni's to use their software.... like m$)

 however, an eeepc mite b a tad low end for such things... but i've tried it on mine.. but my eeebox can get a tad jumpy wit a windows vm on the go. but thts windows 7 pro.. so cud b more hungry than starter.. who knows!? so up to u. 

i'd put all my stuff on an external hd. fire up a live usb (eeepc bios was a bitch to get into on mine.. :-( ) and erase eveything from the hd giving a nice fresh ubuntu install. get all my stuff back from the external hd.. winning! this also means grub wont come up on boot. and then get wine for windows stuff.

ps if u do choose this option take note of ur windows serial number or whatever its called. so if u install windows in a vm, m$ cant complain its not genuine.. its the same computer...

---

### Post by BlackGrapes on 2011-06-30
> **amjjawad said:**
> Hello and Welcome :)

Two advices I would share with you:

1) Better NOT to hurry up and throw Windows out of the window, yet ;)

2) If you're 100% sure you don't really want that so ignore my 1st advice and format the whole HDD and install a fresh copy again. Ubuntu Installation doesn't take much time anyway.

Good luck!


I will like to double this advice.... 
@ Prince_Peculiar: You said you installed Ubuntu today and you are sure to throw Windows in just one day...Don't get hurry..Get along with Ubuntu a couple of days and you can get rid of Windows.. But if you are so sure then I will advise you to format the whole hard drive again with fresh installation of Ubuntu...
And yes.. Enjoy your Ubuntu!

---

### Post by Prince_Peculiar on 2011-06-30
> **nzjethro said:**
> Yes, if you don't want any programmes, you should be fine to delete them. Although if you are that confident that you will no longer need your Windows programmes, why keep the OS around? ;)
 
As for shrinking your Windows partition from Ubuntu, I would recommend against that, and say to resize your Windows partition from Windows. If you want to keep your Windows install around, boot into Windows, right click "My Computer", then select Manage > Disk Management, and you should be able to "shrink" you Windows partition, thus freeing up creating a partition for Ubuntu. You should probably defragment your Windows drive at least 2 or 3 times before this, to free up space.
 
And to your previous post, if your laptop has a USB drive you can use [unetbootin]("http://unetbootin.sourceforge.net/") to create a Live USB stick, which has all the functionality of the Live CD.
 
 
So, if I decide to keep Windows (just in case, you never know) and I do decide to shrink my Windows partition... Do I have to do anything else to ensure Ubuntu will recieve the rest of the partition I "shrunk" off?

---

### Post by Mark Phelps on 2011-06-30
If you want to have any hope of using Win7 again, after resizing your Ubuntu install, then do NOT use GParted, or any other Linux utility, to shrink the Win7 OS.  Doing so risks corrupting the filesystem and leaving it unbootable.

So, I would suggest the following (for minimum data loss):
1) Boot into Win7
2) Uninstall all the programs you no longer want to use
3) Move all the data you want to retain to a USB stick or drive (do NOT delete it just yet)
4) Connect the USB stick/drive to another PC and CONFIRM that all the data files are OK.  Only after this, delete the data files from Win7.
5) Use the Win7 Disk Cleanup utility to remove unwanted files from Win7
6) Defrag the Win7 volume
7) NOW, use the Win7 Disk Management utility to shrink the Win7 OS volume as much as it will allow.
8) Reboot into Win7 after that to let it do any needed filesystem adjustments.
9) Only NOW, boot from Ubuntu LiveCD and use GParted to grow the Ubuntu filesystem to fill the unallocated space.
10) Reboot into Ubuntu

---

### Post by dFlyer on 2011-06-30
Download 

[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)

It's a free download and will allow you to clone your windows partition. After you have a clone you can wipe your hard drive and repartition it any way you want. A clone is much easier to restore that a reinstall of Windows. Once you decide if you want to replace your windows and dual boot you can. Or you can just run Ubuntu and still have the clone should you ever change your mind.

---

### Post by Prince_Peculiar on 2011-06-30
> **Mark Phelps said:**
> If you want to have any hope of using Win7 again, after resizing your Ubuntu install, then do NOT use GParted, or any other Linux utility, to shrink the Win7 OS. Doing so risks corrupting the filesystem and leaving it unbootable.
 
So, I would suggest the following (for minimum data loss):
1) Boot into Win7
2) Uninstall all the programs you no longer want to use
3) Move all the data you want to retain to a USB stick or drive (do NOT delete it just yet)
4) Connect the USB stick/drive to another PC and CONFIRM that all the data files are OK. Only after this, delete the data files from Win7.
5) Use the Win7 Disk Cleanup utility to remove unwanted files from Win7
6) Defrag the Win7 volume
7) NOW, use the Win7 Disk Management utility to shrink the Win7 OS volume as much as it will allow.
8) Reboot into Win7 after that to let it do any needed filesystem adjustments.
9) Only NOW, boot from Ubuntu LiveCD and use GParted to grow the Ubuntu filesystem to fill the unallocated space.
10) Reboot into Ubuntu
 
 
GParted Live looks like it can only ever be burned to a cd before it's use.... Which would be grand - if I had a cd drive. So without a cd drive is there no hope for me to streatch out the Ubuntu partition?
...
They should really make a tool that allows for more ease when doing all of this.

---

### Post by Prince_Peculiar on 2011-06-30
> **dFlyer said:**
> Download 
 
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
 
It's a free download and will allow you to clone your windows partition. After you have a clone you can wipe your hard drive and repartition it any way you want. A clone is much easier to restore that a reinstall of Windows. Once you decide if you want to replace your windows and dual boot you can. Or you can just run Ubuntu and still have the clone should you ever change your mind.
 
If I decide to whipe out my hard drive and keep a clone...
1.) How would I do this?
2.) Can I slap the Windows clone onto a memory stick or card?
3.) Would I have to whipe everything or can I just get rid of Windows (and again, if so - how do I do this?
4.) Once Windows is off, can I streatch out the Ubuntu drive?
5.) Would I possibly need to whipe everything and boot the computer with an Ubuntu installer? (**_PLEASE NOTE: I DO NOT HAVE A CD DRIVE!!!_**)
 
Thanks

---

### Post by Prince_Peculiar on 2011-06-30
> **walt.smith1960 said:**
> That would be my advice as well. There is more than one thread on this forum where the lament is "I need Windows for (X) but I deleted it and have no way to restore it". Is this machine still under warranty? If so and you have to call the manufacturer, they are going to want you to load Windows, not Linux. If the above don't apply, I would clean up the windows partition as much as possible, shrink it so the Windows partition is 75% used then clone it using something like clonezilla. You'd have to copy to cloned partition to either an external USB drive or external hard drive if you choose to go that route. 
 
Did your machine come with a restore disc? My EeePC did even though it had no internal drive. If you have a restore disk, you can indeed "Throw Windows out the window" because you could restore to factory configuration if necessary.
 
My netbook came with no discs at all. It prompted me to make a backup when I first got it, which I had originally done and stored on an external hard drive. Unfortunately the hard drive crashed and I lost my backup.

---

### Post by amjjawad on 2011-06-30
If your machine can boot from USB, you can create LiveUSB (check the download page in [www.ubuntu.com](www.ubuntu.com)) and GParted does exist with the LiveUSB (System > Administration > GParted).

The most important thing is to BACKUP your important data. Whether you save that to External HDD, USB or any other media, just make sure you do it. Then, you can do whatever you want.

Good luck!

---

### Post by dFlyer on 2011-06-30
I'm not sure if this will work with a usb as I've never tried it that way. You may be able to find out more information on the web page I referenced. Sorry I can't be of much more help. Without a reinstall cd/usb, I would wouldn't mess around with your windows partition unless your very 100% sure you want to dump windows as you will have no way to restore windows with out the disk or a clone should something go wrong.

---

### Post by Frogs Hair on 2011-06-30
If you choose to make a Windows USB / clone ,  be sure to write down the product code .  The USB needs to be made from Windows .

---

### Post by Derek Karpinski on 2011-06-30
First, make backups, on a USB stick, of all your documents, emails, pictures, or anything that you have on your Windows partition.
 
Just a note: The Windows 7 install ISO's are out there available for download. There is nothing illegal about downloading a genuine Windows ISO file, as you'll still use your license that came with your computer.
 
I suggest finding the retail ISO for the Windows version you have pre-installed, downloading it, and putting it on a USB stick. You'll probably need a 4GB stick.
 
I'd also suggest downloading a utility called ABR. It backs up your OEM activation code, and when you do a clean install, it uses YOUR OEM license key to activate your 'clean' copy of Windows. Make a backup of the files that ABR generates. Some could question the legality of ABR, but I really don't see anything wrong with it.
 
Now you have a complete backup of Windows just in case you want to go back.
 
Next, download the newest ISO of Ubuntu, and install completely over the whole drive.
 
If you're completely sure you want to get rid of windows, that's what I'd suggest.  I wouldn't mess around with GParted from a Live CD, or even trying to shrink partition sizes with Windows.  In fact, I'd even delete the 'Recovery' partition that most likely came on your HD.

---

### Post by Kixtosh on 2011-06-30
> **Prince_Peculiar said:**
> ... **_PLEASE NOTE: I DO NOT HAVE A CD DRIVE!!!_** ...What method did you use to install Ubuntu in the first place?

I agree with much of what has been already said. If you do not have restore media for Windows, you should keep a clone or backup of some description, just in case it is ever needed. I would use the Disk Defragmenter tool included with Windows at least three times before making the clone or backup (it goes faster each time, and should complete in a few minutes by the third time). There should also be a simple to use backup utility somewhere in your Windows system, identified as something like "Recovery Disk Creator". Try typing "Recovery" in the "Start Menu" search box and see if any such utility shows up in the results. Either cloning, or a recovery utility will preserve not only Windows for future use, but also any other factory installed software. You will have to borrow a USB CD writer or DVD writer for this, however.

If you do wipe Windows off, then the simplest way in my opinion is to install Ubuntu again, the same way you already did before, but this time tell it to use the entire disk (not run side by side). Windows, and any other applications included with it, will get wiped out. You won't have to bother with individually shrinking or removing anything.

Otherwise, if you prefer to just shrink Windows, and expand Ubuntu, the Windows partition will not diminish performance or interfere with Ubuntu in any way, other than to show up in the boot menu. The boot menu will disappear if you have only Ubuntu installed.

---

### Post by nzjethro on 2011-06-30
> 
So, if I decide to keep Windows (just in case, you never know) and I do decide to shrink my Windows partition... Do I have to do anything else to ensure Ubuntu will recieve the rest of the partition I "shrunk" off?

This looks like it has been covered in a roundabout way in previous posts, but I'll try to make it clear. You want to shrink your Windows 7 partition (after backing up, removing files, etc.), which will make your Win7 partition smaller, and create "unallocated space" in the freed up space. For example if Win7 is 50GB and you shrink it to 20GB, your disk will have a 20GB Windows 7 Partition, and 30GB of "unallocated space".

Then, when you go to install Ubuntu (from your LIVE USB, no CD required), choose "Try Ubuntu" rather than "Install Ubuntu". Then, when your Ubuntu Live desktop fires up, open a terminal (by pressing CTRL + ALT + t), and type
```
gksudo gparted
```
It may ask you to install GParted, in which case, do. Then, when you have GParted up and running, you will be able to find your "unallocated space", next to your Win7 partition (which will likely be called "XXGB Filesystem". You want to create an extended partition for Ubuntu within the unallocated space, so right click the "unallocated space", and select "new". You want to format it as "ext4", and where it says "create as", choose "extended". To apply these operations, go to Edit > Apply all operations.

Then, launch into installation, by selecting the "Install Ubuntu" icon from the desktop. Choose all your options until you get upto the partitioning menu, where you should choose "Specify Manual Partitioning" (it may be called "Something Else" in Ubuntu 11.04). This will bring up a menu similar to GParted. You want to right click the ext4 partition you just created, and choose "/" as a mount point. Then, continue with your installation, choosing you main HDD (probably sda) as your MBR location.

[Here's]("http://lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony") a guide that I put all first time dual-booters to. I used it, and had no troubles. It's written for 9.10 (Karmic Koala I think), so it's a bit outdated, but the ideas are the same, and it has a lot of pictures.

And as always, if you are unsure what to do in any stage of the process, post questions here and someone will help out.

---

### Post by Prince_Peculiar on 2011-06-30
Thanks so much for your help everyone!
   I've decided to keep windows partitioned on my computer.... I resized the partition on the Windows side down as far as it could go so now I have random room just sitting here on my computer. All I need to know now, is how to run GParted on Ubuntu off of a memory card? Or does it have to be a usb flash drive? How do I start it? BLAH SO CONFUSED!!! I just want to resize my partion UP in ubuntu. That's all. :)

---

### Post by Kixtosh on 2011-06-30
> **Prince_Peculiar said:**
> ... All I need to know now, is how to run GParted on Ubuntu off of a memory card? Or does it have to be a usb flash drive? ...No, it doesn't have to be a USB drive. Any media that the specific BIOS (Basic Input Output System) of your computer allows you to boot from will do. Whatever media you used to install Ubuntu in the first place will work.

GParted will not be able to modify the Ubuntu partition on your hard drive when you are already running Ubuntu from your hard drive. That is why you will need to use a Live "session" to use GParted to modify your Ubuntu partition while it is not "mounted" (or "in use", basically). These sessions run entirely from RAM, so the hard drive can be "off" essentially. It slows everything down, but you can modify the hard drive contents.

The command already described, used in "Terminal", will give GParted administrative rights and launch the application:

```
gksudo gparted
```

---

### Post by Prince_Peculiar on 2011-06-30
> **Kixtosh said:**
> Whatever media you used to install Ubuntu in the first place will work.

... All I did was went to the Ubuntu website and installed it directly from there. I didn't use a cd drive, an external, NOTHING. Just ran ubuntu.exe

...

Thus, while everyone keeps telling me to use the same method, I am very well just trying to ...

---

### Post by Kixtosh on 2011-06-30
I may be mistaken, but it sounds like you downloaded it as a Windows application, from within Windows, so it doesn't currently have it's own partition. I'm not familiar with that, but chances are it's listed in the programs installed on Windows 7. What happens right now when you boot up, or turn your computer on? What startup options are shown?

Do you have any way to make a USB install disk, on a flash drive or CD drive?

**Edit:** is this what you used? Check the boot selection screen image in particular.

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

---

### Post by amjjawad on 2011-07-01
Great, so we have been discussing this in 4 pages and now, it turns to be Wubi installation? I really hope I'm WRONG!

When you go to "Programs and Features" in Control Panel in Windows, do you see something about Wubi?

If yes, then you can NOT get rid of Windows and keep Ubuntu, period.

Again, if you're happy the way it's now, do NOT change anything.

If you are happy about Ubuntu and NOT happy about Windows (or both together), then format the whole thing and install again.

How to create Live USB since you have NO CD-Drive?
Check [www.ubuntu.com](www.ubuntu.com) - download page. You'll see everything explained in details.

That's ALL what you need to know at this point :)

P.S.
Did I mention that you need to backup your important data first? guess I did in another post :)

---

### Post by Kixtosh on 2011-07-01
> **amjjawad said:**
> ... If yes, then you can NOT get rid of Windows and keep Ubuntu, period. ...Actually, I wouldn't be so categorical about that. The link I provided earlier has a huge amount of great information about Wubi, including how to migrate it to it's own partition and remove Windows. There is a link in the document to this thread:

[http://ubuntuforums.org/showthread.php?t=1519354](http://ubuntuforums.org/showthread.php?t=1519354)

It is necessary to create a partition, however, so GParted will be needed ... after all the disk defragmenting mentioned earlier (at least three times, please!). I'm not sure how GParted works in Wubi, but it's probably not all that different, and it's probably mentioned somewhere in that lengthy thread.

---

### Post by amjjawad on 2011-07-01
> **Kixtosh said:**
> Actually, I wouldn't be so categorical about that. The link I provided earlier has a huge amount of great information about Wubi, including how to migrate it to it's own partition and remove Windows. There is a link in the document to this thread:

[http://ubuntuforums.org/showthread.php?t=1519354](http://ubuntuforums.org/showthread.php?t=1519354)

It is necessary to create a partition, however, so GParted will be needed ... after all the disk defragmenting mentioned earlier (at least three times, please!). I'm not sure how GParted works in Wubi, but it's probably not all that different, and it's probably mentioned somewhere in that lengthy thread.

My bad, you're right about that. I've seen that thread once it's been created by bcbc. I posted here once I woke up so don't expect me to remember everything :D

I'm not into Wubi and will never be. I prefer the ordinary way to install the OS.

That's for the reminder ;)

---

### Post by Kixtosh on 2011-07-01
> **amjjawad said:**
> ... I posted here once I woke up so don't expect me to remember everything ...Dude! Before posting, after waking up, please do:
```
sudo apt-get update
```It's right there in your profile: squished in between your join date and your bean count! ... ;) ... :p ... :D

---

### Post by amjjawad on 2011-07-01
> **Kixtosh said:**
> Dude! Before posting, after waking up, please do:
```
sudo apt-get update
```It's right there in your profile: squished in between your join date and your bean count! ... ;) ... :p ... :D

LOL :D

Actually I had to do:
```
sudo apt-get upgrade

```
first but Unity crashed and you know the rest :P just kidding!

Good one, mate ;)

---

