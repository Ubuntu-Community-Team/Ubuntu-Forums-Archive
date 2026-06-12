---
title: "cups mistakes"
date: 2007-01-19
forum: Networking &amp; Wireless
---

### Post by dsimpson on 2007-01-19
I was attempting to link 2 computers together and used the ubuntu starter guide and entered the changes into /etc/cups/cupsd.conf before making any changes to the printer settings and now I cannot open the System/administration/Printers to make any changes and am not able to print to my printer. I get an error message that the cups server cannot be contacted. I need to get back to the default settings so I can begin anew. Is there anyone out there that can help with my problem. Thanks in advance.:confused:

---

### Post by darrenm on 2007-01-19
Can you try:

```
sudo /etc/init.d/cupsys restart
``` then try again?

---

### Post by dsimpson on 2007-01-19
Tried that, here is what it responded, but nothing changed, still unable to get into the printing module under System/Administration/Printing to make any changes. Thanks for the try..

 * Restarting Common Unix Printing System: cupsd cupsd: Child exited with status 1!
 
Any more fixes, I will try them all, keep them coming..:-k

---

### Post by darrenm on 2007-01-22
Sorry for the delay in responding.

Restart CUPS again and tail the end of /var/log/messages

```
/etc/init.d/cupsys restart && tail -f /var/log/cups/error_log
```

ctrl-c to get out of it. There will be a config typed incorrectly somewhere that it isnt liking while starting up.

---

### Post by dsimpson on 2007-01-22
Hi, (first - did restart, second - did restart and tailed the end per example) - tried and got the following; (restart) -  sudo /etc/init.d/cupsys restart, [COLOR="Blue"](result)[/COLOR] cursor went to new prompt
(restart and tail) -  /etc/init.d/cupsys restart && tail -f /var/log/cups/error_log, [COLOR="Blue"](result)[/COLOR]
[COLOR="Blue"][COLOR="Red"]E [20/Jan/2007:03:01:32 -0800] Unknown Location directive ... on line 36.
E [20/Jan/2007:03:17:37 -0800] Unknown Location directive ... on line 36.
E [20/Jan/2007:03:41:25 -0800] Unknown Location directive ... on line 36.
E [20/Jan/2007:03:49:01 -0800] Unknown Location directive ... on line 36.
E [20/Jan/2007:04:13:40 -0800] Unknown directive Only on line 15.
E [20/Jan/2007:04:13:40 -0800] Unknown Location directive ... on line 36.
E [20/Jan/2007:04:15:34 -0800] Unknown directive Only on line 15.
E [20/Jan/2007:04:15:34 -0800] Unknown Location directive ... on line 36.
E [20/Jan/2007:14:12:45 -0800] Unknown directive Only on line 15.
E [20/Jan/2007:14:12:45 -0800] Unknown Location directive ... on line 36.
[/COLOR][/COLOR]

---

### Post by darrenm on 2007-01-23
> **dsimpson said:**
> Hi, (first - did restart, second - did restart and tailed the end per example) - tried and got the following; (restart) -  sudo /etc/init.d/cupsys restart, [COLOR="Blue"](result)[/COLOR] cursor went to new prompt
(restart and tail) -  /etc/init.d/cupsys restart && tail -f /var/log/cups/error_log, [COLOR="Blue"](result)[/COLOR]
[COLOR="Blue"][COLOR="Red"]E [20/Jan/2007:03:01:32 -0800] Unknown Location directive ... on line 36.
E [20/Jan/2007:03:17:37 -0800] Unknown Location directive ... on line 36.
E [20/Jan/2007:03:41:25 -0800] Unknown Location directive ... on line 36.
E [20/Jan/2007:03:49:01 -0800] Unknown Location directive ... on line 36.
E [20/Jan/2007:04:13:40 -0800] Unknown directive Only on line 15.
E [20/Jan/2007:04:13:40 -0800] Unknown Location directive ... on line 36.
E [20/Jan/2007:04:15:34 -0800] Unknown directive Only on line 15.
E [20/Jan/2007:04:15:34 -0800] Unknown Location directive ... on line 36.
E [20/Jan/2007:14:12:45 -0800] Unknown directive Only on line 15.
E [20/Jan/2007:14:12:45 -0800] Unknown Location directive ... on line 36.
[/COLOR][/COLOR]

Looks like you got something wrong on line 15 and line 36 of /etc/cups/cupsd.conf

I would bet you unhashed the Line:

```
# Only listen for connections from the local machine.
```

and I would say that you haven't put the < at the beginning of this line?

```
<Location /admin>
```

---

### Post by dsimpson on 2007-01-23
Ok, did you want me to put the code in exactly as you did in terminal? Just those 2 lines, and are they to go to the right place?

---

### Post by darrenm on 2007-01-23
Edit /etc/cups/cupsd.conf again, go to line 15 and make sure the line reads as what I've put

then go to line 36 and make sure its the same as the 2nd line that I've put. If they are any different change them to what I've put.

---

### Post by dsimpson on 2007-01-23
Did the changes to (/etc/cups/cupsd.conf) and tried sudo aptitude install cupsys and it came up with errors still. One thing of note though, line 36 had 3 dots (...) and the location line was on line 37, it had <location /> so I made the change to <location /admin>, as you suggested. I also had to put the comment mark into the first line about Only listen for connections from the local machine. [COLOR="Red"]Was the 3 dots in line 36 an error that needs to be removed?[/COLOR]

---

### Post by darrenm on 2007-01-24
Possibly. Try doing the 

```
sudo /etc/init.d/cupsys restart && tail -f /var/log/cups/error_log
```

again and see what happens.

---

### Post by dsimpson on 2007-01-24
Tried and got this output;

* Restarting Common Unix Printing System: cupsd cupsd: Child exited with status 1!

Don't really have a clue about the Child and status 1, have you seen that before?

---

### Post by dsimpson on 2007-01-24
Here is what is in my (/etc/init.d/cupsys). Just thought I would post to see if you can find something in there that doesn't seem right. 

 #! /bin/sh

PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin
DAEMON=/usr/sbin/cupsd
NAME=cupsd
PIDFILE=/var/run/cups/$NAME.pid
DESC="Common Unix Printing System"

unset TMPDIR

test -f $DAEMON || exit 0

set -e

. /lib/lsb/init-functions

# Get the timezone set.
if [ -z "$TZ" -a -e /etc/timezone ]; then
    TZ=`cat /etc/timezone`
    export TZ
fi

case "$1" in
  start)
        log_begin_msg "Starting $DESC: $NAME"
        chown root:lpadmin /usr/share/ppd/custom 2>/dev/null || true
        chmod 3775 /usr/share/ppd/custom 2>/dev/null || true
        mkdir -p `dirname "$PIDFILE"`
        chown cupsys:lp `dirname "$PIDFILE"`

        # create the logs file since cupsd can't
        for l in access_log page_log error_log; do
            if [ ! -e /var/log/cups/$l ]; then
                 touch /var/log/cups/$l
                 chmod 640 /var/log/cups/$l
                 chown cupsys:lpadmin /var/log/cups/$l
            fi
        done

        # load modules for parallel printer support which are not covered by
        # udev
        modprobe lp 2>/dev/null || true
        modprobe ppdev 2>/dev/null || true # for ISO-1284 device name detection

        start-stop-daemon --start --quiet --oknodo --pidfile "$PIDFILE" --exec $ DAEMON
        log_end_msg $?
        ;;
  stop)
        log_begin_msg "Stopping $DESC: $NAME"
        start-stop-daemon --stop --quiet --retry 5 --oknodo --pidfile $PIDFILE - -name $NAME
        log_end_msg $?
        ;;
  restart|force-reload)
        log_begin_msg "Restarting $DESC: $NAME"
        if start-stop-daemon --stop --quiet --retry 5 --oknodo --pidfile $PIDFIL E --name $NAME; then
                start-stop-daemon --start --quiet --pidfile "$PIDFILE" --exec $D AEMON
        fi
        log_end_msg $?
        ;;
  status)
        echo -n "Status of $DESC: "
        if [ ! -r "$PIDFILE" ]; then
                echo "$NAME is not running."
                exit 3
        fi
        if read pid < "$PIDFILE" && ps -p "$pid" > /dev/null 2>&1; then
                echo "$NAME is running."
                exit 0
        else
                echo "$NAME is not running but $PIDFILE exists."
                exit 1
        fi
        ;;
  *)
        N=/etc/init.d/${0##*/}
        echo "Usage: $N {start|stop|restart|force-reload|status}" >&2
        exit 1
        ;;
esac

exit 0

---

### Post by darrenm on 2007-01-24
Its definitely that your cupsd.conf is messed up.

Can you run

```
cat /var/log/cups/error_log
``` and post the output here.

---

### Post by dsimpson on 2007-01-24
This is insane! ha!ha!..I hope that all of these errors are just a repeat of 1 or 2 errors and easy to diagnose. I hope you can find something in here. Thanks in advance, just for going through all this trouble...

not found!
E [10/Jan/2007:01:56:59 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:01:57:00 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:01:57:00 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:01:57:02 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:01:57:02 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:01:57:02 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:01:57:05 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:01:57:05 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:01:57:05 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:01:57:08 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:01:57:08 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:01:57:08 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:01:57:10 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:01:57:10 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:01:57:11 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:01:57:14 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:01:57:14 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:01:57:14 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:01:57:15 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:01:57:15 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:01:57:17 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:01:57:20 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:01:57:20 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:01:57:20 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:01:57:20 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:01:57:20 -0800] CUPS-Add-Modify-Printer: Unauthorized
E [10/Jan/2007:01:57:20 -0800] [Job 112] No %%BoundingBox: comment in header!
E [10/Jan/2007:01:57:20 -0800] PID 534 (/usr/lib/cups/backend/ipp) crashed on signal 9!
E [10/Jan/2007:01:57:21 -0800] [Job 112] No %%BoundingBox: comment in header!
E [10/Jan/2007:01:57:21 -0800] PID 624 (/usr/lib/cups/filter/pstops) crashed on signal 9!
E [10/Jan/2007:01:57:21 -0800] PID 626 (/usr/lib/cups/backend/ipp) crashed on signal 9!
E [10/Jan/2007:01:57:21 -0800] PID 637 (/usr/lib/cups/filter/pstops) crashed on signal 9!
E [10/Jan/2007:01:57:21 -0800] PID 639 (/usr/lib/cups/backend/ipp) crashed on signal 9!
E [10/Jan/2007:01:57:21 -0800] [Job 112] No %%BoundingBox: comment in header!
E [10/Jan/2007:01:57:21 -0800] PID 625 (/usr/lib/cups/filter/foomatic-rip) crashed on signal 9!
E [10/Jan/2007:01:57:21 -0800] PID 640 (/usr/lib/cups/filter/pstops) crashed on signal 9!
E [10/Jan/2007:01:57:21 -0800] PID 642 (/usr/lib/cups/backend/ipp) crashed on signal 9!
E [10/Jan/2007:01:57:21 -0800] [Job 112] No %%BoundingBox: comment in header!
E [10/Jan/2007:01:57:21 -0800] PID 638 (/usr/lib/cups/filter/foomatic-rip) crashed on signal 9!
E [10/Jan/2007:01:57:21 -0800] PID 641 (/usr/lib/cups/filter/foomatic-rip) crashed on signal 9!
E [10/Jan/2007:01:57:22 -0800] PID 643 (/usr/lib/cups/filter/pstops) crashed on signal 9!
E [10/Jan/2007:01:57:22 -0800] PID 645 (/usr/lib/cups/backend/ipp) crashed on signal 9!
E [10/Jan/2007:01:57:22 -0800] [Job 112] No %%BoundingBox: comment in header!
E [10/Jan/2007:01:57:22 -0800] PID 644 (/usr/lib/cups/filter/foomatic-rip) crashed on signal 9!
E [10/Jan/2007:01:57:22 -0800] [Job 112] No %%BoundingBox: comment in header!
E [10/Jan/2007:01:57:22 -0800] PID 646 (/usr/lib/cups/filter/pstops) crashed on signal 9!
E [10/Jan/2007:01:57:22 -0800] PID 647 (/usr/lib/cups/filter/foomatic-rip) crashed on signal 9!
E [10/Jan/2007:01:57:22 -0800] PID 648 (/usr/lib/cups/backend/ipp) crashed on signal 9!
E [10/Jan/2007:01:57:22 -0800] PID 649 (/usr/lib/cups/filter/pstops) crashed on signal 9!
E [10/Jan/2007:01:57:22 -0800] [Job 112] No %%BoundingBox: comment in header!
E [10/Jan/2007:01:57:22 -0800] PID 651 (/usr/lib/cups/backend/ipp) crashed on signal 9!
E [10/Jan/2007:01:57:22 -0800] PID 650 (/usr/lib/cups/filter/foomatic-rip) crashed on signal 9!
E [10/Jan/2007:01:57:22 -0800] [Job 112] No %%BoundingBox: comment in header!
E [10/Jan/2007:01:57:22 -0800] PID 653 (/usr/lib/cups/filter/pstops) crashed on signal 9!
E [10/Jan/2007:01:57:22 -0800] PID 656 (/usr/lib/cups/backend/ipp) crashed on signal 9!
E [10/Jan/2007:01:57:22 -0800] PID 655 (/usr/lib/cups/filter/foomatic-rip) crashed on signal 9!
E [10/Jan/2007:01:57:24 -0800] [Job 112] No %%BoundingBox: comment in header!
E [10/Jan/2007:01:57:24 -0800] PID 659 (/usr/lib/cups/backend/ipp) crashed on signal 9!
E [10/Jan/2007:01:57:24 -0800] PID 658 (/usr/lib/cups/filter/foomatic-rip) crashed on signal 9!
E [10/Jan/2007:01:57:24 -0800] [Job 112] No %%BoundingBox: comment in header!
E [10/Jan/2007:01:57:25 -0800] PID 670 (/usr/lib/cups/filter/pstops) crashed on signal 9!
E [10/Jan/2007:01:57:25 -0800] PID 672 (/usr/lib/cups/backend/ipp) crashed on signal 9!
E [10/Jan/2007:01:57:25 -0800] PID 671 (/usr/lib/cups/filter/foomatic-rip) crashed on signal 9!
E [10/Jan/2007:01:57:25 -0800] PID 674 (/usr/lib/cups/filter/pstops) crashed on signal 9!
E [10/Jan/2007:01:57:25 -0800] PID 675 (/usr/lib/cups/filter/foomatic-rip) crashed on signal 9!
E [10/Jan/2007:01:57:25 -0800] PID 676 (/usr/lib/cups/backend/ipp) crashed on signal 9!
E [10/Jan/2007:01:57:25 -0800] [Job 112] No %%BoundingBox: comment in header!
E [10/Jan/2007:01:57:25 -0800] [Job 112] No %%BoundingBox: comment in header!
E [10/Jan/2007:01:57:25 -0800] PID 677 (/usr/lib/cups/filter/pstops) crashed on signal 9!
E [10/Jan/2007:01:57:25 -0800] PID 678 (/usr/lib/cups/filter/foomatic-rip) crashed on signal 9!
E [10/Jan/2007:01:57:25 -0800] PID 679 (/usr/lib/cups/backend/ipp) crashed on signal 9!
E [10/Jan/2007:01:57:25 -0800] [Job 112] No %%BoundingBox: comment in header!
E [10/Jan/2007:01:57:25 -0800] PID 680 (/usr/lib/cups/filter/pstops) crashed on signal 9!
E [10/Jan/2007:01:57:25 -0800] PID 682 (/usr/lib/cups/backend/ipp) crashed on signal 9!
E [10/Jan/2007:01:57:25 -0800] PID 681 (/usr/lib/cups/filter/foomatic-rip) crashed on signal 9!
E [10/Jan/2007:01:57:26 -0800] [Job 112] No %%BoundingBox: comment in header!
E [10/Jan/2007:01:57:26 -0800] PID 683 (/usr/lib/cups/filter/pstops) crashed on signal 9!
E [10/Jan/2007:01:57:26 -0800] PID 685 (/usr/lib/cups/backend/ipp) crashed on signal 9!
E [10/Jan/2007:01:57:26 -0800] PID 692 (/usr/lib/cups/filter/pstops) crashed on signal 9!
E [10/Jan/2007:01:57:26 -0800] PID 694 (/usr/lib/cups/backend/ipp) crashed on signal 9!
E [10/Jan/2007:01:57:26 -0800] [Job 112] No %%BoundingBox: comment in header!
E [10/Jan/2007:01:57:26 -0800] PID 684 (/usr/lib/cups/filter/foomatic-rip) crashed on signal 9!
E [10/Jan/2007:01:57:26 -0800] PID 693 (/usr/lib/cups/filter/foomatic-rip) crashed on signal 9!
E [10/Jan/2007:01:57:26 -0800] [Job 112] No %%BoundingBox: comment in header!
E [10/Jan/2007:01:57:26 -0800] PID 695 (/usr/lib/cups/filter/pstops) crashed on signal 9!
E [10/Jan/2007:01:57:26 -0800] PID 696 (/usr/lib/cups/filter/foomatic-rip) crashed on signal 9!
E [10/Jan/2007:01:57:26 -0800] PID 697 (/usr/lib/cups/backend/ipp) crashed on signal 9!
E [10/Jan/2007:01:57:38 -0800] [Job 113] No %%BoundingBox: comment in header!
E [10/Jan/2007:02:01:51 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:01:51 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:01:56 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:01:56 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:02:01 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:02:01 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:02:06 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:02:06 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:02:11 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:02:11 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:02:16 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:02:16 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:02:21 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:02:21 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:02:26 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:02:26 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:02:31 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:02:31 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:02:36 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:02:36 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:02:41 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:02:41 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:02:46 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:02:46 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:02:51 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:02:51 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:02:56 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:02:56 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:03:01 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:03:01 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:03:06 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:03:06 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:03:11 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:03:11 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:03:16 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:03:16 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:03:21 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:03:21 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:03:26 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:03:26 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:03:31 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:03:31 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:03:36 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:03:36 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:03:41 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:03:41 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:03:46 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:03:46 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:03:51 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:03:51 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:03:56 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:03:56 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:04:01 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:04:01 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:04:06 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:04:06 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:04:11 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:04:11 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:04:16 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:04:16 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:04:21 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:04:21 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:04:26 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:04:26 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:04:31 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:04:31 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:04:36 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:04:36 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:04:41 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:04:41 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:04:46 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:04:46 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:04:51 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:04:51 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:04:56 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:04:56 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:05:01 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:05:01 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:05:06 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:05:06 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:05:11 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:05:11 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:05:16 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:05:16 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:05:21 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:05:21 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:05:26 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:05:26 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:05:31 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:05:31 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:05:36 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:05:36 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:05:41 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:05:41 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:05:46 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:05:46 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:05:51 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:05:51 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:05:56 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:05:56 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:06:01 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:06:01 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:06:06 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:06:06 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:06:11 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:06:11 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:06:16 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:06:16 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:06:21 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:06:21 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:06:26 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:06:26 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:06:31 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:06:31 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:06:36 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:06:36 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:06:41 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:06:41 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:06:46 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:06:46 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:06:51 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:06:51 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:06:56 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:06:56 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:07:01 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:07:01 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:07:06 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:07:06 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:07:11 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:07:11 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:07:16 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:07:16 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:07:21 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:07:21 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:07:26 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:07:26 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:07:31 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:07:31 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:07:37 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:07:37 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:07:42 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:07:42 -0800] cupsdAuthorize: Local authentication certificate not found!
E [15/Jan/2007:20:19:22 -0800] Creating missing directory "/var/run/cups/certs"
E [15/Jan/2007:22:39:29 -0800] Creating missing directory "/var/run/cups/certs"
E [15/Jan/2007:23:06:43 -0800] Creating missing directory "/var/run/cups/certs"
E [17/Jan/2007:20:59:48 -0800] Creating missing directory "/var/run/cups/certs"
E [17/Jan/2007:21:38:37 -0800] Creating missing directory "/var/run/cups/certs"
E [17/Jan/2007:21:51:43 -0800] Creating missing directory "/var/run/cups/certs"
E [18/Jan/2007:11:51:19 -0800] Creating missing directory "/var/run/cups/certs"
E [18/Jan/2007:20:58:17 -0800] Creating missing directory "/var/run/cups/certs"
E [18/Jan/2007:23:18:33 -0800] Creating missing directory "/var/run/cups/certs"
E [18/Jan/2007:23:58:22 -0800] Unknown Location directive ... on line 34.
E [19/Jan/2007:00:21:38 -0800] Unknown Location directive ... on line 34.
E [19/Jan/2007:01:05:13 -0800] Unknown Location directive ... on line 36.
E [19/Jan/2007:01:05:18 -0800] Unknown Location directive ... on line 36.
E [19/Jan/2007:11:29:32 -0800] Unknown Location directive ... on line 36.
E [20/Jan/2007:01:48:17 -0800] Unknown Location directive ... on line 36.
E [20/Jan/2007:02:05:08 -0800] Unknown Location directive ... on line 36.
E [20/Jan/2007:02:05:56 -0800] Unknown Location directive ... on line 36.
E [20/Jan/2007:02:07:28 -0800] Unknown Location directive ... on line 36.
E [20/Jan/2007:02:49:40 -0800] Unknown Location directive ... on line 36.
E [20/Jan/2007:03:01:32 -0800] Unknown Location directive ... on line 36.
E [20/Jan/2007:03:17:37 -0800] Unknown Location directive ... on line 36.
E [20/Jan/2007:03:41:25 -0800] Unknown Location directive ... on line 36.
E [20/Jan/2007:03:49:01 -0800] Unknown Location directive ... on line 36.
E [20/Jan/2007:04:13:40 -0800] Unknown directive Only on line 15.
E [20/Jan/2007:04:13:40 -0800] Unknown Location directive ... on line 36.
E [20/Jan/2007:04:15:34 -0800] Unknown directive Only on line 15.
E [20/Jan/2007:04:15:34 -0800] Unknown Location directive ... on line 36.
E [20/Jan/2007:14:12:45 -0800] Unknown directive Only on line 15.
E [20/Jan/2007:14:12:45 -0800] Unknown Location directive ... on line 36.
E [23/Jan/2007:16:36:22 -0800] Unknown directive Only on line 15.
E [23/Jan/2007:16:36:22 -0800] Unknown Location directive ... on line 36.
E [23/Jan/2007:16:36:26 -0800] Unknown directive Only on line 15.
E [23/Jan/2007:16:36:26 -0800] Unknown Location directive ... on line 36.
E [23/Jan/2007:17:16:00 -0800] Unknown directive Only on line 15.
E [23/Jan/2007:17:16:00 -0800] Unknown Location directive ... on line 36.
E [23/Jan/2007:17:16:03 -0800] Unknown directive Only on line 15.
E [23/Jan/2007:17:16:03 -0800] Unknown Location directive ... on line 36.
E [23/Jan/2007:17:20:46 -0800] Unknown directive Only on line 15.
E [23/Jan/2007:17:20:46 -0800] Unknown Location directive ... on line 36.
E [23/Jan/2007:17:20:50 -0800] Unknown directive Only on line 15.
E [23/Jan/2007:17:20:50 -0800] Unknown Location directive ... on line 36.
E [23/Jan/2007:17:34:54 -0800] Unknown directive Only on line 15.
E [23/Jan/2007:17:34:54 -0800] Unknown Location directive ... on line 36.
E [23/Jan/2007:17:34:58 -0800] Unknown directive Only on line 15.
E [23/Jan/2007:17:34:58 -0800] Unknown Location directive ... on line 36.
E [23/Jan/2007:17:42:01 -0800] Unknown Location directive ... on line 36.
E [23/Jan/2007:17:42:05 -0800] Unknown Location directive ... on line 36.
E [24/Jan/2007:00:35:33 -0800] Unknown Location directive ... on line 36.
E [24/Jan/2007:01:05:39 -0800] Unknown Location directive ... on line 36.
E [24/Jan/2007:01:06:33 -0800] Unknown Location directive ... on line 36.
E [24/Jan/2007:01:06:37 -0800] Unknown Location directive ... on line 36.
E [24/Jan/2007:01:07:58 -0800] Unknown Location directive ... on line 36.
E [24/Jan/2007:01:08:02 -0800] Unknown Location directive ... on line 36.
E [24/Jan/2007:01:08:57 -0800] Unknown Location directive ... on line 36.
E [24/Jan/2007:01:26:39 -0800] Unknown Location directive ... on line 36.
E [24/Jan/2007:01:28:09 -0800] Unknown Location directive ... on line 36.
eaglesoldier@eaglesoldier:~$

:frown:

---

### Post by darrenm on 2007-01-24
Its telling you exactly what the problem is

On line 15 something is wrong and on line 36 something is wrong.

line 15 now looks ok so just have a look at line 36 and remove the ... on the line.

---

### Post by dsimpson on 2007-01-24
No go yet. Still getting the same error 
eaglesoldier@eaglesoldier:~$ sudo /etc/init.d/cupsys restart && tail -f /var/log/cups/error_log
 [COLOR="Red"]* Restarting Common Unix Printing System: cupsd cupsd: Child exited with status 1!
[/COLOR]

here is just the end of the error_log this time, all the rest is just the same. 

E [20/Jan/2007:04:13:40 -0800] Unknown directive Only on line 15.
E [20/Jan/2007:04:13:40 -0800] Unknown Location directive ... on line 36.
E [20/Jan/2007:04:15:34 -0800] Unknown directive Only on line 15.
E [20/Jan/2007:04:15:34 -0800] Unknown Location directive ... on line 36.
E [20/Jan/2007:14:12:45 -0800] Unknown directive Only on line 15.
E [20/Jan/2007:14:12:45 -0800] Unknown Location directive ... on line 36.
E [23/Jan/2007:16:36:22 -0800] Unknown directive Only on line 15.
E [23/Jan/2007:16:36:22 -0800] Unknown Location directive ... on line 36.
E [23/Jan/2007:16:36:26 -0800] Unknown directive Only on line 15.
E [23/Jan/2007:16:36:26 -0800] Unknown Location directive ... on line 36.
E [23/Jan/2007:17:16:00 -0800] Unknown directive Only on line 15.
E [23/Jan/2007:17:16:00 -0800] Unknown Location directive ... on line 36.
E [23/Jan/2007:17:16:03 -0800] Unknown directive Only on line 15.
E [23/Jan/2007:17:16:03 -0800] Unknown Location directive ... on line 36.
E [23/Jan/2007:17:20:46 -0800] Unknown directive Only on line 15.
E [23/Jan/2007:17:20:46 -0800] Unknown Location directive ... on line 36.
E [23/Jan/2007:17:20:50 -0800] Unknown directive Only on line 15.
E [23/Jan/2007:17:20:50 -0800] Unknown Location directive ... on line 36.
E [23/Jan/2007:17:34:54 -0800] Unknown directive Only on line 15.
E [23/Jan/2007:17:34:54 -0800] Unknown Location directive ... on line 36.
E [23/Jan/2007:17:34:58 -0800] Unknown directive Only on line 15.
E [23/Jan/2007:17:34:58 -0800] Unknown Location directive ... on line 36.
E [23/Jan/2007:17:42:01 -0800] Unknown Location directive ... on line 36.
E [23/Jan/2007:17:42:05 -0800] Unknown Location directive ... on line 36.
E [24/Jan/2007:00:35:33 -0800] Unknown Location directive ... on line 36.
E [24/Jan/2007:01:05:39 -0800] Unknown Location directive ... on line 36.
E [24/Jan/2007:01:06:33 -0800] Unknown Location directive ... on line 36.
E [24/Jan/2007:01:06:37 -0800] Unknown Location directive ... on line 36.
E [24/Jan/2007:01:07:58 -0800] Unknown Location directive ... on line 36.
E [24/Jan/2007:01:08:02 -0800] Unknown Location directive ... on line 36.
E [24/Jan/2007:01:08:57 -0800] Unknown Location directive ... on line 36.
E [24/Jan/2007:01:26:39 -0800] Unknown Location directive ... on line 36.
E [24/Jan/2007:01:28:09 -0800] Unknown Location directive ... on line 36.
E [24/Jan/2007:02:14:07 -0800] Unknown Location directive </Location on line 36.E [24/Jan/2007:02:18:22 -0800] Unknown Location directive </Location on line 36.E [24/Jan/2007:02:18:28 -0800] Unknown Location directive </Location on line 36.E [24/Jan/2007:02:19:16 -0800] Unknown Location directive </Location on line 36.E [24/Jan/2007:02:27:04 -0800] Unknown Location directive </Location on line 37.E [24/Jan/2007:02:41:54 -0800] Unknown Location directive </Location on line

---

### Post by darrenm on 2007-01-24
Heres an unconfigured cupsd.conf, just copy it over yours :)

```
gunzip cupsd.conf.gz && sudo cp -f cupsd.conf /etc/cups/
```

---

### Post by dsimpson on 2007-01-24
I can't even get that to open. it gave me the message 

gunzip: cupsd.conf.gz: No such file or directory

Will I ever get this back in order??:frown:

---

### Post by darrenm on 2007-01-24
You have to run the command in the same directory that you saved the file to.

---

### Post by dsimpson on 2007-01-24
Sorry to have to ask, probably something simple that almost everyone should know, but I don't..Do I cd to cups, cupsd.conf, cupsys?  or do I open etc/cups/cupsd.conf and unpack the zip file in there? If you can walk me through this I would greatly appreciate it, I don't want to make any additional errors at this point. Thank you...:)

---

### Post by darrenm on 2007-01-25
No probs.

click the attached file above in my earlier post
choose to save it to your desktop
open a console and type
```
cd ~/Desktop
gunzip cupsd.conf.gz && sudo cp -f cupsd.conf /etc/cups/
```

Then just follow the earlier advice to restart cups or just reboot the PC.

HTH :)

---

### Post by dsimpson on 2007-01-25
Thank you Paerez, that did the trick. I thank you especially for your patience and for your diligence in coming back to my post and walking me through this.. with someone like you to help Ubuntu will succeed. Thanks again!!

---

