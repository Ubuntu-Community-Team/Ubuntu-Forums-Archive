---
title: "mysqldump command not working at reboot"
date: 2011-04-15
forum: New to Ubuntu
---

### Post by Guruprasad on 2011-04-15
I have created a script for mysqldump. Added that script to cron. It works fine when i run it every hour or every minute. But it does not work when i run it at reboot. The dump file generated is empty.

mysqldump -u "username" -pPassword "databsae" > "path/to/dump.sql"

---

### Post by r-senior on 2011-04-15
How have you configured it to run at reboot?

Depending how you did it, it is possible that MySQL is not running when the script runs.

---

### Post by Guruprasad on 2011-04-15
Thought of delaying the script for 5 minutes so that other required stuff like mysql is loaded properly.

I added sleep 5m before the mysqldump command and it worked.

> 
sleep 5m
mysqldump -u "username" -pPassword "databsae" > "path/to/dump.sql"


---

