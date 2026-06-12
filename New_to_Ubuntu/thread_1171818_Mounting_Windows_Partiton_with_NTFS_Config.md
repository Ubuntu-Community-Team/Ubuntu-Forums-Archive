---
title: "Mounting Windows Partiton with NTFS Config"
date: 2009-05-27
forum: New to Ubuntu
---

### Post by Thurgood Stubbs on 2009-05-27
In 9.04 I am trying to mount my Windows partition for several reasons, one being so Picasa can access pictures on that partition.  I've been following [this guide]("http://www.psychocats.net/ubuntu/mountwindows") and I installed NTFS Config, but when I open it goes right to the last screen shown in the guide and "Enable write support for internal device" is grayed out.  When I click ok, the program closes as though it is done.  How can I get it to recognize the partition on my only internal drive?  Also, getting ahead of myself, but once I do get it working, how can I make it so that it doesn't "mount" to my desktop i.e. - not having the disk icon on the desktop?

---

### Post by Mark Phelps on 2009-05-28
It may be greyed out because it's encountering errors during the mount attempt.

Recommend installing the following packages if you don't already have them: ntfs-3g, ntfsprogs.

Then, open a terminal and do the following:
1) Make a mount directory (as in "sudo mkdir /media/windows")
2) Mount the partition (presuming it's sda1) as in "sudo mount -t ntfs-3g /dev/sda1 /media/windows"

There are other mount options you will want later, but for now, let's just see if it will even mount the partition.

Look for messages in the terminal.  If there are errors during the mount, you will get messages.  A common error is that the partition is "dirty" and Linux will refuse to mount it.

If that happens, you'll have to boot into MS Windows and run chkdsk on the partition to reset the "dirty bit".

---

### Post by powel212 on 2009-05-28
> i.e. - not having the disk icon on the desktop?

If you install Ubuntu Tweak

[http://ubuntu-tweak.com/2009/05/04/ubuntu-tweak-0471-released.html](http://ubuntu-tweak.com/2009/05/04/ubuntu-tweak-0471-released.html)

You will find lots of great tool including a nice little switch to not show drives on the desktop

Powel

---

### Post by drs305 on 2009-05-28
It could be the device was not cleanly umounted from Windows. Probably the best way to fix this is to mount and cleanly unmount it from within Windows.

If this is not easily accomplished, install *ntfsprogs* and run this command. Change the sdXX entry to the correct device:
```

sudo apt-get install ntfsprogs
sudo ntfsfix /dev/sd[COLOR="Red"]XX[/COLOR]

```

To answer the second question, if you mount the device on a mount point in /mnt it shouldn't show up on your desktop. Those mounted in /media will be displayed.

---

### Post by Thurgood Stubbs on 2009-05-29
> **Mark Phelps said:**
> It may be greyed out because it's encountering errors during the mount attempt.

Recommend installing the following packages if you don't already have them: ntfs-3g, ntfsprogs.

Then, open a terminal and do the following:
1) Make a mount directory (as in "sudo mkdir /media/windows")
2) Mount the partition (presuming it's sda1) as in "sudo mount -t ntfs-3g /dev/sda1 /media/windows"

There are other mount options you will want later, but for now, let's just see if it will even mount the partition.

Look for messages in the terminal.  If there are errors during the mount, you will get messages.  A common error is that the partition is "dirty" and Linux will refuse to mount it.

If that happens, you'll have to boot into MS Windows and run chkdsk on the partition to reset the "dirty bit".

This appears to have worked, I got no error messages, was able to access the partition from Picasa.  Also, I followed the advice of drs305 by mounting to /mnt and it isn't on the desktop.  I hope everything will be the same when I restart.  Thanks.

---

### Post by Thurgood Stubbs on 2009-05-29
> **Thurgood Stubbs said:**
> This appears to have worked, I got no error messages, was able to access the partition from Picasa.  Also, I followed the advice of drs305 by mounting to /mnt and it isn't on the desktop.  I hope everything will be the same when I restart.  Thanks.

So after a restart, I'm back to where I started.  Disk mounted to the desktop, in Picasa my pictures from /mnt don't come up.  So now what?  I thought I was good.  What steps can I take to make it like I was with every start-up?

---

### Post by drs305 on 2009-05-29
Do you own the mountpoint? 
```

sudo chown -R yourusername: /mnt/whateverthemountpointis

```

Would you post the following:
```

cat /etc/fstab
mount && sudo fdisk -l && sudo blkid

```

---

### Post by Thurgood Stubbs on 2009-05-29
> **drs305 said:**
> Do you own the mountpoint? 
```

sudo chown -R yourusername: /mnt/whateverthemountpointis

```

Would you post the following:
```

cat /etc/fstab
mount && sudo fdisk -l && sudo blkid

```


I don't understand your first question about the mountpoint?

As for the second:

[PHP]brian@brian-laptop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/sda5 :
UUID=13ce10dd-cbcf-44bd-8679-e88de9deab31 / ext3 relatime,errors=remount-ro 0 1
# Entry for /dev/sda6 :
UUID=3bb63ef8-9615-4157-a3f2-4a785c9276f1 none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
brian@brian-laptop:~$ mount && sudo fdisk -l && sudo blkid
/dev/sda5 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/brian/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=brian)
/dev/sda2 on /media/disk type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
[sudo] password for brian:[/PHP]

---

### Post by drs305 on 2009-05-29
Since you successfully mounted the device without an error message, we will assume the filesystem is not corrupt.

My first question has to do with who owned the mount point. It shouldn't come into play with an non-linux file system. I just find it convenient to be the owner of my mount points.

I don't see an entry in fstab for your windows partition, so either the NTFS Configuration Tool didn't work or you didn't try it. So let's make an fstab entry manually to automount the ntfs partition.

Create a mount point, if you don't already have one. I will use the example "windows", use whatever name you want:
```

sudo mkdir /mnt/windows  # Create the mount point
sudo chown -R *yourusername*: /mnt/windows  # Make yourself the owner (not required for ntfs partitions), but won't hurt.
gksudo gedit /etc/fstab  # Open fstab for editing

```

Add this line. You will have to replace "sd[COLOR="DarkRed"]XX[/COLOR]" with the designation of your NTFS partition (sda2, etc). It assumes you are user 1000. You can check with the command "id":
> 
/dev/sd[COLOR="DarkRed"]XX[/COLOR] /mnt/windows ntfs auto,users,uid=1000,umask=027,utf8 0 0


Save fstab and then try unmounting then mounting the device:
```

sudo umount /dev/sd[COLOR="DarkRed"]XX[/COLOR]
sudo mount /dev/sd[COLOR="DarkRed"]XX[/COLOR]

```
If you don't get any error messages, it successfully mounted to /mnt/windows  (or whatever you named it).

---

### Post by Thurgood Stubbs on 2009-06-02
When I went to create the mount point (/mnt/windows) I was unable to because the file already existed.  No problem, so I moved on to the next step.  I got up to where I added to fstab ```
/dev/sdXX /mnt/windows ntfs auto,users,uid=1000,umask=027,utf8 0 0 
```

When I tried to save fstab, I was unable to because I "do not have the permissions necessary to save the file."

Now, once again I'm stuck.  What can I do so that I can save fstab?  Thanks.

---

### Post by drs305 on 2009-06-02
> **Thurgood Stubbs said:**
> When I went to create the mount point (/mnt/windows) I was unable to because the file already existed.  No problem, so I moved on to the next step.  I got up to where I added to fstab ```
/dev/sdXX /mnt/windows ntfs auto,users,uid=1000,umask=027,utf8 0 0 
```

When I tried to save fstab, I was unable to because I "do not have the permissions necessary to save the file."

Now, once again I'm stuck.  What can I do so that I can save fstab?  Thanks.

Whatever you were using to make the change, open that app with "gksudo <command>"  such as "gksudo gedit". That opens the app with administrative privileges and will allow you to make changes to system files.

---

### Post by Thurgood Stubbs on 2009-06-02
> **drs305 said:**
> Whatever you were using to make the change, open that app with "gksudo <command>"  such as "gksudo gedit". That opens the app with administrative privileges and will allow you to make changes to system files.

Got it.  That was sloppy on my part missing the *gk*sudo.  That worked, and now after a restart the drive is still mounted.  Thank you for the help!

---

### Post by Siggma on 2009-06-04
[SIZE="3"]You're over-killing the Billy Beasty...[/SIZE]

From a working mount line:

```
UUID=36F25324F252E79F /vista ntfs rw,users,quiet	0	0
```

To find the UUID (so it mounts even if you move the drive around in the BIOS as so many new BIOS can do) do this:

```
sudo blkid
```
Find the drive marked UUID="XXXXXXXXXXXXXXXX" ***type "ntfs"*** on the proper drive.
You don't need ntfs-3g in Jaunty, just use ntfs as the type and mount it with the **users** option. The "quiet" option prevents permission errors from cluttering up your logs. NTFS-3g creates a hidden mount point in your userspace (/home/*user*/.fusermount-blah-blah) whereas mounting it this way does not. It mounts it just like a native linux file system.

Copy the UUID="XXXXXXXXXXXXXXXX" part from the blkid command output and paste it into fstab. Then **remove the double quotes **around it and format the remainder of the line just like the line above and save fstab. Then you can create a place for it and mount it as root.

```

sudo mkdir /*vista* #or wherever you want it mounted
sudo mount /*vista* #using the mount point from previous command

```

Works like a charm. To use it as a regular user, navigate to /vista/Users/XXXX in the file browser and drag a shortcut to the bookmarks for the user or directory you want to use often.

[COLOR="Red"]WARNING WARNING WARNING WARNING WARNING WARNING[/COLOR]

Having written what I wrote above; Don't think of an NTFS partition as being just like a native linux partition. From personal experience **NTFS does not store user accounting information for linux users**. For example if you use the command: ```
cp -ax / /vista/backup
``` (meaning copy the native linux root file system to /vista/backup) you'll see a good copy of the entire directory tree but it will be unusable as a backup because permissions cannot be set on an NTFS partition for a linux user. The restored file system will probably boot but all your userspace files (/home/user) will be owned by root.

If you want to use NTFS as a system backup you must create a tar archive. See this article for more information: [http://ubuntuforums.org/showthread.php?t=35087](http://ubuntuforums.org/showthread.php?t=35087)

This issue can also cause you no end of grief is you are saving files from aMule or a torrent client. It will work but keep in mind your user name is only temporarily attached to the file. 

Lastly, all files created this way are marked as owned by "everybody" under windows.

---

