---
title: "Forgot username and/or password"
date: 2009-04-27
forum: New to Ubuntu
---

### Post by mawil1013 on 2009-04-27
Yes, I am stupid, it has been a while since using xubuntu on my old emachine and I have forgotten either my username or password. Do I reinstall xubuntu or is there a work around? I am not ubuntu tech savy.
Piedmont

---

### Post by freak42 on 2009-04-27
at boot choose recovery mode..

you should get into a console with root rights..
use
```
cd /home/
```
and then ```
ls
``` to list all home folders, there should be a folder called "yourusername".

to change the password of this user use
```
su 'username'
``` without the quotes
and then 
```
password
```
it should then ask you for a new password for this user.

hth and I hope it works

---

### Post by cmnorton on 2009-04-27
Find another Linux system where you know your name and passwd, and grab 
/etc/passwd and /etc/shadow.  Or, find another system and create yourself as a user. Then, using a live CD like Ubuntu or Knoppix, boot the system on which you cannot remember your password.

Don't use the passwd and shadow files from the other system where you know your name and password to overwrite the /etc/passwd and /etc/shadow files on the system on which you forgot your passwd. Instead, copy the passwd and shadow fields for the known user on the other system into the passwd and shadow files on your system (that you booted with the live CD). 

Make sure you also edit /etc/group, so that this new user is in the admin group, so you can sudo.

---

### Post by cmnorton on 2009-04-27
This is much friendlier than my suggestion, and a good piece of info to boot.

> **freak42 said:**
> at boot choose recovery mode..

you should get into a console with root rights..
use
```
cd /home/
```and then ```
ls
``` to list all home folders, there should be a folder called "yourusername".

to change the password of this user use
```
su 'username'
``` without the quotes
and then 
```
password
```it should then ask you for a new password for this user.

hth and I hope it works

---

### Post by kanikilu on 2009-04-27
[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

---

### Post by mawil1013 on 2009-04-27
> **freak42 said:**
> at boot choose recovery mode..

you should get into a console with root rights..
use
```
cd /home/
```
and then ```
ls
``` to list all home folders, there should be a folder called "yourusername".

to change the password of this user use
```
su 'username'
``` without the quotes
and then 
```
password
```
it should then ask you for a new password for this user.

hth and I hope it works

Need more help please, I press on button on laptop, Press esc too see - ubuntu 8.10, kernal 2.6.27-7-generic (recovery mode), I select, code runs down screen then I get a menu, Recovery Menu with resume normal boot, try make free space, repair broken packages, file system check, drop to root shell prompt and try to fix x server, now I'm confused.

---

### Post by kanikilu on 2009-04-27
> **mawil1013 said:**
> Need more help please, I press on button on laptop, Press esc too see - ubuntu 8.10, kernal 2.6.27-7-generic (recovery mode), I select, code runs down screen then I get a menu, Recovery Menu with resume normal boot, try make free space, repair broken packages, file system check, drop to root shell prompt and try to fix x server, now I'm confused.

Drop to root shell. See the guide I linked to above for step-by-step instructions.

---

### Post by theozzlives on 2009-04-27
Drop to root shell prompt. Follow the instructions above.

---

### Post by mawil1013 on 2009-04-27
> **kanikilu said:**
> [http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

YES!, YES!, this worked perfectly!
Thanks so much!

---

