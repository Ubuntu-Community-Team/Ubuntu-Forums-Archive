---
title: "sudo command problem"
date: 2009-07-12
forum: New to Ubuntu
---

### Post by mrgreaper on 2009-07-12
Ok sudo wrks fine in terminal but needs my password,
Now on ubuntu boot up I have several custom apps all working fine but I need to execute the following "sudo mediatomb -d" but can't figure out were the password goes in a command I have tried sudo -u root -p pass and sudo -user root -pass pass and root:pass sudo I also need to use sudo in some scripts I plan to make its driving me nuts that my own computer will not allow me to run certain commands with out me typing a password

---

### Post by earthpigg on 2009-07-12
> **mrgreaper said:**
> its driving me nuts that my own computer will not allow me to run certain commands with out me typing a password

there are a zillion great reasons why ubuntu is set up the way it is.

but, if you want a root shell that will never ask you for your password and thus _***[SIZE="4"]can wipe your system if you make a single typo[/SIZE]***_:

```
sudo su
```

you can run scripts from there, etc, it will never ask for your password.

_***[SIZE="4"]i want to emphasise again that a single typo in a root shell can do irreversible damage to your system, including to Windows, including to thumb drives plugged in, including to your very soul itself.[/SIZE]***_


don't say i didn't warn you, when Saint Peter refuses you entry to heaven.

---

### Post by mrgreaper on 2009-07-12
I will try it when I get home, so if I have the context correct the command I tell the computer to run at boot up is "sudo su mediatomb -d"? I understand the warnings but some commands I need to work automaticly with out me at the terminal specialy when it will be a headless box lol

---

### Post by earthpigg on 2009-07-12
nah, just

> sudo su

to open the root shell. and then you can omit 'sudo' from everything thereafter in that root shell. instead of 'sudo apt-get install bla bla bla' you just put 'apt-get install bla bla bla'

you get a visual indication that you are in a root shell:

```
ep@ep-9:~$ sudo su
[sudo] password for ep: 
root@ep-9:/home/ep# 
```

the # instead of the $ you normally see is your reminder that you are in omgwtfhax godmode.

---

### Post by mrgreaper on 2009-07-12
I'm not sure that's what I'm after, I need a way to do aa command as root with out being at the pc I need it so once its all configured I can remove the monitier and just vnc in on rare occasions

---

### Post by wojox on 2009-07-12
What is it exactly your trying to do?

---

### Post by mrgreaper on 2009-07-12
> **wojox said:**
> What is it exactly your trying to do?

to start off with 
in startup apps have the command "sudo mediatomb -d" run 
this will load mediatomb in daemon mode as the root user

if i type it into a terminal it asks for my password then loads up (upon correct password) i need to somehow do the above command but pass the password onto the command so that it will do it with out my intervention, its the last app i have that refuses to play nice 


then armed with how to run things as root in command form with out me needing to use the password i can make a few auto scripts to help out some tasks i perform

as i say i have tried the usual user=root u=root u:root user:root and with the same with passwords , i wish linux was as easy to use as windows but then its free so i have to accept theres limitations, is this one of them ?

---

### Post by ibuclaw on 2009-07-12
> **mrgreaper said:**
> to start off with 
in startup apps have the command "sudo mediatomb -d" run 
this will load mediatomb in daemon mode as the root user

if i type it into a terminal it asks for my password then loads up (upon correct password) i need to somehow do the above command but pass the password onto the command so that it will do it with out my intervention, its the last app i have that refuses to play nice 


then armed with how to run things as root in command form with out me needing to use the password i can make a few auto scripts to help out some tasks i perform

as i say i have tried the usual user=root u=root u:root user:root and with the same with passwords , i wish linux was as easy to use as windows but then its free so i have to accept theres limitations, is this one of them ?

Remove mediatomb from your startup apps, you are going about it the wrong way. ;)


Firstly, you can install the daemon package so it starts up every time you boot your computer.
```
sudo apt-get install mediatomb-daemon
```

Secondly, if you cannot install the daemon package for whatever reason, you can still add it to the startup scripts so that it loads everytime you boot your computer.
```
gksudo gedit /etc/rc.local
```

And put in before the '**exit 0**' line:
```
/usr/bin/mediatomb -d &
```

Regards
Iain

---

### Post by earthpigg on 2009-07-12
disregard

---

### Post by mrgreaper on 2009-07-13
the thing is it took me ages to get mediatomb all set up (including customizing the import scripts so things are oganised in proper lists not just one giant list)

if from terminal i type sudo mediatomb -d then it loads exactly as i need it, i just need a way of doing that command on bootup with out my input if that makes sense, it has to be run as root to use the settings i have on it  

there must be some way to run sudo cammnd with out it asking my password?

---

### Post by ibuclaw on 2009-07-13
> **mrgreaper said:**
> if from terminal i type sudo mediatomb -d then it loads exactly as i need it, i just need a way of doing that command on bootup with out my input if that makes sense, it has to be run as root to use the settings i have on it

Have you tried it using my method then? That will run mediatomb as root.
> 
there must be some way to run sudo cammnd with out it asking my password?

Yes, and you can read about it in my tutorial [here]("http://ubuntuforums.org/showthread.php?t=1132821"), but I am waiting for confirmation from my first fix. :)

Unless you require a special environmental variable from your user account, there is no reason why putting "/usr/bin mediatomb -d" in /etc/rc.local won't work and you can load mediatomb **without** the need of sudo.

Regards
Iain

---

### Post by mrgreaper on 2009-07-13
> **tinivole said:**
> Have you tried it using my method then? That will run mediatomb as root.


Yes, and you can read about it in my tutorial [here]("http://ubuntuforums.org/showthread.php?t=1132821"), but I am waiting for confirmation from my first fix. :)

Unless you require a special environmental variable from your user account, there is no reason why putting "/usr/bin mediatomb -d" in /etc/rc.local won't work and you can load mediatomb **without** the need of sudo.

Regards
Iain


```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.
/usr/bin/mediatomb -d &
exit 0
```

didnt work, mediatomb didnt load up i checked the logs and mediatomb was unable to access the sqlite database located in my users home folder 

now if in terminal i type mediatomb and hit enter i get the same error but if i type sudo mediatomb it loads fine so it looks like rc.local is not loading it as root but as my user

will read through the tutorial you linked to in a minute and see if that helps

the replys guys, despite them not working, are appreciated


edit,

i will have to read the tutorial at work, it looks very informative but i only have 2 hours before i go and need to eat but i get a lot of time at work so i will take it all in then, plus the server is now picking and converting media for me to watch at work so cant be rebooted again till an hour and half from now lol

---

### Post by Keith Hedger on 2009-07-13
```

echo YOURPASSWORD|sudo -S somecommand
```

the -S switch tells sudo to get the password from stdin rather than asking for it.

---

### Post by rustutzman on 2009-07-13
You should not run Mediatomb as root. Is there a reason you want to?? The Mediatomb forums have covered topic a few times. You might want to look around there.

Russ

---

### Post by mrgreaper on 2009-07-13
> **rustutzman said:**
> You should not run Mediatomb as root. Is there a reason you want to?? The Mediatomb forums have covered topic a few times. You might want to look around there.

Russ

As I say if I run it as a normal user it errors if I run it as root it works. The server pc is used by me alone it connects to the net through a rooter but media tomb is setup so only lan can acess it, I respect that root access can cause my computer to rash if I do the. Wrong thing. But surely its mychoice to use ubuntu how I want? Now mediatomb works as root and doesn't as me so I want to use it as root 

I will try the other command when I get home

---

### Post by TheForumTroll on 2009-07-13
Sure you can do whatever you want with your own PC but you can't force people to give bad advice.

---

### Post by AndyCee on 2009-09-06
If I simply run:

```
sudo apt-get install mediatomb
```

[LIST]
[*]I have a startup script in /etc/init.d and /etc/rc4.d for mediatomb
[*]Typing "nmap localhost" shows port 49152 open
[*]Typing "ps -A | grep mediatomb" shows the mediatomb daemon is running
[*]Going to the relevant web address in a browser shows the mediatomb UI
[/LIST]

It's quite possible I've done something and forgotten about it. I don't even seem to have to run the "mediatomb -d" command.

Here is the output of the startup script which appeared - 
```

#! /bin/sh
#
# MediaTomb initscript
#
# Original Author: Tor Krill <tor@excito.com>.
# Modified by:     Leonhard Wimmer <leo@mediatomb.cc>
# Modified again by Andres Mejia <mcitadel@gmail.com> to
# base it off of /etc/init.d/skeleton
#
#

### BEGIN INIT INFO
# Provides:          mediatomb
# Required-Start:    $all
# Required-Stop:     $all
# Should-Start:      $all
# Should-Stop:       $all
# Default-Start:     2 3 4 5
# Default-Stop:      0 1 6
# Short-Description: upnp media server
### END INIT INFO

# Do NOT "set -e"

# PATH should only include /usr/* if it runs after the mountnfs.sh script
PATH=/usr/sbin:/usr/bin:/sbin:/bin
DESC="upnp media server"
NAME=mediatomb
DAEMON=/usr/bin/$NAME
PIDFILE=/var/run/$NAME.pid
LOGFILE=/var/log/$NAME.log
SCRIPTNAME=/etc/init.d/$NAME
DEFAULT=/etc/default/$NAME

# Exit if the package is not installed
[ -x "$DAEMON" ] || exit 0

# Read configuration variable file if it is present
[ -r $DEFAULT ] && . $DEFAULT

# Load the VERBOSE setting and other rcS variables
[ -f /etc/default/rcS ] && . /etc/default/rcS

# Define LSB log_* functions.
# Depend on lsb-base (>= 3.0-6) to ensure that this file is present.
. /lib/lsb/init-functions

# Start the daemon if NO_START is disabled in DEFAULT
if [ "$NO_START" = "yes" ]; then
	test "$1" = "start" && \
	{
		log_warning_msg "$NAME: Not starting $DESC."
		log_warning_msg "$NAME: Disabled in $DEFAULT."
	}
	exit 0
fi

# Run as root if USER not specified
if [ ! $USER ]; then
	USER=root
fi

# Check for an invalid user or one without a home directory
eval USERHOME=~$USER
if [ "${USERHOME#/}" = "${USERHOME}" ]; then
	log_failure_msg "$NAME: The user '$USER' specified in $DEFAULT is invalid."
	exit 1
fi

# Check if group is not specified and assign a proper group
if [ -z $GROUP ]; then
    GROUP="$USER"
fi

if [ "$INTERFACE" != "" ] ; then
    INTERFACE_ARG="-e $INTERFACE"
else
    INTERFACE_ARG=""
fi

DAEMON_ARGS="-c /etc/mediatomb/config.xml -d -u $USER -g $GROUP -P $PIDFILE -l $LOGFILE $INTERFACE_ARG $OPTIONS"

#
#       Function that starts the daemon/service.
#
do_start() {
	# Return
	#   0 if daemon has been started
	#   1 if daemon was already running
	#   2 if daemon could not be started
	touch $PIDFILE
	chown $USER:$GROUP $PIDFILE
	touch $LOGFILE
	chown $USER:$GROUP $LOGFILE
	start-stop-daemon --start --quiet --pidfile $PIDFILE --exec $DAEMON \
		--test > /dev/null \
		|| return 1
	start-stop-daemon --start --quiet --pidfile $PIDFILE --exec $DAEMON -- \
		$DAEMON_ARGS \
		|| return 2
}

#
#       Function that stops the daemon/service.
#
do_stop() {
	# Return
	#   0 if daemon has been stopped
	#   1 if daemon was already stopped
	#   2 if daemon could not be stopped
	#   other if a failure occurred
	start-stop-daemon --stop --quiet --retry=TERM/30/KILL/5 --pidfile $PIDFILE --name $NAME
	RETVAL="$?"
	[ "$RETVAL" = 2 ] && return 2
	rm -f $PIDFILE
	return "$RETVAL"
}

#
#       Function that sends a SIGHUP to the daemon/service.
#
do_reload() {
	start-stop-daemon --stop --signal 1 --quiet --pidfile $PIDFILE --name $NAME
	return 0
}

case "$1" in
  start)
	if [ -n "$INTERFACE" ]; then
		# try to add the multicast route
		if [ "$VERBOSE" != no ]; then
			{
				log_action_begin_msg \
				"$NAME: Trying to add the multicast route"
				$ROUTE_ADD $INTERFACE \
				&& log_action_end_msg 0
			} || {
				true && \
				log_warning_msg "Failed to add multicast route. skipping."
			}
		else
			$ROUTE_ADD $INTERFACE >/dev/null 2>&1 || true
		fi
	fi
	log_daemon_msg "Starting $DESC" "$NAME"
	do_start
	case "$?" in
		0) log_end_msg 0 ;;
		1) log_warning_msg "$DESC" "'$NAME'" "was already started" ;;
		2) log_end_msg 1 ;;
	esac
	;;
  stop)
	log_daemon_msg "Stopping $DESC" "$NAME"
	do_stop
	case "$?" in
		0)
			log_end_msg 0
			if [ -n "$INTERFACE" ]; then
				# try to add the multicast route
				if [ "$VERBOSE" != no ]; then
				{
					log_action_begin_msg \
					"$NAME: Trying to delete the multicast route"
					$ROUTE_DEL $INTERFACE \
					&& log_action_end_msg 0
				} || {
					true && \
					log_warning_msg \
					"Failed to delete multicast route. skipping."
				}
				else
					$ROUTE_DEL $INTERFACE >/dev/null 2>&1 || true
				fi
			fi
			;;
		1) log_warning_msg "$DESC" "'$NAME'" "was already stopped" ;;
		2) log_end_msg 1 ;;
	esac
	;;
  reload|force-reload)
	log_daemon_msg "Reloading $DESC" "$NAME"
	do_reload
	log_end_msg $?
  	;;
  restart)
        #
        #       If the "reload" option is implemented, move the "force-reload"
        #       option to the "reload" entry above. If not, "force-reload" is
        #       just the same as "restart".
        #
	log_daemon_msg "Restarting $DESC" "$NAME"
	do_stop
	case "$?" in
	  0|1)
		sleep 1
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

```

Upon inspection this seems to run as root, which is interesting.

---

