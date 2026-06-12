---
title: "I have to reload network module after boot??"
date: 2005-10-27
forum: Networking &amp; Wireless
---

### Post by tigerstripedcat on 2005-10-27
I have no idea why this happens, but lately I need to 

rmmod via_rhine
modprobe via_rhine 

lsmod does show it listed prior to running this, but I can't ping any servers.  Dhclient is also running.  It cant seem to grab an IP.   It was working, and now this.  Has anyone heard of this?  Anything I can do?  Should I just try and get the latest module and recompile?

Thanks

---

### Post by tigerstripedcat on 2005-10-27
Similar problem here: 

[http://www.ubuntuforums.org/showthread.php?p=446866](http://www.ubuntuforums.org/showthread.php?p=446866)

---

