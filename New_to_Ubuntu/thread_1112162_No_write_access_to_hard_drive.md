---
title: "No write access to hard drive"
date: 2009-03-31
forum: New to Ubuntu
---

### Post by Paddy Landau on 2009-03-31
I've used gparted to create a partition and format it as ext3 on my nice new hard drive.

The drive automatically mounts OK, as it should, but for some reason it's read-only.

How do I tell the system to mount it read-write as it should? (In other words, what have I done wrong?)

---

### Post by MrWES on 2009-03-31
> **Paddy Landau said:**
> I've used gparted to create a partition and format it as ext3 on my nice new hard drive.

The drive automatically mounts OK, as it should, but for some reason it's read-only.

How do I tell the system to mount it read-write as it should? (In other words, what have I done wrong?)

The mount point is most likely owned by root, you need to change the ownership to you, the user

```
sudo chown -R username:username /path/to/mount/point
```

username = your username

Bill

---

### Post by Paddy Landau on 2009-03-31
Sadly, that made no difference.

With the previous formatting (FAT32), Ubuntu would automatically load the hard drive, and I had no problems whatsoever. Everything worked first time, flawlessly.

The only change since then is that I deleted the partition, recreated it, and formatted it as ext3.

And I just realised that I omitted to tell you that it's an external drive, connected through the USB. I don't know if that makes a difference.

---

### Post by kanikilu on 2009-03-31
Hi, can you post the contents of your /etc/fstab file and the output of the **mount** command from the terminal?

---

### Post by MrWES on 2009-03-31
> **Paddy Landau said:**
> Sadly, that made no difference.

With the previous formatting (FAT32), Ubuntu would automatically load the hard drive, and I had no problems whatsoever. Everything worked first time, flawlessly.

The only change since then is that I deleted the partition, recreated it, and formatted it as ext3.

And I just realised that I omitted to tell you that it's an external drive, connected through the USB. I don't know if that makes a difference.


Also do a:

```
sudo chmod 0755 /path/to/mount/point
```

Bill

---

### Post by Paddy Landau on 2009-03-31
> **MrWES said:**
> sudo chmod 0755 /path/to/mount/point
I already tried that, Bill, thanks for the suggestion.

---

### Post by Paddy Landau on 2009-03-31
> **kanikilu said:**
> Hi, can you post the contents of your /etc/fstab file and the output of the **mount** command from the terminal?
Well, usually the mount is automatic. However, I did it manually so that you could see...
```
$ sudo mkdir /media/disk
$ sudo mount /dev/sdb1 /media/disk
$ ls -lAd /media/disk
drwxr-xr-x 3 root root 4096 2009-03-31 18:54 /media/disk
```As you can see, there's no output.

The /etc/fstab file follows:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=2720857a-7ee9-4beb-ad09-fec472fe5e7c /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=2b425f2d-187f-407f-a377-6bcf65d369c7 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
#
guest,rw,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0
#
# For Wuala (http://wua.la/)
localhost:/wuala /home/paddy/.wuala/direct nfs defaults,users,noauto,rsize=8192,wsize=8192,timeo=14,intr,nolock,soft
#
```Thanks for your time and effort.

---

### Post by kanikilu on 2009-03-31
Can you just add it to /etc/fstab? I think something like this should work:
```
/dev/sdb1  /media/drive  ext3  rw,user,auto,relatime  0  0
```Change "drive" to whatever you want, but I believe Gnome tries to use "/media/disk" for automatic mounting of other devices, so I would pick something else.

That should work, but I would probably use the UUID rather than /dev/sdb1, to avoid any potential problems if it's not always attached to the system. To get the UUID, do:```
ls -l /dev/disk/by-uuid | grep sdb1
```Just use the long alphanumeric string in fstab. So instead of "/dev/sdb1", it would be "UUID=11ba35c7-....".

If you want a more user-friendly way than editing fstab, check out a package called pysdm.

---

### Post by Paddy Landau on 2009-04-01
*@kanikilu:* Thanks for the advice. Prompted by this, I've experimented a lot.

Here's what I did.

[LIST]
[*]Created an ext3 partition with [COLOR=Navy]gparted[/COLOR] (as already described).
[*]On Windows, created another NTFS partition.
[*]Windows easily and automatically mounted both the NTFS and ext3 partitions read-write (I used [IFS Driver]("http://www.fs-driver.org/") to access the ext3 partition).
[/LIST]
Here's what happened on Linux.

[LIST]
[*]The NTFS partition mounted automatically and perfectly. I have full read-write access to it.
[*]I had read-only access to the ext3 partition, whereas root (via [COLOR=Navy]sudo[/COLOR] or [COLOR=Navy]gksudo nautilus[/COLOR]) had full read-write access. It made no difference whether I amended the [COLOR=Navy]fstab[/COLOR] file. It also made no difference whether the machine mounted the drive automatically or I did it manually. I experimented with the mount options, especially [COLOR=Navy]user,rw[/COLOR], but again they made no difference (after all, it's always [COLOR=Navy]sudo[/COLOR] that mounts the drive).
[/LIST]
Therefore, it seems that the ext3 partition somehow inherits the authorisation from root, thereby preventing anyone else from accessing it.

Using [COLOR=Navy]sudo[/COLOR], I created a Public folder with [COLOR=Navy]chmod +0777[/COLOR]. However, this seems to be a workaround rather than what I really want, which is to provide full access to whichever machine I plug into. After all, when I then create folders and files within Public, they're created with my own user ID and group; when I plug it into a different machine with different users or switch to a different user, they won't have write access unless I remembered to use [COLOR=Navy]chmod[/COLOR] on everything that I added.

There is one other option that occurs to me. Just don't use ext3! I'll research what various formats are available to both Windows and Linux and, if possible, Mac.

---

### Post by Paddy Landau on 2009-04-02
I found [the answer]("http://forums.opensuse.org/archives/sf-archives/archives-hardware/346903-can-t-get-usb-external-hd-ext3-mount-read-write-mode.html") on the OpenSuse forum.

The problem is that the ext3 drive respects the ownership of the system.

Suppose that Ubuntu mounts the external drive to /media/drive, and your name and group are sandy.

Then issue the command
```
 sudo chown sandy:sandy /media/drive
```This gives you ownership of the drive.

Interestingly, even though Ubuntu removes that directory when unmounting, it remembers the ownership even after rebooting. So, it seems to be a permanent solution.

Yay!

---

### Post by egalvan on 2009-04-02
> **Paddy Landau said:**
> I found [the answer]("http://forums.opensuse.org/archives/sf-archives/archives-hardware/346903-can-t-get-usb-external-hd-ext3-mount-read-write-mode.html") on the OpenSuse forum.

 issue the command
```
 sudo chown sandy:sandy /media/drive
```This gives you ownership of the drive.
Yay!

Interesting...

The same command suggested in back in post #2... :)

---

### Post by Paddy Landau on 2009-04-02
> **egalvan said:**
> Interesting...

The same command suggested in back in post #2... :)
Damn, you're right. And that's something that I'd already tried, without success.

Well, in that case, I have absolutely no clue as to what made the difference! :confused:

---

### Post by nari.kaudle on 2009-05-31
> **Paddy Landau said:**
> Damn, you're right. And that's something that I'd already tried, without success.

Well, in that case, I have absolutely no clue as to what made the difference! :confused:
Well I know I tried the commands and they didn't work, but then I mounted the drive first, and voila, the command worked great. Whew! Thanks, everyone, this forum *rawks* :-D

---

