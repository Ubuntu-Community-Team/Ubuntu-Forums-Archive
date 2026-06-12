---
title: "[Lubuntu 13.10] x11vnc and UltraVNC"
date: 2014-03-22
forum: Networking &amp; Wireless
---

### Post by balubeto on 2014-03-22
Hi

In Windows 7 SP1 64-bit, I use UltraVNC viewer 1.1.9.6 64-bit with the SecureVNCPlugin64.dsm plugin.

Now, I have a computer with Lubuntu 13.10 32 bit that it has installed the x11vnc server.

How can I configure the VNC server so that I can remotely control this Linux machine completely, including its Display Manager LightDM?

Thanks

Bye

---

### Post by balubeto on 2014-03-25
Hi

From Linux, I wrote from the terminal: 

> 
sudo x11vnc -storepasswd /etc/x11vnc.pass


and then I created in the /etc/init directory the x11vnc.conf file and I wrote: 

> 
start on login-session-start
script
/usr/bin/x11vnc -xkb -auth /var/run/lightdm/root/:0 -noxrecord -noxfixes -noxdamage -rfbauth /etc/x11vnc.pass -forever -bg -rfbport 5900 -o /var/log/x11vnc.log
end script


but when I restarted the computer, I tried to connect with UltraVNC without the SecureVNCPlugin64.dsm plugin but the x11vnc server does not respond and it does not even create the log file. Where am I wrong?

Thanks

Bye

---

### Post by balubeto on 2014-03-25
Running this command from the terminal with the sudo command because there is the -o option, I get:

> 
25/03/2014 18:30:24 passing arg to libvncserver: -rfbauth
25/03/2014 18:30:24 passing arg to libvncserver: /etc/x11vnc.pass
25/03/2014 18:30:24 passing arg to libvncserver: -rfbport
25/03/2014 18:30:24 passing arg to libvncserver: 5900
25/03/2014 18:30:24 x11vnc version: 0.9.13 lastmod: 2011-08-10  pid: 2733
No protocol specified
25/03/2014 18:30:24 XOpenDisplay(":0") failed.
25/03/2014 18:30:24 Trying again with XAUTHLOCALHOSTNAME=localhost ...
No protocol specified
25/03/2014 18:30:24 ***************************************
25/03/2014 18:30:24 *** XOpenDisplay failed (:0)
*** x11vnc was unable to open the X DISPLAY: ":0", it cannot continue.
*** There may be "Xlib:" error messages above with details about the failure.
Some tips and guidelines:
** An X server (the one you wish to view) must be running before x11vnc is
   started: x11vnc does not start the X server.  (however, see the -create
   option if that is what you really want).
** You must use -display <disp>, -OR- set and export your $DISPLAY
   environment variable to refer to the display of the desired X server.
 - Usually the display is simply ":0" (in fact x11vnc uses this if you forget
   to specify it), but in some multi-user situations it could be ":1", ":2",
   or even ":137".  Ask your administrator or a guru if you are having
   difficulty determining what your X DISPLAY is.
** Next, you need to have sufficient permissions (Xauthority) 
   to connect to the X DISPLAY.   Here are some Tips:
 - Often, you just need to run x11vnc as the user logged into the X session.
   So make sure to be that user when you type x11vnc.
 - Being root is usually not enough because the incorrect MIT-MAGIC-COOKIE
   file may be accessed.  The cookie file contains the secret key that
   allows x11vnc to connect to the desired X DISPLAY.
 - You can explicitly indicate which MIT-MAGIC-COOKIE file should be used
   by the -auth option, e.g.:
       x11vnc -auth /home/someuser/.Xauthority -display :0
       x11vnc -auth /tmp/.gdmzndVlR -display :0
   you must have read permission for the auth file.
   See also '-auth guess' and '-findauth' discussed below.
** If NO ONE is logged into an X session yet, but there is a greeter login
   program like "gdm", "kdm", "xdm", or "dtlogin" running, you will need
   to find and use the raw display manager MIT-MAGIC-COOKIE file.
   Some examples for various display managers:
     gdm:     -auth /var/gdm/:0.Xauth
              -auth /var/lib/gdm/:0.Xauth
     kdm:     -auth /var/lib/kdm/A:0-crWk72
              -auth /var/run/xauth/A:0-crWk72
     xdm:     -auth /var/lib/xdm/authdir/authfiles/A:0-XQvaJk
     dtlogin: -auth /var/dt/A:0-UgaaXa
   Sometimes the command "ps wwwwaux | grep auth" can reveal the file location.
   Starting with x11vnc 0.9.9 you can have it try to guess by using:
              -auth guess
   (see also the x11vnc -findauth option.)
   Only root will have read permission for the file, and so x11vnc must be run
   as root (or copy it).  The random characters in the filenames will of course
   change and the directory the cookie file resides in is system dependent.
See also: [http://www.karlrunge.com/x11vnc/faq.html](http://www.karlrunge.com/x11vnc/faq.html)


So, how do I fix this?

Thanks

Bye

---

### Post by steeldriver on 2014-03-25
Have you checked that x11vnc is getting started and is listening on 5900?

```

ps -ef | grep [x]11vnc

sudo netstat -nlp | grep vnc

```

---

### Post by balubeto on 2014-03-26
> **steeldriver said:**
> Have you checked that x11vnc is getting started and is listening on 5900?

```

ps -ef | grep [x]11vnc

sudo netstat -nlp | grep vnc

```

Leaving the /etc/init/x11vnc.conf file and restarting the computer, I notice that the /var/run/lightdm/root/:0 file is created, but when I run the command **sudo netstat -anp | grep 5900 ** or **sudo netstat -nlp | grep vnc ** or **sudo ps -ef | grep [x]11vnc **, nothing is displayed.
So, I run from the terminal the command **sudo /usr/bin/x11vnc -xkb -auth /var/run/lightdm/root/:0 -noxrecord -noxfixes -noxdamage -rfbauth /etc/x11vnc.pass -forever -rfbport 5900 -bg -o /var/log/x11vnc.log**, the file /var/run/lightdm/root/:0 is created but the other commands always give the same result.

So, I rebooted the computer and gave the command ** sudo /usr/bin/x11vnc -auth /var/run/lightdm/root/:0 -display :0 ** but the same log file is displayed.

How come?

Thanks

Bye

---

### Post by steeldriver on 2014-03-26
> **balubeto said:**
> So, I rebooted the computer and gave the command ** sudo /usr/bin/x11vnc -auth /var/run/lightdm/root/:0 -display :0 ** but the same log file is displayed.

How come?

x11vnc is a *desktop sharing* server - it needs a running X server to connect to. Normally it's run from a user session (**without** sudo and **without** root X authority) and connects to the invoking user's display - afaik you only need the **-auth /var/run/lightdm/root/:0**  when you're invoking it before login (as when using upstart, as you are  trying to do) - that's probably what it doesn't like when being run  from a user session - drop that part and the sudo

---

### Post by balubeto on 2014-03-27
Also, I tried to do this method:
I activated the xauth_path directive in the /etc/lxdm/default.conf (pointing to the /etc/alternatives/lxdm.conf), I run the command **sudo x11vnc -storepasswd <Password> /etc/x11vnc.pass ** to create a password for access remotely to x11vnc and I created the /etc/lxdm/LoginReady like this:
> 
/bin/sh
#X11vnc AutoStart
sudo x11vnc -auth /tmp/.Xauth1000 -forever rfbauth /etc/x11vnc.pass -rfbport 5900 -o /var/log/x11vnc.log

Then I made &#8203;&#8203;it executable by writing **sudo chmod u+x /etc/lxdm/LoginReady ** and I restarted the computer.
Unfortunately I still can not connect from remote because when I try to do it, UltraVNC viewer can not find the Server.
Also, I noticed that the log file is not created and the process x11vnc is not active.
So, how should I do to fix this?
Thanks
Bye
PS: I noticed that even if I run the command **sudo x11vnc -auth /tmp/.Xauth1000 -forever -rfbauth /etc/x11vnc.pass -rfbport 5900 -o /var/log/x11vnc.log ** does not work but the log file is created but it is always the same.

---

### Post by steeldriver on 2014-03-27
If you're using lxdm (not lightdm) then I'm not sure that the upstart method will work for you

I suggest you take things 1 step at a time:

1. start x11vnc as your regular user after logging in normally - something like 

```
x11vnc -o ~/x11vnc.log -rfbauth /etc/x11vnc.pass -rfbport 5900 -shared -forever -nowf -norc -notruecolor -bg -xkb
```

You can add the *-localhost* flag if you want to jump straight to secure SSH tunnelling but if both machines are behind a router / firewall I'd suggest getting it working without tunnelling (and without the UltraVNC SecureVNCPlugin64) FIRST

2. check that the server is listening using netstat or lsof
```
sudo netstat -nlp | grep :5900
```
```
sudo lsof -i :5900
```


Post back when you get to that point and we'll review next steps

---

### Post by balubeto on 2014-03-27
> **steeldriver said:**
> If you're using lxdm (not lightdm) then I'm not sure that the upstart method will work for you

I suggest you take things 1 step at a time:

1. start x11vnc as your regular user after logging in normally - something like 

```
x11vnc -o ~/x11vnc.log -rfbauth /etc/x11vnc.pass -rfbport 5900 -shared -forever -nowf -norc -notruecolor -bg -xkb
```

You can add the *-localhost* flag if you want to jump straight to secure SSH tunnelling but if both machines are behind a router / firewall I'd suggest getting it working without tunnelling (and without the UltraVNC SecureVNCPlugin64) FIRST

2. check that the server is listening using netstat or lsof
```
sudo netstat -nlp | grep :5900
```
```
sudo lsof -i :5900
```


Post back when you get to that point and we'll review next steps

With this command prefixed with sudo:
```

sudo x11vnc -o ~/x11vnc.log -rfbauth /etc/x11vnc.pass -rfbport 5900 -shared -forever -nowf -norc -notruecolor -bg -xkb

```

I can, with UltraVNC, to make the remote control of the current session of Lubuntu 13.10. How come? So, to be able to control even LightDM, how should I do to get the file that the auth option of x11vnc want? Where should I put this command?

Thanks

Bye

---

### Post by steeldriver on 2014-03-27
Are you using lightdm or lxdm as the display manager?

FYI that command shouldn't need sudo because it should be connecting with  the X server / display associated with your own user's desktop session

---

### Post by balubeto on 2014-03-27
> **steeldriver said:**
> Are you using lightdm or lxdm as the display manager?

FYI that command shouldn't need sudo because it should be connecting with  the X server / display associated with your own user's desktop session

I use LightDM. 

I use LightDM. 

I noticed that if I run that command without sudo, it does not work because when I connect with UltraVNC, I can not do Login, because I get a password error.

Thanks

Bye

---

### Post by balubeto on 2014-03-30
I tried to edit the file /etc/lightdm/lightdm.conf in this way:

```

[SeatDefaults]
greeter-session=lightdm-gtk-greeter
user-session=Lubuntu
display-setup-script=/usr/bin/x11vnc -auth /var/run/lightdm/root/:0 -rfbauth /etc/x11vnc.pass -xkb -noxrecord -noxfixes -noxdamage -forever -bg -rfbport 5900

```

and it works.

Now, there is the problem of mapping of characters and I already tried to replace the xkb option with the noxkb option but the problem remains: 

The Windows computer is mapped to the English-United States (EN) keyboard and the computer with Lubuntu has the Italian-Italian (IT) mapping. Now, doing the remote control from the Windows computer to the Linux computer and setting the keyboard mapping of this latter computer to the English (US) keyboard layout, I see that some characters =, -, +, ..., typed by Windows computer, are reproduced on the Linux machine with the characters ), /,] ... . How come? I also checked directly,, connecting a keyboard to the Linux computer, and I noticed that this problem does not exist even if I change the keyboard layout. 

So, how do I solve this mapping problem caused by the remote control?

Thanks

Bye

---

### Post by balubeto on 2014-04-07
I created this script:

```

#! /bin/sh
#
### BEGIN INIT INFO
# Provides: x11vnc
# Required-Start: $syslog $local_fs
# Required-Stop: $syslog $local_fs
# Should-Start: LightDM
# Default-Start: 2
# Default-Stop: 1
# Short-Description: x11 vnc
# Description: x11vnc
### END INIT INFO
DAEMON=/usr/bin/x11vnc
NAME=x11vnc
DESC="X11 vnc"
test -x $DAEMON || exit 0
DAEMON_OPTS="-auth /var/run/lightdm/root/:0 -rfbauth /etc/x11vnc.pass -nomodtweak -shared -forever -o /var/log/x11vnc.log -bg"
set -e
 case "$1" in
           start)
                   echo -n "Starting $DESC: "
                   start-stop-daemon --start --quiet --pidfile /var/run/$NAME.pid \
                                                     --exec $DAEMON -- $DAEMON_OPTS &
                   echo "$NAME."
           ;;
           stop)
                   echo -n "Stopping $DESC: "
                   start-stop-daemon --stop --oknodo --quiet --pidfile /var/run/$NAME.pid \
                                                    --exec $DAEMON
                   echo "$NAME."
           ;;
           restart)
                      echo -n "Restarting $DESC: "
                      start-stop-daemon --stop --quiet --pidfile \
                      /var/run/$NAME.pid --exec $DAEMON
                      sleep 1
                      start-stop-daemon --start --quiet --pidfile \
                      /var/run/$NAME.pid --exec $DAEMON -- $DAEMON_OPTS
                      echo "$NAME."
          ;;
          status)
                     if [ -s /var/run/$NAME.pid ]; then
                        RUNNING=$(cat /var/run/$NAME.pid)
                        if [ -d /proc/$RUNNING ]; then
                            if [ $(readlink /proc/$RUNNING/exe) = $DAEMON ]; then
                                echo "$NAME is running."
                                exit 0
                            fi
                        fi
                        # No such PID, or executables don't match
                        echo "$NAME is not running, but pidfile existed."
                        rm /var/run/$NAME.pid
                        exit 1
                     else
                           rm -f /var/run/$NAME.pid
                           echo "$NAME not running."
                           exit 1
                     fi
          ;;
          *)
            N=/etc/init.d/$NAME
            echo "Usage: $N {start|stop|restart|force-reload}" >&2
            exit 1
           ;;
 esac
exit 0

```

and I saved in */etc/init.d/x11vnc* and, apparently, it works and I can also control the LightDM. Now, how do I fix the problems with the remote keyboard? Now, I realized that, when a VNC client is connected, the repeat function on the keyboard of the host (and the client on the host) is automatically deactivated and it is restored when VNC clients are disconnected.

For example, under normal conditions, when I hold down a key on the host, its input is repeated until I it release; while, when a VNC client is connected, this repeat function the key does not more work.
How come?

Thanks

Bye

---

### Post by balubeto on 2014-04-09
Using this script:

```

#! /bin/sh
#
### BEGIN INIT INFO
# Provides: x11vnc
# Required-Start: $syslog $local_fs
# Required-Stop: $syslog $local_fs
# Should-Start: LightDM
# Default-Start: 2
# Default-Stop: 1
# Short-Description: x11 vnc
# Description: x11vnc
### END INIT INFO
DAEMON=/usr/bin/x11vnc
NAME=x11vnc
DESC="X11 vnc"
test -x $DAEMON || exit 0
DAEMON_OPTS="-auth /var/run/lightdm/root/:0 -rfbauth /etc/x11vnc.pass -noxkb -modtweak -capslock -repeat -flashcmap -shared -forever -o /var/log/x11vnc.log -bg"
set -e
 case "$1" in
           start)
                   echo -n "Starting $DESC: "
                   export XKL_XMODMAP_DISABLE=1
                   start-stop-daemon --start --quiet --pidfile /var/run/$NAME.pid \
                                                     --exec $DAEMON -- $DAEMON_OPTS &
                   echo "$NAME."
           ;;
           stop)
                   export XKL_XMODMAP_DISABLE=0
                   echo -n "Stopping $DESC: "
                   start-stop-daemon --stop --oknodo --quiet --pidfile /var/run/$NAME.pid \
                                                    --exec $DAEMON
                   echo "$NAME."
           ;;
           restart)
                      export XKL_XMODMAP_DISABLE=1
                      echo -n "Restarting $DESC: "
                      start-stop-daemon --stop --quiet --pidfile \
                      /var/run/$NAME.pid --exec $DAEMON
                      sleep 1
                      start-stop-daemon --start --quiet --pidfile \
                      /var/run/$NAME.pid --exec $DAEMON -- $DAEMON_OPTS
                      echo "$NAME."
          ;;
          status)
                     if [ -s /var/run/$NAME.pid ]; then
                        RUNNING=$(cat /var/run/$NAME.pid)
                        if [ -d /proc/$RUNNING ]; then
                            if [ $(readlink /proc/$RUNNING/exe) = $DAEMON ]; then
                                echo "$NAME is running."
                                exit 0
                            fi
                        fi
                        # No such PID, or executables don't match
                        echo "$NAME is not running, but pidfile existed."
                        rm /var/run/$NAME.pid
                        exit 1
                     else
                           rm -f /var/run/$NAME.pid
                           echo "$NAME not running."
                           exit 1
                     fi
          ;;
          *)
            N=/etc/init.d/$NAME
            echo "Usage: $N {start|stop|restart|force-reload}" >&2
            exit 1
           ;;
 esac
exit 0

```

I can, remotely, to have a U.S keyboard layout (Linux notation) except the *>* symbol. That is, when I press a *Shift*+*>* symbol, a [i]<[/ i] symbol appears. In other words, remotely, I have two symbols [i]<[/ i]. How come? How do I solve it?

I remind you that the keyboard layout of Windows is English-United States (EN); while that of the Linux keyboard is Italian-Italian.

Thanks

Bye

---

