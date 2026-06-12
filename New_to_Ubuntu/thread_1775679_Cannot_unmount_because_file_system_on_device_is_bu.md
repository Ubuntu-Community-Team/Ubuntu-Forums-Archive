---
title: "Cannot unmount because file system on device is busy"
date: 2011-06-05
forum: New to Ubuntu
---

### Post by 2CV67 on 2011-06-05
For a long time, I have been using an Iomega 160GB USB Hard Drive, with FAT32 partition for backing up XP & ext3 partition for backing up Ubuntu - no problems.

Recently, I added an NFTS partition, which now has a Clonezilla image of a Netbook drive & copies of Clonezilla & Tuxboot.

Since adding this partition, I cannot completely unmount the Iomega device.

When I plug it in, all 3 partitions are automounted, as IOMEGA (for the FAT32); Iomega_Linux (for ext3) & Iomega_Asus (for NFTS).
When I right-click on any Iomega desktop ikon & ask to safely remove, then IOMEGA & Iomega_Linux disappear (unmount OK) but Iomega_Asus stays there with the warning message below:
```
Unable to stop drive
Failed to eject media; one or more volumes on the media are busy.
```

Other methods give:

Nautilus > Right click > Unmount > ```
Unable to unmount Iomega_Asus
Cannot unmount because file system on device is busy
```

Nautilus > media > Right click on Iomega_Asus > Safely remove drive > ```
Unable to stop drive
This file cannot be stopped
```

Sometimes, repeated attempts bring success (don't know why) - other times not & I can only switch the HDD off.

I saw some threads suggesting running "lsof" in terminal, but I didn't see anything helpful when I did that.

Thanks for any suggestions to analyse & fix this!

---

### Post by jtarin on 2011-06-05
[There are several ways to go]("http://www.ibm.com/developerworks/aix/library/au-unmount_partitions/index.html") "lsof" being one of them. When it comes to someone's file system I would rather point you the way and have you decide if you want to go in that direction rather than throwing blind suggestions.

---

### Post by Mariane on 2011-06-05
> **jtarin said:**
> 
When it comes to someone's file system I would rather point you the way and have you decide if you want to go in that direction rather than throwing blind suggestions.


Quite, and the fact that my "blind suggestion" works for me does not mean it is a good idea for other people. When I have this issue (external HD or usb key) I first check that no program is using it - sometimes a simple file manager displaying the contents is enough for this message, even if the file manager is not doing anything else with the device - and then I pull the wire. 

And it gives me great pleasure. I'm sick and tired of having to convince the computer to do this or that, so whenever I can force it to do something instead of pleading with it I'm *** well going to force it! Ha. 

Mariane

---

### Post by 2CV67 on 2011-06-05
Thanks jtarin - I appreciate that approach!

I went through the items in your link & tried the "lsof" method.

Terminal "df" clearly shows the problem partition as /dev/sdg3 mounted at /media/Iomega_Asus

Terminal "losf /dev/sdg3" or "losf /media/Iomega_Asus" don't show any result.
[IMG]http://i838.photobucket.com/albums/zz309/2CV67/lsof.png[/IMG]

I am continuing to read, but if that provides any clues, please continue suggestions...

Thanks!

---

### Post by jtarin on 2011-06-05
I wouldn't put too much faith in that.....I get the same feed-back from my external USB that's constantly being written too. Keep reading.

---

### Post by 2CV67 on 2011-06-05
I tried ```
fuser /media/Iomega_Asus
``` & ```
fuser /dev/sdg3
``` but they don't show anything either...

Lost now...:confused:

---

### Post by jtarin on 2011-06-05
> The standard Linux version of the umount command includes a lazy unmount option, -l, to help unmount file systems that are in use. This command requires Linux kernel version 2.4.11 or greater, which isn't much of a problem today. Executing umount -l /name/of/file system detaches the specified file system from the system's directory hierarchy so that no new processes can use the file system and then unmounts the file system when all of the processes that were accessing it terminate. This can be handy but is not exactly what you want to use when you need to unmount a file system now. Try this and report what happens.

---

### Post by 2CV67 on 2011-06-05
> **jtarin said:**
> Try this and report what happens.
Run from a normal terminal it says```
umount: /media/Iomega_Asus is not in the fstab (and you are not root)
```
Run from a root terminal, it instantly unmounts the partition.

Confirmed 3 times in succession.

Looks good & I can always use that, but what does it mean?

Thanks very much for your continued interest!

---

### Post by dcsoldschool53 on 2011-06-05
Try this too ```
sudo umount /media/Iomega_Asus
``` to see if it unmount your drive from a normal terminal. This will give you temporary root privileges to unmount a drive.

---

### Post by 2CV67 on 2011-06-05
> **dcsoldschool53 said:**
> Try this too ```
sudo umount /media/Iomega_Asus
``` to see if it unmount your drive from a normal terminal. This will give you temporary root privileges to unmount a drive.
OK - that works too - confirmed 3 times.

Are we (you) getting near to understanding?
In properties - permissions, I am the owner of Iomega_Asus with RWX permissions.
And in the first-level-down folders.

.....?

---

### Post by dcsoldschool53 on 2011-06-06
In a terminal, try this command```
ls -l /media
```I want to see what your rwx permissions are for the Iomega_Asus drive.

---

### Post by jtarin on 2011-06-06
If you plan on keeping this drive as a permanent fixture, have you considered adding it to your fstab mounting at boot with correct permissions?

---

### Post by 2CV67 on 2011-06-06
Thanks, both, for sticking with me on this one!

Here are the results of ls -l /media
[IMG]http://i838.photobucket.com/albums/zz309/2CV67/media.png[/IMG]

> **jtarin said:**
> If you plan on keeping this drive as a permanent fixture, have you considered adding it to your fstab mounting at boot with correct permissions?
Not sure what you mean by permanent fixture.
I plug it in once a week for backups, then unplug it & keep it in a different location for relative security.
I leave the Lacie HDD permanently connected for daily or more frequent backups.

I try to avoid fiddling with fstab or anything else requiring expertise I don't have.
I really thought removable media was not supposed to be in fstab, but without understanding why?
I am ready to learn...

---

### Post by jtarin on 2011-06-06
Let's try "lsof" again this time do:

```
lsof | grep '/media/Iomega_Asus' (or the appropriate mount point)
```

to see a list of processes that have an open file or directory within that file system.

Any processes that :
started with a working directory in that file system
have open files in that file system
have a working directory in that file system
are possibilities. _Usually, it is just your shell, because you have cd'd into one of the file systems subdirectories._

---

### Post by 2CV67 on 2011-06-06
OK.
I plugged the HDD & that opened 3 Nautilus windows, one for each partition.
I closed those windows.
Did nothing else.

Ran lsof | grep '/media/Iomega_Asus'
Produced nothing.

Right click on Iomega_Asus on desktop > Safely remove...
Other 2 partitions unmounted but Asus stayed with usual busy warning.

Ran lsof | grep '/media/Iomega_Asus' again
Still produced nothing.

Root terminal > umount -l /media/Iomega_Asus
Unmounted immediately.

---

### Post by jtarin on 2011-06-06
[OK here's some more information that maybe you can test]("https://help.ubuntu.com/community/Mount/USB"). NTFS drives are down the page but its all interesting reading.

---

### Post by 2CV67 on 2011-06-06
Oh dear...

Reading that, I found I did not have ntfs-config installed, so installed that & ran it.
It detected /media/Iomega_Asus & I clicked on "Auto configure"

Now I can't MOUNT Iomega_Asus...
Only root can mount...

I notice there is now an entry for it in fstab.

This seems to be going in the wrong direction!

---

### Post by dcsoldschool53 on 2011-06-06
**Try this command now, I want to see what the format is for that drive.```
sudo fdisk -l
```and, I want to ask you this  question? Do you use a backup program to backup to your Iomega_Asus drive huh?**

---

### Post by 2CV67 on 2011-06-06
After ntfs-config & Auto-configure, not only would the Iomega_Asus partition not mount, but the PC would not boot without it - I had to "Skip" to boot.
So I commented out the fstab entry & am now back to where I was at the beginning.
Automount OK, boot OK, no GUI unmount.

sudo fdisk -l gives this result:
[IMG]http://i838.photobucket.com/albums/zz309/2CV67/fdisk.png[/IMG]

You ask about backup to the Iomega_Asus drive:
The IOMEGA (FAT32) partition contains copies of my Desktop's XP documents & settings etc.
The Iomega_Linux (ext3) partition has my weekly backup of my Desktop's Ubuntu /home (by Grsync) & a few incidental manual copies.
When I recently bought the Asus Netbook with Windows 7, I started backing up its documents & settings, using the built-in Windows facility, to the IOMEGA (FAT32) partition.
All that worked just fine.

As there is no windows installation disk with the netbook, I decided it would be prudent to make a whole-disk image of the netbook, which has 2 NTFS partitions & one EFI partition & one recovery partition of "unknown" formats.
At this point, I am getting out of my depth...
I used GParted in Ubuntu to shrink the Iomega_Linux partition & create a new Iomega_Asus (NTFS) partition.
Back on the netbook, I downloaded Tuxboot & Clonezilla-Live.
I used Tuxboot to put Clonezilla-Live on a bootable USB stick.
Then I used Clonezilla on the USB stick to make an image of the netboot drive & copy it into Iomega_Asus.
That is the main content.
Otherwise, there is a folder, installed from the netbook, with a copy of the Clonezilla download .zip file & a copy of the Tuxboot .exe file, in case I ever need them for recovery.
I intend to use that partition also for future backups of netbook W7 stuff, instead of mixing it with the XP items, but am not there yet.

Sorry for that long description.
The short version is that I used Clonezilla to put an image on that partition.

---

### Post by 2CV67 on 2011-06-07
> **2CV67 said:**
> So I commented out the fstab entry & am now back to where I was at the beginning.
Automount OK, boot OK, no GUI unmount.
Not quite where I was - the terminal operations ($ sudo umount /media/Iomega_Asus etc) no longer work!
They result in "umount: /media/Iomega_Asus: not mounted" even though it obviously still is mounted, can be seen & manipulated in Nautilus & still cannot be unmounted by "Safely remove..." because "...busy".

By the way, the device mounts & unmounts OK on the Netbook with Windows7.

---

### Post by jtarin on 2011-06-07
> **2CV67 said:**
> 
By the way, the device mounts & unmounts OK on the Netbook with Windows7.Netbook? Are you dual booting on the Netbook with Ubuntu?

---

### Post by jtarin on 2011-06-07
[Some interesting ideas on using /mnt to mount rather than /media for USB devices.]("https://help.ubuntu.com/community/Mount/USB")

[And mounting Windows NTFS partitions]("https://help.ubuntu.com/community/MountingWindowsPartitions")

Make sure you peruse the links at the bottom of each page.
A thought...did you rename this drive or partitions just before this happened?

---

### Post by 2CV67 on 2011-06-07
> **jtarin said:**
> Netbook? Are you dual booting on the Netbook with Ubuntu?
Not yet.

I just wanted to get a good image of the netbook drive I could come back to, before I started messing with partitions & grub etc....

As you know, that is an ongoing thing!

I didn't get to look at your latest links yet - but thanks anyway!

---

### Post by 2CV67 on 2011-06-07
> **jtarin said:**
> 
A thought...did you rename this drive or partitions just before this happened?
Looking back through my records:
At the end of May, when the device only had 2 partitions - IOMEGA & "Iomega Linux" without underspace, I had an incident with Gparted, which I thought was resolved (without full understanding) by renaming that partition to Iomega_Linux.
Described here: [http://ubuntuforums.org/showthread.php?t=1772195](http://ubuntuforums.org/showthread.php?t=1772195)

That Iomega_Linux partition was then immediately reduced to make room for the new Iomega_Asus partition.
The Iomega_Asus partition had the "unable to stop drive" problem from new.

---

### Post by 2CV67 on 2011-06-07
> **jtarin said:**
> [Some interesting ideas on using /mnt to mount rather than /media for USB devices.]("https://help.ubuntu.com/community/Mount/USB")

[And mounting Windows NTFS partitions]("https://help.ubuntu.com/community/MountingWindowsPartitions")

Make sure you peruse the links at the bottom of each page.
A thought...did you rename this drive or partitions just before this happened?

I ploughed through those links, & the references, without finding anything that helps me diagnose my problems.

Terminal "mesg" looked as though it might show something, but not as far as I can see.

I booted, waited, then plugged the Iomega device.
All 3 partitions came up in Nautilus.
Terminal "mount" showed them all OK.
Closed Nautilus wondows.
Right click on desktop ikon > Safely close... > Warning about unable...busy.
Terminal "sudo umount..." > says Iomega_Asus not mounted
Terminal "mount" > shows it is mounted!
```
chris@DESKTOP:~$ sudo umount /media/Iomega_Asus
[sudo] password for chris: 
umount: /media/Iomega_Asus: not mounted
chris@DESKTOP:~$ mount
/dev/sda3 on / type ext3 (rw,relatime,errors=remount-ro,commit=0)
proc on /proc type proc (rw)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
/dev/sda5 on /home type ext3 (rw,relatime,commit=0)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/chris/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=chris)
/dev/sdb2 on /media/Lacie_linux_ type ext3 (rw,nosuid,nodev,uhelper=udisks)
/dev/sdb1 on /media/LACIE_ type vfat (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush)
/dev/sdg3 on /media/Iomega_Asus_ type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
chris@DESKTOP:~$ 

```

Waited a long time, trying GUI & Terminal methods for unmounting, with no success.
Switched device off.

Terminal "dmesg" (from just before plugging device, to switching off):
```
[   61.403959] EXT3-fs (sdb2): mounted filesystem with ordered data mode
[  364.560044] usb 1-6: new high speed USB device using ehci_hcd and address 6
[  364.703076] scsi4 : usb-storage 1-6:1.0
[  365.701842] scsi 4:0:0:0: Direct-Access     Ext Hard  Disk                 PQ: 0 ANSI: 4
[  365.705555] sd 4:0:0:0: Attached scsi generic sg8 type 0
[  365.709065] sd 4:0:0:0: [sdg] 312581808 512-byte logical blocks: (160 GB/149 GiB)
[  365.709800] sd 4:0:0:0: [sdg] Write Protect is off
[  365.709804] sd 4:0:0:0: [sdg] Mode Sense: 10 00 00 00
[  365.709808] sd 4:0:0:0: [sdg] Assuming drive cache: write through
[  365.713933] sd 4:0:0:0: [sdg] Assuming drive cache: write through
[  365.713956]  sdg: sdg1 sdg2 sdg3
[  365.725180] sd 4:0:0:0: [sdg] Assuming drive cache: write through
[  365.725186] sd 4:0:0:0: [sdg] Attached SCSI disk
[  366.568351] EXT3-fs: barriers not enabled
[  366.590275] kjournald starting.  Commit interval 5 seconds
[  366.590395] EXT3-fs (sdg2): warning: maximal mount count reached, running e2fsck is recommended
[  366.591060] EXT3-fs (sdg2): using internal journal
[  366.591069] EXT3-fs (sdg2): mounted filesystem with ordered data mode
[ 1468.619325] usb 1-6: USB disconnect, address 6
chris@DESKTOP:~$ 
```

Beyond me...

---

### Post by 2CV67 on 2011-06-07
Hmmm


```
~$ sudo umount /media/Iomega_Asus_
```works OK but
```
~$ sudo umount /media/Iomega_Asus
``` doesn't.

I don't need that final underscore for IOMEGA nor Iomega_Linux...

---

### Post by 2CV67 on 2011-06-07
Confusion between Iomega_Asus & Iomega_Asus_

[IMG]http://i838.photobucket.com/albums/zz309/2CV67/nautilus.png[/IMG]

---

### Post by 2CV67 on 2011-06-07
Gparted now sees that partition as:
Label "Iomega_Asus"
Mount point "Iomega_Asus_"

A screenshot of Gparted from 3 June shows the mount point as "Iomega_Asus"

How could that happen & how do I escape?

If I want to keep Automount - and I do - then I don't get to choose the mount point, do I?

---

### Post by 2CV67 on 2011-06-08
With the Iomega device not mounted, I looked in /media & found there was an /Iomega_Asus folder.

Flying blind, I deleted it.

Now, when I plug the device, all 3 partitions appear, with no confusion about Asus_ & Asus.

Terminal "~$ sudo umount /media/Iomega_Asus" unmounts that partition OK & GUI methods unmount the others OK.

So now I am back to where I was before post#17:
- Automount OK
- Can unmount with "sudo umount..." OK
- Cannot unmount NTFS partition by GUI methods > "busy..." though "lsof..." shows nothing.

What could I check next?

---

### Post by dcsoldschool53 on 2011-06-08
[B]This is what I believe is happening to you just as it happened to me.  Back in the days, when I was using Ubuntu 9.04, I had installed a backup program to backup my work. In the settings of the backup program, I set a time and a day for it to start the backups, and to copy newer docs. Anytime I tried to umount the drive by clicking umount, it would not umount. It said that the drive was busy. I had to use the sudo umount command to umount it. It was waiting for that particular time and day to write to my drive, so it always said that it was busy anytime I mounted it.

What I am saying, is look at your settings for your backup program. This is what's causing your problem. The drive is waiting for something to do something, and I think it is waiting for your backup program to write to it.

I don't think you have anything to worry about if you want to keep your settings in the backup program, as long as you can still sudo umount the drive.
[/B]

---

### Post by matt_symes on 2011-06-08
Hi

I think this may be a problem with gvfs-mount that Nautilus uses. I suspect this because you can unmount with sudo but not through Nautilus. 

I'm not sure i know how to fix this but maybe we can identify the problem.

With the drive plugged in open a terminal

```
gvfs-mount -l
```

That is a small -L above.

Post back the results.

Kind regards

---

### Post by 2CV67 on 2011-06-08
> **matt_symes said:**
> With the drive plugged in open a terminal

```
gvfs-mount -l
```

That is a small -L above.

Post back the results.

```
chris@DESKTOP:~$ gvfs-mount -l
Drive(0): IC USB Storage-MMC
  Type: GProxyDrive (GProxyVolumeMonitorGdu)
Drive(1): CD/DVD Drive
  Type: GProxyDrive (GProxyVolumeMonitorGdu)
Drive(2): Floppy Drive
  Type: GProxyDrive (GProxyVolumeMonitorGdu)
Drive(3): 80 GB Hard Disk
  Type: GProxyDrive (GProxyVolumeMonitorGdu)
  Volume(0): LACIE
    Type: GProxyVolume (GProxyVolumeMonitorGdu)
    Mount(0): LACIE -> file:///media/LACIE_
      Type: GProxyMount (GProxyVolumeMonitorGdu)
  Volume(1): Lacie_linux
    Type: GProxyVolume (GProxyVolumeMonitorGdu)
    Mount(0): Lacie_linux -> file:///media/Lacie_linux_
      Type: GProxyMount (GProxyVolumeMonitorGdu)
Drive(4): IC USB Storage-MSC
  Type: GProxyDrive (GProxyVolumeMonitorGdu)
Drive(5): IC USB Storage-CFC
  Type: GProxyDrive (GProxyVolumeMonitorGdu)
Drive(6): IC USB Storage-SMC
  Type: GProxyDrive (GProxyVolumeMonitorGdu)
Drive(7): 120 GB Hard Disk
  Type: GProxyDrive (GProxyVolumeMonitorGdu)
  Volume(0): XP
    Type: GProxyVolume (GProxyVolumeMonitorGdu)
  Volume(1): LTS Ubuntu Drive
    Type: GProxyVolume (GProxyVolumeMonitorGdu)
Drive(8): CD/DVD Drive
  Type: GProxyDrive (GProxyVolumeMonitorGdu)
Drive(9): 160 GB Hard Disk
  Type: GProxyDrive (GProxyVolumeMonitorGdu)
  Volume(0): Iomega_Linux
    Type: GProxyVolume (GProxyVolumeMonitorGdu)
    Mount(0): Iomega_Linux -> file:///media/Iomega_Linux
      Type: GProxyMount (GProxyVolumeMonitorGdu)
  Volume(1): Iomega_Asus
    Type: GProxyVolume (GProxyVolumeMonitorGdu)
    Mount(0): Iomega_Asus -> file:///media/Iomega_Asus
      Type: GProxyMount (GProxyVolumeMonitorGdu)
  Volume(2): IOMEGA
    Type: GProxyVolume (GProxyVolumeMonitorGdu)
    Mount(0): IOMEGA -> file:///media/IOMEGA
      Type: GProxyMount (GProxyVolumeMonitorGdu)
chris@DESKTOP:~$ 
```

---

### Post by matt_symes on 2011-06-08
Hi

What happens if you type this at the terminal

```
gvfs-mount -u file:///media/Iomega_Asus
```

(it was Iomega_Asus wasn't it ? if not change as required)

Post back all and any output from that command.

Kind regards

---

### Post by 2CV67 on 2011-06-08
> **matt_symes said:**
> What happens if you type this at the terminal

```
gvfs-mount -u file:///media/Iomega_Asus
```

With the device mounted or plugged & unmounted or unplugged?

---

### Post by 2CV67 on 2011-06-08
> **dcsoldschool53 said:**
> What I am saying, is look at your settings for your backup program. This is what's causing your problem. The drive is waiting for something to do something, and I think it is waiting for your backup program to write to it.
Thanks for these suggestions, but I don't think that is it either, is it?
The _Asus partition has no backup content at all - It just has a drive image.
The _linux partition does have backup content, generated by Grsync, but there is no scheduling, just click when I feel like it & that partition works OK.
The IOMEGA partition does have backup content generated by W7 & I have not checked if there is any scheduling there (probably) - but that partition works OK.

I hope that is an adequate & not rude answer to your kind suggestion!
Or do I need to look elsewhere?

---

### Post by matt_symes on 2011-06-08
Hi

With the device mounted. That command i posted will try to unmount the partition using gvfs-mount functionality.
```

matthew@matthew-laptop:~$ gvfs-mount -h
Usage:
  gvfs-mount [OPTION&#8230;] - mount <location>

Help Options:
  -h, --help               Show help options

Application Options:
  -m, --mountable          Mount as mountable
  -d, --device             Mount volume with device file
  -u, --unmount            Unmount
  -s, --unmount-scheme     Unmount all mounts with the given scheme
  -l, --list               List
  -i, --detail             Show extra information for List and Monitor
  -o, --monitor            Monitor events

matthew@matthew-laptop:~$ 
```Kind regards

---

### Post by 2CV67 on 2011-06-08
> **matt_symes said:**
> What happens if you type this at the terminal

```
gvfs-mount -u file:///media/Iomega_Asus
```
Post back all and any output from that command.

It unmounted immediately, with nothing in Terminal.
Confirmed 3 times.
So...

---

### Post by matt_symes on 2011-06-08
Hi

> It unmounted immediately, with nothing in Terminal.
Confirmed 3 times.
So...That's very interesting because that is the functionality Nautilus calls to unmount the device. I believe it does it via a DBUS call.

Maybe we should now try to find the dbus calls Nautilus makes.

Open a terminal on the left hand side of the screen. Open nautilus on the right hand side of the screen. Mount the drive in Nautilus.

In the terminal type

```
dbus-monitor
```Click on the arrow in Nautilus to umount the drive. In the terminal press ctrl + c to stop monitoring.

The reason i want you to do it this way is otherwise you will get flooded with other DBUS messages and the messages we want will be lost. You can filter messages but that means more work as i am not sure what to filter for Nautilus.

Post back the results. Hopefully it will tell us where it is failing.

Kind regards

---

### Post by 2CV67 on 2011-06-08
> **matt_symes said:**
> In the terminal type

```
dbus-monitor
```Click on the arrow in Nautilus to umount the drive. In the terminal press ctrl + c to stop monitoring.

```
chris@DESKTOP:~$ dbus-monitor
signal sender=org.freedesktop.DBus -> dest=:1.133 serial=2 path=/org/freedesktop/DBus; interface=org.freedesktop.DBus; member=NameAcquired
   string ":1.133"
method call sender=:1.133 -> dest=org.freedesktop.DBus serial=3 path=/org/freedesktop/DBus; interface=org.freedesktop.DBus; member=AddMatch
   string "type='method_call'"
method call sender=:1.133 -> dest=org.freedesktop.DBus serial=4 path=/org/freedesktop/DBus; interface=org.freedesktop.DBus; member=AddMatch
   string "type='method_return'"
method call sender=:1.133 -> dest=org.freedesktop.DBus serial=5 path=/org/freedesktop/DBus; interface=org.freedesktop.DBus; member=AddMatch
   string "type='error'"
method call sender=:1.44 -> dest=org.gtk.Private.GduVolumeMonitor serial=38 path=/org/gtk/Private/RemoteVolumeMonitor; interface=org.gtk.Private.RemoteVolumeMonitor; member=MountUnmount
   string "0x9d3e5a0"
   string ""
   uint32 0
   string "1679:23"
signal sender=:1.30 -> dest=(null destination) serial=231 path=/org/gtk/Private/RemoteVolumeMonitor; interface=org.gtk.Private.RemoteVolumeMonitor; member=MountPreUnmount
   string "org.gtk.Private.GduVolumeMonitor"
   string "0x9d3e5a0"
   struct {
      string "0x9d3e5a0"
      string "Iomega_Asus"
      string ". GThemedIcon drive-harddisk-usb drive-harddisk drive"
      string ""
      string "file:///media/Iomega_Asus"
      boolean true
      string "0x9d1ad50"
      array [
      ]
   }
signal sender=:1.30 -> dest=(null destination) serial=232 path=/org/gtk/Private/RemoteVolumeMonitor; interface=org.gtk.Private.RemoteVolumeMonitor; member=VolumeChanged
   string "org.gtk.Private.GduVolumeMonitor"
   string "0x9d1ad50"
   struct {
      string "0x9d1ad50"
      string "Iomega_Asus"
      string ". GThemedIcon drive-harddisk-usb drive-harddisk drive"
      string ""
      string ""
      boolean true
      boolean false
      string "0x9d1ad00"
      string "0x9d3e5a0"
      array [
         dict entry(
            string "unix-device"
            string "/dev/sdg3"
         )
         dict entry(
            string "label"
            string "Iomega_Asus"
         )
         dict entry(
            string "uuid"
            string "3531BCE07326F070"
         )
      ]
   }
error sender=:1.30 -> dest=:1.44 error_name=org.glib.GError.g_2Dio_2Derror_2Dquark.c26 reply_serial=38
   string "Cannot unmount because file system on device is busy"
^C
chris@DESKTOP:~$ ^C

```

---

### Post by 2CV67 on 2011-06-08
But after that:```
chris@DESKTOP:~$ ^C
chris@DESKTOP:~$ gvfs-mount -u file:///media/Iomega_Asus
Error unmounting mount: Cannot unmount because file system on device is busy
chris@DESKTOP:~$ 
chris@DESKTOP:~$ gvfs-mount -u file:///media/Iomega_Asus
Error unmounting mount: Cannot unmount because file system on device is busy
chris@DESKTOP:~$ 

```

---

### Post by matt_symes on 2011-06-08
Hi

Umount using sudo. Remount and then
[FONT=monospace]
[/FONT]```
[FONT=monospace]gvfs-mount -u file:///media/Iomega_Asus[/FONT]
```[FONT=monospace]
Does it unmount cleanly like before ?

Kind regards
[/FONT]

---

### Post by 2CV67 on 2011-06-08
> **matt_symes said:**
> Hi

Umount using sudo. Remount and then
[FONT=monospace]
[/FONT]```
[FONT=monospace]gvfs-mount -u file:///media/Iomega_Asus[/FONT]
```[FONT=monospace]
Does it unmount cleanly like before ?

Kind regards
[/FONT]

Unreliable now - can't see what the pattern is...
```
chris@DESKTOP:~$ 
chris@DESKTOP:~$ gvfs-mount -u file:///media/Iomega_Asus
chris@DESKTOP:~$ gvfs-mount -u file:///media/Iomega_Asus
Error unmounting mount: Cannot unmount because file system on device is busy
chris@DESKTOP:~$ sudo umount /media/Iomega_Asus
chris@DESKTOP:~$ gvfs-mount -u file:///media/Iomega_Asus
Error unmounting mount: Cannot unmount because file system on device is busy
chris@DESKTOP:~$ sudo umount /media/Iomega_Asus
chris@DESKTOP:~$ gvfs-mount -u file:///media/Iomega_Asus
chris@DESKTOP:~$ gvfs-mount -u file:///media/Iomega_Asus
Error unmounting mount: Cannot unmount because file system on device is busy
chris@DESKTOP:~$ sudo umount /media/Iomega_Asus
chris@DESKTOP:~$ gvfs-mount -u file:///media/Iomega_Asus
Error unmounting mount: Cannot unmount because file system on device is busy
chris@DESKTOP:~$ sudo umount /media/Iomega_Asus
chris@DESKTOP:~$ gvfs-mount -u file:///media/Iomega_Asus
Error unmounting mount: Cannot unmount because file system on device is busy
chris@DESKTOP:~$ 

```

---

### Post by matt_symes on 2011-06-08
Hi
[FONT=monospace]
[/FONT]> [FONT=monospace][/FONT]chris@DESKTOP:~$  chris@DESKTOP:~$ gvfs-mount -u file:///media/Iomega_Asus chris@DESKTOP:~$ gvfs-mount -u file:///media/Iomega_Asus Error unmounting mount: Cannot unmount because file system on device is busy

Inconsistent like before.

The problem is with gvfs-gdu-volume-monitor. That is what thinks the drive is busy, even though lsof shows nothing.

What version of Ubuntu are you using ? Your output when you gvfs-mount -u is different is mine when i monitor the DBUS messages.

I am currently on 10.04.

What is the output of (copy and paste)

```
dpkg -l | grep gvfs
```

Kind regards

---

### Post by 2CV67 on 2011-06-08
> **matt_symes said:**
> What version of Ubuntu are you using ?
What is the output of (copy and paste)

```
dpkg -l | grep gvfs[/CODE

I am using 10.10

[CODE]chris@DESKTOP:~$ dpkg -l | grep gvfs
ii  gvfs                                       1.6.4-0ubuntu1.1                                  userspace virtual filesystem - server
ii  gvfs-backends                              1.6.4-0ubuntu1.1                                  userspace virtual filesystem - backends
ii  gvfs-bin                                   1.6.4-0ubuntu1.1                                  userspace virtual filesystem - binaries
ii  gvfs-fuse                                  1.6.4-0ubuntu1.1                                  userspace virtual filesystem - fuse server
ii  libgvfscommon0                             1.6.4-0ubuntu1.1                                  userspace virtual filesystem - library
chris@DESKTOP:~$ 

```

Thanks for your interest in this long trail!

---

### Post by 2CV67 on 2011-06-08
I also have LTS 10.04 which I keep for emergencies...

I am sorry to admit I never thought of checking the HDD with LTS.:oops:

So I just tried it & it gives the same (irregular) results.
Trying to unmount by right-clicking on the desktop ikon worked perfectly the first time, but failed "busy" the next twice.

I can do more testing with 10.04 if that is more convenient.

---

### Post by 2CV67 on 2011-06-08
Sorry, but I need to completely drop this subject for the next week or two.

I will post when I can pick it up again.

Please make any suggestions in the meantime.

I am VERY grateful for the time & effort people have put into this!

Thanks!

---

### Post by matt_symes on 2011-06-09
Hi

Have you checked the filing system on the partition ?

Kind regards

---

### Post by comzine on 2011-06-12
Hello I want to join this thread because I do have a very similar problem:

I mount a smb share folder with this script:

```
read -s -p "Password: " mypass

sudo smbmount //192.168.0.4/Music $HOME/Music/czdata -o username=comzine,password=$mypass,uid=comzine,iocharset=utf8,rw

```after this my laptop becomes really slow. Could there be any problems mounting a folder with a lot of files (>5000) thanks to radio stations *g*. If I open gedit and a file from the local $HOME folder, it takes a long time and shows following output:

```
(gedit:3222): GVFS-RemoteVolumeMonitor-WARNING **: invoking IsSupported() failed for remote volume monitor with dbus name org.gtk.Private.GduVolumeMonitor: org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
```I do believe, that it is a similar problem, because if I try to unmount /home/comzine/Music/czdata, it does not work correctly:

```
sudo umount $HOME/Music/czdata

umount: /home/comzine/Music/czdata: device is busy.
        (In some cases useful info about processes that use
         the device is found by lsof(8) or fuser(1))
comzine@czlaptop:~$ fuser $HOME/Music/czdata
/home/comzine/Music/czdata:  2504
comzine@czlaptop:~$ ps 2504
  PID TTY      STAT   TIME COMMAND
 2504 ?        D      0:04 /usr/lib/gvfs/gvfs-gdu-volume-monitor
```I changed in the gconf-editor the setting for automounting in nautilus to off, but the problem remains. Does anyone have an idea?

My system:
Ubuntu 10.10, 64 Bit, 2.6.35-28-generic

//edit:

Sorry to say, but probably it was my NAS Seagate BlackArmor 400 (bought on April 26th, 2011). The hdds work well but the NAS has difficulties to mount them correct as RAID 5. (sorry for off-topic)

---

### Post by 2CV67 on 2011-08-14
Update: Since upgrading to 11.04, this problem has gone away...

---

