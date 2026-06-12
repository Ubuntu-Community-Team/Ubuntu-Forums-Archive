---
title: "FTP mount failed on startup even though i removed it from startup list..."
date: 2014-05-01
forum: Networking &amp; Wireless
---

### Post by Sindri_K. on 2014-05-01
So, i'm running 12.04 LTS.

A while ago, i was using FTP to connect my laptop computer to my main home computer, so that i could access my school documents from anywhere. So i created a bash script to mount to my FTP's on startup.

But, i no longer use those FTP's and have shut them down. And i removed the command from "Startup Programs" and indeed deleted the script, but it still tries to mount on startup. Is there a second list that Ubuntu runs through for startup programs or?

BTW, this is not an urgent problem so if there is no quick solution then that is ok.

-Sindri

---

### Post by tfrue on 2014-05-01
Maybe you have edited the fstab file. So, if you don't mind, post the output of:
```
cat /etc/fstab
```

Thanks,
Chris

---

### Post by Sindri_K. on 2014-05-03
ah, there it is. I recognized my address in one line, well, the only line and removed the line.  After a restart the problem is gone. Thanks!  -Sindri

---

