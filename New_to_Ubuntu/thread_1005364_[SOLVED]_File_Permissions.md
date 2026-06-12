---
title: "[SOLVED] File Permissions"
date: 2008-12-08
forum: New to Ubuntu
---

### Post by bitrocker on 2008-12-08
Hi,

I am going to describe the whole problem... maybe the solution is very different from what I think I have to do.

So the main reason to install Kubuntu was, that I need the latest version of gcc. I am using it to compile SPEC in combination with a program called CodeSurfer (CodeSurfer is e.g. able to produce SDGs that I need).
So first thing is:

1. (not really a prob) Where is the right place to put 3rd party programs? Well, I put it in /home/[users]/Programs/CodeSurfer guess thats not really the palce it should go!?

Although CodeSurfer now lives in my home directory, it seems to work. After setting PATH to point to the CS directory, I can invoke it via the shell...but CS uses a license manager and here things get tricky (for me).
The manual tells to

```
mk-license cs-license.dat>license.dat
```

In CS`s /bin, where cs-license.dat is the file the vendor sent my adviser.

Maybe you cant help me with that, but I am going to tell you about the strange behavior...
This causes a "command not found", but creates a empty file named "license.dat" !?
Command not found is no surprise since there is no mk-license executable, but why is then the new file created?

Ok, now the part where I hope to get help. Invoking CodeSurfer causes a error with the license server (running local on my machine). To find out more about that problem I would need to take a look in the log-file.
The license-manager wants to create a file named "/var/log/lmgrd.log" by default. And tells "Permission denied" for that file. So the question is

2. How to change file permissions? Or permissions for the whole directory (is there a difference?)

I found tips how to edit files that already exist, but none how to change permissions that way, that a program is allowed to create a new file in some directory...

Since there are no permission restrictions on "/home", I tried to make the license-manager write to that directory, what causes a "can`t initialize" (guess you also don`t know why that happens). So this change was no help...

Hope someone has suggestions...

---

### Post by Zill on 2008-12-08
bitrocker:  You *may* get some help on these forums but it seems to me that you are installing commercial software eg. CodeSurfer.

In this case, you might get better support directly from the suppliers.

[http://www.grammatech.com/products/codesurfer/support.html]("http://www.grammatech.com/products/codesurfer/support.html")

---

### Post by bitrocker on 2008-12-08
In my understanding, my questions are not really CodeSurfer related. First I want to try to access the log, before I contact support...

---

### Post by geirha on 2008-12-08
> **bitrocker said:**
> 
```
mk-license cs-license.dat>license.dat
```

In CS`s /bin, where cs-license.dat is the file the vendor sent my adviser.

Maybe you cant help me with that, but I am going to tell you about the strange behavior...
This causes a "command not found", but creates a empty file named "license.dat" !?
Command not found is no surprise since there is no mk-license executable, but why is then the new file created?


The part ">license.dat" means that what the preceding command will output to stdout, should be written to license.dat instead of to the terminal window. It is the shell that handles this. It truncates or creates the file if it doesn't already exist, and then starts the command whose output should be written to that file. So whether the preceding command exists or not, the shell will make that file.

> **bitrocker said:**
> 
Ok, now the part where I hope to get help. Invoking CodeSurfer causes a error with the license server (running local on my machine). To find out more about that problem I would need to take a look in the log-file.
The license-manager wants to create a file named "/var/log/lmgrd.log" by default. And tells "Permission denied" for that file. So the question is


2. How to change file permissions? Or permissions for the whole directory (is there a difference?)

I found tips how to edit files that already exist, but none how to change permissions that way, that a program is allowed to create a new file in some directory...

Since there are no permission restrictions on "/home", I tried to make the license-manager write to that directory, what causes a "can`t initialize" (guess you also don`t know why that happens). So this change was no help...

Hope someone has suggestions...
Try creating the log file yourself, and give it permissions so that the license server can write to it. If you are running the license server as your own user, then
```
sudo touch /var/log/lmgrd.log
sudo chown $USER:$USER /var/log/lmgrd.log
```

I would not recommend changing the permissions/ownership for /var/log, but if you can get the license server to log to a different directory, create a new directory inside /var/log/ for it
```
sudo mkdir /var/log/lmgrd
sudo chown $USER:$USER /var/log/lmgrd/

```

---

### Post by snova on 2008-12-08
> **bitrocker said:**
> So the main reason to install Kubuntu was, that I need the latest version of gcc.

It will be the same. Ubuntu and Kubuntu use the same set of packages. The only difference is the desktop environment they install by default.

---

### Post by bitrocker on 2008-12-09
Thanks geirha for the hint what ">" does. For changing the ownership, my roommate came up with a different solution - wich I think is quite handy.

```
sudo [program name]
```

e.g.

```
sudo dolphin
```

Will start the program with root rights. So I crated the file this way and then gave all rights to it.
So I now got my log, although it`s not telling too much ;( but now it`s up to the vendor`s support...

Thanks for your suggestions.

---

