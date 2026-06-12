---
title: "Cannot access files on PVR after last samba update"
date: 2020-06-13
forum: Networking &amp; Wireless
---

### Post by naiqor0-people on 2020-06-13
:( Hi, Have an old Divco PVR that runs on linux, it is connected to modem/router by LAN, have been able to access files and folders on it from my desktop ubuntu (20.04) machine for years. But Samba up dated just recently Ubuntu machine can see PVR, see HDD, but when double clicked on comes back with dialog box "Unable to access location"  "Failed to mount Windows Share: Software caused connection abort"
Ubuntu can see and swap files with windows laptop and laptop can see and download files from PVR
The PVR uses Samba as well, and as it is old and no longer supported there is no chance of an up date at that end.
Can i add something to smb.conf to allow it to continue to read the HDD on PVR.
Thank you

---

### Post by TheFu on 2020-06-13
[https://ubuntuforums.org/showthread.php?t=2444358&p=13961480#post13961480](https://ubuntuforums.org/showthread.php?t=2444358&p=13961480#post13961480) may be useful but some of these connections have some subtle setting requirements.  Look for other recent forum posts by Morbius1.

---

### Post by naiqor0-people on 2020-06-13
Thank you Fu that worked a treat. The link to to Morbius worked, that is the second time he has helped me.

---

