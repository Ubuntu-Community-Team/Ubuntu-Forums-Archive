---
title: "Can a tool in ubuntu help me open a .sax file from windows?"
date: 2010-02-14
forum: New to Ubuntu
---

### Post by anewguy on 2010-02-14
My brother in law's laptop got screwed up and he took it to a well-advertised place to get it fixed.  They were going to back everything up to a new external driver, then reinstall the OS and what they could from backups.  Over a week later they still needed the recovery disks, and my brother in law didn't have those.  So, he picked up the laptop and brought it home for me to fix.  I used ubuntu livecd to access the hard drive and backed up what he said he needed, then reformatted the drive and installed Windows and all the drivers from scratch.  After that was all done, he told me he needed his email, which using Juno.  Well, needless to say after what I had done there was no going back for that.  After searching the external hard disk, I found in the system volume information (I know, shouldn't be messing aroung in there) a couple of restore points, one of which I swear looks like it probably has his old email, but the files are all .sax, .ctx, etc., file extensions within the restore folder.  Does anyone know of any way in Linux to actually open the .sax files and be able to extract the email and attachments from it?  I went so far as to install Juno in my dual-boot just so I could see the email there.  After copying the files out of the restore file, I still don't see them in Juno mail, so I assume I'm probably missing a step.

Thanks in advance!!

Dave :)

Thanks in advance!

---

### Post by cariboo on 2010-02-14
Which email program created the files?

---

### Post by anewguy on 2010-02-15
It was all done with Juno, but I did some more digging and this is what I found:

[LIST]
[*]Juno actually has a user folder (in this case, "userxxxx") that contains the mail folders and files, and they are quite obvious.
[*]The .sax files are actually delivered with Juno and are not the mail folders or files.
[*]These files, within a _restore folder (created by system_restore taking a check point) are actually just the changes that happened last, and don't contain the Juno email.
[*]The well-advertised repair experts didn't back up the Juno mail when they created copies on the new external disk.  I never did either as I didn't know that my brother in law wanted those files, so all was lost after all.
[/LIST]

So, I'm marking this as solved since I know what everything is and that there are no mail backups from Juno to recover.

Dave ;)

---

