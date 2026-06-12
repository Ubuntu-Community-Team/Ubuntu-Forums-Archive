---
title: "Application Sharing"
date: 2010-08-06
forum: New to Ubuntu
---

### Post by nkingcade on 2010-08-06
I have a number of applications in my account that I use for various purposes. I am the initial account on this machine. So, I have administrators rights (with sudo). I would like to share my applications with my wife. I don't have access to the drive where the applications are stored to install them. Nor can she see the application folders when she logs in. I know this is a administration issue. Can someone help me solve this problem. I want my wife to have access to the applications. I really want to be able to install the applications in my wifes account if possible.

---

### Post by mikewhatever on 2010-08-06
Don't you get graphical launchers in the menu for those apps? Are they graphical apps? Why access a folder to use them?

---

### Post by nkingcade on 2010-08-06
The executables are in folders that I can't access from my wifes logon

---

### Post by mikewhatever on 2010-08-06
Well, this is odd, and you don't seem to be eager to reveal much information. Generally speaking, to be able to access a folder, it needs to be readable by the user, in other words, 
```
chmod u+r user_name /path_to_folder
```

Much in the same manner, files a user needs to execute must be executable by the user, 
```
chmod u+x user_name /path_to_file
```

Being a non-admin user, your wife probably doesn't have sufficient permissions to access the folder you mentioned. Look at 'man chmod' for more info.

---

### Post by WelshChris on 2010-08-06
You say you have administrator rights using sudo, this is good - you're a regular user, like your wife.  Regular users can be members of groups, which can be named e.g. accounts, and groups can own directories - which is the point here.

Each member of a group can create, amend, view, delete and execute files in that group's directory even if it resides in another user's home directory, which is what you need.

A possible fly in the ointment is that the application in question may need to access or write to files elsewhere which your wife may not have permission to do so.

To create a group, #groupadd group_name.
To add a user to a group, #usermod -G group_name wife  and  #usermod -G group_name husband

To change a directory's group, #chgrp group_name directory

You may also need to change the directory's permissions to allow the group to access/edit files etc.  Probably best to use the GUI for that!

Seems complicated, so there's probably a more elegant solution out there - I'll no doubt be corrected!

---

