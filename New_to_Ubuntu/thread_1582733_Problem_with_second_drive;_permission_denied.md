---
title: "Problem with second drive; permission denied"
date: 2010-09-26
forum: New to Ubuntu
---

### Post by ericstrom on 2010-09-26
I recently set up a 2nd IDE drive to auto-mount. Seems to mount just fine. I have it under /media. But then I try to move or copy files (in this case Document 1) to it and I get the following error message:

Error opening file '/media/Drive-b/Unsaved Document 1': Permission denied

What do I need to change so I can use the drive ?

(currently running Lucid Lynx 10.04)

---

### Post by Clever_Username on 2010-09-26
deleted

---

### Post by ericstrom on 2010-09-26
You wrote .... "Can you post an ls -l on the file your trying to move?"

What does that mean ? How do I "post an ls -l" on a file ?

Note, I also tried moving another file to the drive and got the same permission denied message.

---

### Post by SentientFluid on 2010-09-26
Open Terminal ([FONT="Courier New"]Applications > Accessories > Terminal[/FONT]) and type```
ls -l /media
```

Copy and paste the results here.

---

### Post by ericstrom on 2010-09-27
Thanks for helping SentimentFluid. Here's the results:


eric@desktop:~$ ls -l /media
total 8
drwxr-xr-x 3 root root 4096 2010-09-25 09:44 Drive-b
lrwxrwxrwx 1 root root    7 2010-08-08 15:33 floppy -> floppy0
drwxr-xr-x 2 root root 4096 2010-08-08 15:33 floppy0

---

### Post by sidzen on 2010-09-27
[SIZE=3]Go to your /home/username/ directory in the original or first drive and, in terminal, do as the man from Saskatoon said and enter the command  <* ls -a*l >.  The ownerships here are what you want on the second drive, too. 

[/SIZE][SIZE=3]Say your username _is_  *joe.  you do a < ls -al** > in your home directory and it says ownership is  joe:joe , like below *[/SIZE]
[SIZE=3]
[/SIZE][PHP]drwxr-xr-x  2  joe  joe   4096  Aug 29 16:29 Pictures[/PHP][SIZE=3]So, the command <* chown* > is necessary to do this.[/SIZE]

[SIZE=3]So, go to /media/devicename/home/ and do the following, quick and dirty access[/SIZE]

[SIZE=3]chown -R joe:joe username/*
[/SIZE]

---

### Post by bsalem on 2010-09-27
Go look at the properties of the mounted filesystem on /media. If it is a Linux Native partition(s), fine, its a permissions problem alone, but if the filesystem is NTFS or some other foreign type, there could be additional issues. If an NTFS filesystem (Created by Windows ) is corrupt Linux will usually not be able to fix it. and it will be mounted read-only. You will need to use Windows to repair it, sometimes just needing to boot into Windows once, and the filesystem will come back under Linux read/write. At the command line under Linux a 'mount' command will show you how it is mounted, the 'df' command gives less, but it least it will tell you which partition goes with which mount point. Be sure the file system is mounted has the type and mount point you expect.

---

### Post by garyed on 2010-09-27
It looks like only root has permission to write to Drive-b.
If you're using the terminal try using sudo in front of the command & see if that works. 
```
sudo cp /media/Dirve-b/location-to-filename /location-to-new-filename 
```

---

### Post by ericstrom on 2010-09-27
I tried the solution by Gary (but fixed the text so it read Drive-b, not Dirve-b). So the exact command I used is:

sudo cp /media/Drive-b/location-to-filename /location-to-new-filename

I got the following message back

cp: cannot stat `/media/Drive-b/location-to-filename': No such file or directory

What does this mean ? And more importantly, what do I try next ?

---

### Post by garyed on 2010-09-27
Are you typing the same command that you originally typed that gave you the permissions error but with sudo in front of it?
The cannot stat error is usually from a command that can't be executed like on a file not found or a partition not mounted.
Try this to check & make sure Drive-b is really mounted first:
```
mount
``` 

Then try the original command that gave the permissions error with sudo in front of it. See what  if any errors you get. I'm assuming you have an NTFS partition & they can be tricky sometimes. You might have to edit your /etc/fstab file to get it working.
good luck

---

### Post by ericstrom on 2010-09-27
The original error came from simply trying to move and save files to the new drive. Nothing exotic. 

Not using NTFS....have it set up as ext4.

I noticed that the media folder and the /media/drive-b folders do not have folder sharing enabled. I'm not even sure what that means but I'm wondering if that's the issue ?

Per Gary's suggestion, I opened up terminal and typed "mount". Here's the results:

/dev/sda1 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
none on /var/lib/ureadahead/debugfs type debugfs (rw,relatime)
/dev/sdb1 on /media/Drive-b type ext4 (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/eric/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=eric)

Seems like the new drive is mounting. It shows up in "Places" and I think the above output from terminal suggests it has mounted. 

No problem modifying fstab. I just don't know what to modify it to. The current fstab is as follows:

UUID=06eb3868-4edd-4f71-92ca-ad0d871a9a20 /media/Drive-b ext4 defaults 0 2

---

### Post by garyed on 2010-09-28
It doesn't look like you have any problem mounting so it doesn't look like there's any need to mess with fstab yet. If you can read the drive then its mounted. It might just be a matter of the syntax in your command line.
Lets say you have a file in your present home directory called "test".
The path will be ~/test. 
To copy that file into the other drives home directory do:

```
sudo cp ~/test /media/Drive-b/home
```

---

### Post by egalvan on 2010-09-28
> **ericstrom said:**
> 

Error opening file '/media/Drive-b/Unsaved Document 1': Permission denied


per your
```
ls -l /media
total 8
drwxr-xr-x 3 **root root** 4096 2010-09-25 09:44 **Drive-b**
lrwxrwxrwx 1 root root 7 2010-08-08 15:33 floppy -> floppy0
drwxr-xr-x 2 root root 4096 2010-08-08 15:33 floppy0 
```

partition Drive-b is owned by root.
this is a permission (ownership) problem.
the ownership of the partition and all files inside should be changed to your username.
Or, alternatively, always open the partition in 'administration' mode

As an aside, I would be careful using mixed-case file names in *nix...
upper and lower case are different..

Drive-b
 is NOT the same as 
drive-b

something to be aware of, as
Linux is Not Windows

---

### Post by ericstrom on 2010-09-28
Eglavan wrote ...."the ownership of the partition and all files inside should be changed to your username"

May I ask, exactly how does one go about changing the ownership of a partition ? Particularly when the partition is in a folder (/media) that is off root.

---

### Post by egalvan on 2010-09-28
> **ericstrom said:**
> Eglavan wrote ...."the ownership of the partition and all files inside should be changed to your username"

May I ask, exactly how does one go about changing the ownership of a partition ? 
Particularly when the partition is in a folder (/media) that is off root.
running 
```
man chown
```
brings up a list of chown options...

```
EXAMPLES
       chown root /u
              Change the owner of /u to "root".

       [b]chown root:staff /u
              Likewise, but also change its group to "staff".

       chown -hR root /u
              Change the owner of /u and subfiles to "root".[/B]

```

The highlighted portions should give you clues...

In the end. remember that everything in your file-system flows from '/'
which is, of course, owned by root.
Technically speaking, all your files are belong to root :)

---

### Post by egalvan on 2010-09-28
OK, took me a while, but I found my notes on this...

about a year ago I purchased a 750gb drive, and an external USB-eSATA docking station.

I used PartedMagic LiveCD to partition and format the drive to ext3.

When I rebooted under Hardy, surprise, the drive was owned by root.

 ```
sudo chown ernest:ernest /media/750-data1
```

changed it to my username on that machine.

adding the **-hR ** options will also change the files ownership.

N.B. at one time, this was mounted under /mnt, but I preferred having it auto-mount to the desktop, so changed it to /media.
the change in ownership came AFTER the change to /media.
I also set the disk-label to **750-data1**.
When I plug it into any other Linux using USB, it is automatically found, and the icon is called **750-data1**.
labeling partitions is a great time-saver under Linux.

---

### Post by ericstrom on 2010-09-28
One last question on this; I promise !

Why is the command is it ernest:ernest and not just ernest ?

In other words, the suggested command is 

sudo chown ernest:ernest /media/750-data1

but wondering why it wouldn't be:

sudo chown ernest /media/750-data1 or possibly sudo chown -R ernest /media/750-data1

---

### Post by ericstrom on 2010-09-30
Thanks all for the great help. Problem solved !

---

### Post by oldsoundguy on 2010-09-30
system> administration> disk utility.  Make sure it is formatted properly and that it is partitioned and you have checked permissions .. and then mount it.

---

### Post by formaldehyde_spoon on 2010-09-30
Add 'user' option to relevant line in fstab.

---

