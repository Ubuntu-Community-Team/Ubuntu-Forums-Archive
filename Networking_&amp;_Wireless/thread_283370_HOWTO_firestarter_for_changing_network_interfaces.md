---
title: "HOWTO: firestarter for changing network interfaces"
date: 2006-10-24
forum: Networking &amp; Wireless
---

### Post by RikoW on 2006-10-24
Hi all,

I was always bugged by the fact, that I have to change the firestarter configuration manually, when I change my laptop from a wired network on eth0 to a wireless one on eth1. Finally I found a solution by combining ideas from these two posts:

[http://ubuntuforums.org/showthread.php?t=54927]("http://ubuntuforums.org/showthread.php?t=54927") 
[http://ubuntuforums.org/showthread.php?t=253174]("http://ubuntuforums.org/showthread.php?t=253174")

I assume, you have the network-manager set-up correctly to change between different networks. There are other threads here to tell you how that works. Basically, clean out the */etc/network/interface* file of everything except the loopback device.

When the network manager fiddles with the network devices, if executes scripts which are stored in */usr/share/NetworkManager/dispatcher.d* passing some parameters like interface name and action performed (up, down etc).

The interface name for firestarter is defined in */etc/firestarter/configuration*.

So, the only thing you need to do is put a script in the above dispatcher dir which changes the configuration file of firestarter accordingly when a new interface comes up:

```
> cat /usr/share/NetworkManager/dispatcher.d/firestarter
#!/bin/sh -e
# Script to dispatch NetworkManager events
#
# Runs firstarter with proper interface name  when NetworkManager fiddles with interfaces.
#

if [ -z "$1" ]; then
    echo "$0: called with no interface" 1>&2
    exit 1;
fi

# put interface name in quotes
IFACE='"'$1'"'
# extract currently set-up interface for firestarter from configuration file
CONF_IFACE=`grep INIF= /etc/firestarter/configuration | sed 's/INIF=//'`

# Run the right scripts
case "$2" in
    up)
        # set interface in firestarter config file to $IFACE
        # start firestarter
        chmod +w /etc/firestarter/configuration
        sed -i "s/$CONF_IFACE/$IFACE/" /etc/firestarter/configuration
        chmod -w /etc/firestarter/configuration
        firestarter --start
        ;;
    down)
        # just stop firestarter, when interface is shut down
        firestarter --stop
        ;;
esac

```

make sure the firestarter script above is executable:

Hope that helps someone! :)

            Cheers,

                     Riko

---

### Post by jonholio on 2006-11-30
Hey Riko! Thank you for such a handy little script. Much appreciated!

---

