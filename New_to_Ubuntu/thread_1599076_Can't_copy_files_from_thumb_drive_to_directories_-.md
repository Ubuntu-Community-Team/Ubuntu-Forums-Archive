---
title: "Can't copy files from thumb drive to directories - only Desktop"
date: 2010-10-17
forum: New to Ubuntu
---

### Post by okorkie on 2010-10-17
Hi,

I seem to have a fairly easy problem, but I can't figure out what the solution is.

I have recently installed Ubuntu 10.10 and I am trying to copy files from my Windows PC to Ubuntu via WinSCP and I receive a 'Permission Denied' error.  I am successfully able to ssh from my Windows PC to Ubuntu, so that works fine.

As well (and this is probably related), if I take a thumb drive with files and try to copy files from the thumb drive to the /opt directory (or any other directory), it gives me an error.  ** However, I can copy them over to the desktop without a problem.

Any suggestions as to what the problem is?  Thanks in advance!

---

### Post by thunk77 on 2010-10-17
Well if you are logged in as a user and not root, it's natural that you don't have access to system folders (such as /opt).
The only place you have read/write permissions is your home folder (includes Desktop).

However, I don't understand why you would want to write files inside system folders. You can just create subdirectories inside /home/*your username*/ and store everything there. Even link them to your Desktop for easy access.

Here is some info for the Linux Filesystem you may find useful
[http://www.freeos.com/articles/3102/](http://www.freeos.com/articles/3102/)

Regards

---

### Post by ptn107 on 2010-10-17
It's a permissions thing.  /opt is owned by root, not you.  If you want to copy files to /opt press ALT+F2 and type:
```
gksu nautilus /opt
```
and drag and drop as normal.  Be careful as you'll be running nautilus with root permissions so you could really mess stuff up if you're not careful.

---

### Post by Joshwaa on 2010-10-17
Or 
```
sudo nautilus
```

---

### Post by okorkie on 2010-10-17
ah, that makes sense.... I will just copy everything to /home/user.

What I was trying to do was put all of my personal files into /opt/user, and hence the problem.  

I guess I should be putting them into /home/user, although in Windows I never use the My Documents or My Downloads folder... I always downloaded everything to C:\user

Thanks

---

### Post by JKyleOKC on 2010-10-17
The simplest way to think of it, in my opinion, when making the transition from Windows, is to think of your home directory (/home/username) as being your C: drive. It holds not only your data (instead of something like "My Documents") but your personalized configuration files (replacing the "user" part of the registry). In a default setup, you'll have full control over everything in your home directory, and of course the super-user (root or sudo) has control over everything in the system.

Usually when you install a program using the system tools, the program files themselves will go into /usr/bin or a subdirectory there, and will be owned by the super-user so that neither you nor any malware that gets into your user account can modify them. System-wide configuration files will go into /etc or a subdirectory and also will be owned by the super-user, again protecting them against accidental change (including by malware).

The Documents, Desktop, Downloads, and Pictures directories are all created automatically within your home directory, so that you can work with them. You can also rename or delete them if you please; you've got much more freedom to make things go YOUR way here than Windows allows, but with that goes the freedom to mess things up if you don't take care... Best ask here about anything doubtful, before doing it. And enjoy!

---

### Post by okorkie on 2010-10-19
Ah, thanks for the info JKyleOKC... that certainly clarifies things and now I know for future.

Thanks again!

---

