---
title: "password protect folders?"
date: 2009-10-21
forum: New to Ubuntu
---

### Post by insanity99 on 2009-10-21
how can i do this please i have a folder i want just me to have access to. thanks.

---

### Post by gareththegeek on 2009-10-21
You can use the chmod command to set permissions on files and folders.

[http://catcode.com/teachmod/chmod_1.html]("http://catcode.com/teachmod/chmod_1.html")

---

### Post by johnnydopefish on 2009-10-21
set the permissions on it so that only you can access it.  others will only be able to access it if they have root permissions or if you give them your password.

sudo chmod -R 700 /path/to/folder/

---

### Post by insanity99 on 2009-10-21
sorry i didn't explain correctly. then anyone in my house can still access the folder if i say loggin in correct? i want to make it so i can define a unique password, not my user password

---

### Post by TUOggy on 2009-10-21
Try checking out this thread:

[http://ubuntuforums.org/showthread.php?t=572365]("http://ubuntuforums.org/showthread.php?t=572365")

There are a few ways there you could try =)

---

### Post by earthpigg on 2009-10-21
> **insanity99 said:**
> sorry i didn't explain correctly. then anyone in my house can still access the folder if i say loggin in correct? i want to make it so i can define a unique password, not my user password

tsk tsk - any reason you don't log out and give roomates their own logins?

things you specifically do want to share (music, etc)... you can put it in /media/whatever or somewhere in /opt :D

---

### Post by mcduck on 2009-10-21
Changing the permissions of the folder is not really a good way to protect anything, since if the computer is booted with a live-CD the permissions are meaningless. Same thing if the hard drive is connected to a different machine and accessed from there.

If you need to *really* be sure that nobody gets access to a directory without the password then encryption is the only way.

For easy-to-use per-directory encryption you can install Cryptkeeper, which is a nice Gnome app that creates and manages encrypted directories in *extremely* simple way.

You'll find Cryptkeeper in the repositories, just install the package, start it from the Applications menu, and then click it's notification icon to create your encrypted directory. All you need to do is to select a name for the directory, and a password you wan to use for it.

(Of course if you can be sure nobody gets that level of physical access to your computer, and everybody using the system have their own user accounts, then just using the permissions would be enough.)

---

### Post by insanity99 on 2009-10-21
thanks cryptkeeper works well. 

and no, i am not trying to hide porn by the way lol.

---

