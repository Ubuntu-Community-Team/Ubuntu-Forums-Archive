---
title: "The NE2000 network card is not starting at restart of the computer"
date: 2006-11-25
forum: Networking &amp; Wireless
---

### Post by ratanjska on 2006-11-25
Hi!

I am running a computer with an old (ne2000 compatible) network card. My UBUNTU is 6.06.

I have changed etc/network/interfaces by writing in:

auto eth0
iface eth0 inet dhcp

I can get network working and I have the internet access only by running the following:

sudo modprobe ne 

every time I am going to use the net.

I have found somewhere that putting:

/sbin/modprobe ne

at the top of /etc/inti.d/networking

will make that the network card will start at the reboot.

I am not sure how to change (where to put this new command line) into /etc/inti.d/networking
It is beginning like that:

#!/bin/sh -e
### BEGIN INIT INFO
# Provides:          networking
# Required-Start:    mountvirtfs ifupdown $local_fs
# Default-Start:     S
# Default-Stop:      0 6
### END INIT INFO

PATH="/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin"

[ -x /sbin/ifup ] || exit 0

. /lib/lsb/init-functions

case "$1" in
start)
	log_action_begin_msg "Configuring network interfaces"
        type usplash_write >/dev/null 2>/dev/null && usplash_write "TIMEOUT 120" || true
	if [ "$VERBOSE" != no ]; then
	    if ifup -a; then
		log_action_end_msg $?
	    else
		log_action_end_msg $?

Thank you in advance

Ratanjska

*_*_*_*_*_*_*_*_'*_*_*_*_*_*_*_*_*_*_*_*_*

Ratanjska is a small river near my hometown

---

### Post by Huike on 2006-11-27
You may want to try put the following line in your /etc/modules file:

ne irq=N io=0xNNN

If yours ne2k card is not pnp, depends on your card setting, N is the irq of you ne2k card such as 5 or 3 or 4, io is the I/O range such as 0x300, or 0x320, or 0x340 etc.

If you card is pnp maybe just ne will do.

This worked for me, I just found it today on this forum.

---

