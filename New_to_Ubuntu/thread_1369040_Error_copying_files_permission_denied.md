---
title: "Error copying files: permission denied"
date: 2009-12-31
forum: New to Ubuntu
---

### Post by Rhythmdvl on 2009-12-31
I am trying to move a massive number of files (80,000; 130 GB) from my Linux machine to a NAS device. I keep getting 'Error while copying “file.” There was an errory copying the file into smb://...' Under show more details it says 'Error opening file: Permission denied'. 

All files that return that error were created or placed on the Linux machine by a Mac. 

I took a stab in the dark and ran gksudo nautilus to see if that would make a difference, but it didn't. 

Is there any way to force the system to copy? It's a home office, so there doesn't need to be any particular permissions in place – anyone should be able to do anything to the files, so changing permissions in the entire folder would be OK too. Also, I'm not looking to delete or move the files, just copy them to the NAS. 

Thanks, 

Rhythm

---

### Post by Paqman on 2009-12-31
The problem is most likely on the NAS end. Make sure you've got an account on the NAS that has write privileges to the location you're trying to write to.

---

### Post by Rhythmdvl on 2009-12-31
> **Paqman said:**
> The problem is most likely on the NAS end. Make sure you've got an account on the NAS that has write privileges to the location you're trying to write to.

Not sure where to check. I have been able to copy about 200 GB to the NAS so far. Many of the Mac files are copying over fine, but every once in a while I'll get the stop error.

---

### Post by danastasio on 2009-12-31
where are you pulling the files form?
If your pulling from anything other than /home then you'll run into issues because you dont own any other file on the system. Only root does.

---

### Post by Rhythmdvl on 2009-12-31
The files are in /home/linbox
The main home folder is /home/rhythmuser

Rhythmuser is the only user on the machine. I created the linbox folder off of home in order to share with everyone in the office. 

I'll do whatever it takes to brute force my way into copying things. That's why I thought running gksudo > Nautilus would have been the way to go. 

Again, keep in mind that a gazillion files copied without a problem, files that were created by other machines as well as the Mac.

---

### Post by pastalavista on 2009-12-31
If you downloaded files from iTunes or similar, they just might be "copy protected" allowing only a certain number of copies or transfers.

---

### Post by danastasio on 2009-12-31
> **Rhythmdvl said:**
> The files are in /home/linbox
The main home folder is /home/rhythmuser

Rhythmuser is the only user on the machine. I created the linbox folder off of home in order to share with everyone in the office. 

I'll do whatever it takes to brute force my way into copying things. That's why I thought running gksudo > Nautilus would have been the way to go. 

Again, keep in mind that a gazillion files copied without a problem, files that were created by other machines as well as the Mac.

This might be the problem, what user are you using to copy the files from? If you are doing it with another user (from the other machine) you may not have the proper permissions to take the files.

NAS_IGNORANCE = ON

can you use the 
```
su
```
command to try to copy the files as root? If that doesn't work, its a problem with the other machine and, not knowing anything about NAS, I can offer no more help :-(

---

### Post by Rhythmdvl on 2009-12-31
> **pastalavista said:**
> If you downloaded files from iTunes or similar, they just might be "copy protected" allowing only a certain number of copies or transfers.
All files were created here. They are either Quark or MS Office files. I can’t tell why some files would copy without a problem while others won’t — again tens of thousands have already copied. 

> **danastasio said:**
> This might be the problem, what user are you using to copy the files from? If you are doing it with another user (from the other machine) you may not have the proper permissions to take the files.

NAS_IGNORANCE = ON

can you use the 
```
su
```
command to try to copy the files as root? If that doesn't work, its a problem with the other machine and, not knowing anything about NAS, I can offer no more help :-(

I thought there might be a problem or two doing this from another machine (plus I thought it would be quicker not to route things through a third machine) I have been trying the copy straight from the Linux machine. 

As far as trying to copy as root, have I been mistaken all this time in thinking *gksudo nautilus* would do that? Do I have to copy the folder from a command line to test copying as root? 

Conceptually most important — if I can figure out how to copy as root, is there any way the Mac could have stored files on the Linux machine that would bar the root user’s copying ability?

---

### Post by danastasio on 2009-12-31
```
Conceptually most important — if I can figure out how to copy as root, is there any way the Mac could have stored files on the Linux machine that would bar the root user’s copying ability?
```

Not that I know of, the root user is the god of the computer, if root types in "sudo rm -rf /" the system will delete every. single. file. on the hard drive. without question. so the thought that something could be barring root from performing an operation, while possible (i guess) is very VERY slim. 

```
As far as trying to copy as root, have I been mistaken all this time in thinking gksudo nautilus would do that? Do I have to copy the folder from a command line to test copying as root? 

```

honestly, i completley missed that in your posts, my apologies.

I will keep an eye out for you, but you have exausted my knowledge :-\
Sorry I couldnt be more help.

---

### Post by Rhythmdvl on 2009-12-31
So far so good ... 

Someone suggested
```
sudo chmod -R a+rwx /home/linbox/*
```

Which, I believe, changed files in the folder:
(-R) recursively, so all subfolders were affected;

(a+) for everyone under the sun; users, groups, and others; and

(rwx) permission to read, write, and execute all files.

So far 20 GB out of a 100 GB folder has transferred over, far more than I did before getting the original error.

---

### Post by jl2035 on 2010-01-11
I have the same problem here, but I never had this in previous versions of ubuntu.

I opened the terminal and used the command:

```

sudo cp -r /source /destinationfolder

```

The ouput:
```

jaka@LaptopJaka:~$ sudo cp -r .VirtualBox /media/sda6/VBBackup
cp: writing `/media/sda6/VBBackup/.VirtualBox/HardDisks/WinXP.vdi': File too large

```

Please explain me how can I copy my VirtualMachine and hd. And why is this such big deal in Ubuntu 9.10?!?! I'm already becoming sceptic. I think I loved previous versions much more.

---

