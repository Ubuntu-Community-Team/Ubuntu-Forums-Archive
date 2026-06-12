---
title: "Cloud Computing"
date: 2010-04-04
forum: New to Ubuntu
---

### Post by cdcoley on 2010-04-04
I guess I need some education on what Cloud Computing is,  what if any are the costs and in order to use Ubuntu Enterprise Cloud do I have sign up and purchase services from Amazon?  I am asking these questions as it was my goal to setup a cloud with a node or 2 that would allow users to access EDUbuntu LTSP Servers, a mail server from anywhere?  Is that even realistic or am I looking down the wrong road?  I don't want to pay for any services, just use the hardware that I have in order to accomplish this.

Any insight would be very welcome.

---

### Post by boxcorner on 2010-04-04
> **cdcoley said:**
> I guess I need some education on what Cloud Computing is ...
You might find this helpful: [http://en.wikipedia.org/wiki/Cloud_computing]("http://en.wikipedia.org/wiki/Cloud_computing")

---

### Post by arnab_das on 2010-04-04
i guess you should go through this:

[http://www.ubuntu.com/cloud](http://www.ubuntu.com/cloud)

---

### Post by solitaire on 2010-04-04
here's the prices for amazons cloud service:
[http://aws.amazon.com/ec2/pricing/](http://aws.amazon.com/ec2/pricing/)

---

### Post by cecile7 on 2010-04-04
> **cdcoley said:**
> I guess I need some education on what Cloud Computing is,  what if any are the costs and in order to use Ubuntu Enterprise Cloud do I have sign up and purchase services from Amazon?  I am asking these questions as it was my goal to setup a cloud with a node or 2 that would allow users to access EDUbuntu LTSP Servers, a mail server from anywhere?  Is that even realistic or am I looking down the wrong road?  I don't want to pay for any services, just use the hardware that I have in order to accomplish this.

Any insight would be very welcome.

=======================================

I cannot find how to start a topic
so I place my daemon log here
perhaps somebody understands what happened
when all my activ eprograms were deleted

Mar 31 13:11:15 a-desktop NetworkManager: <info>  SWITCH: terminating current connection 'eth0' because it's no longer valid. 
Mar 31 13:11:15 a-desktop NetworkManager: <info>  Deactivating device eth0. 
Mar 31 13:11:15 a-desktop dhclient: There is already a pid file /var/run/dhclient.eth0.pid with pid 5163
Mar 31 13:11:15 a-desktop dhclient: killed old client process, removed PID file
Mar 31 13:11:15 a-desktop dhclient: DHCPRELEASE on eth0 to 192.168.2.1 port 67
Mar 31 13:11:15 a-desktop avahi-daemon[4681]: Withdrawing address record for 192.168.2.2 on eth0.
Mar 31 13:11:15 a-desktop avahi-daemon[4681]: Leaving mDNS multicast group on interface eth0.IPv4 with address 192.168.2.2.
Mar 31 13:11:15 a-desktop avahi-daemon[4681]: Interface eth0.IPv4 no longer relevant for mDNS.
Mar 31 13:11:16 a-desktop avahi-daemon[4681]: Withdrawing address record for fe80::219:21ff:fe5c:be70 on eth0.
Mar 31 13:11:16 a-desktop NetworkManager: nm_device_is_802_3_ethernet: assertion `dev != NULL' failed
Mar 31 13:11:16 a-desktop NetworkManager: nm_device_is_802_11_wireless: assertion `dev != NULL' failed
Mar 31 17:12:56 a-desktop NetworkManager: <info>  Will activate wired connection 'eth0' because it now has a link. 
Mar 31 17:12:56 a-desktop NetworkManager: <info>  SWITCH: no current connection, found better connection 'eth0'. 
Mar 31 17:12:56 a-desktop NetworkManager: <info>  Will activate connection 'eth0'. 
Mar 31 17:12:56 a-desktop NetworkManager: <info>  Device eth0 activation scheduled... 
Mar 31 17:12:56 a-desktop NetworkManager: <info>  Activation (eth0) started... 
Mar 31 17:12:56 a-desktop NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled... 
Mar 31 17:12:56 a-desktop NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) started... 
Mar 31 17:12:56 a-desktop NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) scheduled... 
Mar 31 17:12:56 a-desktop NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) complete. 
Mar 31 17:12:56 a-desktop NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) starting... 
Mar 31 17:12:56 a-desktop NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) successful. 
Mar 31 17:12:56 a-desktop NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled. 
Mar 31 17:12:56 a-desktop NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) complete. 
Mar 31 17:12:56 a-desktop NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) started... 
Mar 31 17:12:57 a-desktop NetworkManager: <info>  Activation (eth0) Beginning DHCP transaction. 
Mar 31 17:12:57 a-desktop dhclient: There is already a pid file /var/run/dhclient.eth0.pid with pid 134519072
Mar 31 17:12:57 a-desktop NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) complete. 
Mar 31 17:12:57 a-desktop NetworkManager: <info>  DHCP daemon state is now 12 (successfully started) for interface eth0 
Mar 31 17:12:57 a-desktop avahi-daemon[4681]: Registering new address record for fe80::219:21ff:fe5c:be70 on eth0.*.
Mar 31 17:12:58 a-desktop NetworkManager: <info>  DHCP daemon state is now 1 (starting) for interface eth0 
Mar 31 17:13:00 a-desktop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
Mar 31 17:13:00 a-desktop dhclient: DHCPOFFER of 192.168.2.2 from 192.168.2.1
Mar 31 17:13:00 a-desktop dhclient: DHCPREQUEST of 192.168.2.2 on eth0 to 255.255.255.255 port 67
Mar 31 17:13:00 a-desktop dhclient: DHCPACK of 192.168.2.2 from 192.168.2.1
Mar 31 17:13:00 a-desktop avahi-daemon[4681]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.2.2.
Mar 31 17:13:00 a-desktop avahi-daemon[4681]: New relevant interface eth0.IPv4 for mDNS.
Mar 31 17:13:00 a-desktop avahi-daemon[4681]: Registering new address record for 192.168.2.2 on eth0.IPv4.
Mar 31 17:13:00 a-desktop NetworkManager: <info>  DHCP daemon state is now 2 (bound) for interface eth0 
Mar 31 17:13:00 a-desktop NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Get) scheduled... 
Mar 31 17:13:00 a-desktop NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Get) started... 
Mar 31 17:13:00 a-desktop NetworkManager: <info>  Retrieved the following IP4 configuration from the DHCP daemon: 
Mar 31 17:13:00 a-desktop NetworkManager: <info>    address 192.168.2.2 
Mar 31 17:13:00 a-desktop NetworkManager: <info>    netmask 255.255.255.0 
Mar 31 17:13:00 a-desktop NetworkManager: <info>    broadcast 192.168.2.255 
Mar 31 17:13:00 a-desktop NetworkManager: <info>    gateway 192.168.2.1 
Mar 31 17:13:00 a-desktop NetworkManager: <info>    nameserver 192.168.2.1 
Mar 31 17:13:00 a-desktop NetworkManager: <info>    domain name 'Belkin' 
Mar 31 17:13:00 a-desktop NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) scheduled... 
Mar 31 17:13:00 a-desktop NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Get) complete. 
Mar 31 17:13:00 a-desktop NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) started... 
Mar 31 17:13:00 a-desktop dhclient: bound to 192.168.2.2 -- renewal in 12165534 seconds.
Mar 31 17:13:00 a-desktop avahi-daemon[4681]: Withdrawing address record for 192.168.2.2 on eth0.
Mar 31 17:13:00 a-desktop avahi-daemon[4681]: Leaving mDNS multicast group on interface eth0.IPv4 with address 192.168.2.2.
Mar 31 17:13:00 a-desktop avahi-daemon[4681]: Interface eth0.IPv4 no longer relevant for mDNS.
Mar 31 17:13:00 a-desktop avahi-daemon[4681]: Withdrawing address record for fe80::219:21ff:fe5c:be70 on eth0.
Mar 31 17:13:00 a-desktop avahi-daemon[4681]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.2.2.
Mar 31 17:13:00 a-desktop avahi-daemon[4681]: New relevant interface eth0.IPv4 for mDNS.
Mar 31 17:13:00 a-desktop avahi-daemon[4681]: Registering new address record for 192.168.2.2 on eth0.IPv4.
Mar 31 17:13:01 a-desktop NetworkManager: <info>  Clearing nscd hosts cache. 
Mar 31 17:13:01 a-desktop NetworkManager: <WARN>  nm_spawn_process(): nm_spawn_process('/usr/sbin/nscd -i hosts'): could not spawn process. (Failed to execute child process "/usr/sbin/nscd" (No such file or directory))  
Mar 31 17:13:01 a-desktop NetworkManager: <info>  Activation (eth0) successful, device activated. 
Mar 31 17:13:01 a-desktop NetworkManager: <info>  Activation (eth0) Finish handler scheduled. 
Mar 31 17:13:01 a-desktop NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) complete. 
Mar 31 17:13:02 a-desktop avahi-daemon[4681]: Registering new address record for fe80::219:21ff:fe5c:be70 on eth0.*.
Mar 31 17:13:06 a-desktop ntpdate[6340]: step time server 91.189.94.4 offset -5.114832 sec
Mar 31 17:40:36 a-desktop NetworkManager: <debug> [1270050036.923721] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_154b_16_6E860506004F'). 
Mar 31 17:40:37 a-desktop NetworkManager: <debug> [1270050037.090295] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_154b_16_6E860506004F_if0'). 
Mar 31 17:40:40 a-desktop NetworkManager: <info>  SWITCH: terminating current connection 'eth0' because it's no longer valid. 
Mar 31 17:40:40 a-desktop NetworkManager: <info>  Deactivating device eth0. 
Mar 31 17:40:40 a-desktop dhclient: There is already a pid file /var/run/dhclient.eth0.pid with pid 6280
Mar 31 17:40:40 a-desktop dhclient: killed old client process, removed PID file
Mar 31 17:40:40 a-desktop dhclient: DHCPRELEASE on eth0 to 192.168.2.1 port 67
Mar 31 17:40:40 a-desktop avahi-daemon[4681]: Withdrawing address record for 192.168.2.2 on eth0.
Mar 31 17:40:40 a-desktop avahi-daemon[4681]: Leaving mDNS multicast group on interface eth0.IPv4 with address 192.168.2.2.
Mar 31 17:40:40 a-desktop avahi-daemon[4681]: Interface eth0.IPv4 no longer relevant for mDNS.
Mar 31 17:40:41 a-desktop avahi-daemon[4681]: Withdrawing address record for fe80::219:21ff:fe5c:be70 on eth0.
Mar 31 17:40:41 a-desktop NetworkManager: nm_device_is_802_3_ethernet: assertion `dev != NULL' failed
Mar 31 17:40:41 a-desktop NetworkManager: nm_device_is_802_11_wireless: assertion `dev != NULL' failed
Mar 31 17:40:42 a-desktop NetworkManager: <debug> [1270050042.259372] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_154b_16_6E860506004F_if0_scsi_host'). 
Mar 31 17:40:42 a-desktop NetworkManager: <debug> [1270050042.266674] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_154b_16_6E860506004F_if0_scsi_host_scsi_device_lun0'). 
Mar 31 17:40:43 a-desktop NetworkManager: <debug> [1270050043.975620] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_154b_16_6E860506004F_if0_scsi_host_scsi_device_lun0_scsi_generic'). 
Mar 31 17:40:44 a-desktop NetworkManager: <debug> [1270050044.298967] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_serial_PNY_USB_2_0_FD_6E860506004F_0_0'). 
Mar 31 17:40:44 a-desktop NetworkManager: <debug> [1270050044.440000] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_CCAF_BE7C'). 
Mar 31 17:40:44 a-desktop hald: mounted /dev/sdb1 on behalf of uid 1000
Mar 31 17:42:16 a-desktop NetworkManager: <debug> [1270050136.192173] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_154b_16_6E860506004F_if0_scsi_host_scsi_device_lun0_scsi_generic'). 
Mar 31 17:42:16 a-desktop hald[4813]: forcibly attempting to lazy unmount /dev/sdb1 as enclosing drive was disconnected
Mar 31 17:42:16 a-desktop hald: unmounted /dev/sdb1 from '/media/USB20FD' on behalf of uid 0
Mar 31 17:42:16 a-desktop NetworkManager: <debug> [1270050136.335847] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_CCAF_BE7C'). 
Mar 31 17:42:16 a-desktop NetworkManager: <debug> [1270050136.341589] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/storage_serial_PNY_USB_2_0_FD_6E860506004F_0_0'). 
Mar 31 17:42:16 a-desktop NetworkManager: <debug> [1270050136.347953] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_154b_16_6E860506004F_if0_scsi_host_scsi_device_lun0'). 
Mar 31 17:42:16 a-desktop NetworkManager: <debug> [1270050136.351791] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_154b_16_6E860506004F_if0_scsi_host'). 
Mar 31 17:42:16 a-desktop NetworkManager: <debug> [1270050136.355599] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_154b_16_6E860506004F_if0'). 
Mar 31 17:42:16 a-desktop NetworkManager: <debug> [1270050136.359350] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_154b_16_6E860506004F'). 
Mar 31 17:43:37 a-desktop NetworkManager: <debug> [1270050217.618600] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_154b_16_6E860506004F'). 
Mar 31 17:43:37 a-desktop NetworkManager: <debug> [1270050217.730330] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_154b_16_6E860506004F_if0'). 
Mar 31 17:43:38 a-desktop NetworkManager: <debug> [1270050218.322968] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_154b_16_6E860506004F_if0'). 
Mar 31 17:43:38 a-desktop NetworkManager: <debug> [1270050218.336285] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_154b_16_6E860506004F'). 
Mar 31 17:43:38 a-desktop NetworkManager: <debug> [1270050218.718322] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_154b_16_6E860506004F'). 
Mar 31 17:43:38 a-desktop NetworkManager: <debug> [1270050218.828992] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_154b_16_6E860506004F_if0'). 
Mar 31 17:43:42 a-desktop NetworkManager: <debug> [1270050222.445702] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_154b_16_6E860506004F_if0'). 
Mar 31 17:43:42 a-desktop NetworkManager: <debug> [1270050222.456105] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_154b_16_6E860506004F'). 
Mar 31 17:43:42 a-desktop NetworkManager: <debug> [1270050222.858581] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_154b_16_6E860506004F'). 
Mar 31 17:43:42 a-desktop NetworkManager: <debug> [1270050222.977122] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_154b_16_6E860506004F_if0'). 
Mar 31 17:43:48 a-desktop NetworkManager: <debug> [1270050228.037342] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_154b_16_6E860506004F_if0_scsi_host'). 
Mar 31 17:43:48 a-desktop NetworkManager: <debug> [1270050228.046927] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_154b_16_6E860506004F_if0_scsi_host_scsi_device_lun0'). 
Mar 31 17:43:49 a-desktop NetworkManager: <debug> [1270050229.275360] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_154b_16_6E860506004F_if0_scsi_host_scsi_device_lun0_scsi_generic'). 
Mar 31 17:43:49 a-desktop NetworkManager: <debug> [1270050229.582949] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_serial_PNY_USB_2_0_FD_6E860506004F_0_0'). 
Mar 31 17:43:49 a-desktop NetworkManager: <debug> [1270050229.690361] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_CCAF_BE7C'). 
Mar 31 17:43:50 a-desktop hald: mounted /dev/sdb1 on behalf of uid 1000
Mar 31 17:44:15 a-desktop NetworkManager: <debug> [1270050255.540957] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_154b_16_6E860506004F_if0_scsi_host_scsi_device_lun0_scsi_generic'). 
Mar 31 17:44:15 a-desktop hald[4813]: forcibly attempting to lazy unmount /dev/sdb1 as enclosing drive was disconnected
Mar 31 17:44:15 a-desktop hald: unmounted /dev/sdb1 from '/media/USB20FD' on behalf of uid 0
Mar 31 17:44:15 a-desktop NetworkManager: <debug> [1270050255.660151] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_CCAF_BE7C'). 
Mar 31 17:44:15 a-desktop NetworkManager: <debug> [1270050255.668045] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/storage_serial_PNY_USB_2_0_FD_6E860506004F_0_0'). 
Mar 31 17:44:15 a-desktop NetworkManager: <debug> [1270050255.671755] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_154b_16_6E860506004F_if0_scsi_host_scsi_device_lun0'). 
Mar 31 17:44:15 a-desktop NetworkManager: <debug> [1270050255.675764] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_154b_16_6E860506004F_if0_scsi_host'). 
Mar 31 17:44:15 a-desktop NetworkManager: <debug> [1270050255.697657] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_154b_16_6E860506004F_if0'). 
Mar 31 17:44:15 a-desktop NetworkManager: <debug> [1270050255.726676] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_154b_16_6E860506004F'). 
Mar 31 17:44:15 a-desktop NetworkManager: <debug> [1270050255.913324] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_154b_16_6E860506004F'). 
Mar 31 17:44:16 a-desktop NetworkManager: <debug> [1270050256.128903] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_154b_16_6E860506004F_if0'). 
Mar 31 17:44:16 a-desktop NetworkManager: <debug> [1270050256.384484] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_154b_16_6E860506004F_if0'). 
Mar 31 17:44:16 a-desktop NetworkManager: <debug> [1270050256.396077] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_154b_16_6E860506004F'). 
Mar 31 18:52:31 a-desktop NetworkManager: <info>  Will activate wired connection 'eth0' because it now has a link. 
Mar 31 18:52:31 a-desktop NetworkManager: <info>  SWITCH: no current connection, found better connection 'eth0'. 
Mar 31 18:52:31 a-desktop NetworkManager: <info>  Will activate connection 'eth0'. 
Mar 31 18:52:31 a-desktop NetworkManager: <info>  Device eth0 activation scheduled... 
Mar 31 18:52:31 a-desktop NetworkManager: <info>  Activation (eth0) started... 
Mar 31 18:52:31 a-desktop NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled... 
Mar 31 18:52:31 a-desktop NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) started... 
Mar 31 18:52:31 a-desktop NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) scheduled... 
Mar 31 18:52:31 a-desktop NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) complete. 
Mar 31 18:52:31 a-desktop NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) starting... 
Mar 31 18:52:31 a-desktop NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) successful. 
Mar 31 18:52:31 a-desktop NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled. 
Mar 31 18:52:31 a-desktop NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) complete. 
Mar 31 18:52:31 a-desktop NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) started... 
Mar 31 18:52:32 a-desktop NetworkManager: <info>  Activation (eth0) Beginning DHCP transaction. 
Mar 31 18:52:32 a-desktop dhclient: There is already a pid file /var/run/dhclient.eth0.pid with pid 134519072
Mar 31 18:52:32 a-desktop NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) complete. 
Mar 31 18:52:32 a-desktop NetworkManager: <info>  DHCP daemon state is now 12 (successfully started) for interface eth0 
Mar 31 18:52:32 a-desktop avahi-daemon[4681]: Registering new address record for fe80::219:21ff:fe5c:be70 on eth0.*.
Mar 31 18:52:33 a-desktop NetworkManager: <info>  DHCP daemon state is now 1 (starting) for interface eth0 
Mar 31 18:52:34 a-desktop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
Mar 31 18:52:34 a-desktop dhclient: DHCPOFFER of 192.168.2.2 from 192.168.2.1
Mar 31 18:52:34 a-desktop dhclient: DHCPREQUEST of 192.168.2.2 on eth0 to 255.255.255.255 port 67
Mar 31 18:52:34 a-desktop dhclient: DHCPACK of 192.168.2.2 from 192.168.2.1
Mar 31 18:52:34 a-desktop avahi-daemon[4681]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.2.2.
Mar 31 18:52:34 a-desktop avahi-daemon[4681]: New relevant interface eth0.IPv4 for mDNS.
Mar 31 18:52:34 a-desktop avahi-daemon[4681]: Registering new address record for 192.168.2.2 on eth0.IPv4.
Mar 31 18:52:34 a-desktop NetworkManager: <info>  DHCP daemon state is now 2 (bound) for interface eth0 
Mar 31 18:52:34 a-desktop NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Get) scheduled... 
Mar 31 18:52:34 a-desktop NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Get) started... 
Mar 31 18:52:34 a-desktop NetworkManager: <info>  Retrieved the following IP4 configuration from the DHCP daemon: 
Mar 31 18:52:34 a-desktop NetworkManager: <info>    address 192.168.2.2 
Mar 31 18:52:34 a-desktop NetworkManager: <info>    netmask 255.255.255.0 
Mar 31 18:52:34 a-desktop NetworkManager: <info>    broadcast 192.168.2.255 
Mar 31 18:52:34 a-desktop NetworkManager: <info>    gateway 192.168.2.1 
Mar 31 18:52:34 a-desktop NetworkManager: <info>    nameserver 192.168.2.1 
Mar 31 18:52:34 a-desktop NetworkManager: <info>    domain name 'Belkin' 
Mar 31 18:52:34 a-desktop NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) scheduled... 
Mar 31 18:52:34 a-desktop NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Get) complete. 
Mar 31 18:52:34 a-desktop NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) started... 
Mar 31 18:52:34 a-desktop avahi-daemon[4681]: Withdrawing address record for 192.168.2.2 on eth0.
Mar 31 18:52:34 a-desktop avahi-daemon[4681]: Leaving mDNS multicast group on interface eth0.IPv4 with address 192.168.2.2.
Mar 31 18:52:34 a-desktop avahi-daemon[4681]: Interface eth0.IPv4 no longer relevant for mDNS.
Mar 31 18:52:34 a-desktop avahi-daemon[4681]: Withdrawing address record for fe80::219:21ff:fe5c:be70 on eth0.
Mar 31 18:52:34 a-desktop dhclient: bound to 192.168.2.2 -- renewal in 14912920 seconds.
Mar 31 18:52:34 a-desktop avahi-daemon[4681]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.2.2.
Mar 31 18:52:34 a-desktop avahi-daemon[4681]: New relevant interface eth0.IPv4 for mDNS.
Mar 31 18:52:34 a-desktop avahi-daemon[4681]: Registering new address record for 192.168.2.2 on eth0.IPv4.
Mar 31 18:52:35 a-desktop NetworkManager: <info>  Clearing nscd hosts cache. 
Mar 31 18:52:35 a-desktop NetworkManager: <WARN>  nm_spawn_process(): nm_spawn_process('/usr/sbin/nscd -i hosts'): could not spawn process. (Failed to execute child process "/usr/sbin/nscd" (No such file or directory))  
Mar 31 18:52:35 a-desktop NetworkManager: <info>  Activation (eth0) successful, device activated. 
Mar 31 18:52:35 a-desktop NetworkManager: <info>  Activation (eth0) Finish handler scheduled. 
Mar 31 18:52:35 a-desktop NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) complete. 
Mar 31 18:52:37 a-desktop avahi-daemon[4681]: Registering new address record for fe80::219:21ff:fe5c:be70 on eth0.*.
Mar 31 18:52:40 a-desktop ntpdate[6793]: step time server 91.189.94.4 offset -0.543264 sec
Mar 31 18:56:03 a-desktop NetworkManager: <info>  SWITCH: terminating current connection 'eth0' because it's no longer valid. 
Mar 31 18:56:03 a-desktop NetworkManager: <info>  Deactivating device eth0. 
Mar 31 18:56:03 a-desktop dhclient: There is already a pid file /var/run/dhclient.eth0.pid with pid 6733
Mar 31 18:56:03 a-desktop dhclient: killed old client process, removed PID file
Mar 31 18:56:03 a-desktop dhclient: DHCPRELEASE on eth0 to 192.168.2.1 port 67
Mar 31 18:56:03 a-desktop avahi-daemon[4681]: Withdrawing address record for 192.168.2.2 on eth0.
Mar 31 18:56:03 a-desktop avahi-daemon[4681]: Leaving mDNS multicast group on interface eth0.IPv4 with address 192.168.2.2.
Mar 31 18:56:03 a-desktop avahi-daemon[4681]: Interface eth0.IPv4 no longer relevant for mDNS.
Mar 31 18:56:04 a-desktop avahi-daemon[4681]: Withdrawing address record for fe80::219:21ff:fe5c:be70 on eth0.
Mar 31 18:56:04 a-desktop NetworkManager: nm_device_is_802_3_ethernet: assertion `dev != NULL' failed
Mar 31 18:56:04 a-desktop NetworkManager: nm_device_is_802_11_wireless: assertion `dev != NULL' failed
Mar 31 19:37:42 a-desktop NetworkManager: <info>  Will activate wired connection 'eth0' because it now has a link. 
Mar 31 19:37:42 a-desktop NetworkManager: <info>  SWITCH: no current connection, found better connection 'eth0'. 
Mar 31 19:37:42 a-desktop NetworkManager: <info>  Will activate connection 'eth0'. 
Mar 31 19:37:42 a-desktop NetworkManager: <info>  Device eth0 activation scheduled... 
Mar 31 19:37:42 a-desktop NetworkManager: <info>  Activation (eth0) started... 
Mar 31 19:37:42 a-desktop NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled... 
Mar 31 19:37:42 a-desktop NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) started... 
Mar 31 19:37:42 a-desktop NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) scheduled... 
Mar 31 19:37:42 a-desktop NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) complete. 
Mar 31 19:37:42 a-desktop NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) starting... 
Mar 31 19:37:42 a-desktop NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) successful. 
Mar 31 19:37:42 a-desktop NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled. 
Mar 31 19:37:42 a-desktop NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) complete. 
Mar 31 19:37:42 a-desktop NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) started... 
Mar 31 19:37:43 a-desktop NetworkManager: <info>  Activation (eth0) Beginning DHCP transaction. 
Mar 31 19:37:43 a-desktop dhclient: There is already a pid file /var/run/dhclient.eth0.pid with pid 134519072
Mar 31 19:37:43 a-desktop NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) complete. 
Mar 31 19:37:43 a-desktop NetworkManager: <info>  DHCP daemon state is now 12 (successfully started) for interface eth0 
Mar 31 19:37:43 a-desktop avahi-daemon[4681]: Registering new address record for fe80::219:21ff:fe5c:be70 on eth0.*.
Mar 31 19:37:44 a-desktop NetworkManager: <info>  DHCP daemon state is now 1 (starting) for interface eth0 
Mar 31 19:37:45 a-desktop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
Mar 31 19:37:45 a-desktop dhclient: DHCPOFFER of 192.168.2.2 from 192.168.2.1
Mar 31 19:37:45 a-desktop dhclient: DHCPREQUEST of 192.168.2.2 on eth0 to 255.255.255.255 port 67
Mar 31 19:37:45 a-desktop dhclient: DHCPACK of 192.168.2.2 from 192.168.2.1
Mar 31 19:37:45 a-desktop avahi-daemon[4681]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.2.2.
Mar 31 19:37:45 a-desktop avahi-daemon[4681]: New relevant interface eth0.IPv4 for mDNS.
Mar 31 19:37:45 a-desktop avahi-daemon[4681]: Registering new address record for 192.168.2.2 on eth0.IPv4.
Mar 31 19:37:45 a-desktop NetworkManager: <info>  DHCP daemon state is now 2 (bound) for interface eth0 
Mar 31 19:37:45 a-desktop NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Get) scheduled... 
Mar 31 19:37:45 a-desktop NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Get) started... 
Mar 31 19:37:45 a-desktop NetworkManager: <info>  Retrieved the following IP4 configuration from the DHCP daemon: 
Mar 31 19:37:45 a-desktop NetworkManager: <info>    address 192.168.2.2 
Mar 31 19:37:45 a-desktop NetworkManager: <info>    netmask 255.255.255.0 
Mar 31 19:37:45 a-desktop NetworkManager: <info>    broadcast 192.168.2.255 
Mar 31 19:37:45 a-desktop NetworkManager: <info>    gateway 192.168.2.1 
Mar 31 19:37:45 a-desktop NetworkManager: <info>    nameserver 192.168.2.1 
Mar 31 19:37:45 a-desktop NetworkManager: <info>    domain name 'Belkin' 
Mar 31 19:37:45 a-desktop NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) scheduled... 
Mar 31 19:37:45 a-desktop NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Get) complete. 
Mar 31 19:37:45 a-desktop NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) started... 
Mar 31 19:37:45 a-desktop dhclient: bound to 192.168.2.2 -- renewal in 13284416 seconds.
Mar 31 19:37:45 a-desktop avahi-daemon[4681]: Withdrawing address record for 192.168.2.2 on eth0.
Mar 31 19:37:45 a-desktop avahi-daemon[4681]: Leaving mDNS multicast group on interface eth0.IPv4 with address 192.168.2.2.
Mar 31 19:37:45 a-desktop avahi-daemon[4681]: Interface eth0.IPv4 no longer relevant for mDNS.
Mar 31 19:37:45 a-desktop avahi-daemon[4681]: Withdrawing address record for fe80::219:21ff:fe5c:be70 on eth0.
Mar 31 19:37:45 a-desktop avahi-daemon[4681]: Received packet from invalid interface.
Mar 31 19:37:45 a-desktop avahi-daemon[4681]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.2.2.
Mar 31 19:37:45 a-desktop avahi-daemon[4681]: New relevant interface eth0.IPv4 for mDNS.
Mar 31 19:37:45 a-desktop avahi-daemon[4681]: Registering new address record for 192.168.2.2 on eth0.IPv4.
Mar 31 19:37:46 a-desktop NetworkManager: <info>  Clearing nscd hosts cache. 
Mar 31 19:37:46 a-desktop NetworkManager: <WARN>  nm_spawn_process(): nm_spawn_process('/usr/sbin/nscd -i hosts'): could not spawn process. (Failed to execute child process "/usr/sbin/nscd" (No such file or directory))  
Mar 31 19:37:46 a-desktop NetworkManager: <info>  Activation (eth0) successful, device activated. 
Mar 31 19:37:46 a-desktop NetworkManager: <info>  Activation (eth0) Finish handler scheduled. 
Mar 31 19:37:46 a-desktop NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) complete. 
Mar 31 19:37:47 a-desktop avahi-daemon[4681]: Registering new address record for fe80::219:21ff:fe5c:be70 on eth0.*.
Mar 31 19:37:51 a-desktop ntpdate[6936]: adjust time server 91.189.94.4 offset -0.246883 sec
Mar 31 20:05:24 a-desktop NetworkManager: <info>  SWITCH: terminating current connection 'eth0' because it's no longer valid. 
Mar 31 20:05:24 a-desktop NetworkManager: <info>  Deactivating device eth0. 
Mar 31 20:05:24 a-desktop dhclient: There is already a pid file /var/run/dhclient.eth0.pid with pid 6876
Mar 31 20:05:24 a-desktop dhclient: killed old client process, removed PID file
Mar 31 20:05:24 a-desktop dhclient: DHCPRELEASE on eth0 to 192.168.2.1 port 67
Mar 31 20:05:24 a-desktop avahi-daemon[4681]: Withdrawing address record for 192.168.2.2 on eth0.
Mar 31 20:05:24 a-desktop avahi-daemon[4681]: Leaving mDNS multicast group on interface eth0.IPv4 with address 192.168.2.2.
Mar 31 20:05:24 a-desktop avahi-daemon[4681]: Interface eth0.IPv4 no longer relevant for mDNS.
Mar 31 20:05:25 a-desktop avahi-daemon[4681]: Withdrawing address record for fe80::219:21ff:fe5c:be70 on eth0.
Mar 31 20:05:25 a-desktop NetworkManager: nm_device_is_802_3_ethernet: assertion `dev != NULL' failed
Mar 31 20:05:25 a-desktop NetworkManager: nm_device_is_802_11_wireless: assertion `dev != NULL' failed
Mar 31 20:16:02 a-desktop NetworkManager: <info>  Will activate wired connection 'eth0' because it now has a link. 
Mar 31 20:16:02 a-desktop NetworkManager: <info>  SWITCH: no current connection, found better connection 'eth0'. 
Mar 31 20:16:02 a-desktop NetworkManager: <info>  Will activate connection 'eth0'. 
Mar 31 20:16:02 a-desktop NetworkManager: <info>  Device eth0 activation scheduled... 
Mar 31 20:16:02 a-desktop NetworkManager: <info>  Activation (eth0) started... 
Mar 31 20:16:02 a-desktop NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled... 
Mar 31 20:16:02 a-desktop NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) started... 
Mar 31 20:16:02 a-desktop NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) scheduled... 
Mar 31 20:16:02 a-desktop NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) complete. 
Mar 31 20:16:02 a-desktop NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) starting... 
Mar 31 20:16:02 a-desktop NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) successful. 
Mar 31 20:16:02 a-desktop NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled. 
Mar 31 20:16:02 a-desktop NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) complete. 
Mar 31 20:16:02 a-desktop NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) started... 
Mar 31 20:16:03 a-desktop NetworkManager: <info>  Activation (eth0) Beginning DHCP transaction. 
Mar 31 20:16:03 a-desktop dhclient: There is already a pid file /var/run/dhclient.eth0.pid with pid 134519072
Mar 31 20:16:03 a-desktop NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) complete. 
Mar 31 20:16:03 a-desktop NetworkManager: <info>  DHCP daemon state is now 12 (successfully started) for interface eth0 
Mar 31 20:16:04 a-desktop avahi-daemon[4681]: Registering new address record for fe80::219:21ff:fe5c:be70 on eth0.*.
Mar 31 20:16:04 a-desktop NetworkManager: <info>  DHCP daemon state is now 1 (starting) for interface eth0 
Mar 31 20:16:04 a-desktop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
Mar 31 20:16:04 a-desktop dhclient: DHCPOFFER of 192.168.2.2 from 192.168.2.1
Mar 31 20:16:04 a-desktop dhclient: DHCPREQUEST of 192.168.2.2 on eth0 to 255.255.255.255 port 67
Mar 31 20:16:04 a-desktop dhclient: DHCPACK of 192.168.2.2 from 192.168.2.1
Mar 31 20:16:04 a-desktop avahi-daemon[4681]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.2.2.
Mar 31 20:16:04 a-desktop avahi-daemon[4681]: New relevant interface eth0.IPv4 for mDNS.
Mar 31 20:16:04 a-desktop avahi-daemon[4681]: Registering new address record for 192.168.2.2 on eth0.IPv4.
Mar 31 20:16:04 a-desktop NetworkManager: <info>  DHCP daemon state is now 2 (bound) for interface eth0 
Mar 31 20:16:04 a-desktop NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Get) scheduled... 
Mar 31 20:16:04 a-desktop NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Get) started... 
Mar 31 20:16:04 a-desktop NetworkManager: <info>  Retrieved the following IP4 configuration from the DHCP daemon: 
Mar 31 20:16:04 a-desktop NetworkManager: <info>    address 192.168.2.2 
Mar 31 20:16:04 a-desktop NetworkManager: <info>    netmask 255.255.255.0 
Mar 31 20:16:04 a-desktop NetworkManager: <info>    broadcast 192.168.2.255 
Mar 31 20:16:04 a-desktop NetworkManager: <info>    gateway 192.168.2.1 
Mar 31 20:16:04 a-desktop NetworkManager: <info>    nameserver 192.168.2.1 
Mar 31 20:16:04 a-desktop NetworkManager: <info>    domain name 'Belkin' 
Mar 31 20:16:04 a-desktop NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) scheduled... 
Mar 31 20:16:04 a-desktop NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Get) complete. 
Mar 31 20:16:04 a-desktop NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) started... 
Mar 31 20:16:04 a-desktop dhclient: bound to 192.168.2.2 -- renewal in 15504548 seconds.
Mar 31 20:16:04 a-desktop avahi-daemon[4681]: Withdrawing address record for 192.168.2.2 on eth0.
Mar 31 20:16:04 a-desktop avahi-daemon[4681]: Leaving mDNS multicast group on interface eth0.IPv4 with address 192.168.2.2.
Mar 31 20:16:04 a-desktop avahi-daemon[4681]: Interface eth0.IPv4 no longer relevant for mDNS.
Mar 31 20:16:04 a-desktop avahi-daemon[4681]: Withdrawing address record for fe80::219:21ff:fe5c:be70 on eth0.
Mar 31 20:16:04 a-desktop avahi-daemon[4681]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.2.2.
Mar 31 20:16:04 a-desktop avahi-daemon[4681]: New relevant interface eth0.IPv4 for mDNS.
Mar 31 20:16:04 a-desktop avahi-daemon[4681]: Registering new address record for 192.168.2.2 on eth0.IPv4.
Mar 31 20:16:05 a-desktop NetworkManager: <info>  Clearing nscd hosts cache. 
Mar 31 20:16:05 a-desktop NetworkManager: <WARN>  nm_spawn_process(): nm_spawn_process('/usr/sbin/nscd -i hosts'): could not spawn process. (Failed to execute child process "/usr/sbin/nscd" (No such file or directory))  
Mar 31 20:16:05 a-desktop NetworkManager: <info>  Activation (eth0) successful, device activated. 
Mar 31 20:16:05 a-desktop NetworkManager: <info>  Activation (eth0) Finish handler scheduled. 
Mar 31 20:16:05 a-desktop NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) complete. 
Mar 31 20:16:07 a-desktop avahi-daemon[4681]: Registering new address record for fe80::219:21ff:fe5c:be70 on eth0.*.
Mar 31 20:16:11 a-desktop ntpdate[7083]: adjust time server 91.189.94.4 offset -0.144094 sec
Mar 31 20:51:33 a-desktop init: tty4 main process (4249) killed by TERM signal
Mar 31 20:51:33 a-desktop init: tty5 main process (4250) killed by TERM signal
Mar 31 20:51:33 a-desktop init: tty2 main process (4254) killed by TERM signal
Mar 31 20:51:33 a-desktop init: tty3 main process (4255) killed by TERM signal
Mar 31 20:51:33 a-desktop init: tty6 main process (4258) killed by TERM signal
Mar 31 20:51:33 a-desktop init: tty1 main process (5183) killed by TERM signal
Mar 31 20:51:34 a-desktop gdm[5021]: GLib-CRITICAL: g_hash_table_lookup_extended: assertion `hash_table != NULL' failed 
Mar 31 20:51:34 a-desktop gdm[5021]: WARNING: Request for invalid configuration key xdmcp/Enable=false 
Mar 31 20:51:34 a-desktop avahi-daemon[4681]: Got SIGTERM, quitting.
Mar 31 20:51:34 a-desktop avahi-daemon[4681]: Leaving mDNS multicast group on interface eth0.IPv4 with address 192.168.2.2.
Apr  1 07:39:35 a-desktop NetworkManager: <info>  starting... 
Apr  1 07:39:35 a-desktop avahi-daemon[4681]: Found user 'avahi' (UID 109) and group 'avahi' (GID 120).
Apr  1 07:39:35 a-desktop avahi-daemon[4681]: Successfully dropped root privileges.
Apr  1 07:39:35 a-desktop avahi-daemon[4681]: avahi-daemon 0.6.22 starting up.
Apr  1 07:39:35 a-desktop avahi-daemon[4681]: Successfully called chroot().
Apr  1 07:39:35 a-desktop avahi-daemon[4681]: Successfully dropped remaining capabilities.
Apr  1 07:39:35 a-desktop avahi-daemon[4681]: No service file found in /etc/avahi/services.
Apr  1 07:39:35 a-desktop avahi-daemon[4681]: Network interface enumeration completed.
Apr  1 07:39:35 a-desktop avahi-daemon[4681]: Registering HINFO record with values 'I686'/'LINUX'.
Apr  1 07:39:35 a-desktop avahi-daemon[4681]: Server startup complete. Host name is a-desktop.local. Local service cookie is 3076956356.
Apr  1 07:39:37 a-desktop NetworkManager: <info>  eth0: Device is fully-supported using driver 'r8169'. 
Apr  1 07:39:37 a-desktop NetworkManager: <info>  nm_device_init(): waiting for device's worker thread to start 
Apr  1 07:39:37 a-desktop NetworkManager: <info>  nm_device_init(): device's worker thread started, continuing. 
Apr  1 07:39:37 a-desktop NetworkManager: <info>  Now managing wired Ethernet (802.3) device 'eth0'. 
Apr  1 07:39:37 a-desktop NetworkManager: <info>  Deactivating device eth0. 
Apr  1 07:39:37 a-desktop NetworkManager: <info>  Will activate wired connection 'eth0' because it now has a link. 
Apr  1 07:39:37 a-desktop NetworkManager: <info>  SWITCH: no current connection, found better connection 'eth0'. 
Apr  1 07:39:37 a-desktop hcid[4961]: Bluetooth HCI daemon
Apr  1 07:39:37 a-desktop hcid[4961]: Starting SDP server
Apr  1 07:39:37 a-desktop hcid[4961]: Created local server at unix:abstract=/var/run/dbus-2YqOiRUbI9,guid=429d4431820575885fe40ab94bb43199
Apr  1 07:39:37 a-desktop audio[4974]: Bluetooth Audio daemon
Apr  1 07:39:37 a-desktop input[4978]: Bluetooth Input daemon
Apr  1 07:39:37 a-desktop audio[4974]: Unix socket created: 5
Apr  1 07:39:37 a-desktop audio[4974]: audio.conf: Key file does not have key 'Enable'
Apr  1 07:39:37 a-desktop audio[4974]: audio.conf: Key file does not have key 'Disable'
Apr  1 07:39:37 a-desktop input[4978]: Registered input manager path:/org/bluez/input
Apr  1 07:39:37 a-desktop audio[4974]: add_service_record: got record id 0x10000
Apr  1 07:39:37 a-desktop audio[4974]: audio.conf: Key file does not have key 'Disable'
Apr  1 07:39:37 a-desktop audio[4974]: audio.conf: Key file does not have group 'A2DP'
Apr  1 07:39:37 a-desktop last message repeated 3 times
Apr  1 07:39:37 a-desktop audio[4974]: SEP 0x806d090 registered: type:0 codec:0 seid:1
Apr  1 07:39:37 a-desktop audio[4974]: add_service_record: got record id 0x10001
Apr  1 07:39:37 a-desktop audio[4974]: add_service_record: got record id 0x10002
Apr  1 07:39:37 a-desktop audio[4974]: add_service_record: got record id 0x10003
Apr  1 07:39:37 a-desktop audio[4974]: Registered manager path:/org/bluez/audio
Apr  1 07:39:39 a-desktop NetworkManager: <info>  Will activate connection 'eth0'. 
Apr  1 07:39:39 a-desktop NetworkManager: <info>  Device eth0 activation scheduled... 
Apr  1 07:39:39 a-desktop NetworkManager: <debug> [1270100379.171492] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_bluetooth'). 
Apr  1 07:39:39 a-desktop NetworkManager: <info>  Activation (eth0) started... 
Apr  1 07:39:39 a-desktop NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled... 
Apr  1 07:39:39 a-desktop NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) started... 
Apr  1 07:39:39 a-desktop NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) scheduled... 
Apr  1 07:39:39 a-desktop NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) complete. 
Apr  1 07:39:39 a-desktop NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) starting... 
Apr  1 07:39:39 a-desktop NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) successful. 
Apr  1 07:39:39 a-desktop NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled. 
Apr  1 07:39:39 a-desktop NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) complete. 
Apr  1 07:39:39 a-desktop NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) started... 
Apr  1 07:39:40 a-desktop NetworkManager: <info>  Activation (eth0) Beginning DHCP transaction. 
Apr  1 07:39:40 a-desktop NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) complete. 
Apr  1 07:39:40 a-desktop NetworkManager: <info>  DHCP daemon state is now 12 (successfully started) for interface eth0 
Apr  1 07:39:41 a-desktop NetworkManager: <info>  DHCP daemon state is now 1 (starting) for interface eth0 
Apr  1 07:39:42 a-desktop dhclient: DHCPREQUEST of 192.168.2.2 on eth0 to 255.255.255.255 port 67
Apr  1 07:39:42 a-desktop dhclient: DHCPNAK from 192.168.2.1
Apr  1 07:39:42 a-desktop avahi-autoipd(eth0)[5202]: Found user 'avahi-autoipd' (UID 105) and group 'avahi-autoipd' (GID 113).
Apr  1 07:39:42 a-desktop avahi-autoipd(eth0)[5202]: Successfully called chroot().
Apr  1 07:39:42 a-desktop avahi-autoipd(eth0)[5202]: Successfully dropped root privileges.
Apr  1 07:39:42 a-desktop avahi-autoipd(eth0)[5202]: Starting with address 169.254.6.152
Apr  1 07:39:48 a-desktop avahi-autoipd(eth0)[5202]: Callout BIND, address 169.254.6.152 on interface eth0
Apr  1 07:39:48 a-desktop avahi-daemon[4681]: Joining mDNS multicast group on interface eth0.IPv4 with address 169.254.6.152.
Apr  1 07:39:48 a-desktop avahi-daemon[4681]: New relevant interface eth0.IPv4 for mDNS.
Apr  1 07:39:48 a-desktop avahi-daemon[4681]: Registering new address record for 169.254.6.152 on eth0.IPv4.
Apr  1 07:39:52 a-desktop avahi-autoipd(eth0)[5202]: Successfully claimed IP address 169.254.6.152
Apr  1 07:39:52 a-desktop NetworkManager: <info>  DHCP daemon state is now 10 (unknown) for interface eth0 
Apr  1 07:39:52 a-desktop avahi-autoipd(eth0)[5202]: Got SIGTERM, quitting.
Apr  1 07:39:52 a-desktop avahi-autoipd(eth0)[5202]: Callout STOP, address 169.254.6.152 on interface eth0
Apr  1 07:39:52 a-desktop avahi-daemon[4681]: Withdrawing address record for 169.254.6.152 on eth0.
Apr  1 07:39:52 a-desktop avahi-daemon[4681]: Leaving mDNS multicast group on interface eth0.IPv4 with address 169.254.6.152.
Apr  1 07:39:52 a-desktop avahi-daemon[4681]: Interface eth0.IPv4 no longer relevant for mDNS.
Apr  1 07:39:52 a-desktop avahi-autoipd(eth0)[5203]: client: RTNETLINK answers: No such process
Apr  1 07:39:53 a-desktop NetworkManager: <info>  DHCP daemon state is now 1 (starting) for interface eth0 
Apr  1 07:39:53 a-desktop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
Apr  1 07:39:55 a-desktop dhclient: DHCPOFFER of 192.168.2.2 from 192.168.2.1
Apr  1 07:39:55 a-desktop dhclient: DHCPREQUEST of 192.168.2.2 on eth0 to 255.255.255.255 port 67
Apr  1 07:39:55 a-desktop dhclient: DHCPACK of 192.168.2.2 from 192.168.2.1
Apr  1 07:39:55 a-desktop avahi-daemon[4681]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.2.2.
Apr  1 07:39:55 a-desktop avahi-daemon[4681]: New relevant interface eth0.IPv4 for mDNS.
Apr  1 07:39:55 a-desktop avahi-daemon[4681]: Registering new address record for 192.168.2.2 on eth0.IPv4.
Apr  1 07:39:55 a-desktop NetworkManager: <info>  DHCP daemon state is now 2 (bound) for interface eth0 
Apr  1 07:39:55 a-desktop NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Get) scheduled... 
Apr  1 07:39:55 a-desktop NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Get) started... 
Apr  1 07:39:55 a-desktop NetworkManager: <info>  Retrieved the following IP4 configuration from the DHCP daemon: 
Apr  1 07:39:55 a-desktop NetworkManager: <info>    address 192.168.2.2 
Apr  1 07:39:55 a-desktop NetworkManager: <info>    netmask 255.255.255.0 
Apr  1 07:39:55 a-desktop NetworkManager: <info>    broadcast 192.168.2.255 
Apr  1 07:39:55 a-desktop NetworkManager: <info>    gateway 192.168.2.1 
Apr  1 07:39:55 a-desktop NetworkManager: <info>    nameserver 192.168.2.1 
Apr  1 07:39:55 a-desktop NetworkManager: <info>    domain name 'Belkin' 
Apr  1 07:39:55 a-desktop NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) scheduled... 
Apr  1 07:39:55 a-desktop NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Get) complete. 
Apr  1 07:39:55 a-desktop NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) started... 
Apr  1 07:39:55 a-desktop dhclient: bound to 192.168.2.2 -- renewal in 12355560 seconds.
Apr  1 07:39:55 a-desktop avahi-daemon[4681]: Withdrawing address record for 192.168.2.2 on eth0.
Apr  1 07:39:55 a-desktop avahi-daemon[4681]: Leaving mDNS multicast group on interface eth0.IPv4 with address 192.168.2.2.
Apr  1 07:39:55 a-desktop avahi-daemon[4681]: Interface eth0.IPv4 no longer relevant for mDNS.
Apr  1 07:39:55 a-desktop avahi-daemon[4681]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.2.2.
Apr  1 07:39:55 a-desktop avahi-daemon[4681]: New relevant interface eth0.IPv4 for mDNS.
Apr  1 07:39:55 a-desktop avahi-daemon[4681]: Registering new address record for 192.168.2.2 on eth0.IPv4.
Apr  1 07:39:56 a-desktop NetworkManager: <info>  Clearing nscd hosts cache. 
Apr  1 07:39:56 a-desktop NetworkManager: <WARN>  nm_spawn_process(): nm_spawn_process('/usr/sbin/nscd -i hosts'): could not spawn process. (Failed to execute child process "/usr/sbin/nscd" (No such file or directory))  
Apr  1 07:39:56 a-desktop NetworkManager: <info>  Activation (eth0) successful, device activated. 
Apr  1 07:39:56 a-desktop NetworkManager: <info>  Activation (eth0) Finish handler scheduled. 
Apr  1 07:39:56 a-desktop NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) complete. 
Apr  1 07:39:57 a-desktop ntpdate[5349]: can't find host ntp.ubuntu.com 
Apr  1 07:39:57 a-desktop ntpdate[5349]: no servers can be used, exiting
Apr  1 07:39:59 a-desktop avahi-daemon[4681]: Registering new address record for fe80::219:21ff:fe5c:be70 on eth0.*.
Apr  1 07:40:00 a-desktop hcid[4961]: Default passkey agent (:1.22, /org/bluez/passkey) registered
Apr  1 07:40:00 a-desktop hcid[4961]: Default authorization agent (:1.22, /org/bluez/auth) registered
Apr  1 07:40:05 a-desktop NetworkManager: <info>  Updating allowed wireless network lists. 
Apr  1 07:40:05 a-desktop NetworkManager: <WARN>  nm_dbus_get_networks_cb(): error received: org.freedesktop.NetworkManagerInfo.NoNetworks - There are no wireless networks stored.. 
Apr  1 09:10:18 a-desktop NetworkManager: <info>  SWITCH: terminating current connection 'eth0' because it's no longer valid. 
Apr  1 09:10:18 a-desktop NetworkManager: <info>  Deactivating device eth0. 
Apr  1 09:10:18 a-desktop dhclient: There is already a pid file /var/run/dhclient.eth0.pid with pid 5172
Apr  1 09:10:18 a-desktop dhclient: killed old client process, removed PID file
Apr  1 09:10:18 a-desktop dhclient: DHCPRELEASE on eth0 to 192.168.2.1 port 67
Apr  1 09:10:18 a-desktop avahi-daemon[4681]: Withdrawing address record for 192.168.2.2 on eth0.
Apr  1 09:10:18 a-desktop avahi-daemon[4681]: Leaving mDNS multicast group on interface eth0.IPv4 with address 192.168.2.2.
Apr  1 09:10:18 a-desktop avahi-daemon[4681]: Interface eth0.IPv4 no longer relevant for mDNS.
Apr  1 09:10:19 a-desktop avahi-daemon[4681]: Withdrawing address record for fe80::219:21ff:fe5c:be70 on eth0.
Apr  1 09:10:19 a-desktop NetworkManager: nm_device_is_802_3_ethernet: assertion `dev != NULL' failed
Apr  1 09:10:19 a-desktop NetworkManager: nm_device_is_802_11_wireless: assertion `dev != NULL' failed
Apr  1 09:10:22 a-desktop NetworkManager: <info>  Will activate wired connection 'eth0' because it now has a link. 
Apr  1 09:10:22 a-desktop NetworkManager: <info>  SWITCH: no current connection, found better connection 'eth0'. 
Apr  1 09:10:22 a-desktop NetworkManager: <info>  Will activate connection 'eth0'. 
Apr  1 09:10:22 a-desktop NetworkManager: <info>  Device eth0 activation scheduled... 
Apr  1 09:10:22 a-desktop NetworkManager: <info>  Activation (eth0) started... 
Apr  1 09:10:22 a-desktop NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled... 
Apr  1 09:10:22 a-desktop NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) started... 
Apr  1 09:10:22 a-desktop NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) scheduled... 
Apr  1 09:10:22 a-desktop NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) complete. 
Apr  1 09:10:22 a-desktop NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) starting... 
Apr  1 09:10:22 a-desktop NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) successful. 
Apr  1 09:10:22 a-desktop NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled. 
Apr  1 09:10:22 a-desktop NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) complete. 
Apr  1 09:10:22 a-desktop NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) started... 
Apr  1 09:10:23 a-desktop NetworkManager: <info>  Activation (eth0) Beginning DHCP transaction. 
Apr  1 09:10:23 a-desktop dhclient: There is already a pid file /var/run/dhclient.eth0.pid with pid 134519072
Apr  1 09:10:23 a-desktop NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) complete. 
Apr  1 09:10:23 a-desktop NetworkManager: <info>  DHCP daemon state is now 12 (successfully started) for interface eth0 
Apr  1 09:10:24 a-desktop avahi-daemon[4681]: Registering new address record for fe80::219:21ff:fe5c:be70 on eth0.*.
Apr  1 09:10:25 a-desktop NetworkManager: <info>  DHCP daemon state is now 1 (starting) for interface eth0 
Apr  1 09:10:28 a-desktop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
Apr  1 09:10:32 a-desktop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
Apr  1 09:10:35 a-desktop NetworkManager: <info>  SWITCH: terminating current connection 'eth0' because it's no longer valid. 
Apr  1 09:10:35 a-desktop NetworkManager: <info>  Deactivating device eth0. 
Apr  1 09:10:35 a-desktop NetworkManager: <info>  Activation (eth0): cancelling... 
Apr  1 09:10:35 a-desktop NetworkManager: <info>  Activation (eth0) cancellation handler scheduled... 
Apr  1 09:10:35 a-desktop NetworkManager: <info>  Activation (eth0): waiting for device to cancel activation. 
Apr  1 09:10:35 a-desktop dhclient: There is already a pid file /var/run/dhclient.eth0.pid with pid 5798
Apr  1 09:10:35 a-desktop dhclient: killed old client process, removed PID file
Apr  1 09:10:35 a-desktop dhclient: DHCPRELEASE on eth0 to 192.168.2.1 port 67
Apr  1 09:10:35 a-desktop dhclient: send_packet: Network is unreachable
Apr  1 09:10:35 a-desktop dhclient: send_packet: please consult README file regarding broadcast address.
Apr  1 09:10:36 a-desktop NetworkManager: <info>  Activation (eth0): waiting for device to cancel activation. 
Apr  1 09:10:36 a-desktop NetworkManager: <info>  Activation (eth0) cancellation handled. 
Apr  1 09:10:36 a-desktop NetworkManager: <info>  Activation (eth0): cancelled. 
Apr  1 09:10:36 a-desktop avahi-daemon[4681]: Withdrawing address record for fe80::219:21ff:fe5c:be70 on eth0.
Apr  1 09:10:36 a-desktop NetworkManager: nm_device_is_802_3_ethernet: assertion `dev != NULL' failed
Apr  1 09:10:36 a-desktop NetworkManager: nm_device_is_802_11_wireless: assertion `dev != NULL' failed
Apr  1 09:10:38 a-desktop NetworkManager: <info>  Will activate wired connection 'eth0' because it now has a link. 
Apr  1 09:10:38 a-desktop NetworkManager: <info>  SWITCH: no current connection, found better connection 'eth0'. 
Apr  1 09:10:38 a-desktop NetworkManager: <info>  Will activate connection 'eth0'. 
Apr  1 09:10:38 a-desktop NetworkManager: <info>  Device eth0 activation scheduled... 
Apr  1 09:10:38 a-desktop NetworkManager: <info>  Activation (eth0) started... 
Apr  1 09:10:38 a-desktop NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled... 
Apr  1 09:10:38 a-desktop NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) started... 
Apr  1 09:10:38 a-desktop NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) scheduled... 
Apr  1 09:10:38 a-desktop NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) complete. 
Apr  1 09:10:38 a-desktop NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) starting... 
Apr  1 09:10:38 a-desktop NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) successful. 
Apr  1 09:10:38 a-desktop NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled. 
Apr  1 09:10:38 a-desktop NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) complete. 
Apr  1 09:10:38 a-desktop NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) started... 
Apr  1 09:10:39 a-desktop NetworkManager: <info>  Activation (eth0) Beginning DHCP transaction. 
Apr  1 09:10:39 a-desktop dhclient: There is already a pid file /var/run/dhclient.eth0.pid with pid 134519072
Apr  1 09:10:39 a-desktop NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) complete. 
Apr  1 09:10:39 a-desktop NetworkManager: <info>  DHCP daemon state is now 12 (successfully started) for interface eth0 
Apr  1 09:10:39 a-desktop avahi-daemon[4681]: Registering new address record for fe80::219:21ff:fe5c:be70 on eth0.*.
Apr  1 09:10:40 a-desktop NetworkManager: <info>  DHCP daemon state is now 1 (starting) for interface eth0 
Apr  1 09:10:43 a-desktop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
Apr  1 09:10:49 a-desktop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
Apr  1 09:11:02 a-desktop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
Apr  1 09:11:02 a-desktop dhclient: DHCPOFFER of 192.168.2.2 from 192.168.2.1
Apr  1 09:11:02 a-desktop dhclient: DHCPREQUEST of 192.168.2.2 on eth0 to 255.255.255.255 port 67
Apr  1 09:11:02 a-desktop dhclient: DHCPACK of 192.168.2.2 from 192.168.2.1
Apr  1 09:11:02 a-desktop avahi-daemon[4681]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.2.2.
Apr  1 09:11:02 a-desktop avahi-daemon[4681]: New relevant interface eth0.IPv4 for mDNS.
Apr  1 09:11:02 a-desktop avahi-daemon[4681]: Registering new address record for 192.168.2.2 on eth0.IPv4.
Apr  1 09:11:02 a-desktop NetworkManager: <info>  DHCP daemon state is now 2 (bound) for interface eth0 
Apr  1 09:11:02 a-desktop NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Get) scheduled... 
Apr  1 09:11:02 a-desktop NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Get) started... 
Apr  1 09:11:02 a-desktop NetworkManager: <info>  Retrieved the following IP4 configuration from the DHCP daemon: 
Apr  1 09:11:02 a-desktop NetworkManager: <info>    address 192.168.2.2 
Apr  1 09:11:02 a-desktop NetworkManager: <info>    netmask 255.255.255.0 
Apr  1 09:11:02 a-desktop NetworkManager: <info>    broadcast 192.168.2.255 
Apr  1 09:11:02 a-desktop NetworkManager: <info>    gateway 192.168.2.1 
Apr  1 09:11:02 a-desktop NetworkManager: <info>    nameserver 192.168.2.1 
Apr  1 09:11:02 a-desktop NetworkManager: <info>    domain name 'Belkin' 
Apr  1 09:11:02 a-desktop NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) scheduled... 
Apr  1 09:11:02 a-desktop NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Get) complete. 
Apr  1 09:11:02 a-desktop NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) started... 
Apr  1 09:11:02 a-desktop dhclient: bound to 192.168.2.2 -- renewal in 14949382 seconds.
Apr  1 09:11:02 a-desktop avahi-daemon[4681]: Withdrawing address record for 192.168.2.2 on eth0.
Apr  1 09:11:02 a-desktop avahi-daemon[4681]: Leaving mDNS multicast group on interface eth0.IPv4 with address 192.168.2.2.
Apr  1 09:11:02 a-desktop avahi-daemon[4681]: Interface eth0.IPv4 no longer relevant for mDNS.
Apr  1 09:11:02 a-desktop avahi-daemon[4681]: Withdrawing address record for fe80::219:21ff:fe5c:be70 on eth0.
Apr  1 09:11:02 a-desktop avahi-daemon[4681]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.2.2.
Apr  1 09:11:02 a-desktop avahi-daemon[4681]: New relevant interface eth0.IPv4 for mDNS.
Apr  1 09:11:02 a-desktop avahi-daemon[4681]: Registering new address record for 192.168.2.2 on eth0.IPv4.
Apr  1 09:11:03 a-desktop NetworkManager: <info>  Clearing nscd hosts cache. 
Apr  1 09:11:03 a-desktop NetworkManager: <WARN>  nm_spawn_process(): nm_spawn_process('/usr/sbin/nscd -i hosts'): could not spawn process. (Failed to execute child process "/usr/sbin/nscd" (No such file or directory))  
Apr  1 09:11:03 a-desktop NetworkManager: <info>  Activation (eth0) successful, device activated. 
Apr  1 09:11:03 a-desktop NetworkManager: <info>  Activation (eth0) Finish handler scheduled. 
Apr  1 09:11:03 a-desktop NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) complete. 
Apr  1 09:11:03 a-desktop ntpdate[5906]: can't find host ntp.ubuntu.com 
Apr  1 09:11:03 a-desktop ntpdate[5906]: no servers can be used, exiting
Apr  1 09:11:04 a-desktop avahi-daemon[4681]: Registering new address record for fe80::219:21ff:fe5c:be70 on eth0.*.
Apr  1 13:23:08 a-desktop NetworkManager: <info>  SWITCH: terminating current connection 'eth0' because it's no longer valid. 
Apr  1 13:23:08 a-desktop NetworkManager: <info>  Deactivating device eth0. 
Apr  1 13:23:08 a-desktop dhclient: There is already a pid file /var/run/dhclient.eth0.pid with pid 5845
Apr  1 13:23:08 a-desktop dhclient: killed old client process, removed PID file
Apr  1 13:23:08 a-desktop dhclient: DHCPRELEASE on eth0 to 192.168.2.1 port 67
Apr  1 13:23:08 a-desktop avahi-daemon[4681]: Withdrawing address record for 192.168.2.2 on eth0.
Apr  1 13:23:08 a-desktop avahi-daemon[4681]: Leaving mDNS multicast group on interface eth0.IPv4 with address 192.168.2.2.
Apr  1 13:23:08 a-desktop avahi-daemon[4681]: Interface eth0.IPv4 no longer relevant for mDNS.
Apr  1 13:23:09 a-desktop avahi-daemon[4681]: Withdrawing address record for fe80::219:21ff:fe5c:be70 on eth0.
Apr  1 13:23:09 a-desktop NetworkManager: nm_device_is_802_3_ethernet: assertion `dev != NULL' failed
Apr  1 13:23:09 a-desktop NetworkManager: nm_device_is_802_11_wireless: assertion `dev != NULL' failed
Apr  1 13:45:23 a-desktop NetworkManager: <info>  Will activate wired connection 'eth0' because it now has a link. 
Apr  1 13:45:23 a-desktop NetworkManager: <info>  SWITCH: no current connection, found better connection 'eth0'. 
Apr  1 13:45:23 a-desktop NetworkManager: <info>  Will activate connection 'eth0'. 
Apr  1 13:45:23 a-desktop NetworkManager: <info>  Device eth0 activation scheduled... 
Apr  1 13:45:23 a-desktop NetworkManager: <info>  Activation (eth0) started... 
Apr  1 13:45:23 a-desktop NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled... 
Apr  1 13:45:23 a-desktop NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) started... 
Apr  1 13:45:23 a-desktop NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) scheduled... 
Apr  1 13:45:23 a-desktop NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) complete. 
Apr  1 13:45:23 a-desktop NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) starting... 
Apr  1 13:45:23 a-desktop NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) successful. 
Apr  1 13:45:23 a-desktop NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled. 
Apr  1 13:45:23 a-desktop NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) complete. 
Apr  1 13:45:23 a-desktop NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) started... 
Apr  1 13:45:24 a-desktop NetworkManager: <info>  Activation (eth0) Beginning DHCP transaction. 
Apr  1 13:45:24 a-desktop dhclient: There is already a pid file /var/run/dhclient.eth0.pid with pid 134519072
Apr  1 13:45:24 a-desktop NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) complete. 
Apr  1 13:45:24 a-desktop NetworkManager: <info>  DHCP daemon state is now 12 (successfully started) for interface eth0 
Apr  1 13:45:25 a-desktop avahi-daemon[4681]: Registering new address record for fe80::219:21ff:fe5c:be70 on eth0.*.
Apr  1 13:45:25 a-desktop NetworkManager: <info>  DHCP daemon state is now 1 (starting) for interface eth0 
Apr  1 13:45:25 a-desktop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
Apr  1 13:45:25 a-desktop dhclient: DHCPOFFER of 192.168.2.2 from 192.168.2.1
Apr  1 13:45:25 a-desktop dhclient: DHCPREQUEST of 192.168.2.2 on eth0 to 255.255.255.255 port 67
Apr  1 13:45:25 a-desktop dhclient: DHCPACK of 192.168.2.2 from 192.168.2.1
Apr  1 13:45:25 a-desktop avahi-daemon[4681]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.2.2.
Apr  1 13:45:25 a-desktop avahi-daemon[4681]: New relevant interface eth0.IPv4 for mDNS.
Apr  1 13:45:25 a-desktop avahi-daemon[4681]: Registering new address record for 192.168.2.2 on eth0.IPv4.
Apr  1 13:45:25 a-desktop NetworkManager: <info>  DHCP daemon state is now 2 (bound) for interface eth0 
Apr  1 13:45:25 a-desktop NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Get) scheduled... 
Apr  1 13:45:25 a-desktop NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Get) started... 
Apr  1 13:45:25 a-desktop NetworkManager: <info>  Retrieved the following IP4 configuration from the DHCP daemon: 
Apr  1 13:45:25 a-desktop NetworkManager: <info>    address 192.168.2.2 
Apr  1 13:45:25 a-desktop NetworkManager: <info>    netmask 255.255.255.0 
Apr  1 13:45:25 a-desktop NetworkManager: <info>    broadcast 192.168.2.255 
Apr  1 13:45:25 a-desktop NetworkManager: <info>    gateway 192.168.2.1 
Apr  1 13:45:25 a-desktop NetworkManager: <info>    nameserver 192.168.2.1 
Apr  1 13:45:25 a-desktop NetworkManager: <info>    domain name 'Belkin' 
Apr  1 13:45:25 a-desktop NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) scheduled... 
Apr  1 13:45:25 a-desktop NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Get) complete. 
Apr  1 13:45:25 a-desktop NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) started... 
Apr  1 13:45:25 a-desktop dhclient: bound to 192.168.2.2 -- renewal in 13608169 seconds.
Apr  1 13:45:25 a-desktop avahi-daemon[4681]: Withdrawing address record for 192.168.2.2 on eth0.
Apr  1 13:45:25 a-desktop avahi-daemon[4681]: Leaving mDNS multicast group on interface eth0.IPv4 with address 192.168.2.2.
Apr  1 13:45:26 a-desktop avahi-daemon[4681]: Interface eth0.IPv4 no longer relevant for mDNS.
Apr  1 13:45:26 a-desktop avahi-daemon[4681]: Withdrawing address record for fe80::219:21ff:fe5c:be70 on eth0.
Apr  1 13:45:26 a-desktop avahi-daemon[4681]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.2.2.
Apr  1 13:45:26 a-desktop avahi-daemon[4681]: New relevant interface eth0.IPv4 for mDNS.
Apr  1 13:45:26 a-desktop avahi-daemon[4681]: Registering new address record for 192.168.2.2 on eth0.IPv4.
Apr  1 13:45:27 a-desktop NetworkManager: <info>  Clearing nscd hosts cache. 
Apr  1 13:45:27 a-desktop NetworkManager: <WARN>  nm_spawn_process(): nm_spawn_process('/usr/sbin/nscd -i hosts'): could not spawn process. (Failed to execute child process "/usr/sbin/nscd" (No such file or directory))  
Apr  1 13:45:27 a-desktop NetworkManager: <info>  Activation (eth0) successful, device activated. 
Apr  1 13:45:27 a-desktop NetworkManager: <info>  Activation (eth0) Finish handler scheduled. 
Apr  1 13:45:27 a-desktop NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) complete. 
Apr  1 13:45:25 a-desktop ntpdate[6155]: step time server 91.189.94.4 offset -2.101435 sec
Apr  1 13:45:26 a-desktop avahi-daemon[4681]: Registering new address record for fe80::219:21ff:fe5c:be70 on eth0.*.
Apr  1 23:19:53 a-desktop init: tty4 main process (4249) killed by TERM signal
Apr  1 23:19:53 a-desktop init: tty5 main process (4250) killed by TERM signal
Apr  1 23:19:53 a-desktop init: tty2 main process (4254) killed by TERM signal
Apr  1 23:19:53 a-desktop init: tty3 main process (4255) killed by TERM signal
Apr  1 23:19:53 a-desktop init: tty6 main process (4257) killed by TERM signal
Apr  1 23:19:53 a-desktop init: tty1 main process (5176) killed by TERM signal
Apr  1 23:19:53 a-desktop avahi-daemon[4681]: Got SIGTERM, quitting.
Apr  1 23:19:53 a-desktop avahi-daemon[4681]: Leaving mDNS multicast group on interface eth0.IPv4 with address 192.168.2.2.
Apr  2 09:11:24 a-desktop NetworkManager: <info>  starting... 
Apr  2 09:11:24 a-desktop avahi-daemon[4678]: Found user 'avahi' (UID 109) and group 'avahi' (GID 120).
Apr  2 09:11:24 a-desktop avahi-daemon[4678]: Successfully dropped root privileges.
Apr  2 09:11:24 a-desktop avahi-daemon[4678]: avahi-daemon 0.6.22 starting up.
Apr  2 09:11:24 a-desktop avahi-daemon[4678]: Successfully called chroot().
Apr  2 09:11:24 a-desktop avahi-daemon[4678]: Successfully dropped remaining capabilities.
Apr  2 09:11:24 a-desktop avahi-daemon[4678]: No service file found in /etc/avahi/services.
Apr  2 09:11:24 a-desktop avahi-daemon[4678]: Network interface enumeration completed.
Apr  2 09:11:24 a-desktop avahi-daemon[4678]: Registering HINFO record with values 'I686'/'LINUX'.
Apr  2 09:11:24 a-desktop avahi-daemon[4678]: Server startup complete. Host name is a-desktop.local. Local service cookie is 1324064288.
Apr  2 09:11:26 a-desktop NetworkManager: <info>  eth0: Device is fully-supported using driver 'r8169'. 
Apr  2 09:11:26 a-desktop NetworkManager: <info>  nm_device_init(): waiting for device's worker thread to start 
Apr  2 09:11:26 a-desktop NetworkManager: <info>  nm_device_init(): device's worker thread started, continuing. 
Apr  2 09:11:26 a-desktop NetworkManager: <info>  Now managing wired Ethernet (802.3) device 'eth0'. 
Apr  2 09:11:26 a-desktop NetworkManager: <info>  Deactivating device eth0. 
Apr  2 09:11:26 a-desktop NetworkManager: <info>  Will activate wired connection 'eth0' because it now has a link. 
Apr  2 09:11:26 a-desktop NetworkManager: <info>  SWITCH: no current connection, found better connection 'eth0'. 
Apr  2 09:11:26 a-desktop hcid[4958]: Bluetooth HCI daemon
Apr  2 09:11:26 a-desktop hcid[4958]: Starting SDP server
Apr  2 09:11:26 a-desktop hcid[4958]: Created local server at unix:abstract=/var/run/dbus-8rhoC5Bf5k,guid=bdd67798bc5a06a1853819164bb5989e
Apr  2 09:11:26 a-desktop audio[4971]: Bluetooth Audio daemon
Apr  2 09:11:26 a-desktop audio[4971]: Unix socket created: 5
Apr  2 09:11:26 a-desktop audio[4971]: audio.conf: Key file does not have key 'Enable'
Apr  2 09:11:26 a-desktop audio[4971]: audio.conf: Key file does not have key 'Disable'
Apr  2 09:11:26 a-desktop input[4975]: Bluetooth Input daemon
Apr  2 09:11:26 a-desktop input[4975]: Registered input manager path:/org/bluez/input
Apr  2 09:11:26 a-desktop audio[4971]: add_service_record: got record id 0x10000
Apr  2 09:11:26 a-desktop audio[4971]: audio.conf: Key file does not have key 'Disable'
Apr  2 09:11:26 a-desktop audio[4971]: audio.conf: Key file does not have group 'A2DP'
Apr  2 09:11:26 a-desktop last message repeated 3 times
Apr  2 09:11:26 a-desktop audio[4971]: SEP 0x806d090 registered: type:0 codec:0 seid:1
Apr  2 09:11:26 a-desktop audio[4971]: add_service_record: got record id 0x10001
Apr  2 09:11:26 a-desktop audio[4971]: add_service_record: got record id 0x10002
Apr  2 09:11:26 a-desktop audio[4971]: add_service_record: got record id 0x10003
Apr  2 09:11:26 a-desktop audio[4971]: Registered manager path:/org/bluez/audio
Apr  2 09:11:28 a-desktop NetworkManager: <info>  Will activate connection 'eth0'. 
Apr  2 09:11:28 a-desktop NetworkManager: <info>  Device eth0 activation scheduled... 
Apr  2 09:11:28 a-desktop NetworkManager: <debug> [1270192288.235857] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_bluetooth'). 
Apr  2 09:11:28 a-desktop NetworkManager: <info>  Activation (eth0) started... 
Apr  2 09:11:28 a-desktop NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled... 
Apr  2 09:11:28 a-desktop NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) started... 
Apr  2 09:11:28 a-desktop NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) scheduled... 
Apr  2 09:11:28 a-desktop NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) complete. 
Apr  2 09:11:28 a-desktop NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) starting... 
Apr  2 09:11:28 a-desktop NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) successful. 
Apr  2 09:11:28 a-desktop NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled. 
Apr  2 09:11:28 a-desktop NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) complete. 
Apr  2 09:11:28 a-desktop NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) started... 
Apr  2 09:11:29 a-desktop NetworkManager: <info>  Activation (eth0) Beginning DHCP transaction. 
Apr  2 09:11:29 a-desktop NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) complete. 
Apr  2 09:11:29 a-desktop NetworkManager: <info>  DHCP daemon state is now 12 (successfully started) for interface eth0 
Apr  2 09:11:30 a-desktop NetworkManager: <info>  DHCP daemon state is now 1 (starting) for interface eth0 
Apr  2 09:11:33 a-desktop dhclient: DHCPREQUEST of 192.168.2.2 on eth0 to 255.255.255.255 port 67
Apr  2 09:11:38 a-desktop dhclient: DHCPREQUEST of 192.168.2.2 on eth0 to 255.255.255.255 port 67
Apr  2 09:11:48 a-desktop avahi-daemon[4678]: Registering new address record for fe80::219:21ff:fe5c:be70 on eth0.*.
Apr  2 09:11:49 a-desktop hcid[4958]: Default passkey agent (:1.19, /org/bluez/passkey) registered
Apr  2 09:11:49 a-desktop hcid[4958]: Default authorization agent (:1.19, /org/bluez/auth) registered
Apr  2 09:11:51 a-desktop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
Apr  2 09:11:54 a-desktop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
Apr  2 09:11:55 a-desktop NetworkManager: <info>  Updating allowed wireless network lists. 
Apr  2 09:11:55 a-desktop NetworkManager: <WARN>  nm_dbus_get_networks_cb(): error received: org.freedesktop.NetworkManagerInfo.NoNetworks - There are no wireless networks stored.. 
Apr  2 09:12:02 a-desktop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
Apr  2 09:12:16 a-desktop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
Apr  2 09:12:22 a-desktop dhclient: No DHCPOFFERS received.
Apr  2 09:12:22 a-desktop dhclient: Trying recorded lease 192.168.2.2
Apr  2 09:12:22 a-desktop avahi-daemon[4678]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.2.2.
Apr  2 09:12:22 a-desktop avahi-daemon[4678]: New relevant interface eth0.IPv4 for mDNS.
Apr  2 09:12:22 a-desktop avahi-daemon[4678]: Registering new address record for 192.168.2.2 on eth0.IPv4.
Apr  2 09:12:25 a-desktop avahi-daemon[4678]: Withdrawing address record for 192.168.2.2 on eth0.
Apr  2 09:12:25 a-desktop avahi-daemon[4678]: Leaving mDNS multicast group on interface eth0.IPv4 with address 192.168.2.2.
Apr  2 09:12:25 a-desktop avahi-daemon[4678]: Interface eth0.IPv4 no longer relevant for mDNS.
Apr  2 09:12:25 a-desktop avahi-autoipd(eth0)[5435]: Found user 'avahi-autoipd' (UID 105) and group 'avahi-autoipd' (GID 113).
Apr  2 09:12:25 a-desktop avahi-autoipd(eth0)[5435]: Successfully called chroot().
Apr  2 09:12:25 a-desktop avahi-autoipd(eth0)[5435]: Successfully dropped root privileges.
Apr  2 09:12:25 a-desktop avahi-autoipd(eth0)[5435]: Starting with address 169.254.6.152
Apr  2 09:12:30 a-desktop avahi-autoipd(eth0)[5435]: Callout BIND, address 169.254.6.152 on interface eth0
Apr  2 09:12:30 a-desktop avahi-daemon[4678]: Joining mDNS multicast group on interface eth0.IPv4 with address 169.254.6.152.
Apr  2 09:12:30 a-desktop avahi-daemon[4678]: New relevant interface eth0.IPv4 for mDNS.
Apr  2 09:12:30 a-desktop avahi-daemon[4678]: Registering new address record for 169.254.6.152 on eth0.IPv4.
Apr  2 09:12:34 a-desktop NetworkManager: <info>  SWITCH: terminating current connection 'eth0' because it's no longer valid. 
Apr  2 09:12:34 a-desktop NetworkManager: <info>  Deactivating device eth0. 
Apr  2 09:12:34 a-desktop NetworkManager: <info>  Activation (eth0): cancelling... 
Apr  2 09:12:34 a-desktop NetworkManager: <info>  Activation (eth0) cancellation handler scheduled... 
Apr  2 09:12:34 a-desktop NetworkManager: <info>  Activation (eth0): waiting for device to cancel activation. 
Apr  2 09:12:34 a-desktop dhclient: There is already a pid file /var/run/dhclient.eth0.pid with pid 5168
Apr  2 09:12:34 a-desktop dhclient: killed old client process, removed PID file
Apr  2 09:12:34 a-desktop dhclient: DHCPRELEASE on eth0 to 192.168.2.1 port 67
Apr  2 09:12:34 a-desktop avahi-autoipd(eth0)[5435]: Got SIGTERM, quitting.
Apr  2 09:12:34 a-desktop avahi-autoipd(eth0)[5435]: Callout STOP, address 169.254.6.152 on interface eth0
Apr  2 09:12:34 a-desktop avahi-daemon[4678]: Withdrawing address record for 169.254.6.152 on eth0.
Apr  2 09:12:34 a-desktop avahi-daemon[4678]: Leaving mDNS multicast group on interface eth0.IPv4 with address 169.254.6.152.
Apr  2 09:12:34 a-desktop avahi-daemon[4678]: Interface eth0.IPv4 no longer relevant for mDNS.
Apr  2 09:12:34 a-desktop avahi-autoipd(eth0)[5436]: client: RTNETLINK answers: No such process
Apr  2 09:12:35 a-desktop NetworkManager: <info>  Activation (eth0): waiting for device to cancel activation. 
Apr  2 09:12:35 a-desktop NetworkManager: <info>  Activation (eth0) cancellation handled. 
Apr  2 09:12:35 a-desktop NetworkManager: <info>  Activation (eth0): cancelled. 
Apr  2 09:12:35 a-desktop avahi-daemon[4678]: Withdrawing address record for fe80::219:21ff:fe5c:be70 on eth0.
Apr  2 09:12:35 a-desktop NetworkManager: nm_device_is_802_3_ethernet: assertion `dev != NULL' failed
Apr  2 09:12:35 a-desktop NetworkManager: nm_device_is_802_11_wireless: assertion `dev != NULL' failed
Apr  2 09:12:38 a-desktop NetworkManager: <info>  Will activate wired connection 'eth0' because it now has a link. 
Apr  2 09:12:38 a-desktop NetworkManager: <info>  SWITCH: no current connection, found better connection 'eth0'. 
Apr  2 09:12:38 a-desktop NetworkManager: <info>  Will activate connection 'eth0'. 
Apr  2 09:12:38 a-desktop NetworkManager: <info>  Device eth0 activation scheduled... 
Apr  2 09:12:38 a-desktop NetworkManager: <info>  Activation (eth0) started... 
Apr  2 09:12:38 a-desktop NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled... 
Apr  2 09:12:38 a-desktop NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) started... 
Apr  2 09:12:38 a-desktop NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) scheduled... 
Apr  2 09:12:38 a-desktop NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) complete. 
Apr  2 09:12:38 a-desktop NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) starting... 
Apr  2 09:12:38 a-desktop NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) successful. 
Apr  2 09:12:38 a-desktop NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled. 
Apr  2 09:12:38 a-desktop NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) complete. 
Apr  2 09:12:38 a-desktop NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) started... 
Apr  2 09:12:39 a-desktop NetworkManager: <info>  Activation (eth0) Beginning DHCP transaction. 
Apr  2 09:12:39 a-desktop dhclient: There is already a pid file /var/run/dhclient.eth0.pid with pid 134519072
Apr  2 09:12:39 a-desktop NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) complete. 
Apr  2 09:12:39 a-desktop NetworkManager: <info>  DHCP daemon state is now 12 (successfully started) for interface eth0 
Apr  2 09:12:40 a-desktop avahi-daemon[4678]: Registering new address record for fe80::219:21ff:fe5c:be70 on eth0.*.
Apr  2 09:12:40 a-desktop NetworkManager: <info>  DHCP daemon state is now 1 (starting) for interface eth0 
Apr  2 09:12:41 a-desktop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
Apr  2 09:12:48 a-desktop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
Apr  2 09:12:59 a-desktop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
Apr  2 09:13:12 a-desktop dhclient: No DHCPOFFERS received.
Apr  2 09:13:12 a-desktop dhclient: Trying recorded lease 192.168.2.3
Apr  2 09:13:12 a-desktop avahi-daemon[4678]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.2.3.
Apr  2 09:13:12 a-desktop avahi-daemon[4678]: New relevant interface eth0.IPv4 for mDNS.
Apr  2 09:13:12 a-desktop avahi-daemon[4678]: Registering new address record for 192.168.2.3 on eth0.IPv4.
Apr  2 09:13:12 a-desktop avahi-autoipd(eth0)[5530]: Found user 'avahi-autoipd' (UID 105) and group 'avahi-autoipd' (GID 113).
Apr  2 09:13:12 a-desktop avahi-autoipd(eth0)[5530]: Successfully called chroot().
Apr  2 09:13:12 a-desktop avahi-autoipd(eth0)[5530]: Successfully dropped root privileges.
Apr  2 09:13:12 a-desktop avahi-autoipd(eth0)[5530]: Starting with address 169.254.6.152
Apr  2 09:13:12 a-desktop avahi-autoipd(eth0)[5530]: Routable address already assigned, sleeping.
Apr  2 09:13:12 a-desktop NetworkManager: <info>  DHCP daemon state is now 8 (timeout) for interface eth0 
Apr  2 09:13:12 a-desktop NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Timeout) scheduled... 
Apr  2 09:13:12 a-desktop NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Timeout) started... 
Apr  2 09:13:12 a-desktop NetworkManager: <info>  No DHCP reply received.  Automatically obtaining IP via Zeroconf. 
Apr  2 09:13:12 a-desktop dhclient: bound: renewal in 13130654 seconds.
Apr  2 09:13:12 a-desktop NetworkManager: <info>  avahi-autoipd running on eth0, assuming IPv4LL address 
Apr  2 09:13:12 a-desktop NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) scheduled... 
Apr  2 09:13:12 a-desktop NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Timeout) complete. 
Apr  2 09:13:12 a-desktop NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) started... 
Apr  2 09:13:12 a-desktop NetworkManager: <info>  not touching eth0 configuration, was configured externally 
Apr  2 09:13:12 a-desktop NetworkManager: <info>  Activation (eth0) successful, device activated. 
Apr  2 09:13:12 a-desktop NetworkManager: <info>  Activation (eth0) Finish handler scheduled. 
Apr  2 09:13:12 a-desktop NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) complete. 
Apr  2 09:13:32 a-desktop ntpdate[5567]: can't find host ntp.ubuntu.com 
Apr  2 09:13:32 a-desktop ntpdate[5567]: no servers can be used, exiting
Apr  2 14:00:36 a-desktop init: tty4 main process (4246) killed by TERM signal
Apr  2 14:00:36 a-desktop init: tty5 main process (4247) killed by TERM signal
Apr  2 14:00:36 a-desktop init: tty2 main process (4251) killed by TERM signal
Apr  2 14:00:36 a-desktop init: tty3 main process (4252) killed by TERM signal
Apr  2 14:00:36 a-desktop init: tty6 main process (4257) killed by TERM signal
Apr  2 14:00:36 a-desktop init: tty1 main process (5173) killed by TERM signal
Apr  2 14:00:37 a-desktop gdm[5018]: GLib-CRITICAL: g_hash_table_lookup_extended: assertion `hash_table != NULL' failed 
Apr  2 14:00:37 a-desktop gdm[5018]: WARNING: Request for invalid configuration key xdmcp/Enable=false 
Apr  2 14:00:37 a-desktop avahi-daemon[4678]: Got SIGTERM, quitting.
Apr  2 14:00:37 a-desktop avahi-daemon[4678]: Leaving mDNS multicast group on interface eth0.IPv4 with address 192.168.2.3.
Apr  2 16:35:00 a-desktop NetworkManager: <info>  starting... 
Apr  2 16:35:00 a-desktop avahi-daemon[4683]: Found user 'avahi' (UID 109) and group 'avahi' (GID 120).
Apr  2 16:35:00 a-desktop avahi-daemon[4683]: Successfully dropped root privileges.
Apr  2 16:35:00 a-desktop avahi-daemon[4683]: avahi-daemon 0.6.22 starting up.
Apr  2 16:35:00 a-desktop avahi-daemon[4683]: Successfully called chroot().
Apr  2 16:35:00 a-desktop avahi-daemon[4683]: Successfully dropped remaining capabilities.
Apr  2 16:35:00 a-desktop avahi-daemon[4683]: No service file found in /etc/avahi/services.
Apr  2 16:35:00 a-desktop avahi-daemon[4683]: Network interface enumeration completed.
Apr  2 16:35:00 a-desktop avahi-daemon[4683]: Registering HINFO record with values 'I686'/'LINUX'.
Apr  2 16:35:00 a-desktop avahi-daemon[4683]: Server startup complete. Host name is a-desktop.local. Local service cookie is 4006938256.
Apr  2 16:35:02 a-desktop NetworkManager: <info>  eth0: Device is fully-supported using driver 'r8169'. 
Apr  2 16:35:02 a-desktop NetworkManager: <info>  nm_device_init(): waiting for device's worker thread to start 
Apr  2 16:35:02 a-desktop NetworkManager: <info>  nm_device_init(): device's worker thread started, continuing. 
Apr  2 16:35:02 a-desktop NetworkManager: <info>  Now managing wired Ethernet (802.3) device 'eth0'. 
Apr  2 16:35:02 a-desktop NetworkManager: <info>  Deactivating device eth0. 
Apr  2 16:35:02 a-desktop NetworkManager: <info>  Will activate wired connection 'eth0' because it now has a link. 
Apr  2 16:35:02 a-desktop NetworkManager: <info>  SWITCH: no current connection, found better connection 'eth0'. 
Apr  2 16:35:02 a-desktop hcid[4963]: Bluetooth HCI daemon
Apr  2 16:35:02 a-desktop hcid[4963]: Starting SDP server
Apr  2 16:35:02 a-desktop hcid[4963]: Created local server at unix:abstract=/var/run/dbus-Bl8Pjp5hE1,guid=04eb76be3d06da687fe433d14bb60096
Apr  2 16:35:02 a-desktop audio[4976]: Bluetooth Audio daemon
Apr  2 16:35:02 a-desktop input[4980]: Bluetooth Input daemon
Apr  2 16:35:02 a-desktop audio[4976]: Unix socket created: 5
Apr  2 16:35:02 a-desktop audio[4976]: audio.conf: Key file does not have key 'Enable'
Apr  2 16:35:02 a-desktop audio[4976]: audio.conf: Key file does not have key 'Disable'
Apr  2 16:35:02 a-desktop input[4980]: Registered input manager path:/org/bluez/input
Apr  2 16:35:02 a-desktop audio[4976]: add_service_record: got record id 0x10000
Apr  2 16:35:02 a-desktop audio[4976]: audio.conf: Key file does not have key 'Disable'
Apr  2 16:35:02 a-desktop audio[4976]: audio.conf: Key file does not have group 'A2DP'
Apr  2 16:35:02 a-desktop last message repeated 3 times
Apr  2 16:35:02 a-desktop audio[4976]: SEP 0x806d090 registered: type:0 codec:0 seid:1
Apr  2 16:35:02 a-desktop audio[4976]: add_service_record: got record id 0x10001
Apr  2 16:35:02 a-desktop audio[4976]: add_service_record: got record id 0x10002
Apr  2 16:35:02 a-desktop audio[4976]: add_service_record: got record id 0x10003
Apr  2 16:35:02 a-desktop audio[4976]: Registered manager path:/org/bluez/audio
Apr  2 16:35:04 a-desktop NetworkManager: <info>  Will activate connection 'eth0'. 
Apr  2 16:35:04 a-desktop NetworkManager: <info>  Device eth0 activation scheduled... 
Apr  2 16:35:04 a-desktop NetworkManager: <debug> [1270218904.204601] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_bluetooth'). 
Apr  2 16:35:04 a-desktop NetworkManager: <info>  Activation (eth0) started... 
Apr  2 16:35:04 a-desktop NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled... 
Apr  2 16:35:04 a-desktop NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) started... 
Apr  2 16:35:04 a-desktop NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) scheduled... 
Apr  2 16:35:04 a-desktop NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) complete. 
Apr  2 16:35:04 a-desktop NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) starting... 
Apr  2 16:35:04 a-desktop NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) successful. 
Apr  2 16:35:04 a-desktop NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled. 
Apr  2 16:35:04 a-desktop NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) complete. 
Apr  2 16:35:04 a-desktop NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) started... 
Apr  2 16:35:05 a-desktop NetworkManager: <info>  Activation (eth0) Beginning DHCP transaction. 
Apr  2 16:35:05 a-desktop NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) complete. 
Apr  2 16:35:05 a-desktop NetworkManager: <info>  DHCP daemon state is now 12 (successfully started) for interface eth0 
Apr  2 16:35:06 a-desktop NetworkManager: <info>  DHCP daemon state is now 1 (starting) for interface eth0 
Apr  2 16:35:06 a-desktop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
Apr  2 16:35:06 a-desktop dhclient: DHCPOFFER of 192.168.2.2 from 192.168.2.1
Apr  2 16:35:06 a-desktop dhclient: DHCPREQUEST of 192.168.2.2 on eth0 to 255.255.255.255 port 67
Apr  2 16:35:06 a-desktop dhclient: DHCPACK of 192.168.2.2 from 192.168.2.1
Apr  2 16:35:06 a-desktop avahi-daemon[4683]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.2.2.
Apr  2 16:35:06 a-desktop avahi-daemon[4683]: New relevant interface eth0.IPv4 for mDNS.
Apr  2 16:35:06 a-desktop avahi-daemon[4683]: Registering new address record for 192.168.2.2 on eth0.IPv4.
Apr  2 16:35:06 a-desktop NetworkManager: <info>  DHCP daemon state is now 2 (bound) for interface eth0 
Apr  2 16:35:06 a-desktop NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Get) scheduled... 
Apr  2 16:35:06 a-desktop NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Get) started... 
Apr  2 16:35:06 a-desktop NetworkManager: <info>  Retrieved the following IP4 configuration from the DHCP daemon: 
Apr  2 16:35:06 a-desktop NetworkManager: <info>    address 192.168.2.2 
Apr  2 16:35:06 a-desktop NetworkManager: <info>    netmask 255.255.255.0 
Apr  2 16:35:06 a-desktop NetworkManager: <info>    broadcast 192.168.2.255 
Apr  2 16:35:06 a-desktop NetworkManager: <info>    gateway 192.168.2.1 
Apr  2 16:35:06 a-desktop NetworkManager: <info>    nameserver 192.168.2.1 
Apr  2 16:35:06 a-desktop NetworkManager: <info>    domain name 'Belkin' 
Apr  2 16:35:06 a-desktop NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) scheduled... 
Apr  2 16:35:06 a-desktop NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Get) complete. 
Apr  2 16:35:06 a-desktop NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) started... 
Apr  2 16:35:06 a-desktop dhclient: bound to 192.168.2.2 -- renewal in 12292880 seconds.
Apr  2 16:35:06 a-desktop avahi-daemon[4683]: Withdrawing address record for 192.168.2.2 on eth0.
Apr  2 16:35:06 a-desktop avahi-daemon[4683]: Leaving mDNS multicast group on interface eth0.IPv4 with address 192.168.2.2.
Apr  2 16:35:06 a-desktop avahi-daemon[4683]: Interface eth0.IPv4 no longer relevant for mDNS.
Apr  2 16:35:06 a-desktop avahi-daemon[4683]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.2.2.
Apr  2 16:35:06 a-desktop avahi-daemon[4683]: New relevant interface eth0.IPv4 for mDNS.
Apr  2 16:35:06 a-desktop avahi-daemon[4683]: Registering new address record for 192.168.2.2 on eth0.IPv4.
Apr  2 16:35:07 a-desktop NetworkManager: <info>  Clearing nscd hosts cache. 
Apr  2 16:35:07 a-desktop NetworkManager: <WARN>  nm_spawn_process(): nm_spawn_process('/usr/sbin/nscd -i hosts'): could not spawn process. (Failed to execute child process "/usr/sbin/nscd" (No such file or directory))  
Apr  2 16:35:07 a-desktop NetworkManager: <info>  Activation (eth0) Finish handler scheduled. 
Apr  2 16:35:07 a-desktop NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) complete. 
Apr  2 16:35:07 a-desktop NetworkManager: <info>  Activation (eth0) successful, device activated. 
Apr  2 16:35:09 a-desktop avahi-daemon[4683]: Registering new address record for fe80::219:21ff:fe5c:be70 on eth0.*.
Apr  2 16:35:13 a-desktop ntpdate[5255]: step time server 91.189.94.4 offset -5.801759 sec
Apr  2 16:35:20 a-desktop hcid[4963]: Default passkey agent (:1.20, /org/bluez/passkey) registered
Apr  2 16:35:20 a-desktop hcid[4963]: Default authorization agent (:1.20, /org/bluez/auth) registered
Apr  2 16:35:28 a-desktop NetworkManager: <info>  Updating allowed wireless network lists. 
Apr  2 16:35:28 a-desktop NetworkManager: <WARN>  nm_dbus_get_networks_cb(): error received: org.freedesktop.NetworkManagerInfo.NoNetworks - There are no wireless networks stored.. 
Apr  2 21:22:11 a-desktop init: tty4 main process (4251) killed by TERM signal
Apr  2 21:22:11 a-desktop init: tty5 main process (4252) killed by TERM signal
Apr  2 21:22:11 a-desktop init: tty2 main process (4256) killed by TERM signal
Apr  2 21:22:11 a-desktop init: tty3 main process (4257) killed by TERM signal
Apr  2 21:22:11 a-desktop init: tty6 main process (4262) killed by TERM signal
Apr  2 21:22:11 a-desktop init: tty1 main process (5177) killed by TERM signal
Apr  2 21:22:13 a-desktop gdm[5023]: GLib-CRITICAL: g_hash_table_lookup_extended: assertion `hash_table != NULL' failed 
Apr  2 21:22:13 a-desktop gdm[5023]: WARNING: Request for invalid configuration key xdmcp/Enable=false 
Apr  2 21:22:13 a-desktop avahi-daemon[4683]: Got SIGTERM, quitting.
Apr  2 21:22:13 a-desktop avahi-daemon[4683]: Leaving mDNS multicast group on interface eth0.IPv4 with address 192.168.2.2.
Apr  3 08:10:33 a-desktop NetworkManager: <info>  starting... 
Apr  3 08:10:33 a-desktop avahi-daemon[4682]: Found user 'avahi' (UID 109) and group 'avahi' (GID 120).
Apr  3 08:10:33 a-desktop avahi-daemon[4682]: Successfully dropped root privileges.
Apr  3 08:10:33 a-desktop avahi-daemon[4682]: avahi-daemon 0.6.22 starting up.
Apr  3 08:10:33 a-desktop avahi-daemon[4682]: Successfully called chroot().
Apr  3 08:10:33 a-desktop avahi-daemon[4682]: Successfully dropped remaining capabilities.
Apr  3 08:10:33 a-desktop avahi-daemon[4682]: No service file found in /etc/avahi/services.
Apr  3 08:10:33 a-desktop avahi-daemon[4682]: Network interface enumeration completed.
Apr  3 08:10:33 a-desktop avahi-daemon[4682]: Registering HINFO record with values 'I686'/'LINUX'.
Apr  3 08:10:33 a-desktop avahi-daemon[4682]: Server startup complete. Host name is a-desktop.local. Local service cookie is 1619217113.
Apr  3 08:10:35 a-desktop NetworkManager: <info>  eth0: Device is fully-supported using driver 'r8169'. 
Apr  3 08:10:35 a-desktop NetworkManager: <info>  nm_device_init(): waiting for device's worker thread to start 
Apr  3 08:10:35 a-desktop NetworkManager: <info>  nm_device_init(): device's worker thread started, continuing. 
Apr  3 08:10:35 a-desktop NetworkManager: <info>  Now managing wired Ethernet (802.3) device 'eth0'. 
Apr  3 08:10:35 a-desktop NetworkManager: <info>  Deactivating device eth0. 
Apr  3 08:10:35 a-desktop NetworkManager: <info>  Will activate wired connection 'eth0' because it now has a link. 
Apr  3 08:10:35 a-desktop NetworkManager: <info>  SWITCH: no current connection, found better connection 'eth0'. 
Apr  3 08:10:35 a-desktop hcid[4962]: Bluetooth HCI daemon
Apr  3 08:10:35 a-desktop hcid[4962]: Starting SDP server
Apr  3 08:10:35 a-desktop hcid[4962]: Created local server at unix:abstract=/var/run/dbus-pMHkaYm3lU,guid=499101042fc740e90525e0b24bb6dbdb
Apr  3 08:10:35 a-desktop audio[4975]: Bluetooth Audio daemon
Apr  3 08:10:35 a-desktop input[4979]: Bluetooth Input daemon
Apr  3 08:10:35 a-desktop audio[4975]: Unix socket created: 5
Apr  3 08:10:35 a-desktop audio[4975]: audio.conf: Key file does not have key 'Enable'
Apr  3 08:10:35 a-desktop audio[4975]: audio.conf: Key file does not have key 'Disable'
Apr  3 08:10:35 a-desktop input[4979]: Registered input manager path:/org/bluez/input
Apr  3 08:10:35 a-desktop audio[4975]: add_service_record: got record id 0x10000
Apr  3 08:10:35 a-desktop audio[4975]: audio.conf: Key file does not have key 'Disable'
Apr  3 08:10:35 a-desktop audio[4975]: audio.conf: Key file does not have group 'A2DP'
Apr  3 08:10:35 a-desktop last message repeated 3 times
Apr  3 08:10:35 a-desktop audio[4975]: SEP 0x806d090 registered: type:0 codec:0 seid:1
Apr  3 08:10:35 a-desktop audio[4975]: add_service_record: got record id 0x10001
Apr  3 08:10:35 a-desktop audio[4975]: add_service_record: got record id 0x10002
Apr  3 08:10:35 a-desktop audio[4975]: add_service_record: got record id 0x10003
Apr  3 08:10:35 a-desktop audio[4975]: Registered manager path:/org/bluez/audio
Apr  3 08:10:37 a-desktop NetworkManager: <info>  Will activate connection 'eth0'. 
Apr  3 08:10:37 a-desktop NetworkManager: <info>  Device eth0 activation scheduled... 
Apr  3 08:10:37 a-desktop NetworkManager: <debug> [1270275037.232514] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_bluetooth'). 
Apr  3 08:10:37 a-desktop NetworkManager: <info>  Activation (eth0) started... 
Apr  3 08:10:37 a-desktop NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled... 
Apr  3 08:10:37 a-desktop NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) started... 
Apr  3 08:10:37 a-desktop NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) scheduled... 
Apr  3 08:10:37 a-desktop NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) complete. 
Apr  3 08:10:37 a-desktop NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) starting... 
Apr  3 08:10:37 a-desktop NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) successful. 
Apr  3 08:10:37 a-desktop NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled. 
Apr  3 08:10:37 a-desktop NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) complete. 
Apr  3 08:10:37 a-desktop NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) started... 
Apr  3 08:10:38 a-desktop NetworkManager: <info>  Activation (eth0) Beginning DHCP transaction. 
Apr  3 08:10:38 a-desktop NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) complete. 
Apr  3 08:10:38 a-desktop NetworkManager: <info>  DHCP daemon state is now 12 (successfully started) for interface eth0 
Apr  3 08:10:39 a-desktop NetworkManager: <info>  DHCP daemon state is now 1 (starting) for interface eth0 
Apr  3 08:10:40 a-desktop dhclient: DHCPREQUEST of 192.168.2.2 on eth0 to 255.255.255.255 port 67
Apr  3 08:10:40 a-desktop dhclient: DHCPNAK from 192.168.2.1
Apr  3 08:10:40 a-desktop avahi-autoipd(eth0)[5203]: Found user 'avahi-autoipd' (UID 105) and group 'avahi-autoipd' (GID 113).
Apr  3 08:10:40 a-desktop avahi-autoipd(eth0)[5203]: Successfully called chroot().
Apr  3 08:10:40 a-desktop avahi-autoipd(eth0)[5203]: Successfully dropped root privileges.
Apr  3 08:10:40 a-desktop avahi-autoipd(eth0)[5203]: Starting with address 169.254.6.152
Apr  3 08:10:45 a-desktop avahi-autoipd(eth0)[5203]: Callout BIND, address 169.254.6.152 on interface eth0
Apr  3 08:10:45 a-desktop avahi-daemon[4682]: Joining mDNS multicast group on interface eth0.IPv4 with address 169.254.6.152.
Apr  3 08:10:45 a-desktop avahi-daemon[4682]: New relevant interface eth0.IPv4 for mDNS.
Apr  3 08:10:45 a-desktop avahi-daemon[4682]: Registering new address record for 169.254.6.152 on eth0.IPv4.
Apr  3 08:10:49 a-desktop avahi-autoipd(eth0)[5203]: Successfully claimed IP address 169.254.6.152
Apr  3 08:10:49 a-desktop NetworkManager: <info>  DHCP daemon state is now 10 (unknown) for interface eth0 
Apr  3 08:10:49 a-desktop avahi-autoipd(eth0)[5203]: Got SIGTERM, quitting.
Apr  3 08:10:49 a-desktop avahi-autoipd(eth0)[5203]: Callout STOP, address 169.254.6.152 on interface eth0
Apr  3 08:10:49 a-desktop avahi-daemon[4682]: Withdrawing address record for 169.254.6.152 on eth0.
Apr  3 08:10:49 a-desktop avahi-daemon[4682]: Leaving mDNS multicast group on interface eth0.IPv4 with address 169.254.6.152.
Apr  3 08:10:49 a-desktop avahi-daemon[4682]: Interface eth0.IPv4 no longer relevant for mDNS.
Apr  3 08:10:49 a-desktop avahi-autoipd(eth0)[5204]: client: RTNETLINK answers: No such process
Apr  3 08:10:50 a-desktop NetworkManager: <info>  DHCP daemon state is now 1 (starting) for interface eth0 
Apr  3 08:10:50 a-desktop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
Apr  3 08:10:52 a-desktop dhclient: DHCPOFFER of 192.168.2.2 from 192.168.2.1
Apr  3 08:10:52 a-desktop dhclient: DHCPREQUEST of 192.168.2.2 on eth0 to 255.255.255.255 port 67
Apr  3 08:10:52 a-desktop dhclient: DHCPACK of 192.168.2.2 from 192.168.2.1
Apr  3 08:10:52 a-desktop avahi-daemon[4682]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.2.2.
Apr  3 08:10:52 a-desktop avahi-daemon[4682]: New relevant interface eth0.IPv4 for mDNS.
Apr  3 08:10:52 a-desktop avahi-daemon[4682]: Registering new address record for 192.168.2.2 on eth0.IPv4.
Apr  3 08:10:53 a-desktop NetworkManager: <info>  DHCP daemon state is now 2 (bound) for interface eth0 
Apr  3 08:10:53 a-desktop NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Get) scheduled... 
Apr  3 08:10:53 a-desktop NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Get) started... 
Apr  3 08:10:53 a-desktop NetworkManager: <info>  Retrieved the following IP4 configuration from the DHCP daemon: 
Apr  3 08:10:53 a-desktop NetworkManager: <info>    address 192.168.2.2 
Apr  3 08:10:53 a-desktop NetworkManager: <info>    netmask 255.255.255.0 
Apr  3 08:10:53 a-desktop NetworkManager: <info>    broadcast 192.168.2.255 
Apr  3 08:10:53 a-desktop NetworkManager: <info>    gateway 192.168.2.1 
Apr  3 08:10:53 a-desktop NetworkManager: <info>    nameserver 192.168.2.1 
Apr  3 08:10:53 a-desktop NetworkManager: <info>    domain name 'Belkin' 
Apr  3 08:10:53 a-desktop NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) scheduled... 
Apr  3 08:10:53 a-desktop NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Get) complete. 
Apr  3 08:10:53 a-desktop NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) started... 
Apr  3 08:10:53 a-desktop dhclient: bound to 192.168.2.2 -- renewal in 13844524 seconds.
Apr  3 08:10:53 a-desktop avahi-daemon[4682]: Withdrawing address record for 192.168.2.2 on eth0.
Apr  3 08:10:53 a-desktop avahi-daemon[4682]: Leaving mDNS multicast group on interface eth0.IPv4 with address 192.168.2.2.
Apr  3 08:10:53 a-desktop avahi-daemon[4682]: Interface eth0.IPv4 no longer relevant for mDNS.
Apr  3 08:10:53 a-desktop avahi-daemon[4682]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.2.2.
Apr  3 08:10:53 a-desktop avahi-daemon[4682]: New relevant interface eth0.IPv4 for mDNS.
Apr  3 08:10:53 a-desktop avahi-daemon[4682]: Registering new address record for 192.168.2.2 on eth0.IPv4.
Apr  3 08:10:54 a-desktop NetworkManager: <info>  Clearing nscd hosts cache. 
Apr  3 08:10:54 a-desktop NetworkManager: <WARN>  nm_spawn_process(): nm_spawn_process('/usr/sbin/nscd -i hosts'): could not spawn process. (Failed to execute child process "/usr/sbin/nscd" (No such file or directory))  
Apr  3 08:10:54 a-desktop NetworkManager: <info>  Activation (eth0) successful, device activated. 
Apr  3 08:10:54 a-desktop NetworkManager: <info>  Activation (eth0) Finish handler scheduled. 
Apr  3 08:10:54 a-desktop NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) complete. 
Apr  3 08:10:54 a-desktop ntpdate[5287]: can't find host ntp.ubuntu.com 
Apr  3 08:10:54 a-desktop ntpdate[5287]: no servers can be used, exiting
Apr  3 08:10:55 a-desktop avahi-daemon[4682]: Registering new address record for fe80::219:21ff:fe5c:be70 on eth0.*.
Apr  3 08:13:32 a-desktop hcid[4962]: Default passkey agent (:1.22, /org/bluez/passkey) registered
Apr  3 08:13:32 a-desktop hcid[4962]: Default authorization agent (:1.22, /org/bluez/auth) registered
Apr  3 08:13:38 a-desktop NetworkManager: <info>  Updating allowed wireless network lists. 
Apr  3 08:13:38 a-desktop NetworkManager: <WARN>  nm_dbus_get_networks_cb(): error received: org.freedesktop.NetworkManagerInfo.NoNetworks - There are no wireless networks stored.. 
Apr  3 08:15:55 a-desktop NetworkManager: <info>  SWITCH: terminating current connection 'eth0' because it's no longer valid. 
Apr  3 08:15:55 a-desktop NetworkManager: <info>  Deactivating device eth0. 
Apr  3 08:15:55 a-desktop dhclient: There is already a pid file /var/run/dhclient.eth0.pid with pid 5179
Apr  3 08:15:55 a-desktop dhclient: killed old client process, removed PID file
Apr  3 08:15:55 a-desktop dhclient: DHCPRELEASE on eth0 to 192.168.2.1 port 67
Apr  3 08:15:55 a-desktop avahi-daemon[4682]: Withdrawing address record for 192.168.2.2 on eth0.
Apr  3 08:15:55 a-desktop avahi-daemon[4682]: Leaving mDNS multicast group on interface eth0.IPv4 with address 192.168.2.2.
Apr  3 08:15:55 a-desktop avahi-daemon[4682]: Interface eth0.IPv4 no longer relevant for mDNS.
Apr  3 08:15:56 a-desktop avahi-daemon[4682]: Withdrawing address record for fe80::219:21ff:fe5c:be70 on eth0.
Apr  3 08:15:56 a-desktop NetworkManager: nm_device_is_802_3_ethernet: assertion `dev != NULL' failed
Apr  3 08:15:56 a-desktop NetworkManager: nm_device_is_802_11_wireless: assertion `dev != NULL' failed
Apr  3 08:16:00 a-desktop NetworkManager: <info>  Will activate wired connection 'eth0' because it now has a link. 
Apr  3 08:16:00 a-desktop NetworkManager: <info>  SWITCH: no current connection, found better connection 'eth0'. 
Apr  3 08:16:00 a-desktop NetworkManager: <info>  Will activate connection 'eth0'. 
Apr  3 08:16:00 a-desktop NetworkManager: <info>  Device eth0 activation scheduled... 
Apr  3 08:16:00 a-desktop NetworkManager: <info>  Activation (eth0) started... 
Apr  3 08:16:00 a-desktop NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled... 
Apr  3 08:16:00 a-desktop NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) started... 
Apr  3 08:16:00 a-desktop NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) scheduled... 
Apr  3 08:16:00 a-desktop NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) complete. 
Apr  3 08:16:00 a-desktop NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) starting... 
Apr  3 08:16:00 a-desktop NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) successful. 
Apr  3 08:16:00 a-desktop NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled. 
Apr  3 08:16:00 a-desktop NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) complete. 
Apr  3 08:16:00 a-desktop NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) started... 
Apr  3 08:16:01 a-desktop NetworkManager: <info>  Activation (eth0) Beginning DHCP transaction. 
Apr  3 08:16:01 a-desktop dhclient: There is already a pid file /var/run/dhclient.eth0.pid with pid 134519072
Apr  3 08:16:01 a-desktop NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) complete. 
Apr  3 08:16:01 a-desktop NetworkManager: <info>  DHCP daemon state is now 12 (successfully started) for interface eth0 
Apr  3 08:16:02 a-desktop avahi-daemon[4682]: Registering new address record for fe80::219:21ff:fe5c:be70 on eth0.*.
Apr  3 08:16:02 a-desktop NetworkManager: <info>  DHCP daemon state is now 1 (starting) for interface eth0 
Apr  3 08:16:06 a-desktop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
Apr  3 08:16:14 a-desktop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
Apr  3 08:16:29 a-desktop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
Apr  3 08:16:29 a-desktop dhclient: DHCPOFFER of 192.168.2.2 from 192.168.2.1
Apr  3 08:16:29 a-desktop dhclient: DHCPREQUEST of 192.168.2.2 on eth0 to 255.255.255.255 port 67
Apr  3 08:16:29 a-desktop dhclient: DHCPACK of 192.168.2.2 from 192.168.2.1
Apr  3 08:16:29 a-desktop avahi-daemon[4682]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.2.2.
Apr  3 08:16:29 a-desktop avahi-daemon[4682]: New relevant interface eth0.IPv4 for mDNS.
Apr  3 08:16:29 a-desktop avahi-daemon[4682]: Registering new address record for 192.168.2.2 on eth0.IPv4.
Apr  3 08:16:29 a-desktop NetworkManager: <info>  DHCP daemon state is now 2 (bound) for interface eth0 
Apr  3 08:16:29 a-desktop NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Get) scheduled... 
Apr  3 08:16:29 a-desktop NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Get) started... 
Apr  3 08:16:29 a-desktop NetworkManager: <info>  Retrieved the following IP4 configuration from the DHCP daemon: 
Apr  3 08:16:29 a-desktop NetworkManager: <info>    address 192.168.2.2 
Apr  3 08:16:29 a-desktop NetworkManager: <info>    netmask 255.255.255.0 
Apr  3 08:16:29 a-desktop NetworkManager: <info>    broadcast 192.168.2.255 
Apr  3 08:16:29 a-desktop NetworkManager: <info>    gateway 192.168.2.1 
Apr  3 08:16:29 a-desktop NetworkManager: <info>    nameserver 192.168.2.1 
Apr  3 08:16:29 a-desktop NetworkManager: <info>    domain name 'Belkin' 
Apr  3 08:16:29 a-desktop NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) scheduled... 
Apr  3 08:16:29 a-desktop NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Get) complete. 
Apr  3 08:16:29 a-desktop NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) started... 
Apr  3 08:16:29 a-desktop dhclient: bound to 192.168.2.2 -- renewal in 12797403 seconds.
Apr  3 08:16:29 a-desktop avahi-daemon[4682]: Withdrawing address record for 192.168.2.2 on eth0.
Apr  3 08:16:29 a-desktop avahi-daemon[4682]: Leaving mDNS multicast group on interface eth0.IPv4 with address 192.168.2.2.
Apr  3 08:16:29 a-desktop avahi-daemon[4682]: Interface eth0.IPv4 no longer relevant for mDNS.
Apr  3 08:16:29 a-desktop avahi-daemon[4682]: Withdrawing address record for fe80::219:21ff:fe5c:be70 on eth0.
Apr  3 08:16:29 a-desktop avahi-daemon[4682]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.2.2.
Apr  3 08:16:29 a-desktop avahi-daemon[4682]: New relevant interface eth0.IPv4 for mDNS.
Apr  3 08:16:29 a-desktop avahi-daemon[4682]: Registering new address record for 192.168.2.2 on eth0.IPv4.
Apr  3 08:16:30 a-desktop NetworkManager: <info>  Clearing nscd hosts cache. 
Apr  3 08:16:30 a-desktop NetworkManager: <WARN>  nm_spawn_process(): nm_spawn_process('/usr/sbin/nscd -i hosts'): could not spawn process. (Failed to execute child process "/usr/sbin/nscd" (No such file or directory))  
Apr  3 08:16:30 a-desktop NetworkManager: <info>  Activation (eth0) successful, device activated. 
Apr  3 08:16:30 a-desktop NetworkManager: <info>  Activation (eth0) Finish handler scheduled. 
Apr  3 08:16:30 a-desktop NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) complete. 
Apr  3 08:16:30 a-desktop ntpdate[5689]: can't find host ntp.ubuntu.com 
Apr  3 08:16:30 a-desktop ntpdate[5689]: no servers can be used, exiting
Apr  3 08:16:31 a-desktop avahi-daemon[4682]: Registering new address record for fe80::219:21ff:fe5c:be70 on eth0.*.
Apr  3 09:14:44 a-desktop NetworkManager: <info>  SWITCH: terminating current connection 'eth0' because it's no longer valid. 
Apr  3 09:14:44 a-desktop NetworkManager: <info>  Deactivating device eth0. 
Apr  3 09:14:44 a-desktop dhclient: There is already a pid file /var/run/dhclient.eth0.pid with pid 5621
Apr  3 09:14:44 a-desktop dhclient: killed old client process, removed PID file
Apr  3 09:14:44 a-desktop dhclient: DHCPRELEASE on eth0 to 192.168.2.1 port 67
Apr  3 09:14:44 a-desktop avahi-daemon[4682]: Withdrawing address record for 192.168.2.2 on eth0.
Apr  3 09:14:44 a-desktop avahi-daemon[4682]: Leaving mDNS multicast group on interface eth0.IPv4 with address 192.168.2.2.
Apr  3 09:14:44 a-desktop avahi-daemon[4682]: Interface eth0.IPv4 no longer relevant for mDNS.
Apr  3 09:14:45 a-desktop avahi-daemon[4682]: Withdrawing address record for fe80::219:21ff:fe5c:be70 on eth0.
Apr  3 09:14:45 a-desktop NetworkManager: nm_device_is_802_3_ethernet: assertion `dev != NULL' failed
Apr  3 09:14:45 a-desktop NetworkManager: nm_device_is_802_11_wireless: assertion `dev != NULL' failed
Apr  3 09:14:46 a-desktop NetworkManager: <info>  Will activate wired connection 'eth0' because it now has a link. 
Apr  3 09:14:46 a-desktop NetworkManager: <info>  SWITCH: no current connection, found better connection 'eth0'. 
Apr  3 09:14:46 a-desktop NetworkManager: <info>  Will activate connection 'eth0'. 
Apr  3 09:14:46 a-desktop NetworkManager: <info>  Device eth0 activation scheduled... 
Apr  3 09:14:46 a-desktop NetworkManager: <info>  Activation (eth0) started... 
Apr  3 09:14:46 a-desktop NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled... 
Apr  3 09:14:46 a-desktop NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) started... 
Apr  3 09:14:46 a-desktop NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) scheduled... 
Apr  3 09:14:46 a-desktop NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) complete. 
Apr  3 09:14:46 a-desktop NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) starting... 
Apr  3 09:14:46 a-desktop NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) successful. 
Apr  3 09:14:46 a-desktop NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled. 
Apr  3 09:14:46 a-desktop NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) complete. 
Apr  3 09:14:46 a-desktop NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) started... 
Apr  3 09:14:47 a-desktop NetworkManager: <info>  Activation (eth0) Beginning DHCP transaction. 
Apr  3 09:14:47 a-desktop dhclient: There is already a pid file /var/run/dhclient.eth0.pid with pid 134519072
Apr  3 09:14:47 a-desktop NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) complete. 
Apr  3 09:14:47 a-desktop NetworkManager: <info>  DHCP daemon state is now 12 (successfully started) for interface eth0 
Apr  3 09:14:47 a-desktop avahi-daemon[4682]: Registering new address record for fe80::219:21ff:fe5c:be70 on eth0.*.
Apr  3 09:14:48 a-desktop NetworkManager: <info>  DHCP daemon state is now 1 (starting) for interface eth0 
Apr  3 09:14:48 a-desktop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
Apr  3 09:14:48 a-desktop dhclient: DHCPOFFER of 192.168.2.2 from 192.168.2.1
Apr  3 09:14:48 a-desktop dhclient: DHCPREQUEST of 192.168.2.2 on eth0 to 255.255.255.255 port 67
Apr  3 09:14:48 a-desktop dhclient: DHCPACK of 192.168.2.2 from 192.168.2.1
Apr  3 09:14:48 a-desktop avahi-daemon[4682]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.2.2.
Apr  3 09:14:48 a-desktop avahi-daemon[4682]: New relevant interface eth0.IPv4 for mDNS.
Apr  3 09:14:48 a-desktop avahi-daemon[4682]: Registering new address record for 192.168.2.2 on eth0.IPv4.
Apr  3 09:14:48 a-desktop NetworkManager: <info>  DHCP daemon state is now 2 (bound) for interface eth0 
Apr  3 09:14:48 a-desktop NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Get) scheduled... 
Apr  3 09:14:48 a-desktop NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Get) started... 
Apr  3 09:14:48 a-desktop NetworkManager: <info>  Retrieved the following IP4 configuration from the DHCP daemon: 
Apr  3 09:14:48 a-desktop NetworkManager: <info>    address 192.168.2.2 
Apr  3 09:14:48 a-desktop NetworkManager: <info>    netmask 255.255.255.0 
Apr  3 09:14:48 a-desktop NetworkManager: <info>    broadcast 192.168.2.255 
Apr  3 09:14:48 a-desktop NetworkManager: <info>    gateway 192.168.2.1 
Apr  3 09:14:48 a-desktop NetworkManager: <info>    nameserver 192.168.2.1 
Apr  3 09:14:48 a-desktop NetworkManager: <info>    domain name 'Belkin' 
Apr  3 09:14:48 a-desktop NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) scheduled... 
Apr  3 09:14:48 a-desktop NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Get) complete. 
Apr  3 09:14:48 a-desktop NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) started... 
Apr  3 09:14:48 a-desktop dhclient: bound to 192.168.2.2 -- renewal in 14750328 seconds.
Apr  3 09:14:48 a-desktop avahi-daemon[4682]: Withdrawing address record for 192.168.2.2 on eth0.
Apr  3 09:14:48 a-desktop avahi-daemon[4682]: Leaving mDNS multicast group on interface eth0.IPv4 with address 192.168.2.2.
Apr  3 09:14:48 a-desktop avahi-daemon[4682]: Interface eth0.IPv4 no longer relevant for mDNS.
Apr  3 09:14:48 a-desktop avahi-daemon[4682]: Withdrawing address record for fe80::219:21ff:fe5c:be70 on eth0.
Apr  3 09:14:48 a-desktop avahi-daemon[4682]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.2.2.
Apr  3 09:14:48 a-desktop avahi-daemon[4682]: New relevant interface eth0.IPv4 for mDNS.
Apr  3 09:14:48 a-desktop avahi-daemon[4682]: Registering new address record for 192.168.2.2 on eth0.IPv4.
Apr  3 09:14:49 a-desktop NetworkManager: <info>  Clearing nscd hosts cache. 
Apr  3 09:14:49 a-desktop NetworkManager: <WARN>  nm_spawn_process(): nm_spawn_process('/usr/sbin/nscd -i hosts'): could not spawn process. (Failed to execute child process "/usr/sbin/nscd" (No such file or directory))  
Apr  3 09:14:49 a-desktop NetworkManager: <info>  Activation (eth0) successful, device activated. 
Apr  3 09:14:49 a-desktop NetworkManager: <info>  Activation (eth0) Finish handler scheduled. 
Apr  3 09:14:49 a-desktop NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) complete. 
Apr  3 09:14:49 a-desktop ntpdate[5974]: can't find host ntp.ubuntu.com 
Apr  3 09:14:49 a-desktop ntpdate[5974]: no servers can be used, exiting
Apr  3 09:14:51 a-desktop avahi-daemon[4682]: Registering new address record for fe80::219:21ff:fe5c:be70 on eth0.*.
Apr  3 21:39:45 a-desktop init: tty4 main process (4250) killed by TERM signal
Apr  3 21:39:45 a-desktop init: tty5 main process (4251) killed by TERM signal
Apr  3 21:39:45 a-desktop init: tty2 main process (4255) killed by TERM signal
Apr  3 21:39:45 a-desktop init: tty3 main process (4256) killed by TERM signal
Apr  3 21:39:45 a-desktop init: tty6 main process (4258) killed by TERM signal
Apr  3 21:39:45 a-desktop init: tty1 main process (5176) killed by TERM signal
Apr  3 21:39:47 a-desktop gdm[5022]: GLib-CRITICAL: g_hash_table_lookup_extended: assertion `hash_table != NULL' failed 
Apr  3 21:39:47 a-desktop gdm[5022]: WARNING: Request for invalid configuration key xdmcp/Enable=false 
Apr  3 21:39:47 a-desktop avahi-daemon[4682]: Got SIGTERM, quitting.
Apr  3 21:39:47 a-desktop avahi-daemon[4682]: Leaving mDNS multicast group on interface eth0.IPv4 with address 192.168.2.2.
Apr  4 06:23:23 a-desktop NetworkManager: <info>  starting... 
Apr  4 06:23:23 a-desktop avahi-daemon[4681]: Found user 'avahi' (UID 109) and group 'avahi' (GID 120).
Apr  4 06:23:23 a-desktop avahi-daemon[4681]: Successfully dropped root privileges.
Apr  4 06:23:23 a-desktop avahi-daemon[4681]: avahi-daemon 0.6.22 starting up.
Apr  4 06:23:23 a-desktop avahi-daemon[4681]: Successfully called chroot().
Apr  4 06:23:23 a-desktop avahi-daemon[4681]: Successfully dropped remaining capabilities.
Apr  4 06:23:23 a-desktop avahi-daemon[4681]: No service file found in /etc/avahi/services.
Apr  4 06:23:23 a-desktop avahi-daemon[4681]: Network interface enumeration completed.
Apr  4 06:23:23 a-desktop avahi-daemon[4681]: Registering HINFO record with values 'I686'/'LINUX'.
Apr  4 06:23:23 a-desktop avahi-daemon[4681]: Server startup complete. Host name is a-desktop.local. Local service cookie is 2563387066.
Apr  4 06:23:25 a-desktop NetworkManager: <info>  eth0: Device is fully-supported using driver 'r8169'. 
Apr  4 06:23:25 a-desktop NetworkManager: <info>  nm_device_init(): waiting for device's worker thread to start 
Apr  4 06:23:25 a-desktop NetworkManager: <info>  nm_device_init(): device's worker thread started, continuing. 
Apr  4 06:23:25 a-desktop NetworkManager: <info>  Now managing wired Ethernet (802.3) device 'eth0'. 
Apr  4 06:23:25 a-desktop NetworkManager: <info>  Deactivating device eth0. 
Apr  4 06:23:25 a-desktop NetworkManager: <info>  Will activate wired connection 'eth0' because it now has a link. 
Apr  4 06:23:25 a-desktop NetworkManager: <info>  SWITCH: no current connection, found better connection 'eth0'. 
Apr  4 06:23:25 a-desktop hcid[4961]: Bluetooth HCI daemon
Apr  4 06:23:25 a-desktop hcid[4961]: Starting SDP server
Apr  4 06:23:25 a-desktop hcid[4961]: Created local server at unix:abstract=/var/run/dbus-MAjPFcswfW,guid=ed54c8b3326cceaf5e17de0a4bb8143d
Apr  4 06:23:25 a-desktop audio[4974]: Bluetooth Audio daemon
Apr  4 06:23:25 a-desktop input[4978]: Bluetooth Input daemon
Apr  4 06:23:25 a-desktop audio[4974]: Unix socket created: 5
Apr  4 06:23:25 a-desktop audio[4974]: audio.conf: Key file does not have key 'Enable'
Apr  4 06:23:25 a-desktop audio[4974]: audio.conf: Key file does not have key 'Disable'
Apr  4 06:23:25 a-desktop input[4978]: Registered input manager path:/org/bluez/input
Apr  4 06:23:25 a-desktop audio[4974]: add_service_record: got record id 0x10000
Apr  4 06:23:25 a-desktop audio[4974]: audio.conf: Key file does not have key 'Disable'
Apr  4 06:23:25 a-desktop audio[4974]: audio.conf: Key file does not have group 'A2DP'
Apr  4 06:23:25 a-desktop last message repeated 3 times
Apr  4 06:23:25 a-desktop audio[4974]: SEP 0x806d090 registered: type:0 codec:0 seid:1
Apr  4 06:23:25 a-desktop audio[4974]: add_service_record: got record id 0x10001
Apr  4 06:23:25 a-desktop audio[4974]: add_service_record: got record id 0x10002
Apr  4 06:23:25 a-desktop audio[4974]: add_service_record: got record id 0x10003
Apr  4 06:23:25 a-desktop audio[4974]: Registered manager path:/org/bluez/audio
Apr  4 06:23:27 a-desktop NetworkManager: <info>  Will activate connection 'eth0'. 
Apr  4 06:23:27 a-desktop NetworkManager: <info>  Device eth0 activation scheduled... 
Apr  4 06:23:27 a-desktop NetworkManager: <debug> [1270355007.245694] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_bluetooth'). 
Apr  4 06:23:27 a-desktop NetworkManager: <info>  Activation (eth0) started... 
Apr  4 06:23:27 a-desktop NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled... 
Apr  4 06:23:27 a-desktop NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) started... 
Apr  4 06:23:27 a-desktop NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) scheduled... 
Apr  4 06:23:27 a-desktop NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) complete. 
Apr  4 06:23:27 a-desktop NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) starting... 
Apr  4 06:23:27 a-desktop NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) successful. 
Apr  4 06:23:27 a-desktop NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled. 
Apr  4 06:23:27 a-desktop NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) complete. 
Apr  4 06:23:27 a-desktop NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) started... 
Apr  4 06:23:28 a-desktop NetworkManager: <info>  Activation (eth0) Beginning DHCP transaction. 
Apr  4 06:23:28 a-desktop NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) complete. 
Apr  4 06:23:28 a-desktop NetworkManager: <info>  DHCP daemon state is now 12 (successfully started) for interface eth0 
Apr  4 06:23:29 a-desktop NetworkManager: <info>  DHCP daemon state is now 1 (starting) for interface eth0 
Apr  4 06:23:29 a-desktop dhclient: DHCPREQUEST of 192.168.2.2 on eth0 to 255.255.255.255 port 67
Apr  4 06:23:29 a-desktop dhclient: DHCPNAK from 192.168.2.1
Apr  4 06:23:29 a-desktop avahi-autoipd(eth0)[5202]: Found user 'avahi-autoipd' (UID 105) and group 'avahi-autoipd' (GID 113).
Apr  4 06:23:29 a-desktop avahi-autoipd(eth0)[5202]: Successfully called chroot().
Apr  4 06:23:29 a-desktop avahi-autoipd(eth0)[5202]: Successfully dropped root privileges.
Apr  4 06:23:29 a-desktop avahi-autoipd(eth0)[5202]: Starting with address 169.254.6.152
Apr  4 06:23:34 a-desktop avahi-autoipd(eth0)[5202]: Callout BIND, address 169.254.6.152 on interface eth0
Apr  4 06:23:34 a-desktop avahi-daemon[4681]: Joining mDNS multicast group on interface eth0.IPv4 with address 169.254.6.152.
Apr  4 06:23:34 a-desktop avahi-daemon[4681]: New relevant interface eth0.IPv4 for mDNS.
Apr  4 06:23:34 a-desktop avahi-daemon[4681]: Registering new address record for 169.254.6.152 on eth0.IPv4.
Apr  4 06:23:38 a-desktop avahi-autoipd(eth0)[5202]: Successfully claimed IP address 169.254.6.152
Apr  4 06:23:38 a-desktop NetworkManager: <info>  DHCP daemon state is now 10 (unknown) for interface eth0 
Apr  4 06:23:38 a-desktop avahi-autoipd(eth0)[5202]: Got SIGTERM, quitting.
Apr  4 06:23:38 a-desktop avahi-autoipd(eth0)[5202]: Callout STOP, address 169.254.6.152 on interface eth0
Apr  4 06:23:38 a-desktop avahi-daemon[4681]: Withdrawing address record for 169.254.6.152 on eth0.
Apr  4 06:23:38 a-desktop avahi-daemon[4681]: Leaving mDNS multicast group on interface eth0.IPv4 with address 169.254.6.152.
Apr  4 06:23:38 a-desktop avahi-daemon[4681]: Interface eth0.IPv4 no longer relevant for mDNS.
Apr  4 06:23:38 a-desktop avahi-autoipd(eth0)[5203]: client: RTNETLINK answers: No such process
Apr  4 06:23:39 a-desktop NetworkManager: <info>  DHCP daemon state is now 1 (starting) for interface eth0 
Apr  4 06:23:39 a-desktop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
Apr  4 06:23:41 a-desktop dhclient: DHCPOFFER of 192.168.2.2 from 192.168.2.1
Apr  4 06:23:41 a-desktop dhclient: DHCPREQUEST of 192.168.2.2 on eth0 to 255.255.255.255 port 67
Apr  4 06:23:41 a-desktop dhclient: DHCPACK of 192.168.2.2 from 192.168.2.1
Apr  4 06:23:41 a-desktop avahi-daemon[4681]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.2.2.
Apr  4 06:23:41 a-desktop avahi-daemon[4681]: New relevant interface eth0.IPv4 for mDNS.
Apr  4 06:23:41 a-desktop avahi-daemon[4681]: Registering new address record for 192.168.2.2 on eth0.IPv4.
Apr  4 06:23:41 a-desktop NetworkManager: <info>  DHCP daemon state is now 2 (bound) for interface eth0 
Apr  4 06:23:41 a-desktop NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Get) scheduled... 
Apr  4 06:23:41 a-desktop NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Get) started... 
Apr  4 06:23:41 a-desktop NetworkManager: <info>  Retrieved the following IP4 configuration from the DHCP daemon: 
Apr  4 06:23:41 a-desktop NetworkManager: <info>    address 192.168.2.2 
Apr  4 06:23:41 a-desktop NetworkManager: <info>    netmask 255.255.255.0 
Apr  4 06:23:41 a-desktop NetworkManager: <info>    broadcast 192.168.2.255 
Apr  4 06:23:41 a-desktop NetworkManager: <info>    gateway 192.168.2.1 
Apr  4 06:23:41 a-desktop NetworkManager: <info>    nameserver 192.168.2.1 
Apr  4 06:23:41 a-desktop NetworkManager: <info>    domain name 'Belkin' 
Apr  4 06:23:41 a-desktop NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) scheduled... 
Apr  4 06:23:41 a-desktop NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Get) complete. 
Apr  4 06:23:41 a-desktop NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) started... 
Apr  4 06:23:41 a-desktop dhclient: bound to 192.168.2.2 -- renewal in 13368992 seconds.
Apr  4 06:23:41 a-desktop avahi-daemon[4681]: Withdrawing address record for 192.168.2.2 on eth0.
Apr  4 06:23:41 a-desktop avahi-daemon[4681]: Leaving mDNS multicast group on interface eth0.IPv4 with address 192.168.2.2.
Apr  4 06:23:41 a-desktop avahi-daemon[4681]: Interface eth0.IPv4 no longer relevant for mDNS.
Apr  4 06:23:41 a-desktop avahi-daemon[4681]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.2.2.
Apr  4 06:23:41 a-desktop avahi-daemon[4681]: New relevant interface eth0.IPv4 for mDNS.
Apr  4 06:23:41 a-desktop avahi-daemon[4681]: Registering new address record for 192.168.2.2 on eth0.IPv4.
Apr  4 06:23:42 a-desktop NetworkManager: <info>  Clearing nscd hosts cache. 
Apr  4 06:23:42 a-desktop NetworkManager: <WARN>  nm_spawn_process(): nm_spawn_process('/usr/sbin/nscd -i hosts'): could not spawn process. (Failed to execute child process "/usr/sbin/nscd" (No such file or directory))  
Apr  4 06:23:42 a-desktop NetworkManager: <info>  Activation (eth0) successful, device activated. 
Apr  4 06:23:42 a-desktop NetworkManager: <info>  Activation (eth0) Finish handler scheduled. 
Apr  4 06:23:42 a-desktop NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) complete. 
Apr  4 06:23:43 a-desktop ntpdate[5286]: can't find host ntp.ubuntu.com 
Apr  4 06:23:43 a-desktop ntpdate[5286]: no servers can be used, exiting
Apr  4 06:23:44 a-desktop avahi-daemon[4681]: Registering new address record for fe80::219:21ff:fe5c:be70 on eth0.*.
Apr  4 06:29:37 a-desktop hcid[4961]: Default passkey agent (:1.22, /org/bluez/passkey) registered
Apr  4 06:29:37 a-desktop hcid[4961]: Default authorization agent (:1.22, /org/bluez/auth) registered
Apr  4 06:29:42 a-desktop NetworkManager: <info>  Updating allowed wireless network lists. 
Apr  4 06:29:42 a-desktop NetworkManager: <WARN>  nm_dbus_get_networks_cb(): error received: org.freedesktop.NetworkManagerInfo.NoNetworks - There are no wireless networks stored.. 
Apr  4 11:23:26 a-desktop NetworkManager: <debug> [1270373006.511187] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_1307_163_4880f8f659222b'). 
Apr  4 11:23:26 a-desktop NetworkManager: <debug> [1270373006.687168] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_1307_163_4880f8f659222b_if0'). 
Apr  4 11:23:31 a-desktop NetworkManager: <debug> [1270373011.898892] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_1307_163_4880f8f659222b_if0_scsi_host'). 
Apr  4 11:23:31 a-desktop NetworkManager: <debug> [1270373011.905519] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_1307_163_4880f8f659222b_if0_scsi_host_scsi_device_lun0'). 
Apr  4 11:23:31 a-desktop NetworkManager: <debug> [1270373011.988199] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_1307_163_4880f8f659222b_if0_scsi_host_scsi_device_lun0_scsi_generic'). 
Apr  4 11:23:32 a-desktop NetworkManager: <debug> [1270373012.307257] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_serial_USB_2_0_Flash_Disk_4880f8f659222b_0_0'). 
Apr  4 11:23:32 a-desktop NetworkManager: <debug> [1270373012.436080] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_DCD0_2EFB'). 
Apr  4 11:23:33 a-desktop hald: mounted /dev/sdb1 on behalf of uid 1000
Apr  4 11:27:53 a-desktop NetworkManager: <debug> [1270373273.159019] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_1307_163_4880f8f659222b_if0_scsi_host_scsi_device_lun0_scsi_generic'). 
Apr  4 11:27:53 a-desktop hald[4813]: forcibly attempting to lazy unmount /dev/sdb1 as enclosing drive was disconnected
Apr  4 11:27:53 a-desktop hald: unmounted /dev/sdb1 from '/media/disk' on behalf of uid 0
Apr  4 11:27:53 a-desktop NetworkManager: <debug> [1270373273.353221] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_DCD0_2EFB'). 
Apr  4 11:27:53 a-desktop NetworkManager: <debug> [1270373273.359189] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/storage_serial_USB_2_0_Flash_Disk_4880f8f659222b_0_0'). 
Apr  4 11:27:53 a-desktop NetworkManager: <debug> [1270373273.362990] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_1307_163_4880f8f659222b_if0_scsi_host_scsi_device_lun0'). 
Apr  4 11:27:53 a-desktop NetworkManager: <debug> [1270373273.366606] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_1307_163_4880f8f659222b_if0_scsi_host'). 
Apr  4 11:27:53 a-desktop NetworkManager: <debug> [1270373273.370473] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_1307_163_4880f8f659222b_if0'). 
Apr  4 11:27:53 a-desktop NetworkManager: <debug> [1270373273.374356] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_1307_163_4880f8f659222b'). 

Thanks and pl have patience with me

---

