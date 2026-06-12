---
title: "Problem with startup script"
date: 2010-04-21
forum: New to Ubuntu
---

### Post by adave on 2010-04-21
Hello all.  I'm trying to get this ccxstream startup script working in an ubuntu install and unfortunately not having any luck.  I have already taken this script and turned it into a command file using the chmod a+x function.  I also checked the paths to make sure they were all correct.  Can anyone take a look and let me know what might be wrong with the  script?

One note.  When I type "sudo /etc/init.d/ccxstream start" as a test, I don't get any errors.  Just goes to next line. But that happens if I type anything in place of "start". I should be getting something like "Starting XBMSP server". Thanks.

```
#!/bin/sh
# Start/stop the ccxstream daemon.
#
### BEGIN INIT INFO
# Provides:          ccxstream
# Required-Start:    $syslog $time
# Required-Stop:     $syslog $time
# Default-Start:     2 3 4 5
# Default-Stop:      0 1 6
# Short-Description: XBMSP server
# Description:       ccxstream streams media to a modified Xbox using Xbox Media Center.
#                    The protocol is faster and more stable than XBMC's Samba integration
### END INIT INFO


test -f /home/ccxstream-1.0.15 || exit 0

. /lib/lsb/init-functions

case "$1" in
start)  log_daemon_msg "Starting XBMSP server" "ccxstream"
        start-stop-daemon --start --quiet --pidfile /var/run/ccxstream.pid --name ccxstream --startas /home/ccxstream-1.0.15 -- -f -F /var/run/ccxstream.pid -r /home/media
        log_end_msg $?
        ;;
stop)   log_daemon_msg "Stopping XBMSP server" "ccxstream"
        start-stop-daemon --stop --quiet --pidfile /var/run/ccxstream.pid --name ccxstream
        log_end_msg $?
        ;;
restart) log_daemon_msg "Restarting XBMSP server" "ccxstream"
        start-stop-daemon --stop --retry 5 --quiet --pidfile /var/run/ccxstream.pid --name ccxstream
        start-stop-daemon --start --quiet --pidfile /var/run/ccxstream.pid --name ccxstream --startas /home/ccxstream-1.0.15 -- -f -F /var/run/ccxstream.pid -r /home/media
        log_end_msg $?
        ;;
reload|force-reload) log_daemon_msg "Reloading configuration for XBMSP server" "ccxstream"
        # ccxstream reloads automatically
        log_end_msg 0
        ;;
*)      log_action_msg "Usage: /etc/init.d/ccxstream {start|stop|restart|reload|force-reload}"
        exit 2
        ;;
esac
exit 0
```

Also, I used this post as a reference to building the script and followed the directions.  [http://ubuntuforums.org/showthread.php?t=487370](http://ubuntuforums.org/showthread.php?t=487370)

---

### Post by adave on 2010-04-22
Hi everyone.  After taking a fresh look I figured out what the problem  was.  The path to ccxstream needed to include the command file.   So I  replaced

/home/ccxstream-1.0.15

with

/home/ccxstream-1.0.15/ccxstream

After that everything worked perfectly and the ccxstream server launches at start-up with no problems!

---

