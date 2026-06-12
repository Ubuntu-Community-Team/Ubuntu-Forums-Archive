---
title: "Can't start DDclient as daemon even with daemon support turned on"
date: 2008-08-22
forum: Networking &amp; Wireless
---

### Post by jonathanmotes on 2008-08-22
I'm checking the status of DDClient on my computer like this:

```
root@jmotes1-laptop:/home/jmotes1# /etc/init.d/ddclient start
root@jmotes1-laptop:/home/jmotes1# /etc/init.d/ddclient status
Status of Dynamic DNS service update utility: ddclient is not running.
root@jmotes1-laptop:/home/jmotes1# 
```

It seems that it is not wanting to run as a daemon even though I have specified that it do so. Here's my /etc/default/ddclient file:
```
# Configuration for ddclient scripts 
# generated from debconf on Wed Aug 20 23:56:43 CDT 2008
#
# /etc/default/ddclient

# Set to "true" if ddclient should be run every time a new ppp connection is 
# established. This might be useful, if you are using dial-on-demand
run_ipup="true"

# Set to "true" if ddclient should run in daemon mode
run_daemon="true"

# Set the time interval between the updates of the dynamic DNS name in seconds.
# This option only takes effect if the ddclient runs in daemon mode.
#daemon_interval="300"
daemon_interval="10"
```

Any ideas anyone?

Thanks!

---

