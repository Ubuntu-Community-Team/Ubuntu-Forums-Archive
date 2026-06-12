---
title: "Running an iwconfig command at startup"
date: 2015-04-26
forum: Networking &amp; Wireless
---

### Post by enarab2 on 2015-04-26
In prior versions of Ubuntu I have been able to add the line

```
/sbin/iwconfig wlan0 txpower 10
```

at the end of */usr/lib/pm-utils/power.d/wireless* to drop the tx-power of the wireless connection to 10 as a workaround to a known bug ([https://bugzilla.kernel.org/show_bug.cgi?id=61111](https://bugzilla.kernel.org/show_bug.cgi?id=61111)). However this no longer works with Kubuntu 15.04 and I have to type the command in manually each time after a reboot. 

Is there any other way to automate this process?

---

### Post by chili555 on 2015-04-26
Have you tried adding the line to /etc/rc.local like this?```
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

iwconfig wlan0 txpower 10

exit 0

```

---

### Post by enarab2 on 2015-04-26
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

/sbin/iwconfig wlan0 txpower 10

exit 0
```

Yep, this definitely works, thanks a lot!

---

