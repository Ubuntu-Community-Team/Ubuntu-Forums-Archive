---
title: "init.d startup script for pppd"
date: 2008-11-24
forum: Networking &amp; Wireless
---

### Post by x0x on 2008-11-24
Hello. i am looking for a script to connect to internet via ppp on boot. can anyone help me with it please?

---

### Post by x0x on 2008-11-24
hi. i found a howto create your own init.d script.. 

```
#!/bin/sh

test -s /etc/rc.status && . /etc/rc.status && rc_reset

PIDFILE=/var/run/ppp0.pid

case "$1" in
    start)
        if [ -f $PIDFILE ]
        then
                echo "$PIDFILE exists, process is already running or crashed"
                rc_failed 1
                rc_status -v1
        else
                echo -n "Starting pppd... "
                pppd call gp > /dev/null 2>&1
                rc_status -v
        fi
        ;;
    stop)
        if [ ! -f $PIDFILE ]
        then
                echo "$PIDFILE does not exist, process is not running"
                rc_failed 1
                rc_status -v1
        else
                echo -n "Stoping pppd... "
                killall pppd
                rc_status -v
        fi
        ;;
    restart)
        if [ -f $PIDFILE ]
        then
                echo -n "Restarting pppd... "
                killall pppd
                pppd call gp > /dev/null 2>&1
                rc_status -v
        else
                echo -n "pppd is not running... Starting pppd..."
                pppd call gp > /dev/null 2>&1
                rc_status -v
        fi
        ;;
    *)
        echo "Usage $0 start|stop|restart"
        exit 1
        ;;
esac
rc_exit

```

will it work?

---

