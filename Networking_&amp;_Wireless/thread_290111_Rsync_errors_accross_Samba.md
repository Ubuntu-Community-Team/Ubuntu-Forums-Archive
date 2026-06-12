---
title: "Rsync errors accross Samba"
date: 2006-10-31
forum: Networking &amp; Wireless
---

### Post by hawkbane on 2006-10-31
I am setting up a file server for the student radio station at my school.  At the moment, the server is all housed on one Dapper box (server1) with no backup.  We would like to mirror our data drive to another box (server2) so taht we have a mirror image of the data.  I currently have Samba set up on server2 and it mounted in my fstab on server1 as:
[I]
//server2/linux    /mnt/backup smbfs  credentials=/root/.smbcredentials    0    0[/I]

following the instructions on [http://ubuntuguide.org/wiki/Ubuntu_Edgy](http://ubuntuguide.org/wiki/Ubuntu_Edgy)

I then set up a shell script to call rsync and to copy the data from server1 to server2
[I]
rsync -a --delete --progress --stats /dir/source /mnt/backup[/I]

However when I execute this script I get the following errors:

[I]building file list ...
5 files to consider
Test/
rsync: failed to set times on "/mnt/backup/Test": Operation not permitted (1)
Test/Test02
           0 100%    0.00kB/s    0:00:00  (1, 40.0% of 5)
Test/Test01/
rsync: failed to set times on "/mnt/backup/Test/Test01": Operation not permitted  (1)
Test/Test01/Test01
           0 100%    0.00kB/s    0:00:00  (2, 80.0% of 5)
Test/Test01/untitled folder/
rsync: failed to set times on "/mnt/backup/Test/Test01/untitled folder": Operati on not permitted (1)
rsync: mkstemp "/mnt/backup/Test/.Test02.5ltIMO" failed: Operation not permitted  (1)
rsync: mkstemp "/mnt/backup/Test/Test01/.Test01.2dN0FI" failed: Operation not pe rmitted (1)
rsync: failed to set times on "/mnt/backup/Test": Operation not permitted (1)
rsync: failed to set times on "/mnt/backup/Test/Test01": Operation not permitted  (1)
rsync: failed to set times on "/mnt/backup/Test/Test01/untitled folder": Operati on not permitted (1)

Number of files: 5
Number of files transferred: 2
Total file size: 0 bytes
Total transferred file size: 0 bytes
Literal data: 0 bytes
Matched data: 0 bytes
File list size: 144
File list generation time: 0.001 seconds
File list transfer time: 0.000 seconds
Total bytes sent: 262
Total bytes received: 82

sent 262 bytes  received 82 bytes  688.00 bytes/sec
total size is 0  speedup is 0.00
rsync error: some files could not be transferred (code 23) at main.c(791)

[/I]

If anyone has a solution to this, I would be very greatful.
Thanx!

---

### Post by DaveBorealis on 2006-10-31
Hello,

Hope you don't mind me asking the easy (obvious) question, but have you tried saving a file to backup by hand so see if you have permission to do so?
```
touch /mnt/backup/hello.txt
```
And see if it saves.  If not, change permissions on the server.

Best regards,
Dave

---

### Post by hawkbane on 2006-10-31
Yes, we do have read/write permissions to the drive.  Using grsync I have successfully backed up the files to the server.  I think the problem lies in rsync trying to set the time attributes to the file.  From what I have been able to gleen from Google, this is a common problem when using rsync from a Linux to a Windows file system, FAT, FAT32, or NTFS.  The filesystem behind the Samba mount is ext3.  Is it a problem with in the smbfs that is used to mount the drive?

---

### Post by DaveBorealis on 2006-10-31
> **hawkbane said:**
> this is a common problem when using rsync from a Linux to a Windows file system, FAT, FAT32, or NTFS.

Sorry I couldn't help....

Incidentally, last I heard saving to and from NTFS from Linux isn't recommended as it's still a bit buggy.  Have you read anything about that in your Googling?

Dave

---

### Post by hawkbane on 2006-10-31
You are right, the implementation up until recently has been pretty unstable.  However, I have used ntfs-3G and have had good r/w success with it.  Obviously I would not put it on a production server, but it still works.

Thanx for keeping me honest ;)
~Hawkbane

---

