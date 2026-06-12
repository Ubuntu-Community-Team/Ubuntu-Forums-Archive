---
title: "getting root access"
date: 2010-10-31
forum: New to Ubuntu
---

### Post by tbrownarcher on 2010-10-31
I'm using ubuntu 10.10 

Why can i not get into (/ - or - root) directory?  I would like to have complete access to any part of the file system.  I'm the only one here and have no need for protection.  I don't mind having to authenticate but this did not even give me the option to authenticate and get in.

I was never given the option to make an admin account and so i figured i was either admin or i would have option to go anywhere as admin .... 

can somone tell me what i'm doing wrong here ???

thanks,
nate

---

### Post by trikster_x on 2010-10-31
First:  What are you using to access the root folders?  If you are using nautilus, you will be able to read files, but not modify anything.


Second:  You are an admin, but even admins have a restricted amount of authority in Ubuntu.

---

### Post by sky_ceiling on 2010-10-31
you cant access these because you dont have the permissions to do so. If you want to access the file manager as root type 

sudo nautilus

Be aware that there is little reason for you to access these, and can screw up your system.

---

### Post by Verbeck on 2010-10-31
you should be able to get to the / directory, but not the /root directory (nothings there actually). root is different from the normal admin account and is locked by default in ubuntu. 

more info on root sudo @ [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

EDIT:
to open a nautilus window with temporary root privilages, run the followng in the run dialogue (alt+F2)

```
gksu nautilus
```

---

### Post by spiky001 on 2010-10-31
have yo tryed ```
gksudo nautilus
``` to acesess these folders

---

### Post by Rex Bouwense on 2010-10-31
> **tbrownarcher said:**
> I'm using ubuntu 10.10 

Why can i not get into (/ - or - root) directory?  I would like to have complete access to any part of the file system.  I'm the only one here and have no need for protection.  I don't mind having to authenticate but this did not even give me the option to authenticate and get in.

I was never given the option to make an admin account and so i figured i was either admin or i would have option to go anywhere as admin .... 

can somone tell me what i'm doing wrong here ???

thanks,
nate

Nate, I am hesitate to write this as you have been a member for a long time but here goes.  You do have access to root.  Grab a terminal and type sudo before your command.  You will be asked for your password.  Type it in and hit enter and you have root access.

---

### Post by uRock on 2010-10-31
> **spiky001 said:**
> have yo tryed ```
gksudo nautilus
``` to acesess these folders
+1 **gksudo nautilus** will allow you to go through folders with root permissions. Please be aware that if you click to delete anything in this user mode that it does not go to Trash, it is permanently deleted.
[COLOR=Red]_**That said, be careful what you do!**_[/COLOR]

---

### Post by tbrownarcher on 2010-10-31
Rex:

No need to be hesitant.  I need all the help I can get. I actually gave up on linux but the other day i reinstalled and so I'm still new.  I have a LOT to learn and and ready willing and maybe able.  

thanks for your help and to every one else also 
Nate

---

### Post by tbrownarcher on 2010-10-31
Thanks to everyone

This is solved 

thanks,
Nate

---

### Post by uRock on 2010-10-31
Another good reason not to judge people by post count or join date. We are all here to learn.

---

