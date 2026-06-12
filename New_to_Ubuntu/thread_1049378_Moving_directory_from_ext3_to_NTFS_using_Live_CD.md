---
title: "Moving directory from ext3 to NTFS using Live CD"
date: 2009-01-24
forum: New to Ubuntu
---

### Post by YEGGE! on 2009-01-24
Forgive me if my problem has already been addressed, I have combed the forums and come close, but nothing has done the trick.

The story:  
A virus infected my Windows Partition and I was using up the last bit of my free space.  So I decided to buy a new HDD, format it in ext3, back up the files there, wipe the old HDD, reinstall XP, then move the files back.

In retrospect, I could have chosen an easier way.

My current position:
I'm afraid to install Ubuntu on the ext3 formatted drive containing the back up files, because it will reformat the whole drive.

I could make a partition on the old drive and install, but I want to keep the different OS's on different drives.  
The Live CD does not give me an option to partition the new drive. Or does it?

Ideally I would like to use the Live CD to move the directory from the ext3 drive to the NTFS drive.

Initially the Live CD wouldn't even let me consolidate the files within the ext3 drive, but I was able to do so using ```
sudo /bin/bash
``` and ```
mv /media/disk/SOURCE /media/disk/DESTINATION
```
The same method does not work in writing to the NTFS drive.

Attempts:
I tried installing Automatix2 via ```
sudo apt-get install ntfs-config
``` and I get the following. ```
ubuntu@ubuntu:~$ sudo apt-get install ntfs-config
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ntfs-config
```

I try to change the permissions of the NTFS drive to Ubuntu Live User by ```
gksudo nautilus
```
Then -> navigating to /media/disk-1 Right Click -> Properties -> Permissions (tab) and changing owner to Ubuntu Live User or changing the Folder Access to create and delete, but no dice.  The following error shows ```
Couldn't change the permissions of "disk-1" because it is on a read-only disk
```

Is there a way to write to NTFS drives using the Live CD?

::edit::
```
gksudo nautilus
```
gave me 
```
Initializing gnome-mount extension

(nautilus:19712): GLib-GObject-WARNING **: instance of invalid non-instantiatable type `(null)'

(nautilus:19712): GLib-GObject-CRITICAL **: g_signal_handlers_disconnect_matched: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

** (nautilus:19712): CRITICAL **: nautilus_file_unref: assertion `NAUTILUS_IS_FILE (file)' failed
```

---

### Post by logos34 on 2009-01-24
The live cd has three auto partitioning install options: 'Guided--Resize', 'Guided--use entire disk', and 'Guided--use largest continuous free space'.  There's a fourth option, 'manual'--it will allow you to specify (or create) the target partition for /.  That's what you want.

But here's an easier way:

reinstall windows on the old drive.  Get[ fs-driver]("http://www.fs-driver.org/") so you can access the ext3 partition.  Copy all the backup files to the windows drive.

Now do what you want with the other disk.

---

### Post by YEGGE! on 2009-01-27
Worked great!  Thanks!

---

