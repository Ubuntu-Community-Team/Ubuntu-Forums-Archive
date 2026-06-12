---
title: "deleted samba files reappear"
date: 2008-06-25
forum: Networking &amp; Wireless
---

### Post by snoopy66 on 2008-06-25
I use rdiff-backup to backup my Kubuntu servers to a Windows machine.  Even though rdiff-backup is designed to preserve Linux file metadata while copying directly to the Samba share, it ran into problems.  To get around the problem, I created a ext3-container file with the commands below:

> # # Create an empty 5 GB container file
# dd if=/dev/zero of=backup-`hostname`.ext3 bs=1024 count=5242880

# # Place an ext3 file system into the container file
# mkfs -t ext3 backup-`hostname`.ext3

Next, I copied the container file to my Windows server (e.g., to //MyServer/MyShare/), and then I do a double mount as follows:

> # smbmount //MyServer/MyShare /mnt/smb -o credentials=./.smbmount
# mount -o loop -t ext3 /mnt/smb/backup-`hostname`.ext3 /mnt/backup

Finally, I issue the rdiff-backup command and unmount the share as follows:

> # rdiff-backup /home /mnt/backup/home
# umount /mnt/backup
# smbumount /mnt/smb

Here's the rub:  I do this exact thing on two different servers - one is running Kubuntu 6.06 and the other is running Kubuntu 8.04.  From 6.06, the operation works perfectly, but on 8.04, I witness some extremely strange behavior.  Using the example above, if I issue the following commands,

> # smbmount //MyServer/MyShare /mnt/smb -o credentials=./.smbmount
# mount -o loop -t ext3 /mnt/smb/backup-`hostname`.ext3 /mnt/backup
# cd /mnt/backup
# ls -lR

I see that the 'home' directory and all of its contents created by rdiff-bacup are present.  Then I issue the following commands:

> # cd /mnt/backup
# rm -fR home
# ls -l

As expected, I see that the 'home' directory is gone.  Next, I issue the following commands:

> # # Unmount the share
# umount /mnt/backup
# smbumount /mnt/smb

# # Remount the share
# smbmount //MyServer/MyShare /mnt/smb -o credentials=./.smbmount
# mount -o loop -t ext3 /mnt/smb/backup-`hostname`.ext3 /mnt/backup
# ls -lR /mnt/backup

And the 'home' directory magically reappears.  It is as if some buffer did not flush before the dismount so the home directory was not actually deleted.

Is anyone else experiencing this peculiar problem with 8.04?  Has anyone found the solution?  Any help would be greatly appreciated.

---

### Post by snoopy66 on 2008-07-01
I found a simple answer to this problem, and I would like to share it in the event anyone else encountered it.

Very simply, prior to issuing the umount and smbumount commands, I issue a sync command.  For example:

> # sync
# umount /mnt/backup
# sync
# smbumount /mnt/smb 

It's nice when someone can be helpful, so if you find this info useful, please let me know.

Thanks.

---

