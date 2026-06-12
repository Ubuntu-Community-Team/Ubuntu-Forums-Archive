---
title: "ugraded wicd - no internet"
date: 2008-09-29
forum: Networking &amp; Wireless
---

### Post by currywuss on 2008-09-29
One of the upgrades to be installed this morning was wicd. During the installation, I received three error messages saying something like 'wicd has been altered by you so say x (three bits of script) - do you want to keep these or install the new version?' I chose keep for all three (thinking that there must have been a reason that I'd changed wicd, even though I didn't actually know what these scripts were doing :oops: ) The internet was working fine, but after switching my laptop back on at a later point this was no longer the case. 

I can't open wicd even though the icon is there in the menu. I've tried re-installing it from /var/cache/apt/archives but that failed. I have no internet access on the laptop in question (I'm using a different machine to write this post) so can't download network manager. I'm rather stuck ](*,) Any help would be great.

---

### Post by ww711 on 2008-09-29
I did the same thing of upgrading the wicd through the package manager. Now my wireless does not work now.

It detects several wireless connections including my own. I have tried configuring the using relevant encryption and passwords that I have. Still no success.

Serves me right for upgrading!?!? 

Maybe II-8.10 will handle the wireless in a better way...

---

### Post by ww711 on 2008-09-29
I decided to uninstall wicd and rebooted, tried selecting the relevant encryption and my wireless network password through using the built in network manager in Ubuntu, it has now detected the wireless network and authenticated, success!

---

### Post by currywuss on 2008-09-29
Thanks guys. I've managed to get a wired connection on the relevant machine & tried to completely uninstall Wicd. Doesn't seem to work... Any ideas?


> julia@julia-laptop:~$ sudo apt-get remove wicd
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libglib1.2ldbl libgtk1.2 libdns32 libxul0d galeon-common libmozjs0d
  libgtk1.2-common libxul-common linux-headers-2.6.24-16-generic
  linux-headers-2.6.24-16
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  wicd
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 1774kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 186616 files and directories currently installed.)
Removing wicd ...
Stopping wicd daemon...
invoke-rc.d: initscript wicd, action "stop" failed.
dpkg: error processing wicd (--remove):
 subprocess pre-removal script returned error exit status 1
Stopping any running daemons...
Starting wicd daemon...
Errors were encountered while processing:
 wicd
E: Sub-process /usr/bin/dpkg returned an error code (1)
julia@julia-laptop:~$ 

---

### Post by STPitcher on 2008-09-29
Ah... I guess I have to assume that WiCd is simply broke!  I also allowed it to upgrade this morning, and then immediately lost wireless contact.  Now I don't seem to be able to get it back, no matter what I try.  I'm stuck with wired.. which is not convenient.  WiCd does handle wired ok... 

I'm using WPA.  On my router, its labeled WPA-PSK.  I assume this refers to the Pre Shared Key...  THis was working fine until this update.

I hope a new fix appears soon.

- stp

---

### Post by itsjareds on 2008-09-29
Does anyone need me to give them the old version? I have it saved.

Also, try uninstalling then deleting the /opt/wicd folder, then reinstall. Do the same if you uninstall then install with my version.

Edit: Here you go :D - [ATTACH]86750[/ATTACH]

---

### Post by imdano on 2008-09-29
In the new version of wicd, /opt/wicd/ is no longer used.  Most of you probably just need to update your sessions entry for wicd to use "wicd-client", instead of /opt/wicd/tray.py.  If you're still having trouble, try rebooting so that both wicd and dbus get reset.  For those of you having trouble uninstalling, see [this thread](http://wicd.net/punbb/viewtopic.php?id=187).

---

### Post by John Jason Jordan on 2008-09-29
> **imdano said:**
> In the new version of wicd, /opt/wicd/ is no longer used.  Most of you probably just need to update your sessions entry for wicd to use "wicd-client", instead of /opt/wicd/tray.py.  If you're still having trouble, try rebooting so that both wicd and dbus get reset.  For those of you having trouble uninstalling, see [this thread](http://wicd.net/punbb/viewtopic.php?id=187).
I had the same problem - the icon no longer worked. In fact, I had the launch icon in my gnome panel and I immediately guessed it wasn't going to work because the icon was a black square instead of the tower radiating waves. However, I discovered that the upgrade did add a new launch item in Applications > Internet, and the new launch item had the new icon. I just copied the launch command from it to the launch icon in my gnome panel and all was well again as far as launching it.

But now I have a different problem. At home I am wired for ethernet, so the wireless is not an issue. However, at the university there are a couple dozen networks listed as being available. Only one is available to me as a student. When I click to connect to it occasionally there is a delay getting an ip address. The delay is just because there are too many students at the moment. Unfortunately, wicd seems to be set to a very short timeout period and, if it does not connect within the timeout period it automatically goes to the next network. It will connect to this network, but since I am not authorized to use it I can't get a DHCP lease. 

I need to figure out how to tell wicd not to do that. If it cannot connect to the network I selected, then just give me a "could not connect" error message and stop. Don't automatically try the next one.

Does anyone know how to do that?

---

### Post by zerofxC on 2008-09-30
I have a similar problem just like currywuss. 

I had a notification that there was a Wicd update avaliable yesterday. I ran the upgrade, selected keep when it asked me if i wanted to replace the three scripts and the connection was fine until i rebooted.

Now there is no tray icon and when i click on the Wicd icon in Applications nothing will load.

When trying to apt-get remove wicd i get a similar error level to this one

```
Sub-process /usr/bin/dpkg returned an error code (1)
```

I have found the wicd_1.5.3_all.deb and am going to try re installing it. Only problem is my desktop is far away from my router so a wired link is pretty much out of the question!

Anyone managed to solve it yet?:guitar:

---

### Post by cutOff on 2008-09-30
> **itsjareds said:**
> Does anyone need me to give them the old version? I have it saved.

Also, try uninstalling then deleting the /opt/wicd folder, then reinstall. Do the same if you uninstall then install with my version.

Edit: Here you go :D - [ATTACH]86750[/ATTACH]

Thanks for the package. I had same trouble, and fixed it:

a) Removing /var/lib/dpkg/info/wicd.prerm
b) Purging wicd (aptitude purge wicd)
c) Installing the package you provide (dpkg -i wicd_1.4.2-1-all.deb)
d) **Restart** and all OK

Thanks :D

---

### Post by manro on 2008-09-30
I also upgrade wicd yesterday and, as others around here, could not connect to my wireless network(s) (WPA-PSK secured), is like wicd doesn't find any wireless network around, but once I connect my laptop to a wired network the wireless networks begin to appear. I restart my laptop several times to tests the auto-connect function and always found the same behavior: If I'm connected to a wired network I can see the wireless ones but *"not wireless found"* until I connect to a wired network.

Not a smart way to work if you want some mobility! :-k

Going back to the old wicd. :)

Regards,
MaNRo

---

### Post by imdano on 2008-09-30
Once you guys are able to uninstall 1.4.2, don't reinstall it!  Install 1.5.3, its really much improved.  The problems you're having installing it are caused by 1.4.2's uninstall script, it has nothing to do with 1.5.3.  However the location of most of the files has moved so it's important that you read [http://wicd.net/latest/changes](http://wicd.net/latest/changes) so you know how to launch it and find config files once you do upgrade successfully.  For the lazy, /opt/wicd/ is gone, and you start the GUI with ```
wicd-client
```This means that your shortcuts might stop working until you update them with the new location.

@manro
What happens when you run "sudo iwlist scan" when you're not connected to a wired network?  What if you run "sudo ifconfig <wireless interface> up", then run the scan command?

---

### Post by currywuss on 2008-09-30
Great, new version of wicd is go! Thanks alot.

---

### Post by itsjareds on 2008-09-30
Hm. I guess I'll update to the latest version.. I'm way behind :D

---

### Post by la3875 on 2008-10-01
:confused: I too saw the upgrade and installed but I think it broke because I can no longer launch the program or connect to networks both wired and wireless. Can I install from external file? How can I get Gnome manager working again w/o network connectivity?

Thanks in advance.

---

### Post by imdano on 2008-10-01
> **la3875 said:**
> :confused: I too saw the upgrade and installed but I think it broke because I can no longer launch the program or connect to networks both wired and wireless. Can I install from external file? How can I get Gnome manager working again w/o network connectivity?

Thanks in advance.Read this, it covers the reasons 1.5.3 might seem broken: [http://wicd.net/punbb/viewtopic.php?pid=822](http://wicd.net/punbb/viewtopic.php?pid=822)

---

### Post by itsjareds on 2008-10-01
Try connecting through the terminal.

---

### Post by Urgazhi on 2008-10-01
```
urgazhi@urgazhi-laptop:~$ sudo apt-get install wicd 
[sudo] password for urgazhi: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  wicd
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/227kB of archives.
After this operation, 65.5kB of additional disk space will be used.
(Reading database ... 187941 files and directories currently installed.)
Preparing to replace wicd 1.5.0rc5 (using .../archives/wicd_1.5.3_all.deb) ...
Stopping wicd daemon...
invoke-rc.d: initscript wicd, action "stop" failed.
dpkg: warning - old pre-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
Stopping wicd daemon...
invoke-rc.d: initscript wicd, action "stop" failed.
dpkg: error processing /var/cache/apt/archives/wicd_1.5.3_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
Stopping any running daemons...
Starting wicd daemon...
Errors were encountered while processing:
 /var/cache/apt/archives/wicd_1.5.3_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
urgazhi@urgazhi-laptop:~$ 

```

I have been trying to update my wicd client... I installed 1.5.0 (I believe) from the sourceforge website a while ago and it installed fine... can anyone give me a hint as how to get it to actually update though?

EDIT:::::

After some searching I think I found the issue....

the file /etc/init.d/wicd should be replaced with

```

#! /bin/sh
### BEGIN INIT INFO
# Provides:          wicd
# Required-Start:    dbus
# Required-Stop:     
# Default-Start:     2 3 4 5
# Default-Stop:      0 1 6
# Short-Description: Starts and stops Wicd
# Description:       Starts and stops Wicd, a network manager
### END INIT INFO

# Author: Adam Blackburn <compwiz18@users.sourceforge.net>
#

# Do NOT "set -e"

# PATH should only include /usr/* if it runs after the mountnfs.sh script
PATH=/usr/sbin:/usr/bin:/sbin:/bin
DESC="Network connection manager"
NAME=wicd
DAEMON=/usr/sbin/$NAME
DAEMON_ARGS=""
PIDFILE=/var/run/wicd/wicd.pid
SCRIPTNAME=/etc/init.d/wicd

# Exit if the package is not installed
[ -x "$DAEMON" ] || exit 0

# Read configuration variable file if it is present
[ -r /etc/default/$NAME ] && . /etc/default/$NAME

# Load the VERBOSE setting and other rcS variables
[ -f /etc/default/rcS ] && . /etc/default/rcS

# Define LSB log_* functions.
# Depend on lsb-base (>= 3.0-6) to ensure that this file is present.
. /lib/lsb/init-functions

# Perhaps not the best idea
# but a confirmation is nice
# when starting/stopping the daemon
VERBOSE=yes

#
# Function that starts the daemon/service
#
do_start()
{
    # Return
    #   0 if daemon has been started
    #   1 if daemon was already running
    #   2 if daemon could not be started
    #   vvvv -- don't do this -- vvvv
    #   [ -e $PIDFILE ] && return 1
    start-stop-daemon --start --quiet --pidfile $PIDFILE --startas $DAEMON --test > /dev/null \
        || return 1
    start-stop-daemon --start --quiet --pidfile $PIDFILE --startas $DAEMON -- \
        $DAEMON_ARGS > /dev/null 2> /dev/null\
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

```

This allowed me to uninstall the old WICD and allowed the new one to install correctly  I believe the old init.d file was wrong in some manner....

---

### Post by la3875 on 2008-10-02
:) I'm back in the game! If your update broke your wicd like it did mine, i recommend the following solution:

First visit this page [http://wicd.net/punbb/viewtopic.php?id=187](http://wicd.net/punbb/viewtopic.php?id=187) and follow this instruction to uninstall

code: sudo rm /var/lib/dpkg/info/wicd.prerm

Second, open Synaptic and search for wicd and mark for complete removal and apply change

Third, I downloaded the .deb package (not the .tar) onto a usb drive and installed and I'm back including my previous wireless profiles!

Hope this helps!

---

### Post by swistakers on 2008-12-13
**zerofxC**: Can you put the deb with 1.5.3 somewhere?

---

### Post by john2 on 2008-12-13
My wireless stopped working when I upgraded Wicd - fixed it as follows:

Open Wicd Manager by clicking on the applet
Click on the down arrow next to your network
Click on Advanced Settings
Make sure 'WPA 1/2 (Preshared Key)' is selected in the dropdown
(Re)enter the WPA key

---

### Post by Dopaque on 2008-12-21
Ha! That's so weird! A wicd update broke my wireless too, and WPA 1/2 (Passphrase) ceased to work, whilst WPA 1/2 (Preshared Key) did it.

Anyone know what's up with that?

---

### Post by imdano on 2008-12-21
Is there whitespace in the name of the network you're trying to connect to?  There's a regression in 1.5.6 that causes psk generation to fail for any essid that's more than a single word.  Using the psk template works around it.

---

