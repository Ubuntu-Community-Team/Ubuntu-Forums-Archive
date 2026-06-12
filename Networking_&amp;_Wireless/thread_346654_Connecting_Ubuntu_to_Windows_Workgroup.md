---
title: "Connecting Ubuntu to Windows Workgroup"
date: 2007-01-26
forum: Networking &amp; Wireless
---

### Post by mastertaco on 2007-01-26
Is it possible to connect Ubuntu to a Windows Workgroup instead of a Domain:confused:

---

### Post by rmartz on 2007-01-26
Yep. You will need to install Samba. 

There are several ways of doing it, the easiest for me was to go to System->Administration->Shared Folders. Select a folder to share, then it will ask if you want to install nfs or smb. Install the smb.

Once installed, you will need to do a little setup. You can search the forums for Samba and get detailed instructions.

Hope that gets you started.

---

### Post by bigken on 2007-01-26
in a terminal

sudo aptitude install samba 

sudo smbpasswd -e yourname

sudo smbpasswd -a yourname

---

### Post by bigken on 2007-01-26
then just right click on the folders you want to share 

or go to system aministration shared folders :D

---

### Post by mastertaco on 2007-01-26
Ok Ill use your advice tonight thank you :D

---

