---
title: "Help setting up dual boot"
date: 2010-03-09
forum: New to Ubuntu
---

### Post by JaMartini on 2010-03-09
Hey everyone!

I've finally decided to give Ubuntu a try. I would like to try dual boot with Windows XP. I'm following the documentation at [https://help.ubuntu.com/9.10/switching/installing-partitioning.html](https://help.ubuntu.com/9.10/switching/installing-partitioning.html) but i'm a bit confused. The instructions say to right click the windows partition and resize. When I do this I only get the options Change, delete, and Revert. The change option doesn't allow for chaange in size. Do I need to make a new partion table? How would I do this? Also will this delete all my data on Windows? Do I need to re-install windows on this new partion or is my current data automaticly moved to the new partition?

Thanks for the help!!!

---

### Post by anthonyrossbach on 2010-03-09
All you need to do is get the iso from the site and use it to make a ubuntu disk.

Then take the disk and when in windows put it in. And run it

there you can install ubuntu with windows and you just go thou the options picking ubuntu install size (how much of the hardrive it will take) and you install with windows.

This is the best way for a starter.

---

### Post by oingk on 2010-03-09
To do what the person before me said go to [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)


Download Ubuntu, than make an iso file (if you don't know how to do this, ask here) on a CD or DVD.

Insert the CD in computer, and either boot up with it inside or just run it on Windows.

The instructions will be very easy, it will guide you through very easily.

---

### Post by oingk on 2010-03-09
OK basically what you must do when you run your CD you will have a number of options:

You can chose "run Ubuntu without making any changes to your system".

If you haven't used Ubuntu before, you can chose this. It will let you use Ubuntu and then if you decide that you like it then there is an icon on your desktop saying "install Ubuntu" and you can chose this.

It will give you options if you want to wipe out your hardrive or make a dual-boot. If you chose to do dual-boot, you can chose how much disk you wanna give to windows and how much to ubuntu

---

### Post by JaMartini on 2010-03-09
I would prefer to do a dual boot to maximize performance, as I have read. I'll do the windows install if I can't get this to work, but I would like to learn how to do the dual boot. 

oingk:
I have tried this. During the "Prepare disk space" section of the install, there are only two options. Erase and use entire disk. Or Specify Partitions Manually.`How do I do the dual boot through manual partitions? My original link said to right click and adjust the size of the windows partition, but this is not an option.

---

### Post by mookiemeister on 2010-03-09
That's strange.  I just recently installed Ubuntu 9.1 64-bit on my system with Windows Vista x64 already on it without any problem.  When I got to the 'Prepare disk space', I had 3 options:
1) Install side by side
2) Erase and use entire disk
3) Specify partition manually (advanced)

Then there is a slider that I can adjust for amount of space for Windows Vista and Ubuntu.

I picked option 1 to install side by side and Ubuntu installer was able to reduce the space that Windows Vista was taking up.

---

### Post by oingk on 2010-03-09
If you downloaded the file from the link I mentioned, when installing, there should be the option where you can set how much disk you want to dedicate to each OS just by drugging a point on an image that represents your disk.

Apparently there are various different installation procedures, depending on where you downloaded your iso file from.

---

### Post by lkraemer on 2010-03-09
The first thing you need to do is boot into Windows.  I assume
you are using XP, as you previously posted.  Run Disk Cleanup,
then Defrag the Drive at least twice before proceeding

Now read this guide twice before doing anything:
[http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm](http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm)

Your Windows install most likely occupies the first Partition on the
Physical Drive.  You may or may not have other partitions on the drive.
Some Computers have a RECOVERY Partition.  To find out if these exist
boot the Ubuntu LiveCD and when it is up and running go to:
SYSTEM -> ADMINISTRATION -> GPARTED
Gparted will show your existing partitions.  Make good notes of what
is displayed.  At this point you can resize Windows, add partitons,
Delete Partitons, etc until you have used the Maximum of Four.
Anything you Delete is gone, so you better have a backup.

Any one Physical Hard Drive can ONLY have a MAXIMUM of FOUR Primary
Partitions.  (Your Windows XP Partition is using one, with three remaining.)
Ubuntu will use another, along with Linux-Swap, leaving
one remaining, unless you have a RECOVERY Partition.

You can use EXTENDED Partitions (Logical), but I prefer not to.....

So at this point you should have a good view of what is on the Hard Drive.
If you assume Windows consumes HALF of the Physical Drive, and there is
a ~10 Gig Recovery Partition, if it exists, the remainder has to be used
for Ubuntu and Linux-Swap.  The Last Partition (Right Most on the Graphics
Display) will be the Linux-Swap and should be sized as 2 Times
the Available RAM.  The remainder will be Ubuntu,.....unless you decide to
make /home a separate partition, in which case the Ubuntu (/) should be sized
at about 10-15 Gig.  This does waste some space, but allows you to have a
separate /home and gives you some extra benefit.  That decision will have to be yours.

So, sit down with a note pad and decide what sizes you have available for each
and resize Windows accordingly.  Sometimes it's easier to purchase a larger
Hard Drive, and just Clone the Windows Partition, then install Ubuntu.

OH, You also need SuperGrub just in case your Master Boot Record needs
to be re-written so XP can boot if it gets trashed.

And be sure to backup your data so as to not lose anything.  If something
weird happens it could be gone in a flash.

lk

---

### Post by chellrose on 2010-03-09
You'll also want to defragment your hard drive in WinXP (perhaps several times), to make sure none of the important files get deleted when you re-partition.  I have a good link for dual-booting with XP on the other partition of my hard drive.  Give me a few minutes to switch over and I'll hunt it down for you...

I installed Ubuntu as dual-boot with XP on my mom's computer a few months ago with no problems, so it should be doable.

Edit: I think the link that lkraemer posted is the same one I followed.  You should be good to go.  Just make sure to defragment first, and also to back up anything important. :-)

---

### Post by JaMartini on 2010-03-09
Thanks for the suggestions guys! The main issue is the lack of options for dual boot, which is seen in the link provided by lkraemer on this page: [http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm?page=3](http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm?page=3). 

I downloaded the version 9.10 at the same location provided by oingk, a few days ago. Unless this has changed, I believe it should be the same.

---

### Post by oingk on 2010-03-09
OK it won't look like the link you provide here, but it will be similar. Something like this:
[http://cdn.cbsi.com.au/story_media/339299234/ubuntu-910-karmic-koala_5.jpg](http://cdn.cbsi.com.au/story_media/339299234/ubuntu-910-karmic-koala_5.jpg)

Where you can slide the slider along the coloured line that represents your hard-drive.

Do you see this when you get to that stage?

---

### Post by JaMartini on 2010-03-09
Nope. I've attached a screen shot of what I am getting. It lacks the one option I want!

---

### Post by hsartoris on 2010-03-09
You can also create a new partition directly in Windows by doing this:
go to the "run" box
type in compmgmt.msc
then, in the menu, click on disk management
resize your existing partition, you can go from there.

my theory is that windows does the partitioning itself, it's far less likely to damage important files

by the way, this is for dual booting, not for booting in windows

---

### Post by chellrose on 2010-03-09
Pick "Specify partitions manually".  That will take you to a screen like the one posted by oingk above.

You can shrink the WinXP partition, and specify partitions for Ubuntu and swap.

---

### Post by oingk on 2010-03-09
I downloaded the iso file from the link I mentioned, last night, and the option that I think you want was there.

If you download again from that link, the options should be the same (it should look like the pic in the last link I sent).

Regardless of that, what option do you want exactly? The "Install them side by side"?

---

### Post by JaMartini on 2010-03-09
oingk: I'm re-downloading the .iso right now to see if that fixes it. Yes, I believe that is the option that I want?

Sissy13: I'm in windows now, so can't get a screen shot, but I did not get the same thing. There was a list of partitions and no way to change the size of the existing partitions. I could only "Create New Partition Table", like I mentioned in the original post. 

hsartoris: Hmm, good sugestion. Maybe ill give that a try!

---

### Post by JaMartini on 2010-03-10
Still no luck. I've attached a screen shot of what happens when I select Specify Partitions Manually.

hsartoris: XP wouldn't let me adjust the partition size. Upon research, this is not available in XP and must be done through a 3rd party software. 


Anyone else have any suggestions?

---

### Post by undecim on 2010-03-10
You can use GParted from the live CD in System -> Administration -> GParted to resize your XP partition, and then when installing, you should be given the option to install Ubuntu in the free space on the drive.

---

### Post by egalvan on 2010-03-10
It seems that both Windows and gparted have troubles re-sizing the disk.

have you run checkdisk from within Windows?
It will be under the properties/tools/check for errors

Have it check and fix errors.
Re-boot and do it again.
Defrag the drive.
Re-boot and defrag again.

Then try the install again.

Personnaly, I use PartedMagic to do all partitioning work.

partedmagic.com

It´s a great mini-distro for drive partitioning, formatting and recovery.

---

### Post by JaMartini on 2010-03-10
Still no luck. I did diskcheck and it repaired errors. Did it a second time and no errors. When I defrag, there are some files it says it cannot defrag. When I try to use GParted, I get a warning that says the disk has at least 7 bad sectors. It has some suggestions of what to do, but I don't know how to use ntfsresize and don't want to do it without being sure.

---

### Post by egalvan on 2010-03-11
Go to the drive maker's website and try to find diagnostic software for your drive.

Seagate, Western Digital and others have such packages.

You can usually run a non-destructive test on the drive that will attempt to preserve the data.

Also, software that checks the  SMART data can give some clues.

It sounds like a failing drive.

---

### Post by NertSkull on 2010-03-11
Its a bit more work, but you could also try simply starting over and wiping the entire disk.  Then re-install windows while leaving a portion set aside for Ubuntu during the process.

Then install ubuntu on that unformated space.  I know its a hassle to re-install windows and back up all your data.  But frankly I find that a fresh install of windows every so often is a good thing anyway.

---

### Post by JaMartini on 2010-03-12
Thanks for the help guys! I think I'll just give up and install Ubuntu as the only OS. It's my old laptop which I only really use for browsing the internet, which I'm sure will be no problem in Ubuntu. Just wanted to keep Windows in case I really needed it for something, but oh well. Thanks again for the help, and I look forward to asking a million more questions.

---

### Post by hsartoris on 2010-03-12
here's another way to resize partitions:
in Windows:
go to "run"
type in "compmgmt.msc" and hit enter
go to "disk management"
change your disk size
create a new one with the freed space
boot into your live cd and choose "choose partitions manually"
install on your new partition (make your partitions different sizes so you can identify them)

---

