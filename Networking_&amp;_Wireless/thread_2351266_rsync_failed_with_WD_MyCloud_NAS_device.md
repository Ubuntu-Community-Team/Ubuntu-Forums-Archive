---
title: "rsync failed with WD MyCloud NAS device"
date: 2017-02-01
forum: Networking &amp; Wireless
---

### Post by bill-lancaster on 2017-02-01
I wish to backup files from my Kubuntu machine to the NAS device (having used rsync for some time to backup to a usb memory stick).
I've mounted the drive at: /media/mycloud and it shows in Dolphin
This is the line for a test run of rsync:- ```
rsync -av --delete /home/bill/temp/ /media/mycloud
```

Am getting error:-
  failed: Permission denied (13)

This I believe is an ownership issue with the folder on the NAS device.

Any advice/help would be welcome

Kubuntu 16.04
MyCloud 2Tb

---

### Post by ajgreeny on 2017-02-01
Let's see the output of command ```
ls -la /media/mycloud
``` which will tell us the permissions carried by that NAS folder mountpoint.

Also, what filesystem is the partition on the NAS formatted to?

---

### Post by bill-lancaster on 2017-02-01
Thanks, here its is:
~$ ls -la /media/mycloud
total 4
drwxr-xr-x 2 root root    0 Jan 31 16:39 .
drwxr-xr-x 4 root root 4096 Feb  1 15:30 ..
drwxr-xr-x 2 root root    0 Feb  1 20:13 Shared Music
drwxr-xr-x 2 root root    0 Jan 31 19:51 Shared Pictures
drwxr-xr-x 2 root root    0 Jan 31 16:39 Shared Videos

---

### Post by SeijiSensei on 2017-02-01
The easiest solution is to run rsync as root with sudo.  It would be possible to mount the NAS filesystem in a manner that permits non-root writes, but it depends on the type of filesystem being mounted.  If it's an NTFS filesystem, you can add set the defaults in /etc/fstab to "[FONT=Courier New]defaults,umask=007,gid=46[/FONT]" which grants full read and write privileges to root and members of group "plugdev" with group ID 46.  Check that you're a member of that group by examining the file /etc/group and looking for the plugdev line.  If you're not, you can add yourself with "[FONT=Courier New]sudo adduser your_user_name plugdev[/FONT]".

A less secure alternative is to use "[FONT=Courier New]umask=000[/FONT]" which would grant everyone permission to write to the NAS device.

---

### Post by bill-lancaster on 2017-02-02
Thanks SeijiSensei
Using sudo get some sort of result.
```
sudo rsync -av --delete /home/bill/temp/ /media/mycloud/Ubuntu
```
has about 20 jpg files.  the result is:-
sent 166,328,712 bytes  received 899 bytes  66,531,844.40 bytes/sec
total size is 166,285,385  speedup is 1.00
But I don't see the files on MyCloud

---

### Post by bill-lancaster on 2017-02-02
Woops!  I forgot that the NAS drive wasn't permanently mounted so wasn't available when I booted the machine this morning.
Now sudo rsync works fine
Thanks again

---

### Post by ajgreeny on 2017-02-02
I am happy this is now working for you but I think it should have been better to change the ownership and permissions of the destination folders if they are on an ext# filesystem; you still did not tell us what that filesystem is.

The problem you will have with the files on the NAS is that you may not have permission to edit them without first changing their permissions.

---

### Post by bill-lancaster on 2017-02-03
Yes, am pleased to get backups going on the NAS device.
As to the file system, I don't know.  Here is what the manufacturer says.

"The file system on the My Cloud and other WD NAS devices support access from Windows, Mac and most Linux based computer systems through a SAMBA network sharing connection."

I was loath to tinker with the ownership of the NAS device because it is used for several other purposes on other machines.

Thanks

---

