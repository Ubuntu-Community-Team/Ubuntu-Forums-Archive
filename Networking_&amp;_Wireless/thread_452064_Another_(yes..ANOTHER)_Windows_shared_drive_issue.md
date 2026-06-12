---
title: "Another (yes..ANOTHER) Windows shared drive issue"
date: 2007-05-22
forum: Networking &amp; Wireless
---

### Post by Jay_in_TN on 2007-05-22
OK--here is my issue:
I have a Windows XP machine which hosts a shared folder. It has the "Everyone" group removed from shared folder permissions for security over my wireless. I have added all the user names and passwords for all users to the users list on the host computer. This is required for other computers to see the shared folder. This way no one can see my shared folder over my wireless unless their user name and password are included as users on the host machine's user list. {This is how you secure a shared folder on a Win XP machine BTW--turn OFF "simple file sharing", which enables "permissions" for the shared folder (or drive) and allows you to add only the users that you specify. These users must be included on the user list of the host machine to enable access to the shared folder/drive by other computers on the network. Be sure to remove the "everyone" from the list if you need security} I hope that makes sense. 

My problem:
I have Ubuntu Edgy Eft installed on a laptop machine. I have included the username and password of the Ubuntu OS on the host Windows computer. When using the "Network File Browser" function I am able to see the "Windows Network" and then the "MSHOME" workgroup and when clicking on "MSHOME I see my host WIn XP computer ("Desktop" in my case). But when I click on Desktop I get the error "*_The folder contents could not be displayed._*"

I added the group "Everybody" back in the permissions on the host Win XP computer as a test and got the same error.

I really need access to my shared folder as nearly all of my files are there so I can access them from multiple computers within my network. I really like using Ubuntu. I have the network printing worked out. Most of the bugs worked out. But I need access to this shared folder.

Please help.

Thanks in advance,
Jay

---

### Post by Jay_in_TN on 2007-05-22
I installed smbfs but I don't know what it is or how to use it.
I really don't want to use script to access my shared folder. Can't I just point and click to it? I am able to see it in OpenSuSE!!! {This is a challenge to you to show me how to make it work!!!!}

Jay

---

### Post by Clay_Banger on 2007-05-23
if you want to mount the share as a local drive, this worked for me:
[http://ubuntuforums.org/showthread.php?t=288534]("http://ubuntuforums.org/showthread.php?t=288534")

However if you can't access the share via browsing to it, i doubt it will work.

---

### Post by Jay_in_TN on 2007-05-23
Its like that Phil Collins song....
"No reply at all....."

---

### Post by Jay_in_TN on 2007-05-23
thank you for your reply. I am reading the other thread now.
Jay

---

