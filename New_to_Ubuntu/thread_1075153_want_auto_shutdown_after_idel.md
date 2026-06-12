---
title: "want auto shutdown after idel?"
date: 2009-02-20
forum: New to Ubuntu
---

### Post by eexpress on 2009-02-20
cat /home/xxx/xxx.bash
#!/bin/bash
[ `who -u|awk '$2 ~ /tty/ && $5 ~ /:/ {print $5}'` \> "00:15" ] && echo xxxx| sudo -S shutdown -h now

crontab -l|grep xxx.bash
*/5 * * * * /home/xxx/xxx.bash

---

