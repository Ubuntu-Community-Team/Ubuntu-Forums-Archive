---
title: "Router DHCP provides ip, Then no data can be sent through network card"
date: 2008-01-08
forum: Networking &amp; Wireless
---

### Post by phcyso on 2008-01-08
Hi there

My computer has a annoying issue where it gets the DHCP data from my router and then will not let me ping, access the internet or local network.

It appears that right after it connects, and gets the DHCP lease, data somehow fails to be sent down the network the light on it does not blink and the corresponding light on the router doesn't blink either.

Other computers work fine. my girlfriend has no issues using the wireless network and my windows partition(which i am using now) also has no issues.

It was working fine till a few days ago when this suddenly happened after booting the computer.
i do tend to hibernate the computer instead of a full shutdown so i do not know if that may have caused this though i have done MANY full shutdowns and reboots trying to resolve this

below is all the info i could think to grab from my system.
```

linux@linux-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0F:EA:8C:80:B4  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20f:eaff:fe8c:80b4/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:107 errors:0 dropped:0 overruns:0 frame:0
          TX packets:137 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:15628 (15.2 KB)  TX bytes:24795 (24.2 KB)
          Interrupt:16 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:6 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:340 (340.0 b)  TX bytes:340 (340.0 b)


linux@linux-desktop:~$ lspci|grep Ether
00:0a.0 Bridge: nVidia Corporation CK804 Ethernet Controller (rev a2)


linux@linux-desktop:~$ sudo dhclient eth0
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:0f:ea:8c:80:b4
Sending on   LPF/eth0/00:0f:ea:8c:80:b4
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
DHCPOFFER from 192.168.1.1
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 192.168.1.1
bound to 192.168.1.2 -- renewal in 35673 seconds.


linux@linux-desktop:~$ ping 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.

--- 192.168.1.1 ping statistics ---
301 packets transmitted, 0 received, 100% packet loss, time 300011ms

linux@linux-desktop:~$ lspci|grep Ether
00:0a.0 Bridge: nVidia Corporation CK804 Ethernet Controller (rev a2)


linux@linux-desktop:~$ sudo ifdown eth0
[sudo] password for linux:
ifdown: interface eth0 not configured

linux@linux-desktop:~$ sudo ifup eth0
Ignoring unknown interface eth0=eth0.

from messages log:


Jan  8 06:56:47 linux-desktop syslogd 1.4.1#21ubuntu3: restart.
Jan  8 06:56:47 linux-desktop anacron[5604]: Job `cron.daily' terminated (exit status: 1) (mailing output)
Jan  8 06:56:47 linux-desktop anacron[5604]: Can't find sendmail at /usr/sbin/sendmail, not mailing output
Jan  8 06:56:47 linux-desktop anacron[5604]: Normal exit (1 job run)
Jan  8 06:56:54 linux-desktop ntpdate[6235]: can't find host ntp.ubuntu.com 
Jan  8 06:56:54 linux-desktop ntpdate[6235]: no servers can be used, exiting
Jan  8 07:06:31 linux-desktop kernel: [  941.104000] eth0: link down.
Jan  8 07:06:31 linux-desktop NetworkManager: <info>  SWITCH: terminating current connection 'eth0' because it's no longer valid. 
Jan  8 07:06:31 linux-desktop NetworkManager: <info>  Deactivating device eth0. 
Jan  8 07:06:31 linux-desktop dhclient: There is already a pid file /var/run/dhclient.eth0.pid with pid 6168
Jan  8 07:06:31 linux-desktop dhclient: killed old client process, removed PID file
Jan  8 07:06:31 linux-desktop dhclient: DHCPRELEASE on eth0 to 192.168.1.1 port 67
Jan  8 07:06:32 linux-desktop avahi-daemon[5447]: Withdrawing address record for 192.168.1.2 on eth0.
Jan  8 07:06:32 linux-desktop avahi-daemon[5447]: Leaving mDNS multicast group on interface eth0.IPv4 with address 192.168.1.2.
Jan  8 07:06:32 linux-desktop avahi-daemon[5447]: Interface eth0.IPv4 no longer relevant for mDNS.
Jan  8 07:06:32 linux-desktop avahi-daemon[5447]: Withdrawing address record for fe80::20f:eaff:fe8c:80b4 on eth0.
Jan  8 07:06:32 linux-desktop NetworkManager: nm_device_is_802_3_ethernet: assertion `dev != NULL' failed
Jan  8 07:06:32 linux-desktop NetworkManager: nm_device_is_802_11_wireless: assertion `dev != NULL' failed
Jan  8 07:06:33 linux-desktop NetworkManager: <info>  Will activate wired connection 'eth0' because it now has a link. 
Jan  8 07:06:33 linux-desktop NetworkManager: <info>  SWITCH: no current connection, found better connection 'eth0'. 
Jan  8 07:06:33 linux-desktop NetworkManager: <info>  Will activate connection 'eth0'. 
Jan  8 07:06:33 linux-desktop NetworkManager: <info>  Device eth0 activation scheduled... 
Jan  8 07:06:33 linux-desktop NetworkManager: <info>  Activation (eth0) started... 
Jan  8 07:06:33 linux-desktop NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled... 
Jan  8 07:06:33 linux-desktop NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) started... 
Jan  8 07:06:33 linux-desktop NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) scheduled... 
Jan  8 07:06:33 linux-desktop NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) complete. 
Jan  8 07:06:33 linux-desktop NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) starting... 
Jan  8 07:06:33 linux-desktop NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) successful. 
Jan  8 07:06:33 linux-desktop NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled. 
Jan  8 07:06:33 linux-desktop NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) complete. 
Jan  8 07:06:33 linux-desktop NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) started... 
Jan  8 07:06:33 linux-desktop kernel: [  942.720000] eth0: link up.
Jan  8 07:06:33 linux-desktop kernel: [  942.720000] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
Jan  8 07:06:34 linux-desktop NetworkManager: <info>  Activation (eth0) Beginning DHCP transaction. 
Jan  8 07:06:34 linux-desktop dhclient: There is already a pid file /var/run/dhclient.eth0.pid with pid 134519120
Jan  8 07:06:34 linux-desktop NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) complete. 
Jan  8 07:06:34 linux-desktop NetworkManager: <info>  DHCP daemon state is now 12 (successfully started) for interface eth0 
Jan  8 07:06:34 linux-desktop avahi-daemon[5447]: Registering new address record for fe80::20f:eaff:fe8c:80b4 on eth0.*.
Jan  8 07:06:35 linux-desktop NetworkManager: <info>  DHCP daemon state is now 1 (starting) for interface eth0 
Jan  8 07:06:38 linux-desktop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
Jan  8 07:06:38 linux-desktop dhclient: DHCPOFFER from 192.168.1.1
Jan  8 07:06:38 linux-desktop dhclient: DHCPREQUEST on eth0 to 255.255.255.255 port 67
Jan  8 07:06:43 linux-desktop dhclient: DHCPREQUEST on eth0 to 255.255.255.255 port 67
Jan  8 07:06:43 linux-desktop dhclient: DHCPACK from 192.168.1.1
Jan  8 07:06:43 linux-desktop avahi-daemon[5447]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.1.2.
Jan  8 07:06:43 linux-desktop avahi-daemon[5447]: New relevant interface eth0.IPv4 for mDNS.
Jan  8 07:06:43 linux-desktop avahi-daemon[5447]: Registering new address record for 192.168.1.2 on eth0.IPv4.
Jan  8 07:06:43 linux-desktop NetworkManager: <info>  DHCP daemon state is now 2 (bound) for interface eth0 
Jan  8 07:06:43 linux-desktop NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Get) scheduled... 
Jan  8 07:06:43 linux-desktop dhclient: bound to 192.168.1.2 -- renewal in 37893 seconds.
Jan  8 07:06:43 linux-desktop NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Get) started... 
Jan  8 07:06:43 linux-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.host_name
Jan  8 07:06:43 linux-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_domain
Jan  8 07:06:43 linux-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_servers
Jan  8 07:06:43 linux-desktop NetworkManager: <info>  Retrieved the following IP4 configuration from the DHCP daemon: 
Jan  8 07:06:43 linux-desktop NetworkManager: <info>    address 192.168.1.2 
Jan  8 07:06:43 linux-desktop NetworkManager: <info>    netmask 255.255.255.0 
Jan  8 07:06:43 linux-desktop NetworkManager: <info>    broadcast 192.168.1.255 
Jan  8 07:06:43 linux-desktop NetworkManager: <info>    gateway 192.168.1.1 
Jan  8 07:06:43 linux-desktop NetworkManager: <info>    nameserver 192.168.1.1 
Jan  8 07:06:43 linux-desktop NetworkManager: <info>    domain name 'home' 
Jan  8 07:06:43 linux-desktop NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) scheduled... 
Jan  8 07:06:43 linux-desktop NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Get) complete. 
Jan  8 07:06:43 linux-desktop NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) started... 
Jan  8 07:06:43 linux-desktop avahi-daemon[5447]: Withdrawing address record for 192.168.1.2 on eth0.
Jan  8 07:06:43 linux-desktop avahi-daemon[5447]: Leaving mDNS multicast group on interface eth0.IPv4 with address 192.168.1.2.
Jan  8 07:06:43 linux-desktop avahi-daemon[5447]: Interface eth0.IPv4 no longer relevant for mDNS.
Jan  8 07:06:43 linux-desktop avahi-daemon[5447]: Withdrawing address record for fe80::20f:eaff:fe8c:80b4 on eth0.
Jan  8 07:06:43 linux-desktop avahi-daemon[5447]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.1.2.
Jan  8 07:06:43 linux-desktop avahi-daemon[5447]: New relevant interface eth0.IPv4 for mDNS.
Jan  8 07:06:43 linux-desktop avahi-daemon[5447]: Registering new address record for 192.168.1.2 on eth0.IPv4.
Jan  8 07:06:44 linux-desktop NetworkManager: <info>  Clearing nscd hosts cache. 
Jan  8 07:06:44 linux-desktop NetworkManager: <WARN>  nm_spawn_process(): nm_spawn_process('/usr/sbin/nscd -i hosts'): could not spawn process. (Failed to execute child process "/usr/sbin/nscd" (No such file or directory))  
Jan  8 07:06:44 linux-desktop NetworkManager: <info>  Activation (eth0) successful, device activated. 
Jan  8 07:06:44 linux-desktop NetworkManager: <info>  Activation (eth0) Finish handler scheduled. 
Jan  8 07:06:44 linux-desktop NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) complete. 
Jan  8 07:06:46 linux-desktop avahi-daemon[5447]: Registering new address record for fe80::20f:eaff:fe8c:80b4 on eth0.*.
Jan  8 07:06:55 linux-desktop kernel: [  964.256000] eth0: no IPv6 routers present
Jan  8 07:06:56 linux-desktop NetworkManager: <info>  Disconnected. 
Jan  8 07:06:56 linux-desktop dhclient: There is already a pid file /var/run/dhclient.eth0.pid with pid 6483
Jan  8 07:06:56 linux-desktop dhclient: killed old client process, removed PID file
Jan  8 07:06:56 linux-desktop avahi-daemon[5447]: Interface eth0.IPv4 no longer relevant for mDNS.
Jan  8 07:06:56 linux-desktop avahi-daemon[5447]: Leaving mDNS multicast group on interface eth0.IPv4 with address 192.168.1.2.
Jan  8 07:06:56 linux-desktop avahi-daemon[5447]: Withdrawing address record for fe80::20f:eaff:fe8c:80b4 on eth0.
Jan  8 07:06:56 linux-desktop avahi-daemon[5447]: Withdrawing address record for 192.168.1.2 on eth0.
Jan  8 07:06:56 linux-desktop dhclient: DHCPRELEASE on eth0 to 192.168.1.1 port 67
Jan  8 07:06:56 linux-desktop dhclient: send_packet: Network is unreachable
Jan  8 07:06:56 linux-desktop dhclient: send_packet: please consult README file regarding broadcast address.
Jan  8 07:06:56 linux-desktop NetworkManager: <info>  Will activate wired connection 'eth0' because it now has a link. 
Jan  8 07:06:57 linux-desktop avahi-daemon[5447]: Registering new address record for fe80::20f:eaff:fe8c:80b4 on eth0.*.
Jan  8 07:06:58 linux-desktop NetworkManager: <info>  Enabling networking. 
Jan  8 07:06:58 linux-desktop NetworkManager: <info>  Deactivating device eth0. 
Jan  8 07:06:58 linux-desktop avahi-daemon[5447]: Withdrawing address record for fe80::20f:eaff:fe8c:80b4 on eth0.
Jan  8 07:06:58 linux-desktop NetworkManager: <info>  eth0: Device is fully-supported using driver 'forcedeth'. 
Jan  8 07:06:58 linux-desktop NetworkManager: <info>  nm_device_init(): waiting for device's worker thread to start 
Jan  8 07:06:58 linux-desktop NetworkManager: <info>  nm_device_init(): device's worker thread started, continuing. 
Jan  8 07:06:58 linux-desktop NetworkManager: <info>  Now managing wired Ethernet (802.3) device 'eth0'. 
Jan  8 07:06:58 linux-desktop NetworkManager: <info>  Deactivating device eth0. 
Jan  8 07:06:58 linux-desktop NetworkManager: <info>  Will activate wired connection 'eth0' because it now has a link. 
Jan  8 07:06:58 linux-desktop NetworkManager: <info>  SWITCH: no current connection, found better connection 'eth0'. 
Jan  8 07:06:58 linux-desktop NetworkManager: <info>  Will activate connection 'eth0'. 
Jan  8 07:06:58 linux-desktop NetworkManager: <info>  Device eth0 activation scheduled... 
Jan  8 07:06:58 linux-desktop NetworkManager: <info>  Activation (eth0) started... 
Jan  8 07:06:58 linux-desktop NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled... 
Jan  8 07:06:58 linux-desktop NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) started... 
Jan  8 07:06:58 linux-desktop NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) scheduled... 
Jan  8 07:06:58 linux-desktop NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) complete. 
Jan  8 07:06:58 linux-desktop NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) starting... 
Jan  8 07:06:58 linux-desktop NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) successful. 
Jan  8 07:06:58 linux-desktop NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled. 
Jan  8 07:06:58 linux-desktop NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) complete. 
Jan  8 07:06:58 linux-desktop NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) started... 
Jan  8 07:06:59 linux-desktop ntpdate[6545]: can't find host ntp.ubuntu.com 
Jan  8 07:06:59 linux-desktop ntpdate[6545]: no servers can be used, exiting
Jan  8 07:06:59 linux-desktop NetworkManager: <info>  Activation (eth0) Beginning DHCP transaction. 
Jan  8 07:06:59 linux-desktop dhclient: There is already a pid file /var/run/dhclient.eth0.pid with pid 134519120
Jan  8 07:06:59 linux-desktop NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) complete. 
Jan  8 07:06:59 linux-desktop NetworkManager: <info>  DHCP daemon state is now 12 (successfully started) for interface eth0 
Jan  8 07:07:00 linux-desktop NetworkManager: <info>  DHCP daemon state is now 1 (starting) for interface eth0 
Jan  8 07:07:03 linux-desktop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
Jan  8 07:07:03 linux-desktop dhclient: DHCPOFFER from 192.168.1.1
Jan  8 07:07:03 linux-desktop dhclient: DHCPREQUEST on eth0 to 255.255.255.255 port 67
Jan  8 07:07:08 linux-desktop dhclient: DHCPREQUEST on eth0 to 255.255.255.255 port 67
Jan  8 07:07:08 linux-desktop dhclient: DHCPACK from 192.168.1.1
Jan  8 07:07:08 linux-desktop avahi-daemon[5447]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.1.2.
Jan  8 07:07:08 linux-desktop avahi-daemon[5447]: New relevant interface eth0.IPv4 for mDNS.
Jan  8 07:07:08 linux-desktop avahi-daemon[5447]: Registering new address record for 192.168.1.2 on eth0.IPv4.
Jan  8 07:07:08 linux-desktop dhclient: bound to 192.168.1.2 -- renewal in 37442 seconds.
Jan  8 07:07:08 linux-desktop NetworkManager: <info>  DHCP daemon state is now 2 (bound) for interface eth0 
Jan  8 07:07:08 linux-desktop NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Get) scheduled... 
Jan  8 07:07:08 linux-desktop NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Get) started... 
Jan  8 07:07:08 linux-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.host_name
Jan  8 07:07:08 linux-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_domain
Jan  8 07:07:08 linux-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_servers
Jan  8 07:07:08 linux-desktop NetworkManager: <info>  Retrieved the following IP4 configuration from the DHCP daemon: 
Jan  8 07:07:08 linux-desktop NetworkManager: <info>    address 192.168.1.2 
Jan  8 07:07:08 linux-desktop NetworkManager: <info>    netmask 255.255.255.0 
Jan  8 07:07:08 linux-desktop NetworkManager: <info>    broadcast 192.168.1.255 
Jan  8 07:07:08 linux-desktop NetworkManager: <info>    gateway 192.168.1.1 
Jan  8 07:07:08 linux-desktop NetworkManager: <info>    nameserver 192.168.1.1 
Jan  8 07:07:08 linux-desktop NetworkManager: <info>    domain name 'home' 
Jan  8 07:07:08 linux-desktop NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) scheduled... 
Jan  8 07:07:08 linux-desktop NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Get) complete. 
Jan  8 07:07:08 linux-desktop NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) started... 
Jan  8 07:07:08 linux-desktop avahi-daemon[5447]: Withdrawing address record for 192.168.1.2 on eth0.
Jan  8 07:07:08 linux-desktop avahi-daemon[5447]: Leaving mDNS multicast group on interface eth0.IPv4 with address 192.168.1.2.
Jan  8 07:07:08 linux-desktop avahi-daemon[5447]: Interface eth0.IPv4 no longer relevant for mDNS.
Jan  8 07:07:08 linux-desktop avahi-daemon[5447]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.1.2.
Jan  8 07:07:08 linux-desktop avahi-daemon[5447]: New relevant interface eth0.IPv4 for mDNS.
Jan  8 07:07:08 linux-desktop avahi-daemon[5447]: Registering new address record for 192.168.1.2 on eth0.IPv4.
Jan  8 07:07:09 linux-desktop NetworkManager: <info>  Clearing nscd hosts cache. 
Jan  8 07:07:09 linux-desktop NetworkManager: <WARN>  nm_spawn_process(): nm_spawn_process('/usr/sbin/nscd -i hosts'): could not spawn process. (Failed to execute child process "/usr/sbin/nscd" (No such file or directory))  
Jan  8 07:07:09 linux-desktop NetworkManager: <info>  Activation (eth0) Finish handler scheduled. 
Jan  8 07:07:09 linux-desktop NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) complete. 
Jan  8 07:07:09 linux-desktop NetworkManager: <info>  Activation (eth0) successful, device activated. 
Jan  8 07:07:10 linux-desktop avahi-daemon[5447]: Registering new address record for fe80::20f:eaff:fe8c:80b4 on eth0.*.
Jan  8 07:07:19 linux-desktop kernel: [  988.920000] eth0: no IPv6 routers present
Jan  8 07:07:29 linux-desktop ntpdate[6658]: can't find host ntp.ubuntu.com 
Jan  8 07:07:29 linux-desktop ntpdate[6658]: no servers can be used, exiting
Jan  8 07:17:01 linux-desktop /USR/SBIN/CRON[7282]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jan  8 07:30:01 linux-desktop /USR/SBIN/CRON[7893]: (root) CMD (test -x /etc/init.d/anacron && /usr/sbin/invoke-rc.d anacron start >/dev/null)
Jan  8 07:30:01 linux-desktop anacron[7917]: Anacron 2.3 started on 2008-01-08
Jan  8 07:30:01 linux-desktop anacron[7917]: Normal exit (0 jobs run)
Jan  8 07:36:31 linux-desktop dhcdbd: Unrequested down ?:3
Jan  8 07:36:31 linux-desktop NetworkManager: <info>  DHCP daemon state is now 14 (normal exit) for interface eth0 
Jan  8 07:36:31 linux-desktop avahi-daemon[5447]: Interface eth0.IPv4 no longer relevant for mDNS.
Jan  8 07:36:31 linux-desktop avahi-daemon[5447]: Leaving mDNS multicast group on interface eth0.IPv4 with address 192.168.1.2.
Jan  8 07:36:31 linux-desktop avahi-daemon[5447]: Withdrawing address record for fe80::20f:eaff:fe8c:80b4 on eth0.
Jan  8 07:36:31 linux-desktop avahi-daemon[5447]: Withdrawing address record for 192.168.1.2 on eth0.
Jan  8 07:36:31 linux-desktop NetworkManager: <info>  SWITCH: terminating current connection 'eth0' because it's no longer valid. 
Jan  8 07:36:31 linux-desktop NetworkManager: <info>  Deactivating device eth0. 
Jan  8 07:36:31 linux-desktop NetworkManager: nm_device_is_802_3_ethernet: assertion `dev != NULL' failed
Jan  8 07:36:31 linux-desktop NetworkManager: nm_device_is_802_11_wireless: assertion `dev != NULL' failed
Jan  8 07:36:31 linux-desktop NetworkManager: <debug> [1199730991.478939] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/net_00_0f_ea_8c_80_b4'). 
Jan  8 07:36:31 linux-desktop NetworkManager: <info>  Deactivating device eth0. 
Jan  8 07:36:31 linux-desktop kernel: [ 2740.756000] ACPI: PCI interrupt for device 0000:00:0a.0 disabled
Jan  8 07:36:33 linux-desktop kernel: [ 2742.964000] PM: suspend-to-disk mode set to 'shutdown'

```

I hope someone has some ideas about what may have caused this.

Thank you

---

### Post by phcyso on 2008-01-08
Just wanted to bump this up a little. 

hopefully someone has seen a issue like this before.

---

