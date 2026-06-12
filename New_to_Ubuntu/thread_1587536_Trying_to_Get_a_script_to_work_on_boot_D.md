---
title: "Trying to Get a script to work on boot D:"
date: 2010-10-03
forum: New to Ubuntu
---

### Post by B00MB0X on 2010-10-03
Hi. Ive been trying to get a script to run each time i boot. the script basically starts a few other another scripts which all do the job together i guess anyways i can get the result i want by running it on (double click -> run in terminal) but i would like it to run at boot i ran the command "sudo update-rc.d server.sh default but it doenst start at boot i chmoded the file to +x still doesnt run heres the script 

#!/bin/sh
### BEGIN INIT INFO
# Provides:          server.sh
# Required-Start:    $remote_fs $syslog
# Required-Stop:     $remote_fs $syslog
# Default-Start:     2 3 4 5
# Default-Stop:      0 1 6
# Short-Description: Start Server After Power Failure
# Description:       Start up Server When Power Surges.
### END INIT INFO
xterm -e /toc/db/db.sh &
sleep 5
xterm -e /toc/login/ls.sh &
sleep 300
xterm -e /toc/game/gs.sh

---

### Post by cariboo on 2010-10-03
I know this isn't what you are trying to do, but wouldn't it be easier to change the bios setting to restart after power-outage? Or better yet get a ups?

---

### Post by B00MB0X on 2010-10-03
im sorry i have no idea what you mean i am completely new to this

---

### Post by Darkness Des on 2010-10-03
The script is in /etc/init.d, correct?

---

### Post by B00MB0X on 2010-10-03
Yes its in there

---

### Post by Darkness Des on 2010-10-03
You could try just adding an autorun entry that points to the script using the Startup Applications dialog.

---

### Post by B00MB0X on 2010-10-03
and how would i go about that? srry im VERY new to linux and anything having to do with code

---

### Post by B00MB0X on 2010-10-03
after exploring the menus i found it thanks guys that was exactly what i wanted ty sooo much i cant say how happy i am now lol my things start up just fine now :)
:P

---

