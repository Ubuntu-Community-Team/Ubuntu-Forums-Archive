---
title: "refusing to change ownership"
date: 2011-04-06
forum: New to Ubuntu
---

### Post by Sonic Reducer on 2011-04-06
i have a folder in my dropbox for all my computer science assignments. right now i am unable to change ownership from root, and this is preventing me from saving my files as i work on them.

the dropbox is located at _/data/Dropbox_ when i run ""sudo chown -R ryan /data" i hear some hard drive activity, but the owner is still root.

if i open nautilus as root (gksu nautilus), right-click the folder, and try to change the dropdown menu to anything other than root, it changes back to root instantly. i dont even click ok, i'll click some other owner and it will still just say root.

i should point out that **/data** is the mount point of a 500Gb hard drive. it looks like root owns the drive, should i change it to myself? this is a single-user computer, and all my personal data is on /data

ls -l /data
```
drwxrwx--- 1 root plugdev  4096 2011-04-05 21:58 *subfolder on /data*
drwxrwx--- 1 root plugdev  4096 2011-04-06 15:04 *subfolder on /data*
drwxrwx--- 1 root plugdev     0 2010-08-03 04:08 *subfolder on /data*
drwxrwx--- 1 root plugdev  4096 2010-10-18 17:48 *subfolder on /data*
drwxrwx--- 1 root plugdev 28672 2011-03-04 23:31 *subfolder on /data*
drwxrwx--- 1 root plugdev 28672 2011-03-14 23:32 *subfolder on /data*
drwxrwx--- 1 root plugdev 86016 2010-10-20 18:28 *subfolder on /data*
drwxrwx--- 1 root plugdev 36864 2011-04-06 05:31 *subfolder on /data*
```

---

### Post by techunit on 2011-04-06
Why do you have Dropbox located under data. If you have it there it will always require root! You should have it in the Home folder. You should purge dropbox from your system and reinstall using the installer found at the site.

---

### Post by Sonic Reducer on 2011-04-06
i put it there because i dual boot (that is, until recently when win7 got messed up). /data is an NTFS partition

that is retarded to allow you to place dropbox wherever you want, but not inform you that root is required for anywhere other than the default location. unbelieveable.

i bet that has something to do with my 2% filled dropbox still syncing after two days right?

---

### Post by Paqman on 2011-04-06
> **Sonic Reducer said:**
> /data is an NTFS partition


That's your problem. NTFS filesystems don't support permissions. Whatever the partition gets mounted as in Linux is what the permissions will be for all folders on that partition. You can work around this by changing the entry in /etc/fstab for /data. You can set it so that it has very open permissions, or you could set it so that it was owned by your user, either would do the same thing.

---

### Post by Sonic Reducer on 2011-04-06
> **Paqman said:**
> That's your problem. NTFS filesystems don't support permissions. Whatever the partition gets mounted as in Linux is what the permissions will be for all folders on that partition. You can work around this by changing the entry in /etc/fstab for /data. You can set it so that it has very open permissions, or you could set it so that it was owned by your user, either would do the same thing.

could you elaborate on this a little bit? i've had a longtime problem with the recycle bin (can't use it, have to delete immediately).

since i dual boot between ubuntu 10.10 and win7 (both single users) would it be better to leave it completely open or to limit access somehow?

---

### Post by Paqman on 2011-04-07
How is your NTFS partition mounted? If you go and check the file /etc/fstab, does it have an entry in it for this partition? If you're not sure just copy the whole file and paste it in here.

/etc/fstab is the File System Table, it tells the system what partitions and things to mount automatically at boot, and how they should be mounted. By adjusting the options for the line relating to your NTFS partition you can give yourself tighter or looser permissions. Because NTFs lacks a permissions system of its own this can't be done on afile by file or folder by folder basis like it can in a proper Linux filesystem. You have to do the whole lot when it's mounted.

---

### Post by Sonic Reducer on 2011-04-08
the line pertaining to /data from my fstab

```
# <file system>		<mount point>	<type>	<options>				<dump>	<pass>
UUID=A6961885961857DF	/data		ntfs	defaults,nls=utf8,umask=007,gid=46	0	0
```

---

### Post by rosencrantz on 2011-04-08
I assume from what you posted that the plugdev group is the one with group id 46?
If you change umask to 077 in the fstab line and add yourself to the plugdev group (sudo usermod -g plugdev <yourusername>), you should be fine.

---

### Post by Sonic Reducer on 2011-04-08
> **rosencrantz said:**
> I assume from what you posted that the plugdev group is the one with group id 46?
If you change umask to 077 in the fstab line and add yourself to the plugdev group (sudo usermod -g plugdev <yourusername>), you should be fine.

```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system>					<mount point>	<type>	<options>				<dump>	<pass>
proc						/proc		proc	nodev,noexec,nosuid			0	0

# / was on /dev/sda5 during installation
UUID=c4501cd7-1db9-4e26-9695-8662201120d6	/		ext4	errors=remount-ro			0	1

[B]# /data was on /dev/sdb1 during installation
UUID=A6961885961857DF				/data		ntfs	defaults,nls=utf8,umask=077,gid=46	0	0[/B]

# /windows was on /dev/sda1 during installation
UUID=3D546BD82C4C63CD				/windows	ntfs	defaults,nls=utf8,umask=007,gid=46	0	0

/dev/sda3					none		swap	sw					0	0
```

i also ran the terminal command you listed, now /data isn't mounting. it says i dont have permission

```
ryan@ryan-desktop-ubuntu:~$ cat /etc/group | grep 46
plugdev:x:46:ryan
```

---

### Post by rosencrantz on 2011-04-08
Terribly sorry! I forgot umask permissions are inverted. Revert to 007. 
Were you a plugdev member already when you had the file saving problems?
If you don't care about user access control, you can also delete the umask=007 and the gid bit. Default is rwx for all.

---

### Post by Sonic Reducer on 2011-04-08
> **rosencrantz said:**
> Were you a plugdev member already when you had the file saving problems?
not unless i was by default

> **rosencrantz said:**
> If you don't care about user access control, you can also delete the umask=007 and the gid bit. Default is rwx for all.

so if i were to modify the two NTFS partitions to this:
```
# <file system>					<mount point>	<type>	<options>		<dump>	<pass>
# /data was on /dev/sdb1 during installation
UUID=A6961885961857DF				/data		ntfs	defaults,nls=utf8	0	0

# /windows was on /dev/sda1 during installation
UUID=3D546BD82C4C63CD				/windows	ntfs	defaults,nls=utf8	0	0
```

i wont break anything?

---

### Post by rosencrantz on 2011-04-08
I don't think you'll break something. Back up your original fstab just in case. As long as you don't fiddle with the permissions for your root partition, the worst that can happen is a refusal to mount and you can always revert to a working fstab.
The following works for me, btw. You won't need the German locale and for recent systems there is no difference between ntfs and ntfs-3g
```
# NTFS data partition
UUID=AEF243C5F243908F   /windows/D   ntfs-3g defaults,locale=de_DE.UTF-8 0 0

```
It might be worth it to try again with the original fstab and being a plugdev member, but if you don't care about user access restrictions, it won't make a difference.

---

### Post by Sonic Reducer on 2011-04-08
> **rosencrantz said:**
> I don't think you'll break something. Back up your original fstab just in case. As long as you don't fiddle with the permissions for your root partition, the worst that can happen is a refusal to mount and you can always revert to a working fstab.
The following works for me, btw. You won't need the German locale and for recent systems there is no difference between ntfs and ntfs-3g
```
# NTFS data partition
UUID=AEF243C5F243908F   /windows/D   ntfs-3g defaults,locale=de_DE.UTF-8 0 0

```
It might be worth it to try again with the original fstab and being a plugdev member, but if you don't care about user access restrictions, it won't make a difference.

i removed the uid and gid stuff from my fstab, and i'm back to square one. still can't change permissions on /data/Dropbox (dropbox is uninstalled so it's just a folder now) and still can't use the trash.

---

### Post by rosencrantz on 2011-04-08
You can't change ownership ever on NTFS partitions, the filesystem doesn't support linux-style ownership and permissions. The only way is to mount the whole partition *as if* it belonged to a specific user/group with certain permissions  - by editing fstab. 
However, by now you should have full read/write/execute access for everybody, have you tried it?
Is the Trash a Windows system folder? In that case, I don't quite see how to use it from Linux. Or are you just trying to delete files from the partition? That should work if you fstab is set up correctly.

---

### Post by Sidewinder1 on 2011-04-08
Sonic, this is totally Off Topic and just a friendly suggestion as I do not have the specific answer to your question. You may wish to edit your profile from Fiesty to Maverick; this should prevent nit-wits like me from thinking that a solution would be found by upgrading to a current, supported version of Ubuntu.  :D

My wife tells me that my advice is worth exactly what I charge for it. :lolflag:

Side

---

### Post by rosencrantz on 2011-04-08
Oh - if you're actually still *on* Feisty or something comparably old, you might want to use ntfs-3g instead of ntfs. Historically, ntfs-3g is the driver with read/write support.

---

### Post by Sonic Reducer on 2011-04-08
> **Sidewinder1 said:**
> Sonic, this is totally Off Topic and just a friendly suggestion as I do not have the specific answer to your question. You may wish to edit your profile from Fiesty to Maverick; this should prevent nit-wits like me from thinking that a solution would be found by upgrading to a current, supported version of Ubuntu.  :D

My wife tells me that my advice is worth exactly what I charge for it. :lolflag:

Side

i'm on 10.10, thanks for pointing out i haven't updated that since 7.04 was current lol

---

### Post by Sidewinder1 on 2011-04-08
No prob.; at least I helped a little...
Side

---

