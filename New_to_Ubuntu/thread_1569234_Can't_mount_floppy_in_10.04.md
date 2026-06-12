---
title: "Can't mount floppy in 10.04"
date: 2010-09-06
forum: New to Ubuntu
---

### Post by tbird6820 on 2010-09-06
Unable to mount floppy
 using Ubuntu 10.04 LTS the Lucid Lynx and up to date.

I have tried this and I still get Unable to mount location, No media in the drive and the floppy disk is good, I even tried moving the button on the disk in the bottom right.

Ok. Step by step, what you need to do:
1. Open a Terminal
2. Type: "sudo nano /etc/fstab <enter>" (Without quotation marks, replace <enter> by an "enter")
3. Use your arrow keys to move to the bottom of the file
4. Type in the following line:
/dev/fd0 /media/floppy0 auto rw,user,noauto 0 0
5.Go Ctrl-o (letter O, not zero), it will prompt:
"File Name to Write: /etc/fstab". Hit enter.
6. Go Ctrl-x . This will exit nano.
7. To mount a floppy, put a floppy in the floppy drive and run the command:
"mount /media/floppy0" (without quotation marks). If that fails,
"mount /dev/fd0 /media/floppy0" (again, no quotation marks).

I also tried disk utility and tried to format, Scheme: Master boot record and got this
Error formatting drive
Error creating partition table: helper exited with exit code 1: Error calling fsync(2) on /dev/fd0: Input/output error

And  I tried sudo mount /dev/fd0 /mnt/floppy
got,
mount: mount point /mnt/floppy does not exist

tried id
got,
dave@dave-desktop:~$ id

uid=1000(dave) gid=1000(dave) groups=4(adm),20(dialout),24(cdrom),46(plugdev),105(lpadmin),119(admin),122(sambashare),1000(dave)






Here is my content of my file

dave@dave-desktop:~$ cat /etc/fstab

# /etc/fstab: static file system information.

#

# Use 'blkid -o value -s UUID' to print the universally unique identifier

# for a device; this may be used with UUID= as a more robust way to name

# devices that works even if disks are added and removed. See fstab(5).

#

# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc            /proc           proc    nodev,noexec,nosuid 0       0

/dev/sda1       /               ext4    errors=remount-ro 0       1

# swap was on /dev/sda5 during installation

UUID=46715bbf-7baa-4972-9f95-3319b9e28b05 none            swap    sw              0       0

/dev/fd0 /media/floppy0 auto rw,user,noauto 0 0

---

### Post by egalvan on 2010-09-06
> **tbird6820 said:**
> Unable to mount floppy
 using Ubuntu 10.04 LTS the Lucid Lynx and up to date.

Here is my content of my file

dave@dave-desktop:~$ cat /etc/fstab

**/dev/fd0 /media/floppy0 auto rw,user,noauto 0 0**


here"s mine:

```

**/dev/fd0  /media/floppy0  auto   rw,user,noauto,[COLOR="Magenta"]exec,utf8[/COLOR]     0  0**
```

I high-lighted the **[COLOR="Red"]differences[/COLOR]**...


Nothing shows with no floppy inserted.
When a floppy inserted, an icon pops up on the desktop.
Been working since I installed Hardy July of 2008.

---

### Post by Ozymandias_117 on 2010-09-06
The previous poster's added utf8 MIGHT do something, but exec has nothing to do with what you're talking about. 

Also, you have another problem.

You need to make the directory /mnt/floppy (Or whatever directory you want it mounted in) before you try to mount it.

PLEASE NOTE! If you mount the floppy in /mnt it WILL NOT show up on the desktop when it's mounted. If you want it to show up on the desktop, it needs to be /media/floppy

Edit: Based on what you've posted from Disk Utility I believe there may still be another problem. Let me know when you've finished the rest.

---

### Post by egalvan on 2010-09-06
Ozymandias_117, the fstab that I showed is the default entry made by the default install of Hardy.
Just an example of what Ubuntu does...
I made no changes to it, which is why I posted it.
(Quite frankly, at that time I had NO idea what it all meant :)


Also, I have a

/media/floppy0


AND  a link

/media/floppy

(whose properties show it as 'type: Link to folder'


Again, these are the default entries mad by the default install.

And two other Dell desktops with floppies show these same entries, under Hardy.


Sadly, can't tell about Lucid....
five different machines, five different crashes during install..
Live DesktopCD, alternate CD, 32-bit, 64bit... all fail...
looking closely at this situation.
(haven't had such bad luck with installs since Feisty/Gutsy)



And I'm thinking the OP should check to verify that the floppy is enabled in the BIOS... that caught me once...

---

### Post by Windows Nerd on 2010-09-06
It was under my impression that HAL auto-mounted DVDs, USBs, floppys and other removable media? I never have to manually mount anything (in Ubuntu and distros that use HAL, that is).

---

### Post by tbird6820 on 2010-09-06
Ok I replaced /dev/fd0 /media/floppy0 auto rw,user,noauto 0 0 
with /dev/fd0  /media/floppy0  auto   rw,user,noauto,exec,utf8     0  0, 
did the Ctrl-o enter and the x.

I don't know how to make the directory /media/floppy also when I go to places and click on computer, my floppy drive shows up there.

---

### Post by Ozymandias_117 on 2010-09-06
> **tbird6820 said:**
> Ok I replaced /dev/fd0 /media/floppy0 auto rw,user,noauto 0 0 
with /dev/fd0  /media/floppy0  auto   rw,user,noauto,exec,utf8     0  0, 
did the Ctrl-o enter and the x.

I don't know how to make the directory /media/floppy also when I go to places and click on computer, my floppy drive shows up there.

Does your floppy work? If so, you must already have the directory :)

@Windows Nerd I'm not sure how HAL interfaces with floppies, but didn't Ubuntu switch from HAL to udev?

---

### Post by tbird6820 on 2010-09-06
I don't know if this makes a differents but my computer is a HP pavilion 526x with over 1gig of ram and the floppy drive is not the original.

---

### Post by tbird6820 on 2010-09-06
floppy works.

---

### Post by Windows Nerd on 2010-09-06
> **tbird6820 said:**
> Ok I replaced /dev/fd0 /media/floppy0 auto rw,user,noauto 0 0 
with /dev/fd0  /media/floppy0  auto   rw,user,noauto,exec,utf8     0  0, 
did the Ctrl-o enter and the x.

I don't know how to make the directory /media/floppy also when I go to places and click on computer, my floppy drive shows up there.
Ubuntu should create /media/Floppy (actually it may be /media/<drive_label>) and mount the floppy automatically when you click on the floppy from "places". When you unmount the disk, Ubuntu should sequentiality destroy the mount directory.

---

### Post by Windows Nerd on 2010-09-06
> **Ozymandias_117 said:**
> Does your floppy work? If so, you must already have the directory :)

@Windows Nerd I'm not sure how HAL interfaces with floppies, but didn't Ubuntu switch from HAL to udev?

Was not aware of the switch, on Ubuntu, I did know that HAL is being deprecated in favour of Udev. However, many GNOME applications still depend on HAL as a dependency (At least in the Arch Repositories, I use Ubuntu on my laptop and did not use a minimal install and build from there. I have no idea about the Ubuntu repositories).

---

### Post by plucky on 2010-09-06
For 10.04.1 this works

[http://ubuntuforums.org/showpost.php?p=9527243&postcount=37](http://ubuntuforums.org/showpost.php?p=9527243&postcount=37)

Good Luck

---

### Post by tbird6820 on 2010-09-06
I did what it said in #12 and went to places and the icon looks like a floppy disk, clicked on it and it said:

Unable to mount Floppy Disk
Error mounting: mount exited with exit code 1: helper failed with:
mount: I could not determine the filesystem type, and none was specified

---

### Post by egalvan on 2010-09-06
> **tbird6820 said:**
> I did what it said in #12 and went to places and the icon looks like a floppy disk, clicked on it and it said:

Unable to mount Floppy Disk
Error mounting: mount exited with exit code 1: helper failed with:
mount: I could not determine the filesystem type, and none was specified

As **Ozymandias_117** stated in post #7, if the floppy icon shows up, the the mount point is created and used...

Further, not to sound like a broken record, but are you **SURE** the floppy drive **AND** the floppy diskette **ACTUALLY WORK**?

Does the floppy drive indicator LED light up when the machine is booted?
If there is a floppy in the drive, can you hear the floppy spin up?
(With no floppy, many drives have a very short spin-up, easy to miss)
Does the floppy spin up and the LED light up when you try to access it (by clicking on the icon)?

Did the floppy drive and floppy disk EVER work ON THIS MACHINE?
(the following may be bad,,
drive
cable
position of cable (it's possible to plug in backwards)
jumpers (depending on age, different mobo's need different jumper setting on the drive)

---

### Post by tbird6820 on 2010-09-06
No problem, sometimes asking more than once helps, I've tried so many different things I'm numb...and I've been tring to write everything down that I have done and you don't sound like a broken record!

Further, not to sound like a broken record, but are you SURE the floppy drive AND the floppy diskette ACTUALLY WORK?  Yes

Does the floppy drive indicator LED light up when the machine is booted? Yes
If there is a floppy in the drive, can you hear the floppy spin up? Yes
(With no floppy, many drives have a very short spin-up, easy to miss)
Does the floppy spin up and the LED light up when you try to access it (by clicking on the icon)? Yes

Did the floppy drive and floppy disk EVER work ON THIS MACHINE? Yes I had xp no problems.
(the following may be bad,,

---

### Post by tbird6820 on 2010-09-06
I fired it up and it open a few times and maybe the third time I get this message 
Unable to mount Floppy Disk
Error mounting: mount exited with exit code 1: helper failed with:

mount: I could not determine the filesystem type, and none was specified

I also went to computer right clicked Floppy Drive: Floppy Disk , format and a box pops up and at the top it states: format 1.5 MB volume (/dev/fd0)
Type: compatible with all systems (fat)
Name: new volume
I get this message 
Error formatting volume

Error creating file system: helper exited with exit code 1: Error calling fsync(2) on /dev/fd0: Input/output error





# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc            /proc           proc    nodev,noexec,nosuid 0       0

/dev/sda1       /               ext4    errors=remount-ro 0       1

# swap was on /dev/sda5 during installation

UUID=46715bbf-7baa-4972-9f95-3319b9e28b05 none            swap    sw           $

/dev/fd0  /media/floppy0  auto   rw,user,noauto,exec,utf8     0  0

---

### Post by Ozymandias_117 on 2010-09-06
> **tbird6820 said:**
> I fired it up and it open a few times and maybe the third time I get this message 
Unable to mount Floppy Disk
Error mounting: mount exited with exit code 1: helper failed with:

mount: I could not determine the filesystem type, and none was specified

I also went to computer right clicked Floppy Drive: Floppy Disk , format and a box pops up and at the top it states: format 1.5 MB volume (/dev/fd0)
Type: compatible with all systems (fat)
Name: new volume
I get this message 
Error formatting volume

Error creating file system: helper exited with exit code 1: Error calling fsync(2) on /dev/fd0: Input/output error





# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc            /proc           proc    nodev,noexec,nosuid 0       0

/dev/sda1       /               ext4    errors=remount-ro 0       1

# swap was on /dev/sda5 during installation

UUID=46715bbf-7baa-4972-9f95-3319b9e28b05 none            swap    sw           $

/dev/fd0  /media/floppy0  auto   rw,user,noauto,exec,utf8     0  0

Is the switch on the floppy set to the direction that you can write to the disk?

---

### Post by tbird6820 on 2010-09-06
Yes the switch is in the up position, as far as I know this is correct I have never moved this before.

---

### Post by khelben1979 on 2010-09-07
Check if the [mtools]("http://en.wikipedia.org/wiki/Mtools") package is installed in your System.

Also, I would recommend that you make sure that /media/floppy0/ can be access'able by your regular user so it's not a file permission problem which would restrict access and force the system to ask for root password just to access the floppy drive.

---

### Post by whiskyprajer on 2010-09-08
I am in the exact same boat (my Windows partition has no trouble with either the drive or the disk) and would very much appreciate a fix.

---

### Post by tbird6820 on 2010-09-08
> **whiskyprajer said:**
> I am in the exact same boat (my Windows partition has no trouble with either the drive or the disk) and would very much appreciate a fix.




Thanks I'll check this tomorrow.;)

---

### Post by tbird6820 on 2010-09-08
> **khelben1979 said:**
> Check if the [mtools]("http://en.wikipedia.org/wiki/Mtools") package is installed in your System.

Also, I would recommend that you make sure that /media/floppy0/ can be access'able by your regular user so it's not a file permission problem which would restrict access and force the system to ask for root password just to access the floppy drive.




Thanks:)

---

### Post by tbird6820 on 2010-09-10
I replaced the floppy/ribbon with another but to no change....and its not like I really need the floppy anyhow.

---

### Post by cjv8888 on 2010-09-10
Floppy mounted in terminal easily in Hardy but somehow this is lost in the subsequent releases. 

This is how I mount floppies in Karma and Lucid.

1) Comment out the /dev/fd0 line on your /etc/fstab file by adding # in front.


2) Then do:
sudo mount -t vfat /dev/fd0 /media/floppy0

Floppy is then mounted as root so to write to it you have to do a gksu nautilus.

Hope this works for you.

---

### Post by whiskyprajer on 2010-09-11
Thanks, cjv, although I'm still holding out hope for a fix vs. a work-around. Currently I've been transferring floppy files (text) via Windows to the central partition, then logging on to Ubuntu. I frankly couldn't say which work-around is less time-consuming.

Still waiting for this to qualify as "solved."

---

### Post by tbird6820 on 2010-09-13
> **Ozymandias_117 said:**
> The previous poster's added utf8 MIGHT do something, but exec has nothing to do with what you're talking about. 

Also, you have another problem.

You need to make the directory /mnt/floppy (Or whatever directory you want it mounted in) before you try to mount it.

PLEASE NOTE! If you mount the floppy in /mnt it WILL NOT show up on the desktop when it's mounted. If you want it to show up on the desktop, it needs to be /media/floppy








Ozymandias_117, you mentioned:
Edit: Based on what you've posted from Disk Utility I believe there may still be another problem. Let me know when you've finished the rest.
 
I'm done playing with this drive for awhile so what is the other problem?

---

### Post by tbird6820 on 2010-09-13
here is my new file:

 <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda1       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=46715bbf-7baa-4972-9f95-3319b9e28b05 none            swap    sw              0       0
/dev/fd0  /media/floppy0  auto   rw,user,noauto,exec,utf8 0 0

---

### Post by GOREMEISTER on 2010-09-13
Unable to mount floppies in 10.4.

I should be able to just click on the floppy in Nautilus and have it mount.

Does not work in 10.10 either.

Sad...

---

### Post by lkraemer on 2010-09-13
/media/floppy has been created.................
```

sudo mount -t vfat /dev/fd0 /media/floppy

```

mount: special device /dev/fd0 does not exist
larry@larry-laptop:~$

My External Drive is good, it works in Windows.  How did this slip through
the cracks in 10.04 LTS?

lk

---

### Post by plucky on 2010-09-14
From [Here](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/441835) this command seems to work ```
udisks --mount /dev/fd0
``` with the upgraded udisks program

Good Luck
.

---

### Post by lkraemer on 2010-09-14
Well, it doesn't work for me when I use:
```

udisks --mount /dev/fd0

```

I plugged in my USB Floppy drive, inserted a floppy disk, and then I
opened Gparted and had a look at the hard drives that were mounted and 
I have my Floppy drive mounted as /dev/sdc with (0,0) bytes.
I removed the floppy from the USB port and then I only have /dev/sda
as a Hard Drive which is correct.

lk

---

### Post by GOREMEISTER on 2010-09-14
This works:

From - [https://answers.launchpad.net/ubuntu/+source/util-linux/+question/120571](https://answers.launchpad.net/ubuntu/+source/util-linux/+question/120571)


Problem solved, thanks to peter b!!!

To summarize, reading (and writing) a floppy disk in Lucid Lynx (10.04) requires three steps:

1. Allow yourself to use the floppy by going to System->Administration->Users and Groups->Advanced Settings->User Privileges and click on "Use floppy drives"

2. Use the old version of udisks () by going to System->Administration->Synaptic Package Manager, find the udisks package, mark udisks for reinstallation, click on Package->Force Version, and select the 1.0.1-1build1 version (which is the old version). Then click on apply to finish the installation.

3. Remember to unclick udisks whenever Update Manager wants to install new updates, or you'll get the new version and floppy disks won't work anymore!

After the old udisks is installed (and the machine is rebooted), when you insert a floppy a cute little icon comes up on the desktop and in Nautilus (and on Disk Mounter if you have that installed). Left clicking on the icon and select Mount Floppy Disk will put an icon in Nautilus, and then you read, write, and format the floppy just like any other drive.

Thank you, peter b!!!

PS: Is this a bug???

---

### Post by cjv8888 on 2010-09-15
> **GOREMEISTER said:**
> This works:

From - [https://answers.launchpad.net/ubuntu/+source/util-linux/+question/120571](https://answers.launchpad.net/ubuntu/+source/util-linux/+question/120571)


Problem solved, thanks to peter b!!!

To summarize, reading (and writing) a floppy disk in Lucid Lynx (10.04) requires three steps:

1. Allow yourself to use the floppy by going to System->Administration->Users and Groups->Advanced Settings->User Privileges and click on "Use floppy drives"

2. Use the old version of udisks () by going to System->Administration->Synaptic Package Manager, find the udisks package, mark udisks for reinstallation, click on Package->Force Version, and select the 1.0.1-1build1 version (which is the old version). Then click on apply to finish the installation.

3. Remember to unclick udisks whenever Update Manager wants to install new updates, or you'll get the new version and floppy disks won't work anymore!

After the old udisks is installed (and the machine is rebooted), when you insert a floppy a cute little icon comes up on the desktop and in Nautilus (and on Disk Mounter if you have that installed). Left clicking on the icon and select Mount Floppy Disk will put an icon in Nautilus, and then you read, write, and format the floppy just like any other drive.

Thank you, peter b!!!

PS: Is this a bug???

Yes, the above does work.  No need for work around anymore.  Thanks for your nice step by step summary.   In my computer, I need to right click on the floppy icon in Nautilus and click detect media to mount it.

---

### Post by tbird6820 on 2010-09-15
> **cjv8888 said:**
> Yes, the above does work.  No need for work around anymore.  Thanks for your nice step by step summary.   In my computer, I need to right click on the floppy icon in Nautilus and click detect media to mount it.



I clicked on 
System->Administration->Users and Groups->Advanced Settings->User Privileges and click on "Use floppy drives"

went to
system->Administration->Synaptic Package Manager, find the udisks package, mark udisks for reinstallation, but I can't click on  reinstallation, see screen shot udisk 1.png

I tried  click on Package->Force Version, and select the 1.0.1-1build1 version but no change, see screen shot udisk 2.png

---

### Post by GOREMEISTER on 2010-09-15
Did you click on "Apply"?

---

### Post by GOREMEISTER on 2010-09-15
Where is the logic in allowing access to CDROM drives but not floppies? 

Shouldn't floppy access be allowed by default?

---

### Post by cjv8888 on 2010-09-15
> **tbird6820 said:**
> I clicked on 
System->Administration->Users and Groups->Advanced Settings->User Privileges and click on "Use floppy drives"

went to
system->Administration->Synaptic Package Manager, find the udisks package, mark udisks for reinstallation, but I can't click on  reinstallation, see screen shot udisk 1.png

I tried  click on Package->Force Version, and select the 1.0.1-1build1 version but no change, see screen shot udisk 2.png

You need to click the drop down to the right of the version and select the version 1.0.1-1build1 (without the lucid)

---

### Post by tbird6820 on 2010-09-15
> **GOREMEISTER said:**
> Did you click on "Apply"?



I hate it when that happens! sorry

Let me try this again.

went to
system->Administration->Synaptic Package Manager, find the udisks package, mark udisks for reinstallation.

click on Package->Force Version, and select the 1.0.1-1build1 version I get this window and click on  apply see screen shot udisk1.png 

than I get this window udisk2.png and close.

and I end up with this window see screen shot udisk3.png

close reboot go to places/computer and I see this screen shot floppy drive4.png. 

I insert a floppy disk that I checked and is good, right click on floppy,hit mount and I get this screen shot floppy drive5.png

 after 2mins. I get this window,  screen shot floppy drive6.png with floppy drive on desktop.

I close computer window and right click on floppy disk that is on desktop click on disk properties and I get this, screen shot floppy disk7.png

close floppy disk properties

right click on floppy disk on desktop, hit open, 40secs. later it opens

I tried to copy a text which is only 256MB and it took 2 mins and I got this screen shot floppy0 8.png


We are getting closer :D

---

### Post by GOREMEISTER on 2010-09-15
256MB or 256KB?

Unmount the floppy and then format the disk with System/Administration/Disk Utility. Choose "Format Volume" not "Format Disk". "Format Disk" does not work correctly.

Then remount and try copying a file again.

---

### Post by cjv8888 on 2010-09-15
May be the file is too big for the floppy or the the switch at the floppy is turned to write-protected?
Try another floppy or format it first before writing.

---

### Post by tbird6820 on 2010-09-15
The file said 256 bytes, not sure if MB or KB see 265bytes1.png.

I tried format drive and got this, see 265bytes1.png

---

### Post by GOREMEISTER on 2010-09-15
Can you format this floppy on a Windows PC?

Did you choose "Format Volume" instead of "Format Drive"?

---

### Post by plucky on 2010-09-16
To format a floppy from a terminal ```
sudo fdformat /dev/fd0
```

Then to create a filesystem ```
sudo mkfs.vfat /dev/fd0
``` or ```
sudo mkfs.msdos /dev/fd0
```

Then to mount the floppy ```
udisks --mount /dev/fd0
``` This is with 10.04 and the updated version of udisks.Also works in Maverick.


Good Luck

---

### Post by tbird6820 on 2010-09-16
I formatted this floppy on a Windows PC added some files see floppy.GIF

I mounted floppy and checked properties and got this, floppy disk properties.png

I tried to open and got this,floppy disk.png

I unmounted went to disk utility and there is no format volume see floppy drive1.png

I mounted went to disk utility and there is format volume so I formatted w/disk in using FAT see 
format drive2.png

this took about 30mins nothing is responding right.



Rebooted and I'll try the terminal

With the disk in,went to terminal sudo fdformat /dev/fd0 got this, terminal1.png

I stopped here.

---

### Post by cjv8888 on 2010-09-16
I think the floppy disc is faulty.

---

### Post by CEB2nd on 2010-09-16
> **GOREMEISTER said:**
> This works:

From - [https://answers.launchpad.net/ubuntu/+source/util-linux/+question/120571](https://answers.launchpad.net/ubuntu/+source/util-linux/+question/120571)


Problem solved, thanks to peter b!!!

To summarize, reading (and writing) a floppy disk in Lucid Lynx (10.04) requires three steps:

1. Allow yourself to use the floppy by going to System->Administration->Users and Groups->Advanced Settings->User Privileges and click on "Use floppy drives"

2. Use the old version of udisks () by going to System->Administration->Synaptic Package Manager, find the udisks package, mark udisks for reinstallation, click on Package->Force Version, and select the 1.0.1-1build1 version (which is the old version). Then click on apply to finish the installation.

3. Remember to unclick udisks whenever Update Manager wants to install new updates, or you'll get the new version and floppy disks won't work anymore!

After the old udisks is installed (and the machine is rebooted), when you insert a floppy a cute little icon comes up on the desktop and in Nautilus (and on Disk Mounter if you have that installed). Left clicking on the icon and select Mount Floppy Disk will put an icon in Nautilus, and then you read, write, and format the floppy just like any other drive.

Thank you, peter b!!!

PS: Is this a bug???

After you install the 1.0.1-1build1 version open Synaptic Package Manager again, click on udisks to highlight it, then package > lock version. This will prevent Update Manager from trying to install the new version again.

---

### Post by GOREMEISTER on 2010-09-17
Slight mod:


> **plucky said:**
> To format a floppy from a terminal ```
sudo fdformat /dev/fd0
```

If the file system is not recognized during the format
```
setfdprm -p /dev/fd0 1440/1440
```

Then to create a filesystem ```
sudo mkfs.vfat /dev/fd0
``` or ```
sudo mkfs.msdos /dev/fd0
```

Then to mount the floppy ```
udisks --mount /dev/fd0
``` This is with 10.04 and the updated version of udisks.Also works in Maverick.


Good Luck

---

### Post by dibuntux on 2011-01-14
I read all pages...disconcerting...

I can read previously formatted floppies, but cannot format them.

To copy files I have to use the terminal, becouse Nautilus says that I do not have permissions to write to the media, but I DO have them and directory is R/W to all...

I cannot believe this is such a mess for such a simple matter.

And even if it worked, the solution to downgrade a package is not acceptable in a LTS version.

Can we have an official solution from Canonical?
 TIA all

---

### Post by GOREMEISTER on 2011-01-21
Yes, please fix floppy support in Ubuntu!

I make a living off of working on $100K machines that still use DOS 6.22 and floppies. There are 400+ machines I must support and fighting with Ubuntu to format and mount floppies is disconcerting.

---

