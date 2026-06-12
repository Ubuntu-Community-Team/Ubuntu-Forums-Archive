---
title: "Deja Dup restored files unreadable"
date: 2010-06-11
forum: New to Ubuntu
---

### Post by Ralph L on 2010-06-11
Note:  The way I wrote this is very misleading.  Deja Dup restored files are indeed readable.  See the following posts.

Ralph

I have been experimenting with backing up my system with Deja Dup.  However, when I do a restore I can't read the files.  I have tried it with gedit generated files and with OpenOffice Writer generated files.  Both the Backup and the Restore complete with the "Successful" message and everything appears normal except the restored files are unreadable.

Running Deja Dup 14.2 under Ubuntu Karmic on a Dell D610 Latitude laptop.  I am dumping a few files from a folder into another folder, and restoring them to a third folder.  All folders are on my boot disk.

Anybody know how to fix this problem?

Ralph

---

### Post by mikix on 2010-06-11
I'm the author of Deja Dup.  This sounds troubling.  What do you mean by 'unreadable'.  Do you not have the permissions to read the files?  Are the files empty?  Are the files full of 'garbage' data?

Can you post examples of an original file and what it becomes?

---

### Post by Ralph L on 2010-06-12
I must apologize for the way I wrote this.  It was very misleading.  If I do a complete restore, I do get back the original files and they are indead readable.  The only problem is that ACLs and Extended User Attributes are not restored.

However, I want to be able to restore individual files if necessary and not to be required to restore all files.  I tried to do this by extracting the individual files from the backup folder "signature".  When I did this the resulting file was unreadable.  In the case of a gedit file gedit refusee to open the extracted file.  In the case of an odt file the file opened but was not readable.

Is there some way to quickly restore an individual file or folder?

Is there some way that ACLs and Extended User Attributes can be backed up and restore?  This would require that any file/folder with a changed ACL/x-attr be backed up.

Again sorry about my mis-representation of the problem.

Ralph

---

### Post by mikix on 2010-06-12
Correct, ACLs are not supported currently.  Duplicity, the backup script that does the heavy lifting in Deja Dup, has a feature request bug for it:  [https://bugs.launchpad.net/duplicity/+bug/558385](https://bugs.launchpad.net/duplicity/+bug/558385)

As for restoring a single file, yes, it's very possible.  Here's some documentation for it:  [http://live.gnome.org/DejaDup/Help/Restore/Revert](http://live.gnome.org/DejaDup/Help/Restore/Revert)

---

### Post by Ralph L on 2010-06-13
Thank you for your quick response.

I went to the web site you recommended and tried the procedures therein.  I was able to restore individual folders and files using the Terminal command "deja-dup --restore filename".  In the case of deleted folders/files I first had to put an empty folder/file (in the destination folder of the restore) of the same name as the one to be restored.

However, when I tried to do the right click on folder/file to be restored using Nautilus, there was no "Revert" in the menu.  In /usr/lib/nautilus/extensions-2.0 I found libnautilus-deja-dup.so,libnautilus-deja-dup.a, and libnautilus-deja-dup.la.   Do I need to install something else in my system for this to work?  Oh, I installed version 14.2 from the PPA in my karmic system.  Could that be part of the problem?

Also, I would appreciate any hints on managing backups with Deja Dup.  I see that the first backup I did was a full backup.  After that the files had an "inc" in the name--I presume for incremental. I am concerned about whether or not I have to periodically do a full backup. I have also been experimenting with LuckyBackup, and I like the way LuckyBackup (using rsync) keeps an up to date copy of my folders/files and keeps N rolling snapshot folders containing the old version of each changed/deleted folder/file.  Because of this design, the LuckyBackup user never needs to do another full backup after the initial one (as far as I know).  This saves the time needed to periodically do a full backup.  Does Deja Dup keep a current copy of all backed up files (such as LuckyBackup uses), or does it have some other method to make full backups unnecessary, or does it require time consuming periodic full backups?  Could you explain? 

Thanks
Ralph

---

### Post by mikix on 2010-07-16
Sorry for late reply.  I'm not sure why you don't see a Revert option in the context menu for files.  It should say "Revert to previous version..." somewhere near the bottom.

As for full vs incremental backups, Deja Dup will do periodic time-consuming full backups when it deems it wise.  It does not keep a current snapshot with rolling incrementals backward in time.  Rather it keeps an old snapshot and rolling incrementals forward in time.

The periodic full backups are to make sure that a corrupted incremental chain won't ruin the whole backup.

---

