---
title: "automount a fat32 partition"
date: 2009-09-16
forum: New to Ubuntu
---

### Post by poliltimmy on 2009-09-16
I got help with the ntfs on one machine, now I need a little help with my strictly Ubuntu machine running 8.10. I want it to auto mount sda1 automatically on start up. Thanks in advance. You guys are great!


john@john-desktop:~$ sudo blkid
[sudo] password for john: 
/dev/ramzswap0: TYPE="swap" 
/dev/sda1: LABEL="DATA" UUID="4A00-6DB6" TYPE="vfat" 
/dev/sda5: UUID="701f16e3-2201-4480-9846-0680a294dd73" TYPE="ext3" 
/dev/sda6: TYPE="swap" UUID="d1d8be5f-3969-427c-adc2-4709044755de"

---

### Post by scragar on 2009-09-16
```
sudo su
mkdir **/media/mount_point**
echo "LABEL=DATA **/media/mount_point** vfat defaults 0 1" >> /etc/fstab
exit
```Change media/mount_point to wherever you want.

---

### Post by poliltimmy on 2009-09-16
> **scragar said:**
> ```
sudo su
mkdir **/media/mount_point**
echo "LABEL=DATA **/media/mount_point** vfat defaults 0 1" >> /etc/fstab
exit
```Change media/mount_point to wherever you want.

I'm sorry but, I do not understand the mount_point. Do I just write DATA in that spot again?

---

### Post by scragar on 2009-09-16
No, that's the mount point, where on the file system should the files on that partition be accessed from? Judging by the fact that you don't know I'd keep to /media which means it will show up on the desktop, the folder name would be what it's called, so **/media/meap** would show up on your desktop called **meap**.
Be sure to edit both lines to say the same mount point, otherwise you'll get errors when booting because the mount point doesn't exist.

---

### Post by drs305 on 2009-09-16
> **poliltimmy said:**
> I'm sorry but, I do not understand the mount_point. Do I just write DATA in that spot again?

The partition you want to mount is named "DATA". But you have to mount it somewhere, so you have to create a mount point for it. You can name it anything you want. If you create the mount point (folder) in /media, you will see it on your Desktop. If you place it in /mnt, you won't. Either way, your DATA partition would be accessible.

For example, let's just say you want to create the mount point "data" and see it on your desktop. The commands from the previous post would be:
```

mkdir /media/data
echo "LABEL=DATA /media/data vfat defaults 0 1" >> /etc/fstab

```

You probably want to own the mount point as well, although this is not technically required:
```

sudo chown -R yourusername: /media/data

```

---

### Post by bodhi.zazen on 2009-09-16
See also :

[How to fstab - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?&t=283131")

---

### Post by poliltimmy on 2009-09-16
> **drs305 said:**
> The partition you want to mount is named "DATA". But you have to mount it somewhere, so you have to create a mount point for it. You can name it anything you want. If you create the mount point (folder) in /media, you will see it on your Desktop. If you place it in /mnt, you won't. Either way, your DATA partition would be accessible.

For example, let's just say you want to create the mount point "data" and see it on your desktop. The commands from the previous post would be:
```

mkdir /media/data
echo "LABEL=DATA /media/data vfat defaults 0 1" >> /etc/fstab

```

You probably want to own the mount point as well, although this is not technically required:
```

sudo chown -R yourusername: /media/data

```

I got this on the last command
chown: changing ownership of `/media/Data': Operation not permitted

It did show up on the desktop but no write permissions

---

### Post by drs305 on 2009-09-16
> **poliltimmy said:**
> I got this on the last command
chown: changing ownership of `/media/Data': Operation not permitted

Case is important in Linux. "Data" does not equal "data". If the mount point was created as "data", that is how you have to run the next command as well.

---

### Post by poliltimmy on 2009-09-16
> **drs305 said:**
> Case is important in Linux. "Data" does not equal "data". If the mount point was created as "data", that is how you have to run the next command as well.

john@john-desktop:~$ sudo chown -R john:/media/data
chown: missing operand after `john:/media/data'
Try `chown --help' for more information.

should this be correct?

---

### Post by scragar on 2009-09-16
> **poliltimmy said:**
> john@john-desktop:~$ sudo chown -R john:/media/data
chown: missing operand after `john:/media/data'
Try `chown --help' for more information.

should this be correct?

No colon and include a space.
```
sudo chown -R john /media/data
```

---

### Post by poliltimmy on 2009-09-16
> **scragar said:**
> No colon and include a space.
```
sudo chown -R john /media/data
```

I get this error when tring to copy files to the partition. I really appreciate all the help!!

The folder "Seether" cannot be copied because you do not have permissions to create it in the destination.

Another error for text files
Error opening file '/media/data/automount.odt': Permission denied

---

### Post by scragar on 2009-09-16
Mind me asking if you could check the perms in long mode:
```
ls -l /media /media/data
```

---

### Post by poliltimmy on 2009-09-16
> **scragar said:**
> Mind me asking if you could check the perms in long mode:
```
ls -l /media /media/data
```

this is what I got.

john@john-desktop:~$ ls -l /media /media/data
/media:
total 28
lrwxrwxrwx  1 root root     6 2009-05-05 11:38 cdrom -> cdrom0
drwxr-xr-x  2 root root  4096 2009-05-05 11:38 cdrom0
drwxr-xr-x  2 root root  4096 2009-05-05 11:38 cdrom1
drwxr-xr-x 11 root root 16384 1969-12-31 19:00 data
drwxr-xr-x  2 root root  4096 2009-09-16 17:01 Data

/media/data:
total 66992
-rwxr-xr-x  1 root root   107847 2009-04-21 12:20 Consumer Authorization Form.pdf
-rwxr-xr-x  1 root root    10554 2009-04-17 22:26 Course%20Sel%20Worksheet%20for%202009-10.pdf
-rwxr-xr-x  1 root root 24526726 2008-12-09 10:45 crossover-games-demo_7.1.0-1_i386.deb
-rwxr-xr-x  1 root root 24906480 2008-12-09 10:45 crossover-pro_7.1.0-1_i386.deb
-rwxr-xr-x  1 root root    39297 2009-03-30 15:53 lees unemployment.odt
drwxr-xr-x 11 root root    16384 2009-05-08 13:10 Music
-rwxr-xr-x  1 root root 18280169 2009-02-04 02:26 pict0030.mp4
drwxr-xr-x  3 root root    16384 2009-09-01 23:57 Picture
drwxr-xr-x 26 root root    16384 2009-09-01 23:32 Pix
drwxr-xr-x  4 root root    16384 2009-06-24 13:09 Programs
drwxr-xr-x  4 root root    16384 2009-05-05 13:55 recycler
drwxr-xr-x  2 root root    16384 2009-09-02 00:38 ricky
drwxr-xr-x  3 root root    16384 2009-05-05 13:55 System Volume Information
-rwxr-xr-x  1 root root   304128 2008-08-08 20:04 Thumbs.db
drwxr-xr-x  2 root root    16384 2009-09-01 23:59 untitled folder
-rwxr-xr-x  1 root root   231233 2009-03-30 18:41 WMT_2010R_INS_6P.pdf

---

### Post by scragar on 2009-09-16
Wonder why it still belongs to root?

Try editing fstab(be carefull) and edit the last line to read something more like:
```
LABEL=DATA /media/mount_point vfat **users,uid=1000,gid=100,utf8,dmask=027,fmask=137** 0 1
```This should give you ownership of the drive I think(you will need to unmount and remount the drive```
sudo umount /dev/sda1
mount /dev/sda1
```I think the last part should work without needing sudo, but if it doesn't adjust accordingly).

---

### Post by bodhi.zazen on 2009-09-16
You can not chown or chmod a FAT or a NTFS partition.

To change ownership and permissions you have to un - mount the partition and re - mount it with new permission.

---

### Post by poliltimmy on 2009-09-16
> **scragar said:**
> Wonder why it still belongs to root?

Try editing fstab(be carefull) and edit the last line to read something more like:
```
LABEL=DATA /media/mount_point vfat **users,uid=1000,gid=100,utf8,dmask=027,fmask=137** 0 1
```This should give you ownership of the drive I think(you will need to unmount and remount the drive```
sudo umount /dev/sda1
mount /dev/sda1
```I think the last part should work without needing sudo, but if it doesn't adjust accordingly).

Bingo! Thanks a bunch. Mounts on boot, with rw perms. Fantastic! No more running back and forth!  :popcorn: :guitar:

---

### Post by swerdna on 2009-09-16
For others who cruise to these parts: [HowTo Mount a Fat32 / Vfat Partition Read Write in Ubuntu & Kubuntu]("http://ubuntu.swerdna.org/ubufat32.html")

---

### Post by bodhi.zazen on 2009-09-16
> **swerdna said:**
> For others who cruise to these parts: [HowTo Mount a Fat32 / Vfat Partition Read Write in Ubuntu & Kubuntu]("http://ubuntu.swerdna.org/ubufat32.html")

I see you like that link.

The umask value on that blog is sub-optimal. Better to use a dmask and fmask.

dmask and umask vaules were given on this thread and in the fstab linky I gave as well.

Too bad there is no place to leave feedback on your linky =)

---

### Post by swerdna on 2009-09-16
> **bodhi.zazen said:**
> I see you like that link.

The umask value on that blog is sub-optimal. Better to use a dmask and fmask.

dmask and umask vaules were given on this thread and in the fstab linky I gave as well.

Too bad there is no place to leave feedback on your linky =)

I have given three options for directories: drwxrwxrwx (windows like), drwxr-xr-x (Linux like) and drw-r----- (paranoid). That's enough IMHO. I've thought about your suggestion and don't see it as optimal for a windows-like partition. I would think, given the origin, normal uses and lack of "real" permissions inherent in a fat32 partition, that 777 would be the best general compromise for a fat32 mount. It's a sub-optimal filesystem after all.

My 2 cents worth.

Why do you like to have the files non-executable by default?

---

### Post by bodhi.zazen on 2009-09-17
Because if you use a terminal, and list your files, they are all green if they are all executable.

IMO it makes no sense to mark all files as executable, lol

It is a minor point.

---

### Post by swerdna on 2009-09-17
> **bodhi.zazen said:**
> Because if you use a terminal, and list your files, they are all green if they are all executable.

IMO it makes no sense to mark all files as executable, lol

It is a minor point.

I like your point and will adjust my tutorials, for both ntfs and vfat, to recommend a more Linux-like mount -- thanks

And your other suggestion re comments: I'll add a place for interaction with ppl making comments in the next month or so (time is so limited)

---

### Post by drs305 on 2009-09-17
Since we've covered so much territory in this thread, I'll just review one of the commands I gave:

> chown -R username**:** /media/mount
The colon was not a typo. The colon is a shorthand way of designating the user & group.  *username:* is the same as username:username, which would change both the folder to an owner of *username* and also make it belong to the group *username*.

As I mentioned, the ownership isn't necessary in this case since the ownership of the mount point is determined at mounting (root via the fstab setting with *defaults*or the owner specified by uid=XXXX if specified in the mounting options on the fstab line).

---

### Post by swerdna on 2009-09-17
> **drs305 said:**
> Since we've covered so much territory in this thread, I'll just review one of the commands I gave:


The colon was not a typo. The colon is a shorthand way of designating the user & group.  *username:* is the same as username:username, which would change both the folder to an owner of *username* and also make it belong to the group *username*.

As I mentioned, the ownership isn't necessary in this case since the ownership of the mount point is determined at mounting (root via the fstab setting with *defaults*or the owner specified by uid=XXXX if specified in the mounting options on the fstab line).

I understood that the ownership is set immutably in the mount command, so that a separate chown command has no effect. So are you presenting this chown command for interest, even though it's not relevant or even valid when used on a FAT32 filesystem? Am I missing the point here?

---

### Post by drs305 on 2009-09-17
> **swerdna said:**
> I understood that the ownership is set immutably in the mount command, so that a separate chown command has no effect. So are you presenting this chown command for interest, even though it's not relevant or even valid when used on a FAT32 filesystem? Am I missing the point here?

I made the post simply as a clarification of the use of the colon. As I stated in my original post, chowning the mount point is not technically required, or required in any way for that matter. The "technically" may have created a false impression.

A folder doesn't know what it's going to be used for, and the folder sits on the system whether it is mounted or not. When *I* manually create a folder, I prefer to own it. (Yes, I know semantically I don't recreate the folder in /media without root's help with the sudo command.) When the system creates a folder, I let the system do what it wants. I often use a single mount point for a variety of uses, and mount many different file systems on it. And of course for mounting linux file systems it does matter.  I see more advantages to owning the point than not.

---

