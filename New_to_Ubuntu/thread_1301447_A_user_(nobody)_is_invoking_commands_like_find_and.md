---
title: "A user (nobody) is invoking commands like find and sort and top in my system :O"
date: 2009-10-26
forum: New to Ubuntu
---

### Post by legolas_w on 2009-10-26
Hi
I saw my hard disk spinning without me executing any commmand. I tried "top" and I saw entries like:


```

 PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
  413 nobody    39  19  3512 1288  904 R   10  0.0   0:09.72 find 

```

how this command is invoked without I issuing it? is it a virus or something?

Thanks.

---

### Post by renkinjutsu on 2009-10-26
should probably have posted this in the security forum.
do you even have a user "nobody" on your computer?

wait... actually, i just checked my passwd file, and there's supposed to be a user "nobody", but i checked the crontabs for the user, and it's blank, so it shouldn't randomly execute "find"... I'll continue to investigate as we wait for the Pros to sniff this thread out

---

### Post by nothingspecial on 2009-10-26
Nobody runs deamons and servers and stuff like that. Nobody owns no files and has no permissions. 

If someone took over your server, they wouldn`t be able to much because nobody has no privaleges.

Standard unix stuff, which I only vaguley understand. But nobody is good. Don`t delete nobody or you will break your system.

---

### Post by kerry_s on 2009-10-26
those are the standard cron jobs, very normal.
look in /etc & you will see the cron folders, inside them are the jobs that run.

---

### Post by cariboo on 2009-10-26
> **nothingspecial said:**
> Nobody runs deamons and servers and stuff like that. Nobody owns no files and has no permissions. 

If someone took over your server, they wouldn`t be able to much because nobody has no privaleges.

Standard unix stuff, which I only vaguley understand. But nobody is good. Don`t delete nobody or you will break your system.

Actually nobody can create and own files if you have:

```
guest ok = yes
```

in /etc/samba/smb.conf, and you copy/create files on a samba share from Windows.

---

### Post by XCan on 2009-10-26
Hehe, these posts are kind of amusing explaining who nobody is and that nobody is running something. ;) 

OT: I'm just curious about the find command, is that used for building "locate"'s cache?

---

### Post by Ryuhayabusa on 2010-05-23
I recently panicked when i saw the same thing :)

Maybe in the future, user friendly linux like debian/ubuntu should change the username from 'nobody' to 'autotask' or something like that?

---

