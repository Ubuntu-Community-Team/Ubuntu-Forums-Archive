---
title: "How to set up users after &quot;the system administrator is not allowed to login&quot;"
date: 2009-06-16
forum: New to Ubuntu
---

### Post by quicksilver1234 on 2009-06-16
Hi All,
I fired up my linux box running ubuntu after leaving it unplugged for a year and half.  I have forgotten everything
I don't remember my user names and passwords that I set up.
I reset my root password but I cannot log into the Graphical Interface. 
I get the dreaded "the system administrator is not allowed to login from this screen"
If I just let the computer start up, it goes the graphical interface, and where I cannot log in with any account or password I know. 

1) Is there a tutorial that walks me through setting up my user accounts as root so I can access/log into the graphical interface?

2) How do I log in as root and by pass the graphical interface?

Thanks!

---

### Post by mcduck on 2009-06-16
You are not really supposed to login to desktop as root. The information how to do that is definitely available with a google search, but you wont find it on these forums as the forum policy is to support Ubuntu's security model. Anyway, you don't need even need to log in as root if your old user account had admin rights as the user name is easy to find out and password is just as easy to reset:

Just boot into recovery mode (you can select it from the Grub menu) and when asked what you want to do select the root console.

Then, run "ls /home" to check the user home directories, the directory name is the same as the user name so now you know what your user name was.

After that simple "passwd *username*" will allow you to set the password for that user.

Now you should be able to log in as that user with the user name you found out and the password you just set.

---

### Post by quicksilver1234 on 2009-06-16
Thanks. 
I'm not trying to login to desktop as root. I did see those tutorials but I'm not trying to hack the computer that way.  

I'll try your steps tonight and it looks like exactly what I needed.

---

### Post by lucio39 on 2009-06-16
Hi!
I have a similar  problem. I recently upgraded to Ubuntu 8.10 (from 7.10). 
I'm the only user of the system. Everything is fine, but I have found out that I've lost the administrator authority which I had under 7.10.
As a consequence, I can't download updates anymore.
Any suggestion?

Thanks.

---

