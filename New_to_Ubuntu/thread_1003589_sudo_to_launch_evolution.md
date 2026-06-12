---
title: "sudo to launch evolution?"
date: 2008-12-06
forum: New to Ubuntu
---

### Post by ant2ne on 2008-12-06
Here is a new one. Evolution quit loading. I don't know why. I changed some account settings, and it didn't work. So, I removed and then re-installed evolution. And it still wouldn't open. On a whim I did a "sudo evolution" and it loaded the evolution welcome screen.I shouldn't have to launch evolution via sudo command line. What gives?

---

### Post by drs305 on 2008-12-06
Have you checked the permissions of the applicable folders. For my /usr/bin/evolution, they are as you would expect:
```
-rwxr-xr-x 1 root root 141312 2008-11-25 18:19 /usr/bin/evolution

```

For my user evolution folder in $HOME they are all owened by me with rwx privileges on the folders and rw on the $HOME/.evolution files:
```

drwxr-xr-x  7 drs drs  4096 2008-11-03 19:53 .
drwxr-x--- 61 drs drs  4096 2008-12-06 10:21 ..
drwxr-xr-x  3 drs drs  4096 2008-11-03 19:53 cache
drwxr-xr-x  4 drs drs  4096 2008-11-03 19:53 calendar
-rw-r--r--  1 drs drs  3152 2008-11-03 19:53 categories.xml
-rw-------  1 drs drs 65536 2008-11-03 19:53 cert8.db
-rw-------  1 drs drs 16384 2008-11-03 19:53 key3.db
drwxr-xr-x  3 drs drs  4096 2008-11-03 19:53 mail
drwxr-xr-x  4 drs drs  4096 2008-11-03 19:53 memos
-rw-------  1 drs drs 16384 2008-11-03 19:53 secmod.db
drwxr-xr-x  4 drs drs  4096 2008-11-03 19:53 tasks

```

---

### Post by zwaardmeester on 2008-12-06
You should not sudo evolution at all. The effect will be that user "root" is running the program, not the default user (yourself). This can be very dangerous, for example if you open a virus-infected attachement.

The problem probably lies in the user settings. [These are not deleted when the program is uninstalled]. You can try the following commands.
```

mv .evolution .evolution_backup
evolution

```
Evolution should now come up properly. However, you lost all settings and emails. To restore these
```

cp .evolution_backup/mail .evolution/mail
cp .evolution_backup/calendar .evolution/calendar
cp .evolution_backup/addressbook .evolution/addressbook

```
To undo everything I have said:
```

mv .evolution_backup .evolution 

```

---

