---
title: "Grsync Permissions Question"
date: 2009-08-28
forum: New to Ubuntu
---

### Post by mikodo on 2009-08-28
Hello everyone,

I thought I would copy the question and response,(below) I asked at OPByte Forums about Preserving Permissions with Grsync. Piero Orsoni's response is that he thinks by not preserving permissions one would simply end up with files in the receiver with the same permissions as it's sender, though it may change with the OS you are using, though. 

Has anyone used Grsync with Ubuntu and able to answer the question about permissions?

The man rsync indicates that rsync does not require super-user privileges.

I have included a screenshot below of the setup of Grsync, specific to the Permissions.

Question to OPByte Forums:

I've read the man rsync on receiving permissions. If, in the Basic Options of Grsync the Owner, Permission and Group are not preserved, will the Receiver of the data (in my case, just my external HD), be owned by root? I am used to having to enact chmod with Sbackup now, when I return data from backup. I want to know if I will have to change the same permission from root with returning data with Grsync.

Basically, what will happen in my case with permissions, if I do not enable the three Preserve options?

I use GNU/Linux OS; Ubuntu 8.04

Piero Orsoni's response:

hello,

by not using the permission preservation options, I think you'll simply end up with files with the same permission as if you created them with another program (like text editor or whatever).
what those permissions are, depends on your system configuration, but usually it will be your user, your group and rw-rw-r (readable and writable by you and your group, read-only by others). It may change with the OS you are using, though.

Piero Orsoni - OPByte  Site Admin

---

### Post by vanadium on 2009-08-28
All I can say is that i would agree with the response you got. To preserve ownership and permissions, you can use the -a option.

That rsync can be run without root permissions is not suggesting that you can copy anything anywhere. You will be able to copy data for which you have the permission to read to a destination where you have the permission to write.

---

### Post by presence1960 on 2009-08-28
```
rsync -r -t -p -o -v --progress --ignore-existing -c -l -H -z /media/data /media/usb_backup/rsync/ 
```

That is the command I use for rsync to run my incrementals. To run the first full back up I did so without --ignore-existing.

When I used grsync I preserved permissions and owner and never had a problem moving files from the back up usb drive to internal disk.

FYI the directories in that command are:
/media/data =  my data storage internal HDD
/media/usb_backup/rsync = rsync is the directory on my external usb HDD that gets the backup

---

### Post by mapes12 on 2009-08-28
Permissions and all that will depend upon what you're syncing. I use Grsync to backup my user account to a second HDD. Attached are my settings. Notice the exclude in Advanced options. That hidden file has caused me problems in the past. You could also exclude thumbnails to save space.

---

### Post by mikodo on 2009-08-28
Thank you for the replies. 

I think I get it now. To allow the receiving HDD to resend data from backup, Permissions must be Preserved as the same as they were sent including any data written and read in super user (Preserve owner option). This is done before the rsync execution. 

Basically: Preserve the owner, permissions, and group and any data returned will be exactly the same as it was before backup; Be it super user or otherwise and I can continue using it as if it was never backed up. 

I will have to read about the hidden file difficulties and command in Additional options. Thanks for that tip also.

---

### Post by mapes12 on 2009-08-28
> **mikodo said:**
> Thank you for the replies. 

I think I get it now. To allow the receiving HDD to resend data from backup, Permissions must be Preserved as the same as they were sent including any data written and read in super user (Preserve owner option). This is done before the rsync execution. 

Basically: Preserve the owner, permissions, and group and any data returned will be exactly the same as it was before backup; Be it super user or otherwise and I can continue using it as if it was never backed up. 

I will have to read about the hidden file difficulties and command in Additional options. Thanks for that tip also.The receiving HDD will always resend the data from the backup. Don't worry about that. Even if you haven't ticked the preserve permissions boxes and all that the data will still come back for sure. The reason the preserve permissions and all that is ticked is so that we don't have to amend the permissions when the data comes back. And that's very easy to do. Just ```
gksu nautilus
``` R/C the folder/file in question, select permissions and change them back again. Easy! Don't get hung up about ticking boxes in Grsync the main thing is that you back up your stuff. Permissions and all that are easy to sort out so long as you have your data somewhere.

That pesky hidden file will alway be recreated everytime you login but can be a pain in the butt if it's in your backup files. Do a test Grsync backup and restore to see for yourself with a dummy user account.

---

### Post by mikodo on 2009-08-29
> **mapes12 said:**
> The receiving HDD will always resend the data from the backup. Don't worry about that. Even if you haven't ticked the preserve permissions boxes and all that the data will still come back for sure. The reason the preserve permissions and all that is ticked is so that we don't have to amend the permissions when the data comes back. And that's very easy to do. Just ```
gksu nautilus
``` R/C the folder/file in question, select permissions and change them back again. Easy! Don't get hung up about ticking boxes in Grsync the main thing is that you back up your stuff. Permissions and all that are easy to sort out so long as you have your data somewhere.

That pesky hidden file will alway be recreated everytime you login but can be a pain in the butt if it's in your backup files. Do a test Grsync backup and restore to see for yourself with a dummy user account.


Just got back from working an afternoon shift. Thanks for the clarifications. I see; Preserving Permissions before allows the permissions to be properly set for data returning from backup. To have not Preserved Permissions first would mean that I would have to set the permissions upon returning. An easy way would be to just right click the returning file and change Permissions then. This is what I already do with Simple backup now, because the returning data is returned in root. Again thanks, this all must have been like "trying to pull a pig through mud", to get me to understand this.

Just set a dummy user account for the first time. Will follow advice and test Grsync with it to, see the problems with that "pesky file".

Mike

---

