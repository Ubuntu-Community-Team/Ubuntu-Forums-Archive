---
title: "Disk Mount Error During Boot-Up"
date: 2011-05-15
forum: New to Ubuntu
---

### Post by lng on 2011-05-15
[SIZE=2]Hi Guys,
Am using UBUNTU 10.10, 32bit Desktop Version.
I tried 2 keep my drives Mounted During Boot-up as the following tutorial says. 
[/SIZE]
[SIZE=2][COLOR=Indigo]- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -- - - - - - - -
[/COLOR][/SIZE][SIZE=2][COLOR=Indigo]Auto Mount Drives at System Startup

[/COLOR][/SIZE] [SIZE=2][COLOR=Indigo]Ubuntu is capable of reading and writing files stored on Windows  formatted partitions, but partitions must be 'mounted' before they can  be accessed each time you start up the system. With these steps, you can  auto mount the drives or partitions without the need to manually mount  them for access.[/COLOR][/SIZE]
 
[LIST=1]
[*][SIZE=2][COLOR=Indigo]Install [/COLOR][/SIZE][SIZE=2][COLOR=Indigo]Storage Device Manager[/COLOR][/SIZE][SIZE=2][COLOR=Indigo] if it has not been added.
[/COLOR][/SIZE]
[LIST=1]
[*][SIZE=2][COLOR=Indigo]Go to Applications (or Main Menu) > Ubuntu Software Center.[/COLOR][/SIZE]
[*][SIZE=2][COLOR=Indigo]Enter [/COLOR][/SIZE][SIZE=2][COLOR=Indigo]pysdm[/COLOR][/SIZE][SIZE=2][COLOR=Indigo] in the Search Box.[/COLOR][/SIZE]
[*][SIZE=2][COLOR=Indigo]Select Storage Device Manager, click the "Install" button.[/COLOR][/SIZE]
[/LIST]
 
[*][SIZE=2][COLOR=Indigo]Go to System > Administration > Storage Device Manager.[/COLOR][/SIZE]
[*][SIZE=2][COLOR=Indigo]Extend the list of sda and select the sda you want to auto mount, click 'OK' to configure.[/COLOR][/SIZE]
[*][SIZE=2][COLOR=Indigo]Click the "Assistant" button.[/COLOR][/SIZE]
[*][SIZE=2][COLOR=Indigo]Uncheck "Mount file system in read only mode" and keep "The file system is mounted at boot time" checked.[/COLOR][/SIZE]
[*][SIZE=2][COLOR=Indigo]Click the "Mount", "Apply" then "Close" button, and restart the system.[/COLOR][/SIZE]
[/LIST]
 [SIZE=2][COLOR=Indigo]In case you wish to remove the auto-mount of a certain drive or  partition, you can similarly use Storage Device Manager to do the  setting.[/COLOR][/SIZE]
[SIZE=2][COLOR=Indigo]
- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -- - - - - - - -[/COLOR][/SIZE]

[SIZE=2]along with that, I renamed the Information Column as Datas (name of the Drive)  Instead of sda3.
Now While Booting I find something like,
[/SIZE]
[SIZE=3][COLOR=Red]Error  while mounting . . . .
press S to skip or M to Manual edit.[/COLOR][/SIZE]

[SIZE=2]& after Login, when i try to open the Drive I Ge[/SIZE]ts

[COLOR=Red][SIZE=3]Error mounting: mount exited with exit code 1: helper failed with:
[mntent]: line 12 in /etc/fstab is bad
[mntent]: line 14 in /etc/fstab is bad
[mntent]: line 15 in /etc/fstab is bad
[mntent]: line 16 in /etc/fstab is bad
mount: can't find /dev/sda3 in /etc/fstab or /etc/mtab[/SIZE]

[COLOR=Black][SIZE=2]when I Mount the Drive using Storage Device Manager its Ok.

Plz Help Me.  :([/SIZE]

[/COLOR][/COLOR]

---

### Post by JKyleOKC on 2011-05-15
> **lng said:**
> along with that, I renamed the Information Column as Datas (name of the Drive)  Instead of sda3.
Now While Booting I find something like,

(snipped)

mount: can't find /dev/sda3 in /etc/fstab or /etc/mtab

when I Mount the Drive using Storage Device Manager its Ok.

Plz Help Me.Change the name back to sda3 and the problem should go away. When a partition name is changed, you must be sure to change ALL of the places that refer to it.

---

### Post by lng on 2011-05-15
[COLOR=Black]I tried that sir.
Bt Still During Boot Up it Says
[COLOR=Red]
Error While Mounting /Media/data[/COLOR]

also I found that inside the Media Folder, There is a folder Data which is not deletable.
and when ever I input new names at Information ( In Storage Device manager) it is shown as a folder out there.
[/COLOR]

---

### Post by JKyleOKC on 2011-05-15
The Storage Device Manager program makes entries in the /etc/fstab file, which the system uses to automagically mount partitions at boot time. Please post that file so we can see exactly what it is doing, and also the output of "sudo fdisk -l" (that's a small L, not the numeral one, after the dash). 

You can copy the /etc/fstab content from any text editor, such as gedit. After pasting both into a reply message, highlight the pasted lines and then click the "#" icon on the toolbar above to put them into a "code" box and preserve the formatting so that we can read them more easily.

---

### Post by lng on 2011-05-16
[SIZE=3][COLOR=Red]/etc/fstab file[/COLOR][/SIZE]

```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc           proc  nodev,noexec,nosuid       0  0  
# / was on /dev/sda7 during installation
UUID=c74d0f32-4f4f-4798-946a-736a4167cfc0  /               ext4  errors=remount-ro         0  1  
/dev/fd0                                   /media/floppy0  auto  rw,user,noauto,exec,utf8  0  0  
/dev/sda3                                  /media/Datas (sda 3)  ntfs  nls=iso8859-1,umask=000     0  0  
/dev/sda5                                  /media/sda5     ntfs  defaults                  0  0  
/dev/sda6                                  /media/MSG (sda 6)    ntfs  nls=iso8859-1,ro,umask=000  0  0  
/dev/sda3                                  /media/Datas (sda 3)  ntfs  nls=iso8859-1,umask=000   0  0  
/dev/sda6                                  /media/MSG (sda 6)    ntfs  nls=iso8859-1,umask=000   0  0  
/dev/sda2                                  /media/sda2     ntfs  defaults                  0  0  
/dev/sda3                                  /media/sda3     ntfs  defaults                  0  0  
/dev/sda6                                  /media/sda6     ntfs  defaults                  0  0  
```
[SIZE=3][COLOR=Red]Sudo fdisk -l[/COLOR][/SIZE]

```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x8cd430bb

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              13        2481    19820544    7  HPFS/NTFS
/dev/sda3            2481        6397    31457280    7  HPFS/NTFS
Partition 3 does not end on cylinder boundary.
/dev/sda4            6397       19458   104906753    f  W95 Ext'd (LBA)
Partition 4 does not end on cylinder boundary.
/dev/sda5            7703       12924    41942016    7  HPFS/NTFS
/dev/sda6           12925       19458    52476928    7  HPFS/NTFS
/dev/sda7            6397        7703    10485760   83  Linux

Partition table entries are not in disk order
```

---

### Post by JKyleOKC on 2011-05-16
It looks like the SDM program has been adding extra entries to /etc/fstab instead of changing existing entries. Fortunately it will be easy to fix. Open the file by going into a terminal and typing "gksudo gedit /etc/fstab" which will open the file for editing, but with some dire warnings that you are using the root account. Then add a few "#" characters to certain lines, so that it looks like this:```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc           proc  nodev,noexec,nosuid       0  0  
# / was on /dev/sda7 during installation
UUID=c74d0f32-4f4f-4798-946a-736a4167cfc0  /               ext4  errors=remount-ro         0  1  
/dev/fd0                                   /media/floppy0  auto  rw,user,noauto,exec,utf8  0  0  
[COLOR="Red"]#/dev/sda3                                  /media/Datas (sda 3)  ntfs  nls=iso8859-1,umask=000     0  0[/COLOR]  
/dev/sda5                                  /media/sda5     ntfs  defaults                  0  0  
[COLOR="Red"]#/dev/sda6                                  /media/MSG (sda 6)    ntfs  nls=iso8859-1,ro,umask=000  0  0  
#/dev/sda3                                  /media/Datas (sda 3)  ntfs  nls=iso8859-1,umask=000   0  0  
#/dev/sda6                                  /media/MSG (sda 6)    ntfs  nls=iso8859-1,umask=000   0  0 [/COLOR] 
/dev/sda2                                  /media/sda2     ntfs  defaults                  0  0  
/dev/sda3                                  /media/sda3     ntfs  defaults                  0  0  
/dev/sda6                                  /media/sda6     ntfs  defaults                  0  0
```Save the file, exit from the editor, and you will be back in the terminal. Before leaving the terminal, type "sudo mount -a" to verify that all is now well. The problem should be gone. That "mount -a" command remounts all the drives, using the fstab file; if anything is wrong you will see error messages. If it returns to the terminal prompt with no messages, the problem is fixed.

Try not to use the SDM program until you can find out why it's adding lines instead of changing them. It might be misconfigured on your machine, or might be a bug in the program -- it's impossible to tell from a distance. I've used it in the past without having any such problem, but I never tried to change the name of a device either, and no longer have it installed on any of my systems.

P.S.--The reasons that you could not remove the named directories from /media could be a problem of permissions, or could be that they had been made busy by the attempt to mount drives to them. After the "mount -a" succeeds, you should be able to delete them from /media easily if you use "gksudo nautilus" to make the attempt using root permissions.

---

### Post by lng on 2011-05-16
[SIZE=2]Thank you sir.
The Problem is fixed.
Now I will be careful not to experiment too much on GNOME, Until i get to know what really am doing.
again,
Thanks a lot sir.[/SIZE]

---

### Post by lng on 2011-05-16
[SIZE=2]I think the System Considered the New Names i gave to be additional Drives & while trying to load them, (since actually they doesn't exist) it was shown as error.

By Changing those Load Commands to Comments, Solved the Problems.
Is that so ?
Is their any way to study How the GRUB & GNOME works ?
[/SIZE]

---

### Post by JKyleOKC on 2011-05-16
There are a number of threads that discuss such things, as well as quite a bit of information on the Ubuntu wiki pages. Try [https://help.ubuntu.com/](https://help.ubuntu.com/) for a good place to start...

And yes, changing the added lines to comments is what solved the problem. This practice, commonly called "commenting out" material, is widely used, especially in troubleshooting, because unlike deleting the line, it's quite easy to change back if it doesn't help.

---

### Post by lng on 2011-05-18
[SIZE=2]Thank you sir, for that link.
That is an excellent help for a beginner like me.  [/SIZE]:)

---

