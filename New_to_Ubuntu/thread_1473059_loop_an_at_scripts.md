---
title: "loop an at scripts"
date: 2010-05-04
forum: New to Ubuntu
---

### Post by lance bermudez on 2010-05-04
i can not get my cron job to work
[http://ubuntuforums.org/showthread.php?t=1466730](http://ubuntuforums.org/showthread.php?t=1466730)

but if i do an at with a script it work what i want to know is how do i loop the script to run say once every 24 hours

i have the below in the script. I know it is unsafe but my cron job will not run.

#!/bin/bash
echo "password" | sudo apt-get update; apt-get dist-upgrade; notify-send "Computer updated and upgraded" -t 0

---

