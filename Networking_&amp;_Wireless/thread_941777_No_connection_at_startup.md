---
title: "No connection at startup"
date: 2008-10-08
forum: Networking &amp; Wireless
---

### Post by davey boy on 2008-10-08
Hi there,

I used Kevdog's great article on how to start a wireless network in terminal, getting it down to typing the following:

```

sudo ifconfig wlan0 down

sudo dhclient -r wlan0

sudo ifconfig wlan0 up

sudo iwconfig wlan0 essid "G604T_WIRELESS"

sudo iwconfig wlan0 mode Managed

sudo dhclient wlan0
```

This works perfectly and I now have no trouble connecting using this method.

I then moved on to connecting at startup, editing my /etc/rc.local file to read as follows:

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

ifconfig eth0 down
ifconfig wlan0 down

dhclient -r wlan0

ifconfig wlan0 up
iwconfig wlan0 essid "G604T_WIRELESS"
iwconfig wlan0 mode Managed
dhclient wlan0

exit 0
```

I then made this executable using the suggested:

```

sudo chmod +x /etc/rc.local
```

On restarting my computer, I didn't have a network connection, although typing the commands into terminal again gave me a perfect connection.

I'm connecting using NDISWrapper and an RT2500usb driver, any pointers as to where I'm going wrong would be greatly appreciated.

---

