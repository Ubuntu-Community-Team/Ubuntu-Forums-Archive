---
title: "Automatic Kppp with Huawei E220"
date: 2008-01-08
forum: Networking &amp; Wireless
---

### Post by karl_kashofer on 2008-01-08
Hi all !

I have now successfully managed to get Kubuntu 7.10 working properly with my Huawei E220. What I wanted is to just plug in the modem and be online.

My setup will now automatically load the proper driver for the Huawei E220, and automatically start kppp with the default profile when it is plugged in.

Here is my way of doing it:

```
karl@karl-laptop:~$ cat /etc/udev/rules.d/50-huawei.rules
SUBSYSTEMS=="scsi",  ATTRS{vendor}=="HUAWEI  ", ACTION=="add", OPTIONS+="ignore_device"
KERNEL=="ttyUSB0", ATTR{dev}=="188:0", SUBSYSTEMS=="usb", ATTRS{product}=="HUAWEI Mobile", ACTION=="add", RUN+="/bin/sh /home/karl/modem.sh", OPTIONS+="last_rule"
karl@karl-laptop:~$
```

```
karl@karl-laptop:~$ cat modem.sh
#! /bin/bash
export PATH=/bin:/sbin:/usr/bin:/usr/sbin
LocalDisplay=':0'

# Get the username of whoever is at the local X11 display.
# If we don't find one, then exit.
X11User=`who | grep $LocalDisplay | cut -f 1 -d ' '`
if [ -z "$X11User" ] ; then
        exit
fi

export DISPLAY=$LocalDisplay
if [ -e /home/$X11User/.bashrc ] ; then
    source /home/$X11User/.bashrc
fi

# We use nice to keep the system from eating a bunch
# of cycles just opening the file manager.
# Note that we set $HOME so the file manager can read its
# configuration file from the right place.
# Thanks to Aaron Griffin for pointing this out.
export HOME=/home/$X11User
nice -n 5 su $X11User -c "/usr/bin/kppp -c Telering" &

karl@karl-laptop:~$ 

```

Getting kppp to start from Udev was not simple until i found this:
[http://linlog.skepticats.com/content/udevautorun/](http://linlog.skepticats.com/content/udevautorun/)

Hope this helps someone,
Cheers,
Karl

---

### Post by karl_kashofer on 2008-01-11
Now with this small modification Knetworkmanager will no longer stop kde apps from accessing the internet via the ppp connection.

```
#! /bin/bash
export PATH=/bin:/sbin:/usr/bin:/usr/sbin
LocalDisplay=':0'

# Get the username of whoever is at the local X11 display.
# If we don't find one, then exit.
X11User=`who | grep $LocalDisplay | cut -f 1 -d ' '`
if [ -z "$X11User" ] ; then
        exit
fi

export DISPLAY=$LocalDisplay
if [ -e /home/$X11User/.bashrc ] ; then
    source /home/$X11User/.bashrc
fi

# We use nice to keep the system from eating a bunch
# of cycles just opening the file manager.
# Note that we set $HOME so the file manager can read its
# configuration file from the right place.
# Thanks to Aaron Griffin for pointing this out.
export HOME=/home/$X11User
#This tells knetworkmanager that we are connected
su $X11User -c "/usr/bin/dcop kded networkstatus setNetworkStatus NMNetwork 1"
nice -n 5 su $X11User -c "/usr/bin/kppp -c Telering"
su $X11User -c "/usr/bin/dcop kded networkstatus setNetworkStatus NMNetwork 0"

```

Hope this helps,
Cheers,
Karl

---

### Post by Gustavo Narea on 2008-02-25
Hello, karl_kashofer!

A dumb question: Where should I put that script?

TIA.

Edit: I'm confused because you've put the same contents twice. Should I run that script everytime I want to connect to the Internet using my USB modem?

> **karl_kashofer said:**
> Now with this small modification Knetworkmanager will no longer stop kde apps from accessing the internet via the ppp connection.

```
#! /bin/bash
export PATH=/bin:/sbin:/usr/bin:/usr/sbin
LocalDisplay=':0'

# Get the username of whoever is at the local X11 display.
# If we don't find one, then exit.
X11User=`who | grep $LocalDisplay | cut -f 1 -d ' '`
if [ -z "$X11User" ] ; then
        exit
fi

export DISPLAY=$LocalDisplay
if [ -e /home/$X11User/.bashrc ] ; then
    source /home/$X11User/.bashrc
fi

# We use nice to keep the system from eating a bunch
# of cycles just opening the file manager.
# Note that we set $HOME so the file manager can read its
# configuration file from the right place.
# Thanks to Aaron Griffin for pointing this out.
export HOME=/home/$X11User
#This tells knetworkmanager that we are connected
su $X11User -c "/usr/bin/dcop kded networkstatus setNetworkStatus NMNetwork 1"
nice -n 5 su $X11User -c "/usr/bin/kppp -c Telering"
su $X11User -c "/usr/bin/dcop kded networkstatus setNetworkStatus NMNetwork 0"

```

Hope this helps,
Cheers,
Karl

---

