---
title: "wireless stopped working after update"
date: 2007-03-22
forum: Networking &amp; Wireless
---

### Post by Slapyo on 2007-03-22
before i ran the updates i had no problem. as soon as i turned on the computer it picked up my wireless connection and everything was good. after i updated the wireless would not work unless i do the following.

- double click network monitor (only lo is in connection name, not eth1)
- click configure
- use the drop down for essid (it picks up the wireless networks and signal stengths just fine)
- click ok
- double click network monitor again (only lo is in connection name, not eth1)
- click configure
- get error "The interface does not exist."
- double click network monitor again (now lo and eth1:avahi in connection name)
- removed the ":avahi" part soonly eth1 is left
- click configure
- put correct essid
- click ok
- now i have internet

:/

i didn't make any changes, just ran the updates and now it doesn't work like it did before. i'd like it to just connect like it did before without having me go through all these hoops to get it to work.

---

### Post by Slapyo on 2007-03-23
anyone?

---

### Post by ffxr on 2007-03-23
if it is the kernel updates, you will have you reinstall the kernel modules for your wireless card.. 

how did u install the wireless NIC previously?

---

### Post by Slapyo on 2007-03-23
the kernel has updated before no problem. but i am using 386 not generic and that one has not updated since i installed ubuntu.  i never installed the wireless nic card myself.  i install ubuntu and it just worked out of the box.

---

### Post by ffxr on 2007-03-23
i still believe you have to reinstall that nic tho.. 

what kernel are you using? 

```
 uname -r 
```

and what wireless card is it?

---

### Post by ffxr on 2007-03-23
oh god m reading your post wrong, my bad.. shouldnt jump to assumptions.. sorry

can you post your interfaces file pls..

```
 gksu gedit /etc/network/interfaces 
```

---

### Post by Slapyo on 2007-03-23
2.6.20-5-386
Intel Corporation PRO/Wireless 2915ABG Network
if I type lspci | grep Ethernet i get this: 03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)

here is my syslog, i see in here stuff regarding eth1 and avahi but have no clue what it means.
```
Mar 23 07:28:45 ubuntu syslogd 1.4.1#20ubuntu4: restart.
Mar 23 07:28:45 ubuntu anacron[5019]: Job `cron.daily' terminated
Mar 23 07:30:01 ubuntu /USR/SBIN/CRON[6162]: (root) CMD (test -x /etc/init.d/anacron && /usr/sbin/invoke-rc.d anacron start >/dev/null)
Mar 23 07:30:32 ubuntu NetworkManager: <WARNING>^I nm_signal_handler (): Caught signal 15, shutting down normally. 
Mar 23 07:30:32 ubuntu NetworkManager: <information>^ICaught terminiation signal 
Mar 23 07:30:32 ubuntu NetworkManager: <debug info>^I[1174660232.787308] nm_print_open_socks (): Open Sockets List: 
Mar 23 07:30:32 ubuntu NetworkManager: <debug info>^I[1174660232.787333] nm_print_open_socks (): Open Sockets List Done. 
Mar 23 07:30:32 ubuntu NetworkManager: <information>^IDeactivating device eth1. 
Mar 23 07:30:32 ubuntu avahi-daemon[4542]: Withdrawing address record for 192.168.0.118 on eth1.
Mar 23 07:30:32 ubuntu avahi-daemon[4542]: Leaving mDNS multicast group on interface eth1.IPv4 with address 192.168.0.118.
Mar 23 07:30:32 ubuntu avahi-daemon[4542]: Interface eth1.IPv4 no longer relevant for mDNS.
Mar 23 07:30:32 ubuntu avahi-daemon[4542]: Withdrawing address record for fe80::213:ceff:fea3:8164 on eth1.
Mar 23 07:30:32 ubuntu NetworkManager: <information>^IDeactivating device eth0. 
Mar 23 07:30:32 ubuntu NetworkManager: <information>^Istarting... 
Mar 23 07:30:32 ubuntu NetworkManager: <information>^Ieth1: Device is fully-supported using driver 'ipw2200'. 
Mar 23 07:30:32 ubuntu NetworkManager: <information>^Inm_device_init(): waiting for device's worker thread to start 
Mar 23 07:30:32 ubuntu NetworkManager: <information>^Inm_device_init(): device's worker thread started, continuing. 
Mar 23 07:30:32 ubuntu NetworkManager: <information>^INow managing wireless (802.11) device 'eth1'. 
Mar 23 07:30:32 ubuntu NetworkManager: <information>^IDeactivating device eth1. 
Mar 23 07:30:32 ubuntu NetworkManager: <information>^Ieth0: Device is fully-supported using driver 'b44'. 
Mar 23 07:30:32 ubuntu NetworkManager: <information>^Inm_device_init(): waiting for device's worker thread to start 
Mar 23 07:30:33 ubuntu NetworkManager: <information>^Inm_device_init(): device's worker thread started, continuing. 
Mar 23 07:30:33 ubuntu NetworkManager: <information>^INow managing wired Ethernet (802.3) device 'eth0'. 
Mar 23 07:30:33 ubuntu NetworkManager: <information>^IDeactivating device eth0. 
Mar 23 07:30:33 ubuntu NetworkManager: <information>^IUpdating allowed wireless network lists. 
Mar 23 07:30:33 ubuntu NetworkManager: <WARNING>^I nm_dbus_get_networks_cb (): error received: org.freedesktop.NetworkManagerInfo.NoNetworks - There are no wireless networks stored.. 
Mar 23 07:30:52 ubuntu gconfd (root-6326): starting (version 2.18.0.1), pid 6326 user 'root'
Mar 23 07:30:52 ubuntu gconfd (root-6326): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Mar 23 07:30:52 ubuntu gconfd (root-6326): Resolved address "xml:readwrite:/root/.gconf" to a writable configuration source at position 1
Mar 23 07:30:52 ubuntu gconfd (root-6326): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Mar 23 07:30:52 ubuntu gconfd (root-6326): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
Mar 23 07:30:52 ubuntu gconfd (root-6326): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
Mar 23 07:31:06 ubuntu dhclient: There is already a pid file /var/run/dhclient.eth1.pid with pid 5660
Mar 23 07:31:06 ubuntu dhclient: killed old client process, removed PID file
Mar 23 07:31:06 ubuntu dhclient: Internet Systems Consortium DHCP Client V3.0.4
Mar 23 07:31:06 ubuntu dhclient: Copyright 2004-2006 Internet Systems Consortium.
Mar 23 07:31:06 ubuntu dhclient: All rights reserved.
Mar 23 07:31:06 ubuntu dhclient: For info, please visit http://www.isc.org/sw/dhcp/
Mar 23 07:31:06 ubuntu dhclient: 
Mar 23 07:31:06 ubuntu dhclient: Listening on LPF/eth1/00:13:ce:a3:81:64
Mar 23 07:31:06 ubuntu dhclient: Sending on   LPF/eth1/00:13:ce:a3:81:64
Mar 23 07:31:06 ubuntu dhclient: Sending on   Socket/fallback
Mar 23 07:31:06 ubuntu dhclient: DHCPRELEASE on eth1 to 192.168.0.1 port 67
Mar 23 07:31:06 ubuntu dhclient: send_packet: Network is unreachable
Mar 23 07:31:06 ubuntu dhclient: send_packet: please consult README file regarding broadcast address.
Mar 23 07:31:06 ubuntu avahi-autoipd(eth1)[6393]: Found user 'avahi-autoipd' (UID 104) and group 'avahi-autoipd' (GID 108).
Mar 23 07:31:06 ubuntu avahi-autoipd(eth1)[6393]: Successfully called chroot().
Mar 23 07:31:06 ubuntu avahi-autoipd(eth1)[6393]: Successfully dropped root privileges.
Mar 23 07:31:06 ubuntu avahi-autoipd(eth1)[6393]: fopen() failed: Permission denied
Mar 23 07:31:06 ubuntu avahi-autoipd(eth1)[6393]: Starting with address 169.254.7.145
Mar 23 07:31:11 ubuntu avahi-autoipd(eth1)[6393]: Callout BIND, address 169.254.7.145 on interface eth1
Mar 23 07:31:11 ubuntu avahi-daemon[4542]: Joining mDNS multicast group on interface eth1.IPv4 with address 169.254.7.145.
Mar 23 07:31:11 ubuntu avahi-daemon[4542]: New relevant interface eth1.IPv4 for mDNS.
Mar 23 07:31:11 ubuntu avahi-daemon[4542]: Registering new address record for 169.254.7.145 on eth1.IPv4.
Mar 23 07:31:15 ubuntu avahi-autoipd(eth1)[6393]: Successfully claimed IP address 169.254.7.145
Mar 23 07:31:15 ubuntu avahi-autoipd(eth1)[6393]: fopen() failed: Permission denied
Mar 23 07:31:15 ubuntu avahi-daemon[4542]: Interface eth1.IPv4 no longer relevant for mDNS.
Mar 23 07:31:15 ubuntu avahi-daemon[4542]: Leaving mDNS multicast group on interface eth1.IPv4 with address 169.254.7.145.
Mar 23 07:31:15 ubuntu avahi-autoipd(eth1)[6393]: SIOCSIFFLAGS failed: Permission denied
Mar 23 07:31:15 ubuntu avahi-autoipd(eth1)[6393]: Callout STOP, address 169.254.7.145 on interface eth1
Mar 23 07:31:15 ubuntu avahi-daemon[4542]: Withdrawing address record for 169.254.7.145 on eth1.
Mar 23 07:31:15 ubuntu avahi-autoipd(eth1)[6394]: client: RTNETLINK answers: No such process
Mar 23 07:31:15 ubuntu kernel: [  583.120000] ADDRCONF(NETDEV_UP): eth1: link is not ready
Mar 23 07:31:15 ubuntu dhclient: There is already a pid file /var/run/dhclient.eth1.pid with pid 134993416
Mar 23 07:31:15 ubuntu dhclient: Internet Systems Consortium DHCP Client V3.0.4
Mar 23 07:31:15 ubuntu dhclient: Copyright 2004-2006 Internet Systems Consortium.
Mar 23 07:31:15 ubuntu dhclient: All rights reserved.
Mar 23 07:31:15 ubuntu dhclient: For info, please visit http://www.isc.org/sw/dhcp/
Mar 23 07:31:15 ubuntu dhclient: 
Mar 23 07:31:16 ubuntu dhclient: Listening on LPF/eth1/00:13:ce:a3:81:64
Mar 23 07:31:16 ubuntu dhclient: Sending on   LPF/eth1/00:13:ce:a3:81:64
Mar 23 07:31:16 ubuntu dhclient: Sending on   Socket/fallback
Mar 23 07:31:17 ubuntu dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
Mar 23 07:31:24 ubuntu dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 9
Mar 23 07:31:33 ubuntu dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 15
Mar 23 07:31:48 ubuntu dhclient: No DHCPOFFERS received.
Mar 23 07:31:48 ubuntu dhclient: No working leases in persistent database - sleeping.
Mar 23 07:31:48 ubuntu avahi-autoipd(eth1)[6465]: Found user 'avahi-autoipd' (UID 104) and group 'avahi-autoipd' (GID 108).
Mar 23 07:31:48 ubuntu avahi-autoipd(eth1)[6465]: Successfully called chroot().
Mar 23 07:31:48 ubuntu avahi-autoipd(eth1)[6465]: Successfully dropped root privileges.
Mar 23 07:31:48 ubuntu avahi-autoipd(eth1)[6465]: fopen() failed: Permission denied
Mar 23 07:31:48 ubuntu avahi-autoipd(eth1)[6465]: Starting with address 169.254.7.145
Mar 23 07:31:53 ubuntu avahi-autoipd(eth1)[6465]: Callout BIND, address 169.254.7.145 on interface eth1
Mar 23 07:31:53 ubuntu avahi-daemon[4542]: Joining mDNS multicast group on interface eth1.IPv4 with address 169.254.7.145.
Mar 23 07:31:53 ubuntu avahi-daemon[4542]: New relevant interface eth1.IPv4 for mDNS.
Mar 23 07:31:53 ubuntu avahi-daemon[4542]: Registering new address record for 169.254.7.145 on eth1.IPv4.
Mar 23 07:31:57 ubuntu avahi-autoipd(eth1)[6465]: Successfully claimed IP address 169.254.7.145
Mar 23 07:31:57 ubuntu avahi-autoipd(eth1)[6465]: fopen() failed: Permission denied
Mar 23 07:32:11 ubuntu anacron[5019]: Job `cron.weekly' started
Mar 23 07:32:11 ubuntu anacron[6518]: Updated timestamp for job `cron.weekly' to 2007-03-23
Mar 23 07:32:13 ubuntu syslogd 1.4.1#20ubuntu4: restart.
Mar 23 07:32:13 ubuntu anacron[5019]: Job `cron.weekly' terminated
Mar 23 07:32:13 ubuntu anacron[5019]: Normal exit (2 jobs run)
Mar 23 07:32:15 ubuntu dhclient: There is already a pid file /var/run/dhclient.eth1.pid with pid 6474
Mar 23 07:32:15 ubuntu dhclient: killed old client process, removed PID file
Mar 23 07:32:15 ubuntu dhclient: Internet Systems Consortium DHCP Client V3.0.4
Mar 23 07:32:15 ubuntu dhclient: Copyright 2004-2006 Internet Systems Consortium.
Mar 23 07:32:15 ubuntu dhclient: All rights reserved.
Mar 23 07:32:15 ubuntu dhclient: For info, please visit http://www.isc.org/sw/dhcp/
Mar 23 07:32:15 ubuntu dhclient: 
Mar 23 07:32:15 ubuntu dhclient: Listening on LPF/eth1/00:13:ce:a3:81:64
Mar 23 07:32:15 ubuntu dhclient: Sending on   LPF/eth1/00:13:ce:a3:81:64
Mar 23 07:32:15 ubuntu dhclient: Sending on   Socket/fallback
Mar 23 07:32:15 ubuntu dhclient: DHCPRELEASE on eth1 to 192.168.0.1 port 67
Mar 23 07:32:16 ubuntu avahi-daemon[4542]: Interface eth1.IPv4 no longer relevant for mDNS.
Mar 23 07:32:16 ubuntu avahi-daemon[4542]: Leaving mDNS multicast group on interface eth1.IPv4 with address 169.254.7.145.
Mar 23 07:32:16 ubuntu avahi-autoipd(eth1)[6465]: SIOCSIFFLAGS failed: Permission denied
Mar 23 07:32:16 ubuntu avahi-autoipd(eth1)[6465]: Callout STOP, address 169.254.7.145 on interface eth1
Mar 23 07:32:16 ubuntu avahi-daemon[4542]: Withdrawing address record for 169.254.7.145 on eth1.
Mar 23 07:32:16 ubuntu avahi-autoipd(eth1)[6466]: client: RTNETLINK answers: No such process
Mar 23 07:32:16 ubuntu kernel: [  643.468000] ADDRCONF(NETDEV_UP): eth1: link is not ready
Mar 23 07:32:16 ubuntu dhclient: There is already a pid file /var/run/dhclient.eth1.pid with pid 134993416
Mar 23 07:32:16 ubuntu dhclient: Internet Systems Consortium DHCP Client V3.0.4
Mar 23 07:32:16 ubuntu dhclient: Copyright 2004-2006 Internet Systems Consortium.
Mar 23 07:32:16 ubuntu dhclient: All rights reserved.
Mar 23 07:32:16 ubuntu dhclient: For info, please visit http://www.isc.org/sw/dhcp/
Mar 23 07:32:16 ubuntu dhclient: 
Mar 23 07:32:17 ubuntu dhclient: Listening on LPF/eth1/00:13:ce:a3:81:64
Mar 23 07:32:17 ubuntu dhclient: Sending on   LPF/eth1/00:13:ce:a3:81:64
Mar 23 07:32:17 ubuntu dhclient: Sending on   Socket/fallback
Mar 23 07:32:17 ubuntu ntpdate[6500]: can't find host ntp.ubuntu.com 
Mar 23 07:32:17 ubuntu ntpdate[6500]: no servers can be used, exiting
Mar 23 07:32:17 ubuntu kernel: [  645.248000] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
Mar 23 07:32:18 ubuntu dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
Mar 23 07:32:18 ubuntu dhclient: DHCPOFFER from 192.168.0.1
Mar 23 07:32:18 ubuntu dhclient: DHCPREQUEST on eth1 to 255.255.255.255 port 67
Mar 23 07:32:18 ubuntu dhclient: DHCPACK from 192.168.0.1
Mar 23 07:32:18 ubuntu avahi-daemon[4542]: Joining mDNS multicast group on interface eth1.IPv4 with address 192.168.0.118.
Mar 23 07:32:18 ubuntu avahi-daemon[4542]: New relevant interface eth1.IPv4 for mDNS.
Mar 23 07:32:18 ubuntu avahi-daemon[4542]: Registering new address record for 192.168.0.118 on eth1.IPv4.
Mar 23 07:32:18 ubuntu dhclient: bound to 192.168.0.118 -- renewal in 34690 seconds.
Mar 23 07:32:19 ubuntu ntpdate[6778]: adjust time server 82.211.81.145 offset -0.027663 sec
Mar 23 07:32:19 ubuntu avahi-daemon[4542]: Registering new address record for fe80::213:ceff:fea3:8164 on eth1.*.
Mar 23 07:32:22 ubuntu gconfd (root-6326): GConf server is not in use, shutting down.
Mar 23 07:32:22 ubuntu gconfd (root-6326): Exiting
Mar 23 07:32:28 ubuntu kernel: [  656.100000] eth1: no IPv6 routers present
Mar 23 07:34:01 ubuntu gconfd (root-6834): starting (version 2.18.0.1), pid 6834 user 'root'
Mar 23 07:34:01 ubuntu gconfd (root-6834): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Mar 23 07:34:01 ubuntu gconfd (root-6834): Resolved address "xml:readwrite:/root/.gconf" to a writable configuration source at position 1
Mar 23 07:34:01 ubuntu gconfd (root-6834): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Mar 23 07:34:01 ubuntu gconfd (root-6834): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
Mar 23 07:34:01 ubuntu gconfd (root-6834): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
Mar 23 07:37:01 ubuntu gconfd (root-6834): GConf server is not in use, shutting down.
Mar 23 07:37:01 ubuntu gconfd (root-6834): Exiting
Mar 23 07:39:01 ubuntu /USR/SBIN/CRON[7026]: (root) CMD (  [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -r -0 rm)
```

---

### Post by Slapyo on 2007-03-23
do you want me to post that info when i don't have a connection as well?

```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth1
iface eth1 inet dhcp
	# wireless-* options are implemented by the wireless-tools package
	wireless-mode managed
	wireless-essid doots
```

---

### Post by ffxr on 2007-03-23
... your card seems to be at first picking up a strange ip address from DCHP...

maybe you could configure you card to use a static address? 

from what i can make out, it does seem to be a problem with DHCP.. 

i also know that the text based configuration done in that interface file can conflict with any settings in whatever network control applet your using.. so it might be worth experimenting with commenting out portions of the eth1 configuration in the interfaces file.. 

e.g
```

# The primary network interface
auto eth1
# iface eth1 inet dhcp
	# wireless-* options are implemented by the wireless-tools package
	wireless-mode managed
	wireless-essid doots 
```

btw, i do all my ip configuration in my interfaces file as i find network control gui's can be buggy...

---

### Post by Slapyo on 2007-03-23
if i comment out that line, nothing works.  in the device list, lo is gone.  no matter what i do i can't get the internet to work, even following the steps i need to take.

---

### Post by Slapyo on 2007-03-24
```

sudo /etc/init.d/networking restart

```

using that worked for me, soon as i ran it i was online.  how would i write a script to do this on start up for me?  or any ideas on how to fix the problem so i don't have to do this anymore?

here was the output:
```
Password:
 * Reconfiguring network interfaces...                                          There is already a pid file /var/run/dhclient.eth1.pid with pid 4462
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth1/00:13:ce:a3:81:64
Sending on   LPF/eth1/00:13:ce:a3:81:64
Sending on   Socket/fallback
DHCPRELEASE on eth1 to 192.168.0.1 port 67
send_packet: Network is unreachable
send_packet: please consult README file regarding broadcast address.
There is already a pid file /var/run/dhclient.eth1.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth1/00:13:ce:a3:81:64
Sending on   LPF/eth1/00:13:ce:a3:81:64
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 6
DHCPOFFER from 192.168.0.1
DHCPREQUEST on eth1 to 255.255.255.255 port 67
DHCPACK from 192.168.0.1
bound to 192.168.0.118 -- renewal in 33879 seconds.
                                                                         [ OK ]
```

---

### Post by Slapyo on 2007-03-26
kernel update to 2.6.20-13-386 ... had an nvidia driver update as well.  no problems there.  but network problem still exists.

---

