---
title: "Wirleless loses connection every 12 min"
date: 2008-08-19
forum: Networking &amp; Wireless
---

### Post by bluester on 2008-08-19
I installed Ubuntu 8.04 months ago.
I recently installed an application that allows me to keep system time via the internet. Now my wireless connection appears to loose connectivity every 12 minutes. I am not sure what is going on....

I installed the latest updates
My system is a Satellite A205-S5825
I am using Madwifi version 3366 and WICD

I have not changed the configuration and my /var/log/syslog is as follows:

 


Aug 19 16:39:33 linux-laptop syslogd 1.5.0#1ubuntu1: restart.
Aug 19 16:39:33 linux-laptop anacron[5389]: Job `cron.daily' terminated
Aug 19 16:39:33 linux-laptop anacron[5389]: Normal exit (1 job run)
Aug 19 16:59:27 linux-laptop kernel: [ 3175.179744] cdrom: This disc doesn't have any tracks I recognize!
Aug 19 17:17:01 linux-laptop /USR/SBIN/CRON[6860]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Aug 19 17:27:12 linux-laptop -- MARK --
Aug 19 17:47:12 linux-laptop -- MARK --
Aug 19 18:07:12 linux-laptop -- MARK --
Aug 19 18:17:01 linux-laptop /USR/SBIN/CRON[6900]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Aug 19 18:27:12 linux-laptop -- MARK --
Aug 19 18:47:12 linux-laptop -- MARK --
Aug 19 19:07:12 linux-laptop -- MARK --
Aug 19 19:14:05 linux-laptop avahi-daemon[5016]: Interface ath0.IPv4 no longer relevant for mDNS.
Aug 19 19:14:05 linux-laptop avahi-daemon[5016]: Leaving mDNS multicast group on interface ath0.IPv4 with address 192.168.0.176.
Aug 19 19:14:05 linux-laptop dhclient: receive_packet failed on ath0: Network is down
Aug 19 19:14:05 linux-laptop avahi-daemon[5016]: Withdrawing address record for fe80::21f:e1ff:fe01:b15c on ath0.
Aug 19 19:14:05 linux-laptop avahi-daemon[5016]: Withdrawing address record for 192.168.0.176 on ath0.
Aug 19 19:14:05 linux-laptop kernel: [11249.449946] ADDRCONF(NETDEV_UP): ath0: link is not ready
Aug 19 19:14:05 linux-laptop kernel: [11249.629588] ADDRCONF(NETDEV_UP): ath0: link is not ready
Aug 19 19:14:05 linux-laptop kernel: [11249.640689] ADDRCONF(NETDEV_CHANGE): ath0: link becomes ready
Aug 19 19:14:05 linux-laptop dhclient: There is already a pid file /var/run/dhclient.pid with pid 6350
Aug 19 19:14:05 linux-laptop dhclient: removed stale PID file
Aug 19 19:14:05 linux-laptop dhclient: Internet Systems Consortium DHCP Client V3.0.6
Aug 19 19:14:05 linux-laptop dhclient: Copyright 2004-2007 Internet Systems Consortium.
Aug 19 19:14:05 linux-laptop dhclient: All rights reserved.
Aug 19 19:14:05 linux-laptop dhclient: For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)
Aug 19 19:14:05 linux-laptop dhclient: 
Aug 19 19:14:05 linux-laptop dhclient: wifi0: unknown hardware address type 801
Aug 19 19:14:06 linux-laptop dhclient: wifi0: unknown hardware address type 801
Aug 19 19:14:06 linux-laptop dhclient: Listening on LPF/ath0/00:1f:e1:01:b1:5c
Aug 19 19:14:06 linux-laptop dhclient: Sending on   LPF/ath0/00:1f:e1:01:b1:5c
Aug 19 19:14:06 linux-laptop dhclient: Sending on   Socket/fallback
Aug 19 19:14:06 linux-laptop avahi-daemon[5016]: Registering new address record for fe80::21f:e1ff:fe01:b15c on ath0.*.
Aug 19 19:14:08 linux-laptop ntpd[6049]: Deleting interface #7 ath0, 192.168.0.176#123, interface stats: received=0, sent=0, dropped=0, active_time=10800 secs
Aug 19 19:14:10 linux-laptop dhclient: DHCPREQUEST of 192.168.0.176 on ath0 to 255.255.255.255 port 67
Aug 19 19:14:15 linux-laptop kernel: [11260.092443] ath0: no IPv6 routers present
Aug 19 19:14:17 linux-laptop dhclient: DHCPREQUEST of 192.168.0.176 on ath0 to 255.255.255.255 port 67
Aug 19 19:14:24 linux-laptop dhclient: DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 3
Aug 19 19:14:24 linux-laptop dhclient: DHCPOFFER of 192.168.0.176 from 192.168.0.1
Aug 19 19:14:24 linux-laptop dhclient: DHCPREQUEST of 192.168.0.176 on ath0 to 255.255.255.255 port 67
Aug 19 19:14:24 linux-laptop dhclient: DHCPACK of 192.168.0.176 from 192.168.0.1
Aug 19 19:14:24 linux-laptop avahi-daemon[5016]: Joining mDNS multicast group on interface ath0.IPv4 with address 192.168.0.176.
Aug 19 19:14:24 linux-laptop avahi-daemon[5016]: New relevant interface ath0.IPv4 for mDNS.
Aug 19 19:14:24 linux-laptop avahi-daemon[5016]: Registering new address record for 192.168.0.176 on ath0.IPv4.
Aug 19 19:14:24 linux-laptop dhclient: bound to 192.168.0.176 -- renewal in 42709 seconds.
Aug 19 19:17:01 linux-laptop /USR/SBIN/CRON[7874]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Aug 19 19:19:08 linux-laptop ntpd[6049]: Listening on interface #8 ath0, 192.168.0.176#123 Enabled
Aug 19 19:30:55 linux-laptop avahi-daemon[5016]: Interface ath0.IPv4 no longer relevant for mDNS.
Aug 19 19:30:55 linux-laptop avahi-daemon[5016]: Leaving mDNS multicast group on interface ath0.IPv4 with address 192.168.0.176.
Aug 19 19:30:55 linux-laptop dhclient: receive_packet failed on ath0: Network is down
Aug 19 19:30:55 linux-laptop avahi-daemon[5016]: Withdrawing address record for fe80::21f:e1ff:fe01:b15c on ath0.
Aug 19 19:30:55 linux-laptop avahi-daemon[5016]: Withdrawing address record for 192.168.0.176 on ath0.
Aug 19 19:30:55 linux-laptop kernel: [12259.435280] ADDRCONF(NETDEV_UP): ath0: link is not ready
Aug 19 19:30:55 linux-laptop kernel: [12259.638864] ADDRCONF(NETDEV_UP): ath0: link is not ready
Aug 19 19:30:55 linux-laptop kernel: [12259.642417] ADDRCONF(NETDEV_CHANGE): ath0: link becomes ready
Aug 19 19:30:55 linux-laptop dhclient: There is already a pid file /var/run/dhclient.pid with pid 7606
Aug 19 19:30:55 linux-laptop dhclient: removed stale PID file
Aug 19 19:30:55 linux-laptop dhclient: Internet Systems Consortium DHCP Client V3.0.6
Aug 19 19:30:55 linux-laptop dhclient: Copyright 2004-2007 Internet Systems Consortium.
Aug 19 19:30:55 linux-laptop dhclient: All rights reserved.
Aug 19 19:30:55 linux-laptop dhclient: For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)
Aug 19 19:30:55 linux-laptop dhclient: 
Aug 19 19:30:55 linux-laptop dhclient: wifi0: unknown hardware address type 801
Aug 19 19:30:56 linux-laptop dhclient: wifi0: unknown hardware address type 801
Aug 19 19:30:56 linux-laptop avahi-daemon[5016]: Registering new address record for fe80::21f:e1ff:fe01:b15c on ath0.*.
Aug 19 19:30:56 linux-laptop dhclient: Listening on LPF/ath0/00:1f:e1:01:b1:5c
Aug 19 19:30:56 linux-laptop dhclient: Sending on   LPF/ath0/00:1f:e1:01:b1:5c
Aug 19 19:30:56 linux-laptop dhclient: Sending on   Socket/fallback
Aug 19 19:30:56 linux-laptop dhclient: DHCPREQUEST of 192.168.0.176 on ath0 to 255.255.255.255 port 67
Aug 19 19:31:01 linux-laptop dhclient: DHCPREQUEST of 192.168.0.176 on ath0 to 255.255.255.255 port 67
Aug 19 19:31:05 linux-laptop kernel: [12269.725918] ath0: no IPv6 routers present
Aug 19 19:31:07 linux-laptop dhclient: DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 7
Aug 19 19:31:14 linux-laptop dhclient: DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 10
Aug 19 19:31:24 linux-laptop dhclient: DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 14
Aug 19 19:31:24 linux-laptop dhclient: DHCPOFFER of 192.168.0.176 from 192.168.0.1
Aug 19 19:31:24 linux-laptop dhclient: DHCPREQUEST of 192.168.0.176 on ath0 to 255.255.255.255 port 67
Aug 19 19:31:24 linux-laptop dhclient: DHCPACK of 192.168.0.176 from 192.168.0.1
Aug 19 19:31:24 linux-laptop avahi-daemon[5016]: Joining mDNS multicast group on interface ath0.IPv4 with address 192.168.0.176.
Aug 19 19:31:24 linux-laptop avahi-daemon[5016]: New relevant interface ath0.IPv4 for mDNS.
Aug 19 19:31:24 linux-laptop avahi-daemon[5016]: Registering new address record for 192.168.0.176 on ath0.IPv4.
Aug 19 19:31:24 linux-laptop dhclient: bound to 192.168.0.176 -- renewal in 38341 seconds.
Aug 19 19:37:18 linux-laptop avahi-daemon[5016]: Interface ath0.IPv4 no longer relevant for mDNS.
Aug 19 19:37:18 linux-laptop avahi-daemon[5016]: Leaving mDNS multicast group on interface ath0.IPv4 with address 192.168.0.176.
Aug 19 19:37:19 linux-laptop dhclient: receive_packet failed on ath0: Network is down
Aug 19 19:37:19 linux-laptop avahi-daemon[5016]: Withdrawing address record for fe80::21f:e1ff:fe01:b15c on ath0.
Aug 19 19:37:19 linux-laptop avahi-daemon[5016]: Withdrawing address record for 192.168.0.176 on ath0.
Aug 19 19:37:19 linux-laptop kernel: [12642.780916] ADDRCONF(NETDEV_UP): ath0: link is not ready
Aug 19 19:37:19 linux-laptop kernel: [12642.886960] ADDRCONF(NETDEV_UP): ath0: link is not ready
Aug 19 19:37:19 linux-laptop dhclient: There is already a pid file /var/run/dhclient.pid with pid 13290
Aug 19 19:37:19 linux-laptop dhclient: removed stale PID file
Aug 19 19:37:19 linux-laptop dhclient: Internet Systems Consortium DHCP Client V3.0.6
Aug 19 19:37:19 linux-laptop dhclient: Copyright 2004-2007 Internet Systems Consortium.
Aug 19 19:37:19 linux-laptop dhclient: All rights reserved.
Aug 19 19:37:19 linux-laptop dhclient: For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)
Aug 19 19:37:19 linux-laptop dhclient: 
Aug 19 19:37:19 linux-laptop dhclient: wifi0: unknown hardware address type 801
Aug 19 19:37:20 linux-laptop dhclient: wifi0: unknown hardware address type 801
Aug 19 19:37:20 linux-laptop dhclient: Listening on LPF/ath0/00:1f:e1:01:b1:5c
Aug 19 19:37:20 linux-laptop dhclient: Sending on   LPF/ath0/00:1f:e1:01:b1:5c
Aug 19 19:37:20 linux-laptop dhclient: Sending on   Socket/fallback
Aug 19 19:37:21 linux-laptop kernel: [12645.749281] ADDRCONF(NETDEV_CHANGE): ath0: link becomes ready
Aug 19 19:37:23 linux-laptop dhclient: DHCPREQUEST of 192.168.0.176 on ath0 to 255.255.255.255 port 67
Aug 19 19:37:23 linux-laptop dhclient: DHCPACK of 192.168.0.176 from 192.168.0.1
Aug 19 19:37:23 linux-laptop avahi-daemon[5016]: Joining mDNS multicast group on interface ath0.IPv4 with address 192.168.0.176.
Aug 19 19:37:23 linux-laptop avahi-daemon[5016]: New relevant interface ath0.IPv4 for mDNS.
Aug 19 19:37:23 linux-laptop avahi-daemon[5016]: Registering new address record for 192.168.0.176 on ath0.IPv4.
Aug 19 19:37:23 linux-laptop dhclient: bound to 192.168.0.176 -- renewal in 39436 seconds.
Aug 19 19:37:23 linux-laptop avahi-daemon[5016]: Registering new address record for fe80::21f:e1ff:fe01:b15c on ath0.*.
Aug 19 19:37:32 linux-laptop kernel: [12656.663078] ath0: no IPv6 routers present
Aug 19 19:54:53 linux-laptop avahi-daemon[5016]: Interface ath0.IPv4 no longer relevant for mDNS.
Aug 19 19:54:53 linux-laptop avahi-daemon[5016]: Leaving mDNS multicast group on interface ath0.IPv4 with address 192.168.0.176.
Aug 19 19:54:53 linux-laptop dhclient: receive_packet failed on ath0: Network is down
Aug 19 19:54:53 linux-laptop avahi-daemon[5016]: Withdrawing address record for fe80::21f:e1ff:fe01:b15c on ath0.
Aug 19 19:54:53 linux-laptop avahi-daemon[5016]: Withdrawing address record for 192.168.0.176 on ath0.
Aug 19 19:54:53 linux-laptop kernel: [13697.144756] ADDRCONF(NETDEV_UP): ath0: link is not ready
Aug 19 19:54:53 linux-laptop kernel: [13697.277660] ADDRCONF(NETDEV_UP): ath0: link is not ready
Aug 19 19:54:54 linux-laptop dhclient: There is already a pid file /var/run/dhclient.pid with pid 22839
Aug 19 19:54:54 linux-laptop dhclient: removed stale PID file
Aug 19 19:54:54 linux-laptop dhclient: Internet Systems Consortium DHCP Client V3.0.6
Aug 19 19:54:54 linux-laptop dhclient: Copyright 2004-2007 Internet Systems Consortium.
Aug 19 19:54:54 linux-laptop dhclient: All rights reserved.
Aug 19 19:54:54 linux-laptop dhclient: For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)
Aug 19 19:54:54 linux-laptop dhclient: 
Aug 19 19:54:54 linux-laptop dhclient: wifi0: unknown hardware address type 801
Aug 19 19:54:55 linux-laptop dhclient: wifi0: unknown hardware address type 801
Aug 19 19:54:55 linux-laptop dhclient: Listening on LPF/ath0/00:1f:e1:01:b1:5c
Aug 19 19:54:55 linux-laptop dhclient: Sending on   LPF/ath0/00:1f:e1:01:b1:5c
Aug 19 19:54:55 linux-laptop dhclient: Sending on   Socket/fallback
Aug 19 19:54:55 linux-laptop dhclient: DHCPREQUEST of 192.168.0.176 on ath0 to 255.255.255.255 port 67
Aug 19 19:54:56 linux-laptop kernel: [13699.964978] ADDRCONF(NETDEV_CHANGE): ath0: link becomes ready
Aug 19 19:54:57 linux-laptop avahi-daemon[5016]: Registering new address record for fe80::21f:e1ff:fe01:b15c on ath0.*.
Aug 19 19:55:00 linux-laptop dhclient: DHCPREQUEST of 192.168.0.176 on ath0 to 255.255.255.255 port 67
Aug 19 19:55:00 linux-laptop dhclient: DHCPACK of 192.168.0.176 from 192.168.0.1
Aug 19 19:55:00 linux-laptop avahi-daemon[5016]: Joining mDNS multicast group on interface ath0.IPv4 with address 192.168.0.176.
Aug 19 19:55:00 linux-laptop avahi-daemon[5016]: New relevant interface ath0.IPv4 for mDNS.
Aug 19 19:55:00 linux-laptop avahi-daemon[5016]: Registering new address record for 192.168.0.176 on ath0.IPv4.
Aug 19 19:55:00 linux-laptop dhclient: bound to 192.168.0.176 -- renewal in 32640 seconds.
Aug 19 19:55:06 linux-laptop kernel: [13710.032457] ath0: no IPv6 routers present

---

### Post by dmizer on 2008-08-20
How many computers and devices (including printers and NAS storage devices) are on your network?  What IP address does each device have? Is everything set for DHCP? What router are you using?

This is not likely to be a problem with Ubuntu even if the problem did not occur in Windows.

---

### Post by cariboo on 2008-08-20
If you disable the system time application, does it work normally?

Jim

---

### Post by dmizer on 2008-08-20
From the log, it doesn't appear to have anything to do with NTP.  Here's the record for when NTP becomes active:
```
Aug 19 19:19:08 linux-laptop ntpd[6049]: Listening on interface #8 ath0, 192.168.0.176#123 Enabled
```
Heres the record for when the ath0 interface drops:
```
Aug 19 19:30:55 linux-laptop avahi-daemon[5016]: Interface ath0.IPv4 no longer relevant for mDNS.
```
As you can see, they are several minutes apart.

The second and third references here:
```
Aug 19 19:37:18 linux-laptop avahi-daemon[5016]: Interface ath0.IPv4 no longer relevant for mDNS.
[snip]
Aug 19 19:54:53 linux-laptop avahi-daemon[5016]: Interface ath0.IPv4 no longer relevant for mDNS.
```
Are not prefaced by a query to the NTP server by any number of minutes at all.

To confirm this, you should check for references of ntpd in /var/log/daemon.log

---

### Post by bluester on 2008-08-20
> **dmizer said:**
> How many computers and devices (including printers and NAS storage devices) are on your network?
Three computers and one printer (all wireless):

Compaq - 
HP - 
Toshiba - 
HP Wireless printer - Photosmart - C4385  

> **dmizer said:**
> What IP address does each device have?

Printer - 192.168.0.104
Compaq - 192.168.0.112
HP - 192.168.0.162
Toshiba 192.168.0.176


> **dmizer said:**
> Is everything set for DHCP?

Yes


> **dmizer said:**
> What router are you using?
D-Link AirPlus Extreme DI-724U

SSID Broadcast - Disabled
Channel - Fixed
Super G Mode - Disabled
Transmission Rate - Auto
802.11g only mode - Disabled
Security Mode - WPA-PSK




> **dmizer said:**
> This is not likely to be a problem with Ubuntu even if the problem did not occur in Windows.

Perhaps, as the Windows system do not seem to be having this issue.

---

### Post by bluester on 2008-08-22
Any other thoughts?

---

### Post by bluester on 2008-08-22
I found some threads that may have solved my problem...

[http://ubuntuforums.org/showthread.php?t=684495](http://ubuntuforums.org/showthread.php?t=684495)
Which lead me to here:
Does your madwifi connection keep dropping??? Possible solution -- [http://ubuntuforums.org/showthread.php?t=540101](http://ubuntuforums.org/showthread.php?t=540101) = Author robnz/tranalbert

The latter thread suggested when using Madwifi drivers, the user should enable the 802.11g mode only.

I will report my results in an hour!

Edit: This worked!!!!

Thanks!

---

### Post by bluester on 2008-08-23
I take it back....

This was only a temporary fix. 
The connection last longer, but it still disconnects after a period of time...

Oh well!

---

### Post by dmizer on 2008-08-23
I know it seems silly, but have you tried rebooting the router?

---

### Post by bluester on 2008-08-23
> **dmizer said:**
> I know it seems silly, but have you tried rebooting the router?

Actually, it is not silly at all!
I rebooted the router several times - soft boot and power off (unplug).
I want to say it is the machine, however, I know Toshiba would ask me to troubleshoot via MS software, which is not on my system.

I am totally blown away as it worked two weeks ago and I changed nothing.
Now, my system show connected via Wicd, stays connected for 10 - 20 minutes, and then looses its connectivity. However, Wicd still shows I am connected; yet, Web sites do not load and I cannot ping any address.... Frustrating!!!!!:confused: :mad:

I edited the /etc/rc.local as instructed here: [http://ubuntuforums.org/showpost.php?p=3421545&postcount=4](http://ubuntuforums.org/showpost.php?p=3421545&postcount=4)

The only change, I stay connected longer (10 - 30 min).

---

### Post by dmizer on 2008-08-23
Well, the software you installed for the clock is related to the ntpd daemon. If you would like to test, you can disable this temporarily with the following command:
```
sudo /etc/init.d/ntpd stop
```
But I'm pretty sure that this is not your problem.  Again, you can look at the daemon logs in /var/log to remove all doubt.

What chipset do you have?  If you don't know, please post the output of:
```
sudo lshw -C network
```

---

### Post by bluester on 2008-08-23
> **dmizer said:**
> Well, the software you installed for the clock is related to the ntpd daemon. If you would like to test, you can disable this temporarily with the following command:
```
sudo /etc/init.d/ntpd stop
```
But I'm pretty sure that this is not your problem.  Again, you can look at the daemon logs in /var/log to remove all doubt.

What chipset do you have?  If you don't know, please post the output of:
```
sudo lshw -C network
```

 *-network               
       description: Ethernet interface
       product: RTL8101E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 01
       serial: 00:1e:ec:35:53:15
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.2LK duplex=half latency=0 link=no module=r8169 multicast=yes port=twisted pair
  *-network
       description: Wireless interface
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: wifi0
       version: 01
       serial: 00:1f:e1:01:b1:5c
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath_pci ip=192.168.0.176 latency=0 module=ath_pci multicast=yes wireless=IEEE 802.11g

---

### Post by bluester on 2008-08-27
Well, Apparently after all the changes and rebooting the router (actually shutting it down for an hour and shutting my system down for an hour), I am able to stay connected.

Weird! :confused:

---

### Post by bballa23523 on 2008-08-27
[http://sikh.myminicity.com/](http://sikh.myminicity.com/)

---

### Post by bluester on 2008-10-16
After many weeks of research I believe I narrowed my issue down to power management.
I set my system to not idle and my system to go to sleep after 59 minutes of inactivity.
My connection is sometimes lost after 59 minutes of inactivity.
I am not sure how I can further test this as when my system was losing connectivity the system went idle after 11 minutes of inactivity - 
let us say I was watching Heroes on [www.hulu.com](www.hulu.com)
If I had the power management to idle, I would lose connectivity after 11 minutes and moving the mouse would keep my screen from going blank, but shortly thereafter, I would somehow need to re-establish my connection.

Currently - I must launch Wicd, click on network and choose hidden network;
type in my hidden network (set not to broadcast), and my network name appears on the list (side note: the status bar reports I am still connected and gives me a percentage, usually 60 - 78 percent) - however, the network connection is re-established as I am able to use Firefox without error. This by far is the strangest behavior of a system to date.
I cannot explain what the deal is and it is only happening with my Linux system. :confused:

---

