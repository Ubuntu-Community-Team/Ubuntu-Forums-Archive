---
title: "External Hard Disk"
date: 2009-08-27
forum: New to Ubuntu
---

### Post by Hoom@n on 2009-08-27
I had an external HDD[NTFS] and I formatted it to ext4.(By GParted)
1-After the format I had 1.05GiB data in it! I had a folder, named "Lost", before the format and about 30GB in it; after the format "lost + find" or something like that with 1.05Gib. I used "rm * -f -r" to remove it; now I have no folder in it, but still 1.05GiB used!
2-I can't format it back to NTFS! I can format it to ext2, ext3, ext4, fat16, fat32, linux-swap & reiserfs, not NTFS! How can I format it back to NTFS?! I may want to use it later in Windows!
3-I think a repair is needed for my externall HDD, it's too slow and... How can I repair it?
Thanks.
**4-**Post #7

---

### Post by aktiwers on 2009-08-27
You deleted the files as root ! Thats why the files are in your Root trash.
/root/.local/share/Trash

Go there and delete them as root:
```
gksudo nautilus /root/.local/share/Trash
```

Delete the files again, and the space should be back.

If you want to run filesystem repair then run:
```
 chkdsk -ry /dev/DRIVENAME
```

If you don't know the drive name check it here:
```
df -h
```

---

### Post by Hoom@n on 2009-08-27
> **aktiwers said:**
> You deleted the files as root ! Thats why the files are in your Root trash.
/root/.local/share/Trash

Go there and delete them as root:
```
gksudo nautilus /root/.local/share/Trash
```Delete the files again, and the space should be back.

If you want to run filesystem repair then run:
```
 chkdsk -ry /dev/DRIVENAME
```If you don't know the drive name check it here:
```
df -h
```
Thanks for the answer.
First of all I used "sudo" because I couldn't use "shift+del" or "right click->Move to Trash".(when I used them, I got I don't have the permission to delete that files!)
And "gksudo nautilus /root/.local/share/Trash" didn't work! I got this(attached screen-shot):
-----
I'll use the other command(for repair) asap and tell the result here(or maybe some more questions!).
->Post #5
-----
Thanks a again.

---

### Post by insane_alien on 2009-08-27
the 'data' is actually just metadata for the filesystem. ALL filesystems will have various amounts of 'used' space when they ar created. this data is necessary for the filesystem to operate.

the lost and found folder is empty and is part of the filesystem.

it will only be filled with files if the filesystem tries to recover them and fails after an improper shutdown. this is done so it is possible that you might recover some of the damaged data. it is normal and nothing to worry about.

---

### Post by Hoom@n on 2009-08-27
> **insane_alien said:**
> the 'data' is actually just metadata for the filesystem. ALL filesystems will have various amounts of 'used' space when they ar created. this data is necessary for the filesystem to operate.

the lost and found folder is empty and is part of the filesystem.

it will only be filled with files if the filesystem tries to recover them and fails after an improper shutdown. this is done so it is possible that you might recover some of the damaged data. it is normal and nothing to worry about.
I deleted that! What happens now?! (Why used space is 3GB? Isn't it too big?)
-----
For "chkdsk -ry /dev/DRIVENAME" I got this: "bash: chkdsk: command not found" What's the problem?
-----
+How can I go back to **NTFS**?
-----
Thanks.

---

### Post by beastrace91 on 2009-08-27
There are various guides online to make GParted create a ntfs partition but personally I have found it doesn't work quiet right :/ It is simplest to just hook the external into a Windows system and format it on there.

~Jeff

---

### Post by Hoom@n on 2009-08-27
I can't paste  or create files in my external hard drive! What's the problem?! What should I do?!

---

### Post by Hoom@n on 2009-08-27
> **beastrace91 said:**
> There are various guides online to make GParted create a ntfs partition but personally I have found it doesn't work quiet right :/ It is simplest to just hook the external into a Windows system and format it on there.

~Jeff
Windows doesn't detect it as a hard drive! I tasted it on Windows XP and Windows 7, none of them found it! (after inserting the USB, nothing happened!)

---

### Post by beastrace91 on 2009-08-27
Use GParted to put the disc to unformatted space - then windows should be able to see it.

As for the not being able to write to, sounds like an ownership issue. Just unhook and reconnect the drive and it should solve that issue.

~Jeff

---

### Post by Hoom@n on 2009-08-28
> **beastrace91 said:**
> Use GParted to put the disc to unformatted space - then windows should be able to see it.

As for the not being able to write to, sounds like an ownership issue. Just unhook and reconnect the drive and it should solve that issue.

~Jeff
I gonna unformatted it; I'll tell the result.
-----
After reconnecting it I had the writing problem again.(also after restarting) I try formatting to NTFS; I hope formatting to NTFS will solve the writing problem.

---

### Post by Hoom@n on 2009-08-28
Windows didn't detect it when it was unallocated. I'm going to make a fat32 drive(using GParted) and test again.

---

### Post by Hoom@n on 2009-08-28
> **Hoom@n said:**
> Windows didn't detect it when it was unallocated. I'm going to make a fat32 drive(using GParted) and test again.
It's unbelievable! By formatting to fat32(with GParted) I wrote on the disk whit the speed of 10 to 11 MB/s!

---

### Post by beastrace91 on 2009-08-28
Just so you know I would recommend formatting the drive to ext3 or ntfs (the latter if it needs to be used on Windows boxes) as fat32 tends to run into issues on partitions over 4gigs.

~Jeff

---

