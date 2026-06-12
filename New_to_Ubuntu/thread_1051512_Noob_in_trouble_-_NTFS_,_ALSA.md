---
title: "Noob in trouble - NTFS , ALSA"
date: 2009-01-26
forum: New to Ubuntu
---

### Post by ashwat on 2009-01-26
Hi all, 

My first post at the ubuntu forums. I shall describe in detail my baby steps with ubuntu. I made a clean swipe of the Windows7 HDD on my Vostro 1400 and installed Ubuntu 8.10. After some searching through forums, got the sound to work and installed Nvidia drivers as well. The trouble started when I tried to connect my NTFS formatted FreeAgent Drive. It gave the following error : 

> Unable to mount FreeAgent Drive 

$LogFile indicates unclean shutdown ( 0,0) Failed to mount '/dev/sdb1': Operation not supported Mount is denied because NTFS is marked to be in use. Choose one action : Choice 1: If you have Windows then disconnect the external devices by clicking on the Safely Remove Hardware icon in the Windows taskbar then shutdown Windows cleanly. Choice 2 : If you don't have Windows then you can use the 'force' option for your own responsibility. For example type on the command line : mount -t ntfs-3g /dec/sdb1 /media/FreeAgent Drive -o force Or add the option to the relevant row in the etc/fstab file :  /dev/sdb1 /media/FreeAgent Drive ntfs-3g force 0 0.

Recurring Error> 
DBus error org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

Since I had no Windows, I tried to enter the command. I hadn't yet discovered then that sudo was  required to run such commands. So I searched for unclean shutdown errors in the forum, only to stumble on this thread [http://ubuntuforums.org/showthread.php?t=971896&page=2]("http://ubuntuforums.org/showthread.php?t=971896&page=2")

I did as was described, only to find sound not working any more. I have since, undid the change to the alsa-utils but the problem persists. So right now I am without sound. 

Getting back to the Free Agent Drive, I entered the command in the terminal, with sudo prefix, only to see a description of the mount command. Using gedit, I trie to edit the fstab file in the following manner : 
> 
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/sdb1       /media/FreeAgent Drive, ntfs-3g force             0       0



The error generated was > Unable to mount the volume 'FreeAgent Drive' 
Details : 
[mntent]: line 10 in /etc/fstab is bad 
mount: can't find /media/FreeAgent in /etc/fstab or /etc/mtab

When I removed the space between Agent and Drive, the error was > You are not privileged to mount the volume 'FreeAgent Drive' 

Point is that the Recurring Error is one thing that pops up at every attempt to access the FreeAgent Drive from the places menu. 

Now people shoot away and help this first timer.

---

### Post by utnubuuser on 2009-01-26
Hmmm....   Maybe  Alt+F2  >>>then>> gksu  >>then>> nautilus  >>then try to access the hdd

Through gksu you enter nautilus with root user priviledge.

---

### Post by doctordruidphd on 2009-01-26
To use the mount command, I'm pretty sure you need to sudo:

sudo mount -t /dev/sdb1 /media/FreeAgentDrive

I use the following line in fstab for ntfs drives:

/dev/sdc1       /media/SDC1     ntfs    rw,user,umask=000       0       0

In spite of that, I don't think writing to ntfs drives is supported. If you want to read and write files, you will need to copy the stuff from the ntfs partitions to a FAT32 (vfat, as fstab calls it) partition, or an ext partition -- since you no longer have windows, probably no need to keep the stuff on ntfs or vfat.

Not quite sure what the sound problem is, though. Check the mixer and see if somehow 'mute' got checked, or some app turned the volume down (I've had that happen).

---

### Post by ashwat on 2009-01-27
> **utnubuuser said:**
> Hmmm....   Maybe  Alt+F2  >>>then>> gksu  >>then>> nautilus  >>then try to access the hdd

Through gksu you enter nautilus with root user priviledge.
It gives the same error as defined by the stab file edits that i have made.

---

### Post by ashwat on 2009-01-27
> **doctordruidphd said:**
> To use the mount command, I'm pretty sure you need to sudo:

sudo mount -t /dev/sdb1 /media/FreeAgentDrive

I use the following line in fstab for ntfs drives:

/dev/sdc1       /media/SDC1     ntfs    rw,user,umask=000       0       0

In spite of that, I don't think writing to ntfs drives is supported. If you want to read and write files, you will need to copy the stuff from the ntfs partitions to a FAT32 (vfat, as fstab calls it) partition, or an ext partition -- since you no longer have windows, probably no need to keep the stuff on ntfs or vfat.

Not quite sure what the sound problem is, though. Check the mixer and see if somehow 'mute' got checked, or some app turned the volume down (I've had that happen).
Using sudo in command prompt gives me details about how to use mount command. 

Using sdc edit in fstab, gave the following error msg:
> ntfs-3g: Failed to access volume '/dev/sdc1': No such file or directory
Please type '/sbin/mount.ntfs --help' for more information

The sounds back up again miraculously enough with no changes from my side. 

I am willing to convert my NTFS drive to ext even, but just want to keep my music. Any help on doing this would be greatly appreciated. 

I am someone who has delayed the shift to Open/FSF movement perennially up until now so I dont want to  lose faith so easily and go back to Windoze. Atleast not before I give this learning curve a good fight.

---

### Post by HittingSmoke on 2009-01-27
> In spite of that, I don't think writing to ntfs drives is supported. If you want to read and write files, you will need to copy the stuff from the ntfs partitions to a FAT32 (vfat, as fstab calls it) partition, or an ext partition -- since you no longer have windows, probably no need to keep the stuff on ntfs or vfat.

When I still had an NTFS drive running with my media after converting from Windows I had full read/write access without any additional packages so I think you are mistaken here.

> The sounds back up again miraculously enough with no changes from my side.

I am willing to convert my NTFS drive to ext even, but just want to keep my music. Any help on doing this would be greatly appreciated.

I am someone who has delayed the shift to Open/FSF movement perennially up until now so I dont want to lose faith so easily and go back to Windoze. Atleast not before I give this learning curve a good fight.

What I did here was sort of complicated, but worked. I moved as much off my NTFS drive as possible to a folder on my Ext3 drive then used a Gparted Live CD to shrink the NTFS volume as much as possible and repartition the newly freed space to Ext3.

I then copied all the files in the backup folder from the first transfer from the NTFS drive back to the newly created Ext3 partition. I did this again, copying as many files as possible to the original Ubuntu Ext3 drive from the NTFS volume then booting to Gparted and shrinking the NTFS volume once again and expanding the new Ext3 using the new free space.

You can do this as many times as needed to free up the space. Of course, the more space you have free on your Ubuntu install drive the faster and easier it will go.

I've tried to explain this best I can. I know it works because I've done it but it can be tricky and you've got to be very careful working with partitions that you want to preserve data from.

---

### Post by ashwat on 2009-01-27
I suppose I can do what you have described in detail, once I am able to mount the NTFS disk in the first place and access the data.

---

### Post by HittingSmoke on 2009-01-27
> **ashwat said:**
> I suppose I can do what you have described in detail, once I am able to mount the NTFS disk in the first place and access the data.

The error you're explaining happens when Windows isn't shut down properly. The problem here being, even when you shut down Windows "properly" it doesn't always, by definition, shut down "properly". Every time I've had this problem I've either just booted the drive and tried to shut down again or used the force command.

Is it possible to connect this HDD to a friend's computer who's running Windows and back up your data onto a portable drive? Or maybe get a windows PC set up temporarily just to get your data off the drive?

---

### Post by talsemgeest on 2009-01-27
Can you please post the output of ```
sudo fdisk -l
```

---

### Post by ashwat on 2009-02-13
> Can you please post the output of
Code:

sudo fdisk -l



> Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe8000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       13995   112414806   83  Linux
/dev/sda2           13996       14593     4803435    5  Extended
/dev/sda5           13996       14593     4803403+  82  Linux swap / Solaris

I have still not been able to mount the disk inspite of following all the advice been given here. I hope I am doing everything right?

---

### Post by egalvan on 2009-02-13
> **ashwat said:**
> I have still not been able to mount the disk inspite of following all the advice been given here. I hope I am doing everything right?

Go into Synaptic Package Manager and see if you have

ntfs-3g
ntfs-config

loaded.

If not, select them and install.

Run ntfs-cinfig. It's found under the *Applicatitions* > *System Tools* menu.

I just tried it and it automatically found an ntfs drive, and set it up inside fstab.


And a few more observations...

Spaces in the drive name (the label) will cause no end of grief under *nix. It's a Windows-thing (MS windows, that is).
I got rid of all spaces on my hard drive labels.
No more "work-arounds" for me, thank you very much.
For that matter, I got rid of capitals in my drive labels...

Next, using NTFS is not totally a bad thing...
it *does* help if you need to move the drive around to different computers, and some run XP.
Linux can and does read/write to NTFS with few problems.
As many others do, I don't think NTFS is as robust as ext2/ext3.

There is a ext2/3-type driver that runs under XP, but it has fallen behind the times with respect to large inodes, so it is problematic.

Good luck

ErnestG

---

### Post by gjoellee on 2009-02-13
Rea this page for how to mount NTFS in Ubuntu: [http://ubuntuforums.org/showthread.php?t=217009](http://ubuntuforums.org/showthread.php?t=217009)

---

### Post by egalvan on 2009-02-13
> **gjoellee said:**
> Rea this page for how to mount NTFS in Ubuntu: [http://ubuntuforums.org/showthread.php?t=217009](http://ubuntuforums.org/showthread.php?t=217009)

Be aware that post was written July 16th, 2006
and last edited  January 23rd, 2008 at 05:28 PM.


for example...


the post shows *** ntfs-3g is now RC1 :)**

Synpatic shows ntfs-3g is now  1:1.2506

---

### Post by ashwat on 2009-02-15
> **egalvan said:**
> Go into Synaptic Package Manager and see if you have

ntfs-3g
ntfs-config

loaded.

If not, select them and install.

Run ntfs-cinfig. It's found under the *Applicatitions* > *System Tools* menu.

I just tried it and it automatically found an ntfs drive, and set it up inside fstab.


And a few more observations...

Spaces in the drive name (the label) will cause no end of grief under *nix. It's a Windows-thing (MS windows, that is).
I got rid of all spaces on my hard drive labels.
No more "work-arounds" for me, thank you very much.
For that matter, I got rid of capitals in my drive labels...

Next, using NTFS is not totally a bad thing...
it *does* help if you need to move the drive around to different computers, and some run XP.
Linux can and does read/write to NTFS with few problems.
As many others do, I don't think NTFS is as robust as ext2/ext3.

There is a ext2/3-type driver that runs under XP, but it has fallen behind the times with respect to large inodes, so it is problematic.

Good luck

ErnestG
Renaming without spaces worked. Thanks one helluva lot :D my first successful community based solution. Now how do I rename this post as SOLVED?

---

