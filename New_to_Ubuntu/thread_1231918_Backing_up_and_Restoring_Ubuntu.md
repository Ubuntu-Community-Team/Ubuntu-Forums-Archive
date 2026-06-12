---
title: "Backing up and Restoring Ubuntu"
date: 2009-08-05
forum: New to Ubuntu
---

### Post by Linuxson25 on 2009-08-05
Hi
 
I recently came across a thread by Heliode about backing up and restoring your Ubuntu system. Mainly, all you do is open up a terminal, super user, copy and zip up all the directories in root, except for /proc, /lost+found, /mnt, /sys.
 
You restore the machine just by unzipping these files back into root directory.
And I assume this would work perfectly if done on the same pc.... :)
 
So here starts my dilemma...
 
I am using Ubuntu 9.04 JJ on my laptop, and have used quite a bit of bandwidth to get it up to date, and install most of the programs I need.
I also got a desktop pc at home, which I would also like to install Ubuntu on.
But I dont wanna go through the whole process again of updating and re-installing all the packages.Besides, I dont have an internet connection there, and cellphone signal aint great. :(
 
AptonCD is a great app, except for the fact that it doesnt re-install all your packages automatically...so thats why I tried this shortcut
 
And here comes the problem!!
 
With Ubuntu installed on the desktop, and my backup.tgz file copied into root, I then start to uncompress it, and basically re-write the files in root.
After about 20min, I immediatly start seeing changes....eg desktop icons and appearance changes.
 
After the process is completed, the system works perfectly!!
 
Except for when I restart
 
It then gives me an Error 15: File not found message.
Now I have tried fixing the GRUB, checking to see if the system is booting from the correct device...even tried copying my fstab file directly after clean installation back into /etc...but to no avail.
 
When I log out, and back in again...all I get is a white screen
And when rebooted, error 15
 
Now I know that the two machines dont have absolutely anything in common...
The laptop is a Pentium, and desktop an AMD....
So I am guessing here that somewhere there is a file with system specs and stuff that gets over written with the wrong copy, and then bombs out the whole machine
 
 
 
If anyone can just give me a hint as to what I am doing wrong here?
I would really like to carry one using Ubuntu, and not have to revert back to ol' Windows :)
 
 
 
Thanx

---

### Post by pastalavista on 2009-08-05
I find it simpler to just back-up my /home directory, which I have on it's own partition. Everything else is easily downloaded. Of course, my bandwidth usage is unlimited.

You should try booting from the live CD and reinstall without formatting. Go through the install process and be sure to use the MANUAL mode, and in the partition editor, **uncheck** the box that says 'format' on all the partitions.

---

### Post by nhasian on 2009-08-05
i just use sbackup

[https://help.ubuntu.com/community/BackupYourSystem/SimpleBackupSuite](https://help.ubuntu.com/community/BackupYourSystem/SimpleBackupSuite)


but you should also look into:

[http://www.ubuntugeek.com/back-in-time-a-simple-backup-tool-for-ubuntu.html](http://www.ubuntugeek.com/back-in-time-a-simple-backup-tool-for-ubuntu.html)

---

### Post by tea for one on 2009-08-05
Good morning

I suggest that you have a quick look at Remastersys to create a live CD and an installer for your system. It will allow you to take all your installed software to another PC

[http://www.dedoimedo.com/computers/remastersys.html](http://www.dedoimedo.com/computers/remastersys.html) is a useful resource.

To back up your home directory, I would suggest Grsync.

---

### Post by slakkie on 2009-08-05
[http://www.clonezilla.org](http://www.clonezilla.org)

---

### Post by indytim on 2009-08-05
Just "another" option.... :D

Partimage (it's in the repositories).

-IndyTim

---

### Post by Cheesemill on 2009-08-05
+1 for Remastersys

---

### Post by kendoori on 2009-08-05
One of my machines running 8.10 runs everything off a CF card, including booting. Is there a way to use Remastersys to clone the CF card to another CF card of the same size for disaster purposes?

I'd previously did this clone through another method, but Remastersys seems simpler.

---

### Post by tea for one on 2009-08-06
> **kendoori said:**
> One of my machines running 8.10 runs everything off a CF card, including booting. Is there a way to use Remastersys to clone the CF card to another CF card of the same size for disaster purposes?

I'd previously did this clone through another method, but Remastersys seems simpler.

Assuming that Compact Flash cards behave in the same way as USB sticks, I would expect that your task is possible. I have done the following with a USB stick just out of curiosity:-

This is based on Ubuntu, I have not experimented with other distros.

(a) Create your live CD ISO via remastersys (not including personal data)
(b) Produce a live USB installation using the USB creator in Ubuntu 8.10 or 9.04
(c) Either use the live USB device to recover disasters or use it to install to a drive. Remastersys will include the install software in its remastered ISO.

---

