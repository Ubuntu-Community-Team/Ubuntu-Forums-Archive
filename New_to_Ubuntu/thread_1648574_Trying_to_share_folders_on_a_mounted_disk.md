---
title: "Trying to share folders on a mounted disk"
date: 2010-12-19
forum: New to Ubuntu
---

### Post by ENach on 2010-12-19
[SIZE=2]Hello,
I have Ubuntu 10.04 installed on my PC.  The machine has a 2nd internal hard drive which appears as a mounted disk in Ubuntu and does not contain any of the system or home folders that were added when I installed Ubuntu (I installed the OS on the former C: drive that had Windows on it.)  This 2nd drive contains folders/files that I am trying to share with another ***puter in my network that has WinXP on it.  While I can share folders on the 2nd hard drive on the Ubuntu machine and the WinXP machine can see the folders, I can't see or access the files through network shares on the WinXP machine.  When I check the permissions for the folders on the 2nd hard drive, the folder access for "Others" is set at "none" and I can't change it to either "list", "access" or "create and delete files".  
This is not a problem when I share subfolders (Documents, Music, Pictures, etc.) that are within the home folder.

Has this ever happened to anyone?  Is there a way to fix it?

Thank you.
[/SIZE]

---

### Post by rockerphil on 2010-12-19
i'm not too experienced with it, but i do know that in order to network an Ubuntu PC and a Windows PC you need the Samba server, perhaps someone more knowledgeable can help you, and remember, Google is your friend. hope this helps,

Phil

---

### Post by vangop on 2010-12-19
It's a good practice to reread your posts :)
Yours came out quite confusing.

> I can share folders on the 2nd hard drive on the Ubuntu machine and the WinXP machine can see the folders

> I can't see or access the files through network shares on the WinXP machine

So your problem is that u'r not able to access files on winXP? I guess not (coz what does it have to do with 2nd drive at all?)
Try to explain the problem a bit.

---

### Post by Morbius1 on 2010-12-19
Here's my best guess:

He's created a share on an NTFS or possibly FAT32 partition. He has no entry in fstab that mounts the partition itself automatically but instead mounts it as needed through Nautilus or Places. That will mount with permissions of 0700 meaning only the login user has access. Since he can't alter permissions on a Windows filesystem though linux ( other than a mount or fstab ) and since Samba has no override authority over Linux file permissions he's not able to share it across the network. 

There's two ways around this problem - one is to add an entry in fstab that will mount it with the required permissions - or you can use Samba itself to mask the remote user to appear to be the login user by using a line added to /etc/samba/smb.conf that looks something like this:
```
force user = login_user_name
```Where you put that line in smb.conf depends on what method of Samba sharing you are using - there are 2. If you post the output of the following commands it will tell us what method of Samba you are using and how you are using it:
```
net usershare info --long
``````
testparm -s
```

---

