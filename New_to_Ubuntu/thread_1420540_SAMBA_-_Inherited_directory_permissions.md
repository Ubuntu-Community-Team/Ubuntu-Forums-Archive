---
title: "SAMBA - Inherited directory permissions?"
date: 2010-03-03
forum: New to Ubuntu
---

### Post by ShinyAndy on 2010-03-03
Scenario is that I have a group folder on my linux box, the "group" (all windows clients) can access the folder fine and can read/write fine. However if user "A" creates a folder or file in that group folder only they can then write to the folder. I tried using umask in the samba.conf but it didnt seem to work. Can anyone explain how I can force any new files and folders created in the "group" folder to inherit the permissions/access from the parent folder

---

### Post by JKyleOKC on 2010-03-03
You can edit the /etc/samba/smb.conf file to add a line in the shares configuration for that group folder, to read "create mask = 0666" which will give all users read and write permission regardless of who created the file. Since smb.conf is owned by root, you'll have to use "gksudo gedit" from a terminal to open the editor with root privileges, and be very careful not to make other changes. After saving the file and returning to the terminal window, type "testparm" to verify that your smb.conf file is still in good shape.

You could change that "0666" value to the permissions value of the shared folder, to do exactly what you ask -- but if the final digit is "6" it won't make any difference in accessibility since that's the permission for "everyone". A value of "0664" would allow group members to read and write but non-members would have only read privileges, while "0660" would prevent non-members from even reading the files.

---

### Post by michwill on 2010-05-12
Hi All,

I'm having similar issues with my install of Ubuntu 9.10 and its samba permissions.  Logging in and reading works fine.  However, creation of new directories by users restricts access for other users.  For instance, if Bob (Windows user who maps the drive) creates a folder in the directory, Jane (Mac user that simply smb mounts) can read from it, but can't write to it -- and vice versa.  I then must go CHMOD 777 the directory for everyone to be happy.  I've tried editing the "create/directory mask", and "force" options in the smb.conf file but this doesn't seem to help.

I'm about to resort to CRONTABing a recursive chmod routine, although I'm sure this isn't the fix.  How do I get all new items to always be 777?  Does anyone have any suggestions to fix this ever-occurring situation?

FYI, the uname info is as follows:
Linux corefilestore 2.6.31-20-generic-pae #58-Ubuntu SMP Fri Mar 12 06:25:51 UTC 2010 i686 GNU/Linux

Regards.

---

