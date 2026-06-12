---
title: "Unable to mount volume....?"
date: 2009-09-20
forum: New to Ubuntu
---

### Post by listerdl on 2009-09-20
I have been using my hard drive for ages between a windows machine and then using a linux ubuntu machine and it has worked perfectly then suddenly the ubuntu machine tells me that it it unable to mount the volume? 

The following messages then appear?

--------------------------

DBus error org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

------------------------

------------------------

$logFile indicated clean shutdown (0,0) Failed to mount '/dev/sdb1': Operation not supported Mount is denied because NTFS is marked to be in use. Choose one action: 

Choice 1: If you have windows then disconnect the external devices (etc etc)

Choice 2:  If you dont have Windows - i.e. ME - then use the 'force' option for your own responsibility by using: mount -t ntfs-3g /dev/sdb1 /nedia/FreeAgent Drive -o force

Or add the option to the relevant row in the /etc/fstab file: /dev/sdb1/media/FreeAgent Drive ntfs 3-g force 0 0

-----------------------

THANKS FOR ALL SUGGESTIONS!!!!!!!!!!!!!!!!!

---

### Post by Paqman on 2009-09-20
What's happened is that your NTFS drive hasn't been shut down cleanly. To avoid this, it's always best to unmount any NTFS partitions before shutting down.

If you still have a copy of Windows installed, all you need to do is boot into it then shut down. If you don't still have Windows, then you can try the command it suggested:
```
mount -t ntfs-3g /dev/sdb1 /nedia/FreeAgent Drive -o force
```

---

### Post by themusicalduck on 2009-09-20
The last time you used the drive in Windows, did it crash? Or did you have to hard reset the PC?

It looks like Windows didn't shut down properly, so if you boot back into Windows with the drive attached, and then shut it down again, hopefully it should fix it.

---

### Post by listerdl on 2009-09-20
> **themusicalduck said:**
> 

It looks like Windows didn't shut down properly, so if you boot back into Windows with the drive attached, and then shut it down again, hopefully it should fix it.

LEGEND - that fixed it ! T H A N K S for the advice.

---

