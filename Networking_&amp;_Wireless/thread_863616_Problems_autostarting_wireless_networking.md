---
title: "Problems autostarting wireless networking"
date: 2008-07-18
forum: Networking &amp; Wireless
---

### Post by electronic_oz on 2008-07-18
Hello!

My wireless networking isn't working under ubuntu 8.04.  I have a broadcom model 

```
02:00.0 Network controller: Broadcom Corporation BCM4328 802.11a/b/g/n (rev 03))
```


when I start up I just get a IP4LL ip address:

```

wlan0     Link encap:Ethernet  HWaddr 00:1f:5b:c1:12:0b  
          inet6 addr: fe80::21f:5bff:fec1:120b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:45 errors:0 dropped:0 overruns:0 frame:0
          TX packets:32 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5085 (4.9 KB)  TX bytes:4917 (4.8 KB)
          Interrupt:16 Memory:90500000-90504000 

wlan0:avahi Link encap:Ethernet  HWaddr 00:1f:5b:c1:12:0b  
          inet addr:169.254.3.152  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:16 Memory:90500000-90504000 

```

but when i sudo /etc/init.d/networking restart it works:

```

wlan0     Link encap:Ethernet  HWaddr 00:1f:5b:c1:12:0b  
          inet addr:192.168.1.7  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21f:5bff:fec1:120b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:224 errors:0 dropped:0 overruns:0 frame:0
          TX packets:192 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:28893 (28.2 KB)  TX bytes:46086 (45.0 KB)
          Interrupt:16 Memory:90500000-90504000)

```

here's my /etc/network/interfaces file:
 
```

auto lo
iface lo inet loopback

iface wlan0 inet dhcp
wpa-psk (password)
wpa-driver wext
wpa-key-mgmt WPA-PSK
wpa-proto WPA
wpa-ssid (ssid)

auto wlan0

```

any ideas? Thanks in advance.

---

### Post by lisati on 2008-07-18
I see you've got WPA encryption set. Have a look at this thread: [http://ubuntuforums.org/showthread.php?t=202834&highlight=setting+wpa](http://ubuntuforums.org/showthread.php?t=202834&highlight=setting+wpa)

The second post deals with networking not properly starting after a reboot.

---

### Post by falcon61102 on 2008-07-18
Go into your terminal and run:
```
lshw -C network
```
and post the output here.  Seems you may have the common Broadcom problem.  It's not a hard fix.

---

### Post by electronic_oz on 2008-07-19
Thanks! Unfortunately, the recommendations in that wieman01's thread did not seem to help. This is what I get after a 
```

lshw -C network

```

```

  *-network               
       description: Wireless interface
       product: BCM4328 802.11a/b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 03
       serial: 00:1f:5b:c1:12:0b
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.52+Broadcom,10/12/2006, 4.100. latency=0 link=no module=ndiswrapper multicast=yes wireless=IEEE 802.11g
  *-network
       description: Ethernet interface
       product: Marvell Yukon 88E8058 PCI-E Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 13
       serial: 00:22:41:1e:be:0a
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.20 firmware=N/A latency=0 link=no module=sky2 multicast=yes port=twisted pair

```

The `common Broadcom problem. It's not a hard fix.' part sounds encouraging?

---

### Post by falcon61102 on 2008-07-19
It looks like your driver is installed correctly.  Are you able to connect at all?

Also, did you add "ndiswrapper" to the last line of "/etc/modules" so that ndiswrapper would be loaded at each boot?

---

### Post by electronic_oz on 2008-07-19
Thanks Falcon, I did indeed:

```
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

fuse
lp
sbp2
mousedev 
psmouse 
ndiswrapper
```

---

### Post by electronic_oz on 2008-07-19
And sorry, to clarify, I am able to connect only when using the manual sudo /etc/init.d/networking restart.

---

### Post by falcon61102 on 2008-07-19
Could you post the contents of your networking file, use:
```
sudo gedit /etc/init.d/networking
```

Also, when you initially installed ndiswrapper do you remember doing a step:
```
sudo depmod -a
```

---

### Post by electronic_oz on 2008-07-19
Hi again, my /etc/init.d/networking follows:

```
#!/bin/sh -e
### BEGIN INIT INFO
# Provides:          networking
# Required-Start:    mountkernfs ifupdown $local_fs
# Required-Stop:     ifupdown $local_fs
# Default-Start:     S
# Default-Stop:      0 6
# Short-Description: Raise network interfaces.
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
	    fi
	else
	    if ifup -a >/dev/null 2>&1; then
		log_action_end_msg $?
	    else
		log_action_end_msg $?
	    fi
	fi
        type usplash_write >/dev/null 2>/dev/null && usplash_write "TIMEOUT 15" || true
	;;

stop)
	if sed -n 's/^[^ ]* \([^ ]*\) \([^ ]*\) .*$/\2/p' /proc/mounts | 
		grep -qE '^(nfs[1234]?|smbfs|ncp|ncpfs|coda|cifs)$'; then
	    log_warning_msg "not deconfiguring network interfaces: network shares still mounted."
	    exit 0
	fi

	log_action_begin_msg "Deconfiguring network interfaces"
	if [ "$VERBOSE" != no ]; then
	    if ifdown -a --exclude=lo; then
		log_action_end_msg $?
	    else
		log_action_end_msg $?
	    fi
	else
	    if ifdown -a --exclude=lo >/dev/null 2>/dev/null; then
		log_action_end_msg $?
	    else
		log_action_end_msg $?
	    fi
	fi
	;;

force-reload|restart)
	log_action_begin_msg "Reconfiguring network interfaces"
	ifdown -a --exclude=lo || true
	if ifup -a --exclude=lo; then
	    log_action_end_msg $?
	else
	    log_action_end_msg $?
	fi
	;;

*)
	echo "Usage: /etc/init.d/networking {start|stop|restart|force-reload}"
	exit 1
	;;
esac

exit 0
```

I don't remember doing sudo depmod -a, but when I gave it a shot just then, it didn't seem to help the problem. Thanks again!

---

