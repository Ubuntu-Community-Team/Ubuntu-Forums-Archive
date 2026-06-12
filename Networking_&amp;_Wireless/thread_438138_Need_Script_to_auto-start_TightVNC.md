---
title: "Need Script to auto-start TightVNC"
date: 2007-05-09
forum: Networking &amp; Wireless
---

### Post by rmonroe36 on 2007-05-09
I am using Hamachi and TightVNC for remote control of my Windows XP Pro. My Windows computer is set up as server and Ubuntu Fiesty is setup as viewer and all works well. Is there a script or a way to start xTightVNCviewer with correct password and address automatically instead of my having to open a terminal and start it that way?          Warning! I am a noobie.

---

### Post by seamuso on 2007-05-09
create a password file for vnc on the linux system

In a terminal - 

$ vncpasswd
Password <your vnc server passwd>
Verify <your vnc server passwd>
$

This creates a passwd file in ~/.vnc, then you just need to have this run 

vncviewer -passwd /home/<your username>/.vnc/passwd <your vnc server address>

create a new application shortcut use the above command set it to run in terminal or not (I do it both ways in xfce)

---

### Post by rmonroe36 on 2007-05-09
Thanks so much seamuso for the quick reply to my plight. It worked perfectly and I learned a little more about using the Application Launcher. [COLOR="Sienna"]**_Ubuntu_**[/COLOR] is a great community!

---

### Post by flade on 2007-05-17
Me is using Xubuntu 6.10

I installed tightvncserver. How to autostart (now i have to manually start vncserver); damnnn


regards,

---

### Post by abubin on 2007-11-11
I am using xubuntu 7.10.

Also looking for scripts that can start tightvncserver when my server is booting up.

There are scripts out there using xinetd but it doesn't work or I am too dumb to figure it out.

I also tried putting the command "vncserver :1" into rc.local file but it doesn't work. Anyone have any idea why it doesn't work in rc.local file? Or anyone with any solution, please help.

Thanks in advance.


edit:

found a site that teaches how to add a startup script. [http://ubuntu.wordpress.com/2005/09/07/adding-a-startup-script-to-be-run-at-bootup/](http://ubuntu.wordpress.com/2005/09/07/adding-a-startup-script-to-be-run-at-bootup/)

will try this later when I get back home.

---

### Post by abubin on 2007-11-12
ok, that startup script above doesn't work.

Currently, I manage to get tightvncserver/vnc4server (they works the same) working by running "vncserver :1" from command line. But this means I have to start this vncserver manually every time I reboot.

The only thing missing now is to add a script to run it like how redhat/fedora is doing. I can't just run "vncserver :1" directly because it will complain that my HOME environment is not setup because during bootup, it's running as ROOT.

This script by redhat actually handles the environment and multiple vncservers. Maybe someone with scripting skill can convert this script into ubuntu?

> 
#!/bin/bash
#
# chkconfig: - 91 35
# description: Starts and stops vncserver. \
#	       used to provide remote X administration services.

# Source function library.
. /etc/init.d/functions

# Source networking configuration.
. /etc/sysconfig/network

# Check that networking is up.
[ ${NETWORKING} = "no" ] && exit 0

VNCSERVERS=""
[ -f /etc/sysconfig/vncservers ] && . /etc/sysconfig/vncservers

prog=$"VNC server"

start() {
    echo -n $"Starting $prog: "
    ulimit -S -c 0 >/dev/null 2>&1
    RETVAL=0
    for display in ${VNCSERVERS}
    do
        echo -n "${display} "
	unset BASH_ENV ENV
        initlog $INITLOG_ARGS -c \
            "su ${display##*:} -c \"cd ~${display##*:} && [ -f .vnc/passwd ] && vncserver :${display%%:*}\""
        RETVAL=$?
        [ "$RETVAL" -ne 0 ] && break
    done
    [ "$RETVAL" -eq 0 ] && success $"vncserver startup" || \
        failure $"vncserver start"
    echo
    [ "$RETVAL" -eq 0 ] && touch /var/lock/subsys/vncserver
}

stop() {
    echo -n $"Shutting down $prog: "
    for display in ${VNCSERVERS}
    do
        echo -n "${display} "
	unset BASH_ENV ENV
        initlog $INITLOG_ARGS -c \
	    "su ${display##*:} -c \"vncserver -kill :${display%%:*}\" >/dev/null 2>&1"
    done
    RETVAL=$?
    [ "$RETVAL" -eq 0 ] && success $"vncserver shutdown" || \
        failure $"vncserver shutdown"
    echo
    [ "$RETVAL" -eq 0 ] && rm -f /var/lock/subsys/vncserver
}

# See how we were called.
case "$1" in
  start)
	start
	;;
  stop)
	stop
	;;
  restart|reload)
	stop
	start
	;;
  condrestart)
	if [ -f /var/lock/subsys/vncserver ]; then
	    stop
	    start
	fi
	;;
  status)
	status Xvnc
	;;
  *)
	echo $"Usage: $0 {start|stop|restart|condrestart|status}"
	exit 1
esac


This is what's in /etc/sysconfig/vncservers. For ubuntu, it should be /etc/vncservers :
> 
# The VNCSERVERS variable is a list of display:user pairs.
#
# Uncomment the line below to start a VNC server on display :1
# as my 'myusername' (adjust this to your own).  You will also
# need to set a VNC password; run 'man vncpasswd' to see how
# to do that.
#
# DO NOT RUN THIS SERVICE if your local area network is
# untrusted!  For a secure way of using VNC, see
# <URL:http://www.uk.research.att.com/vnc/sshvnc.html>.

VNCSERVERS="1:fred 2:joe"

# fred's VNC options
VNCSERVERARGS[1]="-geometry 1024x768"

# joe's VNC options
VNCSERVERARGS[2]="-geometry 1280x1024"


[COLOR="Blue"]
Summary of steps to start vncserver during boot (based on fedora script) :

   1.  Set a password using vncpasswd (done)
   2. Edit /etc/sysconfig/vncservers (done - same file saved in /etc/vncservers)
   3. Enable the service with chkconfig vncserver on (done - use update-rc.d in ubuntu)
   4. Start the service with service vncserver start **(halt - this is the one script that need to convert to ubuntu)**
   5. Edit /home/username/.vnc/xstartup if you want a more advanced session than just twm and an xterm (done - already have this in ubuntu)

[/COLOR]

---

### Post by carlg on 2008-01-30
Phew - this was a problem for me too. I finally got it to work (starting up a tightvnc server on server boot for a specific user). I'm on Ubuntu 7.10 (actually running on Amazon EC2)

First, make sure your user has a passwd file (as already discussed)

Then I simply put this one line at the end of /etc/rc.local:

su user -c "cd ~user && vncserver :1"

where "user" is replaced with your username. All that does is switch user to your user, go to their home directory, and call vncserver :1 like you would if you were logged in. Not very sophisticated, but it worked for me.

Thanks goes to abubin - that script he posted led me to this.

---

