---
title: "TurboTenna 007GTI, USB Restart Cycle, Ubuntu 13.10, RT2800usb"
date: 2014-01-04
forum: Networking &amp; Wireless
---

### Post by Leechpool on 2014-01-04
Hi,
I have a +35dB usb yagi/amp I got from [http://www.danets.com/turbotenna/UsbYagi.php](http://www.danets.com/turbotenna/UsbYagi.php). Its stunning and will pick up wifi like nothing else - I use it in hotels / on site etc. I previously used it successfully with ubuntu 12.04 - it just worked plug and play. I have a new laptop, vaio pro 13. I can't get it to work with new laptop which has ubuntu 13.10 on it.

Unit id is 148F:3070. When I plug it in and click on network manager, the associated dropdown menu/display appears to twitch every second or so but it never clearly displays the two nic I used to get with ubuntu 12.04. Looking at dmesg shows the usb connection is restarting approximately every second. I'm hoping someone can interpret what's going on or point me in the right direction.

I looked at lsmod and rt2800usb (which I think is the required driver) appears to be loaded. I tried sudo modprobe -r iwlmvm (I thought this might be the driver for internal wifi which could be conflicting with rt2800). The internal wifi nic stopped working as expected, but I found the same behaviour when I plugged in the usb adapter. I tried booting using older kernels available in the grub boot menu. The restart cycle seemed to have a lower frequency, maybe every 2 seconds but otherwise the behaviour was the same.

I'm at the end of my knowledge and googling has failed to find anything (I could recognise) as the same as my problem.

I would appreciate any assistance.

Thanks
:P


dmesg:

```
Jan  4 11:41:09 bert-laptop kernel: [  720.199136] usb 2-1: new high-speed USB device number 35 using xhci_hcd
Jan  4 11:41:09 bert-laptop kernel: [  720.233370] usb 2-1: New USB device found, idVendor=148f, idProduct=3070
Jan  4 11:41:09 bert-laptop kernel: [  720.233377] usb 2-1: New USB device strings: Mfr=1, Product=2, SerialNumber=3
Jan  4 11:41:09 bert-laptop kernel: [  720.233381] usb 2-1: Product: 802.11 n WLAN
Jan  4 11:41:09 bert-laptop kernel: [  720.233386] usb 2-1: Manufacturer: Ralink
Jan  4 11:41:09 bert-laptop kernel: [  720.233389] usb 2-1: SerialNumber: 1.0
Jan  4 11:41:10 bert-laptop kernel: [  720.399420] usb 2-1: reset high-speed USB device number 35 using xhci_hcd
Jan  4 11:41:10 bert-laptop kernel: [  720.426630] xhci_hcd 0000:00:14.0: xHCI xhci_drop_endpoint called with disabled ep ffff880210787240
Jan  4 11:41:10 bert-laptop kernel: [  720.426635] xhci_hcd 0000:00:14.0: xHCI xhci_drop_endpoint called with disabled ep ffff880210787200
Jan  4 11:41:10 bert-laptop kernel: [  720.426637] xhci_hcd 0000:00:14.0: xHCI xhci_drop_endpoint called with disabled ep ffff880210787280
Jan  4 11:41:10 bert-laptop kernel: [  720.426639] xhci_hcd 0000:00:14.0: xHCI xhci_drop_endpoint called with disabled ep ffff8802107872c0
Jan  4 11:41:10 bert-laptop kernel: [  720.426641] xhci_hcd 0000:00:14.0: xHCI xhci_drop_endpoint called with disabled ep ffff880210787300
Jan  4 11:41:10 bert-laptop kernel: [  720.426643] xhci_hcd 0000:00:14.0: xHCI xhci_drop_endpoint called with disabled ep ffff880210787340
Jan  4 11:41:10 bert-laptop kernel: [  720.426645] xhci_hcd 0000:00:14.0: xHCI xhci_drop_endpoint called with disabled ep ffff880210787380
Jan  4 11:41:10 bert-laptop kernel: [  720.426967] ieee80211 phy31: rt2x00_set_rt: Info - RT chipset 3070, rev 0201 detected
Jan  4 11:41:10 bert-laptop kernel: [  720.436829] ieee80211 phy31: rt2x00_set_rf: Info - RF chipset 0005 detected
Jan  4 11:41:10 bert-laptop kernel: [  720.437071] ieee80211 phy31: Selected rate control algorithm 'minstrel_ht'
Jan  4 11:41:10 bert-laptop mtp-probe: checking bus 2, device 35: "/sys/devices/pci0000:00/0000:00:14.0/usb2/2-1"
Jan  4 11:41:10 bert-laptop mtp-probe: bus: 2, device: 35 was not an MTP device
Jan  4 11:41:10 bert-laptop NetworkManager[736]: <info> rfkill34: found WiFi radio killswitch (at /sys/devices/pci0000:00/0000:00:14.0/usb2/2-1/2-1:1.0/ieee80211/phy31/rfkill34) (driver rt2800usb)
Jan  4 11:41:10 bert-laptop NetworkManager[736]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:14.0/usb2/2-1/2-1:1.0/net/wlan3, iface: wlan3)
Jan  4 11:41:10 bert-laptop NetworkManager[736]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:14.0/usb2/2-1/2-1:1.0/net/wlan3, iface: wlan3): no ifupdown configuration found.
Jan  4 11:41:10 bert-laptop NetworkManager[736]: <info> (wlan3): using nl80211 for WiFi device control
Jan  4 11:41:10 bert-laptop NetworkManager[736]: <info> (wlan3): driver supports Access Point (AP) mode
Jan  4 11:41:10 bert-laptop NetworkManager[736]: <info> (wlan3): new 802.11 WiFi device (driver: 'rt2800usb' ifindex: 33)
Jan  4 11:41:10 bert-laptop NetworkManager[736]: <info> (wlan3): exported as /org/freedesktop/NetworkManager/Devices/31
Jan  4 11:41:10 bert-laptop NetworkManager[736]: <info> (wlan3): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Jan  4 11:41:10 bert-laptop NetworkManager[736]: <info> (wlan3): bringing up device.
Jan  4 11:41:10 bert-laptop kernel: [  720.460991] ieee80211 phy31: rt2x00lib_request_firmware: Info - Loading firmware file 'rt2870.bin'
Jan  4 11:41:10 bert-laptop kernel: [  720.461016] ieee80211 phy31: rt2x00lib_request_firmware: Info - Firmware detected - version: 0.29
Jan  4 11:41:10 bert-laptop NetworkManager[736]: <info> (wlan3): preparing device.
Jan  4 11:41:10 bert-laptop NetworkManager[736]: <info> (wlan3): deactivating device (reason 'managed') [2]
Jan  4 11:41:10 bert-laptop kernel: [  720.690363] IPv6: ADDRCONF(NETDEV_UP): wlan3: link is not ready
Jan  4 11:41:10 bert-laptop NetworkManager[736]: <info> (wlan3) supports 4 scan SSIDs
Jan  4 11:41:10 bert-laptop NetworkManager[736]: <warn> Trying to remove a non-existant call id.
Jan  4 11:41:10 bert-laptop NetworkManager[736]: <info> (wlan3): supplicant interface state: starting -> ready
Jan  4 11:41:10 bert-laptop NetworkManager[736]: <info> (wlan3): device state change: unavailable -> disconnected (reason 'supplicant-available') [20 30 42]
Jan  4 11:41:10 bert-laptop NetworkManager[736]: <info> (wlan3): supplicant interface state: ready -> inactive
Jan  4 11:41:10 bert-laptop NetworkManager[736]: <info> (wlan3) supports 4 scan SSIDs
Jan  4 11:41:10 bert-laptop kernel: [  720.771795] usb 2-1: USB disconnect, device number 35
Jan  4 11:41:10 bert-laptop kernel: [  720.883661] ieee80211 phy31: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 0 in queue 0
Jan  4 11:41:10 bert-laptop kernel: [  720.883666] ieee80211 phy31: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 0 in queue 0
Jan  4 11:41:10 bert-laptop wpa_supplicant[765]: Could not read interface wlan3 flags: No such device
Jan  4 11:41:10 bert-laptop avahi-daemon[502]: Withdrawing workstation service for wlan3.
Jan  4 11:41:10 bert-laptop NetworkManager[736]:    SCPlugin-Ifupdown: devices removed (path: /sys/devices/pci0000:00/0000:00:14.0/usb2/2-1/2-1:1.0/net/wlan3, iface: wlan3)
Jan  4 11:41:10 bert-laptop NetworkManager[736]: <info> (wlan3): device state change: disconnected -> unmanaged (reason 'removed') [30 10 36]
Jan  4 11:41:10 bert-laptop NetworkManager[736]: <info> (wlan3): cleaning up...
Jan  4 11:41:10 bert-laptop NetworkManager[736]: <warn> (33) failed to find interface name for index
Jan  4 11:41:10 bert-laptop NetworkManager[736]: (nm-system.c:766):nm_system_iface_get_flags: runtime check failed: (iface != NULL)
Jan  4 11:41:10 bert-laptop NetworkManager[736]: <error> [1388835670.648622] [nm-system.c:768] nm_system_iface_get_flags(): (unknown): failed to get interface link object
Jan  4 11:41:10 bert-laptop NetworkManager[736]: <warn> sysctl: failed to open '/proc/sys/net/ipv6/conf/wlan3/accept_ra': (2) No such file or directory
Jan  4 11:41:10 bert-laptop NetworkManager[736]: <warn> sysctl: failed to open '/proc/sys/net/ipv6/conf/wlan3/use_tempaddr': (2) No such file or directory
Jan  4 11:41:10 bert-laptop NetworkManager[736]: <info> radio killswitch /sys/devices/pci0000:00/0000:00:14.0/usb2/2-1/2-1:1.0/ieee80211/phy31/rfkill34 disappeared
Jan  4 11:41:10 bert-laptop wpa_supplicant[765]: Could not read interface wlan3 flags: No such device

and then it repeats.....

Jan  4 11:41:10 bert-laptop kernel: [  721.227942] usb 2-1: new high-speed USB device number 36 using xhci_hcd
Jan  4 11:41:10 bert-laptop kernel: [  721.262282] usb 2-1: New USB device found, idVendor=148f, idProduct=3070
Jan  4 11:41:10 bert-laptop kernel: [  721.262287] usb 2-1: New USB device strings: Mfr=1, Product=2, SerialNumber=3
Jan  4 11:41:10 bert-laptop kernel: [  721.262290] usb 2-1: Product: 802.11 n WLAN
Jan  4 11:41:10 bert-laptop kernel: [  721.262292] usb 2-1: Manufacturer: Ralink
Jan  4 11:41:10 bert-laptop kernel: [  721.262294] usb 2-1: SerialNumber: 1.0
Jan  4 11:41:11 bert-laptop kernel: [  721.428297] usb 2-1: reset high-speed USB device number 36 using xhci_hcd
Jan  4 11:41:11 bert-laptop kernel: [  721.455498] xhci_hcd 0000:00:14.0: xHCI xhci_drop_endpoint called with disabled ep ffff8800d8a62040
Jan  4 11:41:11 bert-laptop kernel: [  721.455503] xhci_hcd 0000:00:14.0: xHCI xhci_drop_endpoint called with disabled ep ffff8800d8a62000
Jan  4 11:41:11 bert-laptop kernel: [  721.455506] xhci_hcd 0000:00:14.0: xHCI xhci_drop_endpoint called with disabled ep ffff8800d8a62080
Jan  4 11:41:11 bert-laptop kernel: [  721.455508] xhci_hcd 0000:00:14.0: xHCI xhci_drop_endpoint called with disabled ep ffff8800d8a620c0
Jan  4 11:41:11 bert-laptop kernel: [  721.455510] xhci_hcd 0000:00:14.0: xHCI xhci_drop_endpoint called with disabled ep ffff8800d8a62100
Jan  4 11:41:11 bert-laptop kernel: [  721.455512] xhci_hcd 0000:00:14.0: xHCI xhci_drop_endpoint called with disabled ep ffff8800d8a62140
Jan  4 11:41:11 bert-laptop kernel: [  721.455514] xhci_hcd 0000:00:14.0: xHCI xhci_drop_endpoint called with disabled ep ffff8800d8a62180
Jan  4 11:41:11 bert-laptop kernel: [  721.455820] ieee80211 phy32: rt2x00_set_rt: Info - RT chipset 3070, rev 0201 detected
Jan  4 11:41:11 bert-laptop kernel: [  721.465530] ieee80211 phy32: rt2x00_set_rf: Info - RF chipset 0005 detected
Jan  4 11:41:11 bert-laptop kernel: [  721.465775] ieee80211 phy32: Selected rate control algorithm 'minstrel_ht'
Jan  4 11:41:11 bert-laptop mtp-probe: checking bus 2, device 36: "/sys/devices/pci0000:00/0000:00:14.0/usb2/2-1"
Jan  4 11:41:11 bert-laptop mtp-probe: bus: 2, device: 36 was not an MTP device
Jan  4 11:41:11 bert-laptop NetworkManager[736]: <info> rfkill35: found WiFi radio killswitch (at /sys/devices/pci0000:00/0000:00:14.0/usb2/2-1/2-1:1.0/ieee80211/phy32/rfkill35) (driver rt2800usb)
Jan  4 11:41:11 bert-laptop NetworkManager[736]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:14.0/usb2/2-1/2-1:1.0/net/wlan3, iface: wlan3)
Jan  4 11:41:11 bert-laptop NetworkManager[736]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:14.0/usb2/2-1/2-1:1.0/net/wlan3, iface: wlan3): no ifupdown configuration found.
Jan  4 11:41:11 bert-laptop NetworkManager[736]: <info> (wlan3): using nl80211 for WiFi device control
Jan  4 11:41:11 bert-laptop NetworkManager[736]: <info> (wlan3): driver supports Access Point (AP) mode
Jan  4 11:41:11 bert-laptop NetworkManager[736]: <info> (wlan3): new 802.11 WiFi device (driver: 'rt2800usb' ifindex: 34)
Jan  4 11:41:11 bert-laptop NetworkManager[736]: <info> (wlan3): exported as /org/freedesktop/NetworkManager/Devices/32
Jan  4 11:41:11 bert-laptop NetworkManager[736]: <info> (wlan3): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Jan  4 11:41:11 bert-laptop NetworkManager[736]: <info> (wlan3): bringing up device.
Jan  4 11:41:11 bert-laptop kernel: [  721.489877] ieee80211 phy32: rt2x00lib_request_firmware: Info - Loading firmware file 'rt2870.bin'
Jan  4 11:41:11 bert-laptop kernel: [  721.489905] ieee80211 phy32: rt2x00lib_request_firmware: Info - Firmware detected - version: 0.29
Jan  4 11:41:11 bert-laptop NetworkManager[736]: <info> (wlan3): preparing device.
Jan  4 11:41:11 bert-laptop NetworkManager[736]: <info> (wlan3): deactivating device (reason 'managed') [2]
Jan  4 11:41:11 bert-laptop kernel: [  721.719281] IPv6: ADDRCONF(NETDEV_UP): wlan3: link is not ready
Jan  4 11:41:11 bert-laptop NetworkManager[736]: <info> (wlan3) supports 4 scan SSIDs
Jan  4 11:41:11 bert-laptop NetworkManager[736]: <warn> Trying to remove a non-existant call id.
Jan  4 11:41:11 bert-laptop NetworkManager[736]: <info> (wlan3): supplicant interface state: starting -> ready
Jan  4 11:41:11 bert-laptop NetworkManager[736]: <info> (wlan3): device state change: unavailable -> disconnected (reason 'supplicant-available') [20 30 42]
Jan  4 11:41:11 bert-laptop NetworkManager[736]: <info> (wlan3): supplicant interface state: ready -> inactive
Jan  4 11:41:11 bert-laptop NetworkManager[736]: <info> (wlan3) supports 4 scan SSIDs
Jan  4 11:41:11 bert-laptop kernel: [  721.804675] usb 2-1: USB disconnect, device number 36
Jan  4 11:41:11 bert-laptop kernel: [  721.916484] ieee80211 phy32: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 0 in queue 0
Jan  4 11:41:11 bert-laptop kernel: [  721.916491] ieee80211 phy32: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 0 in queue 0
Jan  4 11:41:11 bert-laptop wpa_supplicant[765]: Could not read interface wlan3 flags: No such device
Jan  4 11:41:11 bert-laptop avahi-daemon[502]: Withdrawing workstation service for wlan3.
Jan  4 11:41:11 bert-laptop NetworkManager[736]:    SCPlugin-Ifupdown: devices removed (path: /sys/devices/pci0000:00/0000:00:14.0/usb2/2-1/2-1:1.0/net/wlan3, iface: wlan3)
Jan  4 11:41:11 bert-laptop NetworkManager[736]: <info> (wlan3): device state change: disconnected -> unmanaged (reason 'removed') [30 10 36]
Jan  4 11:41:11 bert-laptop NetworkManager[736]: <info> (wlan3): cleaning up...
Jan  4 11:41:11 bert-laptop NetworkManager[736]: <warn> (34) failed to find interface name for index
Jan  4 11:41:11 bert-laptop NetworkManager[736]: (nm-system.c:766):nm_system_iface_get_flags: runtime check failed: (iface != NULL)
Jan  4 11:41:11 bert-laptop NetworkManager[736]: <error> [1388835671.692119] [nm-system.c:768] nm_system_iface_get_flags(): (unknown): failed to get interface link object
Jan  4 11:41:11 bert-laptop NetworkManager[736]: <warn> sysctl: failed to open '/proc/sys/net/ipv6/conf/wlan3/accept_ra': (2) No such file or directory
Jan  4 11:41:11 bert-laptop NetworkManager[736]: <warn> sysctl: failed to open '/proc/sys/net/ipv6/conf/wlan3/use_tempaddr': (2) No such file or directory
Jan  4 11:41:11 bert-laptop NetworkManager[736]: <info> radio killswitch /sys/devices/pci0000:00/0000:00:14.0/usb2/2-1/2-1:1.0/ieee80211/phy32/rfkill35 disappeared
Jan  4 11:41:11 bert-laptop wpa_supplicant[765]: Could not read interface wlan3 flags: No such device

and again .......etc.

Jan  4 11:41:11 bert-laptop kernel: [  722.276785] usb 2-1: new high-speed USB device number 37 using xhci_hcd
Jan  4 11:41:12 bert-laptop kernel: [  722.311147] usb 2-1: New USB device found, idVendor=148f, idProduct=3070
Jan  4 11:41:12 bert-laptop kernel: [  722.311152] usb 2-1: New USB device strings: Mfr=1, Product=2, SerialNumber=3
Jan  4 11:41:12 bert-laptop kernel: [  722.311154] usb 2-1: Product: 802.11 n WLAN
Jan  4 11:41:12 bert-laptop kernel: [  722.311156] usb 2-1: Manufacturer: Ralink
Jan  4 11:41:12 bert-laptop kernel: [  722.311158] usb 2-1: SerialNumber: 1.0
Jan  4 11:41:12 bert-laptop kernel: [  722.425130] usb 2-1: reset high-speed USB device number 37 using xhci_hcd
Jan  4 11:41:12 bert-laptop kernel: [  722.452156] xhci_hcd 0000:00:14.0: xHCI xhci_drop_endpoint called with disabled ep ffff880036a46040
Jan  4 11:41:12 bert-laptop kernel: [  722.452161] xhci_hcd 0000:00:14.0: xHCI xhci_drop_endpoint called with disabled ep ffff880036a46000
Jan  4 11:41:12 bert-laptop kernel: [  722.452164] xhci_hcd 0000:00:14.0: xHCI xhci_drop_endpoint called with disabled ep ffff880036a46080
Jan  4 11:41:12 bert-laptop kernel: [  722.452166] xhci_hcd 0000:00:14.0: xHCI xhci_drop_endpoint called with disabled ep ffff880036a460c0
Jan  4 11:41:12 bert-laptop kernel: [  722.452168] xhci_hcd 0000:00:14.0: xHCI xhci_drop_endpoint called with disabled ep ffff880036a46100
Jan  4 11:41:12 bert-laptop kernel: [  722.452170] xhci_hcd 0000:00:14.0: xHCI xhci_drop_endpoint called with disabled ep ffff880036a46140
Jan  4 11:41:12 bert-laptop kernel: [  722.452172] xhci_hcd 0000:00:14.0: xHCI xhci_drop_endpoint called with disabled ep ffff880036a46180
Jan  4 11:41:12 bert-laptop kernel: [  722.452514] ieee80211 phy33: rt2x00_set_rt: Info - RT chipset 3070, rev 0201 detected
Jan  4 11:41:12 bert-laptop kernel: [  722.462333] ieee80211 phy33: rt2x00_set_rf: Info - RF chipset 0005 detected
Jan  4 11:41:12 bert-laptop kernel: [  722.462588] ieee80211 phy33: Selected rate control algorithm 'minstrel_ht'
Jan  4 11:41:12 bert-laptop mtp-probe: checking bus 2, device 37: "/sys/devices/pci0000:00/0000:00:14.0/usb2/2-1"
Jan  4 11:41:12 bert-laptop mtp-probe: bus: 2, device: 37 was not an MTP device
Jan  4 11:41:12 bert-laptop NetworkManager[736]: <info> rfkill36: found WiFi radio killswitch (at /sys/devices/pci0000:00/0000:00:14.0/usb2/2-1/2-1:1.0/ieee80211/phy33/rfkill36) (driver rt2800usb)
Jan  4 11:41:12 bert-laptop NetworkManager[736]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:14.0/usb2/2-1/2-1:1.0/net/wlan3, iface: wlan3)
Jan  4 11:41:12 bert-laptop NetworkManager[736]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:14.0/usb2/2-1/2-1:1.0/net/wlan3, iface: wlan3): no ifupdown configuration found.
Jan  4 11:41:12 bert-laptop NetworkManager[736]: <info> (wlan3): using nl80211 for WiFi device control
Jan  4 11:41:12 bert-laptop NetworkManager[736]: <info> (wlan3): driver supports Access Point (AP) mode
Jan  4 11:41:12 bert-laptop NetworkManager[736]: <info> (wlan3): new 802.11 WiFi device (driver: 'rt2800usb' ifindex: 35)
Jan  4 11:41:12 bert-laptop NetworkManager[736]: <info> (wlan3): exported as /org/freedesktop/NetworkManager/Devices/33
Jan  4 11:41:12 bert-laptop NetworkManager[736]: <info> (wlan3): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Jan  4 11:41:12 bert-laptop NetworkManager[736]: <info> (wlan3): bringing up device.
Jan  4 11:41:12 bert-laptop kernel: [  722.478748] ieee80211 phy33: rt2x00lib_request_firmware: Info - Loading firmware file 'rt2870.bin'
Jan  4 11:41:12 bert-laptop kernel: [  722.478772] ieee80211 phy33: rt2x00lib_request_firmware: Info - Firmware detected - version: 0.29
Jan  4 11:41:12 bert-laptop NetworkManager[736]: <info> (wlan3): preparing device.
Jan  4 11:41:12 bert-laptop NetworkManager[736]: <info> (wlan3): deactivating device (reason 'managed') [2]
Jan  4 11:41:12 bert-laptop kernel: [  722.707950] IPv6: ADDRCONF(NETDEV_UP): wlan3: link is not ready
Jan  4 11:41:12 bert-laptop NetworkManager[736]: <info> (wlan3) supports 4 scan SSIDs
Jan  4 11:41:12 bert-laptop NetworkManager[736]: <warn> Trying to remove a non-existant call id.
Jan  4 11:41:12 bert-laptop NetworkManager[736]: <info> (wlan3): supplicant interface state: starting -> ready
Jan  4 11:41:12 bert-laptop NetworkManager[736]: <info> (wlan3): device state change: unavailable -> disconnected (reason 'supplicant-available') [20 30 42]
Jan  4 11:41:12 bert-laptop NetworkManager[736]: <info> (wlan3): supplicant interface state: ready -> inactive
Jan  4 11:41:12 bert-laptop NetworkManager[736]: <info> (wlan3) supports 4 scan SSIDs
Jan  4 11:41:12 bert-laptop kernel: [  722.809433] usb 2-1: USB disconnect, device number 37
Jan  4 11:41:12 bert-laptop kernel: [  722.921343] ieee80211 phy33: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 0 in queue 0
Jan  4 11:41:12 bert-laptop kernel: [  722.921353] ieee80211 phy33: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 0 in queue 0
Jan  4 11:41:12 bert-laptop wpa_supplicant[765]: Could not read interface wlan3 flags: No such device
Jan  4 11:41:12 bert-laptop avahi-daemon[502]: Withdrawing workstation service for wlan3.
Jan  4 11:41:12 bert-laptop NetworkManager[736]:    SCPlugin-Ifupdown: devices removed (path: /sys/devices/pci0000:00/0000:00:14.0/usb2/2-1/2-1:1.0/net/wlan3, iface: wlan3)
Jan  4 11:41:12 bert-laptop NetworkManager[736]: <info> (wlan3): device state change: disconnected -> unmanaged (reason 'removed') [30 10 36]
Jan  4 11:41:12 bert-laptop NetworkManager[736]: <info> (wlan3): cleaning up...
Jan  4 11:41:12 bert-laptop NetworkManager[736]: <warn> (35) failed to find interface name for index
Jan  4 11:41:12 bert-laptop NetworkManager[736]: (nm-system.c:766):nm_system_iface_get_flags: runtime check failed: (iface != NULL)
Jan  4 11:41:12 bert-laptop NetworkManager[736]: <error> [1388835672.684417] [nm-system.c:768] nm_system_iface_get_flags(): (unknown): failed to get interface link object
Jan  4 11:41:12 bert-laptop NetworkManager[736]: <warn> sysctl: failed to open '/proc/sys/net/ipv6/conf/wlan3/accept_ra': (2) No such file or directory
Jan  4 11:41:12 bert-laptop NetworkManager[736]: <warn> sysctl: failed to open '/proc/sys/net/ipv6/conf/wlan3/use_tempaddr': (2) No such file or directory
Jan  4 11:41:12 bert-laptop NetworkManager[736]: <info> radio killswitch /sys/devices/pci0000:00/0000:00:14.0/usb2/2-1/2-1:1.0/ieee80211/phy33/rfkill36 disappeared
Jan  4 11:41:12 bert-laptop wpa_supplicant[765]: Could not read interface wlan3 flags: No such device

```

lsmod:
```
bert@bert-laptop:~$ sudo lsmod
[sudo] password for bert: 
Module                  Size  Used by
rt2800usb              27225  0 
rt2x00usb              20886  1 rt2800usb
rt2800lib              95479  1 rt2800usb
rt2x00lib              56124  3 rt2x00usb,rt2800lib,rt2800usb
crc_ccitt              12707  1 rt2800lib
snd_hda_codec_hdmi     41684  1 
snd_hda_codec_realtek    57336  1 
arc4                   12573  4 
joydev                 17575  0 
x86_pkg_temp_thermal    14269  0 
coretemp               17728  0 
kvm_intel             144079  0 
kvm                   458033  1 kvm_intel
crct10dif_pclmul       14250  0 
crc32_pclmul           13160  0 
ghash_clmulni_intel    13259  0 
pn544_mei              12787  0 
aesni_intel            55720  0 
aes_x86_64             17131  1 aesni_intel
lrw                    13323  1 aesni_intel
gf128mul               14951  1 lrw
glue_helper            14095  1 aesni_intel
ablk_helper            13597  1 aesni_intel
cryptd                 20530  3 ghash_clmulni_intel,aesni_intel,ablk_helper
mei_phy                13929  1 pn544_mei
pn544                  17995  1 pn544_mei
hci                    44774  2 pn544,mei_phy
nfc                    99442  2 hci,pn544
parport_pc             32866  0 
ppdev                  17711  0 
snd_hda_intel          57183  7 
snd_hda_codec         194973  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep              13613  1 snd_hda_codec
snd_pcm               107140  4 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
bnep                   24107  2 
rfcomm                 74748  0 
snd_page_alloc         18798  2 snd_pcm,snd_hda_intel
bluetooth             391788  10 bnep,rfcomm
uvcvideo               82247  0 
snd_seq_midi           13324  0 
videobuf2_vmalloc      13216  1 uvcvideo
videobuf2_memops       13362  1 videobuf2_vmalloc
videobuf2_core         40933  1 uvcvideo
snd_seq_midi_event     14899  1 snd_seq_midi
videodev              139263  2 uvcvideo,videobuf2_core
microcode              23788  0 
i915                  739257  5 
iwlmvm                176549  0 
snd_rawmidi            30465  1 snd_seq_midi
mac80211              635046  4 rt2x00lib,rt2x00usb,rt2800lib,iwlmvm
snd_seq                66061  2 snd_seq_midi_event,snd_seq_midi
drm_kms_helper         53224  1 i915
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              30038  2 snd_pcm,snd_seq
iwlwifi               179509  1 iwlmvm
psmouse               104142  0 
snd                    73802  24 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
rpcsec_gss_krb5        40513  0 
serio_raw              13462  0 
drm                   307490  4 i915,drm_kms_helper
cfg80211              505004  4 iwlwifi,mac80211,rt2x00lib,iwlmvm
lpc_ich                21163  0 
nfsd                  292399  2 
mei_me                 18418  0 
i2c_algo_bit           13564  1 i915
auth_rpcgss            60119  2 nfsd,rpcsec_gss_krb5
mei                    78698  3 pn544_mei,mei_phy,mei_me
soundcore              12680  1 snd
nfs_acl                12883  1 nfsd
mac_hid                13253  0 
nfs                   246801  0 
lockd                  95174  2 nfs,nfsd
tpm_tis                19116  0 
sony_laptop            54937  0 
sunrpc                295311  7 nfs,nfsd,rpcsec_gss_krb5,auth_rpcgss,lockd,nfs_acl
fscache                63827  1 nfs
video                  19574  1 i915
intel_smartconnect     12619  0 
lp                     17799  0 
parport                42481  3 lp,ppdev,parport_pc
nls_iso8859_1          12713  1 
ahci                   30063  3 
libahci                32118  1 ahci
bert@bert-laptop:~$ 

```

lsusb:

```
bert@bert-laptop:~$ sudo lsusb
[sudo] password for bert: 
Bus 001 Device 002: ID 8087:8000 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 002: ID 0bda:5727 Realtek Semiconductor Corp. 
Bus 002 Device 003: ID 148f:3070 Ralink Technology, Corp. RT2870/RT3070 Wireless Adapter
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
bert@bert-laptop:~$ 

```

```
bert@bert-laptop:~$ uname -mr
3.12.5-031205-generic x86_64

```

---

### Post by varunendra on 2014-01-05
Please follow the "Wireless Script" link in my signature, download and run the script as per instructions there, and post back the report it generates.

---

### Post by praseodym on 2014-01-05
Maybe there is a conflict with the internal Intel-wifi-card? Blacklist "iwlwifi" and reboot.

---

### Post by Leechpool on 2014-01-05
Varunendra,
Really appreciate your response. I followed the instructions. Output of script is attached.
Thanks again
:D

---

### Post by Leechpool on 2014-01-05
Praseodym,
Thanks for your suggestion. I had already tried blacklisting iwlwifi (in addition to modprobe -r iwlwifi). Anyway, just to make sure, I tried adding to blacklist.conf and rebooting. The internal wifi didn't start as expected and when I plugged in the yagi, the behaviour was the same- wifi manager twitching approximately every second as usb restarted. I've now unblacklisted iwlwifi.

I should mention I've also tried booting the laptop into windows 8 (it came with it and I've set it to be dual boot). With Windows 8 the yagi worked ok.

I've also tried booting my old vaio laptop (the one running ubuntu 12.04 and yagi ok) from usb running ubuntu 13.10. The yagi worked ok on the old vaio running 13.10 from usb. I tried running 12.04 from usb on my new laptop but unfortunately, it wouldn't boot.

I don't have much knowledge but I was wonding if the vaio pro running ubuntu 13.10 is not providing sufficient current to run the yagi and so causing the restart cycle. I had ruled this out as it worked ok with machine running windows 8 but I since read about the usb harware negotiating currents above 100mA with the OS. Hence I'm wondering if the combination of whatever 13.10 thinks the usb port can or can't provide when it interogates it coupled with the high current draw I'm sure the high gain yagi / RF amp requires is causing the problems. Am I "off on one" or is this possible and if so how could I investigate further?

Really appreciate any help to get this going.

:D

---

### Post by varunendra on 2014-01-05
> **Leechpool said:**
> I had already tried blacklisting iwlwifi (in addition to modprobe -r iwlwifi).

Did you also blacklist iwlmvm? Because iwlwifi is a dependency of it and blacklisting iwlwifi would have no effect as long as iwlmvm is loading. The same should be true for "modprobe -r", it won't unload iwlwifi and instead return error that it is being used (by iwlmvm).

And can you turn the power management off on the USB? -
```
sudo iwconfig wlan3 power off
```
Then check iwconfig to make sure it turned off. Does it make it stable?

I'm not sure about the insufficient power stuff, but seeing how the USB hardware is being reinitialized, firmware being reloaded at a constant interval, yes, that does seem to be a possibility. Does this antenna have an 5V input jack somewhere on it? If yes, you may try supplying it power from an external source (strictly between 4.6 to 5.2 volts).

---

### Post by Leechpool on 2014-01-06
Praseodym, Varunendra,

Many thanks to you both for your posts. Following my earlier idea that the issue might not be module related but instead caused by the response of the combination of my hardware (sony vaio Pro 13) and ubuntu 13.10 to the current requirement of the yagi / Rf amp, I went out today and bought  a powered usb hub (the yagi/amp does not have the facility to be power separately). With the yagi/amp powered by the usb hub's a.c. supply, everything works!! :P. 

So the issue was not caused by the driver(s) for the yagi/internal wifi but was lack of current supplied by the usb port. As the same laptop happly runs the yagi/amp when running windows 8, I think I still have some investigating to do e.g. is it possible to change the way ubuntu 13.10 "manages" the current output of the usb ports such that the yagi/amp can be used directly without the hub and associated a.c. power supply.

I'm not sure how this works now. Should I mark this thread as SOLVED and open another one about the managing-usb-current issue? If so where should I post a question about the usb current- in HARDWARE?

Thanks again.
:)

---

### Post by varunendra on 2014-01-06
> **Leechpool said:**
> ..bought  a powered usb hub (the yagi/amp does not have the facility to be power separately). With the yagi/amp powered by the usb hub's a.c. supply, everything works!! :P.

So the issue was not caused by the driver(s) for the yagi/internal wifi but was lack of current supplied by the usb port.
That's a very important thing you discovered. Thanks for sharing with us. :)

> Should I mark this thread as SOLVED and open another one about the managing-usb-current issue? If so where should I post a question about the usb current- in HARDWARE?
If your connection is stable and persistent across reboots (maybe try a day or two), I think you should mark this thread as [SOLVED], since what you tried is definitely a solution for the problem addressed in the thread.

The USB power management issue should definitely be addressed, but that is a different topic and should be discussed in a different thread. Yes 'Hardware' is an appropriate section for that.

I'd encourage you to also submit a bug report at launchpad against the kernel to bring attention to this apparent issue with power management. To collect information to attach with the bug report, "apport-bug" command can be used in a terminal -
```
apport-bug
```

Bug Reporting Etiquette and How to Efficiently Report a Bug : [https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)

Please let us know if you submit a bug report or if you find an already reported similar one.

---

### Post by Leechpool on 2014-01-25
I've done some experimenting and found that the restart cycle occurs with the laptop running windows as well, depending upon what length of USB lead I use. I'm just sorry it took so long for me to realise what was happening. I've got two USB extension leads, one is 1m and the other is 4m. My old laptop will run the Yagi happily through my two USB leads in series so i hadn't realised the significance of their length. With the 1m lead, the new Vaio Pro 13 running Windows 8 or Ubuntu will happily run the Yagi (stable over many days / several hours I've tried it). However, with the 4m lead, the Vaio Pro 13 will not drive the Yagi running Ubuntu or Windows 8, but instead gives the restart cycle I describe in eariler posts. I guess the comination of launch voltage, souce impedance, longitudinal cable impedance and load etc. are such with the Vaio Pro the longer lead / Yagi combination won't work together.  I'm sorry I've wasted everyone's time with this thread but I'm glad I understand what's happening now. :redface:

---

### Post by varunendra on 2014-01-25
A logical discussion about a practical problem can never be a waste of time, even if it leads to same old conclusions. At least, it reaffirms the old beliefs if can't add anything to it.

The length of USB leads has always been a subject of prime concern. Actually I'm surprised I overlooked it earlier.

Thanks for the correction and confirmation. :)

---

