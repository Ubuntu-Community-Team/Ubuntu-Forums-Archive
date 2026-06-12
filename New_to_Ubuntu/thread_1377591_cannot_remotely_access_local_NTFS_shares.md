---
title: "cannot remotely access local NTFS shares"
date: 2010-01-10
forum: New to Ubuntu
---

### Post by Matt26 on 2010-01-10
i have an NTFS share set up on ubuntu 9.10 using samba... if i try accessing the share from a windows computer i get the prompt for the username and password to access the share, but the username and password i type in isn't accepted- this should be my ubuntu username/password, correct?

i've tried restarting the samba service using ```
/etc/init.d/samba restart
``` after i modified the /etc/samba/smb.conf file with the 'usershare owner only = False' line but i still can't get access.

can anyone tell me what i'm missing here?  i think it's something simple, but i'm not sure what.

---

### Post by Charlietje on 2010-01-10
did you do:

```
smbpasswd -a *username*
```

---

### Post by Morbius1 on 2010-01-10
Did you set the share to require a username and password?

Post the output of these commands please:
[B]
net usershare info
testparm -s[/B]

Since it's an ntfs partition, how are you mounting it. Through nautilus or are you auto mounting it with fstab?

---

### Post by Matt26 on 2010-01-10
> **Charlietje said:**
> did you do:

```
smbpasswd -a *username*
```

thank you, that did the trick!

i read that the username also needs to be added to the smbusers file- is this step required for any particular reason?

---

### Post by Charlietje on 2010-01-10
with the "-a" option, you add the user.
No need to configure additional file for the users.

---

### Post by Sctmon on 2010-02-02
I had the same problem with an NTFS share on ubuntu 9.10 using samba. I could see the folder on computers running both windows and ubuntu but was being asked for a username and password which were not being accepted.
I tried setting the samba password to the same as my user account but it didn't work for me.

The drive was mounted at boot using fstab and was the second drive in a system running ubuntu. I could access the drive and folder directly on the computer it is installed in but could not access the shared folder using the same computer. I just got the same password prompt.

I had shared the folder on the NTFS drive by right clicking on a folder and selecting 'Sharing options' but I just noticed that there was no mention of it in smb.conf
I unchecked the share folder option in 'Sharing options' for the folder and added the following to smb.conf and now it works without any password prompt..

[Videos]
comment = Video Library
path = /media/vlib/Videos
public = yes
writable = no
creat mask = 0777
directory mask = 0777
force user = scott
force group = scott

Being a newbie could someone shed any light on why sharing via nautilus causes a problem?

---

### Post by superprash2003 on 2010-02-02
was this only for the NTFS share? samba works fine for other shares?

---

### Post by Sctmon on 2010-02-02
> **superprash2003 said:**
> was this only for the NTFS share? samba works fine for other shares?

No. It seems to do it for all samba shares set up by right clicking on the folders.  I hadn't noticed before because all of the folder in my home folder seem to have been automatically shared (listed in smb.conf) after installing samba and can be accessed without any problems

---

