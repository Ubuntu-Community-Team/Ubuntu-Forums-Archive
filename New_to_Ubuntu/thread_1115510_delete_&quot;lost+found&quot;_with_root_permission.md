---
title: "delete &quot;lost+found&quot; with root permissions?????"
date: 2009-04-03
forum: New to Ubuntu
---

### Post by Ddog8877 on 2009-04-03
Hi I installed a hard drive to my box and it has got a lost+found folder in it.  The hard drive was from my old system that crashed! 
Iv tried every thing I can think of and I just cant get it removed?
Iv tried to wipe the disk several times and format it but that still doesnt work?  What do I do?

---

### Post by Bölvaður on 2009-04-03
This is normal, you may want to try to ignore that directory.
Also drinking green tea is good, so ignore the directory AND drink green tea :p is what you should do.

---

### Post by Ddog8877 on 2009-04-03
Ok but it wont let me do anything with the hard drive?  I cant save anything to the harddrive?

---

### Post by asmoore82 on 2009-04-03
> **Ddog8877 said:**
> Hi I installed a hard drive to my box and it has got a lost+found folder in it.  The hard drive was from my old system that crashed! 
Iv tried every thing I can think of and I just cant get it removed?
Iv tried to wipe the disk several times and format it but that still doesnt work?  What do I do?

"lost+found" is in every ext3 filesystem;
even if you delete it, subsequent filesystem checks with re-create it.

---

### Post by rhcm123 on 2009-04-03
> **Ddog8877 said:**
> Hi I installed a hard drive to my box and it has got a lost+found folder in it.  The hard drive was from my old system that crashed! 
Iv tried every thing I can think of and I just cant get it removed?
Iv tried to wipe the disk several times and format it but that still doesnt work?  What do I do?

lost+found is a folder that contains all the data on a filesystem if it crashes. It is readable only by root as it was designed so that if the system crashed the system admin would be the only one capable of repairing the damage.

**_THESE COMMANDS CAN KILL YOUR FILE SYSTEM! RUN AT YOUR OWN RISK  AFTER *CAREFULLY* READING THROUGH THEM!!!_** :O

**IF THIS IS ON YOUR MAIN PARTITION:**
Do not delete it. **DO NOT DELETE IT.** It is a very important system file that should not be messed with. _IT MAY OR MAY NOT BE REPLACED BY FILE SYSTEM CHECKS_
[U]
**IF THIS IS ON AN OLDER FILESYSTEM:**[/U]
**IF THIS FILESYSTEM IS FORMATTED AS EXT2, EXT3, DO NOT DELETE THE FILE**
All ext filesystems keep a lost+found directory in the root of the filesystem. (e.g. if your filesystem is mounted to /media/drive, then it would be /media/drive/lost+found.).** DO NOT DELETE IF THIS DRIVE IS CURRENTLY FORMATTED AS EXT!1**

**IF OTHERWISE:**
Well, if otherwise... (durr... i forgot :) )run gksudo nautilus to start nautilus as root. see if there are any files you want to keep, then you can delete the folder.

---

### Post by Ddog8877 on 2009-04-03
Ok but is there any way that I could use the hard drive so I can save file to it?

---

### Post by SunnyRabbiera on 2009-04-03
> **Ddog8877 said:**
> Ok but it wont let me do anything with the hard drive?  I cant save anything to the harddrive?

By default Ubuntu locks the user out of the core folders of the system, only your home directory is where you are allowed to edit and add files without root permission.
There is a logic to this, on XP the default user is the administrator and therefore vulnerable to attack.
Ubuntu bypasses this by disabling the root account, its better for you and your computer trust me.
If you really need to edit core files you can enable root access by using sudo in a terminal but its not advised for new users.

---

### Post by Ddog8877 on 2009-04-03
Ok its a second hard drive. and I want to use it for extra storage! How do I run nautilus?

---

### Post by asmoore82 on 2009-04-03
> **Ddog8877 said:**
> Ok its a second hard drive. and I want to use it for extra storage! How do I run nautilus?

to give yourself/everyone access to the drive,
**while it is mounted** and assuming it's mounted at */media/drive*:
```
sudo chmod 1777 /media/drive
```

alternatively, you might want to give yourself a single folder on the drive
and only grant access to that folder:
```
sudo mkdir /media/drive/$USER
sudo chown $USER:$USER /media/drive/$USER
sudo chmod 0750 /media/drive/$USER
```

of course you could also make these changes from a root instance of nautilus:
```
gksudo nautilus
```
and right-click -> Properties -> permissions

---

### Post by SunnyRabbiera on 2009-04-03
as suggested if you want admin access open a terminal and copy and paste this:
gksudo nautilus

Just take caution

---

### Post by Ddog8877 on 2009-04-03
Hi I tried that and nothing worked? I cant get any permission on the hard drive.  It is set as a media drive?

---

### Post by Ddog8877 on 2009-04-03
hi I tried that and nothing worked? I cant get permissions on the hard drive at all?  And the drive is set to media drive!

---

### Post by rhcm123 on 2009-04-03
> **Ddog8877 said:**
> hi I tried that and nothing worked? I cant get permissions on the hard drive at all?  And the drive is set to media drive!

run the following commands, were drive is the mount point and user is your user name:
```
sudo chmod 777 /media/drive
sudo chown user:user /media/drive
sudo umount /media/drive
sudo mount /media/drive
```

---

### Post by asmoore82 on 2009-04-03
If you are going the graphical route, you can't right-click on the device itself -
you need to open it up as a folder and right-click on the white-space inside it and "Properties"

---

### Post by Ddog8877 on 2009-04-03
Ok thank you every body really what a relief!:p   I ran nautilus and just changed the permissions on the file. Now everything is working fine and I can use the hard drive.  Thank You!

---

