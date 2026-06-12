---
title: "Samba Authentication Question"
date: 2008-09-04
forum: Networking &amp; Wireless
---

### Post by simonz on 2008-09-04
I am running Ubuntu 8.04.1 and have configured Samba with security = user, to share a folder to Windows XP Professional (sp3) Clients. The workgroup name = WORKGROUP.

The Ubuntu share is called 'membership' and valid users = test

In Ubuntu I have created an account called 'test' with password = 'password'.

On the Windows XP computer, I created an account called 'test' with password = 'password'.

At this point, the user 'test' on the XP computer is able to connect and access files in Ubuntu Share. 

Now, here is where things are confusing for me.  On the XP computer I changed the password to 'newpassword' and reboot and login again.  To my surprise, the XP computer is still able to access the Ubuntu share without changing the password on the Ubuntu computer.

How can this be?  Isn't there supposed to be a password hash exchange in the SMB protocol that will make sure they are the same and invalidate if different?  Any ideas how to fix this?

simonz

---

### Post by bab1 on 2008-09-05
Did you add the user to the smbusers database.  Samba athenticates users via its own database.  If you have not used the smbusers database then I'll bet you have allowed guest users and/or set the  the "bad user" user directive.  Bad user means Samba can't find the user in the database and uses an alternative.  Either way your in!  Not really good  unless you know your setup.

Make a file via the Windows share and check it's permissions on the Ubuntu using ```
ls -l
``` on the appropriate directory.

---

### Post by simonz on 2008-09-05
I think that I found the problem.  I guess that Samba doesn't use the real-time credentials and does does caching.  So after changing the computer accounts on the Ubuntu computer, I restarted Samba and the new authentication credentials became effecive.  

There are options in the smb.conf about synchronizing passwords.  I'll investigate this to see if this will eliminate the need to restart Samba after changing computer accounts.

simonz

---

