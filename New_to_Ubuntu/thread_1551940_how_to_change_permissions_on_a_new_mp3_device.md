---
title: "how to change permissions on a new mp3 device?"
date: 2010-08-13
forum: New to Ubuntu
---

### Post by dveej on 2010-08-13
Hi! I am pretty new (although I do know a few things like how to enter a command into the terminal) and am running Lucid. I just bought a Sansa Clip and when I try to do anything with it, it shows up in /media/usb0 with a big padlock on it. How do I change permissions on a handheld mp3 device so I can use it?
Thanks for any help!

---

### Post by sahabcse on 2010-08-13
Just create a folder and mount the partition on it.

#mkdir test
#mount /media/usb0 test


Then paste the o/p of following command

#touch test

---

### Post by dveej on 2010-08-16
I typed those three commands in exactly as they appeared in your post, and hit enter. Nothing happened. 

"Then paste the o/p of following command"

Does that mean paste the output that comes back after I enter #touch test into the terminal? Nothing came back. 

Am I supposed to type the # sign as written?

Thanks for your help!

---

### Post by L2U2K2E on 2010-08-16
try mounting it under System>Administration>Disk Utility


you could also attempt to change permissions running nautilus as a root
```
sudo nautilus
```

---

### Post by sahabcse on 2010-08-17
Regarding you issue we have mounted your external drive on a test directory. And try to write a file on it for checking the permission issue.

For example 

sahab@sahab-desktop:~$mkdir test
sahab@sahab-desktop:~$mount /media/usb0 test
sahab@sahab-desktop:~$cd test
sahab@sahab-desktop:~/test$touch testfile
sahab@sahab-desktop:~/test$ls -al testfile
-rw-r--r-- 1 sahab sahab 0 2010-08-17 09:32 testfile

---

