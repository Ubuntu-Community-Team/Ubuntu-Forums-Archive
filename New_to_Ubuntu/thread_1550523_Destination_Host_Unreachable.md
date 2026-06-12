---
title: "Destination Host Unreachable"
date: 2010-08-11
forum: New to Ubuntu
---

### Post by amithad on 2010-08-11
Hi,

I used Ubuntu Desktop 8.10 release and tried to give a static ip for it

after assigning a static IP it received the destination host unreachable message when I try to ping  my default gateway.

after going through several forums including Ubuntu finally I got it corrected

did the changes to

/etc/network/interface   (file looks like below)


auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address x.x.x.x (remove x.x.x.x by your ip)
network x.x.x.x
netmask x.x.x.x
broadcast x.x.x.x
gateway 192.168.1.1
------------------------------------------------------------------------------
/etc/resolv.conf       (file looks like below)

nameserver 192.168.1.1

-------------------------------------------------------------------------------

/etc/rc.local           (file looks like below)

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


/sbin/ifup eth0



exit 0


Cheers !!!

amitha ;)

---

### Post by Bachstelze on 2010-08-11
Double-check your IP settings, they're probably wrong.

---

