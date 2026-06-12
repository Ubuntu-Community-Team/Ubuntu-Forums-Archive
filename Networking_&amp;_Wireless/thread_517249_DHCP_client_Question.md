---
title: "DHCP client Question"
date: 2007-08-04
forum: Networking &amp; Wireless
---

### Post by mr.propre on 2007-08-04
Little noobisch, but how do u turn it on and off using the terminal.
I need it to use it with kismet, but don't find it.

Thanks in advance

---

### Post by kevdog on 2007-08-04
Like this??

sudo dhclient <interface name>

sudo killall dhclient

---

### Post by mr.propre on 2007-08-04
Doesnt seem to work -> sudo killall dhclient

---

### Post by kevdog on 2007-08-04
sudo killall dhclient dhclient3

To confirm, if you have dhcp address

sudo ps -ef | grep dhclient

then do the killall statement above and then recheck with the ps statement.  The process should be gone.

---

