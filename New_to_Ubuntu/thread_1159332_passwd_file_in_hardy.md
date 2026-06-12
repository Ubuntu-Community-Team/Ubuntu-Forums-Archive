---
title: "passwd file in hardy"
date: 2009-05-14
forum: New to Ubuntu
---

### Post by navaneethan on 2009-05-14
Hai friends,

          I ve deleted the file passwd file in the location /etc/passwd for ubuntu hardy

          Then i can't enter into hardy after i ve restarted,it didn't display GUI login prompt

       For more details [CLICK ]("http://navaspot.wordpress.com/2009/05/15/passwd-file-removed/")  

       What i could do ??

------

with regards

Navaneethan

---

### Post by beercz on 2009-05-14
Have you tried booting from a live CD?

Can you add users using the live CD?

Eg To create a user named fred, in terminal type:

> sudo adduser fredNot sure if it will work, but it might be worth a try.

Good luck.

---

### Post by cosine352 on 2009-05-14
have tried to boot in to recovery mode?

this may also help. Look at the last post in this thread
[http://ubuntuforums.org/showthread.php?t=803027](http://ubuntuforums.org/showthread.php?t=803027)

---

### Post by Didius Falco on 2009-05-14
Hi,

I just had a look in my own /etc/ directory and there is a backup  of the file. I have ```
passwd
```  and ```
passwd-
```.

You could try booting with a Live CD, typing ```
gksudo nautilus 
``` navigating to the ```
/etc/
``` directory and looking for a similar backup. If you find one, just copy/paste it into the same folder,rename the copy to "passwd" and reboot.

I hope it helps...

Regards,

Didius

---

### Post by navaneethan on 2009-05-15
Thanks friends i have another doubt if two files are deleted(passwd,passwd-) means

Is any solution available??

---

### Post by keithweddell on 2009-05-16
I don't know if you solved this already but you might find a backup in /var/backups.

---

### Post by navaneethan on 2009-05-23
Oh!! Thanks

---

