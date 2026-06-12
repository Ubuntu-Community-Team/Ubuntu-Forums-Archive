---
title: "AnewKodi AC1200 usb 3.0 wifi adapter not working - Ubuntu 18.04"
date: 2018-06-06
forum: Networking &amp; Wireless
---

### Post by helektron on 2018-06-06
The full report: [http://paste.ubuntu.com/p/x2rgWyCDHJ/](http://paste.ubuntu.com/p/x2rgWyCDHJ/)


I can see the adapter but it seems to be disabled and I can't turn it on.

Can you help me please?

---

### Post by chili555 on 2018-06-06
I strongly suspect that, as soon as the internal device was activated and connected, Network Manager stopped trying. You will probably have better luck if you disable the internal device, ideally by blacklisting its driver.

What are you trying to accomplish with the USB that can't be done probably better with the internal device?

---

### Post by helektron on 2018-06-07
Hi chili55 I tried disabling internal device module "sudo rmmod [COLOR=#000000]ath9k" but it doesn't work. I need to use the adapter because the internal device doesn't have wifi ac 5ghz. Thanks for your help![/COLOR]

---

### Post by chili555 on 2018-06-07
Let's take drastic methods; we'll blacklist the driver:```
sudo -i
modprobe -r ath9k
echo "blacklist ath9k"  >>  /etc/modprobe.d/blacklist.conf
exit
```Reboot and let us see:```
dmesg | grep -e wlx -e rtl
```Thanks.

---

### Post by helektron on 2018-06-07
I tried following your steps but It doesn't work:


> &#10140; ~ dmesg | grep -e wlx -e rtl 
[ 51.730758] RTL871X: rtl8812au v4.3.14_13455.20150212_BTCOEX20150128-51
[ 51.730758] RTL871X: rtl8812au BT-Coex version = BTCOEX20150128-51
[ 51.798523] usbcore: registered new interface driver rtl8812au
[ 51.808262] rtl8812au 3-1.1:1.0 wlx[MASK]: renamed from wlan0
[ 51.848129] IPv6: ADDRCONF(NETDEV_UP): wlx[MASK]: link is not ready



When I plug in it:


> 
Jun 7 17:31:47 helektron kernel: [ 51.580027] usb 3-1.1: new high-speed USB device number 7 using xhci_hcdJun 7 17:31:47 helektron kernel: [ 51.680436] usb 3-1.1: New USB device found, idVendor=0bda, idProduct=b812
Jun 7 17:31:47 helektron kernel: [ 51.680441] usb 3-1.1: New USB device strings: Mfr=1, Product=2, SerialNumber=3
Jun 7 17:31:47 helektron kernel: [ 51.680444] usb 3-1.1: Product: 802.11ac NIC
Jun 7 17:31:47 helektron kernel: [ 51.680447] usb 3-1.1: Manufacturer: Realtek
Jun 7 17:31:47 helektron kernel: [ 51.680450] usb 3-1.1: SerialNumber: 123456
Jun 7 17:31:47 helektron mtp-probe: checking bus 3, device 7: "/sys/devices/pci0000:00/0000:00:14.0/usb3/3-1/3-1.1"
Jun 7 17:31:47 helektron mtp-probe: bus: 3, device: 7 was not an MTP device
Jun 7 17:31:47 helektron kernel: [ 51.718872] cfg80211: Loading compiled-in X.509 certificates for regulatory database
Jun 7 17:31:47 helektron kernel: [ 51.721580] cfg80211: Loaded X.509 cert 'sforshee: 00b28ddf47aef9cea7'
Jun 7 17:31:47 helektron kernel: [ 51.721777] platform regulatory.0: Direct firmware load for regulatory.db failed with error -2
Jun 7 17:31:47 helektron kernel: [ 51.721779] cfg80211: failed to load regulatory.db
Jun 7 17:31:47 helektron kernel: [ 51.730756] RTL871X: module init start
Jun 7 17:31:47 helektron kernel: [ 51.730758] RTL871X: rtl8812au v4.3.14_13455.20150212_BTCOEX20150128-51
Jun 7 17:31:47 helektron kernel: [ 51.730758] RTL871X: rtl8812au BT-Coex version = BTCOEX20150128-51
Jun 7 17:31:47 helektron systemd[1]: Starting Load/Save RF Kill Switch Status...
Jun 7 17:31:47 helektron kernel: [ 51.745254] RTL871X: invalid offset:0x42 
Jun 7 17:31:47 helektron kernel: [ 51.797958] RTL871X: rtw_ndev_init(wlan0)
Jun 7 17:31:47 helektron kernel: [ 51.798523] usbcore: registered new interface driver rtl8812au
Jun 7 17:31:47 helektron kernel: [ 51.798526] RTL871X: module init ret=0
Jun 7 17:31:47 helektron NetworkManager[1085]: <info> [1528385507.8359] wifi-nl80211: (wlan0): using nl80211 for WiFi device control
Jun 7 17:31:47 helektron NetworkManager[1085]: <info> [1528385507.8363] device (wlan0): driver supports Access Point (AP) mode
Jun 7 17:31:47 helektron NetworkManager[1085]: <info> [1528385507.8385] manager: (wlan0): new 802.11 WiFi device (/org/freedesktop/NetworkManager/Devices/3)
Jun 7 17:31:47 helektron systemd-udevd[2582]: link_config: autonegotiation is unset or enabled, the speed and duplex are not writable.
Jun 7 17:31:47 helektron NetworkManager[1085]: <info> [1528385507.8455] supplicant: wpa_supplicant running
Jun 7 17:31:47 helektron upowerd[1266]: unhandled action 'bind' on /sys/devices/pci0000:00/0000:00:14.0/usb3/3-1/3-1.1
Jun 7 17:31:47 helektron NetworkManager[1085]: <info> [1528385507.8484] rfkill3: found WiFi radio killswitch (at /sys/devices/pci0000:00/0000:00:14.0/usb3/3-1/3-1.1/3-1.1:1.0/ieee80211/phy0/rfkill3) (driver rtl8812au)
Jun 7 17:31:47 helektron systemd[1]: Started Load/Save RF Kill Switch Status.
Jun 7 17:31:47 helektron kernel: [ 51.808262] rtl8812au 3-1.1:1.0 wlx[MASK]: renamed from wlan0
Jun 7 17:31:47 helektron NetworkManager[1085]: <info> [1528385507.8843] devices added (path: /sys/devices/pci0000:00/0000:00:14.0/usb3/3-1/3-1.1/3-1.1:1.0/net/wlx[MASK], iface: wlx[MASK])
Jun 7 17:31:47 helektron NetworkManager[1085]: <info> [1528385507.8844] device added (path: /sys/devices/pci0000:00/0000:00:14.0/usb3/3-1/3-1.1/3-1.1:1.0/net/wlx[MASK], iface: wlx[MASK]): no ifupdown configuration found.
Jun 7 17:31:47 helektron NetworkManager[1085]: <info> [1528385507.8845] device (wlx[MASK]): state change: unmanaged -> unavailable (reason 'managed', sys-iface-state: 'external')
Jun 7 17:31:47 helektron kernel: [ 51.848129] IPv6: ADDRCONF(NETDEV_UP): wlx[MASK]: link is not ready
Jun 7 17:31:47 helektron upowerd[1266]: unhandled action 'bind' on /sys/devices/pci0000:00/0000:00:14.0/usb3/3-1/3-1.1/3-1.1:1.0
Jun 7 17:31:50 helektron ModemManager[1071]: <info> Couldn't check support for device at '/sys/devices/pci0000:00/0000:00:14.0/usb3/3-1/3-1.1': not supported by any plugin
Jun 7 17:31:52 helektron NetworkManager[1085]: <warn> [1528385512.0013] platform-linux: do-change-link[3]: failure changing link: failure 1 (Operation not permitted)
Jun 7 17:31:54 helektron wpa_supplicant[1084]: Could not set interface wlx[MASK] flags (UP): Operation not permitted
Jun 7 17:31:54 helektron wpa_supplicant[1084]: nl80211: Could not set interface 'wlx[MASK]' UP
Jun 7 17:31:54 helektron wpa_supplicant[1084]: nl80211: deinit ifname=wlx[MASK] disabled_11b_rates=0
Jun 7 17:31:56 helektron systemd[1]: Starting Stop ureadahead data collection...
Jun 7 17:31:56 helektron systemd[1]: Started Stop ureadahead data collection.
Jun 7 17:31:57 helektron wpa_supplicant[1084]: Could not set interface wlx[MASK] flags (UP): Operation not permitted
Jun 7 17:31:57 helektron wpa_supplicant[1084]: WEXT: Could not set interface 'wlx[MASK]' UP
Jun 7 17:31:57 helektron wpa_supplicant[1084]: wlx[MASK]: Failed to initialize driver interface
Jun 7 17:31:57 helektron NetworkManager[1085]: <error> [1528385517.1225] sup-iface[0x5582d4d2cb90,wlx[MASK]]: error adding interface: wpa_supplicant couldn't grab this interface.
Jun 7 17:31:57 helektron NetworkManager[1085]: <info> [1528385517.1226] device (wlx[MASK]): supplicant interface state: starting -> down


---

### Post by helektron on 2018-06-07
Fixed! At the end it was a wrong driver. The correct driver for that usb adapter is: **rtl8822bu**

I used this fork for compiling 4.15+ kernel:

[https://github.com/FomalhautWeisszwerg/rtl8822bu](https://github.com/FomalhautWeisszwerg/rtl8822bu)

I hope it helps more people.

Thanks for your help!

Regards.

---

