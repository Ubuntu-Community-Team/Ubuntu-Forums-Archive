---
title: "Bash out of control ?"
date: 2010-07-15
forum: New to Ubuntu
---

### Post by nnjond on 2010-07-15
Hi,

I created a system restore file. 

code:

tar cvpzf sysrestor.tgz --exclude=/proc --exclude=/lost+found --exclude=/sysrestor.tgz --exclude=/mnt --exclude=/sys /


And hav tried out:

ctl alt F4

root@ desktop:# tar -cxvpfz sysrestor.tgz /

code has been streaming past for ages. Longer than a fresh install!
 I'm wondering if i've done something to create a cycle?

How and should i interupt it? If i ctl alt F7, will it take me back to Desktop?

Thanks for your time

---

### Post by bodhi.zazen on 2010-07-15
First, you almost certainly would want to restore from a live CD and not to / on a running system.

Second, I would let it run ... and cross your fingers it does not break.

/me looks : [https://help.ubuntu.com/community/BackupYourSystem/TAR](https://help.ubuntu.com/community/BackupYourSystem/TAR)

Well , that wiki page indicated it is possible ...

---

### Post by blur xc on 2010-07-15
Just a question- why are you using the -c and -x flags together at the same time?  Does this do some trick I don't know about?  

Thanks
BM

---

### Post by nnjond on 2010-07-15
Thanks for your help.

I've been following advice without knowing much about the process.

the restore command from the gui terminal is a little different but fails to restore the sys, so i tried a modified one from ctl alt F4.

The tar file should be excluded from the restore.

I thought it was a sensible and convenient precaution to make this file have you not done the same or similar?

---

### Post by blur xc on 2010-07-15
> **nnjond said:**
> Thanks for your help.

I've been following advice without knowing much about the process.

the restore command from the gui terminal is a little different but fails to restore the sys, so i tried a modified one from ctl alt F4.

The tar file should be excluded from the restore.

I thought it was a sensible and convenient precaution to make this file have you not done the same or similar?

I don't have any method of backing up or restoring my system...  I guess I'm playing russian roulette..  The deal is that I don't know a lot about backing up or resotring procedures, what or the benefits and pitfalls of one way for another,  10yrs so far, and no HDD faiure (knock on wood) so far.

Personally, I only care to back up my home directory and photos on my 1tb hdd, system files can be replaced by doing a clean install, which does take some time (not so much for the install, but all the setting up and configuring afterwards)...

Eventually I'll get myself setup with a good backup system.  The problem is what's the best way to back up over 500gb of data, which grows all the time, eventually will be tb's of data, so my backup system will also need to grow as well...fun stuff.

dunno if you know this, but there are manual pages for all your linux commands -
```
man tar
```would bring up the man page for tar.  -c is the create an archive, -x is the extract an archive, which had me wondering why you were using -cx in your restore command.  It's crap like that, that keeps me from blindly following commands on various linux blogs.  Far too often there's someone posting in the comments some other way to do it, or some horror story of how it failed, etc.. etc..  Seems kind of ironic to break your system while trying to test a backup and restore.

BM

---

### Post by jtarin on 2010-07-15
> **blur xc said:**
>  Seems kind of ironic to break your system while trying to test a backup and restore.

BM
Oh! The irony :D

---

### Post by blur xc on 2010-07-15
I just tried that tar command and it failed for me...

```
tar -cxvpfz test.tgz 
tar: You may not specify more than one `-Acdtrux' option
Try `tar --help' or `tar --usage' for more information.
```

Dunno what it could be doing on your system.  Can you post the website from where you found that information?

Thanks,
BM

---

### Post by cariboo on 2010-07-15
@blur xc

Have a look at rsync, it does a full backup the first time, and only backs up changed files after that, there are also compression options that allow you keep the backup at a manageable size.

I only backup the home directories on my three main systems. My home system backup = 166GB, netbook is 7.2GB and office system = 13GB

---

### Post by blur xc on 2010-07-15
> **cariboo907 said:**
> @blur xc

Have a look at rsync, it does a full backup the first time, and only backs up changed files after that, there are also compression options that allow you keep the backup at a manageable size.

I only backup the home directories on my three main systems. My home system backup = 166GB, netbook is 7.2GB and office system = 13GB

Thanks-  I've heard that mentioned around here and ther, I'll dig in to that and see what I can do with it.  

BM

---

### Post by dfreer on 2010-07-16
> **nnjond said:**
> 
How and should i interupt it? If i ctl alt F7, will it take me back to Desktop?

Ctrl c generally kills any currently running process. And if gnome is still running it's generally on F7, yes.

---

### Post by jtarin on 2010-07-16
[Here's a very sane "tar" backup routine/schedule, including incrementals.]("http://www.faqs.org/docs/securing/chap29sec305.html")

---

