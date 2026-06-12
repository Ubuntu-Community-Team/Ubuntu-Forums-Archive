---
title: "Can't get PATH statement to update..."
date: 2010-06-20
forum: New to Ubuntu
---

### Post by akelsall on 2010-06-20
I made a change to /etc/environment to add a directory the the PATH statement. I closed my terminal window and opened a new one, thinking 
that would update the PATH variable. Wrong.  Can someone tell me how to
update the environment file so my PATH statement is updated **now**?

Here's what it was, and what I changed it to:

hiker@eno:~$ echo $PATH
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games

hiker@eno:~$ cat /etc/environment 
PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:~/SCRIPTS:"

After saving the changes, it still shows:

hiker@eno:~$ echo $PATH
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
hiker@eno:~$ 


Must be some step I'm overlooking.

Thanks,

Andy

---

### Post by Bachstelze on 2010-06-20
I believe /etc/environment is only read at boot time, so add it manually for now.

---

### Post by lkjoel on 2010-06-21
If I get what you mean, you could try
```
gedit ~/.bashrc
```
Then change it there, and logout and log back in.

---

### Post by akelsall on 2010-06-21
lkjoel, there is no PATH statement in .bashrc. I know it needs to be modified in /etc/environment. I'm just trying to determine if there's a way to update that file (to reflect the changes to the PATH statement) without rebooting. 

Thanks,

Andy

---

### Post by akelsall on 2010-06-28
Rebooting seems to be the only way to make the change active, so I'm marking this thread as SOLVED.

Andy

---

