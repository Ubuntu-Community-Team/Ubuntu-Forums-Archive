---
title: "set a home directory from command-line"
date: 2009-08-04
forum: New to Ubuntu
---

### Post by shawnisalk on 2009-08-04
[SIZE=1][COLOR=Black]Hey, folks, 

I'm a newbie Ubuntu user, learning admin stuff. I've created a user with "adduser" and I've found out how to add her to different groups in /etc/group. I've created a directory for her in /home and given her ownership of that directory. 

So, now, I'm wondering how to set that directory as her home directory (from the command-line). 

Can anyone tell me?[/COLOR][/SIZE]   [SIZE=2][COLOR=Black]
[/COLOR][/SIZE] 

:D

---

### Post by slakkie on 2009-08-04
With useradd you can set this by.. 

useradd -d /path/to/dir -m username

If the user is already created you need to edit /etc/passwd:

wesleys:x:1000:1000:Wesley XXXXXXXX,,,:**/home/wesleys**:/bin/zsh

Edit the bold entry to fit your needs. You need to be root to change that file.

---

### Post by fahadsadah on 2009-08-04
Also, you can add her to groups by doing:
sudo adduser USERNAME GROUPNAME

---

### Post by shawnisalk on 2009-08-04
Thank you!:D

---

