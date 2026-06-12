---
title: "LAN dhcp/NetworkManager problem"
date: 2008-06-30
forum: Networking &amp; Wireless
---

### Post by Magicdead on 2008-06-30
ok first off, this is LAN, not WLAN, as the title says. Because when i try to google a solution, i only wind up with pages about WLAn problems. I don't have any WLAN-card on my pc.

Since about 4 days, when my pc boots, it has no network connection to my Netgear WGT624v3 router.
```
 Account Name  	WGT624v3
Hardware Version 	V3H1
Firmware Version 	V2.0.16_1.0.1
```

this seems to be the relevant parts of my syslog:
```

Jun 30 10:48:19 Masterchief kernel: [   37.222081] udev: renamed network interface eth0 to eth1
Jun 30 10:48:19 Masterchief NetworkManager: <info>  starting... 
Jun 30 10:48:20 Masterchief avahi-daemon[5581]: Found user 'avahi' (UID 113) and group 'avahi' (GID 119).
Jun 30 10:48:20 Masterchief avahi-daemon[5581]: Successfully dropped root privileges.
Jun 30 10:48:20 Masterchief avahi-daemon[5581]: avahi-daemon 0.6.22 starting up.
Jun 30 10:48:20 Masterchief avahi-daemon[5581]: Successfully called chroot().
Jun 30 10:48:20 Masterchief avahi-daemon[5581]: Successfully dropped remaining capabilities.
Jun 30 10:48:20 Masterchief avahi-daemon[5581]: No service file found in /etc/avahi/services.
Jun 30 10:48:20 Masterchief avahi-daemon[5581]: Network interface enumeration completed.
Jun 30 10:48:20 Masterchief avahi-daemon[5581]: Registering HINFO record with values 'I686'/'LINUX'.
Jun 30 10:48:20 Masterchief avahi-daemon[5581]: Server startup complete. Host name is Masterchief.local. Local service cookie is 964637263.
Jun 30 10:48:30 Masterchief dhcdbd: Started up.
Jun 30 10:48:31 Masterchief kernel: [   67.335663] eth1: link up, 100Mbps, full-duplex, lpa 0x41E1
Jun 30 10:48:31 Masterchief NetworkManager: <info>  eth1: Device is fully-supported using driver '8139too'. 
Jun 30 10:48:31 Masterchief NetworkManager: <info>  nm_device_init(): waiting for device's worker thread to start 
Jun 30 10:48:31 Masterchief NetworkManager: <info>  nm_device_init(): device's worker thread started, continuing. 
Jun 30 10:48:31 Masterchief NetworkManager: <info>  Now managing wired Ethernet (802.3) device 'eth1'. 
Jun 30 10:48:31 Masterchief NetworkManager: <info>  Deactivating device eth1. 
Jun 30 10:48:31 Masterchief NetworkManager: <info>  Will activate wired connection 'eth1' because it now has a link. 
Jun 30 10:48:31 Masterchief NetworkManager: <debug> [1214815711.986738] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_model_Virt__CD/DVD_ROM_2'). 
Jun 30 10:48:31 Masterchief NetworkManager: <info>  SWITCH: no current connection, found better connection 'eth1'. 
Jun 30 10:48:32 Masterchief dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.reason
Jun 30 10:48:32 Masterchief NetworkManager: <info>  Will activate connection 'eth1'. 
Jun 30 10:48:32 Masterchief NetworkManager: <info>  Device eth1 activation scheduled... 
Jun 30 10:48:32 Masterchief NetworkManager: <debug> [1214815712.988324] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_bluetooth'). 
Jun 30 10:48:32 Masterchief NetworkManager: <info>  Activation (eth1) started... 
Jun 30 10:48:32 Masterchief NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled... 
Jun 30 10:48:32 Masterchief NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) started... 
Jun 30 10:48:32 Masterchief NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) scheduled... 
Jun 30 10:48:32 Masterchief NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) complete. 
Jun 30 10:48:32 Masterchief NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) starting... 
Jun 30 10:48:32 Masterchief NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) successful. 
Jun 30 10:48:32 Masterchief NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) scheduled. 
Jun 30 10:48:32 Masterchief NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) complete. 
Jun 30 10:48:32 Masterchief NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) started... 
Jun 30 10:48:33 Masterchief kernel: [   69.187262] NET: Registered protocol family 10
Jun 30 10:48:33 Masterchief kernel: [   69.187621] lo: Disabled Privacy Extensions
Jun 30 10:48:33 Masterchief NetworkManager: <info>  Activation (eth1) Beginning DHCP transaction. 
Jun 30 10:48:33 Masterchief NetworkManager: <info>  DHCP daemon state is now 12 (successfully started) for interface eth1 
Jun 30 10:48:33 Masterchief NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) complete. 
Jun 30 10:48:35 Masterchief avahi-daemon[5581]: Registering new address record for fe80::219:66ff:fe10:759 on eth1.*.
Jun 30 10:48:35 Masterchief NetworkManager: <info>  DHCP daemon state is now 1 (starting) for interface eth1 
Jun 30 10:48:35 Masterchief ntpd[6701]: ntpd 4.2.4p4@1.1520-o Fri Mar  7 20:24:07 UTC 2008 (1)
Jun 30 10:48:35 Masterchief ntpd[6702]: precision = 1.000 usec
Jun 30 10:48:35 Masterchief ntpd[6702]: Listening on interface #0 wildcard, 0.0.0.0#123 Disabled
Jun 30 10:48:35 Masterchief ntpd[6702]: Listening on interface #1 wildcard, ::#123 Disabled
Jun 30 10:48:35 Masterchief ntpd[6702]: Listening on interface #2 eth1, fe80::219:66ff:fe10:759#123 Enabled
Jun 30 10:48:35 Masterchief ntpd[6702]: Listening on interface #3 lo, ::1#123 Enabled
Jun 30 10:48:35 Masterchief ntpd[6702]: Listening on interface #4 lo, 127.0.0.1#123 Enabled
Jun 30 10:48:35 Masterchief ntpd[6702]: kernel time sync status 0040
Jun 30 10:48:35 Masterchief ntpd[6702]: frequency initialized 18.176 PPM from /var/lib/ntp/ntp.drift
Jun 30 10:48:35 Masterchief anacron[6722]: Anacron 2.3 started on 2008-06-30
Jun 30 10:48:35 Masterchief anacron[6722]: Will run job `cron.daily' in 5 min.
Jun 30 10:48:35 Masterchief anacron[6722]: Jobs will be executed sequentially
Jun 30 10:48:35 Masterchief dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
Jun 30 10:48:36 Masterchief /usr/sbin/cron[6749]: (CRON) INFO (pidfile fd = 3)
Jun 30 10:48:36 Masterchief /usr/sbin/cron[6750]: (CRON) STARTUP (fork ok)
Jun 30 10:48:36 Masterchief /usr/sbin/cron[6750]: (CRON) INFO (Running @reboot jobs)
Jun 30 10:48:37 Masterchief dhclient: DHCPOFFER of 192.168.1.2 from 192.168.1.1
Jun 30 10:48:37 Masterchief dhclient: DHCPREQUEST of 192.168.1.2 on eth1 to 255.255.255.255 port 67
Jun 30 10:48:37 Masterchief ntpd_initres[6721]: host name not found: ntp.ubuntu.com
Jun 30 10:48:37 Masterchief ntpd_initres[6721]: couldn't resolve `ntp.ubuntu.com', giving up on it
Jun 30 10:48:39 Masterchief NetworkManager: <debug> [1214815719.105962] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_vhba_scsi_host_scsi_device_lun0_3'). 
Jun 30 10:48:39 Masterchief NetworkManager: <debug> [1214815719.114932] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_vhba_scsi_host_scsi_device_lun0_4'). 
Jun 30 10:48:39 Masterchief NetworkManager: <debug> [1214815719.132158] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_vhba_scsi_host_scsi_device_lun0_5'). 
Jun 30 10:48:39 Masterchief NetworkManager: <debug> [1214815719.140301] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_vhba_scsi_host_scsi_device_lun0_3_scsi_generic'). 
Jun 30 10:48:39 Masterchief NetworkManager: <debug> [1214815719.140846] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_vhba_scsi_host_scsi_device_lun0_5_scsi_generic'). 
Jun 30 10:48:39 Masterchief NetworkManager: <debug> [1214815719.141291] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_vhba_scsi_host_scsi_device_lun0_4_scsi_generic'). 
Jun 30 10:48:39 Masterchief NetworkManager: <debug> [1214815719.166130] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_vhba_scsi_host_scsi_device_lun0_6'). 
Jun 30 10:48:39 Masterchief NetworkManager: <debug> [1214815719.170043] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_vhba_scsi_host_scsi_device_lun0_6_scsi_generic'). 
Jun 30 10:48:39 Masterchief NetworkManager: <debug> [1214815719.172805] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_model_Virt__CD/DVD_ROM_3'). 
Jun 30 10:48:39 Masterchief NetworkManager: <debug> [1214815719.193473] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_model_Virt__CD/DVD_ROM_4'). 
Jun 30 10:48:39 Masterchief NetworkManager: <debug> [1214815719.207877] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_model_Virt__CD/DVD_ROM_5'). 
Jun 30 10:48:39 Masterchief NetworkManager: <debug> [1214815719.224067] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_model_Virt__CD/DVD_ROM_6'). 
Jun 30 10:48:39 Masterchief dhclient: DHCPACK of 192.168.1.2 from 192.168.1.1
Jun 30 10:48:39 Masterchief avahi-daemon[5581]: Joining mDNS multicast group on interface eth1.IPv4 with address 192.168.1.2.
Jun 30 10:48:39 Masterchief avahi-daemon[5581]: New relevant interface eth1.IPv4 for mDNS.
Jun 30 10:48:39 Masterchief avahi-daemon[5581]: Registering new address record for 192.168.1.2 on eth1.IPv4.
Jun 30 10:48:39 Masterchief dhclient: bound to 192.168.1.2 -- renewal in 932667928 seconds.
Jun 30 10:49:27 Masterchief NetworkManager: <info>  Updating allowed wireless network lists. 
Jun 30 10:49:27 Masterchief NetworkManager: <WARN>  nm_dbus_get_networks_cb(): error received: org.freedesktop.NetworkManagerInfo.NoNetworks - There are no wireless networks stored.. 
Jun 30 10:49:27 Masterchief NetworkManager: <info>  Disconnected. 
Jun 30 10:49:27 Masterchief NetworkManager: <info>  Activation (eth1): cancelling... 
Jun 30 10:49:27 Masterchief NetworkManager: <info>  Activation (eth1) cancellation handler scheduled... 
Jun 30 10:49:27 Masterchief NetworkManager: <info>  Activation (eth1): waiting for device to cancel activation. 
Jun 30 10:49:27 Masterchief NetworkManager: <info>  Activation (eth1) cancellation handled. 
Jun 30 10:49:27 Masterchief dhclient: There is already a pid file /var/run/dhclient.eth1.pid with pid 6666
Jun 30 10:49:27 Masterchief dhclient: killed old client process, removed PID file
Jun 30 10:49:27 Masterchief NetworkManager: <info>  Activation (eth1): cancelled. 
Jun 30 10:49:27 Masterchief avahi-daemon[5581]: Interface eth1.IPv4 no longer relevant for mDNS.
Jun 30 10:49:27 Masterchief avahi-daemon[5581]: Leaving mDNS multicast group on interface eth1.IPv4 with address 192.168.1.2.
Jun 30 10:49:27 Masterchief avahi-daemon[5581]: Withdrawing address record for fe80::219:66ff:fe10:759 on eth1.
Jun 30 10:49:27 Masterchief avahi-daemon[5581]: Withdrawing address record for 192.168.1.2 on eth1.
Jun 30 10:49:30 Masterchief dhclient: DHCPRELEASE on eth1 to 192.168.1.1 port 67
Jun 30 10:49:30 Masterchief dhclient: send_packet: Network is unreachable
Jun 30 10:49:30 Masterchief dhclient: send_packet: please consult README file regarding broadcast address.
Jun 30 10:49:30 Masterchief kernel: [  126.324965] eth1: link up, 100Mbps, full-duplex, lpa 0x41E1
Jun 30 10:49:30 Masterchief NetworkManager: <info>  Will activate wired connection 'eth1' because it now has a link. 
Jun 30 10:49:32 Masterchief avahi-daemon[5581]: Registering new address record for fe80::219:66ff:fe10:759 on eth1.*.
Jun 30 10:49:41 Masterchief kernel: [  136.813949] eth1: no IPv6 routers present

```(i left out some anacron stuff that seems to be unrelated, but if you want the full log, i'll gladly post it)

Now, if i do "sudo dhclient" once i'm logged in, everything works like a charm, it connects fine, my internet is working and i have no further problems, except that the network-applet in the gnome-panel still is on disconnected aand that i have to get some aps (like weather plugin) to manually update.

This is ubuntu hardy, 2.6.24-19-generic.
```
lspci |grep Ethernet
02:05.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

```
i'm not sure what initially cause the problem, though i think it might have been some update around 4 days ago.

While i could live with having to do the sudo dhclient bit every boot, i find it rather annoying and help would be greatly apreciated.

Thanks in advance

---

