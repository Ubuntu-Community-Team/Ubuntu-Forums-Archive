---
title: "Wireless only somtimes works upon reboot, always dies after a short time"
date: 2008-01-30
forum: Networking &amp; Wireless
---

### Post by Kawayanan on 2008-01-30
I have a mythbuntu box that has a Netgear WG111V2 usb wireless adapter.  I didn't have the adapter when I did the install and had to add it later (halted, added the adapter, and restarted).  I don't have a ethernet wire pulled to the area, so the wireless is then only network connection.  The nwireless router is an older 802.11 b netgear router.  It is running WEP and MAC filtering.  It is only a room away from where my mythbuntu box is and the signal strength is fine.

When I reboot, the wireless usually comes up (about 3/4 the time).  It will seem to work fine for a little while, then suddenly die.  While it works, the connection seems fine.  I can download updates, surf the web, and ssh in.  The amount of time the network stays up seems to vary, but its never too long (les than 10 min).

Here is what I can find in /var/log/syslog for a reboot when the network comes up, then dies (I am cutting out stuff that doesn't seem to be related, but can post the whole thing if needed):

```
Jan 30 20:06:47 mythbox NetworkManager: <info>  starting... 
Jan 30 20:06:48 mythbox dhclient: DHCPREQUEST on wlan0 to 255.255.255.255 port 67

Jan 30 20:06:48 mythbox kernel: [   40.971984] wlan0: Initial auth_alg=0
Jan 30 20:06:48 mythbox kernel: [   40.971988] wlan0: authenticate with AP 00:09:5b:3e:0a:b6
Jan 30 20:06:48 mythbox kernel: [   40.975092] wlan0: RX authentication from 00:09:5b:3e:0a:b6 (alg=0 transaction=2 status=0)
Jan 30 20:06:48 mythbox kernel: [   40.975095] wlan0: authenticated
Jan 30 20:06:48 mythbox kernel: [   40.975097] wlan0: associate with AP 00:09:5b:3e:0a:b6
Jan 30 20:06:48 mythbox kernel: [   40.977461] wlan0: RX AssocResp from 00:09:5b:3e:0a:b6 (capab=0x1 status=0 aid=4)
Jan 30 20:06:48 mythbox kernel: [   40.977463] wlan0: associated
Jan 30 20:06:48 mythbox kernel: [   41.035600] eth0: no link during initialization.
Jan 30 20:06:48 mythbox NetworkManager: <info>  eth0: Device is fully-supported using driver 'forcedeth'. 
Jan 30 20:06:48 mythbox NetworkManager: <info>  nm_device_init(): waiting for device's worker thread to start 
Jan 30 20:06:49 mythbox NetworkManager: <info>  nm_device_init(): device's worker thread started, continuing. 
Jan 30 20:06:49 mythbox NetworkManager: <info>  Now managing wired Ethernet (802.3) device 'eth0'. 
Jan 30 20:06:49 mythbox NetworkManager: <info>  Deactivating device eth0. 
Jan 30 20:06:49 mythbox NetworkManager: <info>  Will activate wired connection 'eth0' because it now has a link. 
Jan 30 20:06:49 mythbox NetworkManager: <info>  SWITCH: no current connection, found better connection 'eth0'. 
Jan 30 20:06:49 mythbox NetworkManager: <WARN>  nm_dhcp_manager_get_state_for_device(): dhcdbd not running! 
Jan 30 20:06:49 mythbox NetworkManager: <info>  Will activate connection 'eth0'. 
Jan 30 20:06:49 mythbox NetworkManager: <info>  Device eth0 activation scheduled... 
Jan 30 20:06:49 mythbox NetworkManager: <info>  Activation (eth0) started... 
Jan 30 20:06:49 mythbox NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled... 
Jan 30 20:06:49 mythbox NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) started... 
Jan 30 20:06:49 mythbox NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) scheduled... 
Jan 30 20:06:49 mythbox NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) complete. 
Jan 30 20:06:49 mythbox NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) starting... 
Jan 30 20:06:49 mythbox NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) successful. 
Jan 30 20:06:49 mythbox NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled. 
Jan 30 20:06:49 mythbox NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) complete. 
Jan 30 20:06:49 mythbox NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) started... 
Jan 30 20:06:49 mythbox NetworkManager: <WARN>  nm_dhcp_manager_begin_transaction(): dhcdbd not running! 
Jan 30 20:06:49 mythbox NetworkManager: <info>  Activation (eth0) failure scheduled... 
Jan 30 20:06:49 mythbox NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) complete. 
Jan 30 20:06:49 mythbox kernel: [   41.555032] NET: Registered protocol family 10
Jan 30 20:06:49 mythbox kernel: [   41.555152] lo: Disabled Privacy Extensions
Jan 30 20:06:49 mythbox kernel: [   41.555322] ADDRCONF(NETDEV_UP): eth0: link is not ready
Jan 30 20:06:49 mythbox NetworkManager: <info>  Activation (eth0) failed. 
Jan 30 20:06:49 mythbox NetworkManager: <info>  Deactivating device eth0. 
Jan 30 20:06:49 mythbox NetworkManager: <info>  SWITCH: no current connection, found better connection 'eth0'. 
Jan 30 20:06:49 mythbox NetworkManager: <WARN>  nm_dhcp_manager_get_state_for_device(): dhcdbd not running! 
Jan 30 20:06:49 mythbox NetworkManager: <info>  Will activate connection 'eth0'. 
Jan 30 20:06:49 mythbox NetworkManager: <info>  Device eth0 activation scheduled... 
Jan 30 20:06:49 mythbox NetworkManager: <info>  Activation (eth0) started... 
Jan 30 20:06:49 mythbox NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled... 
Jan 30 20:06:49 mythbox NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) started... 
Jan 30 20:06:49 mythbox NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) scheduled... 
Jan 30 20:06:49 mythbox NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) complete. 
Jan 30 20:06:49 mythbox NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) starting... 
Jan 30 20:06:49 mythbox NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) successful. 
Jan 30 20:06:49 mythbox NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled. 
Jan 30 20:06:49 mythbox NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) complete. 
Jan 30 20:06:49 mythbox NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) started... 
Jan 30 20:06:49 mythbox NetworkManager: <WARN>  nm_dhcp_manager_begin_transaction(): dhcdbd not running! 
Jan 30 20:06:49 mythbox NetworkManager: <info>  Activation (eth0) failure scheduled... 
Jan 30 20:06:49 mythbox NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) complete. 
Jan 30 20:06:49 mythbox NetworkManager: <info>  Activation (eth0) failed. 
Jan 30 20:06:49 mythbox NetworkManager: <info>  Deactivating device eth0. 
Jan 30 20:06:49 mythbox NetworkManager: <info>  SWITCH: no current connection, found better connection 'eth0'. 
Jan 30 20:06:49 mythbox NetworkManager: <WARN>  nm_dhcp_manager_get_state_for_device(): dhcdbd not running! 
Jan 30 20:06:49 mythbox NetworkManager: <info>  Will activate connection 'eth0'. 
Jan 30 20:06:49 mythbox NetworkManager: <info>  Device eth0 activation scheduled... 
Jan 30 20:06:49 mythbox NetworkManager: <info>  Activation (eth0) started... 
Jan 30 20:06:49 mythbox NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled... 
Jan 30 20:06:49 mythbox NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) started... 
Jan 30 20:06:49 mythbox NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) scheduled... 
Jan 30 20:06:49 mythbox NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) complete. 
Jan 30 20:06:49 mythbox NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) starting... 
Jan 30 20:06:49 mythbox NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) successful. 
Jan 30 20:06:49 mythbox NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled. 
Jan 30 20:06:49 mythbox NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) complete. 
Jan 30 20:06:49 mythbox NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) started... 
Jan 30 20:06:49 mythbox NetworkManager: <WARN>  nm_dhcp_manager_begin_transaction(): dhcdbd not running! 
Jan 30 20:06:49 mythbox NetworkManager: <info>  Activation (eth0) failure scheduled... 
Jan 30 20:06:49 mythbox NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) complete. 
Jan 30 20:06:49 mythbox NetworkManager: <info>  SWITCH: terminating current connection 'eth0' because it's no longer valid. 
Jan 30 20:06:49 mythbox NetworkManager: <info>  Deactivating device eth0. 
Jan 30 20:06:49 mythbox NetworkManager: nm_device_is_802_3_ethernet: assertion `dev != NULL' failed
Jan 30 20:06:49 mythbox NetworkManager: nm_device_is_802_11_wireless: assertion `dev != NULL' failed
Jan 30 20:06:50 mythbox NetworkManager: <info>  Activation (eth0) failed. 
Jan 30 20:06:50 mythbox NetworkManager: <info>  Deactivating device eth0. 
Jan 30 20:06:51 mythbox dhclient: DHCPREQUEST on wlan0 to 255.255.255.255 port 67

Jan 30 20:06:52 mythbox dhclient: DHCPACK from 192.168.0.1
Jan 30 20:06:52 mythbox dhclient: bound to 192.168.0.13 -- renewal in 242681 seconds.

Jan 30 20:06:55 mythbox ntpd[5462]: ntpd 4.2.4p0@1.1472-o Thu Oct  4 22:22:31 UTC 2007 (1)
Jan 30 20:06:55 mythbox ntpd[5463]: precision = 1.000 usec
Jan 30 20:06:55 mythbox ntpd[5463]: Listening on interface #0 wildcard, 0.0.0.0#123 Disabled
Jan 30 20:06:55 mythbox ntpd[5463]: Listening on interface #1 wildcard, ::#123 Disabled
Jan 30 20:06:55 mythbox ntpd[5463]: Listening on interface #2 lo, ::1#123 Enabled
Jan 30 20:06:55 mythbox ntpd[5463]: Listening on interface #3 wlan0, fe80::21b:2fff:feea:c4c9#123 Enabled
Jan 30 20:06:55 mythbox ntpd[5463]: Listening on interface #4 lo, 127.0.0.1#123 Enabled
Jan 30 20:06:55 mythbox ntpd[5463]: Listening on interface #5 wlan0, 192.168.0.13#123 Enabled
Jan 30 20:06:55 mythbox ntpd[5463]: kernel time sync status 0040
Jan 30 20:06:55 mythbox ntpd[5463]: frequency initialized 0.201 PPM from /var/lib/ntp/ntp.drift
Jan 30 20:06:56 mythbox dhcdbd: Started up.
Jan 30 20:06:58 mythbox gdm[5577]: WARNING: Didn't understand `' (expected true or false) 
Jan 30 20:06:58 mythbox ntpdate[5419]: the NTP socket is in use, exiting
Jan 30 20:06:59 mythbox kernel: [   51.684528] wlan0: no IPv6 routers present
Jan 30 20:07:00 mythbox /usr/sbin/cron[5638]: (CRON) INFO (pidfile fd = 3)
Jan 30 20:07:00 mythbox /usr/sbin/cron[5641]: (CRON) STARTUP (fork ok)
Jan 30 20:07:00 mythbox /usr/sbin/cron[5641]: (CRON) INFO (Running @reboot jobs)
Jan 30 20:07:08 mythbox NetworkManager: <info>  Updating allowed wireless network lists. 
Jan 30 20:07:08 mythbox NetworkManager: <WARN>  nm_dbus_get_networks_cb(): error received: org.freedesktop.NetworkManagerInfo.NoNetworks - There are no wireless networks stored.. 
Jan 30 20:07:11 mythbox lircd-0.8.2[4122]: accepted new client on /dev/lircd
Jan 30 20:09:01 mythbox /USR/SBIN/CRON[5936]: (root) CMD (  [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -r -0 rm)
Jan 30 20:09:06 mythbox kernel: [  178.732761] WEP decrypt failed (ICV)
Jan 30 20:09:06 mythbox kernel: [  178.732768] wlan0: RX WEP frame, decrypt failed
Jan 30 20:12:19 mythbox ntpd[5463]: synchronized to 91.189.94.4, stratum 2
Jan 30 20:12:19 mythbox ntpd[5463]: time reset -0.291424 s
Jan 30 20:12:19 mythbox ntpd[5463]: kernel time sync status change 0001
Jan 30 20:14:20 mythbox kernel: [  492.918469] WEP decrypt failed (ICV)
Jan 30 20:14:20 mythbox kernel: [  492.918476] wlan0: RX WEP frame, decrypt failed
Jan 30 20:17:01 mythbox /USR/SBIN/CRON[6003]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jan 30 20:18:15 mythbox ntpd[5463]: synchronized to 91.189.94.4, stratum 2
Jan 30 20:20:40 mythbox kernel: [  872.007654] WEP decrypt failed (ICV)
Jan 30 20:20:40 mythbox kernel: [  872.007660] wlan0: RX WEP frame, decrypt failed
Jan 30 20:25:55 mythbox kernel: [ 1186.828293] WEP decrypt failed (ICV)
Jan 30 20:25:55 mythbox kernel: [ 1186.828300] wlan0: RX WEP frame, decrypt failed
Jan 30 20:26:57 mythbox kernel: [ 1249.078073] WEP decrypt failed (ICV)
Jan 30 20:26:57 mythbox kernel: [ 1249.078080] wlan0: RX WEP frame, decrypt failed
Jan 30 20:28:00 mythbox kernel: [ 1311.906047] WEP decrypt failed (ICV)
Jan 30 20:28:00 mythbox kernel: [ 1311.906053] wlan0: RX WEP frame, decrypt failed
Jan 30 20:29:05 mythbox kernel: [ 1376.825688] WEP decrypt failed (ICV)
Jan 30 20:29:05 mythbox kernel: [ 1376.825695] wlan0: RX WEP frame, decrypt failed
Jan 30 20:31:10 mythbox kernel: [ 1501.360497] WEP decrypt failed (ICV)
Jan 30 20:31:10 mythbox kernel: [ 1501.360505] wlan0: RX WEP frame, decrypt failed
Jan 30 20:31:11 mythbox kernel: [ 1502.383467] WEP decrypt failed (ICV)
Jan 30 20:31:11 mythbox kernel: [ 1502.383474] wlan0: RX WEP frame, decrypt failed
Jan 30 20:32:14 mythbox kernel: [ 1565.469232] WEP decrypt failed (ICV)
Jan 30 20:32:14 mythbox kernel: [ 1565.469239] wlan0: RX WEP frame, decrypt failed
Jan 30 20:35:24 mythbox kernel: [ 1755.079775] WEP decrypt failed (ICV)
Jan 30 20:35:24 mythbox kernel: [ 1755.079783] wlan0: RX WEP frame, decrypt failed

``` 

It doesn't always seem to have the "Activation (eth0)" stuff, but the "WEP decrypt failed (ICV)" and "wlan0: RX WEP frame, decrypt failed" always seem to show up in the end.  I believe they are already showing up while the network is still working, but there are not other log entries that show up before the network goes down.

Occasionally, the network never comes up after a reboot.  Here is what the /var/log/syslog shows in those cases:

```
Jan 30 18:45:39 mythbox NetworkManager: <info>  starting... 
Jan 30 18:45:40 mythbox kernel: [   41.785595] eth0: no link during initialization.
Jan 30 18:45:40 mythbox NetworkManager: <info>  eth0: Device is fully-supported using driver 'forcedeth'. 
Jan 30 18:45:40 mythbox NetworkManager: <info>  nm_device_init(): waiting for device's worker thread to start 
Jan 30 18:45:40 mythbox NetworkManager: <info>  nm_device_init(): device's worker thread started, continuing. 
Jan 30 18:45:40 mythbox NetworkManager: <info>  Now managing wired Ethernet (802.3) device 'eth0'. 
Jan 30 18:45:40 mythbox NetworkManager: <info>  Deactivating device eth0. 
Jan 30 18:45:40 mythbox kernel: [   42.105583] wlan0: Initial auth_alg=0
Jan 30 18:45:40 mythbox kernel: [   42.105589] wlan0: authenticate with AP 00:09:5b:3e:0a:b6
Jan 30 18:45:40 mythbox NetworkManager: <debug> [1201736740.803095] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_serial_ASUS_Flash_HS_COMBO_000022272228_0_1'). 
Jan 30 18:45:40 mythbox NetworkManager: <info>  Will activate wired connection 'eth0' because it now has a link. 
Jan 30 18:45:40 mythbox kernel: [   42.108831] wlan0: RX authentication from 00:09:5b:3e:0a:b6 (alg=0 transaction=2 status=0)
Jan 30 18:45:40 mythbox kernel: [   42.108836] wlan0: authenticated
Jan 30 18:45:40 mythbox kernel: [   42.108839] wlan0: associate with AP 00:09:5b:3e:0a:b6
Jan 30 18:45:40 mythbox kernel: [   42.111186] wlan0: RX AssocResp from 00:09:5b:3e:0a:b6 (capab=0x1 status=0 aid=4)
Jan 30 18:45:40 mythbox kernel: [   42.111189] wlan0: associated
Jan 30 18:45:40 mythbox kernel: [   42.202071] NET: Registered protocol family 10
Jan 30 18:45:40 mythbox kernel: [   42.202227] lo: Disabled Privacy Extensions
Jan 30 18:45:40 mythbox kernel: [   42.202450] ADDRCONF(NETDEV_UP): eth0: link is not ready
Jan 30 18:45:43 mythbox dhclient: DHCPREQUEST on wlan0 to 255.255.255.255 port 67
Jan 30 18:45:44 mythbox kernel: [   45.734904] wlan0: No ProbeResp from current AP 00:09:5b:3e:0a:b6 - assume out of range
Jan 30 18:45:46 mythbox ntpd[5376]: ntpd 4.2.4p0@1.1472-o Thu Oct  4 22:22:31 UTC 2007 (1)
Jan 30 18:45:46 mythbox ntpd[5377]: precision = 1.000 usec
Jan 30 18:45:46 mythbox ntpd[5377]: Listening on interface #0 wildcard, 0.0.0.0#123 Disabled
Jan 30 18:45:46 mythbox ntpd[5377]: Listening on interface #1 wildcard, ::#123 Disabled
Jan 30 18:45:46 mythbox ntpd[5377]: Listening on interface #2 lo, ::1#123 Enabled
Jan 30 18:45:46 mythbox ntpd[5377]: Listening on interface #3 wlan0, fe80::21b:2fff:feea:c4c9#123 Enabled
Jan 30 18:45:46 mythbox ntpd[5377]: Listening on interface #4 lo, 127.0.0.1#123 Enabled
Jan 30 18:45:46 mythbox ntpd[5377]: kernel time sync status 0040
Jan 30 18:45:46 mythbox ntpd[5377]: frequency initialized 0.201 PPM from /var/lib/ntp/ntp.drift
Jan 30 18:45:46 mythbox ntpd[5382]: signal_no_reset: signal 17 had flags 4000000
Jan 30 18:45:47 mythbox dhcdbd: Started up.
Jan 30 18:45:48 mythbox ntpd_initres[5382]: host name not found: ntp.ubuntu.com
Jan 30 18:45:48 mythbox ntpd_initres[5382]: couldn't resolve `ntp.ubuntu.com', giving up on it
Jan 30 18:45:50 mythbox dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
Jan 30 18:45:51 mythbox kernel: [   52.598561] wlan0: no IPv6 routers present
Jan 30 18:45:56 mythbox dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
Jan 30 18:46:07 mythbox NetworkManager: <info>  Updating allowed wireless network lists. 
Jan 30 18:46:08 mythbox NetworkManager: <WARN>  nm_dbus_get_networks_cb(): error received: org.freedesktop.NetworkManagerInfo.NoNetworks - There are no wireless networks stored.. 
Jan 30 18:46:08 mythbox dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
Jan 30 18:46:10 mythbox lircd-0.8.2[4133]: accepted new client on /dev/lircd
Jan 30 18:46:16 mythbox kernel: [   77.711149] wlan0: No STA entry for own AP 00:09:5b:3e:0a:b6
Jan 30 18:46:21 mythbox dhclient: No DHCPOFFERS received.
Jan 30 18:46:21 mythbox dhclient: Trying recorded lease 192.168.0.13
Jan 30 18:46:24 mythbox dhclient: No working leases in persistent database - sleeping.
Jan 30 18:46:24 mythbox ntpdate[5787]: can't find host ntp.ubuntu.com 
Jan 30 18:46:24 mythbox ntpdate[5787]: no servers can be used, exiting
Jan 30 18:46:48 mythbox kernel: [  109.686417] wlan0: No STA entry for own AP 00:09:5b:3e:0a:b6
Jan 30 18:47:20 mythbox kernel: [  141.661676] wlan0: No STA entry for own AP 00:09:5b:3e:0a:b6
Jan 30 18:47:29 mythbox NetworkManager: <debug> [1201736849.387377] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_label_GUN_BETTYLOU'). 
Jan 30 18:47:30 mythbox kernel: [  151.703014] UDF-fs: Partition marked readonly; forcing readonly mount
Jan 30 18:47:30 mythbox kernel: [  151.703041] UDF-fs INFO UDF 0.9.8.1 (2004/29/09) Mounting volume 'GUN_BETTYLOU', timestamp 2003/08/29 22:50 (1ed4)
Jan 30 18:47:52 mythbox kernel: [  173.637017] wlan0: No STA entry for own AP 00:09:5b:3e:0a:b6
Jan 30 18:48:24 mythbox kernel: [  205.612547] wlan0: No STA entry for own AP 00:09:5b:3e:0a:b6
Jan 30 18:48:56 mythbox kernel: [  237.588116] wlan0: No STA entry for own AP 00:09:5b:3e:0a:b6
Jan 30 18:49:28 mythbox kernel: [  269.563667] wlan0: No STA entry for own AP 00:09:5b:3e:0a:b6
Jan 30 18:50:00 mythbox kernel: [  301.539233] wlan0: No STA entry for own AP 00:09:5b:3e:0a:b6
Jan 30 18:50:32 mythbox kernel: [  333.514741] wlan0: No STA entry for own AP 00:09:5b:3e:0a:b6
Jan 30 18:51:04 mythbox kernel: [  365.489999] wlan0: No STA entry for own AP 00:09:5b:3e:0a:b6
Jan 30 18:51:36 mythbox kernel: [  397.465257] wlan0: No STA entry for own AP 00:09:5b:3e:0a:b6
Jan 30 18:52:04 mythbox NetworkManager: <debug> [1201737124.694889] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/volume_label_GUN_BETTYLOU'). 
Jan 30 18:52:08 mythbox kernel: [  429.440515] wlan0: No STA entry for own AP 00:09:5b:3e:0a:b6
Jan 30 18:52:16 mythbox NetworkManager: <debug> [1201737136.335065] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_label_GUN_BETTYLOU'). 
Jan 30 18:52:16 mythbox kernel: [  437.788668] UDF-fs: Partition marked readonly; forcing readonly mount
Jan 30 18:52:16 mythbox kernel: [  437.788751] UDF-fs INFO UDF 0.9.8.1 (2004/29/09) Mounting volume 'GUN_BETTYLOU', timestamp 2003/08/29 22:50 (1ed4)
Jan 30 18:52:40 mythbox kernel: [  461.415772] wlan0: No STA entry for own AP 00:09:5b:3e:0a:b6
Jan 30 18:52:53 mythbox dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
Jan 30 18:52:56 mythbox dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
Jan 30 18:53:03 mythbox dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
Jan 30 18:53:12 mythbox kernel: [  493.391031] wlan0: No STA entry for own AP 00:09:5b:3e:0a:b6
Jan 30 18:53:18 mythbox dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
Jan 30 18:53:24 mythbox dhclient: No DHCPOFFERS received.
Jan 30 18:53:24 mythbox dhclient: Trying recorded lease 192.168.0.13
Jan 30 18:53:27 mythbox dhclient: No working leases in persistent database - sleeping.
Jan 30 18:53:44 mythbox kernel: [  525.370287] wlan0: No STA entry for own AP 00:09:5b:3e:0a:b6
Jan 30 18:54:16 mythbox kernel: [  557.345547] wlan0: No STA entry for own AP 00:09:5b:3e:0a:b6
Jan 30 18:54:48 mythbox kernel: [  589.320806] wlan0: No STA entry for own AP 00:09:5b:3e:0a:b6
Jan 30 18:55:20 mythbox kernel: [  621.296064] wlan0: No STA entry for own AP 00:09:5b:3e:0a:b6
Jan 30 18:55:52 mythbox kernel: [  653.271321] wlan0: No STA entry for own AP 00:09:5b:3e:0a:b6
Jan 30 18:56:24 mythbox kernel: [  685.246580] wlan0: No STA entry for own AP 00:09:5b:3e:0a:b6
Jan 30 18:56:28 mythbox dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
Jan 30 18:56:34 mythbox dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
Jan 30 18:56:40 mythbox dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
Jan 30 18:56:49 mythbox dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
Jan 30 18:56:56 mythbox kernel: [  717.221837] wlan0: No STA entry for own AP 00:09:5b:3e:0a:b6
...

```

The last bit gets repeated a number of times.  (btw, the "Mounting volume 'GUN_BETTYLOU'" is a DVD my wife was getting set to watch).

Any ideas why my wireless network is not working reliably or staying up?

Thanks,
Kawayanan

---

### Post by Chuckels550 on 2008-01-31
Go to the Preferences setting in Network Manager.  Check to see if the correct driver is set.  I found that it tended to reset to wext, the default,  for no reason.  I don't know what the driver is for your wireless adapter.

---

