---
title: "Trouble with new partition in Ubuntu"
date: 2009-02-08
forum: New to Ubuntu
---

### Post by Hastings101 on 2009-02-08
When I installed Ubuntu awhile ago I had a dual-boot with Windows, today I've removed Windows completely (no more use for it) and created a new partition in a program called Gparted so I could store files on it.  I set the filesystem as Ext3 and everything went well. However, after mounting the Filesystem I receive the error:

 "Internal Error: No mount object for mounted volume"

  After clicking ok and then trying again it loads the partition, but a folder with 'Lost+Found' appears.  When trying to click on the folder, 

"You do not have permissions necessary to view the contents of "lost+found"."

When I try to delete the file, nothing happens.When trying to move afile (for example, opera.deb) onto the partition I get the following error:

"Error opening file '/media/My Programs/opera_9.63.2474.gcc4.qt3_i386.deb': Permission denied
 
  Is there anyway to get the partition working? I'm still very new to Ubuntu after using it  a few months (and it has always been point and click, hardly used terminal) so I'd appreciate it if you could explain how as well.

---

### Post by drs305 on 2009-02-08
You need to become the owner of the partition:
```

sudo chown -R *[COLOR="DarkRed"]your_user_name:your_user_name[/COLOR]* /[COLOR="DarkRed"]mountpoint.location[/COLOR]
Example: sudo chown -R dave:dave /media/data

```

*lost+found* is a system folder created to hold file fragments found during fsck checks.

If this partition is listed in fstab, make sure you have created the above mount point and then run the "chown" command. With "defaults" as the option, the partition will be mounted to the partition you created and owned by you.

A typical fstab entry for an ext3 partition would look like:
```

UUID=XXX-XXXXXX-XXX /media/data ext3 defaults 0 2

```

For an ntfs partition (for user 1000):
```

UUID=XXX-XXXXXX-XXX /media/data ntfs auto,users,uid=1000,umask=027,utf8  0 0

```

---

### Post by Hastings101 on 2009-02-08
Thank you very much, that solved all the problems I was having:D

---

