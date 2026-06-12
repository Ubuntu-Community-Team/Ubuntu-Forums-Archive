---
title: "samba question"
date: 2007-07-03
forum: Networking &amp; Wireless
---

### Post by rolfbeethoven on 2007-07-03
I have two accounts on my Windows XP box and each one has the My Documents folder shared with the "Allow network users to change my files" box checked.  From my Ubuntu Feisty box I try to mount the smb shares from the XP box.  Tyler mounts just fine, but I get an error when I try to mount the Katja share.  I think both accounts are identical.  

I have tried to mount the shares as tyler (with password), as katja (without password) and as an administrator named backuppc (with password).  In each case I can mount the tyler share but not the katja share.

What should I check?

Thanks for your help.


Here's the results from my Ubuntu box.

tyler@mythbox:~$ sudo mkdir /tyler
tyler@mythbox:~$ sudo mkdir /katja
tyler@mythbox:~$ sudo mount -t smbfs -o username=backuppc //192.168.1.111/tyler /tyler
Password:
tyler@mythbox:~$ sudo ls /tyler
Default.PLS  desktop.ini  install
tyler@mythbox:~$ sudo mount -t smbfs -o username=backuppc //192.168.1.111/katja /katja
Password:
tyler@mythbox:~$ sudo ls /katja
ls: /katja: Permission denied

---

### Post by rolfbeethoven on 2007-07-04
I should also mention two things:
I'm working with XP Home edition 

and on the linux side I get the following strange results:
tyler@mythbox:~$ ls -l /
?---------   ? ?     ?         ?                ? /katja
drwxr-xr-x   1 root  root   4096 2007-07-03 23:31 tyler
(I removed inapplicable directories)

What do the ?'s mean?

When I first create the directory with 'sudo mkdir /katja', it has normal permissions like you see in /tyler.  However after I try to connect to the share on XP, I get the funky '?------ ? ? ...' entry above.  When I unmount 'sudo umount /katja', then the file permissions return to normal.  How do I set the file permissions on the XP share so that I don't get this odd result?

Thanks.

---

### Post by scxtt on 2007-07-04
any reason katja doesn't use a password?

i'm guessing the permissions for /katja get messed up when you do the mount, it's unhappy about something ... are you sure it's shared as "katja" on the windows side?

i'd **sudo smbpasswd -a katja** and make the password the same as it it to log into windows ... then try again.

---

### Post by rolfbeethoven on 2007-07-04
I'm trying to mount the Windows XP share on my Linux box and I'm using the Tyler account on Linux, Samba and XP to mount.  Same username and same password.  Tyler is an admin account on XP.  Katja is a limited user account.

I did add a password to Katja and make the account an admin account.  Nothing worked.  It's like the XP files have a permissions setting that is rejecting the mount.  What can I do to troubleshoot and locate the issue?

---

### Post by scxtt on 2007-07-04
samba has to "allow" users to make those connections, that's the point of **sudo smbpasswd -a katja** - and it'll just rule that out as being a potential problem ... not sure if you did it or not ...

---

