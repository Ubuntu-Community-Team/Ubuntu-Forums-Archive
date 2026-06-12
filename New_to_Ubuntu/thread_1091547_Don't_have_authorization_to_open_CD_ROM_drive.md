---
title: "Don't have authorization to open CD ROM drive"
date: 2009-03-09
forum: New to Ubuntu
---

### Post by BDNiner on 2009-03-09
I got the weirdest error yesterday. I have a test account that i use on the computer when i am trying out new software and setups (so that i don't mess up my main profile) which has full admin rights. I was logged in to Gnome with my account. I wanted to listen to an audio CD so i put it in the drive.I then logged out of Gnome and logged into KDE using the test account. When i was done listening to the CD i could not eject it. The system basically said that only my main account has permissions to eject the CD. I had to log out of the test account and back into my main account to eject the CD! Does anyone know why this would happen?

---

### Post by SamNSane on 2009-03-09
Where in the file system is the drive mounted? If, for instance, it is under /media (as in /media/cdrom0) what is listed as the owner, and what are the permissions on the mount point?

---

### Post by BDNiner on 2009-03-09
It is under media/cdrom0, i am not at home so i cannot verify the permissions or owner at this point. I will post once i get home. But the permission are whatever default ubuntu sets up. I have never changed them.

I just thought that it is strange that one user mounts media on a CD drive but only that user can unmount it.

---

### Post by kanikilu on 2009-03-09
Is your test account in the "cdrom" group? You can check by logging in with your normal account and typing **groups testaccount** at the commandline. If it's not listed, you can add it with ```
sudo usermod -a -G cdrom *testaccount*
```

Or if you want to use a GUI, go to System > Administration > Users and Groups, click on your test account name, click Properties and then see if the box next to "Use CD-ROM drives" is checked under the User Privileges tab. You may have to "unlock" the users and groups administration dialog to check the box if it's not already.

---

### Post by BDNiner on 2009-03-10
Both my main account and the test account have the same privileges.I thought i figured it out, I thought i had switched users instead of logging out my main account and left the CDROM open in nautilus after switching to KDE. But this was not the case. I still get the error when i put the CD into the drive under gnome and then switch to another user running KDE (don't know if the DE matters) and then try and remove the CD. I can play the music on the CD fine under the other account.

---

