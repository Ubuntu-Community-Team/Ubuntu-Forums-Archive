---
title: "how to use cron to stop a program"
date: 2009-05-09
forum: New to Ubuntu
---

### Post by cjv8888 on 2009-05-09
How do I use cron to stop or shut down a program eg azureus at a certain time?

Tried the man cron but it did not make sense.
Thanks to all.

---

### Post by superprash2003 on 2009-05-10
15 4 * * *  killall deluge

 i use the above line in cron to stop deluge at 4:15am . So i guess you could replace deluge with your program and try..

---

### Post by cjv8888 on 2009-05-10
> **superprash2003 said:**
> 15 4 * * *  killall deluge

 i use the above line in cron to stop deluge at 4:15am . So i guess you could replace deluge with your program and try..

Do I put that in the terminal or in the crontab?

---

### Post by Partyboi2 on 2009-05-10
Hi, you can add it by typing in a terminal
```
crontab -e
```

[https://help.ubuntu.com/community/CronHowto](https://help.ubuntu.com/community/CronHowto)

---

### Post by 3rdalbum on 2009-05-10
There is a program in the repositories called gCronTab, that makes it easy to set cron jobs and swap around crontab files.

Great minds think alike - I use my home server's crontab to start and stop my bittorrent as well! I use "transmission-daemon" with the web interface, and my crontab sends commands to Transmission-Daemon using the "transmission-remote" command. I don't actually start and stop the daemon, I just use --downlimit 0 and --uplimit 0 to stop torrenting, and then --no-downlimit and --no-uplimit to get it going again.

---

