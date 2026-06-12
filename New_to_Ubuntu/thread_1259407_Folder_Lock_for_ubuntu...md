---
title: "Folder Lock for ubuntu.."
date: 2009-09-06
forum: New to Ubuntu
---

### Post by karthick87 on 2009-09-06
I need a software like Folder Lock for ubuntu..Is there any software available for ubuntu?

---

### Post by Bodsda on 2009-09-06
> **getyourkarthick said:**
> I need a software like Folder Lock for ubuntu..Is there any software available for ubuntu?

Restricting access to folders can be done with permissions, like:
```
sudo chmod a-rwx ~/private
```
after that command, only root can access that folder.

Hope this helps,
Bodsda

---

### Post by karthick87 on 2009-09-06
I am using both windows XP and ubuntu,what i want to do is i want to lock a folder  of NTFS partition,so that windows user cant able to access the folder..

---

### Post by Bodsda on 2009-09-06
> **getyourkarthick said:**
> I am using both windows XP and ubuntu,what i want to do is i want to lock a folder  of NTFS partition,so that windows user cant able to access the folder..

As far as I know, you would have to do that from windows because XP cannot read ext2/3 filesystems and NTFS does not understand the concept of unix file permissions.

Kind regards,
Bodsda

To restrict access on windows, you would need to have xp pro, right click on the folder > permissions tab > select their username > read/write/execute/full control set to deny

I am not going to go into how to do this on xp home as this is an Ubuntu support forum. not a Windows support forum.

---

### Post by mcduck on 2009-09-06
You can also use encfs and Cryptkeeper to create encrypted directories..

[http://ubuntu-unleashed.com/2007/08/howto-encrypt-your-private-files-with-encfs-cryptkeeper-gnome-applet.html]("http://ubuntu-unleashed.com/2007/08/howto-encrypt-your-private-files-with-encfs-cryptkeeper-gnome-applet.html")
[http://ubuntuforums.org/showthread.php?t=148600]("http://ubuntuforums.org/showthread.php?t=148600")
[http://tom.noflag.org.uk/cryptkeeper.html]("http://tom.noflag.org.uk/cryptkeeper.html")
(note that both guides are quite old, and if you are running latest Ubuntu version all the programs in the guides should already be available through Ubuntu's package management. Also the Fuse module mentioned in the encfs HowTo is already loaded by default.)

edit: Actually, just forget about the guides, simply install cryptkeeper package with apt-ger/Synaptic. Then go to Applications/System Tools/Cryptkeeper to start it, and a lock icon appears in the notification area. Click that icon and you'll get option for creating a new encrypted folder.

edit2: Oh, you are looking for a Windows app? Can't help you there.. :)

---

### Post by scrooge_74 on 2009-09-06
What about putting that folder on a Linux Box, then use samba and give out permits accordingly?

---

