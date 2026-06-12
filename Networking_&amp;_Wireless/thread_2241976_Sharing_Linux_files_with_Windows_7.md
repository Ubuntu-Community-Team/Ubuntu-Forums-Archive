---
title: "Sharing Linux files with Windows 7"
date: 2014-08-29
forum: Networking &amp; Wireless
---

### Post by vbalbert on 2014-08-29
First, I'm a Linux newbie.  Assume I know all kinds of things about computers in general and am an expert at Windows, but Linux is still very much terra incognita.

Second, Samba seems rather complex and while I've looked up previous answers to this, I just don't understand enough to apply fixes properly.  So I'm asking for individualized treatment.

Finally, on to the problem:

I have a RAID installed on my Linux box which accesses the network just fine.  No problems with it at all in that area.  The RAID is up and going and I can do whatever I want with it on the Linux box.  The LInux box is to become a home theater PC once I get the file sharing sorted out.  It is far easier to do things on my Windows machine (not because it's Windows but because it's physically more convenient, not to mention that the Linux box has no optical drives at this time.)

I can see the Linux box on my Windows box, but when I try to access it I get, "Windows cannot access \\MEDIA_DRIVE.  Check the spelling of the name.  Otherwise, there might be a problem with your network.  To try to identify and resolve network problems, click Diagnose."  To reiterate, there is nothing wrong with my network.  I'm able to use DLNA to access video files on my Windows machine with my BD player (connected via WiFi), print from both the Linux machine and my Windows machine to the printer connected via WiFi, etc.  Both computers are connected via CAT5E cable to the 1 Gb router to maximize bandwidth.  So in other words, hardware is operating as designed, except an issue with the sound chip built into the Linux box that will be rectified with a new sound card.  (The problem is with Linux's support of the audio hardware, not with the hardware itself.  I just need supported audio hardware.)

I'm aware enough to understand that there is something in the smb.conf file that's not set properly.  I have used a graphical front-end (GADMIN-SAMBA) to edit the smb.conf file to make it easier to edit it, but I have no problem using gedit to edit specific lines in the file.

This is a fresh install of Linux.  Aside from installing the drivers for the RAID adapter (RocketRAID 622) and necessary updates, it's pretty much clean.  Just tell me what information you want (do you want the entire smb.conf file?) and I'll happily provide everything you require to help me resolve this issue.

Thank you in advance for your time and effort to helping me fix this.

---

### Post by dave131 on 2014-08-29
I don't know much about this at all, however I saw a thread last night where they asked the user to post 2 things (enclose in code tags):

testparm

your smb.conf file

Someone else will have to actually help you - I just saw the thread last night and I think they will ask for this.

---

### Post by vbalbert on 2014-08-29
That's good to know.  I'll post those immediately.  At least sneaker-net is still working.  Thanks! For whoever looks at these files, I simply added .txt to the end of the smb.conf file so I could upload it.

---

### Post by bab1 on 2014-08-29
> **vbalbert said:**
> That's good to know.  I'll post those immediately.  At least sneaker-net is still working.  Thanks! For whoever looks at these files, I simply added .txt to the end of the smb.conf file so I could upload it.

Do you have a copy of the default smb.conf file?  What version of Ubuntu are you using?

Using GADMIN-SAMBA is a big mistake.  GADMIN-SAMBA adds needless complexity to your setup.  It configures Samba incorrectly for what you most likely need.  

The first thing I would do is copy the default smb.conf file back to its original location (/etc/samba/smb.conf) and reboot Samba ```
sudo service smbd [COLOR="#0000FF"]restart[/COLOR]
```

Then see if you can see that machine form the others.  Post any errors.  By default you should at least be able to see the installed Samba server.

[COLOR="#0000FF"]Edit:  My bad.  I left out the ***restart*** at the end of the command to restart the Samba daemon.  :-( [/COLOR]

---

### Post by vbalbert on 2014-08-29
I'm using Ubuntu 14.04.1 LTS Desktop with all updates installed.

I do have the original smb.conf file and have copied it over the modified one.

Now when I double-click on the machine in Windows I don't get an error message, but I don't see anything in it.  In other words, my RAID isn't being shared.  This is actually more progress than I've ever gotten.

What now?

---

### Post by bab1 on 2014-08-29
> **vbalbert said:**
> I'm using Ubuntu 14.04.1 LTS Desktop with all updates installed.

I do have the original smb.conf file and have copied it over the modified one.

Now when I double-click on the machine in Windows I don't get an error message, but I don't see anything in it.  In other words, my RAID isn't being shared.  This is actually more progress than I've ever gotten.

What now?
Did you see my edit to my post?  To restart Samba.

The "the RAID" is pretty confusing because you do not share "the RAID".  You share directories stored on a partition that may or may not be part of RAID configured hard drives.

Before you do anything more, let's see if you have the right users added.  Have you added the user to the Linux machine?  The command ***getent passwd*** will show the users.  Have you added the user to the Samba user database?  The command ***sudo pdbedit -L*** will show the Samba users.

Post the output of both of those commands.

---

### Post by vbalbert on 2014-08-29
Yes, I did see the instruction to restart Samba.  I got an error message and a list of parameters so I just said the heck with it and restarted the machine.  That's where I was when I replied.  In fact, whereas originally the name of what I saw in Windows was Media_Drive, now I see the actual machine name, Kodi.  I have no problem with working with this name and, in fact, is actually preferable.

I have a folder on my RAID called Media.  I suspected that this might be necessary because Windows won't allow you to share the root folder of a drive.  But I don't see that folder.  I plan on mapping that folder to my Windows machine as a drive and working from there.

I have not added any users to the Linux machine.  I had considered this as a necessary step, but I wasn't sure what user was needed to be added.  I'm including the output of both commands here as file attachments.

---

### Post by bab1 on 2014-08-29
> **vbalbert said:**
> Yes, I did see the instruction to restart Samba.  I got an error message and a list of parameters so I just said the heck with it and restarted the machine.  That's where I was when I replied.  In fact, whereas originally the name of what I saw in Windows was Media_Drive, now I see the actual machine name, Kodi.  I have no problem with working with this name and, in fact, is actually preferable.

I have a folder on my RAID called Media.  I suspected that this might be necessary because Windows won't allow you to share the root folder of a drive.  But I don't see that folder.  I plan on mapping that folder to my Windows machine as a drive and working from there.

I have not added any users to the Linux machine.  I had considered this as a necessary step, but I wasn't sure what user was needed to be added.  I'm including the output of both commands here as file attachments.

I see that *vern-pc* is a Samba user but your user account ***vbalbert*** is not.  Let's add your user to the Samba database.  User your login password when it prompts you.  The command is```
sudo smbpasswd -a vbalbert
```

Post the output again of ```
sudo pdbedit -L
```

You can post this directly by copying the contents of the terminal and posting it here inside the code brackets provided when you click on the [SIZE=5]#[/SIZE] icon in the **advanced editor** that you use to respond.

Where is the partition (RAID) mounted?  Show me listing of the directories there.  The command is ```

ls -l /path/to/mount-point

```...where /path/to/mount-point is wherever the mount point is.

---

### Post by vbalbert on 2014-08-29
Here's the contents of pbedit:

```
vbalbert@Kodi:~$ sudo pdbedit -L
smbguest:1001:Samba guest account
vern-pc$:1003:Comment
root:0:root
vbalbert:1000:Vernon Balbert

```
And here is the ls output:
```
ls -l /media/vbalbert/a8a13b9a-120d-4bd6-8a60-0d1bcdb4fc73/
total 20
drwx------ 2 root     root     16384 Aug 29 13:20 lost+found
drwxrwxrwx 2 vbalbert vbalbert  4096 Aug 29 16:47 Media

```

---

### Post by bab1 on 2014-08-29
> **vbalbert said:**
> Here's the contents of pbedit:

```
vbalbert@Kodi:~$ sudo pdbedit -L
smbguest:1001:Samba guest account
vern-pc$:1003:Comment
root:0:root
vbalbert:1000:Vernon Balbert

```
And here is the ls output:
```
ls -l /media/vbalbert/a8a13b9a-120d-4bd6-8a60-0d1bcdb4fc73/
total 20
drwx------ 2 root     root     16384 Aug 29 13:20 lost+found
drwxrwxrwx 2 vbalbert vbalbert  4096 Aug 29 16:47 Media

```
I see you have added your user to the Samba database.  Great.  Later on if there are others that are going to use this Samba server just have to add them as a user to both Linux and Samba.
  
How did you mount this partition?  It looks like a USB attached device.  Are you just plugging it in and letting it auto-mount?  If so, you might use The GUI utility called *disks* disks to rename it.  I would not user Media as the name of a folder.  It is ambiguous and confusing.  I always start with the folder *samba* and add all the different shares off of that (i.e. samba/movies or samba/music or samba/pictures).  This will have nothing to do with the share names.  You'll see.

---

### Post by vbalbert on 2014-08-29
> **bab1 said:**
> I see you have added your user to the Samba database.  Great.  Later on if there are others that are going to use this Samba server just have to add them as a user to both Linux and Samba.
  
How did you mount this partition?  It looks like a USB attached device.  Are you just plugging it in and letting it auto-mount?  If so, you might use The GUI utility called *disks* disks to rename it.  I would not user Media as the name of a folder.  It is ambiguous and confusing.  I always start with the folder *samba* and add all the different shares off of that (i.e. samba/movies or samba/music or samba/pictures).  This will have nothing to do with the share names.  You'll see.

The partition was automatically mounted after it was created using GPARTED.  

Okay.  Right now names don't mean spit to me and so I'll change the name of the folder from Media to Samba.

Somewhere along the line I unmounted the drive.  Nautilus makes it far too easy to do this and I probably accidentally clicked the unmount button.  I don't see how to remount the RAID.

---

### Post by bab1 on 2014-08-29
> **vbalbert said:**
> The partition was automatically mounted after it was created using GPARTED.  

Okay.  Right now names don't mean spit to me and so I'll change the name of the folder from Media to Samba.

Somewhere along the line I unmounted the drive.  Nautilus makes it far too easy to do this and I probably accidentally clicked the unmount button.  I don't see how to remount the RAID.

What are you calling "the RAID"?  Do you have another partition (volume) that is based on multiple drives that is normally mounted somewhere?  If this volume listed in /etc/fstab and is normally mounted on booting up, you can just use this from the CLI to mount all the drives ```
sudo mount -a
```

---

### Post by vbalbert on 2014-08-29
> **bab1 said:**
> What are you calling "the RAID"?  Do you have another partition (volume) that is based on multiple drives that is normally mounted somewhere?  If this volume listed in /etc/fstab and is normally mounted on booting up, you can just use this from the CLI to mount all the drives ```
sudo mount -a
```

The RAID is a software RAID consisting of five 4 TB drives arranged in a RAID 5 configuration.  They are mounted in an exterior cabinet connected via a RAID adapter (RocketRAID 622.)  The RAID was created using mdadm.  It has a capacity of close to 16 TB.  (Yeah, there are going to be a LOT of media files on it.)

I rebooted and things are almost back to the way they were, but I somehow deleted the Samba folder and now I don't seem to have the permissions to create a folder there.  I did manage to rename it to Media_Drive so now LS gives:
```
 ls -l /media/vbalbert/Media_Drive/
total 16
drwx------ 2 root root 16384 Aug 29 18:50 lost+found

```
I do believe that I somehow screwed things up when I got the drive renamed.

---

### Post by bab1 on 2014-08-29
> **vbalbert said:**
> The RAID is a software RAID consisting of five 4 TB drives arranged in a RAID 5 configuration.  They are mounted in an exterior cabinet connected via a RAID adapter (RocketRAID 622.)  The RAID was created using mdadm.  It has a capacity of close to 16 TB.  (Yeah, there are going to be a LOT of media files on it.)

I rebooted and things are almost back to the way they were, but I somehow deleted the Samba folder and now I don't seem to have the permissions to create a folder there.  I did manage to rename it to Media_Drive so now LS gives:
```
 ls -l /media/vbalbert/Media_Drive/
total 16
drwx------ 2 root root 16384 Aug 29 18:50 lost+found

```
I do believe that I somehow screwed things up when I got the drive renamed.

It sounds like you are just using the RocketRAID 622 as an external SATA connector if you are using mdam RAID software.  Post the output of these two commands then I will tell you what we have```

cat /etc/fstab

sudo blkid -c /dev/null -o list

```

---

### Post by vbalbert on 2014-08-29
> **bab1 said:**
> It sounds like you are just using the RocketRAID 622 as an external SATA connector if you are using mdam RAID software.  Post the output of these two commands then I will tell you what we have```

cat /etc/fstab

sudo blkid -c /dev/null -o list

```

Using the RocketRAID is pretty much as you say, but because of the hardware architecture, it's the only way to do it.

```
cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
/dev/mapper/ubuntu--vg-root /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda1 during installation
UUID=461f1778-a28e-47f1-bb1b-f81186233f39 /boot           ext2    defaults        0       2
/dev/mapper/ubuntu--vg-swap_1 none            swap    sw              0       0

```
```
device     fs_type label    mount point    UUID
-------------------------------------------------------------------------------
/dev/sda1  ext2             /boot          461f1778-a28e-47f1-bb1b-f81186233f39
/dev/sda5  LVM2_member      (in use)       XfEFaa-cYcZ-8cgh-RV1P-qcaS-FhvT-5sRCOV
/dev/mapper/ubuntu--vg-root
           ext4             /              96d0154f-6f9f-4565-9859-87af562d4cd7
/dev/mapper/ubuntu--vg-swap_1
           swap             <swap>         b9cb383b-7a05-4c93-9dc0-57f9c2a83036
/dev/sdb   linux_raid_member Kodi:0 (in use) 4cd5e788-9a49-fcda-91ff-cc5c1146d1df
/dev/sdc   linux_raid_member Kodi:0 (in use) 4cd5e788-9a49-fcda-91ff-cc5c1146d1df
/dev/sdd   linux_raid_member Kodi:0 (in use) 4cd5e788-9a49-fcda-91ff-cc5c1146d1df
/dev/sde   linux_raid_member Kodi:0 (in use) 4cd5e788-9a49-fcda-91ff-cc5c1146d1df
/dev/sdf   linux_raid_member Kodi:0 (in use) 4cd5e788-9a49-fcda-91ff-cc5c1146d1df
/dev/md0p1 ext4    Media_Drive /media/vbalbert/Media_Drive 467d816b-778f-490c-9e68-53a760fa6936

```

---

### Post by bab1 on 2014-08-29
> **vbalbert said:**
> Using the RocketRAID is pretty much as you say, but because of the hardware architecture, it's the only way to do it.

```
cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
/dev/mapper/ubuntu--vg-root /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda1 during installation
UUID=461f1778-a28e-47f1-bb1b-f81186233f39 /boot           ext2    defaults        0       2
/dev/mapper/ubuntu--vg-swap_1 none            swap    sw              0       0

```


```
device     fs_type label    mount point    UUID
-------------------------------------------------------------------------------
/dev/sda1  ext2             /boot          461f1778-a28e-47f1-bb1b-f81186233f39
/dev/sda5  LVM2_member      (in use)       XfEFaa-cYcZ-8cgh-RV1P-qcaS-FhvT-5sRCOV
/dev/mapper/ubuntu--vg-root
           ext4             /              96d0154f-6f9f-4565-9859-87af562d4cd7
/dev/mapper/ubuntu--vg-swap_1
           swap             <swap>         b9cb383b-7a05-4c93-9dc0-57f9c2a83036
/dev/sdb   linux_raid_member Kodi:0 (in use) 4cd5e788-9a49-fcda-91ff-cc5c1146d1df
/dev/sdc   linux_raid_member Kodi:0 (in use) 4cd5e788-9a49-fcda-91ff-cc5c1146d1df
/dev/sdd   linux_raid_member Kodi:0 (in use) 4cd5e788-9a49-fcda-91ff-cc5c1146d1df
/dev/sde   linux_raid_member Kodi:0 (in use) 4cd5e788-9a49-fcda-91ff-cc5c1146d1df
/dev/sdf   linux_raid_member Kodi:0 (in use) 4cd5e788-9a49-fcda-91ff-cc5c1146d1df
/dev/md0p1 ext4    [COLOR="#008000"]**Media_Drive /media/vbalbert/Media_Drive 467**[/COLOR][COLOR="#0000FF"]d816b-778f-490c-9e68-53a760fa6936[/COLOR]

```
Pretty interesting partition scheme.  The only thing we are really interested in is the last line I highlighted in green and blue.

The USB drive is not attached or is physically off.  Maybe from what you said.  You can always disconnect it, reboot the machine and the re-attach it.

The raid volume can be easily mounted at boot time if we want to do that.  We can mount it anywhere in the file system,  Is this all of this volume going to be shared?  As multiple shares or as one BIG share?

---

### Post by vbalbert on 2014-08-29
> **bab1 said:**
> Pretty interesting partition scheme.  The only thing we are really interested in is the last line I highlighted in green and blue.

The USB drive is not attached or is physically off.  Maybe from what you said.  You can always disconnect it, reboot the machine and the re-attach it.

The raid volume can be easily mounted at boot time if we want to do that.  We can mount it anywhere in the file system,  Is this all of this volume going to be shared?  As multiple shares or as one BIG share?

The USB drive is a 16 GB flash drive used to install the OS and transfer files via sneaker-net.  It's pretty irrelevant to the system.  I haven't had any problems with it.

The entire RAID will be used to hold the media files for the system.  That's its only intended purpose.  It will be used as one big share.  Otherwise I wouldn't have bothered to create a RAID and just use it as a JBOD setup.  I wanted some level of redundancy to prevent data loss which is why I set it up as RAID 5.  With as many files as it will hold, I wanted some form of security in case a drive failed.  It does get mounted automatically at boot time.  On the Linux box, I can't seem to make changes to it with the default account (vbalbert) and while I can see the drive on the Windows box, I can't access it at all.

---

### Post by bab1 on 2014-08-30
> **vbalbert said:**
> The USB drive is a 16 GB flash drive used to install the OS and transfer files via sneaker-net.  It's pretty irrelevant to the system.  I haven't had any problems with it.

The entire RAID will be used to hold the media files for the system.  That's its only intended purpose.  It will be used as one big share.  Otherwise I wouldn't have bothered to create a RAID and just use it as a JBOD setup.  I wanted some level of redundancy to prevent data loss which is why I set it up as RAID 5.  With as many files as it will hold, I wanted some form of security in case a drive failed.  It does get mounted automatically at boot time.  On the Linux box, I can't seem to make changes to it with the default account (vbalbert) and while I can see the drive on the Windows box, I can't access it at all.
It is not mounted via the Linux *mount command*.  Instead it relies on the udev discovery system.  This most likely will cause problems down the road.  It's just not reliable enough for what you want to do.  As it's always going to be mounted at boot time then I would add it to the /etc/fstab and mount it at a different location.  I mount my samba shared partition at /srv/samba.  It looks like this```
/[COLOR="#0000FF"]dev/sda1[/COLOR]             8.4G  2.5G  5.5G  32% /
[COLOR="#0000FF"]/dev/sda3  [/COLOR]           9.3G  230M  8.9G   3% /home
[COLOR="#0000FF"]/dev/sda4 [/COLOR]             93G   47G   46G  51% /data
[COLOR="#FF0000"]/dev/sdb1[/COLOR]             917G  231G  686G  26% /srv/samba

```

See how the device is sdb (red) instead of sda (blue) which has the booting directory.

You should always be able to set the user ownership of the files and directories using sudo.  When we make the directories I will explain
The proper place to mount the 16 TB partition is at /srv  Then we will deal with sharing a directory.

One comment about RAID and redundancy.  There is no redundancy or safety with a 16TB RAID arrangement.  You need to have a robust backup scheme set up to have an alternative repository of all the data on these drives.  RAID used on this large a setup has a high rate of failure when trying to rebuild the array.  I'm not going to tell you you shouldn't do it, but I will tell you it is old technology and is really for arrays that were built with 500GB drives.  It was more for hi-availability systems rather than data protection.

Here is what I would start with.  Make a directory at /srv for the samba share with this command```
sudo mkdir -p /srv/samba
```
Post the output of this command```
ls -l /srv
```

Next we will mount the 16TB at this mount point as soon as I see that the mount point is available.

---

### Post by vbalbert on 2014-08-30
> **bab1 said:**
> It is not mounted via the Linux *mount command*.  Instead it relies on the udev discovery system.  This most likely will cause problems down the road.  It's just not reliable enough for what you want to do.  As it's always going to be mounted at boot time then I would add it to the /etc/fstab and mount it at a different location.  I mount my samba shared partition at /srv/samba.  It looks like this```
/[COLOR="#0000FF"]dev/sda1[/COLOR]             8.4G  2.5G  5.5G  32% /
[COLOR="#0000FF"]/dev/sda3  [/COLOR]           9.3G  230M  8.9G   3% /home
[COLOR="#0000FF"]/dev/sda4 [/COLOR]             93G   47G   46G  51% /data
[COLOR="#FF0000"]/dev/sdb1[/COLOR]             917G  231G  686G  26% /srv/samba

```

See how the device is sdb (red) instead of sda (blue) which has the booting directory.

You should always be able to set the user ownership of the files and directories using sudo.  When we make the directories I will explain
The proper place to mount the 16 TB partition is at /srv  Then we will deal with sharing a directory.

One comment about RAID and redundancy.  There is no redundancy or safety with a 16TB RAID arrangement.  You need to have a robust backup scheme set up to have an alternative repository of all the data on these drives.  RAID used on this large a setup has a high rate of failure when trying to rebuild the array.  I'm not going to tell you you shouldn't do it, but I will tell you it is old technology and is really for arrays that were built with 500GB drives.  It was more for hi-availability systems rather than data protection.

Here is what I would start with.  Make a directory at /srv for the samba share with this command```
sudo mkdir -p /srv/samba
```
Post the output of this command```
ls -l /srv
```

Next we will mount the 16TB at this mount point as soon as I see that the mount point is available.

I realize that no RAID is going to be 100% secure from data loss, but it does offer me the ability to rebuild a drive if it fails.  It's not as good as a backup, but it's better than nothing.  Most of the data is already on DVDs and so if all else fails, I can restore what I need to.  It's just more time consuming.

sda is my boot drive, a 250 GB drive as well.  It's also for the programs that I'll be running.  Since this is going to be a dedicated HTPC I'm not going to put a lot of software on it.

```
 ls -l /srv
total 4
drwxr-xr-x 2 root root 4096 Aug 29 21:48 samba

```

---

### Post by bab1 on 2014-08-30
> **vbalbert said:**
> I realize that no RAID is going to be 100% secure from data loss, but it does offer me the ability to rebuild a drive if it fails.  It's not as good as a backup, but it's better than nothing.  Most of the data is already on DVDs and so if all else fails, I can restore what I need to.  It's just more time consuming.

sda is my boot drive, a 250 GB drive as well.  It's also for the programs that I'll be running.  Since this is going to be a dedicated HTPC I'm not going to put a lot of software on it.

```
 ls -l /srv
total 4
drwxr-xr-x 2 root root 4096 Aug 29 21:48 samba

```

Add the following to the bottom of the /etc/fstab file.  ```
#  This is the 16TB RAID enabled partition for all my media
UUID=d816b-778f-490c-9e68-53a760fa6936	/srv/samba  ext4  defaults  0 0
```...the first line is a comment so you know what you did later on.  ;-)

You should be able to do this by opening the fstab and add the above to the bottom of the file with this command ```
pkexec gedit /etc/fstab
```
After you have added the 2 lines you should reboot the entire machine.  Once the machine is up do the following commands and post the output ```
df -h

cat /etc/fstab

sudo blkid -c /dev/null -o list

ls -l /srv/samba


```

---

### Post by vbalbert on 2014-08-30
> **bab1 said:**
> Add the following to the bottom of the /etc/fstab file.  ```
#  This is the 16TB RAID enabled partition for all my media
UUID=d816b-778f-490c-9e68-53a760fa6936	/srv/samba  ext4  defaults  0 0
```...the first line is a comment so you know what you did later on.  ;-)

You should be able to do this by opening the fstab and add the above to the bottom of the file with this command ```
pkexec gedit /etc/fstab
```
After you have added the 2 lines you should reboot the entire machine.  Once the machine is up do the following commands and post the output ```
df -h

cat /etc/fstab

sudo blkid -c /dev/null -o list

ls -l /srv/samba


```

When I tried to use the pkexec line I got an error:
```
pkexec gedit /etc/fstab
error: XDG_RUNTIME_DIR not set in the environment.

(gedit:2891): Gtk-WARNING **: cannot open display: 

```

So I used sudo gedit fstab to edit the file.

I added the code to fstab as you instructed (using copy and paste rather than relying on typing) and when I rebooted I got an error message saying that the drive was not mounted and offered to let me wait, skip things or issue commands.  I waited for a bit, but nothing happened (I may have been impatient) and then hit S for skip.

Now for the results of the commands:

```
df -h
Filesystem                   Size  Used Avail Use% Mounted on
/dev/mapper/ubuntu--vg-root  222G  4.9G  205G   3% /
none                         4.0K     0  4.0K   0% /sys/fs/cgroup
udev                         3.9G  8.0K  3.9G   1% /dev
tmpfs                        787M  1.4M  786M   1% /run
none                         5.0M     0  5.0M   0% /run/lock
none                         3.9G   19M  3.9G   1% /run/shm
none                         100M   32K  100M   1% /run/user
/dev/sda1                    236M  115M  109M  52% /boot

```
```
cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
/dev/mapper/ubuntu--vg-root /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda1 during installation
UUID=461f1778-a28e-47f1-bb1b-f81186233f39 /boot           ext2    defaults        0       2
/dev/mapper/ubuntu--vg-swap_1 none            swap    sw              0       0
#  This is the 16TB RAID enabled partition for all my media
UUID=d816b-778f-490c-9e68-53a760fa6936	/srv/samba  ext4  defaults  0 0

```
```
sudo blkid -c /dev/null -o list
[sudo] password for vbalbert: 
device     fs_type label    mount point    UUID
-------------------------------------------------------------------------------
/dev/sda1  ext2             /boot          461f1778-a28e-47f1-bb1b-f81186233f39
/dev/sda5  LVM2_member      (in use)       XfEFaa-cYcZ-8cgh-RV1P-qcaS-FhvT-5sRCOV
/dev/mapper/ubuntu--vg-root
           ext4             /              96d0154f-6f9f-4565-9859-87af562d4cd7
/dev/mapper/ubuntu--vg-swap_1
           swap             <swap>         b9cb383b-7a05-4c93-9dc0-57f9c2a83036
/dev/sdb   linux_raid_member Kodi:0 (in use) 4cd5e788-9a49-fcda-91ff-cc5c1146d1df
/dev/sdc   linux_raid_member Kodi:0 (in use) 4cd5e788-9a49-fcda-91ff-cc5c1146d1df
/dev/sdd   linux_raid_member Kodi:0 (in use) 4cd5e788-9a49-fcda-91ff-cc5c1146d1df
/dev/sde   linux_raid_member Kodi:0 (in use) 4cd5e788-9a49-fcda-91ff-cc5c1146d1df
/dev/sdf   linux_raid_member Kodi:0 (in use) 4cd5e788-9a49-fcda-91ff-cc5c1146d1df
/dev/md0p1 ext4    Media_Drive (not mounted) 467d816b-778f-490c-9e68-53a760fa6936

```
```
ls -l /srv/samba
total 0

```

I'm going to try another boot and see if waiting longer does anything.  FWIW, I have drive indicator lights for each drive in the external box so I can see if there's any activity.  The drive lights go out and then come back on when the RAID is seen by the OS so I could see the drivers loaded but no drive activity was present.

---

### Post by bab1 on 2014-08-30
> **vbalbert said:**
> When I tried to use the pkexec line I got an error:
```
pkexec gedit /etc/fstab
error: XDG_RUNTIME_DIR not set in the environment.

(gedit:2891): Gtk-WARNING **: cannot open display: 

```

So I used sudo gedit fstab to edit the file.

I added the code to fstab as you instructed (using copy and paste rather than relying on typing) and when I rebooted I got an error message saying that the drive was not mounted and offered to let me wait, skip things or issue commands.  I waited for a bit, but nothing happened (I may have been impatient) and then hit S for skip.

Now for the results of the commands:

```
df -h
Filesystem                   Size  Used Avail Use% Mounted on
/dev/mapper/ubuntu--vg-root  222G  4.9G  205G   3% /
none                         4.0K     0  4.0K   0% /sys/fs/cgroup
udev                         3.9G  8.0K  3.9G   1% /dev
tmpfs                        787M  1.4M  786M   1% /run
none                         5.0M     0  5.0M   0% /run/lock
none                         3.9G   19M  3.9G   1% /run/shm
none                         100M   32K  100M   1% /run/user
/dev/sda1                    236M  115M  109M  52% /boot

```
```
cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
/dev/mapper/ubuntu--vg-root /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda1 during installation
UUID=461f1778-a28e-47f1-bb1b-f81186233f39 /boot           ext2    defaults        0       2
/dev/mapper/ubuntu--vg-swap_1 none            swap    sw              0       0
#  This is the 16TB RAID enabled partition for all my media
UUID=d816b-778f-490c-9e68-53a760fa6936	/srv/samba  ext4  defaults  0 0

```
```
sudo blkid -c /dev/null -o list
[sudo] password for vbalbert: 
device     fs_type label    mount point    UUID
-------------------------------------------------------------------------------
/dev/sda1  ext2             /boot          461f1778-a28e-47f1-bb1b-f81186233f39
/dev/sda5  LVM2_member      (in use)       XfEFaa-cYcZ-8cgh-RV1P-qcaS-FhvT-5sRCOV
/dev/mapper/ubuntu--vg-root
           ext4             /              96d0154f-6f9f-4565-9859-87af562d4cd7
/dev/mapper/ubuntu--vg-swap_1
           swap             <swap>         b9cb383b-7a05-4c93-9dc0-57f9c2a83036
/dev/sdb   linux_raid_member Kodi:0 (in use) 4cd5e788-9a49-fcda-91ff-cc5c1146d1df
/dev/sdc   linux_raid_member Kodi:0 (in use) 4cd5e788-9a49-fcda-91ff-cc5c1146d1df
/dev/sdd   linux_raid_member Kodi:0 (in use) 4cd5e788-9a49-fcda-91ff-cc5c1146d1df
/dev/sde   linux_raid_member Kodi:0 (in use) 4cd5e788-9a49-fcda-91ff-cc5c1146d1df
/dev/sdf   linux_raid_member Kodi:0 (in use) 4cd5e788-9a49-fcda-91ff-cc5c1146d1df
/dev/md0p1 ext4    Media_Drive (not mounted) 467d816b-778f-490c-9e68-53a760fa6936

```
```
ls -l /srv/samba
total 0

```

I'm going to try another boot and see if waiting longer does anything.  FWIW, I have drive indicator lights for each drive in the external box so I can see if there's any activity.  The drive lights go out and then come back on when the RAID is seen by the OS so I could see the drivers loaded but no drive activity was present.
My bad cut and paste.  The lines should have been this```

#  This is the 16TB RAID enabled partition for all my media
UUID=467d816b-778f-490c-9e68-53a760fa6936	/srv/samba  ext4  defaults  0 0


```
Please run all the tests (commands).  There is no need to wait.  if it fails, then it is not going to help to wait.

[COLOR="#0000FF"]Edit:  pkexec is the new way of calling gksu.  Your machine should have used that with no errors.  What version of Ubuntu are you using again?  Is this a server addition that you added the desktop to it?[/COLOR]

---

### Post by vbalbert on 2014-08-30
> **bab1 said:**
> My bad cut and paste.  The lines should have been this```

#  This is the 16TB RAID enabled partition for all my media
UUID=467d816b-778f-490c-9e68-53a760fa6936	/srv/samba  ext4  defaults  0 0


```
Please run all the tests (commands).  There is no need to wait.  if it fails, then it is not going to help to wait.

[COLOR="#0000FF"]Edit:  pkexec is the new way of calling gksu.  Your machine should have used that with no errors.  What version of Ubuntu are you using again?  Is this a server addition that you added the desktop to it?[/COLOR]

I'm using Ubuntu 14.04 64-bit desktop (the latest available as of yesterday) and I have not added any server additions that I know of.  The only things I have added were GPARTED, GADMIN-SAMBA which I stopped using per your instructions, Samba which wasn't installed by default and Google Chrome, my preferred browser.  I also had to install dkms so that I could get the RAID drivers to compile properly.  Also, all updates were installed as of today.  Based on the error message an environment variable seems not to be set properly.  It doesn't seem to make a difference since sudo works perfectly well.  Right now that's the least of my problems.

I replaced the code in fstab with your new corrections and I booted up just fine.  Here are the test results:
```
df -h
Filesystem                   Size  Used Avail Use% Mounted on
/dev/mapper/ubuntu--vg-root  222G  4.9G  205G   3% /
none                         4.0K     0  4.0K   0% /sys/fs/cgroup
udev                         3.9G   12K  3.9G   1% /dev
tmpfs                        787M  1.4M  786M   1% /run
none                         5.0M     0  5.0M   0% /run/lock
none                         3.9G   20M  3.9G   1% /run/shm
none                         100M   32K  100M   1% /run/user
/dev/sda1                    236M  115M  109M  52% /boot
/dev/md0p1                    15T  9.1M   14T   1% /srv/samba

```
```
cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
/dev/mapper/ubuntu--vg-root /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda1 during installation
UUID=461f1778-a28e-47f1-bb1b-f81186233f39 /boot           ext2    defaults        0       2
/dev/mapper/ubuntu--vg-swap_1 none            swap    sw              0       0
#  This is the 16TB RAID enabled partition for all my media
UUID=467d816b-778f-490c-9e68-53a760fa6936	/srv/samba  ext4  defaults  0 0

```
```
sudo blkid -c /dev/null -o list
[sudo] password for vbalbert: 
device     fs_type label    mount point    UUID
-------------------------------------------------------------------------------
/dev/sda1  ext2             /boot          461f1778-a28e-47f1-bb1b-f81186233f39
/dev/sda5  LVM2_member      (in use)       XfEFaa-cYcZ-8cgh-RV1P-qcaS-FhvT-5sRCOV
/dev/mapper/ubuntu--vg-root
           ext4             /              96d0154f-6f9f-4565-9859-87af562d4cd7
/dev/mapper/ubuntu--vg-swap_1
           swap             <swap>         b9cb383b-7a05-4c93-9dc0-57f9c2a83036
/dev/sdb   linux_raid_member Kodi:0 (in use) 4cd5e788-9a49-fcda-91ff-cc5c1146d1df
/dev/sdc   linux_raid_member Kodi:0 (in use) 4cd5e788-9a49-fcda-91ff-cc5c1146d1df
/dev/sdd   linux_raid_member Kodi:0 (in use) 4cd5e788-9a49-fcda-91ff-cc5c1146d1df
/dev/sde   linux_raid_member Kodi:0 (in use) 4cd5e788-9a49-fcda-91ff-cc5c1146d1df
/dev/sdf   linux_raid_member Kodi:0 (in use) 4cd5e788-9a49-fcda-91ff-cc5c1146d1df
/dev/md0p1 ext4    Media_Drive /srv/samba  467d816b-778f-490c-9e68-53a760fa6936

```
```
ls -l /srv/samba
total 16
drwx------ 2 root root 16384 Aug 29 18:50 lost+found

```

---

### Post by bab1 on 2014-08-30
> **vbalbert said:**
> I'm using Ubuntu 14.04 64-bit desktop (the latest available as of yesterday) and I have not added any server additions that I know of.  The only things I have added were GPARTED, GADMIN-SAMBA which I stopped using per your instructions, Samba which wasn't installed by default and Google Chrome, my preferred browser.  I also had to install dkms so that I could get the RAID drivers to compile properly.  Also, all updates were installed as of today.  Based on the error message an environment variable seems not to be set properly.  It doesn't seem to make a difference since sudo works perfectly well.  Right now that's the least of my problems.

I replaced the code in fstab with your new corrections and I booted up just fine.  Here are the test results:
```
df -h
Filesystem                   Size  Used Avail Use% Mounted on
/dev/mapper/ubuntu--vg-root  222G  4.9G  205G   3% /
none                         4.0K     0  4.0K   0% /sys/fs/cgroup
udev                         3.9G   12K  3.9G   1% /dev
tmpfs                        787M  1.4M  786M   1% /run
none                         5.0M     0  5.0M   0% /run/lock
none                         3.9G   20M  3.9G   1% /run/shm
none                         100M   32K  100M   1% /run/user
/dev/sda1                    236M  115M  109M  52% /boot
/dev/md0p1                    15T  9.1M   14T   1% /srv/samba

```
```
cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
/dev/mapper/ubuntu--vg-root /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda1 during installation
UUID=461f1778-a28e-47f1-bb1b-f81186233f39 /boot           ext2    defaults        0       2
/dev/mapper/ubuntu--vg-swap_1 none            swap    sw              0       0
#  This is the 16TB RAID enabled partition for all my media
UUID=467d816b-778f-490c-9e68-53a760fa6936	/srv/samba  ext4  defaults  0 0

```
```
sudo blkid -c /dev/null -o list
[sudo] password for vbalbert: 
device     fs_type label    mount point    UUID
-------------------------------------------------------------------------------
/dev/sda1  ext2             /boot          461f1778-a28e-47f1-bb1b-f81186233f39
/dev/sda5  LVM2_member      (in use)       XfEFaa-cYcZ-8cgh-RV1P-qcaS-FhvT-5sRCOV
/dev/mapper/ubuntu--vg-root
           ext4             /              96d0154f-6f9f-4565-9859-87af562d4cd7
/dev/mapper/ubuntu--vg-swap_1
           swap             <swap>         b9cb383b-7a05-4c93-9dc0-57f9c2a83036
/dev/sdb   linux_raid_member Kodi:0 (in use) 4cd5e788-9a49-fcda-91ff-cc5c1146d1df
/dev/sdc   linux_raid_member Kodi:0 (in use) 4cd5e788-9a49-fcda-91ff-cc5c1146d1df
/dev/sdd   linux_raid_member Kodi:0 (in use) 4cd5e788-9a49-fcda-91ff-cc5c1146d1df
/dev/sde   linux_raid_member Kodi:0 (in use) 4cd5e788-9a49-fcda-91ff-cc5c1146d1df
/dev/sdf   linux_raid_member Kodi:0 (in use) 4cd5e788-9a49-fcda-91ff-cc5c1146d1df
/dev/md0p1 ext4    Media_Drive /srv/samba  467d816b-778f-490c-9e68-53a760fa6936

```
```
ls -l /srv/samba
total 16
drwx------ 2 root root 16384 Aug 29 18:50 lost+found

```


Let's make a simple share.  I think you should share a directory below the /srv/samba directory for a test.  So let's to this to make a test share

```
sudo mkdir -p /srv/samba/test
```

Now you need to change the owner and group to you with this```

sudo chown vbalbert:vbalbert /srv/samba/test

```

Now we make the share.  We will edit the smb.conf file like this```
sudo gedit /etc/samba/smb.conf
```

At the bottom of this file add this```

[test]
        comment = A Test Share
        path = /srv/samba/test
        browseable = yes
       force group = vbalbert


```

Restart Samba with this and see if you can see the share```
sudo service smbd restart
```

---

### Post by vbalbert on 2014-08-30
> **bab1 said:**
> Let's make a simple share.  I think you should share a directory below the /srv/samba directory for a test.  So let's to this to make a test share

```
sudo mkdir -p /srv/samba/test
```

Now you need to change the owner and group to you with this```

sudo chown vbalbert:vbalbert /srv/samba/test

```

Now we make the share.  We will edit the smb.conf file like this```
sudo gedit /etc/samba/smb.conf
```

At the bottom of this file add this```

[test]
        comment = A Test Share
        path = /srv/samba/test
        browseable = yes
       force group = vbalbert


```

Restart Samba with this and see if you can see the share```
sudo service smbd restart
```

I see the test folder but now it's asking me for a username and password.  I'm not sure what those are supposed to be.  I tried vbalbert and the password, but that didn't work.  We're making progress!

BTW, you have been displaying remarkable patience in dealing with me and helping me get this going.  You are awesome.  I thought you should know that.

---

### Post by bab1 on 2014-08-30
> **vbalbert said:**
> I see the test folder but now it's asking me for a username and password.  I'm not sure what those are supposed to be.  I tried vbalbert and the password, but that didn't work.  We're making progress!

This should be the user vbalbert and that user's password.  
> 
BTW, you have been displaying remarkable patience in dealing with me and helping me get this going.  You are awesome.  I thought you should know that.
Unfortunately we have come to the time when I need to sign off.  I will be back in about 16 hours or so.  I have something to do tomorrow morning.  We can continue then.  At this point it's down to diagnosing what GADMIN-SAMBA has mucked up.  It is a misconfiguration.

Talk to you tomorrow.  What TZ are you in?  I'm west coast USA.

---

### Post by vbalbert on 2014-08-30
> **bab1 said:**
> This should be the user vbalbert and that user's password.  

Unfortunately we have come to the time when I need to sign off.  I will be back in about 16 hours or so.  I have something to do tomorrow morning.  We can continue then.  At this point it's down to diagnosing what GADMIN-SAMBA has mucked up.  It is a misconfiguration.

Talk to you tomorrow.  What TZ are you in?  I'm west coast USA.

No problem.  I'm on the west coast as well.

I found out that gksu is not installed by default.  Trying to get that installed should be a cinch.

When I try to log on I get the following message:
```
\\KODI\test is not accessible. You might not have permission to use this network resource.

Multiple connections to a server or shared resource by the same user, using more than one user name, are not allowed. Disconnect all previous connections to the server or shared resource and try again.
```

Update:  Due to the error message I thought that Windows might be remembering something it shouldn't, so I rebooted.  Behold and lo, I was able to log into the share, but other than that, I was not able to do anything.  I'm not surprised, it doesn't look like you added any file permissions to the share.  I attempted a simple file copy to no avail.  I suspect that's where we're going next.

Update 2: I added "Writeable = yes" to the smb.conf file and vavoom!  I can now create, edit, delete files on share.

---

### Post by bab1 on 2014-08-31
> **vbalbert said:**
> No problem.  I'm on the west coast as well.

I found out that gksu is not installed by default.  Trying to get that installed should be a cinch.

When I try to log on I get the following message:
```
\\KODI\test is not accessible. You might not have permission to use this network resource.

Multiple connections to a server or shared resource by the same user, using more than one user name, are not allowed. Disconnect all previous connections to the server or shared resource and try again.
```

Update:  Due to the error message I thought that Windows might be remembering something it shouldn't, so I rebooted.  Behold and lo, I was able to log into the share, but other than that, I was not able to do anything.  I'm not surprised, it doesn't look like you added any file permissions to the share.  I attempted a simple file copy to no avail.  I suspect that's where we're going next.

Update 2: I added "Writeable = yes" to the smb.conf file and vavoom!  I can now create, edit, delete files on share.
Glad to here you worked on this by your own.  The multiple users problem was a Windows problem.

I'm curious to see what actually is going on.  Do you have files or directories in /srv/samba/test?  What is the output of ```
ls -l /srv/samba/test
```

---

### Post by vbalbert on 2014-08-31
> **bab1 said:**
> Glad to here you worked on this by your own.  The multiple users problem was a Windows problem.

I'm curious to see what actually is going on.  Do you have files or directories in /srv/samba/test?  What is the output of ```
ls -l /srv/samba/test
```

The system is where it seems that I want it to be.  I deleted the test folder, created a Media folder using the same methods as we did the test folder and then altered the smb.conf file to access the Media folder instead.  I can create, modify, move, delete and rename files just like I want to.  In short, it's doing everything I need it to do.  I even played some of the files to make sure that things were working on both ends like I wanted.  It works great!  It is, in short, what I wanted.  Was there anything else that should be done?

---

### Post by bab1 on 2014-08-31
> **vbalbert said:**
> The system is where it seems that I want it to be.  I deleted the test folder, created a Media folder using the same methods as we did the test folder and then altered the smb.conf file to access the Media folder instead.  I can create, modify, move, delete and rename files just like I want to.  In short, it's doing everything I need it to do.  I even played some of the files to make sure that things were working on both ends like I wanted.  It works great!  It is, in short, what I wanted.  Was there anything else that should be done?

Not really.  I just wanted to make sure that the permissions and ownership were correct.  Either way, as long as you can access the file s and the HTPC app can access the files everything is working as it should be.

---

### Post by vbalbert on 2014-08-31
> **bab1 said:**
> Not really.  I just wanted to make sure that the permissions and ownership were correct.  Either way, as long as you can access the file s and the HTPC app can access the files everything is working as it should be.

Thank you VERY much for your help.  You went far beyond what I expected.  Is there somewhere I can give you an upvote or something?

---

### Post by bab1 on 2014-08-31
> **vbalbert said:**
> Thank you VERY much for your help.  You went far beyond what I expected.  Is there somewhere I can give you an upvote or something?

There is no need for any recognition.  I help folks to give back the IT knowledge I have gained over the last 25 years.

[COLOR="#0000FF"]Edit:  You can make this thread ***solved *** since you have what you wanted.[/COLOR]

---

