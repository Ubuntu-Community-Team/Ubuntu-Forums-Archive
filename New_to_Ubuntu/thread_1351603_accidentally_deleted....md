---
title: "accidentally deleted..."
date: 2009-12-10
forum: New to Ubuntu
---

### Post by mydisguise09 on 2009-12-10
well i accidentally deleted /etc/init.d/gdm while to trying to follow another thread on how to change screen resolution. 

this is the code i did:
sudo /etc/init.d/gdm stop
sudo X -configure
sudo /etc/init.d/gdm start

but came up with a black screen

so i tried:
gedit /etc/xll/xorg.conf (came up with a GTK can't open display or something along those lines)
and
dpkg-reconfigure xorg

and nada

this is the point where i was messing around and deleted /etc/init.d/gdm

i tried:
sudo dpkg --audit (not sure what that was supposed to do)

sudo dpkg -P --force-depends gdm
sudo aptitude install gdm (that didn't work)

does anyone know what I could do? thanks ;)

---

### Post by Physical Hook on 2009-12-10
A fresh ( haven't even started the update yet ) install of Ubuntu 9.10:
```

#!/bin/sh -e
# upstart-job
#
# Symlink target for initscripts that have been converted to Upstart.

set -e

INITSCRIPT="$(basename "$0")"
JOB="${INITSCRIPT%.sh}"

if [ "$JOB" = "upstart-job" ]; then
    if [ -z "$1" ]; then
        echo "Usage: upstart-job JOB COMMAND" 1>&2
    exit 1
    fi

    JOB="$1"
    INITSCRIPT="$1"
    shift
else
    if [ -z "$1" ]; then
        echo "Usage: $0 COMMAND" 1>&2
    exit 1
    fi
fi

COMMAND="$1"
shift


if [ -z "$DPKG_MAINTSCRIPT_PACKAGE" ]; then
    ECHO=echo
else
    ECHO=:
fi

$ECHO "Rather than invoking init scripts through /etc/init.d, use the service(8)"
$ECHO "utility, e.g. service $INITSCRIPT $COMMAND"

case $COMMAND in
status)
    $ECHO
    $ECHO "Since the script you are attempting to invoke has been converted to an"
    $ECHO "Upstart job, you may also use the $COMMAND(8) utility, e.g. $COMMAND $JOB"
    $COMMAND "$JOB"
    ;;
start|stop|restart)
    $ECHO
    $ECHO "Since the script you are attempting to invoke has been converted to an"
    $ECHO "Upstart job, you may also use the $COMMAND(8) utility, e.g. $COMMAND $JOB"
    PID=$(status "$JOB" 2>/dev/null | awk '/[0-9]$/ { print $NF }')
    if [ -z "$PID" ] && [ "$COMMAND" = "stop" ]; then
        exit 0
    elif [ -n "$PID" ] && [ "$COMMAND" = "start" ]; then
        exit 0
    elif [ -z "$PID" ] && [ "$COMMAND" = "restart" ]; then
        start "$JOB"
        exit 0
    fi
    $COMMAND "$JOB"
    ;;
reload|force-reload)
    $ECHO
    $ECHO "Since the script you are attempting to invoke has been converted to an"
    $ECHO "Upstart job, you may also use the $COMMAND(8) utility, e.g. $COMMAND $JOB"
    reload "$JOB"
    ;;
*)
    $ECHO
    $ECHO "The script you are attempting to invoke has been converted to an Upstart" 1>&2
    $ECHO "job, but $COMMAND is not supported for Upstart jobs." 1>&2
    exit 1
esac
```Hope that solves your problem ( at least temporary ).

---

### Post by mydisguise09 on 2009-12-12
i only got this far:
#!/bin/sh -e
# upstart-job
and got a -bash on upstart-job :(

---

### Post by mydisguise09 on 2009-12-13
I tried
```
sudo aptitude -f install
```
the following NEW packages will be installed:
gdm
 
but that didn't work so I tried
```
sudo apt-get -f install
```
the following packages have unmet dependencies:
fast-user-switch-applet: Depends: gdm but it is not installed
gdm-guest-session: Depends: gdm (>7=2.20.7-0ubuntu3) but it is not installed
ubuntu-desktop: Depends: gdm but it is not installed
                         Recommends: brasero but it is not installed
E: unmet dependencies. Try using -f.
 
so I tried
```
sudo apt-get -f install
```
the following NEW packages will be installed:
gdm
suggested pacages:
uswsusp gdm-themes xserver-xephyr xnest
but that's not working either
 
I also tried
```
sudo apt-get install gnome-session
```
but it says it's already installed or it's the newest or whatever
 
theres' gotta be something I can do! somebody please help me!

---

### Post by coffeecat on 2009-12-13
The code that Physical Hook posted - you need to copy that into a text file and save that as /etc/init.d/gdm - and then make the file executable. It sounds as though you tried to enter the code in a terminal. :?

If you can't log into a GUI, boot up with the live CD and do it with that. In fact, if you boot up with the live CD, you should be able simply to copy the live session's /etc/init.d/gdm to the root partition of your HD install. Don't forget to make the file executable and owned by root before you finish.

I'm logging off now - late here - but if you need help with the details of this, someone should be able to help.

Good luck.

---

### Post by mydisguise09 on 2009-12-13
I don't have a live cd :( I tried putting that code from that guy in shell promt or when my computer boots up i log into tty1 and tried putting that code in that way (since gdm is gone)

---

### Post by Physical Hook on 2009-12-13
> **mydisguise09 said:**
> I don't have a live cd :( I tried putting that code from that guy in shell promt or when my computer boots up i log into tty1 and tried putting that code in that way (since gdm is gone)

Create a file with the contents posted above, upload it somewhere, write down the URL and use wget to download it.

---

### Post by coffeecat on 2009-12-14
> **mydisguise09 said:**
> I don't have a live cd :( 

Then you'll need to download the ISO and burn a new CD. Do you have broadband? Do you have a CDR or CDRW? Because if the fixes posted for you don't work, it sounds as though you are going to have to reinstall anyway, and for that you'll need a live CD.

> **mydisguise09 said:**
> I tried putting that code from that guy in shell promt or when my computer boots up i log into tty1 and tried putting that code in that way (since gdm is gone)

Yes, I guessed that is what you did. Do not do that - it won't work. You need a text editor to create a file. Physical Hook's idea of uploading the file somewhere and fetching it with wget from the virtual console sounds good. However, if you don't have a working Ubuntu system to create the file, there is a problem with the inbuilt Windows text editor. It creates text files differently from Unix editors. Can't remember the details - something about carriage return characters. So - your best option is to get a live CD.

---

