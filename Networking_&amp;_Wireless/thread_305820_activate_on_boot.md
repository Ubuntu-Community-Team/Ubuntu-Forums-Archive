---
title: "activate on boot"
date: 2006-11-24
forum: Networking &amp; Wireless
---

### Post by new_foo on 2006-11-24
I changed the file /etc/rc.local so that it would spoof my mac address.

It looks like this:

<code>
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each mltiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.
ifconfig eth0 down hw ether 00:00:B0:00:00:01
ifconfig eth0 up
ifconfig ath0 down hw ether 00:00:00:00:00:A1
ifconfig ath0 up
exit 0
</code>

However, now when I boot, to use the ethernet connection or wifi connection, I need to deactivate and then activate the adapter under
System>Administration>Networking.

Is there something I can add to the file so that I don't need to do the deactivate/activate thing?

Thanks in advance

---

