---
title: "need usb wifi adapter to start automatically"
date: 2014-12-12
forum: Networking &amp; Wireless
---

### Post by Entheo on 2014-12-12
Hello all

I have recently added a wifi adapter to my pc and after following advice from chili555 on another thread, it all works great! My only small problem is that i have to take the adapter out and plug it back in before it works everytime i first turn on pc. Once on it stays on but is there a way to configure usb port to automatically switch adapter/usb port on at start up?

Any help would be greatfully received.

---

### Post by chili555 on 2014-12-12
Please restart your computer so we have a clean slate and run:```
lsmod > wifi.txt
lsusb >> wifi.txt
```Remove and reinsert the USB wireless and find the file wifi.txt in your user directory and post it here. Thanks.

---

### Post by Entheo on 2014-12-13
OK Chili here it is............

Module                  Size  Used by
cfg80211              496328  0 
hid_generic            12548  0 
bnep                   19624  2 
rfcomm                 69160  4 
bluetooth             395387  10 bnep,rfcomm
snd_usb_audio         153899  1 
usbhid                 48514  0 
snd_usbmidi_lib        25070  1 snd_usb_audio
hid                   106148  2 hid_generic,usbhid
8192cu                527317  0 
binfmt_misc            17468  1 
snd_hda_codec_via      27860  1 
kvm                   455718  0 
snd_hda_intel          52306  1 
snd_hda_codec         192906  2 snd_hda_codec_via,snd_hda_intel
snd_hwdep              13602  2 snd_usb_audio,snd_hda_codec
snd_pcm               102040  3 snd_usb_audio,snd_hda_codec,snd_hda_intel
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
serio_raw              13413  0 
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
edac_core              62291  0 
snd_rawmidi            30095  2 snd_usbmidi_lib,snd_seq_midi
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29433  2 snd_pcm,snd_seq
snd                    69273  16 snd_usb_audio,snd_hwdep,snd_timer,snd_hda_codec_via,snd_pcm,snd_seq,snd_rawmidi,snd_usbmidi_lib,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
edac_mce_amd           22617  0 
radeon               1522640  3 
k10temp                13126  0 
sp5100_tco             13979  0 
soundcore              12680  1 snd
i2c_piix4              22155  0 
mac_hid                13205  0 
ttm                    85150  1 radeon
drm_kms_helper         55071  1 radeon
drm                   303102  5 ttm,drm_kms_helper,radeon
asus_atk0110           18657  0 
i2c_algo_bit           13413  1 radeon
wmi                    19177  0 
shpchp                 37032  0 
parport_pc             32701  1 
ppdev                  17671  0 
lp                     17759  0 
parport                42299  3 lp,ppdev,parport_pc
pata_acpi              13038  0 
psmouse               102569  0 
ahci                   25819  2 
libahci                32716  1 ahci
atl1c                  46086  0 
pata_atiixp            13271  0 
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 007: ID 0846:9041 NetGear, Inc. WNA1000M 802.11bgn [Realtek RTL8188CUS]
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 002: ID 093a:2510 Pixart Imaging, Inc. Optical Mouse
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 004: ID 0603:00f2 Novatek Microelectronics Corp. 
Bus 003 Device 003: ID 1130:1620 Tenx Technology, Inc. 
[COLOR=#000080]Bus 003 Device 002: ID fc02:0101  [/COLOR]
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub



I have highlighted the adapter in case this helps.

Thanks for taking the time to look into this for me.

---

### Post by chili555 on 2014-12-13
So, not this one??> Bus 001 Device 007: ID 0846:9041 NetGear, Inc. WNA1000M 802.11bgn [Realtek RTL8188CUS]

---

### Post by Entheo on 2014-12-13
Yep sorry you are right! That wasn't on there before i followed them steps of yours on other post (which makes sense!) and before it kept pointing to that line i highlighted as the wifi adapter.

---

### Post by chili555 on 2014-12-13
We see that the driver is present when you boot:> snd_usbmidi_lib 25070 1 snd_usb_audio
hid 106148 2 hid_generic,usbhid
[COLOR="#FF0000"]8192cu [/COLOR]527317 0 
binfmt_misc 17468 1 
snd_hda_codec_via 27860 1 
<snip>So we wonder what's happening when you remove and reinsert the USB. Again, reboot so we have a clean slate and open a terminal and run:```
tail -f /var/log/syslog
```Remove and re-insert the USB and see what the syslog says. Copy and paste the relevant lines in your reply, along with:```
dmesg | grep -e wlan -e 8192
```Get out of 'tail' with  Ctrl+c.

---

### Post by Entheo on 2014-12-13
Ok so heres the syslog after reinserting adapter......

[SIZE=1]Dec 13 17:40:23 entheogenetix blueman-mechanism: Exiting 
Dec 13 17:40:29 entheogenetix kernel: [   58.643360] usb 1-5: USB disconnect, device number 6
Dec 13 17:40:29 entheogenetix kernel: [   58.643723] rtw_cmd_thread: DriverStopped(1) SurpriseRemoved(1) break at line 482
Dec 13 17:40:29 entheogenetix dhclient: receive_packet failed on wlan0: Network is down
Dec 13 17:40:29 entheogenetix avahi-daemon[631]: Interface wlan0.IPv6 no longer relevant for mDNS.
Dec 13 17:40:29 entheogenetix avahi-daemon[631]: Leaving mDNS multicast group on interface wlan0.IPv6 with address fe80::2ac6:8eff:fefd:8fa5.
Dec 13 17:40:29 entheogenetix avahi-daemon[631]: Interface wlan0.IPv4 no longer relevant for mDNS.
Dec 13 17:40:29 entheogenetix avahi-daemon[631]: Leaving mDNS multicast group on interface wlan0.IPv4 with address 192.168.1.2.
Dec 13 17:40:29 entheogenetix avahi-daemon[631]: IP_DROP_MEMBERSHIP failed: No such device
Dec 13 17:40:29 entheogenetix avahi-daemon[631]: Withdrawing address record for fe80::2ac6:8eff:fefd:8fa5 on wlan0.
Dec 13 17:40:29 entheogenetix avahi-daemon[631]: Withdrawing address record for 192.168.1.2 on wlan0.
Dec 13 17:40:29 entheogenetix avahi-daemon[631]: Withdrawing workstation service for wlan0.
Dec 13 17:40:29 entheogenetix whoopsie[955]: offline
Dec 13 17:40:29 entheogenetix NetworkManager[752]: <info> (wlan0): device state change: activated -> unmanaged (reason 'removed') [100 10 36]
Dec 13 17:40:29 entheogenetix NetworkManager[752]: <info> (wlan0): deactivating device (reason 'removed') [36]
Dec 13 17:40:29 entheogenetix NetworkManager[752]: <info> (wlan0): canceled DHCP transaction, DHCP client pid 1433
Dec 13 17:40:29 entheogenetix NetworkManager[752]: <warn> sysctl: failed to open '/proc/sys/net/ipv6/conf/wlan0/accept_ra': (2) No such file or directory
Dec 13 17:40:29 entheogenetix NetworkManager[752]: <warn> sysctl: failed to open '/proc/sys/net/ipv6/conf/wlan0/use_tempaddr': (2) No such file or directory
Dec 13 17:40:29 entheogenetix NetworkManager[752]: <warn> (3) failed to find interface name for index
Dec 13 17:40:29 entheogenetix NetworkManager[752]: (nm-system.c:766):nm_system_iface_get_flags: runtime check failed: (iface != NULL)
Dec 13 17:40:29 entheogenetix NetworkManager[752]: <error> [1418488829.878217] [nm-system.c:768] nm_system_iface_get_flags(): (unknown): failed to get interface link object
Dec 13 17:40:29 entheogenetix NetworkManager[752]: <warn> (3) failed to find interface name for index
Dec 13 17:40:29 entheogenetix NetworkManager[752]: (nm-system.c:766):nm_system_iface_get_flags: runtime check failed: (iface != NULL)
Dec 13 17:40:29 entheogenetix NetworkManager[752]: <error> [1418488829.882572] [nm-system.c:768] nm_system_iface_get_flags(): (unknown): failed to get interface link object
Dec 13 17:40:29 entheogenetix NetworkManager[752]: <info> (wlan0): bringing up device.
Dec 13 17:40:29 entheogenetix NetworkManager[752]: <warn> (3) failed to find interface name for index
Dec 13 17:40:29 entheogenetix NetworkManager[752]: nm_system_iface_flush_routes: assertion 'iface != NULL' failed
Dec 13 17:40:29 entheogenetix NetworkManager[752]: <warn> (3) failed to find interface name for index
Dec 13 17:40:29 entheogenetix NetworkManager[752]: <warn> DNS: plugin dnsmasq update failed
Dec 13 17:40:29 entheogenetix NetworkManager[752]: <info> Removing DNS information from /sbin/resolvconf
Dec 13 17:40:29 entheogenetix dnsmasq[1691]: setting upstream servers from DBus
Dec 13 17:40:29 entheogenetix NetworkManager[752]: <info> (wlan0): cleaning up...
Dec 13 17:40:29 entheogenetix NetworkManager[752]: <warn> (3) failed to find interface name for index
Dec 13 17:40:29 entheogenetix NetworkManager[752]: (nm-system.c:766):nm_system_iface_get_flags: runtime check failed: (iface != NULL)
Dec 13 17:40:29 entheogenetix NetworkManager[752]: <error> [1418488829.911124] [nm-system.c:768] nm_system_iface_get_flags(): (unknown): failed to get interface link object
Dec 13 17:40:29 entheogenetix NetworkManager[752]: <info> Unmanaged Device found; state CONNECTED forced. (see [http://bugs.launchpad.net/bugs/191889](http://bugs.launchpad.net/bugs/191889))
Dec 13 17:40:29 entheogenetix dbus[467]: [system] Activating service name='org.freedesktop.nm_dispatcher' (using servicehelper)
Dec 13 17:40:29 entheogenetix NetworkManager[752]:    SCPlugin-Ifupdown: devices removed (path: /sys/devices/pci0000:00/0000:00:12.2/usb1/1-5/1-5:1.0/net/wlan0, iface: wlan0)
Dec 13 17:40:29 entheogenetix dbus[467]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Dec 13 17:40:30 entheogenetix wpa_supplicant[1030]: Could not read interface wlan0 flags: No such device
Dec 13 17:40:38 entheogenetix kernel: [   67.422505] usb 1-5: new high-speed USB device number 7 using ehci-pci
Dec 13 17:40:38 entheogenetix kernel: [   67.538631] usb 1-5: New USB device found, idVendor=0846, idProduct=9041
Dec 13 17:40:38 entheogenetix kernel: [   67.538636] usb 1-5: New USB device strings: Mfr=1, Product=2, SerialNumber=3
Dec 13 17:40:38 entheogenetix kernel: [   67.538638] usb 1-5: Product: 802.11n WLAN Adapter
Dec 13 17:40:38 entheogenetix kernel: [   67.538640] usb 1-5: Manufacturer: Realtek
Dec 13 17:40:38 entheogenetix kernel: [   67.538641] usb 1-5: SerialNumber: 00e04c000001
Dec 13 17:40:38 entheogenetix mtp-probe: checking bus 1, device 7: "/sys/devices/pci0000:00/0000:00:12.2/usb1/1-5"
Dec 13 17:40:38 entheogenetix mtp-probe: bus: 1, device: 7 was not an MTP device
Dec 13 17:40:38 entheogenetix NetworkManager[752]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:12.2/usb1/1-5/1-5:1.0/net/wlan0, iface: wlan0)
Dec 13 17:40:38 entheogenetix NetworkManager[752]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:12.2/usb1/1-5/1-5:1.0/net/wlan0, iface: wlan0): no ifupdown configuration found.
Dec 13 17:40:38 entheogenetix NetworkManager[752]: <info> (wlan0): driver supports SSID scans (scan_capa 0x3F).
Dec 13 17:40:38 entheogenetix NetworkManager[752]: <info> (wlan0): using WEXT for WiFi device control
Dec 13 17:40:38 entheogenetix NetworkManager[752]: <info> (wlan0): new 802.11 WiFi device (driver: 'rtl8192cu' ifindex: 4)
Dec 13 17:40:38 entheogenetix NetworkManager[752]: <info> (wlan0): exported as /org/freedesktop/NetworkManager/Devices/2
Dec 13 17:40:38 entheogenetix NetworkManager[752]: <info> (wlan0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Dec 13 17:40:38 entheogenetix NetworkManager[752]: <info> (wlan0): bringing up device.
Dec 13 17:40:39 entheogenetix NetworkManager[752]: <info> (wlan0): preparing device.
Dec 13 17:40:39 entheogenetix NetworkManager[752]: <info> (wlan0): deactivating device (reason 'managed') [2]
Dec 13 17:40:39 entheogenetix NetworkManager[752]: <info> (wlan0): taking down device.
Dec 13 17:40:39 entheogenetix kernel: [   68.300821] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
Dec 13 17:40:39 entheogenetix kernel: [   68.301452] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
Dec 13 17:40:39 entheogenetix NetworkManager[752]: <info> (wlan0): bringing up device.
Dec 13 17:40:39 entheogenetix kernel: [   68.310641] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
Dec 13 17:40:39 entheogenetix NetworkManager[752]: <info> NetworkManager state is now DISCONNECTED
Dec 13 17:40:39 entheogenetix wpa_supplicant[1030]: nl80211: Driver does not support authentication/association or connect commands
Dec 13 17:40:39 entheogenetix NetworkManager[752]: <info> (wlan0) supports 1 scan SSIDs
Dec 13 17:40:39 entheogenetix NetworkManager[752]: <info> (wlan0): supplicant interface state: starting -> ready
Dec 13 17:40:39 entheogenetix NetworkManager[752]: <info> (wlan0): device state change: unavailable -> disconnected (reason 'supplicant-available') [20 30 42]
Dec 13 17:40:39 entheogenetix NetworkManager[752]: <warn> Trying to remove a non-existant call id.
Dec 13 17:40:39 entheogenetix NetworkManager[752]: <info> (wlan0): supplicant interface state: ready -> disconnected
Dec 13 17:40:39 entheogenetix NetworkManager[752]: <info> (wlan0) supports 1 scan SSIDs
Dec 13 17:40:40 entheogenetix NetworkManager[752]: <info> (wlan0): supplicant interface state: disconnected -> inactive
Dec 13 17:40:40 entheogenetix NetworkManager[752]: <info> Auto-activating connection 'Wi-Fi connection 1'.
Dec 13 17:40:40 entheogenetix NetworkManager[752]: <info> Activation (wlan0) starting connection 'Wi-Fi connection 1'
Dec 13 17:40:40 entheogenetix NetworkManager[752]: <info> (wlan0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Dec 13 17:40:40 entheogenetix NetworkManager[752]: <info> NetworkManager state is now CONNECTING
Dec 13 17:40:40 entheogenetix NetworkManager[752]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Dec 13 17:40:40 entheogenetix NetworkManager[752]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Dec 13 17:40:40 entheogenetix NetworkManager[752]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Dec 13 17:40:40 entheogenetix NetworkManager[752]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Dec 13 17:40:40 entheogenetix NetworkManager[752]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Dec 13 17:40:40 entheogenetix NetworkManager[752]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Dec 13 17:40:40 entheogenetix NetworkManager[752]: <info> Activation (wlan0/wireless): access point 'Wi-Fi connection 1' has security, but secrets are required.
Dec 13 17:40:40 entheogenetix NetworkManager[752]: <info> (wlan0): device state change: config -> need-auth (reason 'none') [50 60 0]
Dec 13 17:40:40 entheogenetix NetworkManager[752]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Dec 13 17:40:40 entheogenetix NetworkManager[752]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Dec 13 17:40:40 entheogenetix NetworkManager[752]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Dec 13 17:40:40 entheogenetix NetworkManager[752]: <info> (wlan0): device state change: need-auth -> prepare (reason 'none') [60 40 0]
Dec 13 17:40:40 entheogenetix NetworkManager[752]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Dec 13 17:40:40 entheogenetix NetworkManager[752]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Dec 13 17:40:40 entheogenetix NetworkManager[752]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Dec 13 17:40:40 entheogenetix NetworkManager[752]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Dec 13 17:40:42 entheogenetix NetworkManager[752]: <info> Activation (wlan0/wireless): connection 'Wi-Fi connection 1' has security, and secrets exist.  No new secrets needed.
Dec 13 17:40:42 entheogenetix NetworkManager[752]: <info> Config: added 'ssid' value 'heywards@la-roche'
Dec 13 17:40:42 entheogenetix NetworkManager[752]: <info> Config: added 'scan_ssid' value '1'
Dec 13 17:40:42 entheogenetix NetworkManager[752]: <info> Config: added 'key_mgmt' value 'WPA-PSK'
Dec 13 17:40:42 entheogenetix NetworkManager[752]: <info> Config: added 'psk' value '<omitted>'
Dec 13 17:40:42 entheogenetix NetworkManager[752]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Dec 13 17:40:42 entheogenetix NetworkManager[752]: <info> Config: set interface ap_scan to 1
Dec 13 17:40:42 entheogenetix wpa_supplicant[1030]: wlan0: Trying to associate with 4c:60:de:34:df:8a (SSID='heywards@la-roche' freq=2437 MHz)
Dec 13 17:40:42 entheogenetix wpa_supplicant[1030]: wlan0: Association request to the driver failed
Dec 13 17:40:42 entheogenetix NetworkManager[752]: <info> (wlan0): supplicant interface state: inactive -> associating
Dec 13 17:40:42 entheogenetix kernel: [   71.125483] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Dec 13 17:40:42 entheogenetix wpa_supplicant[1030]: wlan0: Associated with 4c:60:de:34:df:8a
Dec 13 17:40:42 entheogenetix NetworkManager[752]: <info> (wlan0): supplicant interface state: associating -> associated
Dec 13 17:40:42 entheogenetix NetworkManager[752]: <info> (wlan0): supplicant interface state: associated -> 4-way handshake
Dec 13 17:40:42 entheogenetix wpa_supplicant[1030]: wlan0: WPA: Key negotiation completed with 4c:60:de:34:df:8a [PTK=CCMP GTK=CCMP]
Dec 13 17:40:42 entheogenetix wpa_supplicant[1030]: wlan0: CTRL-EVENT-CONNECTED - Connection to 4c:60:de:34:df:8a completed [id=0 id_str=]
Dec 13 17:40:42 entheogenetix NetworkManager[752]: <info> (wlan0): supplicant interface state: 4-way handshake -> completed
Dec 13 17:40:42 entheogenetix NetworkManager[752]: <info> Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'heywards@la-roche'.
Dec 13 17:40:42 entheogenetix NetworkManager[752]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) scheduled.
Dec 13 17:40:42 entheogenetix NetworkManager[752]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) started...
Dec 13 17:40:42 entheogenetix NetworkManager[752]: <info> (wlan0): device state change: config -> ip-config (reason 'none') [50 70 0]
Dec 13 17:40:42 entheogenetix NetworkManager[752]: <info> Activation (wlan0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Dec 13 17:40:42 entheogenetix NetworkManager[752]: <info> dhclient started with pid 2162
Dec 13 17:40:42 entheogenetix NetworkManager[752]: <info> Activation (wlan0) Beginning IP6 addrconf.
Dec 13 17:40:42 entheogenetix NetworkManager[752]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete.
Dec 13 17:40:42 entheogenetix dhclient: Internet Systems Consortium DHCP Client 4.2.4
Dec 13 17:40:42 entheogenetix dhclient: Copyright 2004-2012 Internet Systems Consortium.
Dec 13 17:40:42 entheogenetix dhclient: All rights reserved.
Dec 13 17:40:42 entheogenetix dhclient: For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)
Dec 13 17:40:42 entheogenetix dhclient: 
Dec 13 17:40:42 entheogenetix NetworkManager[752]: <info> (wlan0): DHCPv4 state changed nbi -> preinit
Dec 13 17:40:42 entheogenetix dhclient: Listening on LPF/wlan0/28:c6:8e:fd:8f:a5
Dec 13 17:40:42 entheogenetix dhclient: Sending on   LPF/wlan0/28:c6:8e:fd:8f:a5
Dec 13 17:40:42 entheogenetix dhclient: Sending on   Socket/fallback
Dec 13 17:40:42 entheogenetix dhclient: DHCPREQUEST of 192.168.1.2 on wlan0 to 255.255.255.255 port 67 (xid=0x154a7f9f)
Dec 13 17:40:44 entheogenetix avahi-daemon[631]: Joining mDNS multicast group on interface wlan0.IPv6 with address fe80::2ac6:8eff:fefd:8fa5.
Dec 13 17:40:44 entheogenetix avahi-daemon[631]: New relevant interface wlan0.IPv6 for mDNS.
Dec 13 17:40:44 entheogenetix avahi-daemon[631]: Registering new address record for fe80::2ac6:8eff:fefd:8fa5 on wlan0.*.
Dec 13 17:40:45 entheogenetix dhclient: DHCPREQUEST of 192.168.1.2 on wlan0 to 255.255.255.255 port 67 (xid=0x154a7f9f)
Dec 13 17:40:45 entheogenetix dhclient: DHCPACK of 192.168.1.2 from 192.168.1.1
Dec 13 17:40:45 entheogenetix dhclient: bound to 192.168.1.2 -- renewal in 34336 seconds.
Dec 13 17:40:45 entheogenetix NetworkManager[752]: <info> (wlan0): DHCPv4 state changed preinit -> reboot
Dec 13 17:40:45 entheogenetix NetworkManager[752]: <info>   address 192.168.1.2
Dec 13 17:40:45 entheogenetix NetworkManager[752]: <info>   prefix 24 (255.255.255.0)
Dec 13 17:40:45 entheogenetix NetworkManager[752]: <info>   gateway 192.168.1.1
Dec 13 17:40:45 entheogenetix NetworkManager[752]: <info>   nameserver '192.168.1.1'
Dec 13 17:40:45 entheogenetix NetworkManager[752]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Configure Commit) scheduled...
Dec 13 17:40:45 entheogenetix NetworkManager[752]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Commit) started...
Dec 13 17:40:45 entheogenetix avahi-daemon[631]: Joining mDNS multicast group on interface wlan0.IPv4 with address 192.168.1.2.
Dec 13 17:40:45 entheogenetix avahi-daemon[631]: New relevant interface wlan0.IPv4 for mDNS.
Dec 13 17:40:45 entheogenetix avahi-daemon[631]: Registering new address record for 192.168.1.2 on wlan0.IPv4.
Dec 13 17:40:46 entheogenetix NetworkManager[752]: <info> (wlan0): device state change: ip-config -> secondaries (reason 'none') [70 90 0]
Dec 13 17:40:46 entheogenetix NetworkManager[752]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Commit) complete.
Dec 13 17:40:46 entheogenetix NetworkManager[752]: <info> (wlan0): device state change: secondaries -> activated (reason 'none') [90 100 0]
Dec 13 17:40:46 entheogenetix NetworkManager[752]: <info> NetworkManager state is now CONNECTED_GLOBAL
Dec 13 17:40:46 entheogenetix NetworkManager[752]: <info> Policy set 'Wi-Fi connection 1' (wlan0) as default for IPv4 routing and DNS.
Dec 13 17:40:46 entheogenetix NetworkManager[752]: <info> Writing DNS information to /sbin/resolvconf
Dec 13 17:40:46 entheogenetix dnsmasq[1691]: setting upstream servers from DBus
Dec 13 17:40:46 entheogenetix dnsmasq[1691]: using nameserver 192.168.1.1#53
Dec 13 17:40:47 entheogenetix NetworkManager[752]: <info> Activation (wlan0) successful, device activated.
Dec 13 17:40:47 entheogenetix dbus[467]: [system] Activating service name='org.freedesktop.nm_dispatcher' (using servicehelper)
Dec 13 17:40:47 entheogenetix dbus[467]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Dec 13 17:40:47 entheogenetix whoopsie[955]: message repeated 4 times: [ offline]
Dec 13 17:40:47 entheogenetix whoopsie[955]: online
Dec 13 17:40:58 entheogenetix ntpdate[2242]: adjust time server 91.189.89.199 offset 0.173587 sec
Dec 13 17:41:02 entheogenetix NetworkManager[752]: <info> (wlan0): IP6 addrconf timed out or failed.
Dec 13 17:41:02 entheogenetix NetworkManager[752]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) scheduled...
Dec 13 17:41:02 entheogenetix NetworkManager[752]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) started...
Dec 13 17:41:02 entheogenetix NetworkManager[752]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) complete.[/SIZE]

And here is grep....

[    0.000000] PERCPU: Embedded 29 pages/cpu @ffff88011fc00000 s86848 r8192 d23744 u262144
[    0.000000] pcpu-alloc: s86848 r8192 d23744 u262144 alloc=1*2097152
[    0.002080] Mount-cache hash table entries: 8192 (order: 4, 65536 bytes)
[    0.002087] Mountpoint-cache hash table entries: 8192 (order: 4, 65536 bytes)
[   13.675093] 8192cu: module verification failed: signature and/or  required key missing - tainting kernel
[   13.891274] usbcore: registered new interface driver rtl8192cu
[   16.332615] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   16.333294] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   16.342115] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   19.221662] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   68.300821] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   68.301452] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   68.310641] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   71.125483] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready

---

### Post by chili555 on 2014-12-13
Interesting. It actually looks like it was in the middle of trying to connect as you removed it:> Dec 13 17:40:23 entheogenetix blueman-mechanism: Exiting 
Dec 13 17:40:29 entheogenetix kernel: [ 58.643360] usb 1-5: [COLOR="#FF0000"]USB disconnect, device number 6[/COLOR]
Dec 13 17:40:29 entheogenetix kernel: [ 58.643723] rtw_cmd_thread: DriverStopped(1) [COLOR="#FF0000"]SurpriseRemoved[/COLOR](1) break at line 482
Dec 13 17:40:29 entheogenetix dhclient: receive_packet failed on wlan0: Network is down
Dec 13 17:40:29 entheogenetix avahi-daemon[631]: Interface wlan0.IPv6 no longer relevant for mDNS.
Dec 13 17:40:29 entheogenetix avahi-daemon[631]: Leaving mDNS multicast group on interface wlan0.IPv6 with address fe80::2ac6:8eff:fefd:8fa5.
Dec 13 17:40:29 entheogenetix avahi-daemon[631]: Interface wlan0.IPv4 no longer relevant for mDNS.
Dec 13 17:40:29 entheogenetix avahi-daemon[631]: Leaving mDNS multicast group on interface wlan0.IPv4 with address 192.168.1.2.
Dec 13 17:40:29 entheogenetix avahi-daemon[631]: IP_DROP_MEMBERSHIP failed: No such device
Dec 13 17:40:29 entheogenetix avahi-daemon[631]: Withdrawing address record for fe80::2ac6:8eff:fefd:8fa5 on wlan0.
Dec 13 17:40:29 entheogenetix avahi-daemon[631]: [COLOR="#FF0000"]Withdrawing address record for 192.168.1.2 on wlan0[/COLOR].I'm not sure I understand your initial post, then:> My only small problem is that i have to take the adapter out and plug it back in before it works everytime i first turn on pc.Is this an intermittent problem or does it happen every time you boot? Or...what?

---

### Post by Entheo on 2014-12-13
It happens everytime i boot up pc. After boot up i check the adapter and no flashing blue light....nothing until i remove and plug back in then blue flashing light and everything fine.
It would be nice for the wifi adapter to work on start up automatically without having to remove and plug back in everytime.

---

### Post by chili555 on 2014-12-13
Let's keep looking. Please reboot with the USB apparently not working and run:```
dmesg > wifi.txt
iwconfig  >>  wifi.txt
ifconfig  >>  wifi.txt
```Now unplug and replug it and run:```
dmesg | tail -n20 >> wifi.txt
ifconfig  >>  wifi.txt
```Post wifi.txt here: [http://paste.ubuntu.com](http://paste.ubuntu.com)

Tough little problem you have here!

---

### Post by Entheo on 2014-12-14
I cannot work this out but today, for the first time, the adapter is working perfectly and i have rebooted four times to make sure and everytime it connects during post at the same time my keyboard and mouse do which are both usb. I cannot understand it as i have not ran any update or done anything other than install a program called code::blocks from the ubuntu software centre so i don't know how it has fixed itself but fingers crossed it is all good now.

Just to confirm that before today the light would not flash on the adapter until i un and replugged. I would try to open thunderbird and firefox and as i would expect a message came up saying cannot connect to server as was no wifi connection. Why the hell it would suddenly work now is beyond me......but it works now.

If there is anything i can run for you to find out why it is suddenly working then let me know and i will post it but all is ok.

Thanks again chili for your time on this one. I really appreciate it.

---

### Post by chili555 on 2014-12-14
I am glad it is working! Hopefully, it will behave now! Please post back if it doesn't.

---

### Post by Entheo on 2014-12-14
:mad: I spoke to soon chili. All was fine this morning but just turned pc on again and the same problem! I will get that info and paste it in that paste bin link you gave me.

I really do not get this at all. Maybe gremlins grrrrrrr

---

### Post by Entheo on 2014-12-14
I ran them commands and this is all i got....



adam@entheogenetix:~$ dmesg > wifi.txt
adam@entheogenetix:~$ iwconfig >> wifi.txt
eth0      no wireless extensions.

lo        no wireless extensions.

adam@entheogenetix:~$ ifconfig >> wifi.txt
adam@entheogenetix:~$ dmesg | tail -n20 >> wifi.txt
adam@entheogenetix:~$ ifconfig >> wifi.txt

---

### Post by chili555 on 2014-12-14
> **Entheo said:**
> I ran them commands and this is all i got....



adam@entheogenetix:~$ dmesg > wifi.txt
adam@entheogenetix:~$ iwconfig >> wifi.txt
eth0      no wireless extensions.

lo        no wireless extensions.

adam@entheogenetix:~$ ifconfig >> wifi.txt
adam@entheogenetix:~$ dmesg | tail -n20 >> wifi.txt
adam@entheogenetix:~$ ifconfig >> wifi.txtNow please find the file wifi.txt and paste it as before; give me the link. Thanks.

---

### Post by Entheo on 2014-12-14
[http://paste.ubuntu.com/9517728/](http://paste.ubuntu.com/9517728/)

There you go! I think that should be ok

---

### Post by chili555 on 2014-12-14
Please again reboot and run:```
lsmod | grep 819
ps aux | grep -i network
```Post it here. I may see something!

---

### Post by Entheo on 2014-12-14
adam@entheogenetix:~$ lsmod | grep 819
8192cu                527317  0 
ahci                   25819  2 
adam@entheogenetix:~$ ps aux | grep -i network
root       718  0.2  0.1 347936  6300 ?        Ssl  18:39   0:00 NetworkManager
root      1372  0.0  0.0  10232  3672 ?        S    18:39   0:00 /sbin/dhclient -d -sf /usr/lib/NetworkManager/nm-dhcp-client.action -pf /run/sendsigs.omit.d/network-manager.dhclient-wlan0.pid -lf /var/lib/NetworkManager/dhclient-1bde4c89-f3ae-4e1d-a8d8-5fea5ed2d7c9-wlan0.lease -cf /var/lib/NetworkManager/dhclient-wlan0.conf wlan0
nobody    1770  0.0  0.0  38216  1500 ?        S    18:39   0:00 /usr/sbin/dnsmasq --no-resolv --keep-in-foreground --no-hosts --bind-interfaces --pid-file=/run/sendsigs.omit.d/network-manager.dnsmasq.pid --listen-address=127.0.1.1 --conf-file=/var/run/NetworkManager/dnsmasq.conf --cache-size=0 --proxy-dnssec --enable-dbus=org.freedesktop.NetworkManager.dnsmasq --conf-dir=/etc/NetworkManager/dnsmasq.d
adam      2034  0.0  0.0  18936   928 pts/7    S+   18:40   0:00 grep --color=auto -i network
adam@entheogenetix:~$

---

### Post by chili555 on 2014-12-14
We see the driver is loaded and NM is running as expected. Please reboot and when it's not running as needed, do:```
sudo modprobe -r 8192cu
sudo modprobe 8192cu
```If that does it, wait until the next time you would ordinarily shut down. Upon restart, try again. If it works again, we'll drop a couple of lines in rc.local.

---

### Post by Entheo on 2014-12-15
Hi Chili

I tried the modprobe removal and reconnection and it works brilliant! I have tried it twice and both times it activated the adapter when before there was nothing.

---

### Post by chili555 on 2014-12-15
Great news! Let's see if we can automate it:```
gksudo gedit /etc/rc.local
```Use nano or kate or leafpad if you don't have the text editor gedit. Right above exit 0, add these lines:```
modprobe -r 8192cu
sleep 1
modprobe 8192cu
```Proofread carefully, save and close the text editor.

You should be all set. Be sure to report back as the searchers will appreciate it.

---

### Post by Entheo on 2014-12-16
Yippy! It works! Thank you so much chili for all your help on this problem. 

 		 			 				:grin:

---

### Post by chili555 on 2014-12-16
Glad it's working. Please use thread tools at the top to mark Solved. The searchers will appreciate it.

---

