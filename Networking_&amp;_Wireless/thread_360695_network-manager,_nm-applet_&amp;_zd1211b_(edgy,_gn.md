---
title: "network-manager, nm-applet &amp; zd1211b (edgy, gnome)"
date: 2007-02-13
forum: Networking &amp; Wireless
---

### Post by HilliBilly on 2007-02-13
hi,

using edgy, gnome and network-manager (incl. nm-applet) i am unable to connect via the nm-applet with my wifi usb stick (zd1211b, pheenet wlu-703Z).

BUT ... i could connect on the command line with

sudo ifconfing wlan0 up
sudo iwconfig wlan0 essid XXXXXXX key s:XXXXXXXXXXXXX enc on
sudo dhclient wlan0

btw ... sudo iwlist wlan0 scan shows all networks.

also i am able to see all available networks within the nm-applet but when i am choosing my network it asks for encr method and key but does not connect.

nm-applet does work for eth0 (normal ethernet) perfectly.

any ideas why it does not work for my wifi usb stick?


NetworkManager Applet 0.6.3

uname -r shows
2.6.17-11-386

lsusb shows
Bus 001 Device 002: ID 0ace:1215 ZyDAS 

/etc/network/interfaces shows only this:
auto lo
iface lo inet loopback

lsmod | grep zd1211 shows
usbcore               130304  3 zd1211b,uhci_hcd

---

### Post by trippinnik on 2007-02-14
i couldn't it to work with the network manager until i started using the zd1211rw driver.  it must have something to do with the driver or how network manager detects network devices.

---

### Post by HilliBilly on 2007-02-14
hi, 

tried zd1211rw instead of zd1211b but no real difference (except that i got the orange for the line quality which was grey before). sorry for the long text but maybe it helps to find the reason for the problem.

question: is the method how i tried the other module correct?

[B]:~$ sudo modprobe -v zd1211rw
:~$ sudo modprobe -r zd1211
:~$ sudo modprobe -r zd1211b
:~$ sudo /etc/init.d/dbus/ restart
:~$ sudo ifconfig wlan0 up
[/B]
[17257483.452000] UnStoppable Scanning
[17257483.452000] UnStoppable Scanning
[17257483.452000] zd1205: (enter) zd1205_close, /home/hjs/zd1211-driver-r83/src/zd1205.c line 4896
[17257483.452000] zd1205: (exit) zd1205_close, /home/hjs/zd1211-driver-r83/src/zd1205.c line 4962
[17257483.480000] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[17257500.300000] eth0: no IPv6 routers present
[17257924.552000] ieee80211_crypt: registered algorithm 'NULL'
[17257924.564000] ieee80211: 802.11 data/management/control stack, git-1.1.13
[17257924.564000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[17257924.704000] usbcore: registered new driver zd1211rw
[17257939.240000] usbcore: deregistering driver zd1211b
[17257946.528000] eth0: link down
[17257990.916000] usb 1-1: new full speed USB device using uhci_hcd and address 6
[17257991.084000] usb 1-1: configuration #1 chosen from 1 choice
[17257991.472000] zd1211rw 1-1:1.0: firmware version 4725
[17257991.536000] zd1211rw 1-1:1.0: zd1211b chip 0ace:1215 v4810 full 00-1a-50 AL2230_RF pa0 ---
[17257991.540000] zd1211rw 1-1:1.0: eth1
[17257991.732000] ZD1211B - [http://zd1211.ath.cx/](http://zd1211.ath.cx/) - r83
[17257991.732000] Based on [www.zydas.com.tw](www.zydas.com.tw) driver version 2.5.0.0
[17257991.732000] usbcore: registered new driver zd1211b
[17257992.048000] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[17258016.028000] usbcore: deregistering driver zd1211b
[17258022.176000] usb 1-1: USB disconnect, address 6
[17258022.176000] zd1211rw 1-1:1.0: error ioread32(CR_REG1): -22
[17258024.444000] usb 1-1: new full speed USB device using uhci_hcd and address 7
[17258024.612000] usb 1-1: configuration #1 chosen from 1 choice
[17258025.264000] zd1211rw 1-1:1.0: firmware version 4725
[17258025.328000] zd1211rw 1-1:1.0: zd1211b chip 0ace:1215 v4810 full 00-1a-50 AL2230_RF pa0 ---
[17258025.332000] zd1211rw 1-1:1.0: eth1
[17258025.456000] ZD1211B - [http://zd1211.ath.cx/](http://zd1211.ath.cx/) - r83
[17258025.456000] Based on [www.zydas.com.tw](www.zydas.com.tw) driver version 2.5.0.0
[17258025.456000] usbcore: registered new driver zd1211b
[17258025.668000] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[17258067.816000] ieee80211_crypt: registered algorithm 'WEP'
[17258067.944000] SoftMAC: Open Authentication completed with 00:c0:49:d3:da:6b
[17258068.004000] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[17258078.808000] wlan0: no IPv6 routers present
[17258127.932000] ADDRCONF(NETDEV_UP): wlan0: link is not ready


[B]:~$ sudo modprobe -r zd1211rw
:~$ sudo /etc/init.d/dbus restart
[/B] * Stopping System Tools Backends system-tools-backends [ ok ] 
 * Stopping NetworkManager dispatcher[ ok ] 
 * Stopping Avahi mDNS/DNS-SD Daemon: avahi -daemon [ ok ] 
 * Stopping NetworkManager daemon [ ok ] 
 * Stopping DBUS aware dhcp client: dhcdbd [ ok ] 
 * Stopping Hardware abstraction layer hald [ ok ] 
 * Stopping system message bus dbus [ ok ] 
 * Starting system message bus dbus [ ok ] 
 * Starting Hardware abstraction layer hald [ ok ] 
 * Starting DBUS aware dhcp client: dhcdbd [ ok ] 
 * Starting NetworkManager daemon [ ok ] 
 * Starting Avahi mDNS/DNS-SD Daemon: avahi-daemon [ ok ] 
 * Starting NetworkManager dispatcher [ ok ] 
 * Starting System Tools Backends system-tools-backends [ ok ] 
[B]:~$ sudo ifconfig wlan0 up

:~$ dmesg
[/B][17258395.652000] usb 1-1: USB disconnect, address 7
[17258395.652000] zd1211rw 1-1:1.0: error ioread32(CR_REG1): -22
[17258409.260000] usbcore: deregistering driver zd1211rw
[17258443.752000] usb 1-1: new full speed USB device using uhci_hcd and address 8
[17258443.920000] usb 1-1: configuration #1 chosen from 1 choice
[17258444.036000] usb 1-1: reset full speed USB device using uhci_hcd and address 8
[17258444.188000] Release Ver = 4810
[17258444.188000] zd1211:bulk out: wMaxPacketSize = 40
[17258444.188000] zd1211:bulk in: wMaxPacketSize = 40
[17258444.188000] zd1211:interrupt in: wMaxPacketSize = 40
[17258444.188000] zd1211:interrupt in: int_interval = 1
[17258444.188000] zd1211:bulk out: wMaxPacketSize = 40
[17258444.188000] EEPORM Ver = 4810
[17258444.200000] zd1211:USB Download Boot code success
[17258444.212000] zd1211:MAC address = 00:1a:50:00:04:87
[17258444.216000] zd1211:AddrEntryTable = f7c6
[17258444.220000] zd1211:RF_Mode = 80000084
[17258444.220000] PA type: 0
[17258444.220000] Airoha AL2230S_RF
[17258444.220000] zd1211:Pure B-Mode
[17258444.400000] zd1211:AllowedChannel = 000007ff
[17258444.404000] zd1211:LinkLEDn = 200
[17258444.408000] AllowedChannel = 000107ff
[17258444.408000] Region:16
[17258444.904000] zd1205: (exit) zd1205_config, /home/hjs/zd1211-driver-r83/src/zd1205.c line 2601
[17258444.904000] zd1205: (exit) zd1205_init, /home/hjs/zd1211-driver-r83/src/zd1205.c line 8570
[17258451.976000] zd1205: (enter) zd1205_open, /home/hjs/zd1211-driver-r83/src/zd1205.c line 4353
[17258452.016000] zd1205: (exit) zd1205_open, /home/hjs/zd1211-driver-r83/src/zd1205.c line 4436
[17258452.016000] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[17258489.508000] zd1211:Switch to Infra mode
[17258489.508000] zd1211:Pure B-Mode
[17258493.012000] keybuf data [0]: 
[17258493.012000] 
[17258493.012000] Just Update WEP key
[17258493.012000] zd1211:Switch to Infra mode
[17258493.012000] zd1211:Pure B-Mode
[17258493.028000] eth0: link down
[17258493.028000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[17258503.064000] keybuf data [0]: 
[17258503.064000] 
[17258503.064000] Just Update WEP key
[17258503.064000] zd1211:Switch to Infra mode
[17258503.068000] zd1211:Pure B-Mode
[17258524.916000] zd1211:Switch to Infra mode
[17258524.936000] zd1211:Pure B-Mode
[17258525.076000] wlan0: WPA: enabled
[17258525.112000] wlan0: Drop encrypted: enabled
[17258525.140000] wlan0: Configured authentication algorithms:  Open system
[17258525.900000] wlan0: Drop encrypted: enabled
[17258525.900000] zd1211:Switch to Infra mode
[17258525.900000] zd1211:Pure B-Mode
[17258525.904000] wlan0: WPA version:  WPA disabled
[17258525.904000] wlan0: pairwise cipher:  WEP104
[17258525.904000] wlan0: group cipher:  WEP104
[17258525.904000] wlan0: key mgmt:  unsupported key mgmt '0x08'
[17258525.904000] wlan0: privacy: enabled
[17258525.904000] wlan0: Allow Rx unencrypted EAPOL: enabled
[17258526.132000] zd1211:Pure B-Mode
[17258526.316000] zd1211:STA_ASSOCIATED with 00:c0:49:d3:da:6b
[17258526.316000] zd1211:Notify_join_event:00:c0:49:d3:da:6b
[17258526.316000] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[17258526.324000] *** Block Non-EAPol packet before key installed:86dd
[17258526.940000] *** Block Non-EAPol packet before key installed:86dd
[17258527.940000] *** Block Non-EAPol packet before key installed:86dd
[17258528.500000] *** Block Non-EAPol packet before key installed:0800
[17258530.612000] *** Block Non-EAPol packet before key installed:0800
[17258531.940000] *** Block Non-EAPol packet before key installed:86dd
[17258532.716000] *** Block Non-EAPol packet before key installed:86dd
[17258534.612000] *** Block Non-EAPol packet before key installed:0800
[17258535.940000] *** Block Non-EAPol packet before key installed:86dd
[17258536.940000] wlan0: no IPv6 routers present
[17258539.612000] *** Block Non-EAPol packet before key installed:0800
[17258550.608000] *** Block Non-EAPol packet before key installed:0800
[17258569.608000] *** Block Non-EAPol packet before key installed:0800
[17258665.868000] Deauthenticate STA: 00:c0:49:d3:da:6b with reason code: 3
[17258665.888000] zd1211:STA_DEAUTHED:00:c0:49:d3:da:6b
[17258665.944000] wlan0: WPA: disabled
[17258665.944000] wlan0: Drop encrypted: disabled
[17258665.944000] zd1205: (enter) zd1205_close, /home/hjs/zd1211-driver-r83/src/zd1205.c line 4896
[17258665.948000] zd1205: (exit) zd1205_close, /home/hjs/zd1211-driver-r83/src/zd1205.c line 4962
[17258668.120000] keybuf data [0]: 
[17258668.120000] 
[17258668.120000] Just Update WEP key
[17258668.120000] zd1211:Switch to Infra mode
[17258668.120000] zd1211:Pure B-Mode
[17258676.272000] zd1205: (enter) zd1205_open, /home/hjs/zd1211-driver-r83/src/zd1205.c line 4353
[17258676.276000] zd1205: (exit) zd1205_open, /home/hjs/zd1211-driver-r83/src/zd1205.c line 4436
[17258676.276000] ADDRCONF(NETDEV_UP): wlan0: link is not ready

---

