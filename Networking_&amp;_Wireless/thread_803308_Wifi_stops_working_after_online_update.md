---
title: "Wifi stops working after online update"
date: 2008-05-22
forum: Networking &amp; Wireless
---

### Post by warrenstroebel@gmail.com on 2008-05-22
my wifi worked fine after an out of box install of hardy heron (ubuntu 8.04) but stopped working after i ran the online update. the adapter used to only show "wlan0" and "wlan0:avai" but now shows an additional "wmaster0"

the syslog shows:
May 22 12:25:54 warren-laptop kernel: [ 6168.825846] usb 3-1: new full speed USB device using uhci_hcd and address 3
May 22 12:25:54 warren-laptop kernel: [ 6169.070913] usb 3-1: configuration #1 chosen from 1 choice
May 22 12:25:54 warren-laptop hcid[5446]: HCI dev 0 registered
May 22 12:25:54 warren-laptop NetworkManager: <debug> [1211451954.453155] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_b05_1712_0194E8_5B_0002'). 
May 22 12:25:54 warren-laptop hcid[5446]: HCI dev 0 up
May 22 12:25:54 warren-laptop hcid[5446]: Device hci0 has been added
May 22 12:25:54 warren-laptop hcid[5446]: Starting security manager 0
May 22 12:25:54 warren-laptop hcid[5446]: Device hci0 has been activated
May 22 12:25:54 warren-laptop NetworkManager: <debug> [1211451954.641598] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_2_if0_0'). 
May 22 12:25:54 warren-laptop NetworkManager: <debug> [1211451954.646193] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_2_if0_0_bluetooth_hci_ea6f235ac'). 
May 22 12:25:54 warren-laptop NetworkManager: <debug> [1211451954.707984] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_2_if2'). 
May 22 12:25:54 warren-laptop NetworkManager: <debug> [1211451954.713969] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_2_if1'). 
May 22 12:25:58 warren-laptop NetworkManager: <info>  Wireless now enabled by radio killswitch 
May 22 12:29:08 warren-laptop dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
May 22 12:29:11 warren-laptop dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
May 22 12:29:15 warren-laptop dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
May 22 12:29:25 warren-laptop dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
May 22 12:29:39 warren-laptop dhclient: No DHCPOFFERS received.
May 22 12:29:39 warren-laptop dhclient: No working leases in persistent database - sleeping.
May 22 12:33:46 warren-laptop dhclient: There is already a pid file /var/run/dhclient.wlan0.pid with pid 6006
May 22 12:33:46 warren-laptop dhclient: killed old client process, removed PID file
May 22 12:33:46 warren-laptop dhclient: Internet Systems Consortium DHCP Client V3.0.6
May 22 12:33:46 warren-laptop dhclient: Copyright 2004-2007 Internet Systems Consortium.
May 22 12:33:46 warren-laptop dhclient: All rights reserved.
May 22 12:33:46 warren-laptop dhclient: For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)
May 22 12:33:46 warren-laptop dhclient: 
May 22 12:33:46 warren-laptop dhclient: wmaster0: unknown hardware address type 801
May 22 12:33:46 warren-laptop dhclient: wmaster0: unknown hardware address type 801
May 22 12:33:46 warren-laptop dhclient: Listening on LPF/wlan0/00:19:d2:2b:dc:bd
May 22 12:33:46 warren-laptop dhclient: Sending on   LPF/wlan0/00:19:d2:2b:dc:bd
May 22 12:33:46 warren-laptop dhclient: Sending on   Socket/fallback
May 22 12:33:46 warren-laptop dhclient: DHCPRELEASE on wlan0 to 10.0.0.2 port 67
May 22 12:33:46 warren-laptop avahi-autoipd(wlan0)[5712]: Got SIGTERM, quitting.
May 22 12:33:46 warren-laptop avahi-autoipd(wlan0)[5712]: Callout STOP, address 169.254.9.96 on interface wlan0
May 22 12:33:46 warren-laptop avahi-daemon[5169]: Withdrawing address record for 169.254.9.96 on wlan0.
May 22 12:33:46 warren-laptop avahi-daemon[5169]: Leaving mDNS multicast group on interface wlan0.IPv4 with address 169.254.9.96.
May 22 12:33:46 warren-laptop avahi-daemon[5169]: Interface wlan0.IPv4 no longer relevant for mDNS.
May 22 12:33:46 warren-laptop avahi-autoipd(wlan0)[5713]: client: RTNETLINK answers: No such process
May 22 12:33:47 warren-laptop NetworkManager: <info>  /etc/network/interface changed: rebuilding the device list. 
May 22 12:33:47 warren-laptop NetworkManager: <info>  Removing wired Ethernet (802.3) device 'eth0'. 
May 22 12:33:47 warren-laptop NetworkManager: <info>  Deactivating device eth0. 
May 22 12:33:47 warren-laptop NetworkManager: <info>  Recreating the device list. 
May 22 12:33:47 warren-laptop kernel: [ 6641.687389] ADDRCONF(NETDEV_UP): wlan0: link is not ready
May 22 12:33:47 warren-laptop kernel: [ 6641.700413] r8169: eth0: link down
May 22 12:33:47 warren-laptop kernel: [ 6641.703898] ADDRCONF(NETDEV_UP): eth0: link is not ready
May 22 12:33:47 warren-laptop NetworkManager: <info>  eth0: Device is fully-supported using driver 'r8169'. 
May 22 12:33:47 warren-laptop NetworkManager: <info>  nm_device_init(): waiting for device's worker thread to start 
May 22 12:33:47 warren-laptop NetworkManager: <info>  nm_device_init(): device's worker thread started, continuing. 
May 22 12:33:47 warren-laptop NetworkManager: <info>  Now managing wired Ethernet (802.3) device 'eth0'. 
May 22 12:33:47 warren-laptop NetworkManager: <info>  Deactivating device eth0. 
May 22 12:33:47 warren-laptop NetworkManager: <info>  Device list recreated successfully. 
May 22 12:33:47 warren-laptop NetworkManager: <info>  /etc/network/interface changed: rebuilding the device list. 
May 22 12:33:47 warren-laptop NetworkManager: <info>  Removing wired Ethernet (802.3) device 'eth0'. 
May 22 12:33:47 warren-laptop NetworkManager: <info>  Deactivating device eth0. 
May 22 12:33:47 warren-laptop NetworkManager: <info>  Recreating the device list. 
May 22 12:33:47 warren-laptop kernel: [ 6641.797166] r8169: eth0: link down
May 22 12:33:47 warren-laptop NetworkManager: <info>  eth0: Device is fully-supported using driver 'r8169'. 
May 22 12:33:47 warren-laptop NetworkManager: <info>  nm_device_init(): waiting for device's worker thread to start 
May 22 12:33:47 warren-laptop NetworkManager: <info>  nm_device_init(): device's worker thread started, continuing. 
May 22 12:33:47 warren-laptop NetworkManager: <info>  Now managing wired Ethernet (802.3) device 'eth0'. 
May 22 12:33:47 warren-laptop NetworkManager: <info>  Deactivating device eth0. 
May 22 12:33:47 warren-laptop NetworkManager: <info>  Device list recreated successfully. 
May 22 12:33:47 warren-laptop kernel: [ 6641.800627] ADDRCONF(NETDEV_UP): eth0: link is not ready
May 22 12:33:47 warren-laptop dhclient: There is already a pid file /var/run/dhclient.wlan0.pid with pid 134519072
May 22 12:33:47 warren-laptop dhclient: Internet Systems Consortium DHCP Client V3.0.6
May 22 12:33:47 warren-laptop dhclient: Copyright 2004-2007 Internet Systems Consortium.
May 22 12:33:47 warren-laptop dhclient: All rights reserved.
May 22 12:33:47 warren-laptop dhclient: For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)
May 22 12:33:47 warren-laptop dhclient: 
May 22 12:33:47 warren-laptop dhclient: wmaster0: unknown hardware address type 801
May 22 12:33:48 warren-laptop dhclient: wmaster0: unknown hardware address type 801
May 22 12:33:48 warren-laptop dhclient: Listening on LPF/wlan0/00:19:d2:2b:dc:bd
May 22 12:33:48 warren-laptop dhclient: Sending on   LPF/wlan0/00:19:d2:2b:dc:bd
May 22 12:33:48 warren-laptop dhclient: Sending on   Socket/fallback
May 22 12:33:49 warren-laptop kernel: [ 6644.229119] wlan0: Initial auth_alg=0
May 22 12:33:49 warren-laptop kernel: [ 6644.229127] wlan0: authenticate with AP 00:04:ed:5d:43:20
May 22 12:33:49 warren-laptop kernel: [ 6644.230261] wlan0: RX authentication from 00:04:ed:5d:43:20 (alg=0 transaction=2 status=0)
May 22 12:33:49 warren-laptop kernel: [ 6644.230267] wlan0: authenticated
May 22 12:33:49 warren-laptop kernel: [ 6644.230271] wlan0: associate with AP 00:04:ed:5d:43:20
May 22 12:33:49 warren-laptop kernel: [ 6644.230828] wlan0: authentication frame received from 00:04:ed:5d:43:20, but not in authenticate state - ignored
May 22 12:33:49 warren-laptop kernel: [ 6644.231425] wlan0: authentication frame received from 00:04:ed:5d:43:20, but not in authenticate state - ignored
May 22 12:33:49 warren-laptop kernel: [ 6644.231983] wlan0: authentication frame received from 00:04:ed:5d:43:20, but not in authenticate state - ignored
May 22 12:33:49 warren-laptop kernel: [ 6644.232842] wlan0: authentication frame received from 00:04:ed:5d:43:20, but not in authenticate state - ignored
May 22 12:33:49 warren-laptop kernel: [ 6644.233422] wlan0: authentication frame received from 00:04:ed:5d:43:20, but not in authenticate state - ignored
May 22 12:33:49 warren-laptop kernel: [ 6644.233953] wlan0: authentication frame received from 00:04:ed:5d:43:20, but not in authenticate state - ignored
May 22 12:33:49 warren-laptop kernel: [ 6644.234607] wlan0: authentication frame received from 00:04:ed:5d:43:20, but not in authenticate state - ignored
May 22 12:33:49 warren-laptop kernel: [ 6644.235624] wlan0: authentication frame received from 00:04:ed:5d:43:20, but not in authenticate state - ignored
May 22 12:33:49 warren-laptop kernel: [ 6644.236242] wlan0: RX AssocResp from 00:04:ed:5d:43:20 (capab=0x411 status=0 aid=2)
May 22 12:33:49 warren-laptop kernel: [ 6644.236247] wlan0: associated
May 22 12:33:49 warren-laptop kernel: [ 6644.238335] wlan0: association frame received from 00:04:ed:5d:43:20, but not in associate state - ignored
May 22 12:33:49 warren-laptop kernel: [ 6644.238686] wlan0: association frame received from 00:04:ed:5d:43:20, but not in associate state - ignored
May 22 12:33:49 warren-laptop kernel: [ 6644.239925] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
May 22 12:33:49 warren-laptop kernel: [ 6644.241268] wlan0: association frame received from 00:04:ed:5d:43:20, but not in associate state - ignored
May 22 12:33:50 warren-laptop dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
May 22 12:33:51 warren-laptop avahi-daemon[5169]: Registering new address record for fe80::219:d2ff:fe2b:dcbd on wlan0.*.
May 22 12:33:54 warren-laptop dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
May 22 12:34:00 warren-laptop kernel: [ 6655.174501] wlan0: no IPv6 routers present
May 22 12:34:04 warren-laptop dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
May 22 12:34:04 warren-laptop kernel: [ 6658.588489] wlan0: disassociate(reason=3)
May 22 12:34:09 warren-laptop kernel: [ 6663.839699] wlan0: Initial auth_alg=0
May 22 12:34:09 warren-laptop kernel: [ 6663.839709] wlan0: authenticate with AP 00:04:ed:5d:43:20
May 22 12:34:09 warren-laptop kernel: [ 6663.840888] wlan0: Initial auth_alg=0
May 22 12:34:09 warren-laptop kernel: [ 6663.840895] wlan0: authenticate with AP 00:04:ed:5d:43:20
May 22 12:34:09 warren-laptop kernel: [ 6663.840908] wlan0: RX authentication from 00:04:ed:5d:43:20 (alg=0 transaction=2 status=0)
May 22 12:34:09 warren-laptop kernel: [ 6663.840913] wlan0: authenticated
May 22 12:34:09 warren-laptop kernel: [ 6663.840919] wlan0: associate with AP 00:04:ed:5d:43:20
May 22 12:34:09 warren-laptop kernel: [ 6663.845074] wlan0: authentication frame received from 00:04:ed:5d:43:20, but not in authenticate state - ignored
May 22 12:34:09 warren-laptop kernel: [ 6663.848999] wlan0: authentication frame received from 00:04:ed:5d:43:20, but not in authenticate state - ignored
May 22 12:34:09 warren-laptop kernel: [ 6663.849524] wlan0: authentication frame received from 00:04:ed:5d:43:20, but not in authenticate state - ignored
May 22 12:34:09 warren-laptop kernel: [ 6663.852227] wlan0: authentication frame received from 00:04:ed:5d:43:20, but not in authenticate state - ignored
May 22 12:34:09 warren-laptop kernel: [ 6663.858407] wlan0: authentication frame received from 00:04:ed:5d:43:20, but not in authenticate state - ignored
May 22 12:34:09 warren-laptop kernel: [ 6663.858913] wlan0: RX ReassocResp from 00:04:ed:5d:43:20 (capab=0x411 status=0 aid=2)
May 22 12:34:09 warren-laptop kernel: [ 6663.858919] wlan0: associated
May 22 12:34:13 warren-laptop NetworkManager: <info>  Going to sleep. 



as you can see, it does see the AP but doesn't receive an IP. the AP works fine as there are other users able to connect.

if any one has an idea it would be greatly appreciated
thanks

---

### Post by warrenstroebel@gmail.com on 2008-05-22
i have done a clean install of ubuntu twice with exactly the same result...

---

### Post by Fredk on 2008-10-29
I have the same problem - WiFi stopped working after on;ine update.
I am new to Ubuntu and Linux - using Eee PC with Knoppix installed as OS and Ubuntu on SD card.  Knoppix still accesses WiFi O.K.
Any help appreciated.

---

