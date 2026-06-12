---
title: "Setting up file sharing to windows computers"
date: 2008-11-11
forum: Networking &amp; Wireless
---

### Post by Rubicon421 on 2008-11-11
I can see/access files from the windows machines on my network but I can't even see my computer from them. When I try to share a folder I get the following error:

'net usershare' returned error 255: net usershare add: cannot share path /media/Back Up Drive/MUSIC as we are restricted to only sharing directories we own.
    Ask the administrator to add the line "usershare owner only = False" 
    to the [global] section of the smb.conf to allow this.

Is there a setting to fix this or would I have to edit a file manually or use the terminal? I dont know anything about programming or using the terminal so what is the simplest fix for this?

---

### Post by dmizer on 2008-11-11
Please open a command prompt, and perform this:
```
sudo chmod -R 777 /media/Back\ Up\ Drive/MUSIC
```
Then restart samba (or reboot).
```
sudo /etc/init.d/samba restart
```
Since the /media directory (and all it's sub directories) are owned by root, you have to change the ownership to allow read/write by your ubuntu login.

---

### Post by Rubicon421 on 2008-11-12
This sounds like exactly the fix that I need but I think there is an error in the code you gave me. The terminal gave me this error after the first line:
 cannot access `777': No such file or directory

---

### Post by dmizer on 2008-11-12
> **Kill Vista said:**
> This sounds like exactly the fix that I need but I think there is an error in the code you gave me. The terminal gave me this error after the first line:
 cannot access `777': No such file or directory

My mistake. It should be a capital R like so:
```
sudo chmod -R 777 /media/Back\ Up\ Drive/MUSIC
```

---

