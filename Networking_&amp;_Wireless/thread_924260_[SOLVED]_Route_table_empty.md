---
title: "[SOLVED] Route table empty"
date: 2008-09-19
forum: Networking &amp; Wireless
---

### Post by geoff_m on 2008-09-19
We're encountering a strange problem (hardy Heron).  My wife went on a trip and tried to use her new Dell laptop on wireless.  Having the same machine, I tried to help from home when she couldn't connect - which we never got working.

Anyway, now back home and connected to the home STATIC network, every time she suspends, hibernates, or shutdowns, the ifconfig does not have her ip address and the route table is empty.  So she is forced to manually enter from a terminal:

```
sudo ifconfig eth0 192.168.1.xxx
sudo route add default gw 192.168.1.1
```

every time she comes out of suspend mode.

I thought if you did these things they would be permanent.  Any idea why these are being reset?  Her Network manager shows correct values, but doesn't fix the problem.

I screwed around with the network manager, and somehow managed to get *my* laptop back into "normal"mode so I don't have this problem.  I have no idea what I did to make it so.  But seeing as the two machines are "identical" I live in fear that this will happen to me as well.

---

### Post by nixscripter on 2008-09-19
When your computer goes into and comes out of hibernate, a whole bunch of scripts run. One of those isn't setting the network back up.

First, what's in /etc/network/interfaces? By default, that's what those scripts should re-establish. If that's wrong, it won't work.

Second, if that looks okay, then look at the scripts themselves. Assuming you are using ACPI for power management, **/etc/acpi/resume.d** and **/etc/acpi/suspend.d** are what you should look at. These are full of shell scripts. If you're not familiar to linux, look for things with names like **##-ifup.sh** (where ## is a pair of digits). Some script might not be doing the right thing, which could be the problem.

Third, you might try a patchwork solution to several networking-related problems with suspend: add a script to resume to kick the network manager applet (which seems to do the right thing). Create a script called **99-nm-restart.sh** (or whatever number is higher than everything else) in the **/etc/acpi/resume.d/** directory, and put this in it:

```

#!/bin/sh
#
# Shell script created to deal with network restart on resume.
# kudos Ubuntu Forums
/etc/dbus-1/event.d/25NetworkManager restart
/etc/dbus-1/event.d/26NetworkManagerDispatcher restart

```

Hope one of these will work.

---

### Post by geoff_m on 2008-09-19
Spot on.  I had checked the /etc/network/interfaces, but I missed seeing the missing line 

```
auto eth0
```

I wonder how that got messed up.  Learn something new everyday.  Thanks so much! :popcorn:

---

### Post by nixscripter on 2008-09-20
Great. Please Mark This Thread Solved under the thread tools menu.

---

