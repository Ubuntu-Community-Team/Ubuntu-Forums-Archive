---
title: "Firewall being switched off on bootup."
date: 2009-12-10
forum: New to Ubuntu
---

### Post by Hamma Hedd on 2009-12-10
I have Ubuntu 9.4 (?) which was then upgraded to Edubuntu, then to Media Studio (brilliant) and then it was upgraded to Ubu 9.10.

I have added and removed assorted programs. 

It was AFTER the upgrade to Ubu 9.10 that this started happening.

I now have a boot sequence displaying the GRUB and then the BOOT FROM (bios?) codes, then the Media Studio (boot / splash screen) which gets interrupted with code message "Shutting down Firestarter Firewall". Then the boot up resumes to the Media Studio splash screen.

I now want to capture and or save the entire  boot up code, to see WHERE and WHAT is switching off the Firestarter Firewall.

BUT I don't know how to do it.

This is how I see it being done - which may not be how it is done or indeed it may not be the best way to do it... but this is my calculated speculation on the subject:

I want to inject code into the GRUB boot loader, to simultaneously  copy or save the coding of the boot codes; as a text file - for examination at my leisure later on when the computer has actually started.

The reason I want to do this, is OK the Firestarter Firewall IS actually getting switched off - and I don't know WHY.

I don't know IF an older version in the boot up is being switched off, an da newer version is being switched on, or a different firewall is being switched on.

I don't know whether the switch off is malicious or crappy programming... I don't know anything.

BUT one of the really STUPID things about some of the ideas of the people who program for Linux is to make things like the Firestarter Firewall - start and run without any indication in the back ground, with nothing visible on the GUI to show, specifically in instances like this, whether it is running or not.

It's like a car - there might be fuel in the tank and the engine management system is working quite happily with the fuel sensors, BUT - I do not know whether there is enough fuel in the tank to make the trip or no fuel in the tank.

And this is the STUPID back door on the Firestarter Firewall..... There is NOTHING to show me IF the firewall is running or not.

So in this situation I would NOT know whether it is running as it should be as a matter of course, OR if it has been switched off, deliberately - for malicious purposes or as a result of some errant or unexplained programming.

Therefore I want to make a copy into a text file, of the boot sequence codes - from the boot up as it's booting up OR obtain a copy from a log of that event:

Had a thought.... LOG(s) Did a google Ubuntu Boot Log

To shorten it down a bit found references to /var/log/boot

Did a bit of a search in that with some of Ubuntu's IDIOT searchers.... no such luck

Did a search of the ROOT and all it's contents using "firestarter" as the search term.

Came across THIS file:

/etc/init.d

HERE ARE THE CONTENTS:

#!/bin/sh
#
# Init file for the Firestarter firewall
#
# chkconfig: 2345 11 92
#
# description: Starts, stops, and lock the firewall
#
# Script Authors:
#    Tomas Junnonen <majix@sci.fi>
#    Paul Drain <pd@cipherfunk.org>
#
# config: /etc/firestarter/configuration
#
### BEGIN INIT INFO
# Provides:          firestarter
# Required-Start:    $syslog
# Required-Stop:     $syslog
# Should-Start:      $local_fs $network
# Should-Stop:       $local_fs $network
# Default-Start:     2 3 4 5
# Default-Stop:      0 1 6
# Short-Description: Start firewall
# Description:       Run firestarter-configured firewall script.
### END INIT INFO

. /lib/lsb/init-functions

FS_CONTROL="/etc/firestarter/firestarter.sh"

[ -x /usr/sbin/firestarter ] || exit 0
[ -x $FS_CONTROL ] || exit 0
[ -s /etc/firestarter/configuration ] || exit 0

RETVAL=0

start() {
    log_begin_msg "Starting the Firestarter firewall..."
    $FS_CONTROL start > /dev/null
    RETVAL=$?
    if [ $RETVAL -eq 0 ]; then
        log_end_msg 0
    else
        log_end_msg 1
    fi
    return $RETVAL
}

stop() {
    log_begin_msg "[COLOR=Red]**Stopping the Firestarter firewall**[/COLOR]..."
    $FS_CONTROL stop > /dev/null
    RETVAL=$?
    if [ $RETVAL -eq 0 ]; then
        log_end_msg 0
    else
        log_end_msg 1
    fi
    return $RETVAL
}

lock() {
    log_begin_msg "Locking the Firestarter firewall..."
    $FS_CONTROL lock > /dev/null
    RETVAL=$?
    if [ $RETVAL -eq 0 ]; then
        log_end_msg 0
    else
        log_end_msg 1
    fi
    return $RETVAL
}

# See how we were called.
case "$1" in
  start)
    start
    RETVAL=$?
    ;;
  stop)
    stop
    RETVAL=$?
    ;;
  restart)
    stop
    start
    RETVAL=$?
    ;;
  force-reload)
    stop
    start
    RETVAL=$?
    ;;
  lock)
    lock
    RETVAL=$?
    ;;
  status)
    if [ -e /var/lock/subsys/firestarter -o -e /var/lock/firestarter ]; then
        log_warning_msg "Firestarter is running..."
    else
        log_warning_msg "Firestarter is stopped"
    fi
    RETVAL=$?
    ;;
  *)
    log_success_msg "Usage: firestarter {start|stop|restart|force-reload|lock|status}"
    exit 1
esac
exit $RETVAL


Yeah so anyway.... I am having SOME success, but there is NOTHING in the boot log, 

I guess IF either I can find out HOW to make the boot log record it's self etc., which would seem to be the easiest way, or somehow link through the coding / files to find out the root cause by the process of elimination - that may be a good thing.

BUT IF anyone here has the EXPERIENCE of resolving this (combined) issue, of working out WHAT is STOPPING the Firestarter Firewall on boot up and then killing the firewall killer; you contribution would be greatly appreciated.

---

### Post by Geoff918 on 2009-12-10
Firestarter is only a front-end GUI to modify ipchains / iptables?

You wouldn't want Firestarter running as it's a security risk. FS would run only as root, so it becomes a huge attack vector.

You could just use the default UFW that's included with Ubuntu (it is another means of enabling / disabling firewall ports).

sudo ufw enable

If by default you don't want it to accept packets:

sudo ufw default deny

I'm sorry if I dodged your specific question. I more wondered if you're aware of the security risks inherent with running Firestarter continually. (And, yes, I've used Firestarter, it's pretty darn good--but just configures what Ubuntu already has--it in itself does nothing while it's enabled--'cept maybe for log purposes. Those you can have through other means without the security risks).

---

### Post by mikewhatever on 2009-12-10
I agree with Geoff918, Firestarter is deprecated in favor of ufw, and there is also a gui program for that, namely gufw.

---

### Post by ac7ss on 2009-12-10
I have this trouble as well. (until now)

type:
```
ac7ss@athena:~$ ifconfig
eth2      Link encap:Ethernet  HWaddr 00:26:18:c9:e3:6c  
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::226:18ff:fec9:e36c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:391807 errors:0 dropped:0 overruns:0 frame:0
          TX packets:340378 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:367197913 (367.1 MB)  TX bytes:43295956 (43.2 MB)
          Interrupt:26 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1 ... 
```

Note the interface that your internet connection is on...

```
sudo gedit /etc/firestarter/configuration
```

and fix the line:

```
#-----------( Firestarter Configuration File )-----------#

# --(External Interface)--
# Name of external network interface
IF="eth1"
# Network interface is a PPP link
EXT_PPP="off"
```

to:

```
IF="eth2"
```
matching eth2 to your internet connected port. (my example.

It worked for me. YMMV.

---

### Post by egalvan on 2009-12-11
I think that there is a need to emphasize that

 Firestarter **IS NOT A FIREWALL**

it is software that is designed to facilitate making/creating/changing/deleting firewall rules.

In simpler words, it sets up the firewall.

To use your "car" analogy, Firestarter is like the starter for  your engine...
It is only used to start the engine... if it were left running all the time, it would burn up.

Not to mention (as has been) that Firestarter NOT recommended...
it has too many security holes.

ufw is the preferred method of setting up the firewall
(establishing rules/chains)

---

