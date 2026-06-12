---
title: "update databse script on shutdown(vnstat)?"
date: 2008-02-28
forum: Networking &amp; Wireless
---

### Post by dynamethod on 2008-02-28
Hey there im using vnstat to monitor my internet usage, however is there a script or way(cron maybe? i dont know much about cron though) to update the vnstat database after i choose to shutdown the computer?

---

### Post by dynamethod on 2008-02-28
Or does vnstat do this automatically when i shutdown?

---

### Post by Vergo on 2008-03-02
vnStat doesn't automatically run a database update when the system is shutting down or going for a reboot because the current versions rely totally on cron. By default, the cron entry makes vnStat update databases every 5 minute so it can depend a little bit how much data you kind of loose when a shutdown / reboot is started.

You can change the update interval from /etc/cron.d/vnstat. The first column is probably something like "*/5" or "0-55/5". Both stand for one run every five minute. Change that to "*" (without the "-characters of course) and it will start updating every minute and the data lost at shutdown / reboot should be smaller. Another way would be to modify some shutdown script to include "vnstat -u" before the network interface is turned off. Possible the stop function of /etc/init.d/networking could be one such place.

I know that using cron for updating things has some limitation and that's a reason why I'm currently working on getting vnStat to run optionally as a daemon. That way it could automatically run a final update when the shutdown / reboot command is given.

---

