---
title: "Path and Environmental settings"
date: 2009-12-20
forum: New to Ubuntu
---

### Post by alien8predator on 2009-12-20
I'm reading about "Path and Environment settings" now. It says that it's used so that you don't have to type the full path to to command in order to use it, if you don't have the path directory variable you will have to type the full path. If you aren't a privileged user you won't be able to use the command 

this is what I get for my first created user, so he is in special group.

maarten@jigsawpuzzle:~$ echo $PATH
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games

second user(normal user)

nathalie@jigsawpuzzle:~$ echo $PATH
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games

While to my understanding to a normal user shouldn't even get any of the /sbin in their path because they are not in a special group. But then like it said if you aren't a special group they aren't able to use it that is true. Because when I use sudo on the user nathalie, says I'm not in sudoer group no permission. Why then does it show the sbin in the path?

---

### Post by milosz.galazka on 2009-12-20
> **alien8predator said:**
>  Why then does it show the sbin in the path?

I suppose it's just to make things easier on desktop. For example normal user can start www server located in /usr/sbin/ using higher port (>1024) without root privileges.

---

### Post by SecretCode on 2009-12-21
And maybe it's more logical for the regular user to get 'Permission denied' messages than 'Command not found'.

---

