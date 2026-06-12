---
title: "[SOLVED] script conflicts how do i resolve"
date: 2009-01-09
forum: New to Ubuntu
---

### Post by rburkartjo on 2009-01-09
okay i have the following script which i put in sessions 
shutdown 22:00 -P +10

works great however i have another script for reboot which will not work because the above one is active it is

shutdown -r now

how can i keep the first script active and still access (run) the second i know i can go to terminal and type shutdown -c to cancel the first and then i have access to the second. but i want to keep the first active and run the reboot script 
 as i deem necessary without disabling the first/tks cheesemaker

---

### Post by ushimitsudoki on 2009-01-09
I haven't actually tried this, but I would put the first shutdown in as a cron job, rather than a script.

Scheduled things should go in as cron jobs anyway, I think.

---

### Post by rburkartjo on 2009-01-09
ush, tks for the advise but didnt work/cheesemaker

---

### Post by rburkartjo on 2009-01-09
okay i resolved this myself here is how i did it might help someone else
left the timed shutdown as i wrote and kept in sessions
i modified my reboot script as follows

shutdown -c
 shutdown -r now
what this does is cancel the existing timed shutdown script allowing me to reboot but after i reboot since the timed shutdown script loads with sessions it is active again. cool beans/cheesemaker

---

