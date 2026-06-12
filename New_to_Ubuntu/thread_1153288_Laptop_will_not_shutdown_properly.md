---
title: "Laptop will not shutdown properly"
date: 2009-05-08
forum: New to Ubuntu
---

### Post by slughappy1 on 2009-05-08
It actually will not shutdown at all. When I tell it to shutdown it goes to a blank screen with a cursor. I can type stuff, but nothing happens.  I can go to different terminals, i.e. F1, and I can log back in. When I shutdown from there I get the same problem. I found out that when shutting down I get the following error 
```
Killing all remaining processes         [fail]
```
I also get these errors when I plug and unplug the power cord. I can do it forever and they wont stop
```
stopping anac(h)ronistic cron anacron
startinging anac(h)ronistic cron anacron
```


Oh, and I am running Ubuntu 9.04 64-bit.

---

### Post by aysiu on 2009-05-08
[This](http://forums.debian.net/viewtopic.php?f=10&t=23701) may help you.

---

### Post by slughappy1 on 2009-05-09
Well that didn't really help. I changed GDM theme, but did nothing. Here is my /var/log/daemon.log. Also, if needed [here]("http://slughappy.com/files/laptop") is what is on my laptop.
```
May  8 00:48:37 Barnaby console-kit-daemon[2786]: GLib-GObject-WARNING: IA__g_object_get_valist: value location for `gchararray' passed as NULL 
May  8 00:48:37 Barnaby last message repeated 2 times
May  8 00:48:37 Barnaby init: tty4 main process (2582) killed by TERM signal
May  8 00:48:37 Barnaby init: tty5 main process (2583) killed by TERM signal
May  8 00:48:37 Barnaby init: tty2 main process (2588) killed by TERM signal
May  8 00:48:37 Barnaby init: tty3 main process (2589) killed by TERM signal
May  8 00:48:37 Barnaby init: tty6 main process (2590) killed by TERM signal
May  8 00:48:37 Barnaby init: tty1 main process (3323) killed by TERM signal
May  8 00:48:37 Barnaby console-kit-daemon[2786]: GLib-GObject-WARNING: IA__g_object_get_valist: value location for `gchararray' passed as NULL 
May  8 00:48:37 Barnaby console-kit-daemon[2786]: GLib-GObject-WARNING: IA__g_object_get_valist: value location for `gchararray' passed as NULL 
May  8 00:48:43 Barnaby bluetoothd[2965]: bridge pan0 removed
May  8 00:48:43 Barnaby bluetoothd[2965]: Stopping SDP server
May  8 00:48:43 Barnaby bluetoothd[2965]: Exit
May  8 00:52:23 Barnaby acpid: client connected from 3007[105:106] 
May  8 00:52:23 Barnaby bluetoothd[3035]: Bluetooth daemon
May  8 00:52:23 Barnaby bluetoothd[3035]: Starting SDP server
May  8 00:52:23 Barnaby bluetoothd[3035]: Starting experimental netlink support
May  8 00:52:23 Barnaby bluetoothd[3035]: Failed to find Bluetooth netlink family
May  8 00:52:23 Barnaby bluetoothd[3035]: Registered interface org.bluez.Service on path /org/bluez/3035/any
May  8 00:52:23 Barnaby bluetoothd[3035]: bridge pan0 created
May  8 00:52:24 Barnaby acpid: client connected from 3076[0:0] 
May  8 00:52:24 Barnaby NetworkManager: <info>  starting... 
May  8 00:52:24 Barnaby NetworkManager: <info>  Found radio killswitch /org/freedesktop/Hal/devices/pci_8086_4222_rfkill_3945ABG_wlan 
May  8 00:52:24 Barnaby NetworkManager: <info>  Found radio killswitch /org/freedesktop/Hal/devices/dell_wlan_switch 
May  8 00:52:24 Barnaby avahi-daemon[3121]: Found user 'avahi' (UID 108) and group 'avahi' (GID 114).
May  8 00:52:24 Barnaby avahi-daemon[3121]: Successfully dropped root privileges.
May  8 00:52:24 Barnaby avahi-daemon[3121]: avahi-daemon 0.6.23 starting up.
May  8 00:52:24 Barnaby avahi-daemon[3121]: Successfully called chroot().
May  8 00:52:24 Barnaby avahi-daemon[3121]: Successfully dropped remaining capabilities.
May  8 00:52:24 Barnaby NetworkManager: <info>  (eth0): new Ethernet device (driver: 'tg3') 
May  8 00:52:24 Barnaby NetworkManager: <info>  (eth0): exported as /org/freedesktop/Hal/devices/net_00_1c_23_fd_72_6c 
May  8 00:52:24 Barnaby avahi-daemon[3121]: No service file found in /etc/avahi/services.
May  8 00:52:24 Barnaby avahi-daemon[3121]: Network interface enumeration completed.
May  8 00:52:24 Barnaby avahi-daemon[3121]: Registering HINFO record with values 'X86_64'/'LINUX'.
May  8 00:52:24 Barnaby avahi-daemon[3121]: Server startup complete. Host name is Barnaby.local. Local service cookie is 2807198854.
May  8 00:52:24 Barnaby NetworkManager: <info>  (wlan0): driver supports SSID scans (scan_capa 0x01). 
May  8 00:52:24 Barnaby NetworkManager: <info>  (wlan0): new 802.11 WiFi device (driver: 'iwl3945') 
May  8 00:52:24 Barnaby NetworkManager: <info>  (wlan0): exported as /org/freedesktop/Hal/devices/net_00_1c_bf_96_f1_aa 
May  8 00:52:24 Barnaby NetworkManager: <info>  Trying to start the supplicant... 
May  8 00:52:24 Barnaby NetworkManager: <info>  Trying to start the system settings daemon... 
May  8 00:52:24 Barnaby nm-system-settings:    SCPlugin-Ifupdown: init!
May  8 00:52:24 Barnaby nm-system-settings:    SCPlugin-Ifupdown: update_system_hostname
May  8 00:52:24 Barnaby nm-system-settings:    SCPluginIfupdown: management mode: unmanaged
May  8 00:52:24 Barnaby nm-system-settings:    SCPlugin-Ifupdown: device added (udi: /org/freedesktop/Hal/devices/net_00_1c_23_fd_72_6c, iface: eth0): not well known
May  8 00:52:24 Barnaby nm-system-settings:    SCPlugin-Ifupdown: device added (udi: /org/freedesktop/Hal/devices/net_00_1c_bf_96_f1_aa, iface: wlan0): not well known
May  8 00:52:24 Barnaby nm-system-settings:    SCPlugin-Ifupdown: end _init.
May  8 00:52:24 Barnaby nm-system-settings: Loaded plugin ifupdown: (C) 2008 Canonical Ltd.  To report bugs please use the NetworkManager mailing list.
May  8 00:52:24 Barnaby nm-system-settings: Loaded plugin keyfile: (c) 2007 - 2008 Red Hat, Inc.  To report bugs please use the NetworkManager mailing list.
May  8 00:52:24 Barnaby nm-system-settings:    SCPlugin-Ifupdown: (15884752) ... get_connections.
May  8 00:52:24 Barnaby nm-system-settings:    SCPlugin-Ifupdown: (15884752) ... get_connections (managed=false): return empty list.
May  8 00:52:24 Barnaby nm-system-settings:    Ifupdown: get unmanaged devices count: 0
May  8 00:52:24 Barnaby NetworkManager: <info>  (wlan0): supplicant manager state:  down -> idle 
May  8 00:52:29 Barnaby NetworkManager: <info>  (eth0): device state change: 1 -> 2 
May  8 00:52:29 Barnaby NetworkManager: <info>  (eth0): bringing up device. 
May  8 00:52:29 Barnaby nm-system-settings: Added default wired connection 'Auto eth0' for /org/freedesktop/Hal/devices/net_00_1c_23_fd_72_6c
May  8 00:52:29 Barnaby NetworkManager: <info>  (eth0): preparing device. 
May  8 00:52:29 Barnaby NetworkManager: <info>  (eth0): deactivating device (reason: 2). 
May  8 00:52:29 Barnaby NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889) 
May  8 00:52:29 Barnaby NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889) 
May  8 00:52:29 Barnaby NetworkManager: <info>  (wlan0): device state change: 1 -> 2 
May  8 00:52:29 Barnaby NetworkManager: <info>  (wlan0): bringing up device. 
May  8 00:52:29 Barnaby NetworkManager: <info>  (wlan0): preparing device. 
May  8 00:52:29 Barnaby NetworkManager: <info>  (wlan0): deactivating device (reason: 2). 
May  8 00:52:29 Barnaby NetworkManager: <info>  (wlan0): device state change: 2 -> 3 
May  8 00:52:29 Barnaby NetworkManager: <info>  (wlan0): supplicant interface state:  starting -> ready 
May  8 00:52:30 Barnaby NetworkManager: <info>  (eth0): carrier now ON (device state 2) 
May  8 00:52:30 Barnaby NetworkManager: <info>  (eth0): device state change: 2 -> 3 
May  8 00:52:30 Barnaby NetworkManager: <info>  Activation (eth0) starting connection 'Auto eth0' 
May  8 00:52:30 Barnaby NetworkManager: <info>  (eth0): device state change: 3 -> 4 
May  8 00:52:30 Barnaby NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled... 
May  8 00:52:30 Barnaby NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) started... 
May  8 00:52:30 Barnaby NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) scheduled... 
May  8 00:52:30 Barnaby NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) complete. 
May  8 00:52:30 Barnaby NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) starting... 
May  8 00:52:30 Barnaby NetworkManager: <info>  (eth0): device state change: 4 -> 5 
May  8 00:52:30 Barnaby NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) successful. 
May  8 00:52:30 Barnaby NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled. 
May  8 00:52:30 Barnaby NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) complete. 
May  8 00:52:30 Barnaby NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) started... 
May  8 00:52:30 Barnaby NetworkManager: <info>  (eth0): device state change: 5 -> 7 
May  8 00:52:30 Barnaby NetworkManager: <info>  Activation (eth0) Beginning DHCP transaction. 
May  8 00:52:30 Barnaby NetworkManager: <info>  dhclient started with pid 3446 
May  8 00:52:30 Barnaby NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) complete. 
May  8 00:52:30 Barnaby dhclient: Internet Systems Consortium DHCP Client V3.1.1
May  8 00:52:30 Barnaby dhclient: Copyright 2004-2008 Internet Systems Consortium.
May  8 00:52:30 Barnaby dhclient: All rights reserved.
May  8 00:52:30 Barnaby dhclient: For info, please visit http://www.isc.org/sw/dhcp/
May  8 00:52:30 Barnaby dhclient: 
May  8 00:52:30 Barnaby dhclient: wmaster0: unknown hardware address type 801
May  8 00:52:30 Barnaby NetworkManager: <info>  DHCP: device eth0 state changed (null) -> preinit 
May  8 00:52:30 Barnaby dhclient: wmaster0: unknown hardware address type 801
May  8 00:52:30 Barnaby dhclient: Listening on LPF/eth0/00:1c:23:fd:72:6c
May  8 00:52:30 Barnaby dhclient: Sending on   LPF/eth0/00:1c:23:fd:72:6c
May  8 00:52:30 Barnaby dhclient: Sending on   Socket/fallback
May  8 00:52:32 Barnaby avahi-daemon[3121]: Registering new address record for fe80::21c:23ff:fefd:726c on eth0.*.
May  8 00:52:33 Barnaby dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
May  8 00:52:33 Barnaby dhclient: DHCPOFFER of 192.168.1.101 from 192.168.1.1
May  8 00:52:33 Barnaby dhclient: DHCPREQUEST of 192.168.1.101 on eth0 to 255.255.255.255 port 67
May  8 00:52:33 Barnaby dhclient: DHCPACK of 192.168.1.101 from 192.168.1.1
May  8 00:52:34 Barnaby NetworkManager: <info>  DHCP: device eth0 state changed preinit -> bound 
May  8 00:52:34 Barnaby NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Get) scheduled... 
May  8 00:52:34 Barnaby NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Get) started... 
May  8 00:52:34 Barnaby NetworkManager: <info>    address 192.168.1.101 
May  8 00:52:34 Barnaby NetworkManager: <info>    prefix 24 (255.255.255.0) 
May  8 00:52:34 Barnaby NetworkManager: <info>    gateway 192.168.1.1 
May  8 00:52:34 Barnaby NetworkManager: <info>    hostname 'Barnaby' 
May  8 00:52:34 Barnaby NetworkManager: <info>    nameserver '68.87.85.98' 
May  8 00:52:34 Barnaby NetworkManager: <info>    nameserver '68.87.69.146' 
May  8 00:52:34 Barnaby NetworkManager: <info>    nameserver '68.87.78.130' 
May  8 00:52:34 Barnaby NetworkManager: <info>    domain name 'hsd1.ut.comcast.net.' 
May  8 00:52:34 Barnaby NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) scheduled... 
May  8 00:52:34 Barnaby NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Get) complete. 
May  8 00:52:34 Barnaby NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) started... 
May  8 00:52:34 Barnaby avahi-daemon[3121]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.1.101.
May  8 00:52:34 Barnaby avahi-daemon[3121]: New relevant interface eth0.IPv4 for mDNS.
May  8 00:52:34 Barnaby avahi-daemon[3121]: Registering new address record for 192.168.1.101 on eth0.IPv4.
May  8 00:52:34 Barnaby dhclient: bound to 192.168.1.101 -- renewal in 41457 seconds.
May  8 00:52:35 Barnaby NetworkManager: <info>  (eth0): device state change: 7 -> 8 
May  8 00:52:35 Barnaby NetworkManager: <info>  Policy set 'Auto eth0' (eth0) as default for routing and DNS. 
May  8 00:52:35 Barnaby NetworkManager: <info>  Activation (eth0) successful, device activated. 
May  8 00:52:35 Barnaby NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) complete. 
May  8 00:52:36 Barnaby ntpdate[3515]: adjust time server 91.189.94.4 offset -0.127694 sec
May  8 00:53:15 Barnaby console-kit-daemon[2851]: WARNING: Couldn't read /proc/2850/environ: Failed to open file '/proc/2850/environ': No such file or directory 
May  8 00:53:30 Barnaby hald: mounted /dev/sdb1 on behalf of uid 1000
May  8 01:39:56 Barnaby hald: unmounted /dev/sdb1 from '/media/SWEET2' on behalf of uid 1000
May  8 01:41:20 Barnaby hald: mounted /dev/sdb1 on behalf of uid 1000
May  8 01:41:33 Barnaby hald: unmounted /dev/sdb1 from '/media/SWEET' on behalf of uid 1000
May  8 01:42:40 Barnaby init: tty2 main process (2654) killed by TERM signal
May  8 01:42:40 Barnaby init: tty6 main process (2657) killed by TERM signal
May  8 01:42:40 Barnaby init: tty3 main process (2656) killed by TERM signal
May  8 01:42:40 Barnaby init: tty4 main process (2647) killed by TERM signal
May  8 01:42:40 Barnaby init: tty5 main process (2648) killed by TERM signal
May  8 01:42:40 Barnaby init: tty1 main process (3407) killed by TERM signal
May  8 01:42:47 Barnaby bluetoothd[3035]: bridge pan0 removed
May  8 01:42:47 Barnaby bluetoothd[3035]: Stopping SDP server
May  8 01:42:47 Barnaby bluetoothd[3035]: Exit
May  8 02:26:44 Barnaby acpid: client connected from 2942[105:106] 
May  8 02:26:44 Barnaby bluetoothd[2969]: Bluetooth daemon
May  8 02:26:44 Barnaby bluetoothd[2969]: Starting SDP server
May  8 02:26:44 Barnaby bluetoothd[2969]: Starting experimental netlink support
May  8 02:26:44 Barnaby bluetoothd[2969]: Failed to find Bluetooth netlink family
May  8 02:26:44 Barnaby bluetoothd[2969]: Registered interface org.bluez.Service on path /org/bluez/2969/any
May  8 02:26:44 Barnaby bluetoothd[2969]: bridge pan0 created
May  8 02:26:45 Barnaby acpid: client connected from 3010[0:0] 
May  8 02:26:46 Barnaby NetworkManager: <info>  starting... 
May  8 02:26:46 Barnaby avahi-daemon[3054]: Found user 'avahi' (UID 108) and group 'avahi' (GID 114).
May  8 02:26:46 Barnaby avahi-daemon[3054]: Successfully dropped root privileges.
May  8 02:26:46 Barnaby avahi-daemon[3054]: avahi-daemon 0.6.23 starting up.
May  8 02:26:46 Barnaby avahi-daemon[3054]: Successfully called chroot().
May  8 02:26:46 Barnaby avahi-daemon[3054]: Successfully dropped remaining capabilities.
May  8 02:26:46 Barnaby NetworkManager: <info>  Found radio killswitch /org/freedesktop/Hal/devices/pci_8086_4222_rfkill_3945ABG_wlan 
May  8 02:26:46 Barnaby NetworkManager: <info>  Found radio killswitch /org/freedesktop/Hal/devices/dell_wlan_switch 
May  8 02:26:46 Barnaby NetworkManager: <info>  (eth0): new Ethernet device (driver: 'tg3') 
May  8 02:26:46 Barnaby NetworkManager: <info>  (eth0): exported as /org/freedesktop/Hal/devices/net_00_1c_23_fd_72_6c 
May  8 02:26:46 Barnaby avahi-daemon[3054]: No service file found in /etc/avahi/services.
May  8 02:26:46 Barnaby avahi-daemon[3054]: Network interface enumeration completed.
May  8 02:26:46 Barnaby avahi-daemon[3054]: Registering HINFO record with values 'X86_64'/'LINUX'.
May  8 02:26:46 Barnaby avahi-daemon[3054]: Server startup complete. Host name is Barnaby.local. Local service cookie is 257355476.
May  8 02:26:46 Barnaby NetworkManager: <info>  (wlan0): driver supports SSID scans (scan_capa 0x01). 
May  8 02:26:46 Barnaby NetworkManager: <info>  (wlan0): new 802.11 WiFi device (driver: 'iwl3945') 
May  8 02:26:46 Barnaby NetworkManager: <info>  (wlan0): exported as /org/freedesktop/Hal/devices/net_00_1c_bf_96_f1_aa 
May  8 02:26:46 Barnaby NetworkManager: <info>  Trying to start the supplicant... 
May  8 02:26:46 Barnaby NetworkManager: <info>  Trying to start the system settings daemon... 
May  8 02:26:46 Barnaby nm-system-settings:    SCPlugin-Ifupdown: init!
May  8 02:26:46 Barnaby nm-system-settings:    SCPlugin-Ifupdown: update_system_hostname
May  8 02:26:46 Barnaby nm-system-settings:    SCPluginIfupdown: management mode: unmanaged
May  8 02:26:46 Barnaby nm-system-settings:    SCPlugin-Ifupdown: device added (udi: /org/freedesktop/Hal/devices/net_00_1c_23_fd_72_6c, iface: eth0): not well known
May  8 02:26:46 Barnaby nm-system-settings:    SCPlugin-Ifupdown: device added (udi: /org/freedesktop/Hal/devices/net_00_1c_bf_96_f1_aa, iface: wlan0): not well known
May  8 02:26:46 Barnaby nm-system-settings:    SCPlugin-Ifupdown: end _init.
May  8 02:26:46 Barnaby nm-system-settings: Loaded plugin ifupdown: (C) 2008 Canonical Ltd.  To report bugs please use the NetworkManager mailing list.
May  8 02:26:46 Barnaby nm-system-settings: Loaded plugin keyfile: (c) 2007 - 2008 Red Hat, Inc.  To report bugs please use the NetworkManager mailing list.
May  8 02:26:46 Barnaby nm-system-settings:    SCPlugin-Ifupdown: (14029264) ... get_connections.
May  8 02:26:46 Barnaby nm-system-settings:    SCPlugin-Ifupdown: (14029264) ... get_connections (managed=false): return empty list.
May  8 02:26:46 Barnaby nm-system-settings:    Ifupdown: get unmanaged devices count: 0
May  8 02:26:46 Barnaby NetworkManager: <info>  (wlan0): supplicant manager state:  down -> idle 
May  8 02:26:50 Barnaby NetworkManager: <info>  (eth0): device state change: 1 -> 2 
May  8 02:26:50 Barnaby NetworkManager: <info>  (eth0): bringing up device. 
May  8 02:26:50 Barnaby nm-system-settings: Added default wired connection 'Auto eth0' for /org/freedesktop/Hal/devices/net_00_1c_23_fd_72_6c
May  8 02:26:50 Barnaby NetworkManager: <info>  (eth0): preparing device. 
May  8 02:26:50 Barnaby NetworkManager: <info>  (eth0): deactivating device (reason: 2). 
May  8 02:26:50 Barnaby NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889) 
May  8 02:26:50 Barnaby NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889) 
May  8 02:26:50 Barnaby NetworkManager: <info>  (wlan0): device state change: 1 -> 2 
May  8 02:26:50 Barnaby NetworkManager: <info>  (wlan0): bringing up device. 
May  8 02:26:50 Barnaby NetworkManager: <info>  (wlan0): preparing device. 
May  8 02:26:50 Barnaby NetworkManager: <info>  (wlan0): deactivating device (reason: 2). 
May  8 02:26:50 Barnaby NetworkManager: <info>  (wlan0): device state change: 2 -> 3 
May  8 02:26:50 Barnaby NetworkManager: <info>  (wlan0): supplicant interface state:  starting -> ready 
May  8 02:26:51 Barnaby NetworkManager: <info>  (eth0): carrier now ON (device state 2) 
May  8 02:26:51 Barnaby NetworkManager: <info>  (eth0): device state change: 2 -> 3 
May  8 02:26:51 Barnaby NetworkManager: <info>  Activation (eth0) starting connection 'Auto eth0' 
May  8 02:26:51 Barnaby NetworkManager: <info>  (eth0): device state change: 3 -> 4 
May  8 02:26:51 Barnaby NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled... 
May  8 02:26:51 Barnaby NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) started... 
May  8 02:26:51 Barnaby NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) scheduled... 
May  8 02:26:51 Barnaby NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) complete. 
May  8 02:26:51 Barnaby NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) starting... 
May  8 02:26:51 Barnaby NetworkManager: <info>  (eth0): device state change: 4 -> 5 
May  8 02:26:51 Barnaby NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) successful. 
May  8 02:26:51 Barnaby NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled. 
May  8 02:26:51 Barnaby NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) complete. 
May  8 02:26:51 Barnaby NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) started... 
May  8 02:26:51 Barnaby NetworkManager: <info>  (eth0): device state change: 5 -> 7 
May  8 02:26:51 Barnaby NetworkManager: <info>  Activation (eth0) Beginning DHCP transaction. 
May  8 02:26:51 Barnaby NetworkManager: <info>  dhclient started with pid 3369 
May  8 02:26:51 Barnaby NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) complete. 
May  8 02:26:51 Barnaby dhclient: Internet Systems Consortium DHCP Client V3.1.1
May  8 02:26:51 Barnaby dhclient: Copyright 2004-2008 Internet Systems Consortium.
May  8 02:26:51 Barnaby dhclient: All rights reserved.
May  8 02:26:51 Barnaby dhclient: For info, please visit http://www.isc.org/sw/dhcp/
May  8 02:26:51 Barnaby dhclient: 
May  8 02:26:51 Barnaby dhclient: wmaster0: unknown hardware address type 801
May  8 02:26:51 Barnaby dhclient: wmaster0: unknown hardware address type 801
May  8 02:26:51 Barnaby NetworkManager: <info>  DHCP: device eth0 state changed (null) -> preinit 
May  8 02:26:51 Barnaby dhclient: Listening on LPF/eth0/00:1c:23:fd:72:6c
May  8 02:26:51 Barnaby dhclient: Sending on   LPF/eth0/00:1c:23:fd:72:6c
May  8 02:26:51 Barnaby dhclient: Sending on   Socket/fallback
May  8 02:26:52 Barnaby dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
May  8 02:26:53 Barnaby dhclient: DHCPOFFER of 192.168.1.101 from 192.168.1.1
May  8 02:26:53 Barnaby dhclient: DHCPREQUEST of 192.168.1.101 on eth0 to 255.255.255.255 port 67
May  8 02:26:53 Barnaby dhclient: DHCPACK of 192.168.1.101 from 192.168.1.1
May  8 02:26:53 Barnaby NetworkManager: <info>  DHCP: device eth0 state changed preinit -> bound 
May  8 02:26:53 Barnaby NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Get) scheduled... 
May  8 02:26:53 Barnaby NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Get) started... 
May  8 02:26:53 Barnaby NetworkManager: <info>    address 192.168.1.101 
May  8 02:26:53 Barnaby NetworkManager: <info>    prefix 24 (255.255.255.0) 
May  8 02:26:53 Barnaby NetworkManager: <info>    gateway 192.168.1.1 
May  8 02:26:53 Barnaby NetworkManager: <info>    hostname 'Barnaby' 
May  8 02:26:53 Barnaby NetworkManager: <info>    nameserver '68.87.85.98' 
May  8 02:26:53 Barnaby NetworkManager: <info>    nameserver '68.87.69.146' 
May  8 02:26:53 Barnaby NetworkManager: <info>    nameserver '68.87.78.130' 
May  8 02:26:53 Barnaby NetworkManager: <info>    domain name 'hsd1.ut.comcast.net.' 
May  8 02:26:53 Barnaby NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) scheduled... 
May  8 02:26:53 Barnaby NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Get) complete. 
May  8 02:26:53 Barnaby NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) started... 
May  8 02:26:53 Barnaby avahi-daemon[3054]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.1.101.
May  8 02:26:53 Barnaby avahi-daemon[3054]: New relevant interface eth0.IPv4 for mDNS.
May  8 02:26:53 Barnaby avahi-daemon[3054]: Registering new address record for 192.168.1.101 on eth0.IPv4.
May  8 02:26:53 Barnaby dhclient: bound to 192.168.1.101 -- renewal in 33780 seconds.
May  8 02:26:53 Barnaby avahi-daemon[3054]: Registering new address record for fe80::21c:23ff:fefd:726c on eth0.*.
May  8 02:26:54 Barnaby NetworkManager: <info>  (eth0): device state change: 7 -> 8 
May  8 02:26:54 Barnaby NetworkManager: <info>  Policy set 'Auto eth0' (eth0) as default for routing and DNS. 
May  8 02:26:54 Barnaby NetworkManager: <info>  Activation (eth0) successful, device activated. 
May  8 02:26:54 Barnaby NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) complete. 
May  8 02:26:55 Barnaby ntpdate[3438]: adjust time server 91.189.94.4 offset 0.116154 sec
May  8 02:27:00 Barnaby console-kit-daemon[2789]: WARNING: Couldn't read /proc/2788/environ: Failed to open file '/proc/2788/environ': No such file or directory 
May  8 03:05:47 Barnaby console-kit-daemon[2789]: GLib-GObject-WARNING: IA__g_object_get_valist: value location for `gchararray' passed as NULL 
May  8 03:05:47 Barnaby last message repeated 2 times
May  8 03:05:47 Barnaby init: tty3 main process (2594) killed by TERM signal
May  8 03:05:47 Barnaby init: tty1 main process (3331) killed by TERM signal
May  8 03:05:47 Barnaby init: tty2 main process (2593) killed by TERM signal
May  8 03:05:47 Barnaby init: tty5 main process (2586) killed by TERM signal
May  8 03:05:47 Barnaby init: tty4 main process (2585) killed by TERM signal
May  8 03:05:47 Barnaby init: tty6 main process (2595) killed by TERM signal
May  8 03:05:47 Barnaby console-kit-daemon[2789]: GLib-GObject-WARNING: IA__g_object_get_valist: value location for `gchararray' passed as NULL 
May  8 03:05:47 Barnaby console-kit-daemon[2789]: GLib-GObject-WARNING: IA__g_object_get_valist: value location for `gchararray' passed as NULL 
May  8 03:05:54 Barnaby bluetoothd[2969]: bridge pan0 removed
May  8 03:05:54 Barnaby bluetoothd[2969]: Stopping SDP server
May  8 03:05:54 Barnaby bluetoothd[2969]: Exit
May  8 03:06:57 Barnaby acpid: client connected from 2940[105:106] 
May  8 03:06:58 Barnaby bluetoothd[2966]: Bluetooth daemon
May  8 03:06:58 Barnaby bluetoothd[2966]: Starting SDP server
May  8 03:06:58 Barnaby bluetoothd[2966]: Starting experimental netlink support
May  8 03:06:58 Barnaby bluetoothd[2966]: Failed to find Bluetooth netlink family
May  8 03:06:58 Barnaby bluetoothd[2966]: Registered interface org.bluez.Service on path /org/bluez/2966/any
May  8 03:06:58 Barnaby bluetoothd[2966]: bridge pan0 created
May  8 03:06:59 Barnaby acpid: client connected from 3007[0:0] 
May  8 03:06:59 Barnaby NetworkManager: <info>  starting... 
May  8 03:06:59 Barnaby avahi-daemon[3052]: Found user 'avahi' (UID 108) and group 'avahi' (GID 114).
May  8 03:06:59 Barnaby avahi-daemon[3052]: Successfully dropped root privileges.
May  8 03:06:59 Barnaby avahi-daemon[3052]: avahi-daemon 0.6.23 starting up.
May  8 03:06:59 Barnaby avahi-daemon[3052]: Successfully called chroot().
May  8 03:06:59 Barnaby avahi-daemon[3052]: Successfully dropped remaining capabilities.
May  8 03:06:59 Barnaby NetworkManager: <info>  Found radio killswitch /org/freedesktop/Hal/devices/pci_8086_4222_rfkill_3945ABG_wlan 
May  8 03:06:59 Barnaby NetworkManager: <info>  Found radio killswitch /org/freedesktop/Hal/devices/dell_wlan_switch 
May  8 03:06:59 Barnaby NetworkManager: <info>  (eth0): new Ethernet device (driver: 'tg3') 
May  8 03:06:59 Barnaby NetworkManager: <info>  (eth0): exported as /org/freedesktop/Hal/devices/net_00_1c_23_fd_72_6c 
May  8 03:06:59 Barnaby avahi-daemon[3052]: No service file found in /etc/avahi/services.
May  8 03:06:59 Barnaby avahi-daemon[3052]: Network interface enumeration completed.
May  8 03:06:59 Barnaby avahi-daemon[3052]: Registering HINFO record with values 'X86_64'/'LINUX'.
May  8 03:06:59 Barnaby avahi-daemon[3052]: Server startup complete. Host name is Barnaby.local. Local service cookie is 1500450704.
May  8 03:06:59 Barnaby NetworkManager: <info>  (wlan0): driver supports SSID scans (scan_capa 0x01). 
May  8 03:06:59 Barnaby NetworkManager: <info>  (wlan0): new 802.11 WiFi device (driver: 'iwl3945') 
May  8 03:06:59 Barnaby NetworkManager: <info>  (wlan0): exported as /org/freedesktop/Hal/devices/net_00_1c_bf_96_f1_aa 
May  8 03:06:59 Barnaby NetworkManager: <info>  Trying to start the supplicant... 
May  8 03:06:59 Barnaby NetworkManager: <info>  Trying to start the system settings daemon... 
May  8 03:06:59 Barnaby nm-system-settings:    SCPlugin-Ifupdown: init!
May  8 03:06:59 Barnaby nm-system-settings:    SCPlugin-Ifupdown: update_system_hostname
May  8 03:06:59 Barnaby nm-system-settings:    SCPluginIfupdown: management mode: unmanaged
May  8 03:06:59 Barnaby nm-system-settings:    SCPlugin-Ifupdown: device added (udi: /org/freedesktop/Hal/devices/net_00_1c_23_fd_72_6c, iface: eth0): not well known
May  8 03:06:59 Barnaby nm-system-settings:    SCPlugin-Ifupdown: device added (udi: /org/freedesktop/Hal/devices/net_00_1c_bf_96_f1_aa, iface: wlan0): not well known
May  8 03:06:59 Barnaby nm-system-settings:    SCPlugin-Ifupdown: end _init.
May  8 03:06:59 Barnaby nm-system-settings: Loaded plugin ifupdown: (C) 2008 Canonical Ltd.  To report bugs please use the NetworkManager mailing list.
May  8 03:06:59 Barnaby nm-system-settings: Loaded plugin keyfile: (c) 2007 - 2008 Red Hat, Inc.  To report bugs please use the NetworkManager mailing list.
May  8 03:06:59 Barnaby nm-system-settings:    SCPlugin-Ifupdown: (20849104) ... get_connections.
May  8 03:06:59 Barnaby nm-system-settings:    SCPlugin-Ifupdown: (20849104) ... get_connections (managed=false): return empty list.
May  8 03:06:59 Barnaby nm-system-settings:    Ifupdown: get unmanaged devices count: 0
May  8 03:06:59 Barnaby NetworkManager: <info>  (wlan0): supplicant manager state:  down -> idle 
May  8 03:07:03 Barnaby NetworkManager: <info>  (eth0): device state change: 1 -> 2 
May  8 03:07:03 Barnaby NetworkManager: <info>  (eth0): bringing up device. 
May  8 03:07:03 Barnaby NetworkManager: <info>  (eth0): preparing device. 
May  8 03:07:03 Barnaby NetworkManager: <info>  (eth0): deactivating device (reason: 2). 
May  8 03:07:03 Barnaby NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889) 
May  8 03:07:03 Barnaby NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889) 
May  8 03:07:03 Barnaby NetworkManager: <info>  (wlan0): device state change: 1 -> 2 
May  8 03:07:03 Barnaby NetworkManager: <info>  (wlan0): bringing up device. 
May  8 03:07:03 Barnaby NetworkManager: <info>  (wlan0): preparing device. 
May  8 03:07:03 Barnaby NetworkManager: <info>  (wlan0): deactivating device (reason: 2). 
May  8 03:07:03 Barnaby NetworkManager: <info>  (wlan0): device state change: 2 -> 3 
May  8 03:07:03 Barnaby NetworkManager: <info>  (wlan0): supplicant interface state:  starting -> ready 
May  8 03:07:04 Barnaby nm-system-settings: Added default wired connection 'Auto eth0' for /org/freedesktop/Hal/devices/net_00_1c_23_fd_72_6c
May  8 03:07:04 Barnaby NetworkManager: <info>  (eth0): carrier now ON (device state 2) 
May  8 03:07:04 Barnaby NetworkManager: <info>  (eth0): device state change: 2 -> 3 
May  8 03:07:04 Barnaby NetworkManager: <info>  Activation (eth0) starting connection 'Auto eth0' 
May  8 03:07:04 Barnaby NetworkManager: <info>  (eth0): device state change: 3 -> 4 
May  8 03:07:04 Barnaby NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled... 
May  8 03:07:04 Barnaby NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) started... 
May  8 03:07:04 Barnaby NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) scheduled... 
May  8 03:07:04 Barnaby NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) complete. 
May  8 03:07:04 Barnaby NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) starting... 
May  8 03:07:04 Barnaby NetworkManager: <info>  (eth0): device state change: 4 -> 5 
May  8 03:07:04 Barnaby NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) successful. 
May  8 03:07:04 Barnaby NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled. 
May  8 03:07:04 Barnaby NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) complete. 
May  8 03:07:04 Barnaby NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) started... 
May  8 03:07:04 Barnaby NetworkManager: <info>  (eth0): device state change: 5 -> 7 
May  8 03:07:04 Barnaby NetworkManager: <info>  Activation (eth0) Beginning DHCP transaction. 
May  8 03:07:04 Barnaby NetworkManager: <info>  dhclient started with pid 3347 
May  8 03:07:04 Barnaby NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) complete. 
May  8 03:07:04 Barnaby dhclient: Internet Systems Consortium DHCP Client V3.1.1
May  8 03:07:04 Barnaby dhclient: Copyright 2004-2008 Internet Systems Consortium.
May  8 03:07:04 Barnaby dhclient: All rights reserved.
May  8 03:07:04 Barnaby dhclient: For info, please visit http://www.isc.org/sw/dhcp/
May  8 03:07:04 Barnaby dhclient: 
May  8 03:07:04 Barnaby dhclient: wmaster0: unknown hardware address type 801
May  8 03:07:04 Barnaby NetworkManager: <info>  DHCP: device eth0 state changed (null) -> preinit 
May  8 03:07:04 Barnaby dhclient: wmaster0: unknown hardware address type 801
May  8 03:07:04 Barnaby dhclient: Listening on LPF/eth0/00:1c:23:fd:72:6c
May  8 03:07:04 Barnaby dhclient: Sending on   LPF/eth0/00:1c:23:fd:72:6c
May  8 03:07:04 Barnaby dhclient: Sending on   Socket/fallback
May  8 03:07:04 Barnaby dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
May  8 03:07:05 Barnaby avahi-daemon[3052]: Registering new address record for fe80::21c:23ff:fefd:726c on eth0.*.
May  8 03:07:05 Barnaby dhclient: DHCPOFFER of 192.168.1.101 from 192.168.1.1
May  8 03:07:05 Barnaby dhclient: DHCPREQUEST of 192.168.1.101 on eth0 to 255.255.255.255 port 67
May  8 03:07:05 Barnaby dhclient: DHCPACK of 192.168.1.101 from 192.168.1.1
May  8 03:07:05 Barnaby NetworkManager: <info>  DHCP: device eth0 state changed preinit -> bound 
May  8 03:07:05 Barnaby NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Get) scheduled... 
May  8 03:07:05 Barnaby NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Get) started... 
May  8 03:07:05 Barnaby NetworkManager: <info>    address 192.168.1.101 
May  8 03:07:05 Barnaby NetworkManager: <info>    prefix 24 (255.255.255.0) 
May  8 03:07:05 Barnaby NetworkManager: <info>    gateway 192.168.1.1 
May  8 03:07:05 Barnaby NetworkManager: <info>    hostname 'Barnaby' 
May  8 03:07:05 Barnaby NetworkManager: <info>    nameserver '68.87.85.98' 
May  8 03:07:05 Barnaby NetworkManager: <info>    nameserver '68.87.69.146' 
May  8 03:07:05 Barnaby NetworkManager: <info>    nameserver '68.87.78.130' 
May  8 03:07:05 Barnaby NetworkManager: <info>    domain name 'hsd1.ut.comcast.net.' 
May  8 03:07:05 Barnaby NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) scheduled... 
May  8 03:07:05 Barnaby NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Get) complete. 
May  8 03:07:05 Barnaby NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) started... 
May  8 03:07:05 Barnaby avahi-daemon[3052]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.1.101.
May  8 03:07:05 Barnaby dhclient: bound to 192.168.1.101 -- renewal in 34190 seconds.
May  8 03:07:05 Barnaby avahi-daemon[3052]: New relevant interface eth0.IPv4 for mDNS.
May  8 03:07:05 Barnaby avahi-daemon[3052]: Registering new address record for 192.168.1.101 on eth0.IPv4.
May  8 03:07:06 Barnaby NetworkManager: <info>  (eth0): device state change: 7 -> 8 
May  8 03:07:06 Barnaby NetworkManager: <info>  Policy set 'Auto eth0' (eth0) as default for routing and DNS. 
May  8 03:07:06 Barnaby NetworkManager: <info>  Activation (eth0) successful, device activated. 
May  8 03:07:06 Barnaby NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) complete. 
May  8 03:07:08 Barnaby ntpdate[3416]: adjust time server 91.189.94.4 offset -0.180304 sec
May  8 03:07:11 Barnaby console-kit-daemon[2787]: WARNING: Couldn't read /proc/2786/environ: Failed to open file '/proc/2786/environ': No such file or directory 
May  8 03:21:03 Barnaby acpid: client 3007[0:0] has disconnected 
May  8 03:22:40 Barnaby init: tty4 main process (2583) killed by TERM signal
May  8 03:22:40 Barnaby init: tty5 main process (2584) killed by TERM signal
May  8 03:22:40 Barnaby init: tty2 main process (2590) killed by TERM signal
May  8 03:22:40 Barnaby init: tty3 main process (2591) killed by TERM signal
May  8 03:22:40 Barnaby init: tty6 main process (2592) killed by TERM signal
May  8 03:22:40 Barnaby init: tty1 main process (3309) killed by TERM signal
May  8 03:22:44 Barnaby bluetoothd[2966]: bridge pan0 removed
May  8 03:22:44 Barnaby bluetoothd[2966]: Stopping SDP server
May  8 03:22:44 Barnaby bluetoothd[2966]: Exit
May  8 03:24:17 Barnaby acpid: client connected from 2943[105:106] 
May  8 03:24:17 Barnaby bluetoothd[2965]: Bluetooth daemon
May  8 03:24:17 Barnaby bluetoothd[2965]: Starting SDP server
May  8 03:24:17 Barnaby bluetoothd[2965]: Starting experimental netlink support
May  8 03:24:17 Barnaby bluetoothd[2965]: Failed to find Bluetooth netlink family
May  8 03:24:17 Barnaby bluetoothd[2965]: Registered interface org.bluez.Service on path /org/bluez/2965/any
May  8 03:24:17 Barnaby bluetoothd[2965]: bridge pan0 created
May  8 03:24:18 Barnaby acpid: client connected from 3006[0:0] 
May  8 03:24:18 Barnaby NetworkManager: <info>  starting... 
May  8 03:24:18 Barnaby NetworkManager: <info>  Found radio killswitch /org/freedesktop/Hal/devices/pci_8086_4222_rfkill_3945ABG_wlan 
May  8 03:24:18 Barnaby NetworkManager: <info>  Found radio killswitch /org/freedesktop/Hal/devices/dell_wlan_switch 
May  8 03:24:18 Barnaby NetworkManager: <info>  (eth0): new Ethernet device (driver: 'tg3') 
May  8 03:24:18 Barnaby NetworkManager: <info>  (eth0): exported as /org/freedesktop/Hal/devices/net_00_1c_23_fd_72_6c 
May  8 03:24:18 Barnaby avahi-daemon[3051]: Found user 'avahi' (UID 108) and group 'avahi' (GID 114).
May  8 03:24:18 Barnaby avahi-daemon[3051]: Successfully dropped root privileges.
May  8 03:24:18 Barnaby avahi-daemon[3051]: avahi-daemon 0.6.23 starting up.
May  8 03:24:18 Barnaby avahi-daemon[3051]: Successfully called chroot().
May  8 03:24:18 Barnaby avahi-daemon[3051]: Successfully dropped remaining capabilities.
May  8 03:24:18 Barnaby NetworkManager: <info>  (wlan0): driver supports SSID scans (scan_capa 0x01). 
May  8 03:24:18 Barnaby NetworkManager: <info>  (wlan0): new 802.11 WiFi device (driver: 'iwl3945') 
May  8 03:24:18 Barnaby NetworkManager: <info>  (wlan0): exported as /org/freedesktop/Hal/devices/net_00_1c_bf_96_f1_aa 
May  8 03:24:18 Barnaby NetworkManager: <info>  Trying to start the supplicant... 
May  8 03:24:18 Barnaby NetworkManager: <info>  Trying to start the system settings daemon... 
May  8 03:24:18 Barnaby avahi-daemon[3051]: No service file found in /etc/avahi/services.
May  8 03:24:18 Barnaby avahi-daemon[3051]: Network interface enumeration completed.
May  8 03:24:18 Barnaby avahi-daemon[3051]: Registering HINFO record with values 'X86_64'/'LINUX'.
May  8 03:24:18 Barnaby avahi-daemon[3051]: Server startup complete. Host name is Barnaby.local. Local service cookie is 1878783138.
May  8 03:24:18 Barnaby nm-system-settings:    SCPlugin-Ifupdown: init!
May  8 03:24:18 Barnaby nm-system-settings:    SCPlugin-Ifupdown: update_system_hostname
May  8 03:24:18 Barnaby nm-system-settings:    SCPluginIfupdown: management mode: unmanaged
May  8 03:24:18 Barnaby nm-system-settings:    SCPlugin-Ifupdown: device added (udi: /org/freedesktop/Hal/devices/net_00_1c_23_fd_72_6c, iface: eth0): not well known
May  8 03:24:18 Barnaby nm-system-settings:    SCPlugin-Ifupdown: device added (udi: /org/freedesktop/Hal/devices/net_00_1c_bf_96_f1_aa, iface: wlan0): not well known
May  8 03:24:18 Barnaby nm-system-settings:    SCPlugin-Ifupdown: end _init.
May  8 03:24:18 Barnaby nm-system-settings: Loaded plugin ifupdown: (C) 2008 Canonical Ltd.  To report bugs please use the NetworkManager mailing list.
May  8 03:24:18 Barnaby nm-system-settings: Loaded plugin keyfile: (c) 2007 - 2008 Red Hat, Inc.  To report bugs please use the NetworkManager mailing list.
May  8 03:24:18 Barnaby nm-system-settings:    SCPlugin-Ifupdown: (33690064) ... get_connections.
May  8 03:24:18 Barnaby nm-system-settings:    SCPlugin-Ifupdown: (33690064) ... get_connections (managed=false): return empty list.
May  8 03:24:18 Barnaby nm-system-settings:    Ifupdown: get unmanaged devices count: 0
May  8 03:24:18 Barnaby NetworkManager: <info>  (wlan0): supplicant manager state:  down -> idle 
May  8 03:24:23 Barnaby NetworkManager: <info>  (eth0): device state change: 1 -> 2 
May  8 03:24:23 Barnaby NetworkManager: <info>  (eth0): bringing up device. 
May  8 03:24:23 Barnaby nm-system-settings: Added default wired connection 'Auto eth0' for /org/freedesktop/Hal/devices/net_00_1c_23_fd_72_6c
May  8 03:24:23 Barnaby NetworkManager: <info>  (eth0): preparing device. 
May  8 03:24:23 Barnaby NetworkManager: <info>  (eth0): deactivating device (reason: 2). 
May  8 03:24:23 Barnaby NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889) 
May  8 03:24:23 Barnaby NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889) 
May  8 03:24:23 Barnaby NetworkManager: <info>  (wlan0): device state change: 1 -> 2 
May  8 03:24:23 Barnaby NetworkManager: <info>  (wlan0): bringing up device. 
May  8 03:24:23 Barnaby NetworkManager: <info>  (wlan0): preparing device. 
May  8 03:24:23 Barnaby NetworkManager: <info>  (wlan0): deactivating device (reason: 2). 
May  8 03:24:23 Barnaby NetworkManager: <info>  (wlan0): device state change: 2 -> 3 
May  8 03:24:23 Barnaby NetworkManager: <info>  (wlan0): supplicant interface state:  starting -> ready 
May  8 03:24:24 Barnaby NetworkManager: <info>  (eth0): carrier now ON (device state 2) 
May  8 03:24:24 Barnaby NetworkManager: <info>  (eth0): device state change: 2 -> 3 
May  8 03:24:24 Barnaby NetworkManager: <info>  Activation (eth0) starting connection 'Auto eth0' 
May  8 03:24:24 Barnaby NetworkManager: <info>  (eth0): device state change: 3 -> 4 
May  8 03:24:24 Barnaby NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled... 
May  8 03:24:24 Barnaby NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) started... 
May  8 03:24:24 Barnaby NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) scheduled... 
May  8 03:24:24 Barnaby NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) complete. 
May  8 03:24:24 Barnaby NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) starting... 
May  8 03:24:24 Barnaby NetworkManager: <info>  (eth0): device state change: 4 -> 5 
May  8 03:24:24 Barnaby NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) successful. 
May  8 03:24:24 Barnaby NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled. 
May  8 03:24:24 Barnaby NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) complete. 
May  8 03:24:24 Barnaby NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) started... 
May  8 03:24:24 Barnaby NetworkManager: <info>  (eth0): device state change: 5 -> 7 
May  8 03:24:24 Barnaby NetworkManager: <info>  Activation (eth0) Beginning DHCP transaction. 
May  8 03:24:24 Barnaby NetworkManager: <info>  dhclient started with pid 3366 
May  8 03:24:24 Barnaby NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) complete. 
May  8 03:24:24 Barnaby dhclient: Internet Systems Consortium DHCP Client V3.1.1
May  8 03:24:24 Barnaby dhclient: Copyright 2004-2008 Internet Systems Consortium.
May  8 03:24:24 Barnaby dhclient: All rights reserved.
May  8 03:24:24 Barnaby dhclient: For info, please visit http://www.isc.org/sw/dhcp/
May  8 03:24:24 Barnaby dhclient: 
May  8 03:24:24 Barnaby dhclient: wmaster0: unknown hardware address type 801
May  8 03:24:24 Barnaby NetworkManager: <info>  DHCP: device eth0 state changed (null) -> preinit 
May  8 03:24:24 Barnaby dhclient: wmaster0: unknown hardware address type 801
May  8 03:24:24 Barnaby dhclient: Listening on LPF/eth0/00:1c:23:fd:72:6c
May  8 03:24:24 Barnaby dhclient: Sending on   LPF/eth0/00:1c:23:fd:72:6c
May  8 03:24:24 Barnaby dhclient: Sending on   Socket/fallback
May  8 03:24:25 Barnaby avahi-daemon[3051]: Registering new address record for fe80::21c:23ff:fefd:726c on eth0.*.
May  8 03:24:27 Barnaby dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
May  8 03:24:27 Barnaby dhclient: DHCPOFFER of 192.168.1.101 from 192.168.1.1
May  8 03:24:27 Barnaby dhclient: DHCPREQUEST of 192.168.1.101 on eth0 to 255.255.255.255 port 67
May  8 03:24:27 Barnaby dhclient: DHCPACK of 192.168.1.101 from 192.168.1.1
May  8 03:24:28 Barnaby NetworkManager: <info>  DHCP: device eth0 state changed preinit -> bound 
May  8 03:24:28 Barnaby NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Get) scheduled... 
May  8 03:24:28 Barnaby NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Get) started... 
May  8 03:24:28 Barnaby NetworkManager: <info>    address 192.168.1.101 
May  8 03:24:28 Barnaby NetworkManager: <info>    prefix 24 (255.255.255.0) 
May  8 03:24:28 Barnaby NetworkManager: <info>    gateway 192.168.1.1 
May  8 03:24:28 Barnaby NetworkManager: <info>    hostname 'Barnaby' 
May  8 03:24:28 Barnaby NetworkManager: <info>    nameserver '68.87.85.98' 
May  8 03:24:28 Barnaby NetworkManager: <info>    nameserver '68.87.69.146' 
May  8 03:24:28 Barnaby NetworkManager: <info>    nameserver '68.87.78.130' 
May  8 03:24:28 Barnaby NetworkManager: <info>    domain name 'hsd1.ut.comcast.net.' 
May  8 03:24:28 Barnaby NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) scheduled... 
May  8 03:24:28 Barnaby NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Get) complete. 
May  8 03:24:28 Barnaby NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) started... 
May  8 03:24:28 Barnaby avahi-daemon[3051]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.1.101.
May  8 03:24:28 Barnaby avahi-daemon[3051]: New relevant interface eth0.IPv4 for mDNS.
May  8 03:24:28 Barnaby avahi-daemon[3051]: Registering new address record for 192.168.1.101 on eth0.IPv4.
May  8 03:24:28 Barnaby dhclient: bound to 192.168.1.101 -- renewal in 35468 seconds.
May  8 03:24:29 Barnaby NetworkManager: <info>  (eth0): device state change: 7 -> 8 
May  8 03:24:29 Barnaby NetworkManager: <info>  Policy set 'Auto eth0' (eth0) as default for routing and DNS. 
May  8 03:24:29 Barnaby NetworkManager: <info>  Activation (eth0) successful, device activated. 
May  8 03:24:29 Barnaby NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) complete. 
May  8 03:24:29 Barnaby console-kit-daemon[2786]: WARNING: Couldn't read /proc/2785/environ: Failed to open file '/proc/2785/environ': No such file or directory 
May  8 03:24:31 Barnaby ntpdate[3532]: adjust time server 91.189.94.4 offset -0.056251 sec
May  8 03:49:48 Barnaby NetworkManager: <info>  Sleeping... 
May  8 03:49:48 Barnaby NetworkManager: <info>  (eth0): now unmanaged 
May  8 03:49:48 Barnaby NetworkManager: <info>  (eth0): device state change: 8 -> 1 
May  8 03:49:48 Barnaby NetworkManager: <info>  (eth0): deactivating device (reason: 37). 
May  8 03:49:48 Barnaby NetworkManager: <info>  eth0: canceled DHCP transaction, dhcp client pid 3366 
May  8 03:49:48 Barnaby NetworkManager: <WARN>  check_one_route(): (eth0) error -34 returned from rtnl_route_del(): Sucess  
May  8 03:49:48 Barnaby NetworkManager: <info>  (eth0): cleaning up... 
May  8 03:49:48 Barnaby NetworkManager: <info>  (eth0): taking down device. 
May  8 03:49:48 Barnaby avahi-daemon[3051]: Withdrawing address record for 192.168.1.101 on eth0.
May  8 03:49:48 Barnaby avahi-daemon[3051]: Leaving mDNS multicast group on interface eth0.IPv4 with address 192.168.1.101.
May  8 03:49:48 Barnaby avahi-daemon[3051]: Interface eth0.IPv4 no longer relevant for mDNS.
May  8 03:49:48 Barnaby avahi-daemon[3051]: Withdrawing address record for fe80::21c:23ff:fefd:726c on eth0.
May  8 03:49:48 Barnaby NetworkManager: <info>  (wlan0): now unmanaged 
May  8 03:49:48 Barnaby NetworkManager: <info>  (wlan0): device state change: 3 -> 1 
May  8 03:49:48 Barnaby NetworkManager: <info>  (wlan0): cleaning up... 
May  8 03:49:48 Barnaby NetworkManager: <info>  (wlan0): taking down device. 
May  8 03:49:48 Barnaby NetworkManager: <info>  (eth0): carrier now OFF (device state 1) 
May  8 03:49:50 Barnaby NetworkManager: <info>  Waking up... 
May  8 03:49:50 Barnaby NetworkManager: <info>  (eth0): now managed 
May  8 03:49:50 Barnaby NetworkManager: <info>  (eth0): device state change: 1 -> 2 
May  8 03:49:50 Barnaby NetworkManager: <info>  (eth0): bringing up device. 
May  8 03:49:50 Barnaby NetworkManager: <info>  (eth0): preparing device. 
May  8 03:49:50 Barnaby NetworkManager: <info>  (eth0): deactivating device (reason: 2). 
May  8 03:49:50 Barnaby NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889) 
May  8 03:49:50 Barnaby NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889) 
May  8 03:49:50 Barnaby NetworkManager: <info>  (wlan0): now managed 
May  8 03:49:50 Barnaby NetworkManager: <info>  (wlan0): device state change: 1 -> 2 
May  8 03:49:50 Barnaby NetworkManager: <info>  (wlan0): bringing up device. 
May  8 03:49:50 Barnaby NetworkManager: <info>  (wlan0): preparing device. 
May  8 03:49:50 Barnaby NetworkManager: <info>  (wlan0): deactivating device (reason: 2). 
May  8 03:49:50 Barnaby NetworkManager: <info>  (wlan0): device state change: 2 -> 3 
May  8 03:49:50 Barnaby NetworkManager: <info>  (wlan0): supplicant interface state:  starting -> ready 
May  8 03:49:51 Barnaby NetworkManager: <info>  (eth0): carrier now ON (device state 2) 
May  8 03:49:51 Barnaby NetworkManager: <info>  (eth0): device state change: 2 -> 3 
May  8 03:49:51 Barnaby NetworkManager: <info>  Activation (eth0) starting connection 'Auto eth0' 
May  8 03:49:51 Barnaby NetworkManager: <info>  (eth0): device state change: 3 -> 4 
May  8 03:49:51 Barnaby NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled... 
May  8 03:49:51 Barnaby NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) started... 
May  8 03:49:51 Barnaby NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) scheduled... 
May  8 03:49:51 Barnaby NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) complete. 
May  8 03:49:51 Barnaby NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) starting... 
May  8 03:49:51 Barnaby NetworkManager: <info>  (eth0): device state change: 4 -> 5 
May  8 03:49:51 Barnaby NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) successful. 
May  8 03:49:51 Barnaby NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled. 
May  8 03:49:51 Barnaby NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) complete. 
May  8 03:49:51 Barnaby NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) started... 
May  8 03:49:51 Barnaby NetworkManager: <info>  (eth0): device state change: 5 -> 7 
May  8 03:49:51 Barnaby NetworkManager: <info>  Activation (eth0) Beginning DHCP transaction. 
May  8 03:49:51 Barnaby dhclient: Internet Systems Consortium DHCP Client V3.1.1
May  8 03:49:51 Barnaby dhclient: Copyright 2004-2008 Internet Systems Consortium.
May  8 03:49:51 Barnaby dhclient: All rights reserved.
May  8 03:49:51 Barnaby dhclient: For info, please visit http://www.isc.org/sw/dhcp/
May  8 03:49:51 Barnaby dhclient: 
May  8 03:49:51 Barnaby dhclient: wmaster0: unknown hardware address type 801
May  8 03:49:51 Barnaby NetworkManager: <info>  dhclient started with pid 6329 
May  8 03:49:51 Barnaby NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) complete. 
May  8 03:49:51 Barnaby dhclient: wmaster0: unknown hardware address type 801
May  8 03:49:51 Barnaby NetworkManager: <info>  DHCP: device eth0 state changed normal exit -> preinit 
May  8 03:49:51 Barnaby dhclient: Listening on LPF/eth0/00:1c:23:fd:72:6c
May  8 03:49:51 Barnaby dhclient: Sending on   LPF/eth0/00:1c:23:fd:72:6c
May  8 03:49:51 Barnaby dhclient: Sending on   Socket/fallback
May  8 03:49:53 Barnaby avahi-daemon[3051]: Registering new address record for fe80::21c:23ff:fefd:726c on eth0.*.
May  8 03:49:55 Barnaby dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
May  8 03:49:56 Barnaby dhclient: DHCPOFFER of 192.168.1.101 from 192.168.1.1
May  8 03:49:56 Barnaby dhclient: DHCPREQUEST of 192.168.1.101 on eth0 to 255.255.255.255 port 67
May  8 03:49:56 Barnaby dhclient: DHCPACK of 192.168.1.101 from 192.168.1.1
May  8 03:49:56 Barnaby NetworkManager: <info>  DHCP: device eth0 state changed preinit -> bound 
May  8 03:49:56 Barnaby NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Get) scheduled... 
May  8 03:49:56 Barnaby NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Get) started... 
May  8 03:49:56 Barnaby NetworkManager: <info>    address 192.168.1.101 
May  8 03:49:56 Barnaby NetworkManager: <info>    prefix 24 (255.255.255.0) 
May  8 03:49:56 Barnaby NetworkManager: <info>    gateway 192.168.1.1 
May  8 03:49:56 Barnaby NetworkManager: <info>    hostname 'Barnaby' 
May  8 03:49:56 Barnaby NetworkManager: <info>    nameserver '68.87.85.98' 
May  8 03:49:56 Barnaby NetworkManager: <info>    nameserver '68.87.69.146' 
May  8 03:49:56 Barnaby NetworkManager: <info>    nameserver '68.87.78.130' 
May  8 03:49:56 Barnaby NetworkManager: <info>    domain name 'hsd1.ut.comcast.net.' 
May  8 03:49:56 Barnaby NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) scheduled... 
May  8 03:49:56 Barnaby NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Get) complete. 
May  8 03:49:56 Barnaby dhclient: bound to 192.168.1.101 -- renewal in 41122 seconds.
May  8 03:49:56 Barnaby NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) started... 
May  8 03:49:56 Barnaby avahi-daemon[3051]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.1.101.
May  8 03:49:56 Barnaby avahi-daemon[3051]: New relevant interface eth0.IPv4 for mDNS.
May  8 03:49:56 Barnaby avahi-daemon[3051]: Registering new address record for 192.168.1.101 on eth0.IPv4.
May  8 03:49:57 Barnaby NetworkManager: <info>  (eth0): device state change: 7 -> 8 
May  8 03:49:57 Barnaby NetworkManager: <info>  Policy set 'Auto eth0' (eth0) as default for routing and DNS. 
May  8 03:49:57 Barnaby NetworkManager: <info>  Activation (eth0) successful, device activated. 
May  8 03:49:57 Barnaby NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) complete. 
May  8 03:49:58 Barnaby ntpdate[6394]: adjust time server 91.189.94.4 offset 0.017796 sec
May  8 03:50:15 Barnaby NetworkManager: <info>  Sleeping... 
May  8 03:50:15 Barnaby NetworkManager: <info>  (eth0): now unmanaged 
May  8 03:50:15 Barnaby NetworkManager: <info>  (eth0): device state change: 8 -> 1 
May  8 03:50:15 Barnaby NetworkManager: <info>  (eth0): deactivating device (reason: 37). 
May  8 03:50:15 Barnaby NetworkManager: <info>  eth0: canceled DHCP transaction, dhcp client pid 6329 
May  8 03:50:15 Barnaby NetworkManager: <WARN>  check_one_route(): (eth0) error -34 returned from rtnl_route_del(): Sucess  
May  8 03:50:15 Barnaby NetworkManager: <info>  (eth0): cleaning up... 
May  8 03:50:15 Barnaby NetworkManager: <info>  (eth0): taking down device. 
May  8 03:50:15 Barnaby avahi-daemon[3051]: Withdrawing address record for 192.168.1.101 on eth0.
May  8 03:50:15 Barnaby avahi-daemon[3051]: Leaving mDNS multicast group on interface eth0.IPv4 with address 192.168.1.101.
May  8 03:50:15 Barnaby avahi-daemon[3051]: Interface eth0.IPv4 no longer relevant for mDNS.
May  8 03:50:15 Barnaby avahi-daemon[3051]: Withdrawing address record for fe80::21c:23ff:fefd:726c on eth0.
May  8 03:50:15 Barnaby NetworkManager: <info>  (wlan0): now unmanaged 
May  8 03:50:15 Barnaby NetworkManager: <info>  (wlan0): device state change: 3 -> 1 
May  8 03:50:15 Barnaby NetworkManager: <info>  (wlan0): cleaning up... 
May  8 03:50:15 Barnaby NetworkManager: <info>  (wlan0): taking down device. 
May  8 03:50:15 Barnaby NetworkManager: <info>  (eth0): carrier now OFF (device state 1) 
May  8 03:50:19 Barnaby NetworkManager: <info>  Waking up... 
May  8 03:50:19 Barnaby NetworkManager: <info>  (eth0): now managed 
May  8 03:50:19 Barnaby NetworkManager: <info>  (eth0): device state change: 1 -> 2 
May  8 03:50:19 Barnaby NetworkManager: <info>  (eth0): bringing up device. 
May  8 03:50:19 Barnaby NetworkManager: <info>  (eth0): preparing device. 
May  8 03:50:19 Barnaby NetworkManager: <info>  (eth0): deactivating device (reason: 2). 
May  8 03:50:19 Barnaby NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889) 
May  8 03:50:19 Barnaby NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889) 
May  8 03:50:19 Barnaby NetworkManager: <info>  (wlan0): now managed 
May  8 03:50:19 Barnaby NetworkManager: <info>  (wlan0): device state change: 1 -> 2 
May  8 03:50:19 Barnaby NetworkManager: <info>  (wlan0): bringing up device. 
May  8 03:50:19 Barnaby NetworkManager: <info>  (wlan0): preparing device. 
May  8 03:50:19 Barnaby NetworkManager: <info>  (wlan0): deactivating device (reason: 2). 
May  8 03:50:19 Barnaby NetworkManager: <info>  (wlan0): device state change: 2 -> 3 
May  8 03:50:19 Barnaby NetworkManager: <info>  (wlan0): supplicant interface state:  starting -> ready 
May  8 03:50:21 Barnaby NetworkManager: <info>  (eth0): carrier now ON (device state 2) 
May  8 03:50:21 Barnaby NetworkManager: <info>  (eth0): device state change: 2 -> 3 
May  8 03:50:21 Barnaby NetworkManager: <info>  Activation (eth0) starting connection 'Auto eth0' 
May  8 03:50:21 Barnaby NetworkManager: <info>  (eth0): device state change: 3 -> 4 
May  8 03:50:21 Barnaby NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled... 
May  8 03:50:21 Barnaby NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) started... 
May  8 03:50:21 Barnaby NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) scheduled... 
May  8 03:50:21 Barnaby NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) complete. 
May  8 03:50:21 Barnaby NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) starting... 
May  8 03:50:21 Barnaby NetworkManager: <info>  (eth0): device state change: 4 -> 5 
May  8 03:50:21 Barnaby NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) successful. 
May  8 03:50:21 Barnaby NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled. 
May  8 03:50:21 Barnaby NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) complete. 
May  8 03:50:21 Barnaby NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) started... 
May  8 03:50:21 Barnaby NetworkManager: <info>  (eth0): device state change: 5 -> 7 
May  8 03:50:21 Barnaby NetworkManager: <info>  Activation (eth0) Beginning DHCP transaction. 
May  8 03:50:21 Barnaby dhclient: Internet Systems Consortium DHCP Client V3.1.1
May  8 03:50:21 Barnaby dhclient: Copyright 2004-2008 Internet Systems Consortium.
May  8 03:50:21 Barnaby dhclient: All rights reserved.
May  8 03:50:21 Barnaby dhclient: For info, please visit http://www.isc.org/sw/dhcp/
May  8 03:50:21 Barnaby dhclient: 
May  8 03:50:21 Barnaby dhclient: wmaster0: unknown hardware address type 801
May  8 03:50:21 Barnaby NetworkManager: <info>  dhclient started with pid 6655 
May  8 03:50:21 Barnaby NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) complete. 
May  8 03:50:21 Barnaby dhclient: wmaster0: unknown hardware address type 801
May  8 03:50:21 Barnaby NetworkManager: <info>  DHCP: device eth0 state changed normal exit -> preinit 
May  8 03:50:21 Barnaby dhclient: Listening on LPF/eth0/00:1c:23:fd:72:6c
May  8 03:50:21 Barnaby dhclient: Sending on   LPF/eth0/00:1c:23:fd:72:6c
May  8 03:50:21 Barnaby dhclient: Sending on   Socket/fallback
May  8 03:50:22 Barnaby dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
May  8 03:50:22 Barnaby avahi-daemon[3051]: Registering new address record for fe80::21c:23ff:fefd:726c on eth0.*.
May  8 03:50:23 Barnaby dhclient: DHCPOFFER of 192.168.1.101 from 192.168.1.1
May  8 03:50:23 Barnaby dhclient: DHCPREQUEST of 192.168.1.101 on eth0 to 255.255.255.255 port 67
May  8 03:50:23 Barnaby dhclient: DHCPACK of 192.168.1.101 from 192.168.1.1
May  8 03:50:23 Barnaby NetworkManager: <info>  DHCP: device eth0 state changed preinit -> bound 
May  8 03:50:23 Barnaby NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Get) scheduled... 
May  8 03:50:23 Barnaby NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Get) started... 
May  8 03:50:23 Barnaby NetworkManager: <info>    address 192.168.1.101 
May  8 03:50:23 Barnaby NetworkManager: <info>    prefix 24 (255.255.255.0) 
May  8 03:50:23 Barnaby NetworkManager: <info>    gateway 192.168.1.1 
May  8 03:50:23 Barnaby NetworkManager: <info>    hostname 'Barnaby' 
May  8 03:50:23 Barnaby NetworkManager: <info>    nameserver '68.87.85.98' 
May  8 03:50:23 Barnaby NetworkManager: <info>    nameserver '68.87.69.146' 
May  8 03:50:23 Barnaby NetworkManager: <info>    nameserver '68.87.78.130' 
May  8 03:50:23 Barnaby NetworkManager: <info>    domain name 'hsd1.ut.comcast.net.' 
May  8 03:50:23 Barnaby NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) scheduled... 
May  8 03:50:23 Barnaby NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Get) complete. 
May  8 03:50:23 Barnaby NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) started... 
May  8 03:50:23 Barnaby avahi-daemon[3051]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.1.101.
May  8 03:50:23 Barnaby avahi-daemon[3051]: New relevant interface eth0.IPv4 for mDNS.
May  8 03:50:23 Barnaby avahi-daemon[3051]: Registering new address record for 192.168.1.101 on eth0.IPv4.
May  8 03:50:23 Barnaby dhclient: bound to 192.168.1.101 -- renewal in 33588 seconds.
May  8 03:50:24 Barnaby NetworkManager: <info>  (eth0): device state change: 7 -> 8 
May  8 03:50:24 Barnaby NetworkManager: <info>  Policy set 'Auto eth0' (eth0) as default for routing and DNS. 
May  8 03:50:24 Barnaby NetworkManager: <info>  Activation (eth0) successful, device activated. 
May  8 03:50:24 Barnaby NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) complete. 
May  8 03:50:25 Barnaby ntpdate[6715]: adjust time server 91.189.94.4 offset 0.004239 sec
May  8 04:13:05 Barnaby console-kit-daemon[2786]: GLib-GObject-WARNING: IA__g_object_get_valist: value location for `gchararray' passed as NULL 
May  8 04:13:05 Barnaby last message repeated 3 times
May  8 04:13:05 Barnaby init: tty4 main process (2582) killed by TERM signal
May  8 04:13:05 Barnaby init: tty5 main process (2583) killed by TERM signal
May  8 04:13:05 Barnaby init: tty2 main process (2589) killed by TERM signal
May  8 04:13:05 Barnaby init: tty3 main process (2591) killed by TERM signal
May  8 04:13:05 Barnaby init: tty6 main process (2592) killed by TERM signal
May  8 04:13:05 Barnaby init: tty1 main process (3328) killed by TERM signal
May  8 04:13:05 Barnaby console-kit-daemon[2786]: GLib-GObject-WARNING: IA__g_object_get_valist: value location for `gchararray' passed as NULL 
May  8 04:13:11 Barnaby bluetoothd[2965]: bridge pan0 removed
May  8 04:13:11 Barnaby bluetoothd[2965]: Stopping SDP server
May  8 04:13:11 Barnaby bluetoothd[2965]: Exit
May  8 16:29:06 Barnaby acpid: client connected from 2999[105:106] 
May  8 16:29:06 Barnaby bluetoothd[3019]: Bluetooth daemon
May  8 16:29:06 Barnaby bluetoothd[3019]: Starting SDP server
May  8 16:29:06 Barnaby bluetoothd[3019]: Starting experimental netlink support
May  8 16:29:06 Barnaby bluetoothd[3019]: Failed to find Bluetooth netlink family
May  8 16:29:06 Barnaby bluetoothd[3019]: Registered interface org.bluez.Service on path /org/bluez/3019/any
May  8 16:29:06 Barnaby bluetoothd[3019]: bridge pan0 created
May  8 16:29:07 Barnaby acpid: client connected from 3059[0:0] 
May  8 16:29:07 Barnaby NetworkManager: <info>  starting... 
May  8 16:29:07 Barnaby NetworkManager: <info>  Found radio killswitch /org/freedesktop/Hal/devices/pci_8086_4222_rfkill_3945ABG_wlan 
May  8 16:29:07 Barnaby NetworkManager: <info>  Found radio killswitch /org/freedesktop/Hal/devices/dell_wlan_switch 
May  8 16:29:07 Barnaby NetworkManager: <info>  (eth0): new Ethernet device (driver: 'tg3') 
May  8 16:29:07 Barnaby NetworkManager: <info>  (eth0): exported as /org/freedesktop/Hal/devices/net_00_1c_23_fd_72_6c 
May  8 16:29:07 Barnaby avahi-daemon[3105]: Found user 'avahi' (UID 108) and group 'avahi' (GID 114).
May  8 16:29:07 Barnaby avahi-daemon[3105]: Successfully dropped root privileges.
May  8 16:29:07 Barnaby avahi-daemon[3105]: avahi-daemon 0.6.23 starting up.
May  8 16:29:07 Barnaby avahi-daemon[3105]: Successfully called chroot().
May  8 16:29:07 Barnaby avahi-daemon[3105]: Successfully dropped remaining capabilities.
May  8 16:29:07 Barnaby avahi-daemon[3105]: No service file found in /etc/avahi/services.
May  8 16:29:07 Barnaby avahi-daemon[3105]: Network interface enumeration completed.
May  8 16:29:07 Barnaby avahi-daemon[3105]: Registering HINFO record with values 'X86_64'/'LINUX'.
May  8 16:29:07 Barnaby avahi-daemon[3105]: Server startup complete. Host name is Barnaby.local. Local service cookie is 1369639307.
May  8 16:29:07 Barnaby NetworkManager: <info>  (wlan0): driver supports SSID scans (scan_capa 0x01). 
May  8 16:29:07 Barnaby NetworkManager: <info>  (wlan0): new 802.11 WiFi device (driver: 'iwl3945') 
May  8 16:29:07 Barnaby NetworkManager: <info>  (wlan0): exported as /org/freedesktop/Hal/devices/net_00_1c_bf_96_f1_aa 
May  8 16:29:07 Barnaby NetworkManager: <info>  Trying to start the supplicant... 
May  8 16:29:07 Barnaby NetworkManager: <info>  Trying to start the system settings daemon... 
May  8 16:29:07 Barnaby nm-system-settings:    SCPlugin-Ifupdown: init!
May  8 16:29:07 Barnaby nm-system-settings:    SCPlugin-Ifupdown: update_system_hostname
May  8 16:29:07 Barnaby nm-system-settings:    SCPluginIfupdown: management mode: unmanaged
May  8 16:29:07 Barnaby nm-system-settings:    SCPlugin-Ifupdown: device added (udi: /org/freedesktop/Hal/devices/net_00_1c_23_fd_72_6c, iface: eth0): not well known
May  8 16:29:07 Barnaby nm-system-settings:    SCPlugin-Ifupdown: device added (udi: /org/freedesktop/Hal/devices/net_00_1c_bf_96_f1_aa, iface: wlan0): not well known
May  8 16:29:07 Barnaby nm-system-settings:    SCPlugin-Ifupdown: end _init.
May  8 16:29:07 Barnaby nm-system-settings: Loaded plugin ifupdown: (C) 2008 Canonical Ltd.  To report bugs please use the NetworkManager mailing list.
May  8 16:29:07 Barnaby nm-system-settings: Loaded plugin keyfile: (c) 2007 - 2008 Red Hat, Inc.  To report bugs please use the NetworkManager mailing list.
May  8 16:29:07 Barnaby nm-system-settings:    SCPlugin-Ifupdown: (20623824) ... get_connections.
May  8 16:29:07 Barnaby nm-system-settings:    SCPlugin-Ifupdown: (20623824) ... get_connections (managed=false): return empty list.
May  8 16:29:07 Barnaby nm-system-settings:    Ifupdown: get unmanaged devices count: 0
May  8 16:29:07 Barnaby NetworkManager: <info>  (wlan0): supplicant manager state:  down -> idle 
May  8 16:29:12 Barnaby NetworkManager: <info>  (eth0): device state change: 1 -> 2 
May  8 16:29:12 Barnaby NetworkManager: <info>  (eth0): bringing up device. 
May  8 16:29:12 Barnaby nm-system-settings: Added default wired connection 'Auto eth0' for /org/freedesktop/Hal/devices/net_00_1c_23_fd_72_6c
May  8 16:29:12 Barnaby NetworkManager: <info>  (eth0): preparing device. 
May  8 16:29:12 Barnaby NetworkManager: <info>  (eth0): deactivating device (reason: 2). 
May  8 16:29:12 Barnaby NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889) 
May  8 16:29:12 Barnaby NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889) 
May  8 16:29:12 Barnaby NetworkManager: <info>  (wlan0): device state change: 1 -> 2 
May  8 16:29:12 Barnaby NetworkManager: <info>  (wlan0): bringing up device. 
May  8 16:29:12 Barnaby NetworkManager: <info>  (wlan0): preparing device. 
May  8 16:29:12 Barnaby NetworkManager: <info>  (wlan0): deactivating device (reason: 2). 
May  8 16:29:12 Barnaby NetworkManager: <info>  (wlan0): device state change: 2 -> 3 
May  8 16:29:12 Barnaby NetworkManager: <info>  (wlan0): supplicant interface state:  starting -> ready 
May  8 16:29:13 Barnaby NetworkManager: <info>  (eth0): carrier now ON (device state 2) 
May  8 16:29:13 Barnaby NetworkManager: <info>  (eth0): device state change: 2 -> 3 
May  8 16:29:13 Barnaby NetworkManager: <info>  Activation (eth0) starting connection 'Auto eth0' 
May  8 16:29:13 Barnaby NetworkManager: <info>  (eth0): device state change: 3 -> 4 
May  8 16:29:13 Barnaby NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled... 
May  8 16:29:13 Barnaby NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) started... 
May  8 16:29:13 Barnaby NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) scheduled... 
May  8 16:29:13 Barnaby NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) complete. 
May  8 16:29:13 Barnaby NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) starting... 
May  8 16:29:13 Barnaby NetworkManager: <info>  (eth0): device state change: 4 -> 5 
May  8 16:29:13 Barnaby NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) successful. 
May  8 16:29:13 Barnaby NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled. 
May  8 16:29:13 Barnaby NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) complete. 
May  8 16:29:13 Barnaby NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) started... 
May  8 16:29:13 Barnaby NetworkManager: <info>  (eth0): device state change: 5 -> 7 
May  8 16:29:13 Barnaby NetworkManager: <info>  Activation (eth0) Beginning DHCP transaction. 
May  8 16:29:13 Barnaby NetworkManager: <info>  dhclient started with pid 3432 
May  8 16:29:13 Barnaby NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) complete. 
May  8 16:29:13 Barnaby dhclient: Internet Systems Consortium DHCP Client V3.1.1
May  8 16:29:13 Barnaby dhclient: Copyright 2004-2008 Internet Systems Consortium.
May  8 16:29:13 Barnaby dhclient: All rights reserved.
May  8 16:29:13 Barnaby dhclient: For info, please visit http://www.isc.org/sw/dhcp/
May  8 16:29:13 Barnaby dhclient: 
May  8 16:29:13 Barnaby dhclient: wmaster0: unknown hardware address type 801
May  8 16:29:13 Barnaby NetworkManager: <info>  DHCP: device eth0 state changed (null) -> preinit 
May  8 16:29:13 Barnaby dhclient: wmaster0: unknown hardware address type 801
May  8 16:29:13 Barnaby dhclient: Listening on LPF/eth0/00:1c:23:fd:72:6c
May  8 16:29:13 Barnaby dhclient: Sending on   LPF/eth0/00:1c:23:fd:72:6c
May  8 16:29:13 Barnaby dhclient: Sending on   Socket/fallback
May  8 16:29:15 Barnaby dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
May  8 16:29:15 Barnaby avahi-daemon[3105]: Registering new address record for fe80::21c:23ff:fefd:726c on eth0.*.
May  8 16:29:16 Barnaby dhclient: DHCPOFFER of 192.168.1.101 from 192.168.1.1
May  8 16:29:16 Barnaby dhclient: DHCPREQUEST of 192.168.1.101 on eth0 to 255.255.255.255 port 67
May  8 16:29:16 Barnaby dhclient: DHCPACK of 192.168.1.101 from 192.168.1.1
May  8 16:29:16 Barnaby dhclient: bound to 192.168.1.101 -- renewal in 41038 seconds.
May  8 16:29:16 Barnaby NetworkManager: <info>  DHCP: device eth0 state changed preinit -> bound 
May  8 16:29:16 Barnaby NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Get) scheduled... 
May  8 16:29:16 Barnaby NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Get) started... 
May  8 16:29:16 Barnaby NetworkManager: <info>    address 192.168.1.101 
May  8 16:29:16 Barnaby NetworkManager: <info>    prefix 24 (255.255.255.0) 
May  8 16:29:16 Barnaby NetworkManager: <info>    gateway 192.168.1.1 
May  8 16:29:16 Barnaby NetworkManager: <info>    hostname 'Barnaby' 
May  8 16:29:16 Barnaby NetworkManager: <info>    nameserver '68.87.85.98' 
May  8 16:29:16 Barnaby NetworkManager: <info>    nameserver '68.87.69.146' 
May  8 16:29:16 Barnaby NetworkManager: <info>    nameserver '68.87.78.130' 
May  8 16:29:16 Barnaby NetworkManager: <info>    domain name 'hsd1.ut.comcast.net.' 
May  8 16:29:16 Barnaby NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) scheduled... 
May  8 16:29:16 Barnaby NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Get) complete. 
May  8 16:29:16 Barnaby NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) started... 
May  8 16:29:16 Barnaby avahi-daemon[3105]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.1.101.
May  8 16:29:16 Barnaby avahi-daemon[3105]: New relevant interface eth0.IPv4 for mDNS.
May  8 16:29:16 Barnaby avahi-daemon[3105]: Registering new address record for 192.168.1.101 on eth0.IPv4.
May  8 16:29:17 Barnaby NetworkManager: <info>  (eth0): device state change: 7 -> 8 
May  8 16:29:17 Barnaby NetworkManager: <info>  Policy set 'Auto eth0' (eth0) as default for routing and DNS. 
May  8 16:29:17 Barnaby NetworkManager: <info>  Activation (eth0) successful, device activated. 
May  8 16:29:17 Barnaby NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) complete. 
May  8 22:29:18 Barnaby ntpdate[3501]: step time server 91.189.94.4 offset 21600.132695 sec
May  8 22:29:23 Barnaby console-kit-daemon[2838]: WARNING: Couldn't read /proc/2837/environ: Failed to open file '/proc/2837/environ': No such file or directory 
May  8 22:29:27 Barnaby x-session-manager[3522]: EggSMClient-WARNING: Desktop file '/home/jason/.config/autostart/cairo-dock-cairo.desktop' has malformed Icon key 'cairo-dock.svg'(should not include extension) 
May  8 23:09:53 Barnaby console-kit-daemon[2838]: GLib-GObject-WARNING: IA__g_object_get_valist: value location for `gchararray' passed as NULL 
May  8 23:09:53 Barnaby last message repeated 4 times
May  8 23:09:53 Barnaby init: tty4 main process (2634) killed by TERM signal
May  8 23:09:53 Barnaby init: tty5 main process (2635) killed by TERM signal
May  8 23:09:53 Barnaby init: tty2 main process (2641) killed by TERM signal
May  8 23:09:53 Barnaby init: tty3 main process (2643) killed by TERM signal
May  8 23:09:53 Barnaby init: tty6 main process (2644) killed by TERM signal
May  8 23:09:53 Barnaby init: tty1 main process (3394) killed by TERM signal
May  8 23:09:53 Barnaby console-kit-daemon[2838]: GLib-GObject-WARNING: IA__g_object_get_valist: value location for `gchararray' passed as NULL 
May  8 23:09:53 Barnaby last message repeated 4 times
May  8 23:10:00 Barnaby bluetoothd[3019]: bridge pan0 removed
May  8 23:10:00 Barnaby bluetoothd[3019]: Stopping SDP server
May  8 23:10:00 Barnaby bluetoothd[3019]: Exit
May  8 23:13:15 Barnaby acpid: client connected from 2934[105:106] 
May  8 23:13:15 Barnaby bluetoothd[2958]: Bluetooth daemon
May  8 23:13:15 Barnaby bluetoothd[2958]: Starting SDP server
May  8 23:13:15 Barnaby bluetoothd[2958]: Starting experimental netlink support
May  8 23:13:15 Barnaby bluetoothd[2958]: Failed to find Bluetooth netlink family
May  8 23:13:15 Barnaby bluetoothd[2958]: Registered interface org.bluez.Service on path /org/bluez/2958/any
May  8 23:13:15 Barnaby bluetoothd[2958]: bridge pan0 created
May  8 23:13:16 Barnaby acpid: client connected from 2999[0:0] 
May  8 23:13:16 Barnaby NetworkManager: <info>  starting... 
May  8 23:13:16 Barnaby NetworkManager: <info>  Found radio killswitch /org/freedesktop/Hal/devices/pci_8086_4222_rfkill_3945ABG_wlan 
May  8 23:13:16 Barnaby NetworkManager: <info>  Found radio killswitch /org/freedesktop/Hal/devices/dell_wlan_switch 
May  8 23:13:16 Barnaby NetworkManager: <info>  (eth0): new Ethernet device (driver: 'tg3') 
May  8 23:13:16 Barnaby NetworkManager: <info>  (eth0): exported as /org/freedesktop/Hal/devices/net_00_1c_23_fd_72_6c 
May  8 23:13:16 Barnaby avahi-daemon[3044]: Found user 'avahi' (UID 108) and group 'avahi' (GID 114).
May  8 23:13:16 Barnaby avahi-daemon[3044]: Successfully dropped root privileges.
May  8 23:13:16 Barnaby avahi-daemon[3044]: avahi-daemon 0.6.23 starting up.
May  8 23:13:16 Barnaby avahi-daemon[3044]: Successfully called chroot().
May  8 23:13:16 Barnaby avahi-daemon[3044]: Successfully dropped remaining capabilities.
May  8 23:13:16 Barnaby avahi-daemon[3044]: No service file found in /etc/avahi/services.
May  8 23:13:16 Barnaby avahi-daemon[3044]: Network interface enumeration completed.
May  8 23:13:16 Barnaby avahi-daemon[3044]: Registering HINFO record with values 'X86_64'/'LINUX'.
May  8 23:13:16 Barnaby avahi-daemon[3044]: Server startup complete. Host name is Barnaby.local. Local service cookie is 4038638052.
May  8 23:13:16 Barnaby NetworkManager: <info>  (wlan0): driver supports SSID scans (scan_capa 0x01). 
May  8 23:13:16 Barnaby NetworkManager: <info>  (wlan0): new 802.11 WiFi device (driver: 'iwl3945') 
May  8 23:13:16 Barnaby NetworkManager: <info>  (wlan0): exported as /org/freedesktop/Hal/devices/net_00_1c_bf_96_f1_aa 
May  8 23:13:16 Barnaby NetworkManager: <info>  Trying to start the supplicant... 
May  8 23:13:16 Barnaby NetworkManager: <info>  Trying to start the system settings daemon... 
May  8 23:13:16 Barnaby nm-system-settings:    SCPlugin-Ifupdown: init!
May  8 23:13:16 Barnaby nm-system-settings:    SCPlugin-Ifupdown: update_system_hostname
May  8 23:13:16 Barnaby nm-system-settings:    SCPluginIfupdown: management mode: unmanaged
May  8 23:13:16 Barnaby nm-system-settings:    SCPlugin-Ifupdown: device added (udi: /org/freedesktop/Hal/devices/net_00_1c_23_fd_72_6c, iface: eth0): not well known
May  8 23:13:16 Barnaby nm-system-settings:    SCPlugin-Ifupdown: device added (udi: /org/freedesktop/Hal/devices/net_00_1c_bf_96_f1_aa, iface: wlan0): not well known
May  8 23:13:16 Barnaby nm-system-settings:    SCPlugin-Ifupdown: end _init.
May  8 23:13:16 Barnaby nm-system-settings: Loaded plugin ifupdown: (C) 2008 Canonical Ltd.  To report bugs please use the NetworkManager mailing list.
May  8 23:13:16 Barnaby nm-system-settings: Loaded plugin keyfile: (c) 2007 - 2008 Red Hat, Inc.  To report bugs please use the NetworkManager mailing list.
May  8 23:13:16 Barnaby nm-system-settings:    SCPlugin-Ifupdown: (36331984) ... get_connections.
May  8 23:13:16 Barnaby nm-system-settings:    SCPlugin-Ifupdown: (36331984) ... get_connections (managed=false): return empty list.
May  8 23:13:16 Barnaby nm-system-settings:    Ifupdown: get unmanaged devices count: 0
May  8 23:13:16 Barnaby NetworkManager: <info>  (wlan0): supplicant manager state:  down -> idle 
May  8 23:13:21 Barnaby NetworkManager: <info>  (eth0): device state change: 1 -> 2 
May  8 23:13:21 Barnaby NetworkManager: <info>  (eth0): bringing up device. 
May  8 23:13:21 Barnaby nm-system-settings: Added default wired connection 'Auto eth0' for /org/freedesktop/Hal/devices/net_00_1c_23_fd_72_6c
May  8 23:13:21 Barnaby NetworkManager: <info>  (eth0): preparing device. 
May  8 23:13:21 Barnaby NetworkManager: <info>  (eth0): deactivating device (reason: 2). 
May  8 23:13:21 Barnaby NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889) 
May  8 23:13:21 Barnaby NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889) 
May  8 23:13:21 Barnaby NetworkManager: <info>  (wlan0): device state change: 1 -> 2 
May  8 23:13:21 Barnaby NetworkManager: <info>  (wlan0): bringing up device. 
May  8 23:13:21 Barnaby NetworkManager: <info>  (wlan0): preparing device. 
May  8 23:13:21 Barnaby NetworkManager: <info>  (wlan0): deactivating device (reason: 2). 
May  8 23:13:21 Barnaby NetworkManager: <info>  (wlan0): device state change: 2 -> 3 
May  8 23:13:21 Barnaby NetworkManager: <info>  (wlan0): supplicant interface state:  starting -> ready 
May  8 23:13:22 Barnaby NetworkManager: <info>  (eth0): carrier now ON (device state 2) 
May  8 23:13:22 Barnaby NetworkManager: <info>  (eth0): device state change: 2 -> 3 
May  8 23:13:22 Barnaby NetworkManager: <info>  Activation (eth0) starting connection 'Auto eth0' 
May  8 23:13:22 Barnaby NetworkManager: <info>  (eth0): device state change: 3 -> 4 
May  8 23:13:22 Barnaby NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled... 
May  8 23:13:22 Barnaby NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) started... 
May  8 23:13:22 Barnaby NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) scheduled... 
May  8 23:13:22 Barnaby NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) complete. 
May  8 23:13:22 Barnaby NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) starting... 
May  8 23:13:22 Barnaby NetworkManager: <info>  (eth0): device state change: 4 -> 5 
May  8 23:13:22 Barnaby NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) successful. 
May  8 23:13:22 Barnaby NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled. 
May  8 23:13:22 Barnaby NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) complete. 
May  8 23:13:22 Barnaby NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) started... 
May  8 23:13:22 Barnaby NetworkManager: <info>  (eth0): device state change: 5 -> 7 
May  8 23:13:22 Barnaby NetworkManager: <info>  Activation (eth0) Beginning DHCP transaction. 
May  8 23:13:22 Barnaby NetworkManager: <info>  dhclient started with pid 3359 
May  8 23:13:22 Barnaby NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) complete. 
May  8 23:13:22 Barnaby dhclient: Internet Systems Consortium DHCP Client V3.1.1
May  8 23:13:22 Barnaby dhclient: Copyright 2004-2008 Internet Systems Consortium.
May  8 23:13:22 Barnaby dhclient: All rights reserved.
May  8 23:13:22 Barnaby dhclient: For info, please visit http://www.isc.org/sw/dhcp/
May  8 23:13:22 Barnaby dhclient: 
May  8 23:13:22 Barnaby dhclient: wmaster0: unknown hardware address type 801
May  8 23:13:22 Barnaby dhclient: wmaster0: unknown hardware address type 801
May  8 23:13:22 Barnaby NetworkManager: <info>  DHCP: device eth0 state changed (null) -> preinit 
May  8 23:13:22 Barnaby dhclient: Listening on LPF/eth0/00:1c:23:fd:72:6c
May  8 23:13:22 Barnaby dhclient: Sending on   LPF/eth0/00:1c:23:fd:72:6c
May  8 23:13:22 Barnaby dhclient: Sending on   Socket/fallback
May  8 23:13:23 Barnaby gdmgreeter[3358]: Gtk-CRITICAL: gtk_tree_view_get_selection: assertion `GTK_IS_TREE_VIEW (tree_view)' failed 
May  8 23:13:23 Barnaby gdmgreeter[3358]: Gtk-CRITICAL: gtk_tree_selection_unselect_all: assertion `GTK_IS_TREE_SELECTION (selection)' failed 
May  8 23:13:23 Barnaby gdmgreeter[3358]: Gtk-CRITICAL: gtk_tree_selection_select_iter: assertion `GTK_IS_TREE_SELECTION (selection)' failed 
May  8 23:13:23 Barnaby gdmgreeter[3358]: Gtk-CRITICAL: gtk_tree_view_scroll_to_cell: assertion `GTK_IS_TREE_VIEW (tree_view)' failed 
May  8 23:13:24 Barnaby avahi-daemon[3044]: Registering new address record for fe80::21c:23ff:fefd:726c on eth0.*.
May  8 23:13:25 Barnaby dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
May  8 23:13:26 Barnaby dhclient: DHCPOFFER of 192.168.1.101 from 192.168.1.1
May  8 23:13:26 Barnaby dhclient: DHCPREQUEST of 192.168.1.101 on eth0 to 255.255.255.255 port 67
May  8 23:13:26 Barnaby dhclient: DHCPACK of 192.168.1.101 from 192.168.1.1
May  8 23:13:26 Barnaby NetworkManager: <info>  DHCP: device eth0 state changed preinit -> bound 
May  8 23:13:26 Barnaby NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Get) scheduled... 
May  8 23:13:26 Barnaby NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Get) started... 
May  8 23:13:26 Barnaby NetworkManager: <info>    address 192.168.1.101 
May  8 23:13:26 Barnaby NetworkManager: <info>    prefix 24 (255.255.255.0) 
May  8 23:13:26 Barnaby NetworkManager: <info>    gateway 192.168.1.1 
May  8 23:13:26 Barnaby NetworkManager: <info>    hostname 'Barnaby' 
May  8 23:13:26 Barnaby NetworkManager: <info>    nameserver '68.87.85.98' 
May  8 23:13:26 Barnaby NetworkManager: <info>    nameserver '68.87.69.146' 
May  8 23:13:26 Barnaby NetworkManager: <info>    nameserver '68.87.78.130' 
May  8 23:13:26 Barnaby NetworkManager: <info>    domain name 'hsd1.ut.comcast.net.' 
May  8 23:13:26 Barnaby NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) scheduled... 
May  8 23:13:26 Barnaby NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Get) complete. 
May  8 23:13:26 Barnaby NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) started... 
May  8 23:13:26 Barnaby avahi-daemon[3044]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.1.101.
May  8 23:13:26 Barnaby avahi-daemon[3044]: New relevant interface eth0.IPv4 for mDNS.
May  8 23:13:26 Barnaby avahi-daemon[3044]: Registering new address record for 192.168.1.101 on eth0.IPv4.
May  8 23:13:26 Barnaby dhclient: bound to 192.168.1.101 -- renewal in 36169 seconds.
May  8 23:13:27 Barnaby NetworkManager: <info>  (eth0): device state change: 7 -> 8 
May  8 23:13:27 Barnaby NetworkManager: <info>  Policy set 'Auto eth0' (eth0) as default for routing and DNS. 
May  8 23:13:27 Barnaby NetworkManager: <info>  Activation (eth0) successful, device activated. 
May  8 23:13:27 Barnaby NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) complete. 
May  8 23:13:28 Barnaby ntpdate[3428]: adjust time server 91.189.94.4 offset -0.125220 sec
May  8 23:13:34 Barnaby gdm[2994]: WARNING: Couldn't authenticate user 
May  8 23:14:02 Barnaby console-kit-daemon[2779]: WARNING: Couldn't read /proc/2778/environ: Failed to open file '/proc/2778/environ': No such file or directory 
May  8 23:14:05 Barnaby x-session-manager[3466]: EggSMClient-WARNING: Desktop file '/home/jason/.config/autostart/cairo-dock-cairo.desktop' has malformed Icon key 'cairo-dock.svg'(should not include extension) 
May  8 23:47:48 Barnaby console-kit-daemon[2779]: GLib-GObject-WARNING: IA__g_object_get_valist: value location for `gchararray' passed as NULL 
May  8 23:47:48 Barnaby last message repeated 4 times
May  8 23:47:48 Barnaby init: tty4 main process (2574) killed by TERM signal
May  8 23:47:48 Barnaby init: tty5 main process (2575) killed by TERM signal
May  8 23:47:48 Barnaby init: tty2 main process (2578) killed by TERM signal
May  8 23:47:48 Barnaby init: tty3 main process (2581) killed by TERM signal
May  8 23:47:48 Barnaby init: tty6 main process (2582) killed by TERM signal
May  8 23:47:48 Barnaby init: tty1 main process (3321) killed by TERM signal
May  8 23:47:48 Barnaby console-kit-daemon[2779]: GLib-GObject-WARNING: IA__g_object_get_valist: value location for `gchararray' passed as NULL 
May  8 23:47:49 Barnaby console-kit-daemon[2779]: GLib-GObject-WARNING: instance of invalid non-instantiatable type `(null)' 
May  8 23:47:49 Barnaby console-kit-daemon[2779]: GLib-GObject-CRITICAL: g_signal_emit_valist: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed 
May  8 23:47:49 Barnaby console-kit-daemon[2779]: GLib-GObject-CRITICAL: g_object_unref: assertion `G_IS_OBJECT (object)' failed 
May  8 23:47:53 Barnaby bluetoothd[2958]: bridge pan0 removed
May  8 23:47:53 Barnaby bluetoothd[2958]: Stopping SDP server
May  8 23:47:53 Barnaby bluetoothd[2958]: Exit
May  8 23:49:16 Barnaby acpid: client connected from 2922[105:106] 
May  8 23:49:16 Barnaby bluetoothd[2956]: Bluetooth daemon
May  8 23:49:16 Barnaby bluetoothd[2956]: Starting SDP server
May  8 23:49:16 Barnaby bluetoothd[2956]: Starting experimental netlink support
May  8 23:49:16 Barnaby bluetoothd[2956]: Failed to find Bluetooth netlink family
May  8 23:49:16 Barnaby bluetoothd[2956]: Registered interface org.bluez.Service on path /org/bluez/2956/any
May  8 23:49:16 Barnaby bluetoothd[2956]: bridge pan0 created
May  8 23:49:17 Barnaby acpid: client connected from 2997[0:0] 
May  8 23:49:17 Barnaby NetworkManager: <info>  starting... 
May  8 23:49:17 Barnaby avahi-daemon[3041]: Found user 'avahi' (UID 108) and group 'avahi' (GID 114).
May  8 23:49:17 Barnaby avahi-daemon[3041]: Successfully dropped root privileges.
May  8 23:49:17 Barnaby avahi-daemon[3041]: avahi-daemon 0.6.23 starting up.
May  8 23:49:17 Barnaby avahi-daemon[3041]: Successfully called chroot().
May  8 23:49:17 Barnaby avahi-daemon[3041]: Successfully dropped remaining capabilities.
May  8 23:49:17 Barnaby NetworkManager: <info>  Found radio killswitch /org/freedesktop/Hal/devices/pci_8086_4222_rfkill_3945ABG_wlan 
May  8 23:49:17 Barnaby NetworkManager: <info>  Found radio killswitch /org/freedesktop/Hal/devices/dell_wlan_switch 
May  8 23:49:17 Barnaby NetworkManager: <info>  (eth0): new Ethernet device (driver: 'tg3') 
May  8 23:49:17 Barnaby NetworkManager: <info>  (eth0): exported as /org/freedesktop/Hal/devices/net_00_1c_23_fd_72_6c 
May  8 23:49:17 Barnaby avahi-daemon[3041]: No service file found in /etc/avahi/services.
May  8 23:49:17 Barnaby avahi-daemon[3041]: Network interface enumeration completed.
May  8 23:49:17 Barnaby avahi-daemon[3041]: Registering HINFO record with values 'X86_64'/'LINUX'.
May  8 23:49:17 Barnaby avahi-daemon[3041]: Server startup complete. Host name is Barnaby.local. Local service cookie is 1174523825.
May  8 23:49:17 Barnaby NetworkManager: <info>  (wlan0): driver supports SSID scans (scan_capa 0x01). 
May  8 23:49:17 Barnaby NetworkManager: <info>  (wlan0): new 802.11 WiFi device (driver: 'iwl3945') 
May  8 23:49:17 Barnaby NetworkManager: <info>  (wlan0): exported as /org/freedesktop/Hal/devices/net_00_1c_bf_96_f1_aa 
May  8 23:49:17 Barnaby NetworkManager: <info>  Trying to start the supplicant... 
May  8 23:49:17 Barnaby NetworkManager: <info>  Trying to start the system settings daemon... 
May  8 23:49:17 Barnaby nm-system-settings:    SCPlugin-Ifupdown: init!
May  8 23:49:17 Barnaby nm-system-settings:    SCPlugin-Ifupdown: update_system_hostname
May  8 23:49:17 Barnaby nm-system-settings:    SCPluginIfupdown: management mode: unmanaged
May  8 23:49:17 Barnaby nm-system-settings:    SCPlugin-Ifupdown: device added (udi: /org/freedesktop/Hal/devices/net_00_1c_23_fd_72_6c, iface: eth0): not well known
May  8 23:49:17 Barnaby nm-system-settings:    SCPlugin-Ifupdown: device added (udi: /org/freedesktop/Hal/devices/net_00_1c_bf_96_f1_aa, iface: wlan0): not well known
May  8 23:49:17 Barnaby nm-system-settings:    SCPlugin-Ifupdown: end _init.
May  8 23:49:17 Barnaby nm-system-settings: Loaded plugin ifupdown: (C) 2008 Canonical Ltd.  To report bugs please use the NetworkManager mailing list.
May  8 23:49:17 Barnaby nm-system-settings: Loaded plugin keyfile: (c) 2007 - 2008 Red Hat, Inc.  To report bugs please use the NetworkManager mailing list.
May  8 23:49:17 Barnaby nm-system-settings:    SCPlugin-Ifupdown: (33419728) ... get_connections.
May  8 23:49:17 Barnaby nm-system-settings:    SCPlugin-Ifupdown: (33419728) ... get_connections (managed=false): return empty list.
May  8 23:49:17 Barnaby nm-system-settings:    Ifupdown: get unmanaged devices count: 0
May  8 23:49:17 Barnaby NetworkManager: <info>  (wlan0): supplicant manager state:  down -> idle 
May  8 23:49:22 Barnaby NetworkManager: <info>  (eth0): device state change: 1 -> 2 
May  8 23:49:22 Barnaby NetworkManager: <info>  (eth0): bringing up device. 
May  8 23:49:22 Barnaby nm-system-settings: Added default wired connection 'Auto eth0' for /org/freedesktop/Hal/devices/net_00_1c_23_fd_72_6c
May  8 23:49:22 Barnaby NetworkManager: <info>  (eth0): preparing device. 
May  8 23:49:22 Barnaby NetworkManager: <info>  (eth0): deactivating device (reason: 2). 
May  8 23:49:22 Barnaby NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889) 
May  8 23:49:22 Barnaby NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889) 
May  8 23:49:22 Barnaby NetworkManager: <info>  (wlan0): device state change: 1 -> 2 
May  8 23:49:22 Barnaby NetworkManager: <info>  (wlan0): bringing up device. 
May  8 23:49:22 Barnaby NetworkManager: <info>  (wlan0): preparing device. 
May  8 23:49:22 Barnaby NetworkManager: <info>  (wlan0): deactivating device (reason: 2). 
May  8 23:49:22 Barnaby NetworkManager: <info>  (wlan0): device state change: 2 -> 3 
May  8 23:49:22 Barnaby NetworkManager: <info>  (wlan0): supplicant interface state:  starting -> ready 
May  8 23:49:23 Barnaby NetworkManager: <info>  (eth0): carrier now ON (device state 2) 
May  8 23:49:23 Barnaby NetworkManager: <info>  (eth0): device state change: 2 -> 3 
May  8 23:49:23 Barnaby NetworkManager: <info>  Activation (eth0) starting connection 'Auto eth0' 
May  8 23:49:23 Barnaby NetworkManager: <info>  (eth0): device state change: 3 -> 4 
May  8 23:49:23 Barnaby NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled... 
May  8 23:49:23 Barnaby NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) started... 
May  8 23:49:23 Barnaby NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) scheduled... 
May  8 23:49:23 Barnaby NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) complete. 
May  8 23:49:23 Barnaby NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) starting... 
May  8 23:49:23 Barnaby NetworkManager: <info>  (eth0): device state change: 4 -> 5 
May  8 23:49:23 Barnaby NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) successful. 
May  8 23:49:23 Barnaby NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled. 
May  8 23:49:23 Barnaby NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) complete. 
May  8 23:49:23 Barnaby NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) started... 
May  8 23:49:23 Barnaby NetworkManager: <info>  (eth0): device state change: 5 -> 7 
May  8 23:49:23 Barnaby NetworkManager: <info>  Activation (eth0) Beginning DHCP transaction. 
May  8 23:49:23 Barnaby NetworkManager: <info>  dhclient started with pid 3357 
May  8 23:49:23 Barnaby NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) complete. 
May  8 23:49:23 Barnaby dhclient: Internet Systems Consortium DHCP Client V3.1.1
May  8 23:49:23 Barnaby dhclient: Copyright 2004-2008 Internet Systems Consortium.
May  8 23:49:23 Barnaby dhclient: All rights reserved.
May  8 23:49:23 Barnaby dhclient: For info, please visit http://www.isc.org/sw/dhcp/
May  8 23:49:23 Barnaby dhclient: 
May  8 23:49:23 Barnaby dhclient: wmaster0: unknown hardware address type 801
May  8 23:49:23 Barnaby NetworkManager: <info>  DHCP: device eth0 state changed (null) -> preinit 
May  8 23:49:23 Barnaby dhclient: wmaster0: unknown hardware address type 801
May  8 23:49:23 Barnaby dhclient: Listening on LPF/eth0/00:1c:23:fd:72:6c
May  8 23:49:23 Barnaby dhclient: Sending on   LPF/eth0/00:1c:23:fd:72:6c
May  8 23:49:23 Barnaby dhclient: Sending on   Socket/fallback
May  8 23:49:24 Barnaby gdmgreeter[3356]: Gtk-CRITICAL: gtk_tree_view_get_selection: assertion `GTK_IS_TREE_VIEW (tree_view)' failed 
May  8 23:49:24 Barnaby gdmgreeter[3356]: Gtk-CRITICAL: gtk_tree_selection_unselect_all: assertion `GTK_IS_TREE_SELECTION (selection)' failed 
May  8 23:49:24 Barnaby gdmgreeter[3356]: Gtk-CRITICAL: gtk_tree_selection_select_iter: assertion `GTK_IS_TREE_SELECTION (selection)' failed 
May  8 23:49:24 Barnaby gdmgreeter[3356]: Gtk-CRITICAL: gtk_tree_view_scroll_to_cell: assertion `GTK_IS_TREE_VIEW (tree_view)' failed 
May  8 23:49:25 Barnaby avahi-daemon[3041]: Registering new address record for fe80::21c:23ff:fefd:726c on eth0.*.
May  8 23:49:27 Barnaby dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
May  8 23:49:28 Barnaby dhclient: DHCPOFFER of 192.168.1.101 from 192.168.1.1
May  8 23:49:28 Barnaby dhclient: DHCPREQUEST of 192.168.1.101 on eth0 to 255.255.255.255 port 67
May  8 23:49:28 Barnaby dhclient: DHCPACK of 192.168.1.101 from 192.168.1.1
May  8 23:49:28 Barnaby NetworkManager: <info>  DHCP: device eth0 state changed preinit -> bound 
May  8 23:49:28 Barnaby NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Get) scheduled... 
May  8 23:49:28 Barnaby NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Get) started... 
May  8 23:49:28 Barnaby NetworkManager: <info>    address 192.168.1.101 
May  8 23:49:28 Barnaby NetworkManager: <info>    prefix 24 (255.255.255.0) 
May  8 23:49:28 Barnaby NetworkManager: <info>    gateway 192.168.1.1 
May  8 23:49:28 Barnaby NetworkManager: <info>    hostname 'Barnaby' 
May  8 23:49:28 Barnaby NetworkManager: <info>    nameserver '68.87.85.98' 
May  8 23:49:28 Barnaby NetworkManager: <info>    nameserver '68.87.69.146' 
May  8 23:49:28 Barnaby NetworkManager: <info>    nameserver '68.87.78.130' 
May  8 23:49:28 Barnaby NetworkManager: <info>    domain name 'hsd1.ut.comcast.net.' 
May  8 23:49:28 Barnaby dhclient: bound to 192.168.1.101 -- renewal in 38688 seconds.
May  8 23:49:28 Barnaby NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) scheduled... 
May  8 23:49:28 Barnaby NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Get) complete. 
May  8 23:49:28 Barnaby NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) started... 
May  8 23:49:28 Barnaby avahi-daemon[3041]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.1.101.
May  8 23:49:28 Barnaby avahi-daemon[3041]: New relevant interface eth0.IPv4 for mDNS.
May  8 23:49:28 Barnaby avahi-daemon[3041]: Registering new address record for 192.168.1.101 on eth0.IPv4.
May  8 23:49:29 Barnaby NetworkManager: <info>  (eth0): device state change: 7 -> 8 
May  8 23:49:29 Barnaby NetworkManager: <info>  Policy set 'Auto eth0' (eth0) as default for routing and DNS. 
May  8 23:49:29 Barnaby NetworkManager: <info>  Activation (eth0) successful, device activated. 
May  8 23:49:29 Barnaby NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) complete. 
May  8 23:49:30 Barnaby ntpdate[3426]: adjust time server 91.189.94.4 offset -0.047629 sec
May  8 23:49:35 Barnaby console-kit-daemon[2777]: WARNING: Couldn't read /proc/2776/environ: Failed to open file '/proc/2776/environ': No such file or directory 
May  8 23:49:38 Barnaby x-session-manager[3447]: EggSMClient-WARNING: Desktop file '/home/jason/.config/autostart/cairo-dock-cairo.desktop' has malformed Icon key 'cairo-dock.svg'(should not include extension) 
May  9 01:09:28 Barnaby gdmsetup[16521]: GLib-GObject-CRITICAL: g_value_set_boolean: assertion `G_VALUE_HOLDS_BOOLEAN (value)' failed 
May  9 01:09:28 Barnaby gdmsetup[16521]: GLib-GObject-CRITICAL: g_value_get_boolean: assertion `G_VALUE_HOLDS_BOOLEAN (value)' failed 
May  9 01:09:28 Barnaby gdmsetup[16521]: GLib-GObject-CRITICAL: g_value_unset: assertion `G_IS_VALUE (value)' failed 
May  9 01:09:28 Barnaby gdmsetup[16521]: GLib-GObject-CRITICAL: g_value_set_boolean: assertion `G_VALUE_HOLDS_BOOLEAN (value)' failed 
May  9 01:09:28 Barnaby gdmsetup[16521]: GLib-GObject-CRITICAL: g_value_get_boolean: assertion `G_VALUE_HOLDS_BOOLEAN (value)' failed 
May  9 01:09:28 Barnaby gdmsetup[16521]: GLib-GObject-CRITICAL: g_value_unset: assertion `G_IS_VALUE (value)' failed 
```

---

### Post by lisati on 2009-05-09
I had a similar problem. I've seen elsewhere in the forums that sometimes having a Wifi card switched on or connected can sometimes cause the shutdown process to hang. On my laptops (which I usually have hooked up with a wired connection) I've found that leaving the built-in Wifi card switched off makes a difference.

---

### Post by slughappy1 on 2009-05-09
Why would that make a difference? It never has before on Unbuntu 7.04 - 8.10, or on Arch Linux.

---

### Post by lisati on 2009-05-09
> **slughappy1 said:**
> Why would that make a difference? It never has before on Unbuntu 7.04 - 8.10, or on Arch Linux.

I don't know.... I'm looking for a link that touches on this....


EDIT: One link: [http://ubuntuforums.org/showthread.php?t=1140584&highlight=wifi+shutdown&page=2](http://ubuntuforums.org/showthread.php?t=1140584&highlight=wifi+shutdown&page=2)

---

### Post by slughappy1 on 2009-05-09
@lisati
Thank you

@jeffreygg
I don't need a new one

---

### Post by slughappy1 on 2009-05-10
Thanks for all your help. It turns out it was the hardware switch for my wireless card. If it is turned off, my computer will turn off. If it is on... so is my computer. That seems like a weird bug to let back in though.

---

