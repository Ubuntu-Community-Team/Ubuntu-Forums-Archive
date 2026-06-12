---
title: "Connection failed with Huawei E3531 on Ubuntu 14.04"
date: 2014-06-20
forum: Networking &amp; Wireless
---

### Post by varlesh-l on 2014-06-20
A connection is defined and a modem in the system, but an error while connecting: "Connection deactivated".
Please hlp!

lsusb:
Bus 003 Device 005: ID 12d1:1506 Huawei Technologies Co., Ltd. E398 LTE/UMTS/GSM Modem/Networkcard
dmesg:
[ 1437.211610] usb 3-2: new high-speed USB device number 11 using xhci_hcd
[ 1437.228863] usb 3-2: New USB device found, idVendor=12d1, idProduct=1506
[ 1437.228875] usb 3-2: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[ 1437.228881] usb 3-2: Product: Mobile Connect
[ 1437.228886] usb 3-2: Manufacturer: ......
[ 1437.530354] option 3-2:1.0: GSM modem (1-port) converter detected
[ 1437.530662] usb 3-2: GSM modem (1-port) converter now attached to ttyUSB3
[ 1437.570434] huawei_cdc_ncm 3-2:1.1: MAC-Address: 32:14:94:92:ff:b5
[ 1437.570709] huawei_cdc_ncm 3-2:1.1: cdc-wdm1: USB WDM device
[ 1437.571170] huawei_cdc_ncm 3-2:1.1 wwan0: register 'huawei_cdc_ncm' at usb-0000:00:14.0-2, Huawei CDC NCM device, 32:14:94:92:ff:b5
[ 1437.571877] option 3-2:1.2: GSM modem (1-port) converter detected
[ 1437.572197] usb 3-2: GSM modem (1-port) converter now attached to ttyUSB4
[ 1437.572377] option 3-2:1.3: GSM modem (1-port) converter detected
[ 1437.572559] usb 3-2: GSM modem (1-port) converter now attached to ttyUSB5
[ 1437.572816] usb-storage 3-2:1.4: USB Mass Storage device detected
[ 1437.573025] scsi18 : usb-storage 3-2:1.4
[ 1437.573245] usb-storage 3-2:1.5: USB Mass Storage device detected
[ 1437.573385] scsi19 : usb-storage 3-2:1.5
[ 1438.584204] scsi 18:0:0:0: CD-ROM                     Mass Storage     2.31 PQ: 0 ANSI: 2
[ 1438.585152] scsi 19:0:0:0: Direct-Access              TF CARD Storage  2.31 PQ: 0 ANSI: 2
[ 1438.585308] sr1: scsi-1 drive
[ 1438.585454] sr 18:0:0:0: Attached scsi CD-ROM sr1
[ 1438.585571] sr 18:0:0:0: Attached scsi generic sg3 type 5
[ 1438.585859] sd 19:0:0:0: Attached scsi generic sg4 type 0
[ 1438.586796] sd 19:0:0:0: [sdc] Attached SCSI removable disk

syslog:
Jun 20 13:04:31 user44 kernel: [  350.960470] usb 3-4: new high-speed USB device number 4 using xhci_hcd
Jun 20 13:04:31 user44 kernel: [  350.977539] usb 3-4: New USB device found, idVendor=12d1, idProduct=15e7
Jun 20 13:04:31 user44 kernel: [  350.977549] usb 3-4: New USB device strings: Mfr=1, Product=2, SerialNumber=3
Jun 20 13:04:31 user44 kernel: [  350.977555] usb 3-4: Product: Mobile Connect
Jun 20 13:04:31 user44 kernel: [  350.977559] usb 3-4: Manufacturer: ......
Jun 20 13:04:31 user44 kernel: [  350.977564] usb 3-4: SerialNumber: FFFFFFFFFFFFFFFF
Jun 20 13:04:31 user44 kernel: [  351.027424] usb-storage 3-4:1.0: USB Mass Storage device detected
Jun 20 13:04:31 user44 kernel: [  351.027594] scsi8 : usb-storage 3-4:1.0
Jun 20 13:04:31 user44 mtp-probe: checking bus 3, device 4: "/sys/devices/pci0000:00/0000:00:14.0/usb3/3-4"
Jun 20 13:04:31 user44 mtp-probe: bus: 3, device: 4 was not an MTP device
Jun 20 13:04:32 user44 usb_modeswitch: switch device 12d1:15e7 on 003/004
Jun 20 13:04:32 user44 kernel: [  351.710654] usb 3-4: USB disconnect, device number 4
Jun 20 13:04:33 user44 kernel: [  352.560066] usb 3-4: new high-speed USB device number 5 using xhci_hcd
Jun 20 13:04:33 user44 kernel: [  352.577388] usb 3-4: New USB device found, idVendor=12d1, idProduct=1506
Jun 20 13:04:33 user44 kernel: [  352.577400] usb 3-4: New USB device strings: Mfr=1, Product=2, SerialNumber=0
Jun 20 13:04:33 user44 kernel: [  352.577407] usb 3-4: Product: Mobile Connect
Jun 20 13:04:33 user44 kernel: [  352.577412] usb 3-4: Manufacturer: ......
Jun 20 13:04:33 user44 kernel: [  352.885798] usb-storage 3-4:1.4: USB Mass Storage device detected
Jun 20 13:04:33 user44 kernel: [  352.885980] scsi9 : usb-storage 3-4:1.4
Jun 20 13:04:33 user44 kernel: [  352.886131] usb-storage 3-4:1.5: USB Mass Storage device detected
Jun 20 13:04:33 user44 kernel: [  352.886251] scsi10 : usb-storage 3-4:1.5
Jun 20 13:04:33 user44 mtp-probe: checking bus 3, device 5: "/sys/devices/pci0000:00/0000:00:14.0/usb3/3-4"
Jun 20 13:04:33 user44 mtp-probe: bus: 3, device: 5 was not an MTP device
Jun 20 13:04:33 user44 kernel: [  353.021595] usbcore: registered new interface driver usbserial
Jun 20 13:04:33 user44 kernel: [  353.021620] usbcore: registered new interface driver usbserial_generic
Jun 20 13:04:33 user44 kernel: [  353.021636] usbserial: USB Serial support registered for generic
Jun 20 13:04:33 user44 kernel: [  353.039139] usbcore: registered new interface driver cdc_ncm
Jun 20 13:04:33 user44 kernel: [  353.047829] usbcore: registered new interface driver cdc_wdm
Jun 20 13:04:33 user44 kernel: [  353.062351] usbcore: registered new interface driver option
Jun 20 13:04:33 user44 kernel: [  353.062366] usbserial: USB Serial support registered for GSM modem (1-port)
Jun 20 13:04:33 user44 kernel: [  353.062501] option 3-4:1.0: GSM modem (1-port) converter detected
Jun 20 13:04:33 user44 kernel: [  353.063352] usb 3-4: GSM modem (1-port) converter now attached to ttyUSB0
Jun 20 13:04:33 user44 kernel: [  353.063406] option 3-4:1.2: GSM modem (1-port) converter detected
Jun 20 13:04:33 user44 kernel: [  353.063791] usb 3-4: GSM modem (1-port) converter now attached to ttyUSB1
Jun 20 13:04:33 user44 kernel: [  353.063830] option 3-4:1.3: GSM modem (1-port) converter detected
Jun 20 13:04:33 user44 kernel: [  353.063935] usb 3-4: GSM modem (1-port) converter now attached to ttyUSB2
Jun 20 13:04:33 user44 kernel: [  353.111577] huawei_cdc_ncm 3-4:1.1: MAC-Address: 32:14:94:92:ff:b5
Jun 20 13:04:33 user44 kernel: [  353.111884] huawei_cdc_ncm 3-4:1.1: cdc-wdm1: USB WDM device
Jun 20 13:04:33 user44 kernel: [  353.112231] huawei_cdc_ncm 3-4:1.1 wwan0: register 'huawei_cdc_ncm' at usb-0000:00:14.0-4, Huawei CDC NCM device, 32:14:94:92:ff:b5
Jun 20 13:04:33 user44 kernel: [  353.112445] usbcore: registered new interface driver huawei_cdc_ncm
Jun 20 13:04:33 user44 ModemManager[755]: <warn>  (ttyUSB0): port attributes not fully set
Jun 20 13:04:33 user44 NetworkManager[1026]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:14.0/usb3/3-4/3-4:1.1/net/wwan0, iface: wwan0)
Jun 20 13:04:33 user44 NetworkManager[1026]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:14.0/usb3/3-4/3-4:1.1/net/wwan0, iface: wwan0): no ifupdown configuration found.
Jun 20 13:04:33 user44 ModemManager[755]: <warn>  (ttyUSB1): port attributes not fully set
Jun 20 13:04:34 user44 ModemManager[755]: <warn>  (ttyUSB2): port attributes not fully set
Jun 20 13:04:34 user44 logger: usb_modeswitch: switched to 12d1:1506 on 003/005
Jun 20 13:04:34 user44 kernel: [  353.896732] scsi 9:0:0:0: CD-ROM                     Mass Storage     2.31 PQ: 0 ANSI: 2
Jun 20 13:04:34 user44 kernel: [  353.896808] scsi 10:0:0:0: Direct-Access              TF CARD Storage  2.31 PQ: 0 ANSI: 2
Jun 20 13:04:34 user44 kernel: [  353.898663] sr1: scsi-1 drive
Jun 20 13:04:34 user44 kernel: [  353.898835] sr 9:0:0:0: Attached scsi CD-ROM sr1
Jun 20 13:04:34 user44 kernel: [  353.898955] sr 9:0:0:0: Attached scsi generic sg3 type 5
Jun 20 13:04:34 user44 kernel: [  353.899719] sd 10:0:0:0: Attached scsi generic sg4 type 0
Jun 20 13:04:34 user44 kernel: [  353.900540] sd 10:0:0:0: [sdc] Attached SCSI removable disk
Jun 20 13:04:37 user44 ModemManager[755]: <warn>  (ttyUSB1): port attributes not fully set
Jun 20 13:04:37 user44 ModemManager[755]: <warn>  (ttyUSB2): port attributes not fully set
Jun 20 13:04:53 user44 ModemManager[755]: <info>  Creating modem with plugin 'Huawei' and '5' ports
Jun 20 13:04:53 user44 ModemManager[755]: <warn>  Could not grab port (usbmisc/cdc-wdm1): 'Cannot add port 'usbmisc/cdc-wdm1', unsupported'
Jun 20 13:04:53 user44 ModemManager[755]: <warn>  Could not grab port (tty/ttyUSB1): 'Cannot add port 'tty/ttyUSB1', unhandled serial type'
Jun 20 13:04:53 user44 ModemManager[755]: <warn>  (ttyUSB2): port attributes not fully set
Jun 20 13:04:53 user44 ModemManager[755]: <info>  Modem for device at '/sys/devices/pci0000:00/0000:00:14.0/usb3/3-4' successfully created
Jun 20 13:04:53 user44 ModemManager[755]: <warn>  couldn't load Supported Modes: 'Couldn't retrieve supported modes'
Jun 20 13:04:57 user44 ModemManager[755]: <warn>  couldn't load list of Own Numbers: 'Not found'
Jun 20 13:04:57 user44 ModemManager[755]: Invalid mobile equipment error code: 50
Jun 20 13:04:57 user44 ModemManager[755]: <info>  Modem: state changed (unknown -> disabled)
Jun 20 13:04:57 user44 NetworkManager[1026]: <warn> (ttyUSB2): failed to look up interface index
Jun 20 13:04:57 user44 NetworkManager[1026]: <info> (ttyUSB2): new Broadband device (driver: 'option1, huawei_cdc_ncm' ifindex: 0)
Jun 20 13:04:57 user44 NetworkManager[1026]: <info> (ttyUSB2): exported as /org/freedesktop/NetworkManager/Devices/2
Jun 20 13:04:57 user44 NetworkManager[1026]: <info> (ttyUSB2): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Jun 20 13:04:57 user44 NetworkManager[1026]: <info> (ttyUSB2): deactivating device (reason 'managed') [2]
Jun 20 13:04:57 user44 NetworkManager[1026]: <info> (ttyUSB2): device state change: unavailable -> disconnected (reason 'none') [20 30 0]
Jun 20 13:05:52 user44 NetworkManager[1026]: <info> Activation (ttyUSB2) starting connection 'MTS Default'
Jun 20 13:05:52 user44 NetworkManager[1026]: <info> (ttyUSB2): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Jun 20 13:05:52 user44 NetworkManager[1026]: <info> NetworkManager state is now CONNECTING
Jun 20 13:05:52 user44 NetworkManager[1026]: <info> Activation (ttyUSB2) Stage 1 of 5 (Device Prepare) scheduled...
Jun 20 13:05:52 user44 NetworkManager[1026]: <info> Activation (ttyUSB2) Stage 1 of 5 (Device Prepare) started...
Jun 20 13:05:52 user44 NetworkManager[1026]: <info> (ttyUSB2): device state change: prepare -> need-auth (reason 'none') [40 60 0]
Jun 20 13:05:52 user44 NetworkManager[1026]: mm_modem_simple_disconnect: assertion 'MM_IS_MODEM_SIMPLE (self)' failed
Jun 20 13:05:52 user44 NetworkManager[1026]: <info> Activation (ttyUSB2) Stage 1 of 5 (Device Prepare) complete.
Jun 20 13:05:52 user44 whoopsie[1052]: offline
Jun 20 13:05:52 user44 NetworkManager[1026]: <warn> No agents were available for this request.
Jun 20 13:05:52 user44 NetworkManager[1026]: <info> (ttyUSB2): device state change: need-auth -> failed (reason 'no-secrets') [60 120 7]
Jun 20 13:05:52 user44 NetworkManager[1026]: <info> NetworkManager state is now DISCONNECTED
Jun 20 13:05:52 user44 NetworkManager[1026]: <info> Marking connection 'MTS Default' invalid.
Jun 20 13:05:52 user44 NetworkManager[1026]: mm_modem_simple_disconnect: assertion 'MM_IS_MODEM_SIMPLE (self)' failed
Jun 20 13:05:52 user44 NetworkManager[1026]: <warn> Activation (ttyUSB2) failed for connection 'MTS Default'
Jun 20 13:05:52 user44 NetworkManager[1026]: <info> (ttyUSB2): device state change: failed -> disconnected (reason 'none') [120 30 0]
Jun 20 13:05:52 user44 NetworkManager[1026]: <info> (ttyUSB2): deactivating device (reason 'none') [0]
Jun 20 13:06:06 user44 NetworkManager[1026]: <info> Activation (ttyUSB2) starting connection 'MTS Default'
Jun 20 13:06:06 user44 NetworkManager[1026]: <info> (ttyUSB2): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Jun 20 13:06:06 user44 NetworkManager[1026]: <info> NetworkManager state is now CONNECTING
Jun 20 13:06:06 user44 NetworkManager[1026]: <info> Activation (ttyUSB2) Stage 1 of 5 (Device Prepare) scheduled...
Jun 20 13:06:06 user44 NetworkManager[1026]: <info> Activation (ttyUSB2) Stage 1 of 5 (Device Prepare) started...
Jun 20 13:06:06 user44 NetworkManager[1026]: <info> (ttyUSB2): device state change: prepare -> need-auth (reason 'none') [40 60 0]
Jun 20 13:06:06 user44 NetworkManager[1026]: mm_modem_simple_disconnect: assertion 'MM_IS_MODEM_SIMPLE (self)' failed
Jun 20 13:06:06 user44 NetworkManager[1026]: <info> Activation (ttyUSB2) Stage 1 of 5 (Device Prepare) complete.
Jun 20 13:06:06 user44 NetworkManager[1026]: <warn> No agents were available for this request.
Jun 20 13:06:06 user44 NetworkManager[1026]: <info> (ttyUSB2): device state change: need-auth -> failed (reason 'no-secrets') [60 120 7]
Jun 20 13:06:06 user44 NetworkManager[1026]: <info> NetworkManager state is now DISCONNECTED
Jun 20 13:06:06 user44 NetworkManager[1026]: <info> Marking connection 'MTS Default' invalid.
Jun 20 13:06:06 user44 NetworkManager[1026]: mm_modem_simple_disconnect: assertion 'MM_IS_MODEM_SIMPLE (self)' failed
Jun 20 13:06:06 user44 NetworkManager[1026]: <warn> Activation (ttyUSB2) failed for connection 'MTS Default'
Jun 20 13:06:06 user44 NetworkManager[1026]: <info> (ttyUSB2): device state change: failed -> disconnected (reason 'none') [120 30 0]
Jun 20 13:06:06 user44 NetworkManager[1026]: <info> (ttyUSB2): deactivating device (reason 'none') [0]
Jun 20 13:06:24 user44 NetworkManager[1026]:    keyfile: removed /etc/NetworkManager/system-connections/MTS Default.
Jun 20 13:06:50 user44 NetworkManager[1026]: <info> Activation (ttyUSB2) starting connection 'MTS Default 1'
Jun 20 13:06:50 user44 NetworkManager[1026]: <info> (ttyUSB2): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Jun 20 13:06:50 user44 NetworkManager[1026]: <info> NetworkManager state is now CONNECTING
Jun 20 13:06:50 user44 NetworkManager[1026]: <info> Activation (ttyUSB2) Stage 1 of 5 (Device Prepare) scheduled...
Jun 20 13:06:50 user44 NetworkManager[1026]: <info> Activation (ttyUSB2) Stage 1 of 5 (Device Prepare) started...
Jun 20 13:06:50 user44 NetworkManager[1026]: <info> Activation (ttyUSB2) Stage 1 of 5 (Device Prepare) complete.
Jun 20 13:06:51 user44 ModemManager[755]: <info>  Simple connect started...
Jun 20 13:06:51 user44 ModemManager[755]: <info>  Simple connect state (3/8): Enable
Jun 20 13:06:51 user44 ModemManager[755]: <info>  Modem /org/freedesktop/ModemManager1/Modem/0: state changed (disabled -> enabling)
Jun 20 13:06:51 user44 NetworkManager[1026]: <info> (ttyUSB2) modem state changed, 'disabled' --> 'enabling' (reason: user-requested)
Jun 20 13:06:51 user44 ModemManager[755]: <warn>  (ttyUSB2): port attributes not fully set
Jun 20 13:06:51 user44 ModemManager[755]: <warn>  (ttyUSB0): port attributes not fully set
Jun 20 13:06:51 user44 ModemManager[755]: <info>  Modem /org/freedesktop/ModemManager1/Modem/0: 3GPP Registration state changed (unknown -> registering)
Jun 20 13:06:51 user44 ModemManager[755]: <info>  Modem /org/freedesktop/ModemManager1/Modem/0: 3GPP Registration state changed (registering -> home)
Jun 20 13:06:51 user44 ModemManager[755]: <info>  Modem /org/freedesktop/ModemManager1/Modem/0: 3GPP location updated (MCC: '0', MNC: '0', Location area code: 'D0B', Cell ID: '5412005')
Jun 20 13:06:51 user44 ModemManager[755]: <info>  Modem /org/freedesktop/ModemManager1/Modem/0: 3GPP location updated (MCC: '250', MNC: '1', Location area code: 'D0B', Cell ID: '5412005')
Jun 20 13:06:52 user44 ModemManager[755]: <info>  Modem /org/freedesktop/ModemManager1/Modem/0: state changed (enabling -> registered)
Jun 20 13:06:52 user44 ModemManager[755]: <info>  Simple connect state (4/8): Wait to get fully enabled
Jun 20 13:06:52 user44 ModemManager[755]: <info>  Simple connect state (5/8): Register
Jun 20 13:06:52 user44 ModemManager[755]: <info>  Simple connect state (6/8): Bearer
Jun 20 13:06:52 user44 NetworkManager[1026]: <info> (ttyUSB2) modem state changed, 'enabling' --> 'registered' (reason: user-requested)
Jun 20 13:06:52 user44 NetworkManager[1026]: <info> WWAN now enabled by management service
Jun 20 13:06:52 user44 ModemManager[755]: <info>  Simple connect state (7/8): Connect
Jun 20 13:06:52 user44 ModemManager[755]: <info>  Modem /org/freedesktop/ModemManager1/Modem/0: state changed (registered -> connecting)
Jun 20 13:06:52 user44 NetworkManager[1026]: <info> (ttyUSB2) modem state changed, 'registered' --> 'connecting' (reason: user-requested)
Jun 20 13:06:52 user44 ModemManager[755]: <info>  Modem /org/freedesktop/ModemManager1/Modem/0: signal quality updated (83)
Jun 20 13:06:52 user44 ModemManager[755]: <info>  Modem /org/freedesktop/ModemManager1/Modem/0: access technology changed (unknown -> umts)
Jun 20 13:06:52 user44 ModemManager[755]: <info>  Modem /org/freedesktop/ModemManager1/Modem/0: state changed (connecting -> connected)
Jun 20 13:06:52 user44 ModemManager[755]: <info>  Simple connect state (8/8): All done
Jun 20 13:06:52 user44 NetworkManager[1026]: <info> (ttyUSB2) modem state changed, 'connecting' --> 'connected' (reason: user-requested)
Jun 20 13:06:52 user44 NetworkManager[1026]: <warn> (ttyUSB2): failed to look up interface index
Jun 20 13:06:52 user44 NetworkManager[1026]: <info> Activation (ttyUSB2) Stage 2 of 5 (Device Configure) scheduled...
Jun 20 13:06:52 user44 NetworkManager[1026]: <info> Activation (ttyUSB2) Stage 2 of 5 (Device Configure) starting...
Jun 20 13:06:52 user44 NetworkManager[1026]: <info> (ttyUSB2): device state change: prepare -> config (reason 'none') [40 50 0]
Jun 20 13:06:52 user44 NetworkManager[1026]: <info> Activation (ttyUSB2) Stage 2 of 5 (Device Configure) successful.
Jun 20 13:06:52 user44 NetworkManager[1026]: <info> Activation (ttyUSB2) Stage 3 of 5 (IP Configure Start) scheduled.
Jun 20 13:06:52 user44 NetworkManager[1026]: <info> Activation (ttyUSB2) Stage 2 of 5 (Device Configure) complete.
Jun 20 13:06:52 user44 NetworkManager[1026]: <info> Activation (ttyUSB2) Stage 3 of 5 (IP Configure Start) started...
Jun 20 13:06:52 user44 NetworkManager[1026]: <info> (ttyUSB2): device state change: config -> ip-config (reason 'none') [50 70 0]
Jun 20 13:06:52 user44 NetworkManager[1026]: <info> using modem-specified IP timeout: 20 seconds
Jun 20 13:06:52 user44 NetworkManager[1026]: <info> starting PPP connection
Jun 20 13:06:52 user44 NetworkManager[1026]: <info> pppd started with pid 4253
Jun 20 13:06:52 user44 NetworkManager[1026]: <info> Activation (ttyUSB2) Stage 4 of 5 (IPv6 Configure Timeout) scheduled...
Jun 20 13:06:52 user44 NetworkManager[1026]: <info> Activation (ttyUSB2) Stage 3 of 5 (IP Configure Start) complete.
Jun 20 13:06:52 user44 NetworkManager[1026]: <info> Activation (ttyUSB2) Stage 4 of 5 (IPv6 Configure Timeout) started...
Jun 20 13:06:52 user44 NetworkManager[1026]: <info> Activation (ttyUSB2) Stage 4 of 5 (IPv6 Configure Timeout) complete.
Jun 20 13:06:52 user44 pppd[4253]: Plugin /usr/lib/x86_64-linux-gnu/pppd/2.4.5/nm-pppd-plugin.so loaded.
Jun 20 13:06:52 user44 pppd[4253]: pppd 2.4.5 started by root, uid 0
Jun 20 13:06:52 user44 pppd[4253]: Using interface ppp0
Jun 20 13:06:52 user44 pppd[4253]: Connect: ppp0 <--> /dev/ttyUSB2
Jun 20 13:06:52 user44 NetworkManager[1026]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
Jun 20 13:06:52 user44 NetworkManager[1026]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/ppp0, iface: ppp0): no ifupdown configuration found.
Jun 20 13:06:52 user44 NetworkManager[1026]: <warn> /sys/devices/virtual/net/ppp0: couldn't determine device driver; ignoring...
Jun 20 13:07:12 user44 NetworkManager[1026]: <warn> pppd timed out or didn't initialize our dbus module
Jun 20 13:07:12 user44 NetworkManager[1026]: <info> Activation (ttyUSB2) Stage 4 of 5 (IPv4 Configure Timeout) scheduled...
Jun 20 13:07:12 user44 pppd[4253]: Terminating on signal 15
Jun 20 13:07:12 user44 NetworkManager[1026]: <info> Activation (ttyUSB2) Stage 4 of 5 (IPv4 Configure Timeout) started...
Jun 20 13:07:12 user44 NetworkManager[1026]: <info> (ttyUSB2): device state change: ip-config -> failed (reason 'ip-config-unavailable') [70 120 5]
Jun 20 13:07:12 user44 NetworkManager[1026]: <info> NetworkManager state is now DISCONNECTED
Jun 20 13:07:12 user44 NetworkManager[1026]: <warn> Activation (ttyUSB2) failed for connection 'MTS Default 1'
Jun 20 13:07:12 user44 ModemManager[755]: <info>  Modem /org/freedesktop/ModemManager1/Modem/0: state changed (connected -> disconnecting)
Jun 20 13:07:12 user44 NetworkManager[1026]: <info> Activation (ttyUSB2) Stage 4 of 5 (IPv4 Configure Timeout) complete.
Jun 20 13:07:12 user44 NetworkManager[1026]: <info> (ttyUSB2) modem state changed, 'connected' --> 'disconnecting' (reason: user-requested)
Jun 20 13:07:12 user44 NetworkManager[1026]: <info> (ttyUSB2): device state change: failed -> disconnected (reason 'none') [120 30 0]
Jun 20 13:07:12 user44 NetworkManager[1026]: <info> (ttyUSB2): deactivating device (reason 'none') [0]
Jun 20 13:07:13 user44 ModemManager[755]: <warn>  (ttyUSB2): port attributes not fully set
Jun 20 13:07:14 user44 avahi-daemon[841]: Withdrawing workstation service for ppp0.
Jun 20 13:07:14 user44 NetworkManager[1026]:    SCPlugin-Ifupdown: devices removed (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
Jun 20 13:07:14 user44 ModemManager[755]: <info>  Modem /org/freedesktop/ModemManager1/Modem/0: state changed (disconnecting -> registered)
Jun 20 13:07:14 user44 NetworkManager[1026]: <info> (ttyUSB2) modem state changed, 'disconnecting' --> 'registered' (reason: user-requested)

---

### Post by varlesh-l on 2014-06-20
Problem solved. Modem was unlocked and installed firmware Huawei E3531s-6 22.318.05.00.00 Universal and Huawei WEBUI 15.100.05.03.03 
Device working and connected fine on HiLink

---

### Post by hakim-ara on 2015-03-09
> **varlesh-l said:**
> Problem solved. Modem was unlocked and installed firmware Huawei E3531s-6 22.318.05.00.00 Universal and Huawei WEBUI 15.100.05.03.03  Device working and connected fine on HiLink  How i can install firmware huawei on ubuntu 12.04

---

