---
title: "Restricted Access to USB drives"
date: 2010-05-15
forum: New to Ubuntu
---

### Post by AstroVision on 2010-05-15
When I upgraded from Ubuntu 9.10 to 10.04, my write access to my usb drive or flash drives just became non-existent.  It's driving me crazy!  The paste command is greyed out when I try copy a file from my main hd to the usb one.  When I try to drag and drop the file, this is the error message I get: 

Error while copying "boomarks-april5.html".
There was an error copying the file into /media/usb0.
Error opening file '/media/usb0/boomarks-april5.html': Permission denied.

Also, I noticed that when I plug my one drive in, two drives are coming are popping up.  For example, I plug in my ps3 backup drive and there are the two icons that pop up.  "usb0" and "PS3 Backup"  The weird thing is, the PS3 Backup, when I tried to double click on it, nothing happens.  The usb0 drives has all my ps3 backup files.

In Ubuntu 9.10 I didn't have this problem.  I don't know what it just happened.  Somebody please help me.

---

### Post by ayenack on 2010-05-15
I'll give you a quick answer so you can copy files onto the USB drive. I'll assume the path to your USB drive is /media/usb0 it may be different so make sure you use the correct path.

```
sudo mkdir /media/usb0/dropbox
``` (Where usb0 is your USB drive and dropbox is the foldr name you'll create.)

Then.

```
sudo chown your_user_name_here:your_user_name_here /media/usb0/dropbox
``` (Put your user name where I've put your_user_name_here.) 

You should now have a folder where you can put your files. You can also change the permissions of the other folders on the drive using chown in the same way.

For example if you have a folder on the drive called documents. You'd do this.

```
sudo chown your_user_name_here:your_user_name_here /media/usb0/documents
```

Not to sure about the PS3 drive so can't give any advice on that.

---

### Post by AstroVision on 2010-05-15
When I try to change the permission, it gives me this error message: 

chown: changing ownership of `/media/usb0/_Video': Operation not permitted

---

### Post by readycarpenter on 2010-05-15
you need to change permissions to allow read and write for your new user account. this can be easily done using nautilus

sudo nautilus

right click and goto properties on the directory you want to change.

and then all the permissions that were grayed out will not be, change the permissions and apply, viola 

cheers

---

### Post by ayenack on 2010-05-15
You need to make sure that you're using the correct path. Seems to me that you may not be.

Turn off or unplug all the USB drives that you do not want to make changes to and type this in terminal.

```
sudo fdisk -l
```

This will list all your drives. You need to pick the one that's your USb drive.

Also give me a bit more info on what you did. Did you create a new folder on the drive or are you trying to change ownership of a folder that already existed?

---

### Post by AstroVision on 2010-05-15
When I tried to change the restrictions from the root to my name, it says the following:

The owner could not be changed.
Sorry, could not change the owner of "_VIDEO": Error setting owner: Operation not permitted

Do I need to login as the root to change the permissions?  And if so, how do I login as the root.  In Ubuntu 9.10 all you had to do was create a user called root, and it you were good to go.  If I do that now in v10.04, it doesn't work...

---

### Post by AstroVision on 2010-05-15
All I want to do is copy or delete files from my USB drive.  I was able to do it before, I just don't understand why I can't now.  It's not isolated to that usb drive too.  I tried 2 gig flash disk, and it won't let me write to that either.

The weird thing that happened last week as well.  One day for no reason, it let me write to the drive.  Then the next day, after a reboot, I wasn't able to any longer...

---

### Post by ayenack on 2010-05-16
Did you create a new folder on the drive to write files to?

It's a strange folder name to have _VIDEO I'm wondering if this was a folder that already existed for some purpose.

Were you able to write to that folder before?

What is the drive formatted to ext3/4 NTFS?

As for the changing of permissions on the drive this has obviously got something to do with the upgrade. If you had the drive plugged in when you upgraded then the permissions may well have been changed.

It's possible to change permission of the whole drive but it's best not to do this.

---

### Post by ad delblade on 2010-05-16
Hallo,

I have a simular problem. 
Running Ubuntu 9.10.
My USB drive is a multimedia drive from dane elec 1 tera.
I am using that drive for over a year en wrote 700 gb with ubuntu 8.10 and 9.04. and that went well. But I think that after the last upgrade it changed.

I cant write to the drive, when I look at the permission it says its read/write. 
User name in property's is correct. All other disk and flash and sd and so on work fine.

When the drive is in Windows, even in virtual box I can write to is en change dirs.
But in Ubuntu it doesn't work.

Even tested  every USB port but that did nothing

Please help

---

### Post by ayenack on 2010-05-16
Hello ad delblade.

It's better if you start a new thread and ask for help as it gets confusing trying reply to two people at the same time. ;-)

You'll need to state what the drive is formated in ext3/4 FAT32 NTFS and give as much info as possible.

---

### Post by AstroVision on 2010-05-16
All the different USB drives I mount, won't allow for files to be deleted or copied onto itself.  My PS3 drive is formatted Fat32.  The others are NTSF.  I use the PS3 drive to watch videos that I get from my computer.

I just want to move a file onto the USB drive.  It's a basic procedure

When I log in as the root, I can copy files onto the drive... but it's waaayyy slower then my main account for some reason.  I'm just a little pissed off here... I don't want to have to do a fresh install or revert back to 9.10 because I don't want to loose my WindowsXP multi-boot.  

Also, I'm having problems with that damn black screen while it's booting.  I disabled the floppy drive, but that didn't help.  I just wish I would have stayed with 9.10... I've lost too many hours trying to solve this issue...

---

### Post by ayenack on 2010-05-17
Try this.

```
sudo apt-get install ntfs-config
```

Then:-
```
System -> Administration -> NTFS Configuration Tool
```

And see if you can config it.

As for the FAT32 drive there should not be a problem with this as FAT32 does not support permissions so can't help you with that.

---

### Post by ayenack on 2010-05-17
BTW. Did you create a new folder on the drive as I suggested in my earlier post?

---

### Post by AstroVision on 2010-06-11
Sorry guys for being MIA. I've been avoiding the problem because it enrages me so much...

I've tried both a FAT32 and NTSF drive.  They just won't allow me to copy or cut onto them.  When I was running Ubunto 9.10, there was no problem.

One thing that I noticed that changed when I installed version 10 was that when I plug in my usb drive, usb# (0,1,2... depending on how many I have plugged in) and the drive name appears in the file browser.   The drive name is just for show.  I can only click on the usb# to get access to the files on the drive. 

If we can't figure out the problem, I'm ready to just do a full fresh reinstall of 10.  If I do that, will I loose my multiboot with WindowsXP?  Do I have to do them both?

Cheers,
-R

---

### Post by AstroVision on 2010-06-11
And I tried everything you guys asked me to do.
I would like to avoid having to reinstall everything, if possible.

---

### Post by mikewhatever on 2010-06-11
Is the problem on all the drives is that the filesystem is owned by root? Why don't you connect some of them and post the output of the **mount** command.

---

### Post by AstroVision on 2010-06-12
Problem fixed!!!!
I backed up and re-formated all the drives that were giving me the issue.  Good thing for GParted and it's formatting capability! :D  Thanks for everyone that gave me help.

Cheers,
-R

---

### Post by AstroVision on 2010-06-16
The problem came back again.  It happened when I plugged my buddies NTSF drive in.  The other drives that I reformatted reverted back to the usb# problem too.  Never ending battle...  Not sure what else I can do.  Any other suggestions would be awesome!

Cheers,
-AV

---

### Post by anewguy on 2010-06-16
It's possible you are fighting a udev rule problem.  Try opening a terminal window, then copying a file manually using sudo, such as:

sudo cp file1onusbdrive newfileonusbdrive

*If* that works, we know things are being mounted via one of the default udev rules that results in them being mounted as owned by root.  I can give you a file to put in the udev rules if this works.

It's also possible there is something in fstab that is causing the mounting as root.

Dave ;)

---

### Post by jetcomputer on 2010-06-17
Hi, go to synaptic. If you have a usbmount installed, remove it from your system

---

### Post by AstroVision on 2010-06-19
Hi Dave,

Sorry, stupid question.  How do I navigate to the drive directory?  It starts me off in the user/desktop/ folder.  From there I don't know how to find to the usb drive.  I know it's located in the media folder.  But how to get there, that's another question.

Hi Jetcomputer,

I tried removing the mountusb from synaptic.  When I rebooted, the
drive says it cannot determine the user permissions.  So I can't copy anything to it.

Cheers,
-AV

---

### Post by Jonas thomas on 2010-06-19
Is this what you need?

> jonas@jonas5:~/Desktop$ cd /media
jonas@jonas5:/media$ ls
0AFD-2985  cdrom  cdrom0  cdrom1  floppy  floppy0  GADDIS_SOC_CSO_6CD
jonas@jonas5:/media$ cd 0AFD-2985


---

### Post by AstroVision on 2010-06-19
Thanks Jonas thomas. :)

Ok Dave, I made a duplicate file as you instructed. Now what do we do?

Cheers,
-AV

---

### Post by anewguy on 2010-06-19
> **AstroVision said:**
> Thanks Jonas thomas. :)

Ok Dave, I made a duplicate file as you instructed. Now what do we do?

Cheers,
-AV

So - I'm interpretting this to mean you could copy a file to the USB drive by sudo, just not as your default user.  That being the case, you can create a rule file which will be default make all USB devices read/write by all users, but it would be better to do it by device so as not to open the system up too much.  Therefore, please plug in each of your USB devices and do lsusb in a terminal for each, and post each output back here.  That way we can use the manufacturer and product ids to set a rule per device.

Post that info back and I'll post you the file contents, the name of the file, and the location of the file to create to make these new udev rules.

Dave ;)

---

### Post by anewguy on 2010-06-20
The following should get it working - it only allows access to USB devices by users in the "usbusers" group (I have you add root to the group because I'm not sure if the keyboard, mouse, printer, etc., would work otherwise).

In a terminal window (applications/accessories/terminal):

type:

sudo addgroup usbusers <press enter>

sudo adduser <your username here> usbusers <press enter>

sudo adduser root usbusers  <press enter>

sudo gedit /lib/udev/rules.d/100-local-permissions.rules <press enter>

This should call up the editor and the file shown should be empty.

Add the following to the file shown:

# USB access limited to users in usbusers group

SUBSYSTEMS=="usb" MODE:="0666" GROUP:="usbusers"

Save the file, exit the editor and close the terminal window.

Now plug in one of your USB flash drives (if external USB hard disk, you must unplug it and then plug it back in for the rule to affect it).

See if you can do what you want now and post back your results.


I also think I've seen this problem in the forum for a previous release, and I thought it was fixed through something in fstab, but I don't know what or how for that.

Dave ;)

---

### Post by anewguy on 2010-06-23
Did you ever get your USB devices working, and if so, how?  Posting that information back here, and marking the thread as "solved" via "Thread Tools" will help others having similar problems.

Dave ;)

---

### Post by AstroVision on 2010-06-25
Sorry Dave.
No it didn't work unfortunetly.  Trust me, if it worked I would have let everyone know. :)  
Is there anything I do to help with solving this issue?

---

### Post by AstroVision on 2010-07-03
Come on guys, I can't be the only one experiencing this problem?  

Having to reboot and boot to windows just to copy a file to a usb stick is kinda pathetic.  Being able to copy files is pretty essential.

---

### Post by rading on 2010-10-18
I'm having similar problems with copying files from any usb drives on my system. These issues also started after I upgraded to ubuntu 10.04, never had them earlier.

Anyone figured out how to fix this??

//edit...

Ok. So completely removing usbmount did the trick for me.

Thanks for that tip jet.

---

### Post by Handssolow on 2010-10-18
I've had both a problem with permissions which was solved then a few weeks later another problem mounting a USB sticks. It's ridiculous.

The first solution was to remove usbmount which solved the problem with permissions. When it wouldn't mount I installed PySDM Storage Device Manager which is fstab in gui form- so be careful. It's a sort of work round because sdb1 (my USB stick) shows up waiting to be mounted even when it's not yet plugged in.

My posts are #50 and #51

[http://ubuntuforums.org/showthread.php?t=1336847&page=5](http://ubuntuforums.org/showthread.php?t=1336847&page=5)

---

### Post by 4partee on 2012-08-25
The unanswered question is WHY is there Restricted Access to USB drives?!!  

WHY?WHY?WHY?WHY?WHY?WHY?WHY?WHY?

---

