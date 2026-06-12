---
title: "Howto change permissions in External HDD"
date: 2010-05-13
forum: New to Ubuntu
---

### Post by Harriak on 2010-05-13
I just bought an Iomega External HDD (that was formatted and used by a Mac user) and I didn't succeed in changing the permission (write and read) into root and admin (me) using the nautilus-gksu programm.
What command should I use in Terminal to change the user-ID/UID?
(I use the new Ubuntu 10-04 as my OS).

---

### Post by oldfred on 2010-05-13
You can only set permissions and ownership on linux partitions. Is the partition NTFS to be compatible?

Understanding fstab
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)
Ownership and permissions of vfat / ntfs are set at the time of mounting. This is often a source of confusion.

[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)

---

### Post by Harriak on 2010-05-13
> **oldfred said:**
> You can only set permissions and ownership on linux partitions. Is the partition NTFS to be compatible?

Understanding fstab
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)
Ownership and permissions of vfat / ntfs are set at the time of mounting. This is often a source of confusion.

[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)

Thanks Oldfred for your reply. I want to get rid of the Mac stuff, so I guess I'll either have to 'get permission' to write at the disk (using fstab, and if so, how??) or partition it Linux wise (maybe using Gparted??). But also I want to be able to use it on a Windows machine, so I suppose it therefore needs to be NTFS compatible.

---

### Post by oldfred on 2010-05-13
This is my entry for one of my NTFS partitions (my other is slightly different and without the noexec it keeps asking if text files are to be executed, but I use it so little I have not changed fstab):

# Entry for /dev/sdc2 :
UUID=44332FD360AA9657                      /home/fred/shared  ntfs-3g      defaults,noexec,nosuid,locale=en_US.UTF-8          0  0

some also add this which I have on the one that does not work as well??
fmask=0111,dmask=0000

---

### Post by vandorjw on 2010-05-13
Why are we making things complicated?

This is what I would do.
Hook the external Drive up to your windows machine.
Format the disk, (open my computer, right click the external drive and click "format...") as NTFS.

Create folders, move files, etc... make sure its working.

Now go to your computer running Ubuntu 10.04 and plug in your hard drive.
It will likely show up on your desktop, double click it to mount it.

If you don't have permission to write to the folders do this.

open up a shell, (terminal) and type this.
```

sudo chmod USER /media/PATH/TO/HARD/DRIVE/FOLDER

```

replace USER with your username, and path_to_hdd_folder with the actual path.

enter your password and you are done.
If there is a problem write back.

----------------------------------------------
oldfred's method is much more permanent and since what you are working with is an external hard drive, and not an internal I do not like it as much. when you do not have the hard drive plugged in and you start up the computer it will waste time looking for it, then return some error that it cannot be found. (although most if this is covered up by Ubuntu's loading screen, and you won't actually see it) 

Please note that your "UUID" will not be 44332FD360AA9657.You can find your UUID for your external drive by typing
```

ls -l /dev/disk/by-uuid

```
in a shell

Also, I recommend you leave it after Defaults, and do not type noexec, etc...

If you are annoyed by it asking if you want to run a text file, just open up nautilus, click "Edit" --> "Preferences" --> "Behaviour" 

Here change Executable text file from "Ask each time" to --> "View each time"

Hope that helps.

@oldfred -- If you feel like I am stomping on your suggestion, I do not mean to. Just offering an alternative.

---

### Post by mike555 on 2010-05-13
just a note , be sure to safely remove it , don't just yank out the usb from the Windows computer or it might not work in Ubuntu...

---

### Post by oldfred on 2010-05-13
cc7gir, not a problem - I thought we all were here to help ( and learn), but I thought unless it was a linux file system that supports permissions and ownership you could not change except when you mount it.

---

### Post by Harriak on 2010-05-14
Thanks both of you.
As I am not experienced in using the commandline, I found my way at roundabout, experimenting with the programs Gparted and Nautilus GKSU. Also I was not in need of saving any files or directories on the disk, so no risk of loosing stuff...
The disk was detected by GParted after which I created a partition table (gpt) cleaning up everything nicely. And made a primary partition (nfts), which I then resized. Finally I made a new primary partition (ext4) in the created unallocated area.

Accessing, writing, deleting in the NTFS part was no problem with Ubuntu. But the ext4 part was not accessible at first (Lost&Found directory, owner:root, group:root). I used nautilus gksu to change the group owner (root) into my own name and was able to access, write, delete.

cheers, harriak

---

### Post by piemonkey on 2010-05-15
> **mike555 said:**
> just a note , be sure to safely remove it , don't just yank out the usb from the Windows computer or it might not work in Ubuntu...

For the record, this used to cause trouble (on top of any normal trouble from 'unsafely removing' a drive), because the linux didn't know how to deal with it. Thanks to improvements in ntfs-3g, this has been fixed for quite a while now, so you shouldn't have any problems.

---

