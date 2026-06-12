---
title: "network backup issue"
date: 2010-01-25
forum: New to Ubuntu
---

### Post by Matt26 on 2010-01-25
i have a USB 2.0 backup drive plugged into my ubuntu 9.10 system used for storing backups of some windows systems over my home network.

i have norton ghost 15 installed on the windows systems that are being backed up, and for some reason the backups will fail eventually with an error message about the network path no longer being available.

if i plug the backup drive into one of my windows systems the backups complete successfully.

so my guess is there's an issue with performing the backups using the ubuntu system, but i'm not sure what that would be.

does anyone have any suggestions as to how i can fix this?

---

### Post by cariboo on 2010-01-25
Can your Windows computers see the Ubuntu system in My network Places? If so, how is the drive setup in /etc/samba/smb.conf?

---

### Post by Matt26 on 2010-01-25
> **cariboo907 said:**
> Can your Windows computers see the Ubuntu system in My network Places? If so, how is the drive setup in /etc/samba/smb.conf?

no, the ubuntu system isn't viewable from my network places on my windows systems.

i haven't added anything related to this drive in the smb.conf file.

---

