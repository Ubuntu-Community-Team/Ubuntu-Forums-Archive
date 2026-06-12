---
title: "permission confusion"
date: 2010-08-04
forum: New to Ubuntu
---

### Post by beew on 2010-08-04
Hi,

I have installed some programs iin my home folder, but somehow the directories of these programs are owned by root. As a result when I run the programs they cannot modify the files in their own directories (since I am not running the program as root )  I can run these programs by simply typing the name of the programs, but if I type```
 $ sudo progname
``` I get an error message saying the command doesn't exist, as the programs are installed in my home folder.

So, running the program requires accessing the files in the program's directory and that requires root privilege, but sudo doesn't run the program as theybelongs to me (desktop user) rather than root,--even though I am actually the same dude as this guy "root". It gets all confusing.

1. How did this happen? 

2.How to fix it, so the I can either run the program as supersur so that I (the program) can access the forbidden files?

Another thing, I was trying to fix this myself I went into System > Administration> users and groups and changed my profile from desktop user to administrator. But when I tried to change it back I got an error message saying that I was  the only user of the computer so I couldn't lose my administrative status.

 Is there a way to change it back? Should I?

---

### Post by Peter09 on 2010-08-04
You can use the chown command to change the ownership of the files to you.
 
[http://www.computerhope.com/unix/uchown.htm](http://www.computerhope.com/unix/uchown.htm)
 
you will need to use sudo to run the command to give you priviledges to change ownership.
 
Also, the reason that you cannot run the program in sudo  is that it is not in the defined 'path'. for executables.
 
If you did
 
```
sudo ./prgname
```
it will work - if you are in the same directory as the program.

---

### Post by mcduck on 2010-08-04
> **beew said:**
> Hi,
1. How did this happen? 

When you installed the programs you used "sudo" in some place where you didn't need it.

If you unzip an archive using sudo, you unzip it as root and the extracted contents are owned by root. If you create a directory with sudo the directory will be owned by root. If you execute some installer script with sudo the script runs as root and all the files it creates are owned by root. And so on.

The good practice, when you aren't sure if you need sudo or not, is to first try without it. If you get an error about permissions, *then* you can try again with sudo.

---

### Post by beew on 2010-08-04
Hi, Peter

> Also, the reason that you cannot run the program in sudo  is that it is not in the defined 'path'. for executables.
 


But then how come I could run it without sudo? I actually did cd into the directory where the executable is , so I think I was in the path.

---

### Post by beew on 2010-08-04
> **mcduck said:**
> When you installed the programs you used "sudo" in some place where you didn't need it.

If you unzip an archive using sudo, you unzip it as root and the extracted contents are owned by root. If you create a directory with sudo the directory will be owned by root. If you execute some installer script with sudo the script runs as root and all the files it creates are owned by root. And so on.

The good practice, when you aren't sure if you need sudo or not, is to first try without it. If you get an error about permissions, *then* you can try again with sudo.

Yeah, that is what confuses me sometimes. I think I don't need sudo for most things that I do in the /home directory, but sometimes  it seems that I do need sudo for rather mundane tasks like mounting isos  and running the installer. I could be wrong on which specific act required sudoing  because I can't remember exactly but I am sure that certain things didn't work without sudo-ing when I installed those programs even though I specifically installed them in my /home directory so I can easily remove them if I don't want them. They didn't come from the repos or in .deb packages so they don't integrate into Ubunti's software managing system.

I am wondering if that miht have to do with the fact that my default status in "users-groups" was "desktop user" instead  of "administrator" and as a result the range of things that I could do was limited without invoking sudo. That might be because I chose "automatic login" when I installed Ubuntu.

Also, it seems that I have to run certain programs with sudo in order to get updates. Now I am not sure if I can run them with sudo if I haven't installed them that way. In one case that I mentioned above, I could run the program without sudo but not with it, though it seems that for other programs I can run with or without sudo but cannot get updates without sudo.

---

### Post by sandyd on 2010-08-04
> **beew said:**
> Hi, Peter



But then how come I could run it without sudo? I actually did cd into the directory where the executable is , so I think I was in the path.
cd  to the directory and run this (replace $username with your username)
```

sudo chown -R $username:$username *
```
and yes, thats a collon in between the two $usernames

---

### Post by mcduck on 2010-08-05
> **beew said:**
> 
I am wondering if that miht have to do with the fact that my default status in "users-groups" was "desktop user" instead  of "administrator" and as a result the range of things that I could do was limited without invoking sudo. That might be because I chose "automatic login" when I installed Ubuntu.

Definitely not. Non-admin users aren't able to use sudo at all, so if you are able to use it then you are member of the "admin" group. (if you want to, you can check which groups you belong to by running the "groups" command in a terminal.)

Also not being able to do certain tasks without sudo is how it's supposed to work.

Having to use "sudo" to update a program that you instead outside of the package management, and using sudo, is normal. Of course you shouldn't really need to use "sudo" to install anything inside your home directory, you already have enough permissions to do whatever you want in there.

If you are talking about having to launch some app from the repositories with sudo to update it, you simply shouldn't be sing that at all. Instead you should update it through the package manager (I've seen quite many people launching Firefox with sudo to update it, but really they could have just waited a day or two for the update to become available through the repositories).

Anyway, the simple rule with permissions and sudo is that anything you do in your own home, and anything that only affects your own user, doesn't require sudo. And everything that affects the whole system and all it's users is an admin task and therefore requires you to use sudo.

If some third-party program's installer requires you to use sudo then it's a sign that the installer is made to install, the program system-wide (which is an admin task), not just for your own user, so you should install it somewhere else than in your home.

What comes to mounting .iso images, if you do it from command line you will need sudo, but in Ubuntu 10.04 you can also mount images directly from your desktop/file manager by right-clicking the image and selecting "Open with Archive Mounter".

---

### Post by beew on 2010-08-06
Hi,

> Of course you shouldn't really need to use "sudo" to install anything inside your home directory, you already have enough permissions to do whatever you want in there.

Actually this is not true. If I install from iso I need to create the mount point and mount the iso with sudo or the installer won't be able to create new directories or write to them. I don't know if this is normal and if it is then it is pretty stupid because I have to do this through command lines. Automatic mounting with other tools just wouldn't work.

Well I know some people would say it is no big deal to use the command line. It is no big deal if your program comes in one iso. What do I do if I have a program that comes in several iso? Do I have to create all the mount points and then mount them manually??? I certainly can't see the greatness of command lines in such a scenario especially if you are prone to typos. There are tools that allow you to mount multiple isos such as Furius Iso mount but if I  need root privilege to install programs then they are no good.

P.S. I am talking about installing programs only locally, in my /home directory or /usr/local

---

