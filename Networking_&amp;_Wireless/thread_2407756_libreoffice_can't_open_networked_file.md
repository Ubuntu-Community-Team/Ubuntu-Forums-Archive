---
title: "libreoffice can't open networked file"
date: 2018-12-08
forum: Networking &amp; Wireless
---

### Post by bradhaack on 2018-12-08
I have an sftp connection open in the file manager (PCManFM),   I can open pdf files and txt files, but not libreoffice files (.ods).   I'm getting an error msg:
> General input/output error while accessing /run/user/1000/gvfs/sftp:host ...

if I try to open that file (/run/...) on the cmd line I get this:
> 
(soffice:8561): dbind-WARNING **: 17:32:21.985: Error retrieving accessibility bus address: org.freedesktop.DBus.Error.ServiceUnknown: The name org.a11y.Bus was not provided by any .service files

---

### Post by TheFu on 2018-12-08
Just a guess, but I think libreoffice requires a file system that supports flock().  sftp, scp, ftp, and batch file transfer protocols don't support that.  Let me google to check this guess.  [https://help.libreoffice.org/Common/Using_Remote_Files](https://help.libreoffice.org/Common/Using_Remote_Files) is the closest I could find.

However, if you have ssh/sftp, then you might have **sshfs**.  Often sshfs can handle things like this well. 
Just install the sshfs package, then you can create an empty directory, say ~/mount-point/, to use as the mount point, and finally use a commnd like this:
$ sshfs user@IP ~/mount-point

That's it.  To de-mount it, use the **fusermount -u  ~/mount-point** command.  Don't forget this because the mount won't be gone at logout.  Reboot or shutdown will clean it up.

Like all ssh-based tools, sshfs honors any ssh-keys and the settings in your ~/.ssh/config file.

Anyway, hope this is helpful and I hope this works.  It might not.

Update - I missed this: [https://help.libreoffice.org/Common/Using_Remote_Files_1#Connecting_to_FTP_and_SSH_servers](https://help.libreoffice.org/Common/Using_Remote_Files_1#Connecting_to_FTP_and_SSH_servers)  looks like you can use ssh directly.

---

### Post by bradhaack on 2018-12-09
> **TheFu said:**
> 

Update - I missed this: [https://help.libreoffice.org/Common/Using_Remote_Files_1#Connecting_to_FTP_and_SSH_servers](https://help.libreoffice.org/Common/Using_Remote_Files_1#Connecting_to_FTP_and_SSH_servers)  looks like you can use ssh directly.

thx, that worked

---

