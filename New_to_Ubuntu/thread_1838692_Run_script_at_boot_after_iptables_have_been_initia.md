---
title: "Run script at boot after iptables have been initiated"
date: 2011-09-04
forum: New to Ubuntu
---

### Post by Frozen Forest on 2011-09-04
How do you start a script at boot but after iptables have been initiated, have a script for monitoring network traffic but this script relies on iptables to get useful data.

---

### Post by spiky001 on 2011-09-04
You could run the sleep command before the script, You can put the script in /etc/rc.local [http://wiki.eeeuser.com/howto:startupscript](http://wiki.eeeuser.com/howto:startupscript)  Hope it helps

---

### Post by Frozen Forest on 2011-09-04
I but the following script in /etc/init.d/ but pidof -x TrafficLimiter.py don't return any pid, so by the look of it doesn't the script start. The delayed start is implemented in TrafficLimiter.py
[PHP]
#!/bin/sh
RETVAL=0
start(){
    /home/server/Script/TrafficLimiter.py upload 4 GB &
}
stop(){
    /bin/kill $(/bin/pidof -x TrafficLimiter.py)
}

case $1 in
  start)
    start
    ;;
  stop)
    stop
    ;;
  restart)
    stop
    start
    ;;
  *)
    echo "Usage: start_tl {start|stop|restart}"
    RETVAL=1
esac

exit
[/PHP]

---

