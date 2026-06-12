---
title: "Connected to router, no internet Ubuntu 15.10"
date: 2015-11-21
forum: Networking &amp; Wireless
---

### Post by zakrapovic on 2015-11-21
Hi everyone,

Recently reinstalled ubuntu, everything went fine
One problem, I do not have internet through wireless (I have to use USB tethering mobile)
The script wireless-info do not works either...

iwconfig:

> 
wlp5s0    IEEE 802.11abgn  ESSID:"Jacqueline"  
          Mode:Managed  Frequency:2.442 GHz  Access Point: F4:CA:E5:F4:E8:64   
          Bit Rate=1 Mb/s   Tx-Power=22 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=61/70  Signal level=-49 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:1  Invalid misc:186   Missed beacon:0

enp0s25   no wireless extensions.

lo        no wireless extensions.



ifconfig:

> enp0s25   Link encap:Ethernet  HWaddr d0:50:99:50:7b:22  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:20 Memory:fb300000-fb320000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:2308 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2308 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:463928 (463.9 KB)  TX bytes:463928 (463.9 KB)

wlp5s0    Link encap:Ethernet  HWaddr 48:51:b7:84:26:78  
          inet addr:192.168.1.32  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: 2a01:e35:39b8:c670:4829:a963:1880:886a/64 Scope:Global
          inet6 addr: 2a01:e35:39b8:c670:4a51:b7ff:fe84:2678/64 Scope:Global
          inet6 addr: fe80::4a51:b7ff:fe84:2678/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1280  Metric:1
          RX packets:430611 errors:0 dropped:0 overruns:0 frame:0
          TX packets:215218 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:539489266 (539.4 MB)  TX bytes:26833473 (26.8 MB)


netstat -r:
> 
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
default         192.168.1.254   0.0.0.0         UG        0 0          0 wlp5s0
link-local      *               255.255.0.0     U         0 0          0 wlp5s0
192.168.1.0     *               255.255.255.0   U         0 0          0 wlp5s0

My interface used to be wlan0 instead of wlp5s0, what the meaning of this change ?

Thank you very much, I suck at network

---

### Post by zakrapovic on 2015-11-22
Looking in kern.log show :

Nov 21 11:05:04 Yak kernel: [    1.695657] Intel(R) Wireless WiFi driver for Linux
Nov 21 11:05:04 Yak kernel: [    1.695659] Copyright(c) 2003- 2015 Intel Corporation
Nov 21 11:05:04 Yak kernel: [    1.695737] iwlwifi 0000:05:00.0: enabling device (0000 -> 0002)
Nov 21 11:05:04 Yak kernel: [    1.699954] iwlwifi 0000:05:00.0: Direct firmware load for iwlwifi-7260-15.ucode failed with error -2
Nov 21 11:05:04 Yak kernel: [    1.699969] iwlwifi 0000:05:00.0: Direct firmware load for iwlwifi-7260-14.ucode failed with error -2

It works on my dualboot (Elementary OS) how could i see the configuration it use, to put the same in my ubuntu ?

Thanks for helping

---

### Post by zakrapovic on 2015-11-26
Nobody inspired ? Very boring issue :(

---

### Post by chili555 on 2015-11-26
There are several questions here; I could turn this into a 50 reply thread. However, as life is short, let's shortcut to the kwik-n-durty answer. Please download this file to your desktop: [https://wireless.wiki.kernel.org/_media/en/users/drivers/iwlwifi-7260-ucode-15.227938.0.tgz](https://wireless.wiki.kernel.org/_media/en/users/drivers/iwlwifi-7260-ucode-15.227938.0.tgz) Right-click it and select 'Extract Here.' Now, in a terminal:```
cd ~/Desktop/iwlwifi-7260-ucode-15.227938.0/   
sudo cp  iwlwifi-7260-15.ucode  /lib/firmware
sudo modprobe -r iwlwifi
sudo modprobe iwlwifi 
```Detach the tether and your wireless should be working.

As for the renaming, please see: [http://askubuntu.com/questions/689070/network-interface-name-changes-after-update-to-15-10-udev-changes](http://askubuntu.com/questions/689070/network-interface-name-changes-after-update-to-15-10-udev-changes)

What, exactly, about the wireless script didn't work? Did you run it? Did it produce diagnostics that would have helped us find out and fix what is wrong? Or...??

---

### Post by zakrapovic on 2015-11-26
The script return that 
```
sed: -e expression #1, char 243: Unmatched ) or \)
Results saved in ".../wireless-info.txt".
```
and wireless-info.txt is empty

I did as you said, but I still do not have internet.

Thanks a lot helping

---

### Post by zakrapovic on 2015-11-28
Did some reading, feel less dumb, but I still do not succeed making it works
Here is some log that may be usefull

```
journalcmd -a -p err
```
Nov 28 16:33:12 Yak kernel: EDAC sbridge: ECC is disabled. Aborting
Nov 28 16:33:12 Yak kernel: EDAC sbridge: Couldn't find mci handler
Nov 28 16:33:12 Yak nvidia-persistenced[520]: Failed to query NVIDIA devices. Please ensure that the NVIDIA device files (/dev/nvidia*) exist, and that user 120 has read and write
Nov 28 16:33:14 Yak NetworkManager[852]: nm_device_get_device_type: assertion 'NM_IS_DEVICE (self)' failed
Nov 28 16:33:14 Yak NetworkManager[852]: <error> [1448724794.852826] [dns-manager/nm-dns-dnsmasq.c:387] update(): dnsmasq owner not found on bus: Could not get owner of name 'org.
Nov 28 16:33:14 Yak wpa_supplicant[1068]: dbus: wpa_dbus_get_object_properties: failed to get object properties: (none) none
Nov 28 16:33:14 Yak wpa_supplicant[1068]: dbus: Failed to construct signal
Nov 28 16:33:14 Yak wpa_supplicant[1068]: Could not read interface p2p-dev-wlp5s0 flags: No such device
Nov 28 16:33:18 Yak pulseaudio[1739]: [pulseaudio] bluez5-util.c: GetManagedObjects() failed: org.freedesktop.systemd1.LoadFailed: Unit dbus-org.bluez.service failed to load: No s
Nov 28 16:33:18 Yak pulseaudio[2136]: [pulseaudio] pid.c: Daemon already running.
Nov 28 16:33:18 Yak pulseaudio[2138]: [pulseaudio] pid.c: Daemon already running.

```
journalctl -a |grep 852                                                                      
```
Nov 28 16:33:14 Yak NetworkManager[852]: <info>  NetworkManager (version 1.0.4) is starting...
Nov 28 16:33:14 Yak NetworkManager[852]: <info>  Read config: /etc/NetworkManager/NetworkManager.conf
Nov 28 16:33:14 Yak NetworkManager[852]: <info>  VPN: loaded org.freedesktop.NetworkManager.pptp
Nov 28 16:33:14 Yak NetworkManager[852]: <info>  DNS: loaded plugin dnsmasq
Nov 28 16:33:14 Yak NetworkManager[852]: <info>  init!
Nov 28 16:33:14 Yak NetworkManager[852]: <info>  update_system_hostname
Nov 28 16:33:14 Yak NetworkManager[852]: <info>        interface-parser: parsing file /etc/network/interfaces
Nov 28 16:33:14 Yak NetworkManager[852]: <info>        interface-parser: finished parsing file /etc/network/interfaces
Nov 28 16:33:14 Yak NetworkManager[852]: <info>  management mode: unmanaged
Nov 28 16:33:14 Yak NetworkManager[852]: <info>  devices added (path: /sys/devices/pci0000:00/0000:00:14.0/usb1/1-8/1-8:1.0/net/enx02000d563537, iface: enx02000d563537)
Nov 28 16:33:14 Yak NetworkManager[852]: <info>  device added (path: /sys/devices/pci0000:00/0000:00:14.0/usb1/1-8/1-8:1.0/net/enx02000d563537, iface: enx02000d563537): no ifupdown configuration found.
Nov 28 16:33:14 Yak NetworkManager[852]: <info>  devices added (path: /sys/devices/pci0000:00/0000:00:19.0/net/enp0s25, iface: enp0s25)
Nov 28 16:33:14 Yak NetworkManager[852]: <info>  device added (path: /sys/devices/pci0000:00/0000:00:19.0/net/enp0s25, iface: enp0s25): no ifupdown configuration found.
Nov 28 16:33:14 Yak NetworkManager[852]: <info>  devices added (path: /sys/devices/pci0000:00/0000:00:1c.2/0000:05:00.0/net/wlp5s0, iface: wlp5s0)
Nov 28 16:33:14 Yak NetworkManager[852]: <info>  device added (path: /sys/devices/pci0000:00/0000:00:1c.2/0000:05:00.0/net/wlp5s0, iface: wlp5s0): no ifupdown configuration found.
Nov 28 16:33:14 Yak NetworkManager[852]: <info>  devices added (path: /sys/devices/virtual/net/lo, iface: lo)
Nov 28 16:33:14 Yak NetworkManager[852]: <info>  device added (path: /sys/devices/virtual/net/lo, iface: lo): no ifupdown configuration found.
Nov 28 16:33:14 Yak NetworkManager[852]: <info>  end _init.
Nov 28 16:33:14 Yak NetworkManager[852]: <info>  Loaded settings plugin ifupdown: (C) 2008 Canonical Ltd.  To report bugs please use the NetworkManager mailing list. (/usr/lib/x86_64-linux-gnu/NetworkManager/libnm-settings-plugin-ifupdown.so)
Nov 28 16:33:14 Yak NetworkManager[852]: <info>  Loaded settings plugin keyfile: (c) 2007 - 2015 Red Hat, Inc.  To report bugs please use the NetworkManager mailing list.
Nov 28 16:33:14 Yak NetworkManager[852]: <info>  SCPlugin-Ofono: init!
Nov 28 16:33:14 Yak NetworkManager[852]: <warn>  SCPlugin-Ofono: file doesn't exist: /var/lib/ofono
Nov 28 16:33:14 Yak NetworkManager[852]: <info>  SCPlugin-Ofono: end _init.
Nov 28 16:33:14 Yak NetworkManager[852]: <info>  Loaded settings plugin ofono: (C) 2013 Canonical Ltd.  To report bugs please use the NetworkManager mailing list. (/usr/lib/x86_64-linux-gnu/NetworkManager/libnm-settings-plugin-ofono.so)
Nov 28 16:33:14 Yak NetworkManager[852]: <info>  (12147776) ... get_connections.
Nov 28 16:33:14 Yak NetworkManager[852]: <info>  (12147776) ... get_connections (managed=false): return empty list.
Nov 28 16:33:14 Yak NetworkManager[852]: <info>  keyfile: new connection /etc/NetworkManager/system-connections/Auto Ethernet (72bb140b-fd56-490d-8b08-43f24fc06aa0,"Auto Ethernet")
Nov 28 16:33:14 Yak NetworkManager[852]: <info>  keyfile: new connection /etc/NetworkManager/system-connections/Jacqueline (ddfffcea-d8c2-449a-8c13-ac48cda088fa,"Jacqueline")
Nov 28 16:33:14 Yak NetworkManager[852]: <info>  SCPlugin-Ofono: (11893664) ... get_connections.
Nov 28 16:33:14 Yak NetworkManager[852]: <info>  SCPlugin-Ofono: (11893664) connections count: 0
Nov 28 16:33:14 Yak NetworkManager[852]: <info>  get unmanaged devices count: 0
Nov 28 16:33:14 Yak NetworkManager[852]: <info>  monitoring kernel firmware directory '/lib/firmware'.
Nov 28 16:33:14 Yak NetworkManager[852]: <info>  monitoring ifupdown state file '/run/network/ifstate'.
Nov 28 16:33:14 Yak NetworkManager[852]: <info>  rfkill0: found WiFi radio killswitch (at /sys/devices/pci0000:00/0000:00:1c.2/0000:05:00.0/ieee80211/phy0/rfkill0) (driver iwlwifi)
Nov 28 16:33:14 Yak NetworkManager[852]: <info>  Loaded device plugin: NMVxlanFactory (internal)
Nov 28 16:33:14 Yak NetworkManager[852]: <info>  Loaded device plugin: NMVlanFactory (internal)
Nov 28 16:33:14 Yak NetworkManager[852]: <info>  Loaded device plugin: NMVethFactory (internal)
Nov 28 16:33:14 Yak NetworkManager[852]: <info>  Loaded device plugin: NMTunFactory (internal)
Nov 28 16:33:14 Yak NetworkManager[852]: <info>  Loaded device plugin: NMMacvlanFactory (internal)
Nov 28 16:33:14 Yak NetworkManager[852]: <info>  Loaded device plugin: NMInfinibandFactory (internal)
Nov 28 16:33:14 Yak NetworkManager[852]: <info>  Loaded device plugin: NMGreFactory (internal)
Nov 28 16:33:14 Yak NetworkManager[852]: <info>  Loaded device plugin: NMEthernetFactory (internal)
Nov 28 16:33:14 Yak NetworkManager[852]: <info>  Loaded device plugin: NMBridgeFactory (internal)
Nov 28 16:33:14 Yak NetworkManager[852]: <info>  Loaded device plugin: NMBondFactory (internal)
Nov 28 16:33:14 Yak NetworkManager[852]: <info>  Loaded device plugin: NMAtmManager (/usr/lib/x86_64-linux-gnu/NetworkManager/libnm-device-plugin-adsl.so)
Nov 28 16:33:14 Yak NetworkManager[852]: <info>  Loaded device plugin: NMWwanFactory (/usr/lib/x86_64-linux-gnu/NetworkManager/libnm-device-plugin-wwan.so)
Nov 28 16:33:14 Yak NetworkManager[852]: <info>  Loaded device plugin: NMBluezManager (/usr/lib/x86_64-linux-gnu/NetworkManager/libnm-device-plugin-bluetooth.so)
Nov 28 16:33:14 Yak NetworkManager[852]: <info>  Loaded device plugin: NMWifiFactory (/usr/lib/x86_64-linux-gnu/NetworkManager/libnm-device-plugin-wifi.so)
Nov 28 16:33:14 Yak NetworkManager[852]: <info>  WiFi enabled by radio killswitch; enabled by state file
Nov 28 16:33:14 Yak NetworkManager[852]: <info>  WWAN enabled by radio killswitch; enabled by state file
Nov 28 16:33:14 Yak NetworkManager[852]: <info>  WiMAX enabled by radio killswitch; enabled by state file
Nov 28 16:33:14 Yak NetworkManager[852]: <info>  Networking is enabled by state file
Nov 28 16:33:14 Yak NetworkManager[852]: nm_device_get_device_type: assertion 'NM_IS_DEVICE (self)' failed
Nov 28 16:33:14 Yak NetworkManager[852]: <info>  (lo): link connected
Nov 28 16:33:14 Yak NetworkManager[852]: <info>  (lo): new Generic device (carrier: ON, driver: 'unknown', ifindex: 1)
Nov 28 16:33:14 Yak NetworkManager[852]: <info>  (wlp5s0): using nl80211 for WiFi device control
Nov 28 16:33:14 Yak NetworkManager[852]: <info>  (wlp5s0): driver supports Access Point (AP) mode
Nov 28 16:33:14 Yak NetworkManager[852]: <info>  (wlp5s0): new 802.11 WiFi device (carrier: UNKNOWN, driver: 'iwlwifi', ifindex: 3)
Nov 28 16:33:14 Yak NetworkManager[852]: <info>  (wlp5s0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Nov 28 16:33:14 Yak NetworkManager[852]: <info>  (enp0s25): new Ethernet device (carrier: OFF, driver: 'e1000e', ifindex: 2)
Nov 28 16:33:14 Yak NetworkManager[852]: <info>  (enp0s25): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Nov 28 16:33:14 Yak NetworkManager[852]: <info>  keyfile: add connection in-memory (1db669e6-5691-4bdf-9046-5556c1d5a334,"Wired connection 1")
Nov 28 16:33:14 Yak NetworkManager[852]: <info>  (enp0s25): created default wired connection 'Wired connection 1'
Nov 28 16:33:14 Yak NetworkManager[852]: <info>  (enx02000d563537): new Ethernet device (carrier: OFF, driver: 'rndis_host', ifindex: 4)
Nov 28 16:33:14 Yak NetworkManager[852]: <info>  (enx02000d563537): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Nov 28 16:33:14 Yak NetworkManager[852]: <info>  (enx02000d563537): link connected
Nov 28 16:33:14 Yak NetworkManager[852]: <info>  urfkill disappeared from the bus
Nov 28 16:33:14 Yak NetworkManager[852]: <info>  (enx02000d563537): device state change: unavailable -> disconnected (reason 'none') [20 30 0]
Nov 28 16:33:14 Yak NetworkManager[852]: <info>  Device 'enx02000d563537' has no connection; scheduling activate_check in 0 seconds.
Nov 28 16:33:14 Yak NetworkManager[852]: <info>  Auto-activating connection 'Auto Ethernet'.
Nov 28 16:33:14 Yak NetworkManager[852]: <info>  ofono is now available
Nov 28 16:33:14 Yak NetworkManager[852]: <info>  (enx02000d563537): Activation: starting connection 'Auto Ethernet' (72bb140b-fd56-490d-8b08-43f24fc06aa0)
Nov 28 16:33:14 Yak NetworkManager[852]: <info>  (enx02000d563537): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Nov 28 16:33:14 Yak NetworkManager[852]: <info>  NetworkManager state is now CONNECTING
Nov 28 16:33:14 Yak NetworkManager[852]: <warn>  failed to enumerate oFono devices: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.ofono was not provided by any .service files
Nov 28 16:33:14 Yak NetworkManager[852]: <info>  (enx02000d563537): device state change: prepare -> config (reason 'none') [40 50 0]
Nov 28 16:33:14 Yak NetworkManager[852]: <info>  ModemManager available in the bus
Nov 28 16:33:14 Yak NetworkManager[852]: <info>  (enx02000d563537): device state change: config -> ip-config (reason 'none') [50 70 0]
Nov 28 16:33:14 Yak NetworkManager[852]: <info>  Activation (enx02000d563537) Beginning DHCPv4 transaction (timeout in 45 seconds)
Nov 28 16:33:14 Yak NetworkManager[852]: <info>  dhclient started with pid 1070
Nov 28 16:33:14 Yak NetworkManager[852]: <info>  wpa_supplicant running
Nov 28 16:33:14 Yak NetworkManager[852]: <info>    address 192.168.42.189
Nov 28 16:33:14 Yak NetworkManager[852]: <info>    plen 24 (255.255.255.0)
Nov 28 16:33:14 Yak NetworkManager[852]: <info>    gateway 192.168.42.129
Nov 28 16:33:14 Yak NetworkManager[852]: <info>    server identifier 192.168.42.129
Nov 28 16:33:14 Yak NetworkManager[852]: <info>    lease time 3600
Nov 28 16:33:14 Yak NetworkManager[852]: <info>    hostname 'Yak'
Nov 28 16:33:14 Yak NetworkManager[852]: <info>    nameserver '192.168.42.129'
Nov 28 16:33:14 Yak NetworkManager[852]: <info>  (enx02000d563537): DHCPv4 state changed unknown -> bound
Nov 28 16:33:14 Yak NetworkManager[852]: <info>  (enx02000d563537): device state change: ip-config -> ip-check (reason 'none') [70 80 0]
Nov 28 16:33:14 Yak NetworkManager[852]: <info>  (enx02000d563537): device state change: ip-check -> secondaries (reason 'none') [80 90 0]
Nov 28 16:33:14 Yak NetworkManager[852]: <info>  (enx02000d563537): device state change: secondaries -> activated (reason 'none') [90 100 0]
Nov 28 16:33:14 Yak NetworkManager[852]: <info>  NetworkManager state is now CONNECTED_LOCAL
Nov 28 16:33:14 Yak NetworkManager[852]: <info>  NetworkManager state is now CONNECTED_GLOBAL
Nov 28 16:33:14 Yak NetworkManager[852]: <info>  Policy set 'Auto Ethernet' (enx02000d563537) as default for IPv4 routing and DNS.
Nov 28 16:33:14 Yak NetworkManager[852]: <info>  DNS: starting dnsmasq...
Nov 28 16:33:14 Yak NetworkManager[852]: <warn>  dnsmasq not available on the bus, can't update servers.
Nov 28 16:33:14 Yak NetworkManager[852]: <error> [1448724794.852826] [dns-manager/nm-dns-dnsmasq.c:387] update(): dnsmasq owner not found on bus: Could not get owner of name 'org.freedesktop.NetworkManager.dnsmasq': no such name
Nov 28 16:33:14 Yak NetworkManager[852]: <warn>  DNS: plugin dnsmasq update failed
Nov 28 16:33:14 Yak NetworkManager[852]: <info>  Writing DNS information to /sbin/resolvconf
Nov 28 16:33:14 Yak NetworkManager[852]: /etc/resolvconf/update.d/libc: Warning: /etc/resolv.conf is not a symbolic link to /run/resolvconf/resolv.conf
Nov 28 16:33:14 Yak NetworkManager[852]: <info>  (enx02000d563537): Activation: successful, device activated.
Nov 28 16:33:14 Yak NetworkManager[852]: <warn>  dnsmasq appeared on DBus: :1.22
Nov 28 16:33:14 Yak NetworkManager[852]: <info>  Writing DNS information to /sbin/resolvconf
Nov 28 16:33:14 Yak dbus[855]: [system] Rejected send message, 10 matched rules; type="method_return", sender=":1.22" (uid=0 pid=1081 comm="/usr/sbin/dnsmasq --no-resolv --keep-in-foreground") interface="(unset)" member="(unset)" error name="(unset)" requested_reply="0" destination=":1.6" (uid=0 pid=852 comm="/usr/sbin/NetworkManager --no-daemon ")
Nov 28 16:33:14 Yak NetworkManager[852]: /etc/resolvconf/update.d/libc: Warning: /etc/resolv.conf is not a symbolic link to /run/resolvconf/resolv.conf
Nov 28 16:33:14 Yak NetworkManager[852]: <info>  (wlp5s0): supplicant interface state: starting -> ready
Nov 28 16:33:14 Yak NetworkManager[852]: <info>  (wlp5s0): device state change: unavailable -> disconnected (reason 'supplicant-available') [20 30 42]
Nov 28 16:33:14 Yak NetworkManager[852]: <info>  Device 'wlp5s0' has no connection; scheduling activate_check in 0 seconds.
Nov 28 16:33:18 Yak NetworkManager[852]: <info>  (wlp5s0): supplicant interface state: ready -> inactive
Nov 28 16:33:18 Yak NetworkManager[852]: <info>  Auto-activating connection 'Jacqueline'.
Nov 28 16:33:18 Yak NetworkManager[852]: <info>  (wlp5s0): Activation: starting connection 'Jacqueline' (ddfffcea-d8c2-449a-8c13-ac48cda088fa)
Nov 28 16:33:18 Yak NetworkManager[852]: <info>  (wlp5s0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Nov 28 16:33:18 Yak NetworkManager[852]: <info>  (wlp5s0): device state change: prepare -> config (reason 'none') [40 50 0]
Nov 28 16:33:18 Yak NetworkManager[852]: <info>  (wlp5s0): Activation: (wifi) connection 'Jacqueline' has security, and secrets exist.  No new secrets needed.
Nov 28 16:33:18 Yak NetworkManager[852]: <info>  Config: added 'ssid' value 'Jacqueline'
Nov 28 16:33:18 Yak NetworkManager[852]: <info>  Config: added 'scan_ssid' value '1'
Nov 28 16:33:18 Yak NetworkManager[852]: <info>  Config: added 'key_mgmt' value 'WPA-PSK'
Nov 28 16:33:18 Yak NetworkManager[852]: <info>  Config: added 'auth_alg' value 'OPEN'
Nov 28 16:33:18 Yak NetworkManager[852]: <info>  Config: added 'psk' value '<omitted>'
Nov 28 16:33:18 Yak NetworkManager[852]: <info>  Config: set interface ap_scan to 1
Nov 28 16:33:18 Yak NetworkManager[852]: <info>  (wlp5s0): supplicant interface state: inactive -> associating
Nov 28 16:33:18 Yak NetworkManager[852]: <info>  (wlp5s0): supplicant interface state: associating -> completed
Nov 28 16:33:18 Yak NetworkManager[852]: <info>  (wlp5s0): Activation: (wifi) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'Jacqueline'.
Nov 28 16:33:18 Yak NetworkManager[852]: <info>  (wlp5s0): device state change: config -> ip-config (reason 'none') [50 70 0]
Nov 28 16:33:18 Yak NetworkManager[852]: <info>  Activation (wlp5s0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Nov 28 16:33:18 Yak NetworkManager[852]: <info>  dhclient started with pid 1958
Nov 28 16:33:18 Yak NetworkManager[852]: <info>    address 192.168.1.32
Nov 28 16:33:18 Yak NetworkManager[852]: <info>    plen 24 (255.255.255.0)
Nov 28 16:33:18 Yak NetworkManager[852]: <info>    gateway 192.168.1.254
Nov 28 16:33:18 Yak NetworkManager[852]: <info>    server identifier 192.168.1.254
Nov 28 16:33:18 Yak NetworkManager[852]: <info>    lease time 43200
Nov 28 16:33:18 Yak NetworkManager[852]: <info>    nameserver '8.8.8.8'
Nov 28 16:33:18 Yak NetworkManager[852]: <info>    nameserver '192.168.1.254'
Nov 28 16:33:18 Yak NetworkManager[852]: <info>  (wlp5s0): DHCPv4 state changed unknown -> bound
Nov 28 16:33:18 Yak NetworkManager[852]: <info>  (wlp5s0): device state change: ip-config -> ip-check (reason 'none') [70 80 0]
Nov 28 16:33:18 Yak NetworkManager[852]: <info>  (wlp5s0): device state change: ip-check -> secondaries (reason 'none') [80 90 0]
Nov 28 16:33:18 Yak NetworkManager[852]: <info>  (wlp5s0): device state change: secondaries -> activated (reason 'none') [90 100 0]
Nov 28 16:33:18 Yak NetworkManager[852]: <info>  Writing DNS information to /sbin/resolvconf
Nov 28 16:33:18 Yak dbus[855]: [system] Rejected send message, 10 matched rules; type="method_return", sender=":1.22" (uid=0 pid=1081 comm="/usr/sbin/dnsmasq --no-resolv --keep-in-foreground") interface="(unset)" member="(unset)" error name="(unset)" requested_reply="0" destination=":1.6" (uid=0 pid=852 comm="/usr/sbin/NetworkManager --no-daemon ")
Nov 28 16:33:18 Yak NetworkManager[852]: <info>  (wlp5s0): Activation: successful, device activated.
Nov 28 16:33:19 Yak NetworkManager[852]: <info>  startup complete
Nov 28 16:33:19 Yak NetworkManager[852]: <info>  Policy set 'Jacqueline' (wlp5s0) as default for IPv6 routing and DNS.
Nov 28 16:33:19 Yak NetworkManager[852]: <info>  Writing DNS information to /sbin/resolvconf
Nov 28 16:33:19 Yak dbus[855]: [system] Rejected send message, 10 matched rules; type="method_return", sender=":1.22" (uid=0 pid=1081 comm="/usr/sbin/dnsmasq --no-resolv --keep-in-foreground") interface="(unset)" member="(unset)" error name="(unset)" requested_reply="0" destination=":1.6" (uid=0 pid=852 comm="/usr/sbin/NetworkManager --no-daemon ")
Nov 28 16:33:24 Yak NetworkManager[852]: <info>  WiFi hardware radio set enabled
Nov 28 16:33:24 Yak NetworkManager[852]: <info>  WWAN hardware radio set enabled

```
journalctl -a |grep 1068
```
Nov 28 16:33:14 Yak wpa_supplicant[1068]: Successfully initialized wpa_supplicant
Nov 28 16:33:14 Yak wpa_supplicant[1068]: dbus: wpa_dbus_get_object_properties: failed to get object properties: (none) none
Nov 28 16:33:14 Yak wpa_supplicant[1068]: dbus: Failed to construct signal
Nov 28 16:33:14 Yak wpa_supplicant[1068]: Could not read interface p2p-dev-wlp5s0 flags: No such device
Nov 28 16:33:18 Yak wpa_supplicant[1068]: wlp5s0: SME: Trying to authenticate with f4:ca:e5:f4:e8:64 (SSID='Jacqueline' freq=2412 MHz)
Nov 28 16:33:18 Yak wpa_supplicant[1068]: wlp5s0: Trying to associate with f4:ca:e5:f4:e8:64 (SSID='Jacqueline' freq=2412 MHz)
Nov 28 16:33:18 Yak wpa_supplicant[1068]: wlp5s0: Associated with f4:ca:e5:f4:e8:64
Nov 28 16:33:18 Yak wpa_supplicant[1068]: wlp5s0: WPA: Key negotiation completed with f4:ca:e5:f4:e8:64 [PTK=CCMP GTK=CCMP]
Nov 28 16:33:18 Yak wpa_supplicant[1068]: wlp5s0: CTRL-EVENT-CONNECTED - Connection to f4:ca:e5:f4:e8:64 completed [id=0 id_str=]

---

### Post by zakrapovic on 2015-11-28
Soled it :) !

Thanks to the journalctl that oriented me to DNS issue and this thread : [http://ubuntuforums.org/showthread.php?t=2227955](http://ubuntuforums.org/showthread.php?t=2227955)

Thanks for helping

---

