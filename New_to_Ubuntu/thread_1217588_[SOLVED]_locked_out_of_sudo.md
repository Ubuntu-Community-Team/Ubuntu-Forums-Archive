---
title: "[SOLVED] locked out of sudo"
date: 2009-07-19
forum: New to Ubuntu
---

### Post by songl100 on 2009-07-19
I made a big mistake going into the visudo command and editing the sudoers file. I did the following:

changed 

%admin ALL=(ALL) 

to:

%admin ALL=(ALL) !/bin/su

Now when I try to use sudo with my login I get the following.

song@dell-desktop:/etc$ sudo visudo
[sudo] password for song: 
Sorry, user song is not allowed to execute '/usr/sbin/visudo' as root on dell-desktop.example.com.
song@dell-desktop:/etc$ sudo -i
[sudo] password for song: 
Sorry, user song is not allowed to execute '/bin/bash' as root on dell-desktop.example.com.

Is there a way to get into my laptop and correct the sudoers file with visudo? Any help is appreciated.

- Song

---

### Post by utnubuuser on 2009-07-19
as far as I know, you can edit the sudoers file with nano from the recovery console.  Not sure why everyone says you have to use visudo.

---

### Post by songl100 on 2009-07-19
I found out the solution by doing some googling. I rebooted into the recovery mode and then when to the root login and reedited the file by doing a visudo. I put the settings for the admin group of what they were. Phew! I thought I was locked out of sudo permanently! 

-Song

---

### Post by Clorow on 2009-07-19
One way to do it is to use su instead of sudo, but this only works if you have specified a root password. If you have, then:
```

foo@bar:~$ su
Password:
root@bar:/home/foo# visudo

```

---

### Post by sandyd on 2009-07-19
simply do
```

sudo passwd root

```
and remember that password. 

That will unlock the root account.
However, that creates a security risk as anyone who is able to guess your root password can do anything they want to the computer.

---

### Post by aysiu on 2009-07-20
There's no reason to enable a root login, and the OP has already solved the problem.

If you enable root with a password, then you cannot log into recovery mode if the root password is forgotten.

---

