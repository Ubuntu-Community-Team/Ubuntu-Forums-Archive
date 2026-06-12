---
title: "Samba Shared Folders"
date: 2009-10-18
forum: New to Ubuntu
---

### Post by PistolPLC on 2009-10-18
So, I'm trying to get Ubuntu to act as a server for a shared external hard drive.  I've  been working with a couple of tutorials, and am now stuck.  

([http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605))

My general plan is to run my desktop (Ubuntu) as a server, and access my files (in an external hard drive "My Book") via my vista laptop.

I've done pretty much everything here, but I'm having problems with the passwords, usernames, and user accounts.  

I have Samba configured to share MyBook.  At least, there is a "MyBook" entry under the "DESKTOP" entry in the "network locations" in Vista.  When I try to open it, though, it asks for a username and password.  None of my combinations work, though.  I followed the steps in the tutorial above for adding users.  I've added two users, one with a username and password that correspond exactly to my Ubuntu name/password, and one that corresponds exactly to my Vista name/password.  

Neither of these work, though.  Am I missing something?  Did I not set the passwords properly?  Any thoughts or help would be appreciated!

PistolPLC
(Ubuntu 8.04)

---

### Post by cariboo on 2009-10-18
Have you set a samba passwd on the server?

---

### Post by PistolPLC on 2009-10-18
I think the only passwords I set at all were related to the creating users in Samba.  

From the tutorial >>>[INDENT]Time to add yourself as an samba user.

*NOTE: You will be asked for a password - make sure you use the same as you use for login!*

     Code:
     sudo smbpasswd -L -a your_username
sudo smbpasswd -L -e your_username 
In case you need other users to be able to access the share you need to add them to your system AND samba as well. Make sure you use the very same Windows usernames and passwords!
[/INDENT]I don't think I've created any other passwords.  Where/how/when would I have done that?  

I should also clarify - if I try to open the shared folder "MyBook" from the network places in Windows, I get an error that I don't have permission.  If I try to MAP the drive via add network places, I am asked for the username/password which then doesn't work.

Thanks for the help!

PistolPLC

---

