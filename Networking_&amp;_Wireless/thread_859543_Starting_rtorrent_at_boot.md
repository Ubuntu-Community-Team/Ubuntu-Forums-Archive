---
title: "Starting rtorrent at boot"
date: 2008-07-14
forum: Networking &amp; Wireless
---

### Post by ranger0293 on 2008-07-14
I'm trying to add an rtorrent script to /etc/init.d, but it's not able to start up an rtorrent instance.

Here is the script in /etc/init.d which I got from the rtorrent site:
```
#!/bin/bash
#############
###<Notes>###
#############
# This script depends on screen.
# For the stop function to work, you must set an
# explicit session directory using absolute paths (no, ~ is not absolute) in your rtorrent.rc.
# If you typically just start rtorrent with just "rtorrent" on the
# command line, all you need to change is the "user" option.
# Attach to the screen session as your user with 
# "screen -dr rtorrent". Change "rtorrent" with srnname option.
# Licensed under the GPLv2 by lostnihilist: lostnihilist _at_ gmail _dot_ com
##############
###</Notes>###
##############

#######################
##Start Configuration##
#######################
# You can specify your configuration in a different file 
# (so that it is saved with upgrades, saved in your home directory,
# or whatever reason you want to)
# by commenting out/deleting the configuration lines and placing them
# in a text file (say /home/user/.rtorrent.init.conf) exactly as you would
# have written them here (you can leave the comments if you desire
# and then uncommenting the following line correcting the path/filename 
# for the one you used. note the space after the ".".
# . /etc/rtorrent.init.conf


#Do not put a space on either side of the equal signs e.g.
# user = user 
# will not work
# system user to run as (can only use one)
user="jeff"

# system user to run as # not implemented, see d_start for beginning implementation
# group=$(id -ng "$user")

# the full path to the filename where you store your rtorrent configuration
# must keep parentheses around the entire statement, quotations around each config file
#config=("$(su -c 'echo $HOME' $user)/.rtorrent.rc")
# Examples:
config=("/home/jeff/.rtorrent.rc")
# config=("/home/user/.rtorrent.rc" "/mnt/some/drive/.rtorrent2.rc")
# config=("/home/user/.rtorrent.rc"
# "/mnt/some/drive/.rtorrent2.rc"
# "/mnt/another/drive/.rtorrent3.rc")

# set of options to run with each instance, separated by a new line
# must keep parentheses around the entire statement
#if no special options, specify with: ""
options=("")
# Examples:
# starts one instance, sourcing both .rtorrent.rc and .rtorrent2.rc
# options=("-o import=~/.rtorrent2.rc")
# starts two instances, ignoring .rtorrent.rc for both, and using
# .rtorrent2.rc for the first, and .rtorrent3.rc for the second
# we do not check for valid options
# options=("-n -o import=~/.rtorrent2.rc" "-n -o import=~/rtorrent3.rc")

# default directory for screen, needs to be an absolute path
base=$(su -c 'echo $HOME' $user)

# name of screen session
srnname="rtorrent"

# file to log to (makes for easier debugging if something goes wrong)
logfile="/var/log/rtorrentInit.log"
#######################
###END CONFIGURATION###
#######################

PATH=/usr/bin:/usr/local/bin:/usr/local/sbin:/sbin:/bin:/usr/sbin
DESC="rtorrent"
NAME=rtorrent
DAEMON=$NAME
SCRIPTNAME=/etc/init.d/$NAME

checkcnfg() {
  exists=0
  for i in `echo "$PATH" | tr ':' '\n'` ; do
    if [ -f $i/$NAME ] ; then
      exists=1
      break
    fi
  done
  if [ $exists -eq 0 ] ; then
    echo "cannot find $NAME binary in PATH: $PATH" | tee -a "$logfile" >&2
    exit 3
  fi
  for (( i=0 ; i < ${#config[@]} ;  i++ )) ; do
    if ! [ -r "${config[i]}" ] ; then
        echo "cannot find readable config ${config[i]}. check that it is there and permissions are appropriate"  | tee -a "$logfile" >&2
        exit 3
    fi
    session=$(getsession "${config[i]}")
    if ! [ -d "${session}" ] ; then
        echo "cannot find readable session directory ${session} from config ${config[i]}. check permissions" | tee -a "$logfile" >&2
        exit 3
    fi
  done
}

d_start() {
  [ -d "${base}" ] && cd "${base}"
  stty stop undef && stty start undef
  #su -c "screen -S "${srnname}" -X screen rtorrent ${options} 2>&1 1>/dev/null" ${user} | tee -a "$logfile" >&2
  su -c "screen -S "${srnname}" -X screen rtorrent ${options} " ${user} | tee -a "$logfile" >&2
  # this works for the screen command, but starting rtorrent below adopts screen session gid
  # even if it is not the screen session we started (e.g. running under an undesirable gid
  #su -c "screen -ls | grep -sq "\.${srnname}[[:space:]]" " ${user} || su -c "sg \"$group\" -c \"screen -fn -dm -S ${srnname} 2>&1 1>/dev/null\"" ${user} | tee -a "$logfile" >&2
  for (( i=0 ; i < ${#options[@]} ; i++ )) ;  do
    sleep 3
    #su -c "screen -S "${srnname}" -X screen rtorrent ${options[i]} 2>&1 1>/dev/null" ${user} | tee -a "$logfile" >&2
    su -c "screen -S "${srnname}" -X screen rtorrent ${options[i]} " ${user} | tee -a "$logfile" >&2
  done
}

d_stop() {
  for (( i=0 ; i < ${#config[@]} ; i++ )) ; do
    session=$(getsession "${config[i]}")
    if ! [ -s ${session}/rtorrent.lock ] ; then
        return
    fi
    pid=$(cat ${session}/rtorrent.lock | awk -F: '{print($2)}' | sed "s/[^0-9]//g")
    # make sure the pid doesn't belong to another process
    if ps -A | grep -sq ${pid}.*rtorrent ; then
        kill -s INT ${pid}
    fi
  done
}

getsession() { 
    session=$(cat "$1" | grep "^[[:space:]]*session[[:space:]]*=" | sed "s/^[[:space:]]*session[[:space:]]*=[[:space:]]*//" )
    #session=${session/#~/`getent passwd ${user}|cut -d: -f6`}
    echo $session
}

checkcnfg

case "$1" in
  start)
    echo -n "Starting $DESC: $NAME"
    d_start
    echo "."
    ;;
  stop)
    echo -n "Stopping $DESC: $NAME"
    d_stop
    echo "."
    ;;
  restart|force-reload)
    echo -n "Restarting $DESC: $NAME"
    d_stop
    sleep 1
    d_start
    echo "."
    ;;
  *)
    echo "Usage: $SCRIPTNAME {start|stop|restart|force-reload}" >&2
    exit 1
    ;;
esac

exit 0
```

As you can I see, I removed the redirection of output and errors in the actual 'screen' commands to try and better debug it.  When I run it from the command line I get this:
```
jeff@lamp:/etc/init.d$ sudo /etc/init.d/rtorrent start
Starting rtorrent: rtorrentNo screen session found.
No screen session found.
.
jeff@lamp:/etc/init.d$ 
```

It seems like it's an issue with the screen command more than with rtorrent, but I don't know what "No screen session found" means.

I'd appreciate any help.

---

### Post by chalewa on 2008-07-14
why not just add ```
screen rtorrent 
```to your system startup programs?

---

### Post by ranger0293 on 2008-07-14
> **chalewa said:**
> why not just add ```
screen rtorrent 
```to your system startup programs?

Thanks for the suggestion, but that doesn't seem to be possible either:

```
jeff@lamp:~$ screen rtorrent
[screen is terminating]
jeff@lamp:~$ sudo screen rtorrent
[sudo] password for jeff: 
[screen is terminating]
jeff@lamp:~$
```

---

### Post by ranger0293 on 2008-07-14
Is there a more appropriate forum to ask this question in?

---

### Post by chalewa on 2008-07-15
hm 
```

screen rtorrent 
```works for me

maybe try

```
screen && rtorrent
```

---

### Post by fuzZzball on 2009-10-30
I know this thread is old, but this is one of many solutions, using start-stop-daemon.

Here *ranger0293* is using screen, I suggest using dtach, it has less overhead than screen.

So, install dtach
```
sudo apt-get install dtach
```

I have several users, one user with less permission is 'pacman', just use your desired user instead.

Using start-stop-daemon is not so hard, but setting the permission right for rtorrent is, to first check if the command is accepted, set permissions on your rtorrent's download and session folder to 0777 (or a+rwx). Here I assume you have configured your .rtorrent.rc file correctly.

Now don't fool around in the /etc/init.d/rtorrent, just add the following line to your /etc/rc.local file (inbetween the comments and exit 0 lines).
```
start-stop-daemon --start --chuid pacman --name rtorrent --exec /usr/bin/dtach -- -n /tmp/rtorrent.dtach /usr/bin/rtorrent
```

Either Reboot or type in a terminal
```
sudo /etc/rc.local
```

then type in a terminal
```
ps -ef | grep rtorrent
```

It should display something like
```
pacman    4783     1  0 18:03 ?        00:00:00 /usr/bin/dtach -n /tmp/rtorrent.dtach /usr/bin/rtorrent
pacman    4784  4783  0 18:03 pts/0    00:00:02 /usr/bin/rtorrent
pacman    4838  4820  0 18:03 pts/2    00:00:00 dtach -a /tmp/rtorrent.dtach
1002      4853  4799  0 18:18 pts/1    00:00:00 grep rtorrent

```

To attach the rtorrent screen, open a **new** terminal and type
```
dtach -a /tmp/rtorrent.dtach
```

If everything worked fine, you can see the rtorrent screen, and ofcourse, see what happens, close the terminal when you've seen enough (or use CTRL+Z to close dtach, it just closes, does not quite!), you can repeat this action to observe the torrents.

Oh, if it works, don't forget to set permissions to 0755 or less, or whatever you want it to be.

Cheers,
f

---

### Post by sentryab on 2011-02-07
Great post FuzZzball. I couldn't get the regular way to do it to work, it kept saying command not found, but this works perfectly.

I'm not really sure how screen or dtach works, but this did open my eyes a little more to how managing a nix server works, cool stuff.

One question, since screen has more overhead than dtach, is it safe to remove screen from the system entirely? Or is dtach dependent on it?

Really happy to be finally running rtorrent as a daemon :)

---

### Post by Pithikos on 2011-10-20
Did everything as you said but it doesn't work. I even tryied running the command explicitly:

```
sudo start-stop-daemon --start --chuid manos --name rtorrent --exec /usr/bin/dtach -- -n /tmp/rtorrent.dtach /usr/bin/rtorrent
```

But if I ps aux I don't get anything and my /tmp remains empty :/

---

