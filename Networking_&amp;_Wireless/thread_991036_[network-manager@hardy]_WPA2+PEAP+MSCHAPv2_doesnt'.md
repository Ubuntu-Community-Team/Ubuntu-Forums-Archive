---
title: "[network-manager@hardy] WPA2+PEAP+MSCHAPv2 doesnt't work anymore"
date: 2008-11-23
forum: Networking &amp; Wireless
---

### Post by deadland on 2008-11-23
Hi ubuntu community,

I have to PC:
BenQ R55.G21 + iwl3945
eeePC 701 G4
both with Hardy


I had a working wireless configuration of my university with WPA2+PEAP+MSCHAPv2, but it doesn't work anymore. There were no updates, I doesn't touch my configuration, other win32-clients can access the network and the helpdesk said, that my account isn't locked. So I don't know whats wrong.

So here is the syslog of the last day the connection worked:

```
Nov 17 13:33:10 benq NetworkManager: <info>  SWITCH: no current connection, found better connection 'wlan0'. 
Nov 17 13:33:10 benq NetworkManager: <info>  Will activate connection 'wlan0/h_da'. 
Nov 17 13:33:10 benq NetworkManager: <info>  Device wlan0 activation scheduled... 
Nov 17 13:33:10 benq NetworkManager: <info>  Activation (wlan0) started... 
Nov 17 13:33:10 benq NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled... 
Nov 17 13:33:10 benq NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started... 
Nov 17 13:33:10 benq NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled... 
Nov 17 13:33:10 benq NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete. 
Nov 17 13:33:10 benq NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting... 
Nov 17 13:33:10 benq NetworkManager: <info>  Activation (wlan0/wireless): access point 'h_da' is encrypted, but NO valid key exists.  New key needed. 
Nov 17 13:33:10 benq NetworkManager: <info>  Activation (wlan0) New wireless user key requested for network 'h_da'. 
Nov 17 13:33:10 benq NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete. 
Nov 17 13:33:10 benq NetworkManager: <info>  Activation (wlan0) New wireless user key for network 'h_da' received. 
Nov 17 13:33:10 benq NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled... 
Nov 17 13:33:10 benq NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started... 
Nov 17 13:33:10 benq NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled... 
Nov 17 13:33:10 benq NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete. 
Nov 17 13:33:10 benq NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting... 
Nov 17 13:33:10 benq NetworkManager: <info>  Activation (wlan0/wireless): access point 'h_da' is encrypted, and a key exists.  No new key needed. 
Nov 17 13:33:11 benq NetworkManager: <info>  retry to connect to global supplicant socket (try=1) 
Nov 17 13:33:11 benq NetworkManager: <info>  SUP: sending command 'INTERFACE_ADD wlan0^I^Iwext^I/var/run/wpa_supplicant0^I' 
Nov 17 13:33:11 benq NetworkManager: <info>  SUP: response was 'OK' 
Nov 17 13:33:12 benq NetworkManager: <info>  SUP: sending command 'AP_SCAN 1' 
Nov 17 13:33:12 benq NetworkManager: <info>  SUP: response was 'OK' 
Nov 17 13:33:12 benq NetworkManager: <info>  SUP: sending command 'ADD_NETWORK' 
Nov 17 13:33:12 benq NetworkManager: <info>  SUP: response was '0' 
Nov 17 13:33:12 benq NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 ssid 685f6461' 
Nov 17 13:33:12 benq NetworkManager: <info>  SUP: response was 'OK' 
Nov 17 13:33:12 benq NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 proto WPA2' 
Nov 17 13:33:12 benq NetworkManager: <info>  SUP: response was 'OK' 
Nov 17 13:33:12 benq NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 key_mgmt WPA-EAP' 
Nov 17 13:33:12 benq NetworkManager: <info>  SUP: response was 'OK' 
Nov 17 13:33:12 benq NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 phase2 "auth=MSCHAPV2"' 
Nov 17 13:33:12 benq NetworkManager: <info>  SUP: response was 'OK' 
Nov 17 13:33:12 benq NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 eap PEAP' 
Nov 17 13:33:12 benq NetworkManager: <info>  SUP: response was 'OK' 
Nov 17 13:33:12 benq NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 identity "stmaober"' 
Nov 17 13:33:12 benq NetworkManager: <info>  SUP: response was 'OK' 
Nov 17 13:33:12 benq NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 password <password>' 
Nov 17 13:33:12 benq NetworkManager: <info>  SUP: response was 'OK' 
Nov 17 13:33:12 benq NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 pairwise TKIP' 
Nov 17 13:33:12 benq NetworkManager: <info>  SUP: response was 'OK' 
Nov 17 13:33:12 benq NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 group TKIP' 
Nov 17 13:33:12 benq NetworkManager: <info>  SUP: response was 'OK' 
Nov 17 13:33:12 benq NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 fragment_size 1300' 
Nov 17 13:33:12 benq NetworkManager: <info>  SUP: response was 'OK' 
Nov 17 13:33:12 benq NetworkManager: <info>  SUP: sending command 'ENABLE_NETWORK 0' 
Nov 17 13:33:12 benq NetworkManager: <info>  SUP: response was 'OK' 
Nov 17 13:33:12 benq NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete. 
Nov 17 13:33:14 benq kernel: [   11.841221] wlan0: Initial auth_alg=0
Nov 17 13:33:14 benq kernel: [   11.841231] wlan0: direct probe to AP 00:0b:0e:83:5e:46 try 1
Nov 17 13:33:14 benq kernel: [   11.843700] wlan0 direct probe responded
Nov 17 13:33:14 benq kernel: [   11.843708] wlan0: authenticate with AP 00:0b:0e:83:5e:46
Nov 17 13:33:14 benq kernel: [   11.845463] wlan0: RX authentication from 00:0b:0e:83:5e:46 (alg=0 transaction=2 status=0)
Nov 17 13:33:14 benq kernel: [   11.845474] wlan0: authenticated
Nov 17 13:33:14 benq kernel: [   11.845478] wlan0: associate with AP 00:0b:0e:83:5e:46
Nov 17 13:33:14 benq kernel: [   11.847545] wlan0: RX AssocResp from 00:0b:0e:83:5e:46 (capab=0x31 status=0 aid=3)
Nov 17 13:33:14 benq kernel: [   11.847552] wlan0: associated
Nov 17 13:33:14 benq kernel: [   11.847569] wlan0: WMM queue=2 aci=0 acm=0 aifs=3 cWmin=15 cWmax=1023 txop=0
Nov 17 13:33:14 benq kernel: [   11.849276] wlan0: WMM queue=3 aci=1 acm=0 aifs=7 cWmin=15 cWmax=1023 txop=0
Nov 17 13:33:14 benq kernel: [   11.849359] wlan0: WMM queue=1 aci=2 acm=0 aifs=2 cWmin=7 cWmax=15 txop=94
Nov 17 13:33:14 benq kernel: [   11.849803] wlan0: WMM queue=0 aci=3 acm=0 aifs=2 cWmin=3 cWmax=7 txop=47
Nov 17 13:33:14 benq kernel: [   11.849905] printk: 5 messages suppressed.
Nov 17 13:33:14 benq kernel: [   11.849911] wlan0: CTS protection enabled (BSSID=00:0b:0e:83:5e:46)
Nov 17 13:33:14 benq kernel: [   11.853243] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Nov 17 13:33:14 benq nmbd[5309]: [2008/11/17 13:33:14, 0] libsmb/nmblib.c:send_udp(793) 
Nov 17 13:33:14 benq nmbd[5309]:   Packet send failed to 172.17.15.255(138) ERRNO=Invalid argument 
Nov 17 13:33:14 benq nmbd[5309]: [2008/11/17 13:33:14, 0] libsmb/nmblib.c:send_udp(793) 
Nov 17 13:33:14 benq nmbd[5309]:   Packet send failed to 172.17.15.255(138) ERRNO=Invalid argument 
Nov 17 13:33:14 benq nmbd[5309]: [2008/11/17 13:33:14, 0] nmbd/nmbd.c:reload_interfaces(240) 
Nov 17 13:33:14 benq nmbd[5309]:   reload_interfaces: No subnets to listen to. Waiting.. 
Nov 17 13:33:15 benq avahi-daemon[5111]: Registering new address record for fe80::218:deff:fe0a:ccb0 on wlan0.*.
Nov 17 13:33:16 benq NetworkManager: <info>  Supplicant state changed: 1 
Nov 17 13:33:16 benq NetworkManager: <info>  Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to access point 'h_da'. 
Nov 17 13:33:16 benq NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) scheduled. 
Nov 17 13:33:16 benq NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) started... 
Nov 17 13:33:17 benq NetworkManager: <info>  Activation (wlan0) Beginning DHCP transaction. 
Nov 17 13:33:17 benq dhclient: There is already a pid file /var/run/dhclient.wlan0.pid with pid 134519072
Nov 17 13:33:17 benq NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete. 
Nov 17 13:33:17 benq NetworkManager: <info>  DHCP daemon state is now 12 (successfully started) for interface wlan0 
Nov 17 13:33:17 benq dhclient: wmaster0: unknown hardware address type 801
Nov 17 13:33:18 benq NetworkManager: <info>  DHCP daemon state is now 1 (starting) for interface wlan0 
Nov 17 13:33:18 benq dhclient: wmaster0: unknown hardware address type 801
Nov 17 13:33:19 benq NetworkManager: <info>  Old device 'wlan0' activating, won't change. 
Nov 17 13:33:20 benq dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
Nov 17 13:33:20 benq dhclient: DHCPOFFER of 172.17.12.23 from 172.17.12.1
Nov 17 13:33:20 benq dhclient: DHCPREQUEST of 172.17.12.23 on wlan0 to 255.255.255.255 port 67
Nov 17 13:33:20 benq dhclient: DHCPACK of 172.17.12.23 from 172.17.12.1
Nov 17 13:33:20 benq avahi-daemon[5111]: Joining mDNS multicast group on interface wlan0.IPv4 with address 172.17.12.23.
Nov 17 13:33:20 benq avahi-daemon[5111]: New relevant interface wlan0.IPv4 for mDNS.
Nov 17 13:33:20 benq avahi-daemon[5111]: Registering new address record for 172.17.12.23 on wlan0.IPv4.
Nov 17 13:33:20 benq avahi-daemon[5111]: Withdrawing address record for 172.17.12.23 on wlan0.
Nov 17 13:33:20 benq avahi-daemon[5111]: Leaving mDNS multicast group on interface wlan0.IPv4 with address 172.17.12.23.
Nov 17 13:33:20 benq avahi-daemon[5111]: Interface wlan0.IPv4 no longer relevant for mDNS.
Nov 17 13:33:20 benq avahi-daemon[5111]: Joining mDNS multicast group on interface wlan0.IPv4 with address 172.17.12.23.
Nov 17 13:33:20 benq avahi-daemon[5111]: New relevant interface wlan0.IPv4 for mDNS.
Nov 17 13:33:20 benq avahi-daemon[5111]: Registering new address record for 172.17.12.23 on wlan0.IPv4.
Nov 17 13:33:20 benq dhclient: bound to 172.17.12.23 -- renewal in 42209 seconds.
Nov 17 13:33:20 benq NetworkManager: <info>  DHCP daemon state is now 2 (bound) for interface wlan0 
Nov 17 13:33:20 benq NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP Configure Get) scheduled... 
Nov 17 13:33:20 benq NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP Configure Get) started... 
Nov 17 13:33:20 benq dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan0 for sub-path wlan0.dbus.get.host_name
Nov 17 13:33:20 benq dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan0 for sub-path wlan0.dbus.get.domain_name
Nov 17 13:33:20 benq dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan0 for sub-path wlan0.dbus.get.nis_domain
Nov 17 13:33:20 benq dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan0 for sub-path wlan0.dbus.get.nis_servers
Nov 17 13:33:20 benq NetworkManager: <info>  Retrieved the following IP4 configuration from the DHCP daemon: 
Nov 17 13:33:20 benq NetworkManager: <info>    address 172.17.12.23 
Nov 17 13:33:20 benq NetworkManager: <info>    netmask 255.255.252.0 
Nov 17 13:33:20 benq NetworkManager: <info>    broadcast 172.17.15.255 
Nov 17 13:33:20 benq NetworkManager: <info>    gateway 172.17.12.1 
Nov 17 13:33:20 benq NetworkManager: <info>    nameserver 141.100.1.140 
Nov 17 13:33:20 benq NetworkManager: <info>    nameserver 141.100.1.141 
Nov 17 13:33:20 benq dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan0 for sub-path wlan0.dbus.get.interface_mtu
Nov 17 13:33:20 benq NetworkManager: <info>  Activation (wlan0) Stage 5 of 5 (IP Configure Commit) scheduled... 
Nov 17 13:33:20 benq NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP Configure Get) complete. 
Nov 17 13:33:20 benq NetworkManager: <info>  Activation (wlan0) Stage 5 of 5 (IP Configure Commit) started... 
Nov 17 13:33:20 benq avahi-daemon[5111]: Withdrawing address record for 172.17.12.23 on wlan0.
Nov 17 13:33:20 benq avahi-daemon[5111]: Leaving mDNS multicast group on interface wlan0.IPv4 with address 172.17.12.23.
Nov 17 13:33:20 benq avahi-daemon[5111]: Interface wlan0.IPv4 no longer relevant for mDNS.
Nov 17 13:33:20 benq avahi-daemon[5111]: Withdrawing address record for fe80::218:deff:fe0a:ccb0 on wlan0.
Nov 17 13:33:20 benq avahi-daemon[5111]: Joining mDNS multicast group on interface wlan0.IPv4 with address 172.17.12.23.
Nov 17 13:33:20 benq avahi-daemon[5111]: New relevant interface wlan0.IPv4 for mDNS.
Nov 17 13:33:20 benq avahi-daemon[5111]: Registering new address record for 172.17.12.23 on wlan0.IPv4.
Nov 17 13:33:21 benq NetworkManager: <info>  Clearing nscd hosts cache. 
Nov 17 13:33:21 benq NetworkManager: <WARN>  nm_spawn_process(): nm_spawn_process('/usr/sbin/nscd -i hosts'): could not spawn process. (Failed to execute child process "/usr/sbin/nscd" (No such file or directory))  
Nov 17 13:33:21 benq NetworkManager: <info>  Activation (wlan0) Finish handler scheduled. 
Nov 17 13:33:21 benq NetworkManager: <info>  Activation (wlan0) Stage 5 of 5 (IP Configure Commit) complete. 
Nov 17 13:33:21 benq NetworkManager: <info>  Activation (wlan0) successful, device activated. 
Nov 17 13:33:21 benq ntpd[7025]: ntpd exiting on signal 15
Nov 17 13:33:21 benq kernel: [   13.834990] usb 1-1: new low speed USB device using uhci_hcd and address 5
Nov 17 13:33:21 benq kernel: [   13.921280] usb 1-1: configuration #1 chosen from 1 choice
Nov 17 13:33:21 benq NetworkManager: <debug> [1226925201.801877] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_45e_39_noserial'). 
Nov 17 13:33:21 benq kernel: [   13.939515] input: Microsoft Microsoft 5-Button Mouse with IntelliEye(TM) as /devices/pci0000:00/0000:00:1d.0/usb1/1-1/1-1:1.0/input/input15
Nov 17 13:33:21 benq kernel: [   13.972013] input,hidraw0: USB HID v1.10 Mouse [Microsoft Microsoft 5-Button Mouse with IntelliEye(TM)] on usb-0000:00:1d.0-1
Nov 17 13:33:21 benq NetworkManager: <debug> [1226925201.918422] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_45e_39_noserial_if0'). 
Nov 17 13:33:21 benq NetworkManager: <debug> [1226925201.966012] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_45e_39_noserial_if0_logicaldev_input'). 
Nov 17 13:33:22 benq avahi-daemon[5111]: Registering new address record for fe80::218:deff:fe0a:ccb0 on wlan0.*.
Nov 17 13:33:26 benq ntpdate[21828]: no server suitable for synchronization found
Nov 17 13:33:26 benq ntpd[21885]: ntpd 4.2.4p4@1.1520-o Fri Mar  7 20:24:07 UTC 2008 (1)
Nov 17 13:33:26 benq ntpd[21886]: precision = 1.000 usec
Nov 17 13:33:26 benq ntpd[21886]: Listening on interface #0 wildcard, 0.0.0.0#123 Disabled
Nov 17 13:33:26 benq ntpd[21886]: Listening on interface #1 wildcard, ::#123 Disabled
Nov 17 13:33:26 benq ntpd[21886]: Listening on interface #2 lo, ::1#123 Enabled
Nov 17 13:33:26 benq ntpd[21886]: Listening on interface #3 wlan0, fe80::218:deff:fe0a:ccb0#123 Enabled
Nov 17 13:33:26 benq ntpd[21886]: Listening on interface #4 lo, 127.0.0.1#123 Enabled
Nov 17 13:33:26 benq ntpd[21886]: Listening on interface #5 wlan0, 172.17.12.23#123 Enabled
Nov 17 13:33:26 benq ntpd[21886]: kernel time sync status 0040
Nov 17 13:33:26 benq ntpd[21886]: frequency initialized -37.788 PPM from /var/lib/ntp/ntp.drift

```

and thats the day it stops working:

```
Nov 18 12:36:03 benq NetworkManager: <info>  Enabling networking. 
Nov 18 12:36:03 benq NetworkManager: <info>  Deactivating device eth0. 
Nov 18 12:36:03 benq NetworkManager: <info>  Deactivating device wlan0. 
Nov 18 12:36:03 benq kernel: [ 2110.521707] sky2 eth0: enabling interface
Nov 18 12:36:03 benq kernel: [ 2110.526646] ADDRCONF(NETDEV_UP): eth0: link is not ready
Nov 18 12:36:03 benq NetworkManager: <info>  eth0: Device is fully-supported using driver 'sky2'. 
Nov 18 12:36:03 benq NetworkManager: <info>  nm_device_init(): waiting for device's worker thread to start 
Nov 18 12:36:04 benq NetworkManager: <info>  nm_device_init(): device's worker thread started, continuing. 
Nov 18 12:36:04 benq NetworkManager: <info>  Now managing wired Ethernet (802.3) device 'eth0'. 
Nov 18 12:36:04 benq NetworkManager: <info>  Deactivating device eth0. 
Nov 18 12:36:04 benq kernel: [ 2110.555815] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 16 (level, low) -> IRQ 16
Nov 18 12:36:04 benq kernel: [ 2110.555946] PM: Writing back config space on device 0000:02:00.0 at offset 1 (was 100002, writing 100006)
Nov 18 12:36:04 benq kernel: [ 2110.582977] Registered led device: iwl-phy0:radio
Nov 18 12:36:04 benq kernel: [ 2110.583053] Registered led device: iwl-phy0:assoc
Nov 18 12:36:04 benq kernel: [ 2110.583086] Registered led device: iwl-phy0:RX
Nov 18 12:36:04 benq kernel: [ 2110.583117] Registered led device: iwl-phy0:TX
Nov 18 12:36:04 benq kernel: [ 2110.601091] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Nov 18 12:36:04 benq NetworkManager: <info>  wlan0: Device is fully-supported using driver 'iwl3945'. 
Nov 18 12:36:04 benq NetworkManager: <info>  wlan0: driver supports SSID scans (scan_capa 0x01). 
Nov 18 12:36:04 benq NetworkManager: <info>  nm_device_init(): waiting for device's worker thread to start 
Nov 18 12:36:04 benq NetworkManager: <info>  nm_device_init(): device's worker thread started, continuing. 
Nov 18 12:36:04 benq NetworkManager: <info>  Now managing wireless (802.11) device 'wlan0'. 
Nov 18 12:36:04 benq NetworkManager: <info>  Deactivating device wlan0. 
Nov 18 12:36:20 benq dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan0 for sub-path wlan0.dbus.get.reason
Nov 18 12:36:20 benq NetworkManager: <debug> [1227008180.482794] nm_device_802_11_wireless_get_activation_ap(): Forcing AP 'h_da' 
Nov 18 12:36:20 benq NetworkManager: <info>  User Switch: /org/freedesktop/NetworkManager/Devices/wlan0 / h_da 
Nov 18 12:36:20 benq NetworkManager: <info>  Deactivating device wlan0. 
Nov 18 12:36:20 benq NetworkManager: <info>  Device wlan0 activation scheduled... 
Nov 18 12:36:20 benq NetworkManager: <info>  Activation (wlan0) started... 
Nov 18 12:36:20 benq NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled... 
Nov 18 12:36:20 benq NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started... 
Nov 18 12:36:20 benq NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled... 
Nov 18 12:36:20 benq NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete. 
Nov 18 12:36:20 benq NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting... 
Nov 18 12:36:20 benq NetworkManager: <info>  Activation (wlan0/wireless): access point 'h_da' is encrypted, but NO valid key exists.  New key needed. 
Nov 18 12:36:20 benq NetworkManager: <info>  Activation (wlan0) New wireless user key requested for network 'h_da'. 
Nov 18 12:36:20 benq NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete. 
Nov 18 12:36:20 benq NetworkManager: <info>  Activation (wlan0) New wireless user key for network 'h_da' received. 
Nov 18 12:36:20 benq NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled... 
Nov 18 12:36:20 benq NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started... 
Nov 18 12:36:20 benq NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled... 
Nov 18 12:36:20 benq NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete. 
Nov 18 12:36:20 benq NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting... 
Nov 18 12:36:20 benq NetworkManager: <info>  Activation (wlan0/wireless): access point 'h_da' is encrypted, and a key exists.  No new key needed. 
Nov 18 12:36:21 benq NetworkManager: <info>  retry to connect to global supplicant socket (try=1) 
Nov 18 12:36:21 benq NetworkManager: <info>  SUP: sending command 'INTERFACE_ADD wlan0^I^Iwext^I/var/run/wpa_supplicant0^I' 
Nov 18 12:36:22 benq NetworkManager: <info>  SUP: response was 'OK' 
Nov 18 12:36:22 benq NetworkManager: <info>  SUP: sending command 'AP_SCAN 1' 
Nov 18 12:36:22 benq NetworkManager: <info>  SUP: response was 'OK' 
Nov 18 12:36:22 benq NetworkManager: <info>  SUP: sending command 'ADD_NETWORK' 
Nov 18 12:36:22 benq NetworkManager: <info>  SUP: response was '0' 
Nov 18 12:36:22 benq NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 ssid 685f6461' 
Nov 18 12:36:22 benq NetworkManager: <info>  SUP: response was 'OK' 
Nov 18 12:36:22 benq NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 proto WPA' 
Nov 18 12:36:22 benq NetworkManager: <info>  SUP: response was 'OK' 
Nov 18 12:36:22 benq NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 key_mgmt WPA-EAP' 
Nov 18 12:36:22 benq NetworkManager: <info>  SUP: response was 'OK' 
Nov 18 12:36:22 benq NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 phase2 "auth=MSCHAPV2"' 
Nov 18 12:36:22 benq NetworkManager: <info>  SUP: response was 'OK' 
Nov 18 12:36:22 benq NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 eap PEAP' 
Nov 18 12:36:22 benq NetworkManager: <info>  SUP: response was 'OK' 
Nov 18 12:36:22 benq NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 identity "stmaober"' 
Nov 18 12:36:22 benq NetworkManager: <info>  SUP: response was 'OK' 
Nov 18 12:36:22 benq NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 password <password>' 
Nov 18 12:36:22 benq NetworkManager: <info>  SUP: response was 'OK' 
Nov 18 12:36:22 benq NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 private_key_passwd <key>' 
Nov 18 12:36:22 benq NetworkManager: <info>  SUP: response was 'OK' 
Nov 18 12:36:22 benq NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 pairwise TKIP' 
Nov 18 12:36:22 benq NetworkManager: <info>  SUP: response was 'OK' 
Nov 18 12:36:22 benq NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 group TKIP' 
Nov 18 12:36:22 benq NetworkManager: <info>  SUP: response was 'OK' 
Nov 18 12:36:22 benq NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 fragment_size 1300' 
Nov 18 12:36:22 benq NetworkManager: <info>  SUP: response was 'OK' 
Nov 18 12:36:22 benq NetworkManager: <info>  SUP: sending command 'ENABLE_NETWORK 0' 
Nov 18 12:36:22 benq NetworkManager: <info>  SUP: response was 'OK' 
Nov 18 12:36:22 benq NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete. 
Nov 18 12:36:24 benq kernel: [ 2117.864760] wlan0: Initial auth_alg=0
Nov 18 12:36:24 benq kernel: [ 2117.864771] wlan0: direct probe to AP 00:0b:0e:83:5e:47 try 1
Nov 18 12:36:24 benq kernel: [ 2117.865963] wlan0: Initial auth_alg=0
Nov 18 12:36:24 benq kernel: [ 2117.865971] wlan0: direct probe to AP 00:0b:0e:83:5e:47 try 1
Nov 18 12:36:24 benq kernel: [ 2117.865990] wlan0 direct probe responded
Nov 18 12:36:24 benq kernel: [ 2117.865996] wlan0: authenticate with AP 00:0b:0e:83:5e:47
Nov 18 12:36:24 benq kernel: [ 2117.866881] wlan0: RX authentication from 00:0b:0e:83:5e:47 (alg=0 transaction=2 status=0)
Nov 18 12:36:24 benq kernel: [ 2117.866889] wlan0: authenticated
Nov 18 12:36:24 benq kernel: [ 2117.866894] wlan0: associate with AP 00:0b:0e:83:5e:47
Nov 18 12:36:24 benq kernel: [ 2117.868092] wlan0: RX AssocResp from 00:0b:0e:83:5e:47 (capab=0x11 status=0 aid=2)
Nov 18 12:36:24 benq kernel: [ 2117.868099] wlan0: associated
Nov 18 12:36:24 benq kernel: [ 2117.868113] wlan0: WMM queue=2 aci=0 acm=0 aifs=3 cWmin=15 cWmax=1023 txop=0
Nov 18 12:36:24 benq kernel: [ 2117.869648] wlan0: WMM queue=3 aci=1 acm=0 aifs=7 cWmin=15 cWmax=1023 txop=0
Nov 18 12:36:24 benq kernel: [ 2117.869724] wlan0: WMM queue=1 aci=2 acm=0 aifs=2 cWmin=7 cWmax=15 txop=94
Nov 18 12:36:24 benq kernel: [ 2117.869799] wlan0: WMM queue=0 aci=3 acm=0 aifs=2 cWmin=3 cWmax=7 txop=47
Nov 18 12:36:24 benq kernel: [ 2117.871656] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Nov 18 12:36:26 benq NetworkManager: <debug> [1227008186.340480] nm_device_802_11_wireless_update_bssid(): Roamed from BSSID 00:0B:0E:83:5E:46 to 00:0B:0E:83:5E:47 on wireless network 'h_da' 
Nov 18 12:36:26 benq NetworkManager: <debug> [1227008186.346020] nm_dbus_signal_filter(): NetworkManagerInfo triggered update of wireless network 'h_da' 
Nov 18 12:36:26 benq NetworkManager: <info>  Old device 'wlan0' activating, won't change. 
Nov 18 12:36:26 benq avahi-daemon[5101]: Registering new address record for fe80::218:deff:fe0a:ccb0 on wlan0.*.
Nov 18 12:36:29 benq NetworkManager: <info>  Old device 'wlan0' activating, won't change. 
Nov 18 12:36:30 benq NetworkManager: <debug> [1227008190.340470] nm_device_802_11_wireless_update_bssid(): Roamed from BSSID 00:0B:0E:83:5E:46 to 00:0B:0E:83:5E:47 on wireless network 'h_da' 
Nov 18 12:36:30 benq NetworkManager: <debug> [1227008190.347255] nm_dbus_signal_filter(): NetworkManagerInfo triggered update of wireless network 'h_da' 
Nov 18 12:36:30 benq NetworkManager: <info>  Old device 'wlan0' activating, won't change. 
Nov 18 12:36:35 benq kernel: [ 2121.205217] wlan0: no IPv6 routers present
Nov 18 12:37:03 benq ntpd[5394]: Listening on interface #6 wlan0, fe80::218:deff:fe0a:ccb0#123 Enabled
Nov 18 12:37:37 benq kernel: [ 2139.768095] wlan0: disassociate(reason=3)
Nov 18 12:37:37 benq NetworkManager: <info>  Supplicant state changed: 0 
Nov 18 12:37:40 benq kernel: [ 2140.879701] wlan0: RX disassociation from 00:0b:0e:83:5e:47 (reason=7)
Nov 18 12:37:40 benq kernel: [ 2140.879728] wlan0: RX disassociation from 00:0b:0e:83:5e:47 (reason=7)
Nov 18 12:37:40 benq kernel: [ 2140.879749] wlan0: associate with AP 00:0b:0e:83:5e:47
Nov 18 12:37:40 benq kernel: [ 2140.880618] wlan0: RX disassociation from 00:0b:0e:83:5e:47 (reason=7)
Nov 18 12:37:40 benq NetworkManager: <info>  Supplicant state changed: 0 
Nov 18 12:37:40 benq last message repeated 2 times
Nov 18 12:37:40 benq kernel: [ 2140.882106] wlan0: Initial auth_alg=0
Nov 18 12:37:40 benq kernel: [ 2140.882114] wlan0: direct probe to AP 00:0b:0e:83:5e:47 try 1
Nov 18 12:37:40 benq kernel: [ 2140.882136] wlan0: association frame received from 00:0b:0e:83:5e:47, but not in associate state - ignored
Nov 18 12:37:40 benq kernel: [ 2140.883569] wlan0 direct probe responded
Nov 18 12:37:40 benq kernel: [ 2140.883576] wlan0: authenticate with AP 00:0b:0e:83:5e:47
Nov 18 12:37:40 benq kernel: [ 2140.935596] wlan0: authenticate with AP 00:0b:0e:83:5e:47
Nov 18 12:37:40 benq kernel: [ 2140.937124] wlan0: RX authentication from 00:0b:0e:83:5e:47 (alg=0 transaction=2 status=0)
Nov 18 12:37:40 benq kernel: [ 2140.937135] wlan0: authenticated
Nov 18 12:37:40 benq kernel: [ 2140.937140] wlan0: associate with AP 00:0b:0e:83:5e:47
Nov 18 12:37:40 benq kernel: [ 2140.938837] wlan0: RX ReassocResp from 00:0b:0e:83:5e:47 (capab=0x11 status=0 aid=2)
Nov 18 12:37:40 benq kernel: [ 2140.938847] wlan0: associated
Nov 18 12:37:40 benq kernel: [ 2140.938856] wlan0: WMM queue=2 aci=0 acm=0 aifs=3 cWmin=15 cWmax=1023 txop=0
Nov 18 12:37:40 benq kernel: [ 2140.940429] wlan0: WMM queue=3 aci=1 acm=0 aifs=7 cWmin=15 cWmax=1023 txop=0
Nov 18 12:37:40 benq kernel: [ 2140.940514] wlan0: WMM queue=1 aci=2 acm=0 aifs=2 cWmin=7 cWmax=15 txop=94
Nov 18 12:37:40 benq kernel: [ 2140.940602] wlan0: WMM queue=0 aci=3 acm=0 aifs=2 cWmin=3 cWmax=7 txop=47
Nov 18 12:37:45 benq NetworkManager: <info>  Old device 'wlan0' activating, won't change. 
Nov 18 12:37:57 benq NetworkManager: <info>  Activation (wlan0/wireless): disconnected during association, asking for new key. 
Nov 18 12:37:57 benq NetworkManager: <info>  Activation (wlan0) New wireless user key requested for network 'h_da'. 
Nov 18 12:38:00 benq NetworkManager: <info>  Activation (wlan0) New wireless user key request for network 'h_da' was canceled. 
Nov 18 12:38:00 benq NetworkManager: <info>  Activation (wlan0) failure scheduled... 
Nov 18 12:38:01 benq NetworkManager: <info>  Activation (wlan0) failed for access point (h_da) 
Nov 18 12:38:01 benq NetworkManager: <info>  Activation (wlan0) failed. 
Nov 18 12:38:01 benq NetworkManager: <info>  Deactivating device wlan0. 
Nov 18 12:38:01 benq kernel: [ 2147.369191] wlan0: deauthenticate(reason=3)
Nov 18 12:38:01 benq avahi-daemon[5101]: Withdrawing address record for fe80::218:deff:fe0a:ccb0 on wlan0.
Nov 18 12:38:08 benq kernel: [ 2149.606620] wlan0: RX deauthentication from 00:0b:0e:83:5e:47 (reason=6)
Nov 18 12:38:08 benq kernel: [ 2149.606628] wlan0: deauthenticated
Nov 18 12:38:08 benq kernel: [ 2149.606700] wlan0: RX deauthentication from 00:0b:0e:83:5e:47 (reason=6)
Nov 18 12:38:08 benq kernel: [ 2149.606717] wlan0: RX deauthentication from 00:0b:0e:83:5e:47 (reason=6)
Nov 18 12:38:08 benq kernel: [ 2149.606734] wlan0: direct probe to AP 00:0b:0e:83:5e:47 try 1
Nov 18 12:38:08 benq kernel: [ 2149.608303] wlan0: RX deauthentication from 00:0b:0e:83:5e:47 (reason=6)
Nov 18 12:38:08 benq kernel: [ 2149.609193] wlan0 direct probe responded
Nov 18 12:38:08 benq kernel: [ 2149.609200] wlan0: authenticate with AP 00:0b:0e:83:5e:47
Nov 18 12:38:08 benq kernel: [ 2149.610000] wlan0: RX authentication from 00:0b:0e:83:5e:47 (alg=0 transaction=2 status=0)
Nov 18 12:38:08 benq kernel: [ 2149.610008] wlan0: authenticated
Nov 18 12:38:08 benq kernel: [ 2149.610012] wlan0: associate with AP 00:0b:0e:83:5e:47
Nov 18 12:38:08 benq kernel: [ 2149.610788] wlan0: RX AssocResp from 00:0b:0e:83:5e:47 (capab=0x11 status=1 aid=0)
Nov 18 12:38:08 benq kernel: [ 2149.610794] wlan0: AP denied association (code=1)
Nov 18 12:38:08 benq kernel: [ 2149.673576] wlan0: associate with AP 00:0b:0e:83:5e:47
Nov 18 12:38:08 benq kernel: [ 2149.674337] wlan0: RX AssocResp from 00:0b:0e:83:5e:47 (capab=0x11 status=1 aid=0)
Nov 18 12:38:08 benq kernel: [ 2149.674344] wlan0: AP denied association (code=1)
Nov 18 12:38:08 benq kernel: [ 2149.723806] wlan0: associate with AP 00:0b:0e:83:5e:47
Nov 18 12:38:08 benq kernel: [ 2149.724495] wlan0: RX AssocResp from 00:0b:0e:83:5e:47 (capab=0x11 status=1 aid=0)
Nov 18 12:38:08 benq kernel: [ 2149.724502] wlan0: AP denied association (code=1)
Nov 18 12:38:08 benq kernel: [ 2149.772363] wlan0: association with AP 00:0b:0e:83:5e:47 timed out
```

Both laptops have the same problem, what it makes even more wired.


Any ideas?

---

