---
title: "Help with file permissions"
date: 2010-09-21
forum: New to Ubuntu
---

### Post by roflbuntu on 2010-09-21
I want to use ad ons but that error keeps popping up, does anyone know how i can obtain permissions to edit that directory? (sorry, i am relatively new to linux.)

---

### Post by NightwishFan on 2010-09-21
You need root access to move files into such a directory. I do not recommend doing so unless you know what you are doing, however as long as you do not 'delete' anything, all should go well.

To open a single nautilus windows with root permissions, press alt+f2 and type:
```
gksudo nautilus
```

Use this one nautilus window to move the files you want, and then close it when you are done. USE EXTREME CAUTION as you are now allowed to delete important system files.

---

### Post by perspectoff on 2010-09-21
If using Ubuntu, try starting Nautilus as root:

 sudo nautilus

If using Kubuntu, try starting Dolphin as root:

 sudo dolphin

Then try to move the files.

Many folders for apps are owned by the root user and can't be added to/changed/deleted from unless you have root privileges while manipulating them (as above).

---

### Post by Begin_learn on 2010-09-21
> **roflbuntu said:**
> I want to use ad ons but that error keeps popping up, does anyone know how i can obtain permissions to edit that directory? (sorry, i am relatively new to linux.)

You need to have rooot permissions to access the file you are trying to move..you can do this by opening a terminal(ctrl alt f2) and then writing the command with sudo 
for eg if you want to copy a directory from /home/abc to /media/xyz the command would look like
sudo cp /home/abc/filename /media/xyz/
hope you find it useful
you may get to me on my id
[email]bhupendra.singh32@gmail.com[/email]

---

### Post by roflbuntu on 2010-09-21
Thanks ,now i can stop searching for answers!

---

### Post by NightwishFan on 2010-09-21
Please go to "Thread Tools -> Mark As Solved" if the issue was fixed for you. Glad to be of help! :)

---

### Post by jokesarcade on 2010-09-21
> **Begin_learn said:**
> You need to have rooot permissions to access the file you are trying to move..you can do this by opening a terminal(ctrl alt f2) and then writing the command with sudo 
for eg if you want to copy a directory from /home/abc to /media/xyz the command would look like
sudo cp /home/abc/filename /media/xyz/
hope you find it useful
you may get to me on my id
[EMAIL="bhupendra.singh32@gmail.com"]bhupendra.singh32@gmail.com[/EMAIL]

Thanks for the solution :)
i really appreciate your post for me, as i don't have to find the answer any more.

---

