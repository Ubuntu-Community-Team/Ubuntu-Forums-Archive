---
title: "Partition Question-Dual Boot w/ Windows 7"
date: 2010-08-25
forum: New to Ubuntu
---

### Post by meem1029 on 2010-08-25
I am planning on installing Ubuntu on my new laptop, but have a question about partitions.  Will I be able to access files (music, word docs, etc.) from my windows partition in Ubuntu and vice-versa.  I am wondering this because I am going to college and will likely want to be using both OS's for things and want to be able to listen to my music on both.  If I am unable to access files from the other partitions, can I just create another partition to store all my data with the Windows and Ubuntu ones used just for the OS and programs?
 
Thanks ahead of time for the help, and I'm looking forward to getting into the Linux world.

---

### Post by d5xtgr on 2010-08-25
Under Lucid Lynx, I am able to access files on the Windows partition by going under the Places menu.

---

### Post by meem1029 on 2010-08-25
Sweet, thanks for answering my question!

---

### Post by leprkhn on 2010-08-25
Ubuntu will have no problems accessing your Windows (FAT/NTFS) file systems. Windows, on the other hand, will now see your Linux file systems.

So... Using a FAT or NTFS file system as shared storage space between OSs will be your best bet (since Windows doesn't know how to play nice).

---

### Post by Verbeck on 2010-08-25
you can access the ubuntu partition in windows by using ext2explore. It can view ext4 as well.

```
http://www.softpedia.com/get/System/File-Management/ext2explore.shtml
```

---

### Post by oldfred on 2010-08-25
I prefer to have a separate shared NTFS partition like leprkhn's suggestion.

While you can read & write into the windows system partition, I have seen windows users recommend a separate data partition so when you have to reinstall windows you do not have to worry as much about your data ( you still should have good backups).

I just prefer not to write into another system unless I have to for repairs. Windows can be particular.  I read from my windows partition, but use a shared for anything I want to write from either system and want to share.

---

### Post by natravis on 2010-08-25
Another vote for a shared data partition. There are lots of guides out there, but here is a summary

Remove fluff, defrag, and shrink Windows partition (you need to free up at least 10G for Ubuntu then n GBs for your shared data partition)

Boot up with Live CD and run through the installer, and at the "where to install" screen, you need to create two partitions, one NTFS (mount it as /shared or /media/shared or something like that) and one ext4 (mount it as /).

Let installer run. Get updates. Reboot.

Boot back into windows and use disk management to mount the shared partition as a drive.

Victory

---

### Post by srs5694 on 2010-08-25
> **oldfred said:**
> I prefer to have a separate shared NTFS partition like leprkhn's suggestion.

While you can read & write into the windows system partition, I have seen windows users recommend a separate data partition so when you have to reinstall windows you do not have to worry as much about your data ( you still should have good backups).

I just prefer not to write into another system unless I have to for repairs. Windows can be particular.  I read from my windows partition, but use a shared for anything I want to write from either system and want to share.

I agree with oldfred. As a general rule, it's a Bad Idea to regularly read and write one OS's boot partition from another OS. Although the NTFS-3g driver that Linux uses for NTFS access is pretty reliable, it is reverse-engineered and could conceivably damage a partition pretty badly. (AFAIK, this isn't a common problem, but you don't want to be the unlucky 1 in a million who discovers such a bug!) The ext2fs/ext3fs drivers for Windows don't seem to get glowing reviews, although I don't know how dangerous they really are. Either way, to share data it's better to use a non-boot partition, thus minimizing the risk of damage should problems arise.

---

### Post by meem1029 on 2010-08-25
Thanks for all the help, Ubuntu is now up and running.  For some reason it didn't want to make the shared partition during setup, but I left space for it and am making it right now.

---

### Post by oldfred on 2010-08-26
Some info on shared partitions:

Mount, hide & link windows partition
[http://ubuntuforums.org/showthread.php?t=1397508](http://ubuntuforums.org/showthread.php?t=1397508)
Share Windows partition:
[http://lifehacker.com/348858/use-a-single-data-store-when-dual-booting](http://lifehacker.com/348858/use-a-single-data-store-when-dual-booting)
Link XP my docs
[http://www.techsupportalert.com/how_to_move_my_documents.htm](http://www.techsupportalert.com/how_to_move_my_documents.htm)

---

### Post by meem1029 on 2010-08-26
And the shared partition is now complete.  Thanks a ton guys!  That is awesome that you are willing to help new people like me that don't always know what's going on.

---

