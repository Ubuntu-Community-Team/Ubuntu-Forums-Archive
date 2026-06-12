---
title: "Incorrect Username or Password"
date: 2009-08-27
forum: New to Ubuntu
---

### Post by jesse100 on 2009-08-27
I somehow have installed Ubuntu 9.04 (side by side with XP) and when I boot to ubuntu I get the above. I don't believe I ever put one in. What do I do?

Jesse

---

### Post by credobyte on 2009-08-27
Simply enter your username and password - you entered it at the end of setup configuration ( partitioning, user info, etc. ). If you don't know this info, umm .. reinstall.

---

### Post by jbrown96 on 2009-08-27
1) find your username
When you boot the computer, you should get a Grub menu (maybe have to press Esc). There should be a recovery option. Select it. Once that boots you will be presented with a menu on what you want to recover. Choose "root shell"


Edit: all the emoticons should be :x below. You just need the first part.
you should now be at a root prompt. Try this command ```
cat /etc/passwd | grep /home/
``` This will list all accounts that have a password and a home directory. On my computer I get > syslog:x:101:102::/home/syslog:/bin/false
klog:x:102:103::/home/klog:/bin/false
saned:x:109:117::/home/saned:/bin/false
justin:x:1000:1000:justin,,,:/home/justin:/bin/bash
festival:x:111:29::/home/festival:/bin/false
You should be able to figure out which is your account (it should have uid and gid of 1000), but if you are still having trouble look at the default shell. Notice that all but the "justin" account use /bin/false, which means they are not allowed to login. 

2) Now that you have the password. Let's reset it to something else

```
passwd USER
``` replace user from what you found in the last step. this will prompt you for your new password. You won't see anything as you type -- this is a security feature. Once you get it set, just type ```
reboot
``` and you're done.

---

### Post by LewRockwell on 2009-08-27
> **jbrown96 said:**
> 1) find your username
When you boot the computer, you should get a Grub menu (maybe have to press Esc). There should be a recovery option. Select it. Once that boots you will be presented with a menu on what you want to recover. Choose "root shell"


Edit: all the emoticons should be :x below. You just need the first part.
you should now be at a root prompt. Try this command ```
cat /etc/passwd | grep /home/
``` This will list all accounts that have a password and a home directory. On my computer I get 
You should be able to figure out which is your account (it should have uid and gid of 1000), but if you are still having trouble look at the default shell. Notice that all but the "justin" account use /bin/false, which means they are not allowed to login. 

2) Now that you have the password. Let's reset it to something else

```
passwd USER
``` replace user from what you found in the last step. this will prompt you for your new password. You won't see anything as you type -- this is a security feature. Once you get it set, just type ```
reboot
``` and you're done.

note that this will cause the noob with absolutely no idea what a terminal is...to run shreiking from the room swearing eternal allegiance to Windows forevermore...

just sayin'

.

---

### Post by jesse100 on 2009-08-27
Hey guys, 

I just went ahead and reinstalled. I figured since this was my first foray into linux that I had nothing to lose. I did discover the way this happened. I installed with the wubi and it assigns a username (I assume from windows). You just put a password in. Thanks for the help.

Jesse

---

### Post by credobyte on 2009-08-27
> **jesse100 said:**
> Hey guys, 

I just went ahead and reinstalled. I figured since this was my first foray into linux that I had nothing to lose. I did discover the way this happened. I installed with the wubi and it assigns a username (I assume from windows). You just put a password in. Thanks for the help.

Jesse

It shouldn't do that ( at least, I haven't seen it doing anything similar to what you suspect was true ) :-s

---

