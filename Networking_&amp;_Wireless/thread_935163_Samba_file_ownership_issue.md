---
title: "Samba file ownership issue"
date: 2008-10-01
forum: Networking &amp; Wireless
---

### Post by JordanCB on 2008-10-01
Howdy,

I am having some issues

```

security = user
username map = /etc/samba/smbusers

[Photos]
        comment = Photos
        path = /home/shares/Photos
        writeable = yes
        guest ok = yes
        public = yes
[Marketing]
        comment = Marketing Files
        path = /home/shares/Marketing/
        writeable = yes
        force group = users

```

Using this basic smb.conf , I am having issues on the "Photos" share.  Whenever a user creates new files or copies files onto the share, they become the exclusive owner of the file and any other users with access can not modify the files.   Is there any way to set a group mask so that all files within the share belong to a group?  Or any other work around for this?  Are the create masks, dir mask, etc the way to go for this?  Any help is appreciated.  Thank you!

-- Jordan

---

### Post by Julius1988 on 2008-10-01
check this it might help you
[http://ubuntuforums.org/showthread.php?t=933491](http://ubuntuforums.org/showthread.php?t=933491)

---

### Post by dward526 on 2008-10-01
Just a thought

Look into changing the following permissions in your smb.conf

# File creation mask is set to 0700 for security reasons. If you want to
# create files with group=rw permissions, set next parameter to 0775.
;   create mask = 0700

# Directory creation mask is set to 0700 for security reasons. If you want to
# create dirs. with group=rw permissions, set next parameter to 0775.
;   directory mask = 0700


Try 7770 for full control in the masks

---

### Post by JordanCB on 2008-10-01
Awesome,

Thanks for the quick replys.  I appreciate the help!

-- Jordan

---

