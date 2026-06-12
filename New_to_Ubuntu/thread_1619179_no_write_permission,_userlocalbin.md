---
title: "no write permission, user/local/bin"
date: 2010-11-11
forum: New to Ubuntu
---

### Post by comotion on 2010-11-11
hello I'm a beginner using Linux 10.04lts and I'm having problems installing a demo version of Logo soft v6.1 from Siemens. After downloading I cd to the directory then *sh ./Setup.bin *the install. starts o.k. 'till I get the message "Don't have have "write permissions" the installer wants to put it in user/local/bin. I've already tried chmod -R 777 /usr/....  and again I don't have permission. Would be very greatfull if someone could help I need the software running for my college work.
p.s. answers in German are o.k. to

---

### Post by bioterror on 2010-11-11
> **comotion said:**
> hello I'm a beginner using Linux 10.04lts and I'm having problems installing a demo version of Logo soft v6.1 from Siemens. After downloading I cd to the directory then *sh ./Setup.bin *the install. starts o.k. 'till I get the message "Don't have have "write permissions" the installer wants to put it in user/local/bin. I've already tried chmod -R 777 /usr/....  and again I don't have permission. Would be very greatfull if someone could help I need the software running for my college work.

you have to do it like this:

```
sudo ./Setup.bin
```
You have to use "sudo" to get permission to write there.

---

### Post by comotion on 2010-11-11
could you tell me when to sudo because after I start the install. I can't use the terminal anymore

---

### Post by mcduck on 2010-11-11
You'll probably want to read this guide about permisisons and admin tasks in Ubuntu, and the use of "sudo":

[https://help.ubuntu.com/community/RootSudo]("https://help.ubuntu.com/community/RootSudo")

(and as a nice tip, changing the ownership or permissions of any of the system files/directories is pretty easy way to break your system. Don't do that, change your *own*  permissions instead, by using "sudo" for the tasks that require admin privileges)

---

### Post by mcduck on 2010-11-11
> **comotion said:**
> could you tell me when to sudo because after I start the install. I can't use the terminal anymore

you use it to start the installer.

If you'd normally execute the installer by running a command like "*./setup.bin*", you'd instead need to run "*sudo ./setup.bin*".

In short, adding "sudo" in front of a command will execute the command as root (the admin user of a Linux system) instead of your own user.

For graphical applications use "gksudo" instead of "sudo".

---

### Post by comotion on 2010-11-11
That worked o.k. but now I can't find where to start it sorry to nerv. and big thanks to u both for the prompt help

---

### Post by comotion on 2010-11-11
I've found the file (it's in user/local/bin naturally) but I can't find a way to start it there's no executable and auto run prompt isn't helping either. Can sudo help here?

---

### Post by mcduck on 2010-11-11
What you mean that you found the file and there's no executable?

If the program only has one file, that *is* the executable. (which would pretty much make sense, since /usr/local/bin is meant only for executable files)

Linux doesn't use any file name extensions like ".exe" to mark executable files, in case you were looking for something like that.

Anyway, if the program has a file in /usr/local/bin, then that's most likely the executable you are looking for, and to actually run the program you just need to type it's name in a terminal and hit enter. (if it's a graphical app you can of course create a menu entry for it yourself if the installer didn't make one for you)

---

### Post by bwbloch on 2010-11-11
I'm having a similar problem and think I've figured it out but want to check that this is correct.  I'm downloading a package to add to R (a statistical programming language).  I've extracted it from the tar.gz file and need to move it to usr/local/lib/R/site-library.  To get permission to do that, do I run the following in the terminal:

sudo chmod 700 usr/local/lib/R/site-library

Thanks!

---

### Post by mcduck on 2010-11-11
> **bwbloch said:**
> I'm having a similar problem and think I've figured it out but want to check that this is correct.  I'm downloading a package to add to R (a statistical programming language).  I've extracted it from the tar.gz file and need to move it to usr/local/lib/R/site-library.  To get permission to do that, do I run the following in the terminal:

sudo chmod 700 usr/local/lib/R/site-library

Thanks!

No you don't!

Like I've  already said in this thread, changing the ownership or permissions of system files and directories is a quick way to break your system. You shouldn't do that. Most of the stuff requires certain ownership and permissions to work at all.

If you don't have suitable permissions to copy a file to some location, you don't change the location's permissions, you change *your own* permissions. That's what "sudo" is for.
```

sudo mv somefile /usr/local/lib/R/site-library/somefile
```

---

### Post by comotion on 2010-11-12
In user/local/bin I've got the file Siemens in it is the file  LOGOComfort_V6 which is the name of the software I'd like to start tried  both in terminal w&without sudo only get command not found. It's a  software to program logic controllers for electrical systems and works  on a graphical level. I'd be happy enough just to get it started but any  tips or links about creating a menu would be appreciated.

thanks again

---

