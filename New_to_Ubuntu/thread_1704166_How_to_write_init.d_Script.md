---
title: "How to write init.d Script?"
date: 2011-03-10
forum: New to Ubuntu
---

### Post by opensource10 on 2011-03-10
Hello Ubuntu User,

I have some question here, I want to add my program called "fw1loggrabber" inside /etc/init.d so the program can run once computer boots up. 

I have check general step in internet, step that i can do are create init script and make a symbol link to start and stop the program.

In order to create init script, i have modified "Skeleton" to be suitable to my programm. Here are the code ...

```
#! /bin/sh
### BEGIN INIT INFO
#
# Provides : fw1loggrabber
# Required-Start : $remote_fs
# Required-Stop  : $remote_fs
# Default-Start     : 2 3 4 5
# Default-Stop     : 0 1 6
# Short-Description : Example initscript
# Description : This file should be used to construct scripts to be placed in /etc/init.d.
#
### END INIT INFO

# PATH should only include /usr/* if it runs after the mountnfs.sh script
PATH=/sbin:/usr/sbin:/bin:/usr/bin
DESC="Description of the Loggrabber"
NAME=fw1loggrabber
DAEMON=/usr/sbin/$NAME
DAEMON_ARGS="--options args"
PIDFILE=/var/run/$NAME.pid
SCRIPTNAME=/etc/init.d/$NAME

# Exit if the package is not installed
[ -x "$DAEMON" ] || exit 0

# Read configuration variable file if it is present
[ -r /etc/default/$NAME] && . /etc/default/$NAME

# Load the VERBOSE setting and other rcS variables
. /lib/init/vars.sh

# Define LSB log_* functions.
# Depend on lsb-base (>= 3.0-6) to ensure that this file is present
. /lib/lsb/init-functions

#
# Function that starts the daemon/service
#

do_start ()

{
    # Return 
    # 0 if daemon has been started
    # 1 if daemon was already running
    # 2 if daemon could not be started
    
    start-stop-daemon --start --quite --pidfile $PIDFILE --exec $DAEMON --test > /dev/null \
        || return 1
    start-stop-daemon --start --quite --pidfile $PIDFILE --exec $DAEMON -- \ 
        $DAEMON_ARGS \
        || return 2
        
    # Add code here, if necessary, that waits for the process to be ready
    # to handle requests from services started subsequently which depend
    # on this one.  As a last resort, sleep for some time.
}

#
# Function that stops the daemon/service
#
do_stop()
{
        # Return
        #   0 if daemon has been stopped
        #   1 if daemon was already stopped
        #   2 if daemon could not be stopped
        #   other if a failure occurred
        start-stop-daemon --stop --quiet --retry=TERM/30/KILL/5 --pidfile $PIDFILE --name $NAME
        RETVAL="$?"
        [ "$RETVAL" = 2 ] && return 2
        # Wait for children to finish too if this is a daemon that forks
        # and if the daemon is only ever run from this initscript.
        # If the above conditions are not satisfied then add some other code
        # that waits for the process to drop all resources that could be
        # needed by services started subsequently.  A last resort is to
        # sleep for some time.
        start-stop-daemon --stop --quiet --oknodo --retry=0/30/KILL/5 --exec $DAEMON
        [ "$?" = 2 ] && return 2
        # Many daemons don't delete their pidfiles when they exit.
        rm -f $PIDFILE
        return "$RETVAL"
}

#
# Function that sends a SIGHUP to the daemon/service
#
do_reload() {
        #
        # If the daemon can reload its configuration without
        # restarting (for example, when it is sent a SIGHUP),
        # then implement that here.
        #
        start-stop-daemon --stop --signal 1 --quiet --pidfile $PIDFILE --name $NAME
        return 0
}

case "$1" in
  start)
        [ "$VERBOSE" != no ] && log_daemon_msg "Starting $DESC" "$NAME"
        do_start
        case "$?" in
                0|1) [ "$VERBOSE" != no ] && log_end_msg 0 ;;
                2) [ "$VERBOSE" != no ] && log_end_msg 1 ;;
        esac
        ;;
  stop)
        [ "$VERBOSE" != no ] && log_daemon_msg "Stopping $DESC" "$NAME"
        do_stop
        case "$?" in
                0|1) [ "$VERBOSE" != no ] && log_end_msg 0 ;;
                2) [ "$VERBOSE" != no ] && log_end_msg 1 ;;
        esac
        ;;
  #reload|force-reload)
        #
        # If do_reload() is not implemented then leave this commented out
        # and leave 'force-reload' as an alias for 'restart'.
        #
        #log_daemon_msg "Reloading $DESC" "$NAME"
        #do_reload
        #log_end_msg $?
        #;;
  restart|force-reload)
        #
        # If the "reload" option is implemented then remove the
        # 'force-reload' alias
        # 
        log_daemon_msg "Restarting $DESC" "$NAME"
        do_stop
        case "$?" in
          0|1)
                do_start
                case "$?" in
                        0) log_end_msg 0 ;;
                        1) log_end_msg 1 ;; # Old process is still running
                        *) log_end_msg 1 ;; # Failed to start
                esac
                ;;
          *)
                # Failed to stop
                log_end_msg 1
                ;;
        esac
        ;;
  *)
        #echo "Usage: $SCRIPTNAME {start|stop|restart|reload|force-reload}" >&2
        echo "Usage: $SCRIPTNAME {start|stop|restart|force-reload}" >&2
        exit 3
        ;;
esac

:
```Can someone give me a guidance or suggestion, whether my code or whether i am doing right or not?

Thanks in advance :)

---

### Post by cipherboy_loc on 2011-03-10
I hate to tell you this, but most of the stuff in that file is pure fluff. I will work on mocking up a basic (but expandable) init script for you, but in essence, its just a bash script with a couple of functions (start/stop/status), and a switch statement to choose between them.



Cipherboy

---

### Post by opensource10 on 2011-03-10
> **cipherboy_loc said:**
> I hate to tell you this, but most of the stuff in that file is pure fluff. I will work on mocking up a basic (but expandable) init script for you, but in essence, its just a bash script with a couple of functions (start/stop/status), and a switch statement to choose between them.

Cipherboy

Hi Cipherboy,

Thanks for the respond :P.

Appreciate if you can also teach me to modify this 'Skeleton' file...

another question are **init.d** or **start-stop-daemon** or **chkconfig command** have a same function which is to add some program while computer boots up?:confused:

---

### Post by cipherboy_loc on 2011-03-10
Okay, so here is a basic init.d script with start, stop and restart/reload features:

```

#!/bin/bash

## Fill in name of program here.
PROG="pi"
PROG_PATH="/usr/bin" ## Not need, but sometimes helpful (if $PROG resides in /opt for example).
PROG_ARGS="10000000" 
PID_PATH="/var/run/"

start() {
    if [ -e "$PID_PATH/$PROG.pid" ]; then
        ## Program is running, exit with error.
        echo "Error! $PROG is currently running!" 1>&2
        exit 1
    else
        ## Change from /dev/null to something like /var/log/$PROG if you want to save output.
            $PROG_PATH/$PROG $PROG_ARGS 2>&1 >/dev/null &
        echo "$PROG started"
        touch "$PID_PATH/$PROG.pid"
    fi
}

stop() {
    if [ -e "$PID_PATH/$PROG.pid" ]; then
        ## Program is running, so stop it
        killall $PROG

        rm "$PID_PATH/$PROG.pid"
        
        echo "$PROG stopped"
    else
        ## Program is not running, exit with error.
        echo "Error! $PROG not started!" 1>&2
        exit 1
    fi
}

## Check to see if we are running as root first.
## Found at http://www.cyberciti.biz/tips/shell-root-user-check-script.html
if [ "$(id -u)" != "0" ]; then
    echo "This script must be run as root" 1>&2
    exit 1
fi

case "$1" in
    start)
        start
        exit 0
    ;;
    stop)
        stop
        exit 0
    ;;
    reload|restart|force-reload)
        stop
        start
        exit 0
    ;;
    **)
        echo "Usage: $0 {start|stop|reload}" 1>&2
        exit 1
    ;;
esac

```
So name it something, modify the variables at the top, and save it to /etc/init.d/. To get it to start at startup, run:

```

$ ll /etc/init.d/trial
-rwxr-xr-x 1 root root 1222 2011-03-10 07:48 /etc/init.d/trial

$ sudo update-rc.d trial defaults
update-rc.d: warning: /etc/init.d/trial missing LSB information
update-rc.d: see <http://wiki.debian.org/LSBInitScripts>
 Adding system startup for /etc/init.d/trial ...
   /etc/rc0.d/K20trial -> ../init.d/trial
   /etc/rc1.d/K20trial -> ../init.d/trial
   /etc/rc6.d/K20trial -> ../init.d/trial
   /etc/rc2.d/S20trial -> ../init.d/trial
   /etc/rc3.d/S20trial -> ../init.d/trial
   /etc/rc4.d/S20trial -> ../init.d/trial
   /etc/rc5.d/S20trial -> ../init.d/trial


```
Do you see how it gives us this error about missing LSB information? That is the "fluff" that your skeleton script provides. Namely, after the hashbang line (#!/bin/bash) add something:

```

### BEGIN INIT INFO
#
# Provides : example
# Required-Start : $remote_fs
# Required-Stop  : $remote_fs
# Default-Start     : 2 3 4 5
# Default-Stop     : 0 1 6
# Short-Description : Example initscript
# Description : This file should be used to construct scripts to be placed in /etc/init.d.
#
### END INIT INFO
```

Edit:
Side note:
If you notice, my script is not fully compatible with yours, because (namely) rather than exiting with error code 2 if it couldn't be stopped, it continues on (but outputs the results of killall). If you program(s) do not continue running, you can modify the stop to call different ones on stop, etc. (Like if you use an init script to mount a NFS share, you could then specify a different program to be called when the script gets stoped).


If you have any more questions, feel free to post back.
Cipherboy

---

### Post by opensource10 on 2011-03-10
Hi Cipherboy,

Thousand thanks for your help...=D>

Please give me some time to understand about your code. I may need to learn the code (as I am new on  this field) and will get back to you if i have questions.

Regards

---

### Post by cipherboy_loc on 2011-03-10
If you need some help with bash scripting, I often look at [http://tldp.org/LDP/abs/html/](http://tldp.org/LDP/abs/html/) and [http://www.cyberciti.biz/](http://www.cyberciti.biz/)

---

### Post by opensource10 on 2011-03-10
Hello Sir,

I am confuse here...In order init.d script has 'connection' to my programe, fw1loggrabber. is there something i need to modify from the code you provide to me? maybe such as Process' name or Path?

What is the meaning of PROG="pi" ? could I change as in PROG="fw1loggrabber"?

Thanks for the link...

---

### Post by opensource10 on 2011-03-10
Hi Cipherboy,

I have followed your previous thread reply. I write my init script as bellow 

```
#!/bin/bash 
### BEGIN INIT INFO
#
# Provides : fw1loggrabber
# Required-Start : $remote_fs
# Required-Stop  : $remote_fs
# Default-Start     : 2 3 4 5
# Default-Stop      : 0 1 6
# Short-Description : Log grabber for Checkpointfirewall
# Description : Program that capture traffic form the Checkpointfirewall and will send the log to Server management
#               This file should be used to construct scripts to be placed in /etc/init.d.
#
### END INIT INFO

PROG="pi"
PROG_PATH="/usr/bin" ## Not need, but sometimes helpful (if $PROG resides in /opt for example).
PROG_ARGS="10000000" 
PID_PATH="/var/run/"

start() {
    if [ -e "$PID_PATH/$PROG.pid" ]; then
        ## Program is running, exit with error.
        echo "Error! $PROG is currently running!" 1>&2
        exit 1
    else
        ## Change from /dev/null to something like /var/log/$PROG if you want to save output.
            $PROG_PATH/$PROG $PROG_ARGS 2>&1 >/dev/null &
        echo "$PROG started"
        touch "$PID_PATH/$PROG.pid"
    fi
}

stop() {
    if [ -e "$PID_PATH/$PROG.pid" ]; then
        ## Program is running, so stop it
        killall $PROG

        rm "$PID_PATH/$PROG.pid"
        
        echo "$PROG stopped"
    else
        ## Program is not running, exit with error.
        echo "Error! $PROG not started!" 1>&2
        exit 1
    fi
}

## Check to see if we are running as root first.
## Found at http://www.cyberciti.biz/tips/shell-root-user-check-script.html
if [ "$(id -u)" != "0" ]; then
    echo "This script must be run as root" 1>&2
    exit 1
fi

case "$1" in
    start)
        start
        exit 0
    ;;
    stop)
        stop
        exit 0
    ;;
    reload|restart|force-reload)
        stop
        start
        exit 0
    ;;
    **)
        echo "Usage: $0 {start|stop|reload}" 1>&2
        exit 1
    ;;
esac
```and then 

```
opensourcesim:/etc/init.d# update-rc.d fw1loggrabber defaults
update-rc.d: warning: /etc/init.d/fw1loggrabber missing LSB keyword 'provides'
update-rc.d: warning: /etc/init.d/fw1loggrabber missing LSB keyword 'required-start'
update-rc.d: warning: /etc/init.d/fw1loggrabber missing LSB keyword 'required-stop'
update-rc.d: warning: /etc/init.d/fw1loggrabber missing LSB keyword 'default-start'
update-rc.d: warning: /etc/init.d/fw1loggrabber missing LSB keyword 'default-stop'
 Adding system startup for /etc/init.d/fw1loggrabber ...
   /etc/rc0.d/K20fw1loggrabber -> ../init.d/fw1loggrabber
   /etc/rc1.d/K20fw1loggrabber -> ../init.d/fw1loggrabber
   /etc/rc6.d/K20fw1loggrabber -> ../init.d/fw1loggrabber
   /etc/rc2.d/S20fw1loggrabber -> ../init.d/fw1loggrabber
   /etc/rc3.d/S20fw1loggrabber -> ../init.d/fw1loggrabber
   /etc/rc4.d/S20fw1loggrabber -> ../init.d/fw1loggrabber
   /etc/rc5.d/S20fw1loggrabber -> ../init.d/fw1loggrabber
```after that, i could see...

```

opensourcesim:/var/run# chkconfig --list

fw1loggrabber             0:off  1:off  **[COLOR=Lime]2:on[/COLOR]**   **[COLOR=Lime]3:on   4:on   5:on[/COLOR]**   6:off


```

So does it mean..that my program is running on runlevel 2, 3, 4 and 5?

Another update,
I have restarted my machine and when i type *#ps xa | grep loggrabber* or *#ps xa | grep fw1loggrabber* it shows that fw1/loggrabber is not running automatically.

---

### Post by cipherboy_loc on 2011-03-10
First of all, you need to modify these lines:

```

PROG="pi"
PROG_PATH="/usr/bin"
PROG_ARGS="10000000"

```To suit your needs. I think in your case, you need to change it to:
```

PROG="fw1loggrabber"
PROG_PATH="/usr/bin"
PROG_ARGS=""

```Also, if this is just a simple on/off program that may stop, in my opinion, you do not need a handle to it; starting it should be fine. So yes, the only lines you need to modify are the lines stated above. PROG is the name of the executable (fw1loggrabber in your case), PROG_PATH is the path to the program (the command `which fw1loggrabber` will tell you where it is in most cases), and  PROG_ARGS is what you need to change if you want to give it input (without knowing the program, say you want to pass it the location of a config file, change PROG_ARGS="" to PROG_ARGS="--config=/path/to/config/file").

Cipherboy

---

### Post by opensource10 on 2011-03-11
Hi Cipherboy...

Wait a moment..i need a time to understand [LSBInitScripts]("http://wiki.debian.org/LSBInitScripts")...will get back to you again later ;)

---

### Post by opensource10 on 2011-03-11
Hi Cipherboy,

I have modified little bit my init script code as below...
```
opensourcesim:/install# cat fw1-loggrabber
#! /bin/sh
### BEGIN INIT INFO
# Provides:          fw1-loggrabber
# Required-Start:    $remote_fs
# Required-Stop:     $remote_fs
# Default-Start:     2 3 4 5
# Default-Stop:      0 1 6
# Short-Description: Log grabber for Checkpointfirewall
# Description : Program that capture traffic form the Checkpointfirewall and will send the log to Server management.This file should be used to construct scripts to be placed in /etc/init.d.
### END INIT INFO

PROG="fw1-loggrabber"
PROG_PATH="/usr/bin/fw1-loggrabber/bin/"   ## Not need, but sometimes helpful (if $PROG resides in /opt for example).
PROG_ARGS=""
PID_PATH="/var/run/"

start() {
    if [ -e "$PID_PATH/$PROG.pid" ]; then
        ## Program is running, exit with error.
        echo "Error! $PROG is currently running!" 1>&2
        exit 1
    else
        ## Change from /dev/null to something like /var/log/$PROG if you want to save output.
            $PROG_PATH/$PROG $PROG_ARGS 2>&1 >/dev/null &
        echo "$PROG started"
        touch "$PID_PATH/$PROG.pid"
    fi
}

stop() {
    if [ -e "$PID_PATH/$PROG.pid" ]; then
        ## Program is running, so stop it
        killall $PROG

        rm "$PID_PATH/$PROG.pid"

        echo "$PROG stopped"
    else
        ## Program is not running, exit with error.
        echo "Error! $PROG not started!" 1>&2
        exit 1
    fi
}

## Check to see if we are running as root first.
## Found at http://www.cyberciti.biz/tips/shell-root-user-check-script.html
if [ "$(id -u)" != "0" ]; then
    echo "This script must be run as root" 1>&2
    exit 1
fi

case "$1" in
    start)
        start
        exit 0
    ;;
    stop)
        stop
        exit 0
    ;;
    reload|restart|force-reload)
        stop
        start
        exit 0
    ;;
    **)
        echo "Usage: $0 {start|stop|reload}" 1>&2
        exit 1
    ;;
esac
```and found no error while creating a symbolic link

```

opensourcesim:/etc/init.d# update-rc.d fw1-loggrabber defaults
Adding system startup for /etc/init.d/fw1-loggrabber ...
   /etc/rc0.d/K20fw1-loggrabber -> ../init.d/fw1-loggrabber
   /etc/rc1.d/K20fw1-loggrabber -> ../init.d/fw1-loggrabber
   /etc/rc6.d/K20fw1-loggrabber -> ../init.d/fw1-loggrabber
   /etc/rc2.d/S20fw1-loggrabber -> ../init.d/fw1-loggrabber
   /etc/rc3.d/S20fw1-loggrabber -> ../init.d/fw1-loggrabber
   /etc/rc4.d/S20fw1-loggrabber -> ../init.d/fw1-loggrabber
   /etc/rc5.d/S20fw1-loggrabber -> ../init.d/fw1-loggrabber
```

I have deleted previous fw1loggrabber and left fw1-loggrabber. So, after put loggrabber init script, how do we check whether program start while computer boot up?

Now i restart the machine and will infom you again to check the result. >>> the mention program is not automatically running (-_-!)

---

### Post by cipherboy_loc on 2011-03-11
You could change:

```

$PROG_PATH/$PROG $PROG_ARGS 2>&1 >/dev/null &

```to
```

$PROG_PATH/$PROG $PROG_ARGS 2>&1 >/var/log/$PROG.log &

```And, if you want to, you could do something like from a terminal:

```

ps aux | grep -i '[f]w1-loggrabber'

```

---

### Post by opensource10 on 2011-03-11
I also notice that when i terminate/kill the process, it shows "Terminated" instead of "fw1-loggrabber stopped" and in order to start it again, i have to erase fw1-loggrabber.pid (under *var/run*) manually then do fw1-loggrabber start.
  
```
opensourcesim:/etc/init.d# ./fw1-loggrabber stop
Terminated
```Is there some line to be added/missing?

By the way..this is update of my code

```
opensourcesim:/etc/init.d# cat fw1-loggrabber
#! /bin/sh
### BEGIN INIT INFO
# Provides:          fw1-loggrabber
# Required-Start:    $remote_fs
# Required-Stop:     $remote_fs
# Default-Start:     2 3 4 5
# Default-Stop:      0 1 6
# Short-Description: Log grabber for Checkpointfirewall
# Description : Program that capture traffic form the Checkpointfirewall and will send the log to Server management.This file should be used to construct scripts to be placed in /etc/init.d.
### END INIT INFO

PROG="fw1-loggrabber"
PROG_PATH="/usr/local/fw1-loggrabber/bin"   ## Not need, but sometimes helpful (if $PROG resides in /opt for example).
PROG_ARGS="-c /usr/local/fw1-loggrabber/etc/fw1-loggrabber.conf -l /usr/local/fw1-loggrabber/etc/lea.conf"
PID_PATH="/var/run/"

start() {
    if [ -e "$PID_PATH/$PROG.pid" ]; then
        ## Program is running, exit with error.
        echo "Error! $PROG is currently running!" 1>&2
        exit 1
    else
        ## Change from /dev/null to something like /var/log/$PROG if you want to save output.
            $PROG_PATH/$PROG $PROG_ARGS 2>&1 >/var/log/$PROG.log &
        echo "$PROG started"
        touch "$PID_PATH/$PROG.pid"
    fi
}

stop() {
    if [ -e "$PID_PATH/$PROG.pid" ]; then
        ## Program is running, so stop it
        killall $PROG

        rm "$PID_PATH/$PROG.pid"

        echo "$PROG stopped"
    else
        ## Program is not running, exit with error.
        echo "Error! $PROG not started!" 1>&2
        exit 1
    fi
}

## Check to see if we are running as root first.
## Found at http://www.cyberciti.biz/tips/shell-root-user-check-script.html
if [ "$(id -u)" != "0" ]; then
    echo "This script must be run as root" 1>&2
    exit 1
fi

case "$1" in
    start)
        start
        exit 0
    ;;
    stop)
        stop
        exit 0
    ;;
    reload|restart|force-reload)
        stop
        start
        exit 0
    ;;
    **)
        echo "Usage: $0 {start|stop|reload}" 1>&2
        exit 1
    ;;
esac
opensourcesim:/etc/init.d#
```

---

### Post by cipherboy_loc on 2011-03-11
That's the issue (and generally speaking, why you get the PID)! Name the script something different that the program (say your program is f1-logger or whatever, name it f1logger). You could also do some complicated `ps aux | grep -i 'process name'` stuff and get the PID, write it a file, and then use kill rather than killall, but for the moment, I don't have enough time to write that statement. Maybe later, if no one gets to it before me.


Cipherboy

---

### Post by opensource10 on 2011-03-11
> **cipherboy_loc said:**
> That's the issue (and generally speaking, why you get the PID)! Name the script something different that the program (say your program is f1-logger or whatever, name it f1logger). You could also do some complicated `ps aux | grep -i 'process name'` stuff and get the PID, write it a file, and then use kill rather than killall, but for the moment, I don't have enough time to write that statement. Maybe later, if no one gets to it before me.


Cipherboy

Okay I will rename the script different with the program.

---

### Post by cipherboy_loc on 2011-03-11
Did that work, or should I remake the script to work with kill (PIDs) rather than killall?


Cipherboy

---

### Post by opensource10 on 2011-03-12
> **cipherboy_loc said:**
> Did that work, or should I remake the script to work with kill (PIDs) rather than killall?


Cipherboy

The issue still remain...it wont work once computer boot up...btw can you provide me with the script to work with kill (PID) 

Thanks in advance and have a nice weekend

---

### Post by cipherboy_loc on 2011-03-12
```

#!/bin/bash

## Fill in name of program here.
PROG="pi"
PROG_PATH="/usr/bin" ## Not need, but sometimes helpful (if $PROG resides in /opt for example).
PROG_ARGS="10000000" 
PID_PATH="/var/run/"

start() {
    if [ -e "$PID_PATH/$PROG.pid" ]; then
        ## Program is running, exit with error.
        echo "Error! $PROG is currently running!" 1>&2
        exit 1
    else
        ## Change from /dev/null to something like /var/log/$PROG if you want to save output.
            $PROG_PATH/$PROG $PROG_ARGS 2>&1 >/dev/null &
        pid=`ps ax | grep -i 'pi 10000000$'| sed 's/^\([0-9]\{1,\}\).*/\1/g' | head -n 1`
        echo "$PROG started ($pid)"
        echo $pid > "$PID_PATH/$PROG.pid"
    fi
}

stop() {
    if [ -e "$PID_PATH/$PROG.pid" ]; then
        ## Program is running, so stop it
        pid=`cat $PID_PATH/$PROG.pid`
        kill $pid

        rm "$PID_PATH/$PROG.pid"
        
        echo "$PROG stopped ($pid)"
    else
        ## Program is not running, exit with error.
        echo "Error! $PROG not started!" 1>&2
        exit 1
    fi
}

## Check to see if we are running as root first.
## Found at http://www.cyberciti.biz/tips/shell-root-user-check-script.html
if [ "$(id -u)" != "0" ]; then
    echo "This script must be run as root" 1>&2
    exit 1
fi

case "$1" in
    start)
        start
        exit 0
    ;;
    stop)
        stop
        exit 0
    ;;
    reload|restart|force-reload)
        stop
        start
        exit 0
    ;;
    **)
        echo "Usage: $0 {start|stop|reload}" 1>&2
        exit 1
    ;;
esac



```


That should work now, but make sure you fix the stuff at the top (PATH, etc). Oh, and add in the LSB information. I didn't add that back in to this one. 



Cipherboy

---

### Post by opensource10 on 2011-03-14
Dear Cipherboy...

Thank you very much for the tutorial and help so far. I will check again using the latest code. :P

---

### Post by tobiz on 2012-06-07
Is the line:
"pid=`ps ax | grep -i 'pi 10000000$'| sed 's/^\([0-9]\{1,\}\).*/\1/g' | head -n 1`"
correct?  should 'pi' be replaced by PROG?, eg something like:
"pid=`ps ax | grep -i '$PROG 10000000$'| sed 's/^\([0-9]\{1,\}\).*/\1/g' | head -n 1`"

---

### Post by oldos2er on 2012-06-07
Old thread closed.

---

