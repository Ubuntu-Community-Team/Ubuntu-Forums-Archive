---
title: "Ubuntu install, please advise."
date: 2009-05-06
forum: New to Ubuntu
---

### Post by 85nissan on 2009-05-06
I am getting this error message when ever i get the last step (#7) of the install process using Ubuntu's install manager: 

"The installer needs to commit changes to partition tables, but cannot do so because partitions on the following points could not be unmounted: /cdrom     Please close any applications using these mount points."

WTF? I'm sooo close yet so far. What do I do?

---

### Post by modmadmike on 2009-05-06
Go to Applications>Accessories>Terminal and type "sudo umount /cdrom"

---

### Post by modmadmike on 2009-05-06
Wait... AREN"T YOU INSTALLING FROM A CD LOL

---

### Post by Penguin Guy on 2009-05-06
> umount /cdrom
**Not** a good idea.
I think this was mentioned somewhere else but can't remember the solution; sorry.

---

### Post by 85nissan on 2009-05-06
Attempting to set up a dual boot: Using the last command someone here just gave me, I'm getting this message on the terminal: 
umount: /cdrom: device is busy.
        (In some cases useful info about processes that use
         the device is found by lsof(8) or fuser(1))
ubuntu@ubuntu:~$ 



What do you say, and thanks for all your help gang...

---

### Post by modmadmike on 2009-05-06
> **85nissan said:**
> Attempting to set up a dual boot: Using the last command someone here just gave me, I'm getting this message on the terminal: 
umount: /cdrom: device is busy.
        (In some cases useful info about processes that use
         the device is found by lsof(8) or fuser(1))
ubuntu@ubuntu:~$ 



What do you say, and thanks for all your help gang...

try installing from USB, something similar happened to me when my CD drive went bad [https://help.ubuntu.com/community/Installation/FromUSBStick]("https://help.ubuntu.com/community/Installation/FromUSBStick")

---

### Post by 85nissan on 2009-05-06
I can't install from a cd. dont have any blank discs. I am trying to set up a dual boot and am using UNetbootin to do so. Any other ideas????

---

### Post by 85nissan on 2009-05-06
Some body on craigslist.org suggested I do this when setting up partitions: 

/ 
/home 
swap


instead what I did which is: 

swap
/
home

---

### Post by 85nissan on 2009-05-06
Just tried aforementioned advice, no luck. Still getting message about the /cdrom mount.

---

### Post by modmadmike on 2009-05-06
Ok since you are NOT using a cd run this:
```
sudo umount -fl /media/cdrom
```
and if that does not work then type 
```
lsof
``` and find out what is acessing /media/cdrom and post it here so i can see what i can do.

---

