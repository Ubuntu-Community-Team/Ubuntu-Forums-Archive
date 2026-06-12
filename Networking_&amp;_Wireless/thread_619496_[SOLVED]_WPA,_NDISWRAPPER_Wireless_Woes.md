---
title: "[SOLVED] WPA, NDISWRAPPER Wireless Woes"
date: 2007-11-21
forum: Networking &amp; Wireless
---

### Post by lvleph on 2007-11-21
I have been trying to get my wifi to work on 7.04. I have a gateway mt3705. This has the infamous realtek wireless. I used ndiswrapper as per [these instruction](http://ubuntuforums.org/showpost.php?p=3397386&postcount=13). This seemed to work, except that I use WPA. So I followed [these instructions](http://ubuntuforums.org/showthread.php?t=263136&highlight=wpa) next. Once, I completed those instruction I have not been able to see my wireless connection in the network manager. Can someone please help me? Below are my outputs for lspci, ndiswrapper -l, interfaces file, wpa-supplicant, and sudo wpa_supplicant -w -Dndiswrapper -i wlan0 -c/etc/wpa_supplicant.conf -dd. If anything else is needed please let me know.


**lspci**
```
00:00.0 Host bridge: ATI Technologies Inc Unknown device 5a31 (rev 01)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:04.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:05.0 PCI bridge: ATI Technologies Inc Unknown device 5a37
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 83)
00:14.1 IDE interface: ATI Technologies Inc Standard Dual Channel PCI IDE Controller ATI (rev 80)
00:14.2 Audio device: ATI Technologies Inc SB450 HDA Audio (rev 01)
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)
01:05.0 VGA compatible controller: ATI Technologies Inc RC410 [Radeon Xpress 200M]
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8038 PCI-E Fast Ethernet Controller (rev 14)
08:09.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller (rev 20)
```

**ndiswrapper -l**
```
net8185 : driver installed
        device (10EC:8185) present (alternate driver: r818x)
```

**iwconfig**
```
lo        no wireless extensions.

eth0      no wireless extensions.
```


**/etc/network/interfaces**
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet dhcp
pre-up wpa_supplicant -Bw -Dndiswrapper -iwlan0 -c/etc/wpa_supplicant.conf
post-down killall -q wpa_supplicant
```

**/etc/wpa-suplicant.conf**
```
ctrl_interface=/var/run/wpa_supplicant
#ap_scan=2

network={
       ssid=<removed>
       scan_ssid=1
       key_mgmt=WPA-PSK
       proto=WPA
       psk=<<removed>
}
```

**sudo wpa_supplicant -w -Dndiswrapper -i wlan0 -c/etc/wpa_supplicant.conf -dd**
```
Initializing interface 'wlan0' conf '/etc/wpa_supplicant.conf' driver 'ndiswrapper' ctrl_interface 'N/A' bridge 'N/A'
Configuration file '/etc/wpa_supplicant.conf' -> '/etc/wpa_supplicant.conf'
Reading configuration file '/etc/wpa_supplicant.conf'
ctrl_interface='/var/run/wpa_supplicant'
Line: 4 - start of a new network block
ssid - hexdump_ascii(len=6):
     46 6f 73 74 65 72                                 <removed>      
scan_ssid=1 (0x1)
key_mgmt: 0x2
proto: 0x1
PSK - hexdump(len=32): [REMOVED]
Priority group 0
   id=0 ssid=<removed>
Initializing interface (2) 'wlan0'
EAPOL: SUPP_PAE entering state DISCONNECTED
EAPOL: KEY_RX entering state NO_KEY_RECEIVE
EAPOL: SUPP_BE entering state INITIALIZE
EAP: EAP entering state DISABLED
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
ioctl[SIOCSIWPMKSA]: No such device
ioctl[SIOCSIWMODE]: No such device
Could not configure driver to use managed mode
ioctl[SIOCGIFFLAGS]: No such device
Could not set interface 'wlan0' UP
ioctl[SIOCGIWRANGE]: No such device
WEXT: Operstate: linkmode=1, operstate=5
ioctl[SIOCGIFINDEX]: No such device
Waiting for interface..
ioctl[SIOCGIFINDEX]: No such device
Waiting for interface..
```

---

### Post by MaximusTG on 2007-11-21
I think you need to use the wext driver instead of the ndiswrapper one in your wpa_supplicant command

so 

-Dwext instead of -Dndiswrapper

---

### Post by lvleph on 2007-11-21
Yeah, I tried that and here are the results.

**sudo wpa_supplicant -w -Dwext -i wlan0 -c/etc/wpa_supplicant.conf -dd**
```
Initializing interface 'wlan0' conf '/etc/wpa_supplicant.conf' driver 'wext' ctrl_interface 'N/A' bridge 'N/A'
Configuration file '/etc/wpa_supplicant.conf' -> '/etc/wpa_supplicant.conf'
Reading configuration file '/etc/wpa_supplicant.conf'
ctrl_interface='/var/run/wpa_supplicant'
Line: 4 - start of a new network block
ssid - hexdump_ascii(len=6):
     46 6f 73 74 65 72                                 <removed>          
scan_ssid=1 (0x1)
key_mgmt: 0x2
proto: 0x1
PSK - hexdump(len=32): [REMOVED]
Priority group 0
   id=0 ssid=<removed>
Initializing interface (2) 'wlan0'
EAPOL: SUPP_PAE entering state DISCONNECTED
EAPOL: KEY_RX entering state NO_KEY_RECEIVE
EAPOL: SUPP_BE entering state INITIALIZE
EAP: EAP entering state DISABLED
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
ioctl[SIOCSIWPMKSA]: No such device
ioctl[SIOCSIWMODE]: No such device
Could not configure driver to use managed mode
ioctl[SIOCGIFFLAGS]: No such device
Could not set interface 'wlan0' UP
ioctl[SIOCGIWRANGE]: No such device
WEXT: Operstate: linkmode=1, operstate=5
ioctl[SIOCGIFINDEX]: No such device
Waiting for interface..
ioctl[SIOCGIFINDEX]: No such device
Waiting for interface..
```

The issue seems to be that my wifi is not detected by the network manager any more. And I cannot figure out how to fix that. I am not even sure what I did to get rid of it. But if I go to administration>network the wireless is not even shown anymore, whereas it use to show before I tried the WPA stuff.

---

### Post by MaximusTG on 2007-11-21
Ah okay, I see what you mean. Well I know that if you use wpa_supplicant directly you bypass network-manager (which uses wpa_supplicant internally) so you should focus on getting ndiswrapper recognized by network-manager.

There maybe more to it, but you should know that the configuration via the System-> administration-> network is not related to network-manager. And if you configure the interface in /etc/network/interfaces network-manager won't see it.

So remove everything related to wlan0 from your /etc/network/interfaces file, and it should work (could require a reboot).
You can also put #'s before the relevant lines in that file, so you can still go back to that situation.

---

### Post by lvleph on 2007-11-21
Yeah, I had made a backup of my original interfaces file and restored that, but my wireless did not show back up.

---

### Post by lvleph on 2007-11-21
Okay, so I changed everything to eth0 instead of wlan0.

**interfaces**
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp
pre-up wpa_supplicant -Bw -Dwext -ieth0 -c/etc/wpa_supplicant.conf
post-down killall -q wpa_supplicant
```

**sudo wpa_supplicant -w -Dwext -i eth0 -c/etc/wpa_supplicant.conf -dd**
```
Initializing interface 'eth0' conf '/etc/wpa_supplicant.conf' driver 'wext' ctrl_interface 'N/A' bridge 'N/A'
Configuration file '/etc/wpa_supplicant.conf' -> '/etc/wpa_supplicant.conf'
Reading configuration file '/etc/wpa_supplicant.conf'
ctrl_interface='/var/run/wpa_supplicant'
Line: 4 - start of a new network block
ssid - hexdump_ascii(len=6):
     46 6f 73 74 65 72                                 <removed>          
scan_ssid=1 (0x1)
key_mgmt: 0x2
proto: 0x1
PSK - hexdump(len=32): [REMOVED]
Priority group 0
   id=0 ssid=<removed>
Initializing interface (2) 'eth0'
EAPOL: SUPP_PAE entering state DISCONNECTED
EAPOL: KEY_RX entering state NO_KEY_RECEIVE
EAPOL: SUPP_BE entering state INITIALIZE
EAP: EAP entering state DISABLED
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
ioctl[SIOCSIWMODE]: Operation not supported
Could not configure driver to use managed mode
ioctl[SIOCGIWRANGE]: Operation not supported
WEXT: Operstate: linkmode=1, operstate=5
Own MAC address: 00:03:25:3f:b1:e6
wpa_driver_wext_set_wpa
ioctl[SIOCSIWAUTH]: Operation not supported
WEXT auth param 7 value 0x1 - **Driver does not support WPA.**
wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0
```

So it seems that my driver does not support WPA, but I use WPA under windows and this is a windows driver that I used ndiswrapper on. I am so confused.

---

### Post by kevdog on 2007-11-21
Can you post lshw -C network

---

### Post by lvleph on 2007-11-21
Okay, now my wired doesn't want to work. I can see it in the network manager, but it will not connect to anything. Rather, it says it is connected, but I cannot connect to any websites.

**lshw -C network**
```
  *-network               
       description: Ethernet interface
       product: 88E8038 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@02:00.0
       logical name: eth0
       version: 14
       serial: 00:03:25:3f:b1:e6
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.13 duplex=full firmware=N/A ip=192.168.15.102 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: iomemory:c0100000-c0103fff ioport:a000-a0ff irq:17
  *-network UNCLAIMED
       description: Ethernet controller
       product: RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 9
       bus info: pci@08:09.0
       version: 20
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=64 maxlatency=64 mingnt=32
       resources: ioport:b000-b0ff iomemory:c0200000-c02001ff irq:11
```

So what is the deal there? The wireless doesn't have a logical name?

Edit: Wired works again.

---

### Post by kevdog on 2007-11-21
The wireless interface doesnt have a driver assigned to it either -- hence the UNCLAIMED statement.  Im not sure what you did initially to get your wireless up and running -- as far as configuring a driver, but I would go ahead and repeat the steps.  WPA doesnt work with wired interfaces.

---

### Post by lvleph on 2007-11-21
I realize wpa doesn't work with wired. I tried to redo the ndiswrapper to get my wireless back up, but it didn't fix the problem. I now have no wired again. I get an error saying something along the lines of not being able to load Hal, when I log in. I may just start from scratch again. This will be the second time.

---

### Post by kevdog on 2007-11-21
You can reinstall if you want, but I doubt that is necessary.  Are you find HAL errors in dmesg?? Sometimes the grub boot entry needs to be modified to add noacpi or similar to avoid these errors.  Its really hard to know right now since you aren't providing any specific output.

---

### Post by lvleph on 2007-11-22
Well, I get a pop up right after I log in that says, "Internal Error Failed to initialize HAL!"

I don't want to reinstall, because that would mean I would have to reinstall the packages I have working and would have to get my sound working again.

---

### Post by lvleph on 2007-11-22
**sudo /etc/init.d/dbus restart**
```

 * Stopping System Tools Backends system-tools-backends                  [ OK ] 
 * Stopping network events dispatcher NetworkManagerDispatcher           [ OK ] 
 * Stopping Avahi mDNS/DNS-SD Daemon: avahi-daemon                       [ OK ] 
 * Stopping network connection manager NetworkManager                    [ OK ] 
 * Stopping DHCP D-Bus daemon dhcdbd                                     [ OK ] 
 * Stopping Hardware abstraction layer hald                              [ OK ] 
 * Stopping system message bus dbus                                      [ OK ] 
 * Starting system message bus dbus                                      [ OK ] 
 * Starting Hardware abstraction layer hald                                     run-parts: /etc/dbus-1/event.d/20hal exited with return code 1
 * Starting DHCP D-Bus daemon dhcdbd                                     [ OK ] 
 * Starting network connection manager NetworkManager                    [ OK ] 
 * Starting Avahi mDNS/DNS-SD Daemon: avahi-daemon                       [ OK ] 
 * Starting network events dispatcher NetworkManagerDispatcher           [ OK ] 
 * Starting System Tools Backends system-tools-backends                  [ OK ]
```

**daemon.log**
```
Nov 21 12:01:56 ubuntu gdm[5252]: Restarting computer...
Nov 21 12:01:57 ubuntu hald: unmounted /dev/sda1 from '/media/disk' on behalf of uid 1000
Nov 21 12:01:59 ubuntu init: tty5 main process (4606) killed by TERM signal
Nov 21 12:01:59 ubuntu init: tty3 main process (4610) killed by TERM signal
Nov 21 12:01:59 ubuntu init: tty1 main process (4612) killed by TERM signal
Nov 21 12:01:59 ubuntu init: tty6 main process (4613) killed by TERM signal
Nov 21 12:01:59 ubuntu init: tty2 main process (4608) killed by TERM signal
Nov 21 12:01:59 ubuntu init: tty4 main process (4605) killed by TERM signal
Nov 21 12:03:46 ubuntu NetworkManager: <information>^Istarting... 
Nov 21 12:03:46 ubuntu NetworkManager: <information>^Ieth0: Device is fully-supported using driver 'sky2'. 
Nov 21 12:03:46 ubuntu NetworkManager: <information>^Inm_device_init(): waiting for device's worker thread to start 
Nov 21 12:03:46 ubuntu NetworkManager: <information>^Inm_device_init(): device's worker thread started, continuing. 
Nov 21 12:03:46 ubuntu NetworkManager: <information>^INow managing wired Ethernet (802.3) device 'eth0'. 
Nov 21 12:03:46 ubuntu NetworkManager: <information>^IDeactivating device eth0. 
Nov 21 12:03:46 ubuntu avahi-daemon[5269]: Found user 'avahi' (UID 105) and group 'avahi' (GID 111).
Nov 21 12:03:46 ubuntu avahi-daemon[5269]: Successfully dropped root privileges.
Nov 21 12:03:46 ubuntu avahi-daemon[5269]: avahi-daemon 0.6.17 starting up.
Nov 21 12:03:46 ubuntu avahi-daemon[5269]: Successfully called chroot().
Nov 21 12:03:46 ubuntu avahi-daemon[5269]: Successfully dropped remaining capabilities.
Nov 21 12:03:46 ubuntu avahi-daemon[5269]: No service found in /etc/avahi/services.
Nov 21 12:03:46 ubuntu avahi-daemon[5269]: Network interface enumeration completed.
Nov 21 12:03:46 ubuntu avahi-daemon[5269]: Registering HINFO record with values 'I686'/'LINUX'.
Nov 21 12:03:46 ubuntu avahi-daemon[5269]: Server startup complete. Host name is ubuntu.local. Local service cookie is 3661274557.
Nov 21 12:03:48 ubuntu NetworkManager: <information>^IWill activate wired connection 'eth0' because it now has a link. 
Nov 21 12:03:48 ubuntu NetworkManager: <information>^ISWITCH: no current connection, found better connection 'eth0'. 
Nov 21 12:03:49 ubuntu NetworkManager: <information>^IWill activate connection 'eth0'. 
Nov 21 12:03:49 ubuntu NetworkManager: <information>^IDevice eth0 activation scheduled... 
Nov 21 12:03:49 ubuntu NetworkManager: <information>^IActivation (eth0) started... 
Nov 21 12:03:49 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 1 of 5 (Device Prepare) scheduled... 
Nov 21 12:03:50 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 1 of 5 (Device Prepare) started... 
Nov 21 12:03:50 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 2 of 5 (Device Configure) scheduled... 
Nov 21 12:03:50 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 1 of 5 (Device Prepare) complete. 
Nov 21 12:03:50 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 2 of 5 (Device Configure) starting... 
Nov 21 12:03:50 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 2 of 5 (Device Configure) successful. 
Nov 21 12:03:50 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 3 of 5 (IP Configure Start) scheduled. 
Nov 21 12:03:50 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 2 of 5 (Device Configure) complete. 
Nov 21 12:03:50 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 3 of 5 (IP Configure Start) started... 
Nov 21 12:03:50 ubuntu NetworkManager: <information>^IActivation (eth0) Beginning DHCP transaction. 
Nov 21 12:03:51 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 3 of 5 (IP Configure Start) complete. 
Nov 21 12:03:51 ubuntu NetworkManager: <information>^IDHCP daemon state is now 12 (successfully started) for interface eth0 
Nov 21 12:03:51 ubuntu hcid[5524]: Bluetooth HCI daemon
Nov 21 12:03:52 ubuntu hcid[5524]: Starting SDP server
Nov 21 12:03:52 ubuntu NetworkManager: <debug info>^I[1195664630.751249] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_bluetooth'). 
Nov 21 12:03:52 ubuntu NetworkManager: <information>^IDHCP daemon state is now 1 (starting) for interface eth0 
Nov 21 12:03:53 ubuntu dhclient: isc-dhclient-V3.0.4
Nov 21 12:03:55 ubuntu dhclient: DHCPREQUEST on eth0 to 255.255.255.255 port 67
Nov 21 12:03:55 ubuntu dhclient: DHCPACK from 192.168.15.1
Nov 21 12:03:55 ubuntu avahi-daemon[5269]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.15.102.
Nov 21 12:03:55 ubuntu avahi-daemon[5269]: New relevant interface eth0.IPv4 for mDNS.
Nov 21 12:03:55 ubuntu avahi-daemon[5269]: Registering new address record for 192.168.15.102 on eth0.IPv4.
Nov 21 12:03:55 ubuntu NetworkManager: <information>^IDHCP daemon state is now 4 (reboot) for interface eth0 
Nov 21 12:03:55 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 4 of 5 (IP Configure Get) scheduled... 
Nov 21 12:03:55 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 4 of 5 (IP Configure Get) started... 
Nov 21 12:03:55 ubuntu NetworkManager: <information>^IRetrieved the following IP4 configuration from the DHCP daemon: 
Nov 21 12:03:55 ubuntu NetworkManager: <information>^I  address 192.168.15.102 
Nov 21 12:03:55 ubuntu NetworkManager: <information>^I  netmask 255.255.255.0 
Nov 21 12:03:55 ubuntu NetworkManager: <information>^I  broadcast 192.168.15.255 
Nov 21 12:03:55 ubuntu dhclient: bound to 192.168.15.102 -- renewal in 42961 seconds.
Nov 21 12:03:55 ubuntu NetworkManager: <information>^I  gateway 192.168.15.1 
Nov 21 12:03:55 ubuntu NetworkManager: <information>^I  nameserver 192.168.15.1 
Nov 21 12:03:55 ubuntu NetworkManager: <information>^I  hostname 'ubuntu' 
Nov 21 12:03:55 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 5 of 5 (IP Configure Commit) scheduled... 
Nov 21 12:03:55 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 4 of 5 (IP Configure Get) complete. 
Nov 21 12:03:55 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 5 of 5 (IP Configure Commit) started... 
Nov 21 12:03:55 ubuntu avahi-daemon[5269]: Withdrawing address record for 192.168.15.102 on eth0.
Nov 21 12:03:55 ubuntu avahi-daemon[5269]: Leaving mDNS multicast group on interface eth0.IPv4 with address 192.168.15.102.
Nov 21 12:03:55 ubuntu avahi-daemon[5269]: Interface eth0.IPv4 no longer relevant for mDNS.
Nov 21 12:03:55 ubuntu avahi-daemon[5269]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.15.102.
Nov 21 12:03:55 ubuntu avahi-daemon[5269]: New relevant interface eth0.IPv4 for mDNS.
Nov 21 12:03:55 ubuntu avahi-daemon[5269]: Registering new address record for 192.168.15.102 on eth0.IPv4.
Nov 21 12:03:56 ubuntu NetworkManager: <information>^IClearing nscd hosts cache. 
Nov 21 12:03:56 ubuntu NetworkManager: <WARNING>^I nm_spawn_process (): nm_spawn_process('/usr/sbin/nscd -i hosts'): could not spawn process. (Failed to execute child process "/usr/sbin/nscd" (No such file or directory))  
Nov 21 12:03:56 ubuntu NetworkManager: <information>^IActivation (eth0) Finish handler scheduled. 
Nov 21 12:03:56 ubuntu NetworkManager: <information>^IActivation (eth0) successful, device activated. 
Nov 21 12:03:56 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 5 of 5 (IP Configure Commit) complete. 
Nov 21 12:03:58 ubuntu avahi-daemon[5269]: Registering new address record for fe80::203:25ff:fe3f:b1e6 on eth0.*.
Nov 21 12:04:07 ubuntu ntpdate[5810]: adjust time server 91.189.94.4 offset -0.348671 sec
Nov 21 12:04:28 ubuntu hald: mounted /dev/sda1 on behalf of uid 1000
Nov 21 12:04:30 ubuntu NetworkManager: <information>^IUpdating allowed wireless network lists. 
Nov 21 12:04:30 ubuntu NetworkManager: <WARNING>^I nm_dbus_get_networks_cb (): error received: org.freedesktop.NetworkManagerInfo.NoNetworks - There are no wireless networks stored.. 
Nov 21 12:58:55 ubuntu hald: unmounted /dev/sda1 from '/media/disk' on behalf of uid 1000
Nov 21 12:58:56 ubuntu NetworkManager: <debug info>^I[1195667936.151013] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_352D_1380'). 
Nov 21 12:58:58 ubuntu NetworkManager: <debug info>^I[1195667937.161903] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_718_65_AA0070006371905A_if0_scsi_device_lun0_scsi_generic'). 
Nov 21 12:58:58 ubuntu NetworkManager: <debug info>^I[1195667937.166127] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_718_65_AA0070006371905A_if0_scsi_device_lun0'). 
Nov 21 12:58:58 ubuntu NetworkManager: <debug info>^I[1195667937.168123] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_718_65_AA0070006371905A_if0_scsi_host'). 
Nov 21 12:58:58 ubuntu NetworkManager: <debug info>^I[1195667937.171640] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_718_65_AA0070006371905A_if0'). 
Nov 21 12:58:58 ubuntu NetworkManager: <debug info>^I[1195667937.174119] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_718_65_AA0070006371905A'). 
Nov 21 12:58:58 ubuntu NetworkManager: <debug info>^I[1195667937.648101] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/storage_serial_Imation_USB_Flash_Drive_AA0070006371905A_0_0'). 
Nov 21 12:58:58 ubuntu NetworkManager: <debug info>^I[1195667938.159804] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_718_65_AA0070006371905A_usbraw'). 
Nov 21 13:05:15 ubuntu NetworkManager: <debug info>^I[1195668315.294922] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/net_00_c0_a8_d0_e4_e0'). 
Nov 21 13:05:15 ubuntu NetworkManager: <information>^Iwlan0: Device is fully-supported using driver 'ndiswrapper'. 
Nov 21 13:05:15 ubuntu NetworkManager: <information>^Inm_device_init(): waiting for device's worker thread to start 
Nov 21 13:05:15 ubuntu NetworkManager: <information>^Inm_device_init(): device's worker thread started, continuing. 
Nov 21 13:05:15 ubuntu NetworkManager: <information>^INow managing wireless (802.11) device 'wlan0'. 
Nov 21 13:05:15 ubuntu NetworkManager: <information>^IDeactivating device wlan0. 
Nov 21 13:05:15 ubuntu NetworkManager: <WARNING>^I nm_device_802_11_wireless_set_essid (): error setting ESSID to '' for device wlan0: Invalid argument 
Nov 21 13:05:19 ubuntu avahi-daemon[5269]: Registering new address record for fe80::2c0:a8ff:fed0:e4e0 on wlan0.*.
Nov 21 13:07:41 ubuntu gdm[5320]: Restarting computer...
Nov 21 13:07:44 ubuntu init: tty4 main process (4678) killed by TERM signal
Nov 21 13:07:44 ubuntu init: tty5 main process (4679) killed by TERM signal
Nov 21 13:07:44 ubuntu init: tty2 main process (4681) killed by TERM signal
Nov 21 13:07:44 ubuntu init: tty3 main process (4683) killed by TERM signal
Nov 21 13:07:44 ubuntu init: tty1 main process (4685) killed by TERM signal
Nov 21 13:07:44 ubuntu init: tty6 main process (4686) killed by TERM signal
Nov 21 13:09:27 ubuntu NetworkManager: <information>^Istarting... 
Nov 21 13:09:27 ubuntu NetworkManager: <information>^Ieth0: Device is fully-supported using driver 'sky2'. 
Nov 21 13:09:27 ubuntu avahi-daemon[5201]: Found user 'avahi' (UID 105) and group 'avahi' (GID 111).
Nov 21 13:09:27 ubuntu NetworkManager: <information>^Inm_device_init(): waiting for device's worker thread to start 
Nov 21 13:09:27 ubuntu avahi-daemon[5201]: Successfully dropped root privileges.
Nov 21 13:09:27 ubuntu NetworkManager: <information>^Inm_device_init(): device's worker thread started, continuing. 
Nov 21 13:09:27 ubuntu avahi-daemon[5201]: avahi-daemon 0.6.17 starting up.
Nov 21 13:09:27 ubuntu NetworkManager: <information>^INow managing wired Ethernet (802.3) device 'eth0'. 
Nov 21 13:09:27 ubuntu avahi-daemon[5201]: Successfully called chroot().
Nov 21 13:09:27 ubuntu NetworkManager: <information>^IDeactivating device eth0. 
Nov 21 13:09:27 ubuntu avahi-daemon[5201]: Successfully dropped remaining capabilities.
Nov 21 13:09:27 ubuntu avahi-daemon[5201]: No service found in /etc/avahi/services.
Nov 21 13:09:27 ubuntu avahi-daemon[5201]: Network interface enumeration completed.
Nov 21 13:09:27 ubuntu avahi-daemon[5201]: Registering HINFO record with values 'I686'/'LINUX'.
Nov 21 13:09:27 ubuntu avahi-daemon[5201]: Server startup complete. Host name is ubuntu.local. Local service cookie is 3822770920.
Nov 21 13:09:29 ubuntu NetworkManager: <information>^IWill activate wired connection 'eth0' because it now has a link. 
Nov 21 13:09:29 ubuntu NetworkManager: <information>^ISWITCH: no current connection, found better connection 'eth0'. 
Nov 21 13:09:30 ubuntu NetworkManager: <information>^IWill activate connection 'eth0'. 
Nov 21 13:09:30 ubuntu NetworkManager: <information>^IDevice eth0 activation scheduled... 
Nov 21 13:09:30 ubuntu NetworkManager: <information>^IActivation (eth0) started... 
Nov 21 13:09:31 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 1 of 5 (Device Prepare) scheduled... 
Nov 21 13:09:31 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 1 of 5 (Device Prepare) started... 
Nov 21 13:09:31 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 2 of 5 (Device Configure) scheduled... 
Nov 21 13:09:31 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 1 of 5 (Device Prepare) complete. 
Nov 21 13:09:31 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 2 of 5 (Device Configure) starting... 
Nov 21 13:09:32 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 2 of 5 (Device Configure) successful. 
Nov 21 13:09:32 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 3 of 5 (IP Configure Start) scheduled. 
Nov 21 13:09:32 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 2 of 5 (Device Configure) complete. 
Nov 21 13:09:32 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 3 of 5 (IP Configure Start) started... 
Nov 21 13:09:33 ubuntu NetworkManager: <information>^IActivation (eth0) Beginning DHCP transaction. 
Nov 21 13:09:33 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 3 of 5 (IP Configure Start) complete. 
Nov 21 13:09:34 ubuntu NetworkManager: <information>^IDHCP daemon state is now 12 (successfully started) for interface eth0 
Nov 21 13:09:34 ubuntu hcid[5460]: Bluetooth HCI daemon
Nov 21 13:09:34 ubuntu NetworkManager: <debug info>^I[1195668572.413562] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_bluetooth'). 
Nov 21 13:09:34 ubuntu hcid[5460]: Starting SDP server
Nov 21 13:09:34 ubuntu dhclient: isc-dhclient-V3.0.4
Nov 21 13:09:34 ubuntu NetworkManager: <information>^IDHCP daemon state is now 1 (starting) for interface eth0 
Nov 21 13:09:36 ubuntu dhclient: DHCPREQUEST on eth0 to 255.255.255.255 port 67
Nov 21 13:09:36 ubuntu dhclient: DHCPACK from 192.168.15.1
Nov 21 13:09:36 ubuntu avahi-daemon[5201]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.15.102.
Nov 21 13:09:36 ubuntu avahi-daemon[5201]: New relevant interface eth0.IPv4 for mDNS.
Nov 21 13:09:36 ubuntu avahi-daemon[5201]: Registering new address record for 192.168.15.102 on eth0.IPv4.
Nov 21 13:09:36 ubuntu NetworkManager: <information>^IDHCP daemon state is now 4 (reboot) for interface eth0 
Nov 21 13:09:36 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 4 of 5 (IP Configure Get) scheduled... 
Nov 21 13:09:36 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 4 of 5 (IP Configure Get) started... 
Nov 21 13:09:36 ubuntu NetworkManager: <information>^IRetrieved the following IP4 configuration from the DHCP daemon: 
Nov 21 13:09:36 ubuntu NetworkManager: <information>^I  address 192.168.15.102 
Nov 21 13:09:36 ubuntu NetworkManager: <information>^I  netmask 255.255.255.0 
Nov 21 13:09:36 ubuntu dhclient: bound to 192.168.15.102 -- renewal in 36190 seconds.
Nov 21 13:09:36 ubuntu NetworkManager: <information>^I  broadcast 192.168.15.255 
Nov 21 13:09:36 ubuntu NetworkManager: <information>^I  gateway 192.168.15.1 
Nov 21 13:09:36 ubuntu NetworkManager: <information>^I  nameserver 192.168.15.1 
Nov 21 13:09:36 ubuntu NetworkManager: <information>^I  hostname 'ubuntu' 
Nov 21 13:09:36 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 5 of 5 (IP Configure Commit) scheduled... 
Nov 21 13:09:37 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 4 of 5 (IP Configure Get) complete. 
Nov 21 13:09:37 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 5 of 5 (IP Configure Commit) started... 
Nov 21 13:09:37 ubuntu avahi-daemon[5201]: Withdrawing address record for 192.168.15.102 on eth0.
Nov 21 13:09:37 ubuntu avahi-daemon[5201]: Leaving mDNS multicast group on interface eth0.IPv4 with address 192.168.15.102.
Nov 21 13:09:37 ubuntu avahi-daemon[5201]: Interface eth0.IPv4 no longer relevant for mDNS.
Nov 21 13:09:37 ubuntu avahi-daemon[5201]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.15.102.
Nov 21 13:09:37 ubuntu avahi-daemon[5201]: New relevant interface eth0.IPv4 for mDNS.
Nov 21 13:09:37 ubuntu avahi-daemon[5201]: Registering new address record for 192.168.15.102 on eth0.IPv4.
Nov 21 13:09:37 ubuntu NetworkManager: <information>^IClearing nscd hosts cache. 
Nov 21 13:09:37 ubuntu NetworkManager: <WARNING>^I nm_spawn_process (): nm_spawn_process('/usr/sbin/nscd -i hosts'): could not spawn process. (Failed to execute child process "/usr/sbin/nscd" (No such file or directory))  
Nov 21 13:09:37 ubuntu NetworkManager: <information>^IActivation (eth0) successful, device activated. 
Nov 21 13:09:37 ubuntu NetworkManager: <information>^IActivation (eth0) Finish handler scheduled. 
Nov 21 13:09:38 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 5 of 5 (IP Configure Commit) complete. 
Nov 21 13:09:39 ubuntu avahi-daemon[5201]: Registering new address record for fe80::203:25ff:fe3f:b1e6 on eth0.*.
Nov 21 13:09:48 ubuntu ntpdate[5744]: adjust time server 91.189.94.4 offset -0.192189 sec
Nov 21 13:10:30 ubuntu NetworkManager: <information>^IUpdating allowed wireless network lists. 
Nov 21 13:10:31 ubuntu NetworkManager: <WARNING>^I nm_dbus_get_networks_cb (): error received: org.freedesktop.NetworkManagerInfo.NoNetworks - There are no wireless networks stored.. 
Nov 21 13:24:52 ubuntu NetworkManager: <information>^ISWITCH: terminating current connection 'eth0' because it's no longer valid. 
Nov 21 13:24:52 ubuntu NetworkManager: <information>^IDeactivating device eth0. 
Nov 21 13:24:52 ubuntu dhclient: There is already a pid file /var/run/dhclient.eth0.pid with pid 5459
Nov 21 13:24:52 ubuntu dhclient: killed old client process, removed PID file
Nov 21 13:24:52 ubuntu dhclient: DHCPRELEASE on eth0 to 192.168.15.1 port 67
Nov 21 13:24:52 ubuntu avahi-daemon[5201]: Withdrawing address record for 192.168.15.102 on eth0.
Nov 21 13:24:53 ubuntu avahi-daemon[5201]: Leaving mDNS multicast group on interface eth0.IPv4 with address 192.168.15.102.
Nov 21 13:24:53 ubuntu avahi-daemon[5201]: Interface eth0.IPv4 no longer relevant for mDNS.
Nov 21 13:24:53 ubuntu avahi-autoipd(eth0)[6537]: Found user 'avahi-autoipd' (UID 104) and group 'avahi-autoipd' (GID 110).
Nov 21 13:24:53 ubuntu avahi-autoipd(eth0)[6537]: Successfully called chroot().
Nov 21 13:24:53 ubuntu avahi-autoipd(eth0)[6537]: Successfully dropped root privileges.
Nov 21 13:24:53 ubuntu avahi-autoipd(eth0)[6537]: Starting with address 169.254.8.77
Nov 21 13:24:53 ubuntu avahi-daemon[5201]: Withdrawing address record for fe80::203:25ff:fe3f:b1e6 on eth0.
Nov 21 13:24:53 ubuntu NetworkManager: nm_device_is_802_3_ethernet: assertion `dev != NULL' failed
Nov 21 13:24:53 ubuntu NetworkManager: nm_device_is_802_11_wireless: assertion `dev != NULL' failed
Nov 21 13:24:53 ubuntu NetworkManager: <information>^IWill activate wired connection 'eth0' because it now has a link. 
Nov 21 13:24:53 ubuntu NetworkManager: <information>^ISWITCH: no current connection, found better connection 'eth0'. 
Nov 21 13:24:53 ubuntu NetworkManager: <information>^IWill activate connection 'eth0'. 
Nov 21 13:24:53 ubuntu NetworkManager: <information>^IDevice eth0 activation scheduled... 
Nov 21 13:24:54 ubuntu NetworkManager: <information>^IActivation (eth0) started... 
Nov 21 13:24:54 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 1 of 5 (Device Prepare) scheduled... 
Nov 21 13:24:54 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 1 of 5 (Device Prepare) started... 
Nov 21 13:24:54 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 2 of 5 (Device Configure) scheduled... 
Nov 21 13:24:54 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 1 of 5 (Device Prepare) complete. 
Nov 21 13:24:54 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 2 of 5 (Device Configure) starting... 
Nov 21 13:24:54 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 2 of 5 (Device Configure) successful. 
Nov 21 13:24:54 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 3 of 5 (IP Configure Start) scheduled. 
Nov 21 13:24:54 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 2 of 5 (Device Configure) complete. 
Nov 21 13:24:54 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 3 of 5 (IP Configure Start) started... 
Nov 21 13:24:55 ubuntu NetworkManager: <information>^IActivation (eth0) Beginning DHCP transaction. 
Nov 21 13:24:55 ubuntu NetworkManager: <information>^ICouldn't send DHCP 'up' message because: name 'com.redhat.dhcp.OperationInProgress', message 'interface eth0 is being released. Please try again later.'. 
Nov 21 13:24:56 ubuntu NetworkManager: <information>^IActivation (eth0) failed. 
Nov 21 13:24:56 ubuntu NetworkManager: <information>^IDeactivating device eth0. 
Nov 21 13:24:56 ubuntu NetworkManager: <information>^IActivation (eth0) failure scheduled... 
Nov 21 13:24:56 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 3 of 5 (IP Configure Start) complete. 
Nov 21 13:24:57 ubuntu NetworkManager: <information>^ISWITCH: no current connection, found better connection 'eth0'. 
Nov 21 13:24:57 ubuntu NetworkManager: <information>^IWill activate connection 'eth0'. 
Nov 21 13:24:57 ubuntu NetworkManager: <information>^IDevice eth0 activation scheduled... 
Nov 21 13:24:57 ubuntu NetworkManager: <information>^IActivation (eth0) started... 
Nov 21 13:24:57 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 1 of 5 (Device Prepare) scheduled... 
Nov 21 13:24:57 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 1 of 5 (Device Prepare) started... 
Nov 21 13:24:57 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 2 of 5 (Device Configure) scheduled... 
Nov 21 13:24:57 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 1 of 5 (Device Prepare) complete. 
Nov 21 13:24:57 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 2 of 5 (Device Configure) starting... 
Nov 21 13:24:57 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 2 of 5 (Device Configure) successful. 
Nov 21 13:24:57 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 3 of 5 (IP Configure Start) scheduled. 
Nov 21 13:24:57 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 2 of 5 (Device Configure) complete. 
Nov 21 13:24:57 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 3 of 5 (IP Configure Start) started... 
Nov 21 13:24:57 ubuntu avahi-autoipd(eth0)[6537]: Callout BIND, address 169.254.8.77 on interface eth0
Nov 21 13:24:57 ubuntu avahi-daemon[5201]: Joining mDNS multicast group on interface eth0.IPv4 with address 169.254.8.77.
Nov 21 13:24:57 ubuntu avahi-daemon[5201]: New relevant interface eth0.IPv4 for mDNS.
Nov 21 13:24:57 ubuntu avahi-daemon[5201]: Registering new address record for 169.254.8.77 on eth0.IPv4.
Nov 21 13:24:59 ubuntu NetworkManager: <information>^IActivation (eth0) Beginning DHCP transaction. 
Nov 21 13:24:59 ubuntu NetworkManager: <information>^ICouldn't send DHCP 'up' message because: name 'com.redhat.dhcp.OperationInProgress', message 'interface eth0 is being released. Please try again later.'. 
Nov 21 13:24:59 ubuntu NetworkManager: <information>^IActivation (eth0) failure scheduled... 
Nov 21 13:24:59 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 3 of 5 (IP Configure Start) complete. 
Nov 21 13:24:59 ubuntu NetworkManager: <information>^IActivation (eth0) failed. 
Nov 21 13:24:59 ubuntu NetworkManager: <information>^IDeactivating device eth0. 
Nov 21 13:25:00 ubuntu avahi-daemon[5201]: Withdrawing address record for 169.254.8.77 on eth0.
Nov 21 13:25:00 ubuntu avahi-daemon[5201]: Leaving mDNS multicast group on interface eth0.IPv4 with address 169.254.8.77.
Nov 21 13:25:00 ubuntu avahi-daemon[5201]: Interface eth0.IPv4 no longer relevant for mDNS.
Nov 21 13:25:00 ubuntu NetworkManager: <information>^ISWITCH: no current connection, found better connection 'eth0'. 
Nov 21 13:25:00 ubuntu NetworkManager: <information>^IWill activate connection 'eth0'. 
Nov 21 13:25:00 ubuntu NetworkManager: <information>^IDevice eth0 activation scheduled... 
Nov 21 13:25:00 ubuntu NetworkManager: <information>^IActivation (eth0) started... 
Nov 21 13:25:00 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 1 of 5 (Device Prepare) scheduled... 
Nov 21 13:25:00 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 1 of 5 (Device Prepare) started... 
Nov 21 13:25:00 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 2 of 5 (Device Configure) scheduled... 
Nov 21 13:25:00 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 1 of 5 (Device Prepare) complete. 
Nov 21 13:25:00 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 2 of 5 (Device Configure) starting... 
Nov 21 13:25:00 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 2 of 5 (Device Configure) successful. 
Nov 21 13:25:00 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 3 of 5 (IP Configure Start) scheduled. 
Nov 21 13:25:00 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 2 of 5 (Device Configure) complete. 
Nov 21 13:25:00 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 3 of 5 (IP Configure Start) started... 
Nov 21 13:25:01 ubuntu avahi-autoipd(eth0)[6537]: Successfully claimed IP address 169.254.8.77
Nov 21 13:25:01 ubuntu NetworkManager: <information>^IDHCP daemon state is now 11 (unknown) for interface eth0 
Nov 21 13:25:01 ubuntu NetworkManager: <information>^IDHCP daemon state is now 14 (normal exit) for interface eth0 
Nov 21 13:25:02 ubuntu NetworkManager: <information>^IActivation (eth0) Beginning DHCP transaction. 
Nov 21 13:25:02 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 3 of 5 (IP Configure Start) complete. 
Nov 21 13:25:02 ubuntu dhclient: There is already a pid file /var/run/dhclient.eth0.pid with pid 134993440
Nov 21 13:25:02 ubuntu NetworkManager: <information>^IDHCP daemon state is now 12 (successfully started) for interface eth0 
Nov 21 13:25:02 ubuntu avahi-autoipd(eth0)[6537]: Got SIGTERM, quitting.
Nov 21 13:25:02 ubuntu avahi-autoipd(eth0)[6537]: Callout STOP, address 169.254.8.77 on interface eth0
Nov 21 13:25:02 ubuntu avahi-autoipd(eth0)[6538]: client: RTNETLINK answers: No such device
Nov 21 13:25:02 ubuntu avahi-autoipd(eth0)[6538]: Script execution failed with return value 2
Nov 21 13:25:03 ubuntu NetworkManager: <information>^IDHCP daemon state is now 1 (starting) for interface eth0 
Nov 21 13:25:06 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
Nov 21 13:25:06 ubuntu dhclient: DHCPOFFER from 192.168.15.1
Nov 21 13:25:06 ubuntu dhclient: DHCPREQUEST on eth0 to 255.255.255.255 port 67
Nov 21 13:25:06 ubuntu dhclient: DHCPACK from 192.168.15.1
Nov 21 13:25:06 ubuntu avahi-daemon[5201]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.15.102.
Nov 21 13:25:06 ubuntu avahi-daemon[5201]: New relevant interface eth0.IPv4 for mDNS.
Nov 21 13:25:06 ubuntu avahi-daemon[5201]: Registering new address record for 192.168.15.102 on eth0.IPv4.
Nov 21 13:25:06 ubuntu NetworkManager: <information>^IDHCP daemon state is now 2 (bound) for interface eth0 
Nov 21 13:25:06 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 4 of 5 (IP Configure Get) scheduled... 
Nov 21 13:25:06 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 4 of 5 (IP Configure Get) started... 
Nov 21 13:25:06 ubuntu NetworkManager: <information>^IRetrieved the following IP4 configuration from the DHCP daemon: 
Nov 21 13:25:06 ubuntu NetworkManager: <information>^I  address 192.168.15.102 
Nov 21 13:25:06 ubuntu NetworkManager: <information>^I  netmask 255.255.255.0 
Nov 21 13:25:06 ubuntu NetworkManager: <information>^I  broadcast 192.168.15.255 
Nov 21 13:25:06 ubuntu NetworkManager: <information>^I  gateway 192.168.15.1 
Nov 21 13:25:06 ubuntu NetworkManager: <information>^I  nameserver 192.168.15.1 
Nov 21 13:25:06 ubuntu NetworkManager: <information>^I  hostname 'ubuntu' 
Nov 21 13:25:06 ubuntu dhclient: bound to 192.168.15.102 -- renewal in 42279 seconds.
Nov 21 13:25:06 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 5 of 5 (IP Configure Commit) scheduled... 
Nov 21 13:25:06 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 4 of 5 (IP Configure Get) complete. 
Nov 21 13:25:06 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 5 of 5 (IP Configure Commit) started... 
Nov 21 13:25:06 ubuntu avahi-daemon[5201]: Withdrawing address record for 192.168.15.102 on eth0.
Nov 21 13:25:06 ubuntu avahi-daemon[5201]: Leaving mDNS multicast group on interface eth0.IPv4 with address 192.168.15.102.
Nov 21 13:25:06 ubuntu avahi-daemon[5201]: Interface eth0.IPv4 no longer relevant for mDNS.
Nov 21 13:25:06 ubuntu avahi-daemon[5201]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.15.102.
Nov 21 13:25:06 ubuntu avahi-daemon[5201]: New relevant interface eth0.IPv4 for mDNS.
Nov 21 13:25:06 ubuntu avahi-daemon[5201]: Registering new address record for 192.168.15.102 on eth0.IPv4.
Nov 21 13:25:07 ubuntu NetworkManager: <information>^IClearing nscd hosts cache. 
Nov 21 13:25:07 ubuntu NetworkManager: <WARNING>^I nm_spawn_process (): nm_spawn_process('/usr/sbin/nscd -i hosts'): could not spawn process. (Failed to execute child process "/usr/sbin/nscd" (No such file or directory))  
Nov 21 13:25:07 ubuntu NetworkManager: <information>^IActivation (eth0) successful, device activated. 
Nov 21 13:25:07 ubuntu NetworkManager: <information>^IActivation (eth0) Finish handler scheduled. 
Nov 21 13:25:07 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 5 of 5 (IP Configure Commit) complete. 
Nov 21 13:25:08 ubuntu avahi-daemon[5201]: Registering new address record for fe80::203:25ff:fe3f:b1e6 on eth0.*.
Nov 21 13:25:18 ubuntu ntpdate[6699]: adjust time server 91.189.94.4 offset 0.159770 sec
Nov 21 13:26:59 ubuntu gdm[5256]: Restarting computer...
Nov 21 13:27:02 ubuntu init: tty5 main process (4618) killed by TERM signal
Nov 21 13:27:02 ubuntu init: tty3 main process (4622) killed by TERM signal
Nov 21 13:27:02 ubuntu init: tty6 main process (4625) killed by TERM signal
Nov 21 13:27:02 ubuntu init: tty1 main process (4624) killed by TERM signal
Nov 21 13:27:02 ubuntu init: tty4 main process (4617) killed by TERM signal
Nov 21 13:27:02 ubuntu init: tty2 main process (4620) killed by TERM signal
Nov 21 13:28:46 ubuntu NetworkManager: <information>^Istarting... 
Nov 21 13:28:46 ubuntu NetworkManager: <information>^Ieth0: Device is fully-supported using driver 'sky2'. 
Nov 21 13:28:46 ubuntu NetworkManager: <information>^Inm_device_init(): waiting for device's worker thread to start 
Nov 21 13:28:46 ubuntu NetworkManager: <information>^Inm_device_init(): device's worker thread started, continuing. 
Nov 21 13:28:46 ubuntu NetworkManager: <information>^INow managing wired Ethernet (802.3) device 'eth0'. 
Nov 21 13:28:46 ubuntu NetworkManager: <information>^IDeactivating device eth0. 
Nov 21 13:28:46 ubuntu avahi-daemon[5202]: Found user 'avahi' (UID 105) and group 'avahi' (GID 111).
Nov 21 13:28:46 ubuntu avahi-daemon[5202]: Successfully dropped root privileges.
Nov 21 13:28:46 ubuntu avahi-daemon[5202]: avahi-daemon 0.6.17 starting up.
Nov 21 13:28:46 ubuntu avahi-daemon[5202]: Successfully called chroot().
Nov 21 13:28:46 ubuntu avahi-daemon[5202]: Successfully dropped remaining capabilities.
Nov 21 13:28:46 ubuntu avahi-daemon[5202]: No service found in /etc/avahi/services.
Nov 21 13:28:46 ubuntu avahi-daemon[5202]: Network interface enumeration completed.
Nov 21 13:28:46 ubuntu avahi-daemon[5202]: Registering HINFO record with values 'I686'/'LINUX'.
Nov 21 13:28:46 ubuntu avahi-daemon[5202]: Server startup complete. Host name is ubuntu.local. Local service cookie is 3270081231.
Nov 21 13:28:49 ubuntu NetworkManager: <information>^IWill activate wired connection 'eth0' because it now has a link. 
Nov 21 13:28:49 ubuntu NetworkManager: <information>^ISWITCH: no current connection, found better connection 'eth0'. 
Nov 21 13:28:49 ubuntu NetworkManager: <information>^IWill activate connection 'eth0'. 
Nov 21 13:28:49 ubuntu NetworkManager: <information>^IDevice eth0 activation scheduled... 
Nov 21 13:28:49 ubuntu NetworkManager: <information>^IActivation (eth0) started... 
Nov 21 13:28:49 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 1 of 5 (Device Prepare) scheduled... 
Nov 21 13:28:49 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 1 of 5 (Device Prepare) started... 
Nov 21 13:28:49 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 2 of 5 (Device Configure) scheduled... 
Nov 21 13:28:50 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 1 of 5 (Device Prepare) complete. 
Nov 21 13:28:50 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 2 of 5 (Device Configure) starting... 
Nov 21 13:28:51 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 2 of 5 (Device Configure) successful. 
Nov 21 13:28:51 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 3 of 5 (IP Configure Start) scheduled. 
Nov 21 13:28:51 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 2 of 5 (Device Configure) complete. 
Nov 21 13:28:51 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 3 of 5 (IP Configure Start) started... 
Nov 21 13:28:52 ubuntu NetworkManager: <information>^IActivation (eth0) Beginning DHCP transaction. 
Nov 21 13:28:52 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 3 of 5 (IP Configure Start) complete. 
Nov 21 13:28:53 ubuntu NetworkManager: <information>^IDHCP daemon state is now 12 (successfully started) for interface eth0 
Nov 21 13:28:53 ubuntu hcid[5457]: Bluetooth HCI daemon
Nov 21 13:28:53 ubuntu hcid[5457]: Starting SDP server
Nov 21 13:28:53 ubuntu NetworkManager: <debug info>^I[1195669731.148586] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_bluetooth'). 
Nov 21 13:28:53 ubuntu dhclient: isc-dhclient-V3.0.4
Nov 21 13:28:54 ubuntu NetworkManager: <information>^IDHCP daemon state is now 1 (starting) for interface eth0 
Nov 21 13:28:54 ubuntu dhclient: DHCPREQUEST on eth0 to 255.255.255.255 port 67
Nov 21 13:28:54 ubuntu dhclient: DHCPACK from 192.168.15.1
Nov 21 13:28:54 ubuntu avahi-daemon[5202]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.15.102.
Nov 21 13:28:54 ubuntu NetworkManager: <information>^IDHCP daemon state is now 4 (reboot) for interface eth0 
Nov 21 13:28:54 ubuntu dhclient: bound to 192.168.15.102 -- renewal in 39479 seconds.
Nov 21 13:28:54 ubuntu avahi-daemon[5202]: New relevant interface eth0.IPv4 for mDNS.
Nov 21 13:28:54 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 4 of 5 (IP Configure Get) scheduled... 
Nov 21 13:28:54 ubuntu avahi-daemon[5202]: Registering new address record for 192.168.15.102 on eth0.IPv4.
Nov 21 13:28:54 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 4 of 5 (IP Configure Get) started... 
Nov 21 13:28:54 ubuntu NetworkManager: <information>^IRetrieved the following IP4 configuration from the DHCP daemon: 
Nov 21 13:28:54 ubuntu NetworkManager: <information>^I  address 192.168.15.102 
Nov 21 13:28:54 ubuntu NetworkManager: <information>^I  netmask 255.255.255.0 
Nov 21 13:28:54 ubuntu NetworkManager: <information>^I  broadcast 192.168.15.255 
Nov 21 13:28:54 ubuntu NetworkManager: <information>^I  gateway 192.168.15.1 
Nov 21 13:28:54 ubuntu NetworkManager: <information>^I  nameserver 192.168.15.1 
Nov 21 13:28:54 ubuntu NetworkManager: <information>^I  hostname 'ubuntu' 
Nov 21 13:28:54 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 5 of 5 (IP Configure Commit) scheduled... 
Nov 21 13:28:54 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 4 of 5 (IP Configure Get) complete. 
Nov 21 13:28:54 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 5 of 5 (IP Configure Commit) started... 
Nov 21 13:28:55 ubuntu avahi-daemon[5202]: Withdrawing address record for 192.168.15.102 on eth0.
Nov 21 13:28:55 ubuntu avahi-daemon[5202]: Leaving mDNS multicast group on interface eth0.IPv4 with address 192.168.15.102.
Nov 21 13:28:55 ubuntu avahi-daemon[5202]: Interface eth0.IPv4 no longer relevant for mDNS.
Nov 21 13:28:55 ubuntu avahi-daemon[5202]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.15.102.
Nov 21 13:28:55 ubuntu avahi-daemon[5202]: New relevant interface eth0.IPv4 for mDNS.
Nov 21 13:28:55 ubuntu avahi-daemon[5202]: Registering new address record for 192.168.15.102 on eth0.IPv4.
Nov 21 13:28:55 ubuntu NetworkManager: <information>^IClearing nscd hosts cache. 
Nov 21 13:28:55 ubuntu NetworkManager: <WARNING>^I nm_spawn_process (): nm_spawn_process('/usr/sbin/nscd -i hosts'): could not spawn process. (Failed to execute child process "/usr/sbin/nscd" (No such file or directory))  
Nov 21 13:28:55 ubuntu NetworkManager: <information>^IActivation (eth0) Finish handler scheduled. 
Nov 21 13:28:55 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 5 of 5 (IP Configure Commit) complete. 
Nov 21 13:28:56 ubuntu NetworkManager: <information>^IActivation (eth0) successful, device activated. 
Nov 21 13:28:57 ubuntu avahi-daemon[5202]: Registering new address record for fe80::203:25ff:fe3f:b1e6 on eth0.*.
Nov 21 13:29:06 ubuntu ntpdate[5739]: adjust time server 91.189.94.4 offset -0.149951 sec
Nov 21 13:29:36 ubuntu NetworkManager: <information>^IUpdating allowed wireless network lists. 
Nov 21 13:29:37 ubuntu NetworkManager: <WARNING>^I nm_dbus_get_networks_cb (): error received: org.freedesktop.NetworkManagerInfo.NoNetworks - There are no wireless networks stored.. 
Nov 21 13:35:41 ubuntu dhclient: isc-dhclient-V3.0.4
Nov 21 13:36:59 ubuntu NetworkManager: <information>^IUser Switch: /org/freedesktop/NetworkManager/Devices/eth0 
Nov 21 13:36:59 ubuntu NetworkManager: <information>^IDeactivating device eth0. 
Nov 21 13:36:59 ubuntu dhclient: There is already a pid file /var/run/dhclient.eth0.pid with pid 5410
Nov 21 13:36:59 ubuntu dhclient: killed old client process, removed PID file
Nov 21 13:36:59 ubuntu dhclient: DHCPRELEASE on eth0 to 192.168.15.1 port 67
Nov 21 13:36:59 ubuntu avahi-daemon[5202]: Withdrawing address record for 192.168.15.102 on eth0.
Nov 21 13:36:59 ubuntu avahi-daemon[5202]: Leaving mDNS multicast group on interface eth0.IPv4 with address 192.168.15.102.
Nov 21 13:36:59 ubuntu avahi-daemon[5202]: Interface eth0.IPv4 no longer relevant for mDNS.
Nov 21 13:36:59 ubuntu avahi-autoipd(eth0)[7163]: Found user 'avahi-autoipd' (UID 104) and group 'avahi-autoipd' (GID 110).
Nov 21 13:36:59 ubuntu avahi-autoipd(eth0)[7163]: Successfully called chroot().
Nov 21 13:36:59 ubuntu avahi-autoipd(eth0)[7163]: Successfully dropped root privileges.
Nov 21 13:36:59 ubuntu avahi-autoipd(eth0)[7163]: fopen() failed: Permission denied
Nov 21 13:36:59 ubuntu avahi-autoipd(eth0)[7163]: Starting with address 169.254.8.77
Nov 21 13:37:00 ubuntu avahi-daemon[5202]: Withdrawing address record for fe80::203:25ff:fe3f:b1e6 on eth0.
Nov 21 13:37:00 ubuntu NetworkManager: <information>^IDevice eth0 activation scheduled... 
Nov 21 13:37:00 ubuntu NetworkManager: <information>^IActivation (eth0) started... 
Nov 21 13:37:00 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 1 of 5 (Device Prepare) scheduled... 
Nov 21 13:37:00 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 1 of 5 (Device Prepare) started... 
Nov 21 13:37:00 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 2 of 5 (Device Configure) scheduled... 
Nov 21 13:37:00 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 1 of 5 (Device Prepare) complete. 
Nov 21 13:37:00 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 2 of 5 (Device Configure) starting... 
Nov 21 13:37:00 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 2 of 5 (Device Configure) successful. 
Nov 21 13:37:00 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 3 of 5 (IP Configure Start) scheduled. 
Nov 21 13:37:00 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 2 of 5 (Device Configure) complete. 
Nov 21 13:37:00 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 3 of 5 (IP Configure Start) started... 
Nov 21 13:37:02 ubuntu NetworkManager: <information>^IActivation (eth0) Beginning DHCP transaction. 
Nov 21 13:37:02 ubuntu NetworkManager: <information>^ICouldn't send DHCP 'up' message because: name 'com.redhat.dhcp.OperationInProgress', message 'interface eth0 is being released. Please try again later.'. 
Nov 21 13:37:02 ubuntu NetworkManager: <information>^IActivation (eth0) failure scheduled... 
Nov 21 13:37:02 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 3 of 5 (IP Configure Start) complete. 
Nov 21 13:37:02 ubuntu NetworkManager: <information>^IActivation (eth0) failed. 
Nov 21 13:37:02 ubuntu NetworkManager: <information>^IDeactivating device eth0. 
Nov 21 13:37:03 ubuntu NetworkManager: <information>^ISWITCH: no current connection, found better connection 'eth0'. 
Nov 21 13:37:03 ubuntu NetworkManager: <information>^IWill activate connection 'eth0'. 
Nov 21 13:37:03 ubuntu NetworkManager: <information>^IDevice eth0 activation scheduled... 
Nov 21 13:37:03 ubuntu NetworkManager: <information>^IActivation (eth0) started... 
Nov 21 13:37:03 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 1 of 5 (Device Prepare) scheduled... 
Nov 21 13:37:03 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 1 of 5 (Device Prepare) started... 
Nov 21 13:37:03 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 2 of 5 (Device Configure) scheduled... 
Nov 21 13:37:03 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 1 of 5 (Device Prepare) complete. 
Nov 21 13:37:03 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 2 of 5 (Device Configure) starting... 
Nov 21 13:37:03 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 2 of 5 (Device Configure) successful. 
Nov 21 13:37:03 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 3 of 5 (IP Configure Start) scheduled. 
Nov 21 13:37:03 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 2 of 5 (Device Configure) complete. 
Nov 21 13:37:03 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 3 of 5 (IP Configure Start) started... 
Nov 21 13:37:04 ubuntu avahi-autoipd(eth0)[7163]: Callout BIND, address 169.254.8.77 on interface eth0
Nov 21 13:37:04 ubuntu avahi-daemon[5202]: Joining mDNS multicast group on interface eth0.IPv4 with address 169.254.8.77.
Nov 21 13:37:04 ubuntu avahi-daemon[5202]: New relevant interface eth0.IPv4 for mDNS.
Nov 21 13:37:04 ubuntu avahi-daemon[5202]: Registering new address record for 169.254.8.77 on eth0.IPv4.
Nov 21 13:37:05 ubuntu NetworkManager: <information>^IActivation (eth0) Beginning DHCP transaction. 
Nov 21 13:37:05 ubuntu NetworkManager: <information>^ICouldn't send DHCP 'up' message because: name 'com.redhat.dhcp.OperationInProgress', message 'interface eth0 is being released. Please try again later.'. 
Nov 21 13:37:05 ubuntu NetworkManager: <information>^IActivation (eth0) failure scheduled... 
Nov 21 13:37:05 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 3 of 5 (IP Configure Start) complete. 
Nov 21 13:37:05 ubuntu NetworkManager: <information>^IActivation (eth0) failed. 
Nov 21 13:37:05 ubuntu NetworkManager: <information>^IDeactivating device eth0. 
Nov 21 13:37:06 ubuntu avahi-daemon[5202]: Withdrawing address record for 169.254.8.77 on eth0.
Nov 21 13:37:06 ubuntu avahi-daemon[5202]: Leaving mDNS multicast group on interface eth0.IPv4 with address 169.254.8.77.
Nov 21 13:37:06 ubuntu avahi-daemon[5202]: Interface eth0.IPv4 no longer relevant for mDNS.
Nov 21 13:37:06 ubuntu NetworkManager: <information>^ISWITCH: no current connection, found better connection 'eth0'. 
Nov 21 13:37:06 ubuntu NetworkManager: <information>^IWill activate connection 'eth0'. 
Nov 21 13:37:06 ubuntu NetworkManager: <information>^IDevice eth0 activation scheduled... 
Nov 21 13:37:06 ubuntu NetworkManager: <information>^IActivation (eth0) started... 
Nov 21 13:37:06 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 1 of 5 (Device Prepare) scheduled... 
Nov 21 13:37:06 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 1 of 5 (Device Prepare) started... 
Nov 21 13:37:06 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 2 of 5 (Device Configure) scheduled... 
Nov 21 13:37:06 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 1 of 5 (Device Prepare) complete. 
Nov 21 13:37:06 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 2 of 5 (Device Configure) starting... 
Nov 21 13:37:06 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 2 of 5 (Device Configure) successful. 
Nov 21 13:37:06 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 3 of 5 (IP Configure Start) scheduled. 
Nov 21 13:37:06 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 2 of 5 (Device Configure) complete. 
Nov 21 13:37:06 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 3 of 5 (IP Configure Start) started... 
Nov 21 13:37:08 ubuntu NetworkManager: <information>^IActivation (eth0) Beginning DHCP transaction. 
Nov 21 13:37:08 ubuntu NetworkManager: <information>^ICouldn't send DHCP 'up' message because: name 'com.redhat.dhcp.OperationInProgress', message 'interface eth0 is being released. Please try again later.'. 
Nov 21 13:37:08 ubuntu NetworkManager: <information>^IActivation (eth0) failure scheduled... 
Nov 21 13:37:08 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 3 of 5 (IP Configure Start) complete. 
Nov 21 13:37:08 ubuntu NetworkManager: <information>^IActivation (eth0) failed. 
Nov 21 13:37:08 ubuntu NetworkManager: <information>^IDeactivating device eth0. 
Nov 21 13:37:08 ubuntu avahi-autoipd(eth0)[7163]: Successfully claimed IP address 169.254.8.77
Nov 21 13:37:08 ubuntu avahi-autoipd(eth0)[7163]: fopen() failed: Permission denied
Nov 21 13:37:09 ubuntu NetworkManager: <information>^ISWITCH: no current connection, found better connection 'eth0'. 
Nov 21 13:37:09 ubuntu NetworkManager: <information>^IWill activate connection 'eth0'. 
Nov 21 13:37:09 ubuntu NetworkManager: <information>^IDevice eth0 activation scheduled... 
Nov 21 13:37:09 ubuntu NetworkManager: <information>^IActivation (eth0) started... 
Nov 21 13:37:09 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 1 of 5 (Device Prepare) scheduled... 
Nov 21 13:37:09 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 1 of 5 (Device Prepare) started... 
Nov 21 13:37:09 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 2 of 5 (Device Configure) scheduled... 
Nov 21 13:37:09 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 1 of 5 (Device Prepare) complete. 
Nov 21 13:37:09 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 2 of 5 (Device Configure) starting... 
Nov 21 13:37:09 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 2 of 5 (Device Configure) successful. 
Nov 21 13:37:09 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 3 of 5 (IP Configure Start) scheduled. 
Nov 21 13:37:09 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 2 of 5 (Device Configure) complete. 
Nov 21 13:37:09 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 3 of 5 (IP Configure Start) started... 
Nov 21 13:37:10 ubuntu NetworkManager: <information>^IActivation (eth0) Beginning DHCP transaction. 
Nov 21 13:37:10 ubuntu dhclient: There is already a pid file /var/run/dhclient.eth0.pid with pid 134993440
Nov 21 13:37:10 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 3 of 5 (IP Configure Start) complete. 
Nov 21 13:37:10 ubuntu NetworkManager: <information>^IDHCP daemon state is now 12 (successfully started) for interface eth0 
Nov 21 13:37:10 ubuntu avahi-autoipd(eth0)[7163]: Got SIGTERM, quitting.
Nov 21 13:37:10 ubuntu avahi-autoipd(eth0)[7163]: Callout STOP, address 169.254.8.77 on interface eth0
Nov 21 13:37:10 ubuntu avahi-autoipd(eth0)[7164]: client: RTNETLINK answers: No such device
Nov 21 13:37:10 ubuntu avahi-autoipd(eth0)[7164]: Script execution failed with return value 2
Nov 21 13:37:11 ubuntu NetworkManager: <information>^IDHCP daemon state is now 1 (starting) for interface eth0 
Nov 21 13:37:13 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
Nov 21 13:37:13 ubuntu dhclient: DHCPOFFER from 192.168.15.1
Nov 21 13:37:13 ubuntu dhclient: DHCPREQUEST on eth0 to 255.255.255.255 port 67
Nov 21 13:37:13 ubuntu dhclient: DHCPACK from 192.168.15.1
Nov 21 13:37:13 ubuntu avahi-daemon[5202]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.15.102.
Nov 21 13:37:13 ubuntu avahi-daemon[5202]: New relevant interface eth0.IPv4 for mDNS.
Nov 21 13:37:13 ubuntu avahi-daemon[5202]: Registering new address record for 192.168.15.102 on eth0.IPv4.
Nov 21 13:37:13 ubuntu NetworkManager: <information>^IDHCP daemon state is now 2 (bound) for interface eth0 
Nov 21 13:37:13 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 4 of 5 (IP Configure Get) scheduled... 
Nov 21 13:37:13 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 4 of 5 (IP Configure Get) started... 
Nov 21 13:37:13 ubuntu NetworkManager: <information>^IRetrieved the following IP4 configuration from the DHCP daemon: 
Nov 21 13:37:13 ubuntu NetworkManager: <information>^I  address 192.168.15.102 
Nov 21 13:37:13 ubuntu NetworkManager: <information>^I  netmask 255.255.255.0 
Nov 21 13:37:13 ubuntu NetworkManager: <information>^I  broadcast 192.168.15.255 
Nov 21 13:37:13 ubuntu NetworkManager: <information>^I  gateway 192.168.15.1 
Nov 21 13:37:13 ubuntu NetworkManager: <information>^I  nameserver 192.168.15.1 
Nov 21 13:37:13 ubuntu NetworkManager: <information>^I  hostname 'ubuntu' 
Nov 21 13:37:13 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 5 of 5 (IP Configure Commit) scheduled... 
Nov 21 13:37:13 ubuntu dhclient: bound to 192.168.15.102 -- renewal in 40660 seconds.
Nov 21 13:37:13 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 4 of 5 (IP Configure Get) complete. 
Nov 21 13:37:13 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 5 of 5 (IP Configure Commit) started... 
Nov 21 13:37:13 ubuntu avahi-daemon[5202]: Withdrawing address record for 192.168.15.102 on eth0.
Nov 21 13:37:13 ubuntu avahi-daemon[5202]: Leaving mDNS multicast group on interface eth0.IPv4 with address 192.168.15.102.
Nov 21 13:37:13 ubuntu avahi-daemon[5202]: Interface eth0.IPv4 no longer relevant for mDNS.
Nov 21 13:37:13 ubuntu avahi-daemon[5202]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.15.102.
Nov 21 13:37:13 ubuntu avahi-daemon[5202]: New relevant interface eth0.IPv4 for mDNS.
Nov 21 13:37:13 ubuntu avahi-daemon[5202]: Registering new address record for 192.168.15.102 on eth0.IPv4.
Nov 21 13:37:14 ubuntu NetworkManager: <information>^IClearing nscd hosts cache. 
Nov 21 13:37:14 ubuntu NetworkManager: <WARNING>^I nm_spawn_process (): nm_spawn_process('/usr/sbin/nscd -i hosts'): could not spawn process. (Failed to execute child process "/usr/sbin/nscd" (No such file or directory))  
Nov 21 13:37:14 ubuntu NetworkManager: <information>^IActivation (eth0) Finish handler scheduled. 
Nov 21 13:37:14 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 5 of 5 (IP Configure Commit) complete. 
Nov 21 13:37:14 ubuntu NetworkManager: <information>^IActivation (eth0) successful, device activated. 
Nov 21 13:37:15 ubuntu avahi-daemon[5202]: Registering new address record for fe80::203:25ff:fe3f:b1e6 on eth0.*.
Nov 21 13:37:25 ubuntu ntpdate[7608]: adjust time server 91.189.94.4 offset 0.085507 sec
Nov 21 13:39:42 ubuntu NetworkManager: <information>^ISWITCH: terminating current connection 'eth0' because it's no longer valid. 
Nov 21 13:39:42 ubuntu NetworkManager: <information>^IDeactivating device eth0. 
Nov 21 13:39:42 ubuntu dhclient: There is already a pid file /var/run/dhclient.eth0.pid with pid 7381
Nov 21 13:39:42 ubuntu dhclient: killed old client process, removed PID file
Nov 21 13:39:42 ubuntu dhclient: DHCPRELEASE on eth0 to 192.168.15.1 port 67
Nov 21 13:39:42 ubuntu avahi-daemon[5202]: Withdrawing address record for 192.168.15.102 on eth0.
Nov 21 13:39:42 ubuntu avahi-daemon[5202]: Leaving mDNS multicast group on interface eth0.IPv4 with address 192.168.15.102.
Nov 21 13:39:42 ubuntu avahi-daemon[5202]: Interface eth0.IPv4 no longer relevant for mDNS.
Nov 21 13:39:42 ubuntu avahi-autoipd(eth0)[7894]: Found user 'avahi-autoipd' (UID 104) and group 'avahi-autoipd' (GID 110).
Nov 21 13:39:42 ubuntu avahi-autoipd(eth0)[7894]: Successfully called chroot().
Nov 21 13:39:42 ubuntu avahi-autoipd(eth0)[7894]: Successfully dropped root privileges.
Nov 21 13:39:42 ubuntu avahi-autoipd(eth0)[7894]: fopen() failed: Permission denied
Nov 21 13:39:42 ubuntu avahi-autoipd(eth0)[7894]: Starting with address 169.254.8.77
Nov 21 13:39:43 ubuntu avahi-daemon[5202]: Withdrawing address record for fe80::203:25ff:fe3f:b1e6 on eth0.
Nov 21 13:39:43 ubuntu NetworkManager: nm_device_is_802_3_ethernet: assertion `dev != NULL' failed
Nov 21 13:39:43 ubuntu NetworkManager: nm_device_is_802_11_wireless: assertion `dev != NULL' failed
Nov 21 13:39:44 ubuntu NetworkManager: <information>^IWill activate wired connection 'eth0' because it now has a link. 
Nov 21 13:39:44 ubuntu NetworkManager: <information>^ISWITCH: no current connection, found better connection 'eth0'. 
Nov 21 13:39:44 ubuntu NetworkManager: <information>^IWill activate connection 'eth0'. 
Nov 21 13:39:44 ubuntu NetworkManager: <information>^IDevice eth0 activation scheduled... 
Nov 21 13:39:44 ubuntu NetworkManager: <information>^IActivation (eth0) started... 
Nov 21 13:39:44 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 1 of 5 (Device Prepare) scheduled... 
Nov 21 13:39:44 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 1 of 5 (Device Prepare) started... 
Nov 21 13:39:44 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 2 of 5 (Device Configure) scheduled... 
Nov 21 13:39:44 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 1 of 5 (Device Prepare) complete. 
Nov 21 13:39:44 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 2 of 5 (Device Configure) starting... 
Nov 21 13:39:44 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 2 of 5 (Device Configure) successful. 
Nov 21 13:39:44 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 3 of 5 (IP Configure Start) scheduled. 
Nov 21 13:39:44 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 2 of 5 (Device Configure) complete. 
Nov 21 13:39:44 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 3 of 5 (IP Configure Start) started... 
Nov 21 13:39:46 ubuntu NetworkManager: <information>^IActivation (eth0) Beginning DHCP transaction. 
Nov 21 13:39:46 ubuntu NetworkManager: <information>^ICouldn't send DHCP 'up' message because: name 'com.redhat.dhcp.OperationInProgress', message 'interface eth0 is being released. Please try again later.'. 
Nov 21 13:39:46 ubuntu NetworkManager: <information>^IActivation (eth0) failed. 
Nov 21 13:39:46 ubuntu NetworkManager: <information>^IDeactivating device eth0. 
Nov 21 13:39:46 ubuntu NetworkManager: <information>^IActivation (eth0) failure scheduled... 
Nov 21 13:39:46 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 3 of 5 (IP Configure Start) complete. 
Nov 21 13:39:47 ubuntu NetworkManager: <information>^ISWITCH: no current connection, found better connection 'eth0'. 
Nov 21 13:39:47 ubuntu NetworkManager: <information>^IWill activate connection 'eth0'. 
Nov 21 13:39:47 ubuntu NetworkManager: <information>^IDevice eth0 activation scheduled... 
Nov 21 13:39:47 ubuntu NetworkManager: <information>^IActivation (eth0) started... 
Nov 21 13:39:47 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 1 of 5 (Device Prepare) scheduled... 
Nov 21 13:39:47 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 1 of 5 (Device Prepare) started... 
Nov 21 13:39:47 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 2 of 5 (Device Configure) scheduled... 
Nov 21 13:39:47 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 1 of 5 (Device Prepare) complete. 
Nov 21 13:39:47 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 2 of 5 (Device Configure) starting... 
Nov 21 13:39:47 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 2 of 5 (Device Configure) successful. 
Nov 21 13:39:47 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 3 of 5 (IP Configure Start) scheduled. 
Nov 21 13:39:47 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 2 of 5 (Device Configure) complete. 
Nov 21 13:39:47 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 3 of 5 (IP Configure Start) started... 
Nov 21 13:39:47 ubuntu avahi-autoipd(eth0)[7894]: Callout BIND, address 169.254.8.77 on interface eth0
Nov 21 13:39:47 ubuntu avahi-daemon[5202]: Joining mDNS multicast group on interface eth0.IPv4 with address 169.254.8.77.
Nov 21 13:39:47 ubuntu avahi-daemon[5202]: New relevant interface eth0.IPv4 for mDNS.
Nov 21 13:39:47 ubuntu avahi-daemon[5202]: Registering new address record for 169.254.8.77 on eth0.IPv4.
Nov 21 13:39:49 ubuntu NetworkManager: <information>^IActivation (eth0) Beginning DHCP transaction. 
Nov 21 13:39:49 ubuntu NetworkManager: <information>^ICouldn't send DHCP 'up' message because: name 'com.redhat.dhcp.OperationInProgress', message 'interface eth0 is being released. Please try again later.'. 
Nov 21 13:39:49 ubuntu NetworkManager: <information>^IActivation (eth0) failure scheduled... 
Nov 21 13:39:49 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 3 of 5 (IP Configure Start) complete. 
Nov 21 13:39:49 ubuntu NetworkManager: <information>^IActivation (eth0) failed. 
Nov 21 13:39:49 ubuntu NetworkManager: <information>^IDeactivating device eth0. 
Nov 21 13:39:50 ubuntu avahi-daemon[5202]: Withdrawing address record for 169.254.8.77 on eth0.
Nov 21 13:39:50 ubuntu avahi-daemon[5202]: Leaving mDNS multicast group on interface eth0.IPv4 with address 169.254.8.77.
Nov 21 13:39:50 ubuntu NetworkManager: <information>^ISWITCH: no current connection, found better connection 'eth0'. 
Nov 21 13:39:50 ubuntu avahi-daemon[5202]: Interface eth0.IPv4 no longer relevant for mDNS.
Nov 21 13:39:50 ubuntu NetworkManager: <information>^IWill activate connection 'eth0'. 
Nov 21 13:39:50 ubuntu NetworkManager: <information>^IDevice eth0 activation scheduled... 
Nov 21 13:39:50 ubuntu NetworkManager: <information>^IActivation (eth0) started... 
Nov 21 13:39:50 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 1 of 5 (Device Prepare) scheduled... 
Nov 21 13:39:50 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 1 of 5 (Device Prepare) started... 
Nov 21 13:39:50 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 2 of 5 (Device Configure) scheduled... 
Nov 21 13:39:50 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 1 of 5 (Device Prepare) complete. 
Nov 21 13:39:50 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 2 of 5 (Device Configure) starting... 
Nov 21 13:39:50 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 2 of 5 (Device Configure) successful. 
Nov 21 13:39:50 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 3 of 5 (IP Configure Start) scheduled. 
Nov 21 13:39:50 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 2 of 5 (Device Configure) complete. 
Nov 21 13:39:50 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 3 of 5 (IP Configure Start) started... 
Nov 21 13:39:51 ubuntu avahi-autoipd(eth0)[7894]: Successfully claimed IP address 169.254.8.77
Nov 21 13:39:51 ubuntu avahi-autoipd(eth0)[7894]: fopen() failed: Permission denied
Nov 21 13:39:51 ubuntu NetworkManager: <information>^IDHCP daemon state is now 11 (unknown) for interface eth0 
Nov 21 13:39:51 ubuntu NetworkManager: <information>^IDHCP daemon state is now 14 (normal exit) for interface eth0 
Nov 21 13:39:52 ubuntu NetworkManager: <information>^IActivation (eth0) Beginning DHCP transaction. 
Nov 21 13:39:52 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 3 of 5 (IP Configure Start) complete. 
Nov 21 13:39:52 ubuntu NetworkManager: <information>^IDHCP daemon state is now 12 (successfully started) for interface eth0 
Nov 21 13:39:52 ubuntu dhclient: There is already a pid file /var/run/dhclient.eth0.pid with pid 134993440
Nov 21 13:39:52 ubuntu avahi-autoipd(eth0)[7894]: Got SIGTERM, quitting.
Nov 21 13:39:52 ubuntu avahi-autoipd(eth0)[7894]: Callout STOP, address 169.254.8.77 on interface eth0
Nov 21 13:39:52 ubuntu avahi-autoipd(eth0)[7895]: client: RTNETLINK answers: No such device
Nov 21 13:39:52 ubuntu avahi-autoipd(eth0)[7895]: Script execution failed with return value 2
Nov 21 13:39:53 ubuntu NetworkManager: <information>^IDHCP daemon state is now 1 (starting) for interface eth0 
Nov 21 13:39:56 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
Nov 21 13:39:56 ubuntu dhclient: DHCPOFFER from 192.168.15.1
Nov 21 13:39:56 ubuntu dhclient: DHCPREQUEST on eth0 to 255.255.255.255 port 67
Nov 21 13:39:56 ubuntu dhclient: DHCPACK from 192.168.15.1
Nov 21 13:39:56 ubuntu avahi-daemon[5202]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.15.102.
Nov 21 13:39:56 ubuntu avahi-daemon[5202]: New relevant interface eth0.IPv4 for mDNS.
Nov 21 13:39:56 ubuntu avahi-daemon[5202]: Registering new address record for 192.168.15.102 on eth0.IPv4.
Nov 21 13:39:56 ubuntu NetworkManager: <information>^IDHCP daemon state is now 2 (bound) for interface eth0 
Nov 21 13:39:56 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 4 of 5 (IP Configure Get) scheduled... 
Nov 21 13:39:56 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 4 of 5 (IP Configure Get) started... 
Nov 21 13:39:56 ubuntu NetworkManager: <information>^IRetrieved the following IP4 configuration from the DHCP daemon: 
Nov 21 13:39:56 ubuntu NetworkManager: <information>^I  address 192.168.15.102 
Nov 21 13:39:56 ubuntu NetworkManager: <information>^I  netmask 255.255.255.0 
Nov 21 13:39:56 ubuntu NetworkManager: <information>^I  broadcast 192.168.15.255 
Nov 21 13:39:56 ubuntu NetworkManager: <information>^I  gateway 192.168.15.1 
Nov 21 13:39:56 ubuntu NetworkManager: <information>^I  nameserver 192.168.15.1 
Nov 21 13:39:56 ubuntu NetworkManager: <information>^I  hostname 'ubuntu' 
Nov 21 13:39:56 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 5 of 5 (IP Configure Commit) scheduled... 
Nov 21 13:39:56 ubuntu dhclient: bound to 192.168.15.102 -- renewal in 41363 seconds.
Nov 21 13:39:56 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 4 of 5 (IP Configure Get) complete. 
Nov 21 13:39:56 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 5 of 5 (IP Configure Commit) started... 
Nov 21 13:39:56 ubuntu avahi-daemon[5202]: Withdrawing address record for 192.168.15.102 on eth0.
Nov 21 13:39:56 ubuntu avahi-daemon[5202]: Leaving mDNS multicast group on interface eth0.IPv4 with address 192.168.15.102.
Nov 21 13:39:56 ubuntu avahi-daemon[5202]: Interface eth0.IPv4 no longer relevant for mDNS.
Nov 21 13:39:56 ubuntu avahi-daemon[5202]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.15.102.
Nov 21 13:39:56 ubuntu avahi-daemon[5202]: New relevant interface eth0.IPv4 for mDNS.
Nov 21 13:39:56 ubuntu avahi-daemon[5202]: Registering new address record for 192.168.15.102 on eth0.IPv4.
Nov 21 13:39:57 ubuntu NetworkManager: <information>^IClearing nscd hosts cache. 
Nov 21 13:39:57 ubuntu NetworkManager: <WARNING>^I nm_spawn_process (): nm_spawn_process('/usr/sbin/nscd -i hosts'): could not spawn process. (Failed to execute child process "/usr/sbin/nscd" (No such file or directory))  
Nov 21 13:39:57 ubuntu NetworkManager: <information>^IActivation (eth0) Finish handler scheduled. 
Nov 21 13:39:57 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 5 of 5 (IP Configure Commit) complete. 
Nov 21 13:39:57 ubuntu NetworkManager: <information>^IActivation (eth0) successful, device activated. 
Nov 21 13:39:58 ubuntu avahi-daemon[5202]: Registering new address record for fe80::203:25ff:fe3f:b1e6 on eth0.*.
Nov 21 13:40:07 ubuntu ntpdate[8064]: adjust time server 91.189.94.4 offset 0.011941 sec
Nov 21 14:24:02 ubuntu NetworkManager: <debug info>^I[1195673042.121397] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_718_65_AA0070006371905A'). 
Nov 21 14:24:02 ubuntu NetworkManager: <debug info>^I[1195673042.192650] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_718_65_AA0070006371905A_if0'). 
Nov 21 14:24:02 ubuntu NetworkManager: <debug info>^I[1195673042.194981] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_718_65_AA0070006371905A_if0_scsi_host'). 
Nov 21 14:24:02 ubuntu NetworkManager: <debug info>^I[1195673042.196942] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_718_65_AA0070006371905A_usbraw'). 
Nov 21 14:24:10 ubuntu NetworkManager: <debug info>^I[1195673049.381545] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_718_65_AA0070006371905A_if0_scsi_host_scsi_device_lun0'). 
Nov 21 14:24:10 ubuntu NetworkManager: <debug info>^I[1195673049.417634] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_718_65_AA0070006371905A_if0_scsi_host_scsi_device_lun0_scsi_generic'). 
Nov 21 14:24:10 ubuntu NetworkManager: <debug info>^I[1195673049.687854] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_serial_Imation_USB_Flash_Drive_AA0070006371905A_0_0'). 
Nov 21 14:24:10 ubuntu NetworkManager: <debug info>^I[1195673049.748671] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_352D_1380'). 
Nov 21 14:24:12 ubuntu hald: mounted /dev/sda1 on behalf of uid 1000
Nov 21 14:27:02 ubuntu NetworkManager: <information>^IUser Switch: /org/freedesktop/NetworkManager/Devices/eth0 
Nov 21 14:27:02 ubuntu NetworkManager: <information>^IDeactivating device eth0. 
Nov 21 14:27:02 ubuntu dhclient: There is already a pid file /var/run/dhclient.eth0.pid with pid 7966
Nov 21 14:27:02 ubuntu dhclient: killed old client process, removed PID file
Nov 21 14:27:03 ubuntu dhclient: DHCPRELEASE on eth0 to 192.168.15.1 port 67
Nov 21 14:27:03 ubuntu avahi-daemon[5202]: Withdrawing address record for 192.168.15.102 on eth0.
Nov 21 14:27:03 ubuntu avahi-daemon[5202]: Leaving mDNS multicast group on interface eth0.IPv4 with address 192.168.15.102.
Nov 21 14:27:03 ubuntu avahi-daemon[5202]: Interface eth0.IPv4 no longer relevant for mDNS.
Nov 21 14:27:03 ubuntu avahi-autoipd(eth0)[11237]: Found user 'avahi-autoipd' (UID 104) and group 'avahi-autoipd' (GID 110).
Nov 21 14:27:03 ubuntu avahi-autoipd(eth0)[11237]: Successfully called chroot().
Nov 21 14:27:03 ubuntu avahi-autoipd(eth0)[11237]: Successfully dropped root privileges.
Nov 21 14:27:04 ubuntu avahi-autoipd(eth0)[11237]: fopen() failed: Permission denied
Nov 21 14:27:04 ubuntu avahi-autoipd(eth0)[11237]: Starting with address 169.254.8.77
Nov 21 14:27:04 ubuntu avahi-daemon[5202]: Withdrawing address record for fe80::203:25ff:fe3f:b1e6 on eth0.
Nov 21 14:27:04 ubuntu NetworkManager: <information>^IDevice eth0 activation scheduled... 
Nov 21 14:27:04 ubuntu NetworkManager: <information>^IActivation (eth0) started... 
Nov 21 14:27:04 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 1 of 5 (Device Prepare) scheduled... 
Nov 21 14:27:04 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 1 of 5 (Device Prepare) started... 
Nov 21 14:27:04 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 2 of 5 (Device Configure) scheduled... 
Nov 21 14:27:04 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 1 of 5 (Device Prepare) complete. 
Nov 21 14:27:04 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 2 of 5 (Device Configure) starting... 
Nov 21 14:27:04 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 2 of 5 (Device Configure) successful. 
Nov 21 14:27:04 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 3 of 5 (IP Configure Start) scheduled. 
Nov 21 14:27:04 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 2 of 5 (Device Configure) complete. 
Nov 21 14:27:04 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 3 of 5 (IP Configure Start) started... 
Nov 21 14:27:06 ubuntu NetworkManager: <information>^IActivation (eth0) Beginning DHCP transaction. 
Nov 21 14:27:06 ubuntu NetworkManager: <information>^ICouldn't send DHCP 'up' message because: name 'com.redhat.dhcp.OperationInProgress', message 'interface eth0 is being released. Please try again later.'. 
Nov 21 14:27:06 ubuntu NetworkManager: <information>^IActivation (eth0) failure scheduled... 
Nov 21 14:27:06 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 3 of 5 (IP Configure Start) complete. 
Nov 21 14:27:06 ubuntu NetworkManager: <information>^IActivation (eth0) failed. 
Nov 21 14:27:06 ubuntu NetworkManager: <information>^IDeactivating device eth0. 
Nov 21 14:27:07 ubuntu NetworkManager: <information>^ISWITCH: no current connection, found better connection 'eth0'. 
Nov 21 14:27:07 ubuntu NetworkManager: <information>^IWill activate connection 'eth0'. 
Nov 21 14:27:07 ubuntu NetworkManager: <information>^IDevice eth0 activation scheduled... 
Nov 21 14:27:07 ubuntu NetworkManager: <information>^IActivation (eth0) started... 
Nov 21 14:27:07 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 1 of 5 (Device Prepare) scheduled... 
Nov 21 14:27:07 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 1 of 5 (Device Prepare) started... 
Nov 21 14:27:07 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 2 of 5 (Device Configure) scheduled... 
Nov 21 14:27:07 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 1 of 5 (Device Prepare) complete. 
Nov 21 14:27:07 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 2 of 5 (Device Configure) starting... 
Nov 21 14:27:07 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 2 of 5 (Device Configure) successful. 
Nov 21 14:27:07 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 3 of 5 (IP Configure Start) scheduled. 
Nov 21 14:27:07 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 2 of 5 (Device Configure) complete. 
Nov 21 14:27:07 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 3 of 5 (IP Configure Start) started... 
Nov 21 14:27:08 ubuntu avahi-autoipd(eth0)[11237]: Callout BIND, address 169.254.8.77 on interface eth0
Nov 21 14:27:08 ubuntu avahi-daemon[5202]: Joining mDNS multicast group on interface eth0.IPv4 with address 169.254.8.77.
Nov 21 14:27:08 ubuntu avahi-daemon[5202]: New relevant interface eth0.IPv4 for mDNS.
Nov 21 14:27:08 ubuntu avahi-daemon[5202]: Registering new address record for 169.254.8.77 on eth0.IPv4.
Nov 21 14:27:09 ubuntu NetworkManager: <information>^IActivation (eth0) Beginning DHCP transaction. 
Nov 21 14:27:09 ubuntu NetworkManager: <information>^ICouldn't send DHCP 'up' message because: name 'com.redhat.dhcp.OperationInProgress', message 'interface eth0 is being released. Please try again later.'. 
Nov 21 14:27:09 ubuntu NetworkManager: <information>^IActivation (eth0) failed. 
Nov 21 14:27:09 ubuntu NetworkManager: <information>^IDeactivating device eth0. 
Nov 21 14:27:09 ubuntu NetworkManager: <information>^IActivation (eth0) failure scheduled... 
Nov 21 14:27:09 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 3 of 5 (IP Configure Start) complete. 
Nov 21 14:27:10 ubuntu avahi-daemon[5202]: Withdrawing address record for 169.254.8.77 on eth0.
Nov 21 14:27:10 ubuntu avahi-daemon[5202]: Leaving mDNS multicast group on interface eth0.IPv4 with address 169.254.8.77.
Nov 21 14:27:10 ubuntu avahi-daemon[5202]: Interface eth0.IPv4 no longer relevant for mDNS.
Nov 21 14:27:10 ubuntu NetworkManager: <information>^ISWITCH: no current connection, found better connection 'eth0'. 
Nov 21 14:27:10 ubuntu NetworkManager: <information>^IWill activate connection 'eth0'. 
Nov 21 14:27:10 ubuntu NetworkManager: <information>^IDevice eth0 activation scheduled... 
Nov 21 14:27:10 ubuntu NetworkManager: <information>^IActivation (eth0) started... 
Nov 21 14:27:10 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 1 of 5 (Device Prepare) scheduled... 
Nov 21 14:27:10 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 1 of 5 (Device Prepare) started... 
Nov 21 14:27:10 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 2 of 5 (Device Configure) scheduled... 
Nov 21 14:27:10 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 1 of 5 (Device Prepare) complete. 
Nov 21 14:27:10 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 2 of 5 (Device Configure) starting... 
Nov 21 14:27:10 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 2 of 5 (Device Configure) successful. 
Nov 21 14:27:10 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 3 of 5 (IP Configure Start) scheduled. 
Nov 21 14:27:10 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 2 of 5 (Device Configure) complete. 
Nov 21 14:27:10 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 3 of 5 (IP Configure Start) started... 
Nov 21 14:27:12 ubuntu avahi-autoipd(eth0)[11237]: Successfully claimed IP address 169.254.8.77
Nov 21 14:27:12 ubuntu avahi-autoipd(eth0)[11237]: fopen() failed: Permission denied
Nov 21 14:27:12 ubuntu NetworkManager: <information>^IActivation (eth0) Beginning DHCP transaction. 
Nov 21 14:27:12 ubuntu NetworkManager: <information>^ICouldn't send DHCP 'up' message because: name 'com.redhat.dhcp.OperationInProgress', message 'interface eth0 is being released. Please try again later.'. 
Nov 21 14:27:12 ubuntu NetworkManager: <information>^IActivation (eth0) failure scheduled... 
Nov 21 14:27:12 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 3 of 5 (IP Configure Start) complete. 
Nov 21 14:27:12 ubuntu NetworkManager: <information>^IActivation (eth0) failed. 
Nov 21 14:27:12 ubuntu NetworkManager: <information>^IDeactivating device eth0. 
Nov 21 14:27:13 ubuntu NetworkManager: <information>^ISWITCH: no current connection, found better connection 'eth0'. 
Nov 21 14:27:13 ubuntu NetworkManager: <information>^IWill activate connection 'eth0'. 
Nov 21 14:27:13 ubuntu NetworkManager: <information>^IDevice eth0 activation scheduled... 
Nov 21 14:27:13 ubuntu NetworkManager: <information>^IActivation (eth0) started... 
Nov 21 14:27:13 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 1 of 5 (Device Prepare) scheduled... 
Nov 21 14:27:13 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 1 of 5 (Device Prepare) started... 
Nov 21 14:27:13 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 2 of 5 (Device Configure) scheduled... 
Nov 21 14:27:13 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 1 of 5 (Device Prepare) complete. 
Nov 21 14:27:13 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 2 of 5 (Device Configure) starting... 
Nov 21 14:27:13 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 2 of 5 (Device Configure) successful. 
Nov 21 14:27:13 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 3 of 5 (IP Configure Start) scheduled. 
Nov 21 14:27:13 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 2 of 5 (Device Configure) complete. 
Nov 21 14:27:13 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 3 of 5 (IP Configure Start) started... 
Nov 21 14:27:14 ubuntu NetworkManager: <information>^IActivation (eth0) Beginning DHCP transaction. 
Nov 21 14:27:14 ubuntu dhclient: There is already a pid file /var/run/dhclient.eth0.pid with pid 134993440
Nov 21 14:27:14 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 3 of 5 (IP Configure Start) complete. 
Nov 21 14:27:14 ubuntu NetworkManager: <information>^IDHCP daemon state is now 12 (successfully started) for interface eth0 
Nov 21 14:27:14 ubuntu avahi-autoipd(eth0)[11237]: Got SIGTERM, quitting.
Nov 21 14:27:14 ubuntu avahi-autoipd(eth0)[11237]: Callout STOP, address 169.254.8.77 on interface eth0
Nov 21 14:27:14 ubuntu avahi-autoipd(eth0)[11238]: client: RTNETLINK answers: No such device
Nov 21 14:27:14 ubuntu avahi-autoipd(eth0)[11238]: Script execution failed with return value 2
Nov 21 14:27:15 ubuntu NetworkManager: <information>^IDHCP daemon state is now 1 (starting) for interface eth0 
Nov 21 14:27:18 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
Nov 21 14:27:18 ubuntu dhclient: DHCPOFFER from 192.168.15.1
Nov 21 14:27:18 ubuntu dhclient: DHCPREQUEST on eth0 to 255.255.255.255 port 67
Nov 21 14:27:18 ubuntu dhclient: DHCPACK from 192.168.15.1
Nov 21 14:27:18 ubuntu avahi-daemon[5202]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.15.102.
Nov 21 14:27:18 ubuntu avahi-daemon[5202]: New relevant interface eth0.IPv4 for mDNS.
Nov 21 14:27:18 ubuntu avahi-daemon[5202]: Registering new address record for 192.168.15.102 on eth0.IPv4.
Nov 21 14:27:18 ubuntu NetworkManager: <information>^IDHCP daemon state is now 2 (bound) for interface eth0 
Nov 21 14:27:18 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 4 of 5 (IP Configure Get) scheduled... 
Nov 21 14:27:18 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 4 of 5 (IP Configure Get) started... 
Nov 21 14:27:18 ubuntu NetworkManager: <information>^IRetrieved the following IP4 configuration from the DHCP daemon: 
Nov 21 14:27:18 ubuntu NetworkManager: <information>^I  address 192.168.15.102 
Nov 21 14:27:18 ubuntu NetworkManager: <information>^I  netmask 255.255.255.0 
Nov 21 14:27:18 ubuntu dhclient: bound to 192.168.15.102 -- renewal in 38999 seconds.
Nov 21 14:27:18 ubuntu NetworkManager: <information>^I  broadcast 192.168.15.255 
Nov 21 14:27:18 ubuntu NetworkManager: <information>^I  gateway 192.168.15.1 
Nov 21 14:27:18 ubuntu NetworkManager: <information>^I  nameserver 192.168.15.1 
Nov 21 14:27:19 ubuntu NetworkManager: <information>^I  hostname 'ubuntu' 
Nov 21 14:27:19 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 5 of 5 (IP Configure Commit) scheduled... 
Nov 21 14:27:19 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 4 of 5 (IP Configure Get) complete. 
Nov 21 14:27:19 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 5 of 5 (IP Configure Commit) started... 
Nov 21 14:27:19 ubuntu avahi-daemon[5202]: Withdrawing address record for 192.168.15.102 on eth0.
Nov 21 14:27:19 ubuntu avahi-daemon[5202]: Leaving mDNS multicast group on interface eth0.IPv4 with address 192.168.15.102.
Nov 21 14:27:19 ubuntu avahi-daemon[5202]: Interface eth0.IPv4 no longer relevant for mDNS.
Nov 21 14:27:19 ubuntu avahi-daemon[5202]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.15.102.
Nov 21 14:27:19 ubuntu avahi-daemon[5202]: New relevant interface eth0.IPv4 for mDNS.
Nov 21 14:27:19 ubuntu avahi-daemon[5202]: Registering new address record for 192.168.15.102 on eth0.IPv4.
Nov 21 14:27:19 ubuntu NetworkManager: <information>^IClearing nscd hosts cache. 
Nov 21 14:27:20 ubuntu NetworkManager: <WARNING>^I nm_spawn_process (): nm_spawn_process('/usr/sbin/nscd -i hosts'): could not spawn process. (Failed to execute child process "/usr/sbin/nscd" (No such file or directory))  
Nov 21 14:27:20 ubuntu NetworkManager: <information>^IActivation (eth0) successful, device activated. 
Nov 21 14:27:20 ubuntu NetworkManager: <information>^IActivation (eth0) Finish handler scheduled. 
Nov 21 14:27:20 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 5 of 5 (IP Configure Commit) complete. 
Nov 21 14:27:21 ubuntu avahi-daemon[5202]: Registering new address record for fe80::203:25ff:fe3f:b1e6 on eth0.*.
Nov 21 14:27:33 ubuntu ntpdate[11408]: adjust time server 91.189.94.4 offset 0.117444 sec
Nov 21 16:46:56 ubuntu gdm[5253]: Restarting computer...
Nov 21 16:46:57 ubuntu hald: unmounted /dev/sda1 from '/media/disk' on behalf of uid 1000
Nov 21 16:47:00 ubuntu init: tty4 main process (4614) killed by TERM signal
Nov 21 16:47:00 ubuntu init: tty5 main process (4615) killed by TERM signal
Nov 21 16:47:00 ubuntu init: tty2 main process (4617) killed by TERM signal
Nov 21 16:47:00 ubuntu init: tty3 main process (4619) killed by TERM signal
Nov 21 16:47:00 ubuntu init: tty1 main process (4621) killed by TERM signal
Nov 21 16:47:00 ubuntu init: tty6 main process (4622) killed by TERM signal
Nov 21 16:48:47 ubuntu NetworkManager: <information>^Istarting... 
Nov 21 16:48:48 ubuntu NetworkManager: <information>^Ieth0: Device is fully-supported using driver 'sky2'. 
Nov 21 16:48:48 ubuntu NetworkManager: <information>^Inm_device_init(): waiting for device's worker thread to start 
Nov 21 16:48:48 ubuntu NetworkManager: <information>^Inm_device_init(): device's worker thread started, continuing. 
Nov 21 16:48:48 ubuntu NetworkManager: <information>^INow managing wired Ethernet (802.3) device 'eth0'. 
Nov 21 16:48:48 ubuntu NetworkManager: <information>^IDeactivating device eth0. 
Nov 21 16:48:48 ubuntu avahi-daemon[5374]: Found user 'avahi' (UID 105) and group 'avahi' (GID 111).
Nov 21 16:48:48 ubuntu avahi-daemon[5374]: Successfully dropped root privileges.
Nov 21 16:48:48 ubuntu avahi-daemon[5374]: avahi-daemon 0.6.17 starting up.
Nov 21 16:48:48 ubuntu avahi-daemon[5374]: Successfully called chroot().
Nov 21 16:48:48 ubuntu avahi-daemon[5374]: Successfully dropped remaining capabilities.
Nov 21 16:48:48 ubuntu NetworkManager: <information>^IWill activate wired connection 'eth0' because it now has a link. 
Nov 21 16:48:48 ubuntu avahi-daemon[5374]: No service found in /etc/avahi/services.
Nov 21 16:48:48 ubuntu NetworkManager: <information>^ISWITCH: no current connection, found better connection 'eth0'. 
Nov 21 16:48:48 ubuntu avahi-daemon[5374]: Network interface enumeration completed.
Nov 21 16:48:48 ubuntu NetworkManager: <information>^IWill activate connection 'eth0'. 
Nov 21 16:48:48 ubuntu avahi-daemon[5374]: Registering HINFO record with values 'I686'/'LINUX'.
Nov 21 16:48:48 ubuntu NetworkManager: <information>^IDevice eth0 activation scheduled... 
Nov 21 16:48:48 ubuntu avahi-daemon[5374]: Server startup complete. Host name is ubuntu.local. Local service cookie is 597442820.
Nov 21 16:48:48 ubuntu NetworkManager: <information>^IActivation (eth0) started... 
Nov 21 16:48:48 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 1 of 5 (Device Prepare) scheduled... 
Nov 21 16:48:48 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 1 of 5 (Device Prepare) started... 
Nov 21 16:48:48 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 2 of 5 (Device Configure) scheduled... 
Nov 21 16:48:48 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 1 of 5 (Device Prepare) complete. 
Nov 21 16:48:48 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 2 of 5 (Device Configure) starting... 
Nov 21 16:48:48 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 2 of 5 (Device Configure) successful. 
Nov 21 16:48:48 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 3 of 5 (IP Configure Start) scheduled. 
Nov 21 16:48:48 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 2 of 5 (Device Configure) complete. 
Nov 21 16:48:48 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 3 of 5 (IP Configure Start) started... 
Nov 21 16:48:49 ubuntu NetworkManager: <information>^IActivation (eth0) Beginning DHCP transaction. 
Nov 21 16:48:49 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 3 of 5 (IP Configure Start) complete. 
Nov 21 16:48:50 ubuntu NetworkManager: <information>^IDHCP daemon state is now 12 (successfully started) for interface eth0 
Nov 21 16:48:51 ubuntu NetworkManager: <information>^IDHCP daemon state is now 1 (starting) for interface eth0 
Nov 21 16:48:52 ubuntu hcid[5620]: Bluetooth HCI daemon
Nov 21 16:48:53 ubuntu hcid[5620]: Starting SDP server
Nov 21 16:48:53 ubuntu NetworkManager: <debug info>^I[1195681732.293934] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_bluetooth'). 
Nov 21 16:48:54 ubuntu dhclient: DHCPREQUEST on eth0 to 255.255.255.255 port 67
Nov 21 16:48:54 ubuntu dhclient: DHCPACK from 192.168.15.1
Nov 21 16:48:54 ubuntu avahi-daemon[5374]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.15.102.
Nov 21 16:48:54 ubuntu avahi-daemon[5374]: New relevant interface eth0.IPv4 for mDNS.
Nov 21 16:48:54 ubuntu avahi-daemon[5374]: Registering new address record for 192.168.15.102 on eth0.IPv4.
Nov 21 16:48:54 ubuntu NetworkManager: <information>^IDHCP daemon state is now 4 (reboot) for interface eth0 
Nov 21 16:48:54 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 4 of 5 (IP Configure Get) scheduled... 
Nov 21 16:48:54 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 4 of 5 (IP Configure Get) started... 
Nov 21 16:48:54 ubuntu NetworkManager: <information>^IRetrieved the following IP4 configuration from the DHCP daemon: 
Nov 21 16:48:54 ubuntu NetworkManager: <information>^I  address 192.168.15.102 
Nov 21 16:48:54 ubuntu NetworkManager: <information>^I  netmask 255.255.255.0 
Nov 21 16:48:54 ubuntu dhclient: bound to 192.168.15.102 -- renewal in 34945 seconds.
Nov 21 16:48:54 ubuntu NetworkManager: <information>^I  broadcast 192.168.15.255 
Nov 21 16:48:54 ubuntu NetworkManager: <information>^I  gateway 192.168.15.1 
Nov 21 16:48:54 ubuntu NetworkManager: <information>^I  nameserver 192.168.15.1 
Nov 21 16:48:54 ubuntu NetworkManager: <information>^I  hostname 'ubuntu' 
Nov 21 16:48:54 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 5 of 5 (IP Configure Commit) scheduled... 
Nov 21 16:48:54 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 4 of 5 (IP Configure Get) complete. 
Nov 21 16:48:54 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 5 of 5 (IP Configure Commit) started... 
Nov 21 16:48:55 ubuntu avahi-daemon[5374]: Withdrawing address record for 192.168.15.102 on eth0.
Nov 21 16:48:55 ubuntu avahi-daemon[5374]: Leaving mDNS multicast group on interface eth0.IPv4 with address 192.168.15.102.
Nov 21 16:48:55 ubuntu avahi-daemon[5374]: Interface eth0.IPv4 no longer relevant for mDNS.
Nov 21 16:48:55 ubuntu avahi-daemon[5374]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.15.102.
Nov 21 16:48:55 ubuntu avahi-daemon[5374]: New relevant interface eth0.IPv4 for mDNS.
Nov 21 16:48:55 ubuntu avahi-daemon[5374]: Registering new address record for 192.168.15.102 on eth0.IPv4.
Nov 21 16:48:55 ubuntu NetworkManager: <information>^IClearing nscd hosts cache. 
Nov 21 16:48:55 ubuntu NetworkManager: <WARNING>^I nm_spawn_process (): nm_spawn_process('/usr/sbin/nscd -i hosts'): could not spawn process. (Failed to execute child process "/usr/sbin/nscd" (No such file or directory))  
Nov 21 16:48:56 ubuntu NetworkManager: <information>^IActivation (eth0) Finish handler scheduled. 
Nov 21 16:48:56 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 5 of 5 (IP Configure Commit) complete. 
Nov 21 16:48:56 ubuntu NetworkManager: <information>^IActivation (eth0) successful, device activated. 
Nov 21 16:48:57 ubuntu avahi-daemon[5374]: Registering new address record for fe80::203:25ff:fe3f:b1e6 on eth0.*.
Nov 21 16:49:06 ubuntu ntpdate[5845]: step time server 91.189.94.4 offset -0.653365 sec
Nov 21 16:49:31 ubuntu hald: mounted /dev/sda1 on behalf of uid 1000
Nov 21 16:49:40 ubuntu NetworkManager: <information>^IUpdating allowed wireless network lists. 
Nov 21 16:49:40 ubuntu NetworkManager: <WARNING>^I nm_dbus_get_networks_cb (): error received: org.freedesktop.NetworkManagerInfo.NoNetworks - There are no wireless networks stored.. 
Nov 21 16:53:20 ubuntu NetworkManager: <information>^ISWITCH: terminating current connection 'eth0' because it's no longer valid. 
Nov 21 16:53:20 ubuntu NetworkManager: <information>^IDeactivating device eth0. 
Nov 21 16:53:20 ubuntu dhclient: There is already a pid file /var/run/dhclient.eth0.pid with pid 5468
Nov 21 16:53:20 ubuntu dhclient: killed old client process, removed PID file
Nov 21 16:53:20 ubuntu dhclient: DHCPRELEASE on eth0 to 192.168.15.1 port 67
Nov 21 16:53:20 ubuntu avahi-daemon[5374]: Withdrawing address record for 192.168.15.102 on eth0.
Nov 21 16:53:20 ubuntu avahi-daemon[5374]: Leaving mDNS multicast group on interface eth0.IPv4 with address 192.168.15.102.
Nov 21 16:53:20 ubuntu avahi-daemon[5374]: Interface eth0.IPv4 no longer relevant for mDNS.
Nov 21 16:53:20 ubuntu avahi-autoipd(eth0)[6359]: Found user 'avahi-autoipd' (UID 104) and group 'avahi-autoipd' (GID 110).
Nov 21 16:53:20 ubuntu avahi-autoipd(eth0)[6359]: Successfully called chroot().
Nov 21 16:53:20 ubuntu avahi-autoipd(eth0)[6359]: Successfully dropped root privileges.
Nov 21 16:53:20 ubuntu avahi-autoipd(eth0)[6359]: fopen() failed: Permission denied
Nov 21 16:53:20 ubuntu avahi-autoipd(eth0)[6359]: Starting with address 169.254.8.77
Nov 21 16:53:20 ubuntu avahi-daemon[5374]: Withdrawing address record for fe80::203:25ff:fe3f:b1e6 on eth0.
Nov 21 16:53:21 ubuntu NetworkManager: nm_device_is_802_3_ethernet: assertion `dev != NULL' failed
Nov 21 16:53:21 ubuntu NetworkManager: nm_device_is_802_11_wireless: assertion `dev != NULL' failed
Nov 21 16:53:24 ubuntu avahi-autoipd(eth0)[6359]: Callout BIND, address 169.254.8.77 on interface eth0
Nov 21 16:53:24 ubuntu avahi-daemon[5374]: Joining mDNS multicast group on interface eth0.IPv4 with address 169.254.8.77.
Nov 21 16:53:24 ubuntu avahi-daemon[5374]: New relevant interface eth0.IPv4 for mDNS.
Nov 21 16:53:24 ubuntu avahi-daemon[5374]: Registering new address record for 169.254.8.77 on eth0.IPv4.
Nov 21 16:53:28 ubuntu avahi-autoipd(eth0)[6359]: Successfully claimed IP address 169.254.8.77
Nov 21 16:53:28 ubuntu avahi-autoipd(eth0)[6359]: fopen() failed: Permission denied
Nov 21 16:53:35 ubuntu hald: unmounted /dev/sda1 from '/media/disk' on behalf of uid 1000
Nov 21 16:53:35 ubuntu NetworkManager: <debug info>^I[1195682015.754472] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_352D_1380'). 
Nov 21 16:53:49 ubuntu NetworkManager: <debug info>^I[1195682029.416204] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_718_65_AA0070006371905A_if0_scsi_device_lun0_scsi_generic'). 
Nov 21 16:53:49 ubuntu NetworkManager: <debug info>^I[1195682029.420232] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/storage_serial_Imation_USB_Flash_Drive_AA0070006371905A_0_0'). 
Nov 21 16:53:49 ubuntu NetworkManager: <debug info>^I[1195682029.431711] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_718_65_AA0070006371905A_if0_scsi_device_lun0'). 
Nov 21 16:53:49 ubuntu NetworkManager: <debug info>^I[1195682029.431871] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_718_65_AA0070006371905A_if0_scsi_host'). 
Nov 21 16:53:49 ubuntu NetworkManager: <debug info>^I[1195682029.435396] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_718_65_AA0070006371905A_if0'). 
Nov 21 16:53:49 ubuntu NetworkManager: <debug info>^I[1195682029.436784] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_718_65_AA0070006371905A'). 
Nov 21 16:53:49 ubuntu NetworkManager: <debug info>^I[1195682029.442253] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_718_65_AA0070006371905A_usbraw'). 
Nov 21 17:25:11 ubuntu NetworkManager: <information>^IWill activate wired connection 'eth0' because it now has a link. 
Nov 21 17:25:11 ubuntu NetworkManager: <information>^ISWITCH: no current connection, found better connection 'eth0'. 
Nov 21 17:25:11 ubuntu NetworkManager: <information>^IWill activate connection 'eth0'. 
Nov 21 17:25:11 ubuntu NetworkManager: <information>^IDevice eth0 activation scheduled... 
Nov 21 17:25:11 ubuntu NetworkManager: <information>^IActivation (eth0) started... 
Nov 21 17:25:11 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 1 of 5 (Device Prepare) scheduled... 
Nov 21 17:25:11 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 1 of 5 (Device Prepare) started... 
Nov 21 17:25:11 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 2 of 5 (Device Configure) scheduled... 
Nov 21 17:25:11 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 1 of 5 (Device Prepare) complete. 
Nov 21 17:25:11 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 2 of 5 (Device Configure) starting... 
Nov 21 17:25:11 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 2 of 5 (Device Configure) successful. 
Nov 21 17:25:11 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 3 of 5 (IP Configure Start) scheduled. 
Nov 21 17:25:11 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 2 of 5 (Device Configure) complete. 
Nov 21 17:25:11 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 3 of 5 (IP Configure Start) started... 
Nov 21 17:25:12 ubuntu NetworkManager: <information>^IActivation (eth0) Beginning DHCP transaction. 
Nov 21 17:25:12 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 3 of 5 (IP Configure Start) complete. 
Nov 21 17:25:12 ubuntu dhclient: There is already a pid file /var/run/dhclient.eth0.pid with pid 134993440
Nov 21 17:25:12 ubuntu NetworkManager: <information>^IDHCP daemon state is now 12 (successfully started) for interface eth0 
Nov 21 17:25:12 ubuntu avahi-autoipd(eth0)[6359]: Got SIGTERM, quitting.
Nov 21 17:25:12 ubuntu avahi-autoipd(eth0)[6359]: Callout STOP, address 169.254.8.77 on interface eth0
Nov 21 17:25:12 ubuntu avahi-daemon[5374]: Withdrawing address record for 169.254.8.77 on eth0.
Nov 21 17:25:12 ubuntu avahi-daemon[5374]: Leaving mDNS multicast group on interface eth0.IPv4 with address 169.254.8.77.
Nov 21 17:25:12 ubuntu avahi-daemon[5374]: Interface eth0.IPv4 no longer relevant for mDNS.
Nov 21 17:25:12 ubuntu avahi-autoipd(eth0)[6360]: client: RTNETLINK answers: No such process
Nov 21 17:25:12 ubuntu avahi-daemon[5374]: Registering new address record for fe80::203:25ff:fe3f:b1e6 on eth0.*.
Nov 21 17:25:13 ubuntu NetworkManager: <information>^IDHCP daemon state is now 1 (starting) for interface eth0 
Nov 21 17:25:14 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
Nov 21 17:25:14 ubuntu dhclient: DHCPOFFER from 192.168.15.1
Nov 21 17:25:14 ubuntu dhclient: DHCPREQUEST on eth0 to 255.255.255.255 port 67
Nov 21 17:25:14 ubuntu dhclient: DHCPACK from 192.168.15.1
Nov 21 17:25:14 ubuntu avahi-daemon[5374]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.15.102.
Nov 21 17:25:14 ubuntu avahi-daemon[5374]: New relevant interface eth0.IPv4 for mDNS.
Nov 21 17:25:14 ubuntu avahi-daemon[5374]: Registering new address record for 192.168.15.102 on eth0.IPv4.
Nov 21 17:25:14 ubuntu NetworkManager: <information>^IDHCP daemon state is now 2 (bound) for interface eth0 
Nov 21 17:25:14 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 4 of 5 (IP Configure Get) scheduled... 
Nov 21 17:25:14 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 4 of 5 (IP Configure Get) started... 
Nov 21 17:25:14 ubuntu NetworkManager: <information>^IRetrieved the following IP4 configuration from the DHCP daemon: 
Nov 21 17:25:14 ubuntu NetworkManager: <information>^I  address 192.168.15.102 
Nov 21 17:25:14 ubuntu NetworkManager: <information>^I  netmask 255.255.255.0 
Nov 21 17:25:14 ubuntu NetworkManager: <information>^I  broadcast 192.168.15.255 
Nov 21 17:25:14 ubuntu NetworkManager: <information>^I  gateway 192.168.15.1 
Nov 21 17:25:14 ubuntu NetworkManager: <information>^I  nameserver 192.168.15.1 
Nov 21 17:25:14 ubuntu NetworkManager: <information>^I  hostname 'ubuntu' 
Nov 21 17:25:14 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 5 of 5 (IP Configure Commit) scheduled... 
Nov 21 17:25:14 ubuntu dhclient: bound to 192.168.15.102 -- renewal in 38440 seconds.
Nov 21 17:25:14 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 4 of 5 (IP Configure Get) complete. 
Nov 21 17:25:14 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 5 of 5 (IP Configure Commit) started... 
Nov 21 17:25:14 ubuntu avahi-daemon[5374]: Withdrawing address record for 192.168.15.102 on eth0.
Nov 21 17:25:14 ubuntu avahi-daemon[5374]: Leaving mDNS multicast group on interface eth0.IPv4 with address 192.168.15.102.
Nov 21 17:25:14 ubuntu avahi-daemon[5374]: Interface eth0.IPv4 no longer relevant for mDNS.
Nov 21 17:25:14 ubuntu avahi-daemon[5374]: Withdrawing address record for fe80::203:25ff:fe3f:b1e6 on eth0.
Nov 21 17:25:14 ubuntu avahi-daemon[5374]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.15.102.
Nov 21 17:25:14 ubuntu avahi-daemon[5374]: New relevant interface eth0.IPv4 for mDNS.
Nov 21 17:25:14 ubuntu avahi-daemon[5374]: Registering new address record for 192.168.15.102 on eth0.IPv4.
Nov 21 17:25:15 ubuntu NetworkManager: <information>^IClearing nscd hosts cache. 
Nov 21 17:25:15 ubuntu NetworkManager: <WARNING>^I nm_spawn_process (): nm_spawn_process('/usr/sbin/nscd -i hosts'): could not spawn process. (Failed to execute child process "/usr/sbin/nscd" (No such file or directory))  
Nov 21 17:25:15 ubuntu NetworkManager: <information>^IActivation (eth0) successful, device activated. 
Nov 21 17:25:15 ubuntu NetworkManager: <information>^IActivation (eth0) Finish handler scheduled. 
Nov 21 17:25:15 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 5 of 5 (IP Configure Commit) complete. 
Nov 21 17:25:16 ubuntu avahi-daemon[5374]: Registering new address record for fe80::203:25ff:fe3f:b1e6 on eth0.*.
Nov 21 17:25:27 ubuntu ntpdate[8890]: adjust time server 91.189.94.4 offset 0.215564 sec
Nov 21 17:30:25 ubuntu NetworkManager: <information>^ISWITCH: terminating current connection 'eth0' because it's no longer valid. 
Nov 21 17:30:25 ubuntu NetworkManager: <information>^IDeactivating device eth0. 
Nov 21 17:30:25 ubuntu dhclient: There is already a pid file /var/run/dhclient.eth0.pid with pid 8803
Nov 21 17:30:25 ubuntu dhclient: killed old client process, removed PID file
Nov 21 17:30:25 ubuntu dhclient: DHCPRELEASE on eth0 to 192.168.15.1 port 67
Nov 21 17:30:25 ubuntu avahi-autoipd(eth0)[9406]: Found user 'avahi-autoipd' (UID 104) and group 'avahi-autoipd' (GID 110).
Nov 21 17:30:25 ubuntu avahi-daemon[5374]: Withdrawing address record for 192.168.15.102 on eth0.
Nov 21 17:30:25 ubuntu avahi-daemon[5374]: Leaving mDNS multicast group on interface eth0.IPv4 with address 192.168.15.102.
Nov 21 17:30:26 ubuntu avahi-daemon[5374]: Interface eth0.IPv4 no longer relevant for mDNS.
Nov 21 17:30:26 ubuntu avahi-autoipd(eth0)[9406]: Successfully called chroot().
Nov 21 17:30:26 ubuntu avahi-autoipd(eth0)[9406]: Successfully dropped root privileges.
Nov 21 17:30:26 ubuntu avahi-autoipd(eth0)[9406]: fopen() failed: Permission denied
Nov 21 17:30:26 ubuntu avahi-autoipd(eth0)[9406]: Starting with address 169.254.8.77
Nov 21 17:30:26 ubuntu avahi-daemon[5374]: Withdrawing address record for fe80::203:25ff:fe3f:b1e6 on eth0.
Nov 21 17:30:26 ubuntu NetworkManager: nm_device_is_802_3_ethernet: assertion `dev != NULL' failed
Nov 21 17:30:26 ubuntu NetworkManager: nm_device_is_802_11_wireless: assertion `dev != NULL' failed
Nov 21 17:30:31 ubuntu avahi-autoipd(eth0)[9406]: Callout BIND, address 169.254.8.77 on interface eth0
Nov 21 17:30:31 ubuntu avahi-daemon[5374]: Joining mDNS multicast group on interface eth0.IPv4 with address 169.254.8.77.
Nov 21 17:30:31 ubuntu avahi-daemon[5374]: New relevant interface eth0.IPv4 for mDNS.
Nov 21 17:30:31 ubuntu avahi-daemon[5374]: Registering new address record for 169.254.8.77 on eth0.IPv4.
Nov 21 17:30:35 ubuntu avahi-autoipd(eth0)[9406]: Successfully claimed IP address 169.254.8.77
Nov 21 17:30:35 ubuntu avahi-autoipd(eth0)[9406]: fopen() failed: Permission denied
Nov 21 18:39:50 ubuntu NetworkManager: <information>^IWill activate wired connection 'eth0' because it now has a link. 
Nov 21 18:39:50 ubuntu NetworkManager: <information>^ISWITCH: no current connection, found better connection 'eth0'. 
Nov 21 18:39:50 ubuntu NetworkManager: <information>^IWill activate connection 'eth0'. 
Nov 21 18:39:51 ubuntu NetworkManager: <information>^IDevice eth0 activation scheduled... 
Nov 21 18:39:51 ubuntu NetworkManager: <information>^IActivation (eth0) started... 
Nov 21 18:39:51 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 1 of 5 (Device Prepare) scheduled... 
Nov 21 18:39:51 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 1 of 5 (Device Prepare) started... 
Nov 21 18:39:51 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 2 of 5 (Device Configure) scheduled... 
Nov 21 18:39:51 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 1 of 5 (Device Prepare) complete. 
Nov 21 18:39:51 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 2 of 5 (Device Configure) starting... 
Nov 21 18:39:51 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 2 of 5 (Device Configure) successful. 
Nov 21 18:39:51 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 3 of 5 (IP Configure Start) scheduled. 
Nov 21 18:39:51 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 2 of 5 (Device Configure) complete. 
Nov 21 18:39:51 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 3 of 5 (IP Configure Start) started... 
Nov 21 18:39:52 ubuntu avahi-daemon[5374]: Registering new address record for fe80::203:25ff:fe3f:b1e6 on eth0.*.
Nov 21 18:39:53 ubuntu NetworkManager: <information>^IActivation (eth0) Beginning DHCP transaction. 
Nov 21 18:39:53 ubuntu dhclient: There is already a pid file /var/run/dhclient.eth0.pid with pid 134993440
Nov 21 18:39:53 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 3 of 5 (IP Configure Start) complete. 
Nov 21 18:39:53 ubuntu NetworkManager: <information>^IDHCP daemon state is now 12 (successfully started) for interface eth0 
Nov 21 18:39:53 ubuntu avahi-autoipd(eth0)[9406]: Got SIGTERM, quitting.
Nov 21 18:39:53 ubuntu avahi-autoipd(eth0)[9406]: Callout STOP, address 169.254.8.77 on interface eth0
Nov 21 18:39:53 ubuntu avahi-daemon[5374]: Withdrawing address record for 169.254.8.77 on eth0.
Nov 21 18:39:53 ubuntu avahi-daemon[5374]: Leaving mDNS multicast group on interface eth0.IPv4 with address 169.254.8.77.
Nov 21 18:39:53 ubuntu avahi-daemon[5374]: Interface eth0.IPv4 no longer relevant for mDNS.
Nov 21 18:39:53 ubuntu avahi-autoipd(eth0)[9407]: client: RTNETLINK answers: No such process
Nov 21 18:39:54 ubuntu NetworkManager: <information>^IDHCP daemon state is now 1 (starting) for interface eth0 
Nov 21 18:39:56 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
Nov 21 18:39:56 ubuntu dhclient: DHCPOFFER from 192.168.15.1
Nov 21 18:39:56 ubuntu dhclient: DHCPREQUEST on eth0 to 255.255.255.255 port 67
Nov 21 18:39:56 ubuntu dhclient: DHCPACK from 192.168.15.1
Nov 21 18:39:56 ubuntu avahi-daemon[5374]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.15.102.
Nov 21 18:39:56 ubuntu avahi-daemon[5374]: New relevant interface eth0.IPv4 for mDNS.
Nov 21 18:39:56 ubuntu avahi-daemon[5374]: Registering new address record for 192.168.15.102 on eth0.IPv4.
Nov 21 18:39:56 ubuntu NetworkManager: <information>^IDHCP daemon state is now 2 (bound) for interface eth0 
Nov 21 18:39:56 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 4 of 5 (IP Configure Get) scheduled... 
Nov 21 18:39:56 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 4 of 5 (IP Configure Get) started... 
Nov 21 18:39:56 ubuntu NetworkManager: <information>^IRetrieved the following IP4 configuration from the DHCP daemon: 
Nov 21 18:39:56 ubuntu NetworkManager: <information>^I  address 192.168.15.102 
Nov 21 18:39:56 ubuntu NetworkManager: <information>^I  netmask 255.255.255.0 
Nov 21 18:39:56 ubuntu NetworkManager: <information>^I  broadcast 192.168.15.255 
Nov 21 18:39:56 ubuntu NetworkManager: <information>^I  gateway 192.168.15.1 
Nov 21 18:39:56 ubuntu NetworkManager: <information>^I  nameserver 192.168.15.1 
Nov 21 18:39:56 ubuntu NetworkManager: <information>^I  hostname 'ubuntu' 
Nov 21 18:39:56 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 5 of 5 (IP Configure Commit) scheduled... 
Nov 21 18:39:56 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 4 of 5 (IP Configure Get) complete. 
Nov 21 18:39:56 ubuntu dhclient: bound to 192.168.15.102 -- renewal in 33665 seconds.
Nov 21 18:39:56 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 5 of 5 (IP Configure Commit) started... 
Nov 21 18:39:56 ubuntu avahi-daemon[5374]: Withdrawing address record for 192.168.15.102 on eth0.
Nov 21 18:39:56 ubuntu avahi-daemon[5374]: Leaving mDNS multicast group on interface eth0.IPv4 with address 192.168.15.102.
Nov 21 18:39:56 ubuntu avahi-daemon[5374]: Interface eth0.IPv4 no longer relevant for mDNS.
Nov 21 18:39:56 ubuntu avahi-daemon[5374]: Withdrawing address record for fe80::203:25ff:fe3f:b1e6 on eth0.
Nov 21 18:39:56 ubuntu avahi-daemon[5374]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.15.102.
Nov 21 18:39:56 ubuntu avahi-daemon[5374]: New relevant interface eth0.IPv4 for mDNS.
Nov 21 18:39:56 ubuntu avahi-daemon[5374]: Registering new address record for 192.168.15.102 on eth0.IPv4.
Nov 21 18:39:57 ubuntu NetworkManager: <information>^IClearing nscd hosts cache. 
Nov 21 18:39:57 ubuntu NetworkManager: <WARNING>^I nm_spawn_process (): nm_spawn_process('/usr/sbin/nscd -i hosts'): could not spawn process. (Failed to execute child process "/usr/sbin/nscd" (No such file or directory))  
Nov 21 18:39:57 ubuntu NetworkManager: <information>^IActivation (eth0) successful, device activated. 
Nov 21 18:39:57 ubuntu NetworkManager: <information>^IActivation (eth0) Finish handler scheduled. 
Nov 21 18:39:57 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 5 of 5 (IP Configure Commit) complete. 
Nov 21 18:39:58 ubuntu avahi-daemon[5374]: Registering new address record for fe80::203:25ff:fe3f:b1e6 on eth0.*.
Nov 21 18:40:08 ubuntu ntpdate[14508]: adjust time server 91.189.94.4 offset 0.380911 sec
Nov 21 18:44:18 ubuntu gdm[5425]: Restarting computer...
Nov 21 18:44:20 ubuntu init: tty4 main process (4780) killed by TERM signal
Nov 21 18:44:20 ubuntu init: tty5 main process (4781) killed by TERM signal
Nov 21 18:44:21 ubuntu init: tty1 main process (4787) killed by TERM signal
Nov 21 18:44:21 ubuntu init: tty6 main process (4788) killed by TERM signal
Nov 21 18:44:21 ubuntu init: tty3 main process (4785) killed by TERM signal
Nov 21 18:44:21 ubuntu init: tty2 main process (4783) killed by TERM signal
Nov 21 18:46:04 ubuntu NetworkManager: <information>^Istarting... 
Nov 21 18:46:04 ubuntu NetworkManager: <information>^Ieth0: Device is fully-supported using driver 'sky2'. 
Nov 21 18:46:04 ubuntu NetworkManager: <information>^Inm_device_init(): waiting for device's worker thread to start 
Nov 21 18:46:04 ubuntu NetworkManager: <information>^Inm_device_init(): device's worker thread started, continuing. 
Nov 21 18:46:04 ubuntu NetworkManager: <information>^INow managing wired Ethernet (802.3) device 'eth0'. 
Nov 21 18:46:04 ubuntu NetworkManager: <information>^IDeactivating device eth0. 
Nov 21 18:46:04 ubuntu avahi-daemon[5197]: Found user 'avahi' (UID 105) and group 'avahi' (GID 111).
Nov 21 18:46:04 ubuntu avahi-daemon[5197]: Successfully dropped root privileges.
Nov 21 18:46:04 ubuntu avahi-daemon[5197]: avahi-daemon 0.6.17 starting up.
Nov 21 18:46:04 ubuntu avahi-daemon[5197]: Successfully called chroot().
Nov 21 18:46:04 ubuntu avahi-daemon[5197]: Successfully dropped remaining capabilities.
Nov 21 18:46:04 ubuntu avahi-daemon[5197]: No service found in /etc/avahi/services.
Nov 21 18:46:04 ubuntu avahi-daemon[5197]: Network interface enumeration completed.
Nov 21 18:46:05 ubuntu avahi-daemon[5197]: Registering HINFO record with values 'I686'/'LINUX'.
Nov 21 18:46:05 ubuntu avahi-daemon[5197]: Server startup complete. Host name is ubuntu.local. Local service cookie is 838683942.
Nov 21 18:46:07 ubuntu NetworkManager: <information>^IWill activate wired connection 'eth0' because it now has a link. 
Nov 21 18:46:07 ubuntu NetworkManager: <information>^ISWITCH: no current connection, found better connection 'eth0'. 
Nov 21 18:46:07 ubuntu NetworkManager: <information>^IWill activate connection 'eth0'. 
Nov 21 18:46:07 ubuntu NetworkManager: <information>^IDevice eth0 activation scheduled... 
Nov 21 18:46:07 ubuntu NetworkManager: <information>^IActivation (eth0) started... 
Nov 21 18:46:07 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 1 of 5 (Device Prepare) scheduled... 
Nov 21 18:46:07 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 1 of 5 (Device Prepare) started... 
Nov 21 18:46:08 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 2 of 5 (Device Configure) scheduled... 
Nov 21 18:46:08 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 1 of 5 (Device Prepare) complete. 
Nov 21 18:46:08 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 2 of 5 (Device Configure) starting... 
Nov 21 18:46:09 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 2 of 5 (Device Configure) successful. 
Nov 21 18:46:09 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 3 of 5 (IP Configure Start) scheduled. 
Nov 21 18:46:09 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 2 of 5 (Device Configure) complete. 
Nov 21 18:46:09 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 3 of 5 (IP Configure Start) started... 
Nov 21 18:46:09 ubuntu NetworkManager: <information>^IActivation (eth0) Beginning DHCP transaction. 
Nov 21 18:46:09 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 3 of 5 (IP Configure Start) complete. 
Nov 21 18:46:09 ubuntu NetworkManager: <information>^IDHCP daemon state is now 12 (successfully started) for interface eth0 
Nov 21 18:46:09 ubuntu hcid[5441]: Bluetooth HCI daemon
Nov 21 18:46:10 ubuntu hcid[5441]: Starting SDP server
Nov 21 18:46:10 ubuntu NetworkManager: <debug info>^I[1195688769.958769] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_bluetooth'). 
Nov 21 18:46:11 ubuntu NetworkManager: <information>^IDHCP daemon state is now 1 (starting) for interface eth0 
Nov 21 18:46:11 ubuntu dhclient: DHCPREQUEST on eth0 to 255.255.255.255 port 67
Nov 21 18:46:11 ubuntu dhclient: DHCPACK from 192.168.15.1
Nov 21 18:46:11 ubuntu avahi-daemon[5197]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.15.102.
Nov 21 18:46:11 ubuntu avahi-daemon[5197]: New relevant interface eth0.IPv4 for mDNS.
Nov 21 18:46:11 ubuntu avahi-daemon[5197]: Registering new address record for 192.168.15.102 on eth0.IPv4.
Nov 21 18:46:11 ubuntu NetworkManager: <information>^IDHCP daemon state is now 4 (reboot) for interface eth0 
Nov 21 18:46:12 ubuntu dhclient: bound to 192.168.15.102 -- renewal in 41153 seconds.
Nov 21 18:46:12 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 4 of 5 (IP Configure Get) scheduled... 
Nov 21 18:46:12 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 4 of 5 (IP Configure Get) started... 
Nov 21 18:46:12 ubuntu NetworkManager: <information>^IRetrieved the following IP4 configuration from the DHCP daemon: 
Nov 21 18:46:12 ubuntu NetworkManager: <information>^I  address 192.168.15.102 
Nov 21 18:46:12 ubuntu NetworkManager: <information>^I  netmask 255.255.255.0 
Nov 21 18:46:12 ubuntu NetworkManager: <information>^I  broadcast 192.168.15.255 
Nov 21 18:46:12 ubuntu NetworkManager: <information>^I  gateway 192.168.15.1 
Nov 21 18:46:12 ubuntu NetworkManager: <information>^I  nameserver 192.168.15.1 
Nov 21 18:46:12 ubuntu NetworkManager: <information>^I  hostname 'ubuntu' 
Nov 21 18:46:12 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 5 of 5 (IP Configure Commit) scheduled... 
Nov 21 18:46:12 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 4 of 5 (IP Configure Get) complete. 
Nov 21 18:46:12 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 5 of 5 (IP Configure Commit) started... 
Nov 21 18:46:12 ubuntu avahi-daemon[5197]: Withdrawing address record for 192.168.15.102 on eth0.
Nov 21 18:46:12 ubuntu avahi-daemon[5197]: Leaving mDNS multicast group on interface eth0.IPv4 with address 192.168.15.102.
Nov 21 18:46:12 ubuntu avahi-daemon[5197]: Interface eth0.IPv4 no longer relevant for mDNS.
Nov 21 18:46:12 ubuntu avahi-daemon[5197]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.15.102.
Nov 21 18:46:12 ubuntu avahi-daemon[5197]: New relevant interface eth0.IPv4 for mDNS.
Nov 21 18:46:12 ubuntu avahi-daemon[5197]: Registering new address record for 192.168.15.102 on eth0.IPv4.
Nov 21 18:46:13 ubuntu NetworkManager: <information>^IClearing nscd hosts cache. 
Nov 21 18:46:13 ubuntu NetworkManager: <WARNING>^I nm_spawn_process (): nm_spawn_process('/usr/sbin/nscd -i hosts'): could not spawn process. (Failed to execute child process "/usr/sbin/nscd" (No such file or directory))  
Nov 21 18:46:13 ubuntu NetworkManager: <information>^IActivation (eth0) Finish handler scheduled. 
Nov 21 18:46:13 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 5 of 5 (IP Configure Commit) complete. 
Nov 21 18:46:13 ubuntu NetworkManager: <information>^IActivation (eth0) successful, device activated. 
Nov 21 18:46:15 ubuntu avahi-daemon[5197]: Registering new address record for fe80::203:25ff:fe3f:b1e6 on eth0.*.
Nov 21 18:46:24 ubuntu ntpdate[5684]: adjust time server 91.189.94.4 offset -0.425083 sec
Nov 21 18:46:51 ubuntu NetworkManager: <information>^IUpdating allowed wireless network lists. 
Nov 21 18:46:52 ubuntu NetworkManager: <WARNING>^I nm_dbus_get_networks_cb (): error received: org.freedesktop.NetworkManagerInfo.NoNetworks - There are no wireless networks stored.. 
Nov 21 18:50:09 ubuntu NetworkManager: <information>^ISWITCH: terminating current connection 'eth0' because it's no longer valid. 
Nov 21 18:50:09 ubuntu NetworkManager: <information>^IDeactivating device eth0. 
Nov 21 18:50:09 ubuntu dhclient: There is already a pid file /var/run/dhclient.eth0.pid with pid 5325
Nov 21 18:50:09 ubuntu dhclient: killed old client process, removed PID file
Nov 21 18:50:09 ubuntu dhclient: DHCPRELEASE on eth0 to 192.168.15.1 port 67
Nov 21 18:50:09 ubuntu avahi-daemon[5197]: Withdrawing address record for 192.168.15.102 on eth0.
Nov 21 18:50:09 ubuntu avahi-daemon[5197]: Leaving mDNS multicast group on interface eth0.IPv4 with address 192.168.15.102.
Nov 21 18:50:09 ubuntu avahi-daemon[5197]: Interface eth0.IPv4 no longer relevant for mDNS.
Nov 21 18:50:09 ubuntu avahi-autoipd(eth0)[5999]: Found user 'avahi-autoipd' (UID 104) and group 'avahi-autoipd' (GID 110).
Nov 21 18:50:09 ubuntu avahi-autoipd(eth0)[5999]: Successfully called chroot().
Nov 21 18:50:09 ubuntu avahi-autoipd(eth0)[5999]: Successfully dropped root privileges.
Nov 21 18:50:09 ubuntu avahi-autoipd(eth0)[5999]: fopen() failed: Permission denied
Nov 21 18:50:09 ubuntu avahi-autoipd(eth0)[5999]: Starting with address 169.254.8.77
Nov 21 18:50:10 ubuntu avahi-daemon[5197]: Withdrawing address record for fe80::203:25ff:fe3f:b1e6 on eth0.
Nov 21 18:50:10 ubuntu NetworkManager: nm_device_is_802_3_ethernet: assertion `dev != NULL' failed
Nov 21 18:50:10 ubuntu NetworkManager: nm_device_is_802_11_wireless: assertion `dev != NULL' failed
Nov 21 18:50:14 ubuntu avahi-autoipd(eth0)[5999]: Callout BIND, address 169.254.8.77 on interface eth0
Nov 21 18:50:14 ubuntu avahi-daemon[5197]: Joining mDNS multicast group on interface eth0.IPv4 with address 169.254.8.77.
Nov 21 18:50:14 ubuntu avahi-daemon[5197]: New relevant interface eth0.IPv4 for mDNS.
Nov 21 18:50:14 ubuntu avahi-daemon[5197]: Registering new address record for 169.254.8.77 on eth0.IPv4.
Nov 21 18:50:18 ubuntu avahi-autoipd(eth0)[5999]: Successfully claimed IP address 169.254.8.77
Nov 21 18:50:18 ubuntu avahi-autoipd(eth0)[5999]: fopen() failed: Permission denied
Nov 21 19:09:25 ubuntu gdm[5248]: Restarting computer...
Nov 21 19:09:30 ubuntu init: tty4 main process (4609) killed by TERM signal
Nov 21 19:09:30 ubuntu init: tty5 main process (4610) killed by TERM signal
Nov 21 19:09:30 ubuntu init: tty2 main process (4612) killed by TERM signal
Nov 21 19:09:30 ubuntu init: tty3 main process (4614) killed by TERM signal
Nov 21 19:09:30 ubuntu init: tty1 main process (4616) killed by TERM signal
Nov 21 19:09:30 ubuntu init: tty6 main process (4617) killed by TERM signal
Nov 21 19:11:13 ubuntu NetworkManager: <information>^Istarting... 
Nov 21 19:11:13 ubuntu NetworkManager: <information>^Ieth0: Device is fully-supported using driver 'sky2'. 
Nov 21 19:11:13 ubuntu avahi-daemon[5194]: Found user 'avahi' (UID 105) and group 'avahi' (GID 111).
Nov 21 19:11:13 ubuntu NetworkManager: <information>^Inm_device_init(): waiting for device's worker thread to start 
Nov 21 19:11:13 ubuntu NetworkManager: <information>^Inm_device_init(): device's worker thread started, continuing. 
Nov 21 19:11:13 ubuntu avahi-daemon[5194]: Successfully dropped root privileges.
Nov 21 19:11:13 ubuntu NetworkManager: <information>^INow managing wired Ethernet (802.3) device 'eth0'. 
Nov 21 19:11:13 ubuntu avahi-daemon[5194]: avahi-daemon 0.6.17 starting up.
Nov 21 19:11:13 ubuntu NetworkManager: <information>^IDeactivating device eth0. 
Nov 21 19:11:13 ubuntu avahi-daemon[5194]: Successfully called chroot().
Nov 21 19:11:13 ubuntu avahi-daemon[5194]: Successfully dropped remaining capabilities.
Nov 21 19:11:13 ubuntu avahi-daemon[5194]: No service found in /etc/avahi/services.
Nov 21 19:11:13 ubuntu avahi-daemon[5194]: Network interface enumeration completed.
Nov 21 19:11:13 ubuntu avahi-daemon[5194]: Registering HINFO record with values 'I686'/'LINUX'.
Nov 21 19:11:13 ubuntu avahi-daemon[5194]: Server startup complete. Host name is ubuntu.local. Local service cookie is 1065433424.
Nov 21 19:11:18 ubuntu hcid[5431]: Bluetooth HCI daemon
Nov 21 19:11:18 ubuntu hcid[5431]: Starting SDP server
Nov 21 19:11:18 ubuntu NetworkManager: <debug info>^I[1195690278.478484] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_bluetooth'). 
Nov 21 19:12:01 ubuntu NetworkManager: <information>^IUpdating allowed wireless network lists. 
Nov 21 19:12:02 ubuntu NetworkManager: <WARNING>^I nm_dbus_get_networks_cb (): error received: org.freedesktop.NetworkManagerInfo.NoNetworks - There are no wireless networks stored.. 
Nov 21 19:13:03 ubuntu NetworkManager: <debug info>^I[1195690383.028900] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_718_65_AA0070006371905A'). 
Nov 21 19:13:03 ubuntu NetworkManager: <debug info>^I[1195690383.150735] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_718_65_AA0070006371905A_if0'). 
Nov 21 19:13:03 ubuntu NetworkManager: <debug info>^I[1195690383.179765] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_718_65_AA0070006371905A_if0_scsi_host'). 
Nov 21 19:13:03 ubuntu NetworkManager: <debug info>^I[1195690383.183515] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_718_65_AA0070006371905A_usbraw'). 
Nov 21 19:13:11 ubuntu NetworkManager: <debug info>^I[1195690391.259408] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_718_65_AA0070006371905A_if0_scsi_host_scsi_device_lun0'). 
Nov 21 19:13:11 ubuntu NetworkManager: <debug info>^I[1195690391.282740] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_718_65_AA0070006371905A_if0_scsi_host_scsi_device_lun0_scsi_generic'). 
Nov 21 19:13:11 ubuntu NetworkManager: <debug info>^I[1195690391.386805] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_serial_Imation_USB_Flash_Drive_AA0070006371905A_0_0'). 
Nov 21 19:13:11 ubuntu NetworkManager: <debug info>^I[1195690391.447222] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_352D_1380'). 
Nov 21 19:13:11 ubuntu hald: mounted /dev/sda1 on behalf of uid 1000
Nov 21 19:25:14 ubuntu hald: unmounted /dev/sda1 from '/media/disk' on behalf of uid 1000
Nov 21 19:25:15 ubuntu NetworkManager: <debug info>^I[1195691115.513456] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_352D_1380'). 
Nov 21 19:25:16 ubuntu NetworkManager: <debug info>^I[1195691116.330076] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_718_65_AA0070006371905A_if0_scsi_host_scsi_device_lun0_scsi_generic'). 
Nov 21 19:25:16 ubuntu NetworkManager: <debug info>^I[1195691116.343532] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/storage_serial_Imation_USB_Flash_Drive_AA0070006371905A_0_0'). 
Nov 21 19:25:16 ubuntu NetworkManager: <debug info>^I[1195691116.352607] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_718_65_AA0070006371905A_if0_scsi_host_scsi_device_lun0'). 
Nov 21 19:25:16 ubuntu NetworkManager: <debug info>^I[1195691116.355945] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_718_65_AA0070006371905A_if0_scsi_host'). 
Nov 21 19:25:16 ubuntu NetworkManager: <debug info>^I[1195691116.358902] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_718_65_AA0070006371905A_if0'). 
Nov 21 19:25:16 ubuntu NetworkManager: <debug info>^I[1195691116.361230] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_718_65_AA0070006371905A'). 
Nov 21 19:25:16 ubuntu NetworkManager: <debug info>^I[1195691116.371126] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_718_65_AA0070006371905A_usbraw'). 
Nov 21 19:25:32 ubuntu avahi-daemon[5194]: Registering new address record for fe80::203:25ff:fe3f:b1e6 on eth0.*.
Nov 21 19:25:33 ubuntu NetworkManager: <information>^IWill activate wired connection 'eth0' because it now has a link. 
Nov 21 19:25:33 ubuntu NetworkManager: <information>^ISWITCH: no current connection, found better connection 'eth0'. 
Nov 21 19:25:33 ubuntu NetworkManager: <information>^IWill activate connection 'eth0'. 
Nov 21 19:25:33 ubuntu NetworkManager: <information>^IDevice eth0 activation scheduled... 
Nov 21 19:25:33 ubuntu NetworkManager: <information>^IActivation (eth0) started... 
Nov 21 19:25:33 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 1 of 5 (Device Prepare) scheduled... 
Nov 21 19:25:33 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 1 of 5 (Device Prepare) started... 
Nov 21 19:25:33 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 2 of 5 (Device Configure) scheduled... 
Nov 21 19:25:33 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 1 of 5 (Device Prepare) complete. 
Nov 21 19:25:33 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 2 of 5 (Device Configure) starting... 
Nov 21 19:25:33 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 2 of 5 (Device Configure) successful. 
Nov 21 19:25:33 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 3 of 5 (IP Configure Start) scheduled. 
Nov 21 19:25:33 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 2 of 5 (Device Configure) complete. 
Nov 21 19:25:33 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 3 of 5 (IP Configure Start) started... 
Nov 21 19:25:34 ubuntu NetworkManager: <information>^IActivation (eth0) Beginning DHCP transaction. 
Nov 21 19:25:34 ubuntu NetworkManager: <information>^IDHCP daemon state is now 12 (successfully started) for interface eth0 
Nov 21 19:25:34 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 3 of 5 (IP Configure Start) complete. 
Nov 21 19:25:35 ubuntu NetworkManager: <information>^IDHCP daemon state is now 1 (starting) for interface eth0 
Nov 21 19:25:38 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
Nov 21 19:25:38 ubuntu dhclient: DHCPOFFER from 192.168.15.1
Nov 21 19:25:38 ubuntu dhclient: DHCPREQUEST on eth0 to 255.255.255.255 port 67
Nov 21 19:25:38 ubuntu dhclient: DHCPACK from 192.168.15.1
Nov 21 19:25:38 ubuntu avahi-daemon[5194]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.15.102.
Nov 21 19:25:38 ubuntu avahi-daemon[5194]: New relevant interface eth0.IPv4 for mDNS.
Nov 21 19:25:38 ubuntu avahi-daemon[5194]: Registering new address record for 192.168.15.102 on eth0.IPv4.
Nov 21 19:25:38 ubuntu NetworkManager: <information>^IDHCP daemon state is now 2 (bound) for interface eth0 
Nov 21 19:25:38 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 4 of 5 (IP Configure Get) scheduled... 
Nov 21 19:25:38 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 4 of 5 (IP Configure Get) started... 
Nov 21 19:25:38 ubuntu dhclient: bound to 192.168.15.102 -- renewal in 34407 seconds.
Nov 21 19:25:38 ubuntu NetworkManager: <information>^IRetrieved the following IP4 configuration from the DHCP daemon: 
Nov 21 19:25:38 ubuntu NetworkManager: <information>^I  address 192.168.15.102 
Nov 21 19:25:38 ubuntu NetworkManager: <information>^I  netmask 255.255.255.0 
Nov 21 19:25:38 ubuntu NetworkManager: <information>^I  broadcast 192.168.15.255 
Nov 21 19:25:38 ubuntu NetworkManager: <information>^I  gateway 192.168.15.1 
Nov 21 19:25:38 ubuntu NetworkManager: <information>^I  nameserver 192.168.15.1 
Nov 21 19:25:38 ubuntu NetworkManager: <information>^I  hostname 'ubuntu' 
Nov 21 19:25:38 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 5 of 5 (IP Configure Commit) scheduled... 
Nov 21 19:25:38 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 4 of 5 (IP Configure Get) complete. 
Nov 21 19:25:38 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 5 of 5 (IP Configure Commit) started... 
Nov 21 19:25:38 ubuntu avahi-daemon[5194]: Withdrawing address record for 192.168.15.102 on eth0.
Nov 21 19:25:38 ubuntu avahi-daemon[5194]: Leaving mDNS multicast group on interface eth0.IPv4 with address 192.168.15.102.
Nov 21 19:25:38 ubuntu avahi-daemon[5194]: Interface eth0.IPv4 no longer relevant for mDNS.
Nov 21 19:25:38 ubuntu avahi-daemon[5194]: Withdrawing address record for fe80::203:25ff:fe3f:b1e6 on eth0.
Nov 21 19:25:38 ubuntu avahi-daemon[5194]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.15.102.
Nov 21 19:25:38 ubuntu avahi-daemon[5194]: New relevant interface eth0.IPv4 for mDNS.
Nov 21 19:25:38 ubuntu avahi-daemon[5194]: Registering new address record for 192.168.15.102 on eth0.IPv4.
Nov 21 19:25:39 ubuntu NetworkManager: <information>^IClearing nscd hosts cache. 
Nov 21 19:25:39 ubuntu NetworkManager: <WARNING>^I nm_spawn_process (): nm_spawn_process('/usr/sbin/nscd -i hosts'): could not spawn process. (Failed to execute child process "/usr/sbin/nscd" (No such file or directory))  
Nov 21 19:25:40 ubuntu NetworkManager: <information>^IActivation (eth0) successful, device activated. 
Nov 21 19:25:41 ubuntu NetworkManager: <information>^IActivation (eth0) Finish handler scheduled. 
Nov 21 19:25:41 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 5 of 5 (IP Configure Commit) complete. 
Nov 21 19:25:41 ubuntu avahi-daemon[5194]: Registering new address record for fe80::203:25ff:fe3f:b1e6 on eth0.*.
Nov 21 19:25:52 ubuntu ntpdate[6828]: adjust time server 91.189.94.4 offset -0.310343 sec
Nov 21 19:28:17 ubuntu avahi-daemon[5194]: Interface eth0.IPv4 no longer relevant for mDNS.
Nov 21 19:28:17 ubuntu avahi-daemon[5194]: Leaving mDNS multicast group on interface eth0.IPv4 with address 192.168.15.102.
Nov 21 19:28:17 ubuntu NetworkManager: <information>^ISWITCH: terminating current connection 'eth0' because it's no longer valid. 
Nov 21 19:28:17 ubuntu NetworkManager: <information>^IDeactivating device eth0. 
Nov 21 19:28:17 ubuntu dhclient: receive_packet failed on eth0: Network is down
Nov 21 19:28:17 ubuntu avahi-daemon[5194]: Withdrawing address record for fe80::203:25ff:fe3f:b1e6 on eth0.
Nov 21 19:28:17 ubuntu avahi-daemon[5194]: Withdrawing address record for 192.168.15.102 on eth0.
Nov 21 19:28:17 ubuntu dhclient: There is already a pid file /var/run/dhclient.eth0.pid with pid 6747
Nov 21 19:28:17 ubuntu dhclient: killed old client process, removed PID file
Nov 21 19:28:17 ubuntu dhclient: DHCPRELEASE on eth0 to 192.168.15.1 port 67
Nov 21 19:28:17 ubuntu dhclient: send_packet: Network is unreachable
Nov 21 19:28:17 ubuntu dhclient: send_packet: please consult README file regarding broadcast address.
Nov 21 19:28:17 ubuntu avahi-autoipd(eth0)[6910]: Found user 'avahi-autoipd' (UID 104) and group 'avahi-autoipd' (GID 110).
Nov 21 19:28:18 ubuntu avahi-autoipd(eth0)[6910]: Successfully called chroot().
Nov 21 19:28:18 ubuntu avahi-autoipd(eth0)[6910]: Successfully dropped root privileges.
Nov 21 19:28:18 ubuntu avahi-autoipd(eth0)[6910]: fopen() failed: Permission denied
Nov 21 19:28:18 ubuntu avahi-autoipd(eth0)[6910]: Starting with address 169.254.8.77
Nov 21 19:28:18 ubuntu NetworkManager: nm_device_is_802_3_ethernet: assertion `dev != NULL' failed
Nov 21 19:28:18 ubuntu NetworkManager: nm_device_is_802_11_wireless: assertion `dev != NULL' failed
Nov 21 19:28:18 ubuntu NetworkManager: <information>^IWill activate wired connection 'eth0' because it now has a link. 
Nov 21 19:28:18 ubuntu NetworkManager: <information>^ISWITCH: no current connection, found better connection 'eth0'. 
Nov 21 19:28:18 ubuntu NetworkManager: <information>^IWill activate connection 'eth0'. 
Nov 21 19:28:18 ubuntu NetworkManager: <information>^IDevice eth0 activation scheduled... 
Nov 21 19:28:18 ubuntu NetworkManager: <information>^IActivation (eth0) started... 
Nov 21 19:28:18 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 1 of 5 (Device Prepare) scheduled... 
Nov 21 19:28:18 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 1 of 5 (Device Prepare) started... 
Nov 21 19:28:18 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 2 of 5 (Device Configure) scheduled... 
Nov 21 19:28:18 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 1 of 5 (Device Prepare) complete. 
Nov 21 19:28:18 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 2 of 5 (Device Configure) starting... 
Nov 21 19:28:18 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 2 of 5 (Device Configure) successful. 
Nov 21 19:28:18 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 3 of 5 (IP Configure Start) scheduled. 
Nov 21 19:28:18 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 2 of 5 (Device Configure) complete. 
Nov 21 19:28:18 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 3 of 5 (IP Configure Start) started... 
Nov 21 19:28:20 ubuntu NetworkManager: <information>^IActivation (eth0) Beginning DHCP transaction. 
Nov 21 19:28:20 ubuntu NetworkManager: <information>^ICouldn't send DHCP 'up' message because: name 'com.redhat.dhcp.OperationInProgress', message 'interface eth0 is being released. Please try again later.'. 
Nov 21 19:28:20 ubuntu NetworkManager: <information>^IActivation (eth0) failure scheduled... 
Nov 21 19:28:20 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 3 of 5 (IP Configure Start) complete. 
Nov 21 19:28:20 ubuntu NetworkManager: <information>^IActivation (eth0) failed. 
Nov 21 19:28:20 ubuntu NetworkManager: <information>^IDeactivating device eth0. 
Nov 21 19:28:21 ubuntu NetworkManager: <information>^ISWITCH: no current connection, found better connection 'eth0'. 
Nov 21 19:28:21 ubuntu NetworkManager: <information>^IWill activate connection 'eth0'. 
Nov 21 19:28:21 ubuntu NetworkManager: <information>^IDevice eth0 activation scheduled... 
Nov 21 19:28:21 ubuntu NetworkManager: <information>^IActivation (eth0) started... 
Nov 21 19:28:21 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 1 of 5 (Device Prepare) scheduled... 
Nov 21 19:28:21 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 1 of 5 (Device Prepare) started... 
Nov 21 19:28:21 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 2 of 5 (Device Configure) scheduled... 
Nov 21 19:28:21 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 1 of 5 (Device Prepare) complete. 
Nov 21 19:28:21 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 2 of 5 (Device Configure) starting... 
Nov 21 19:28:21 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 2 of 5 (Device Configure) successful. 
Nov 21 19:28:21 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 3 of 5 (IP Configure Start) scheduled. 
Nov 21 19:28:21 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 2 of 5 (Device Configure) complete. 
Nov 21 19:28:21 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 3 of 5 (IP Configure Start) started... 
Nov 21 19:28:22 ubuntu avahi-autoipd(eth0)[6910]: Callout BIND, address 169.254.8.77 on interface eth0
Nov 21 19:28:22 ubuntu avahi-daemon[5194]: Joining mDNS multicast group on interface eth0.IPv4 with address 169.254.8.77.
Nov 21 19:28:22 ubuntu avahi-daemon[5194]: New relevant interface eth0.IPv4 for mDNS.
Nov 21 19:28:22 ubuntu avahi-daemon[5194]: Registering new address record for 169.254.8.77 on eth0.IPv4.
Nov 21 19:28:23 ubuntu NetworkManager: <information>^IActivation (eth0) Beginning DHCP transaction. 
Nov 21 19:28:23 ubuntu NetworkManager: <information>^ICouldn't send DHCP 'up' message because: name 'com.redhat.dhcp.OperationInProgress', message 'interface eth0 is being released. Please try again later.'. 
Nov 21 19:28:23 ubuntu NetworkManager: <information>^IActivation (eth0) failure scheduled... 
Nov 21 19:28:23 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 3 of 5 (IP Configure Start) complete. 
Nov 21 19:28:23 ubuntu NetworkManager: <information>^IActivation (eth0) failed. 
Nov 21 19:28:23 ubuntu NetworkManager: <information>^IDeactivating device eth0. 
Nov 21 19:28:24 ubuntu avahi-daemon[5194]: Withdrawing address record for 169.254.8.77 on eth0.
Nov 21 19:28:24 ubuntu avahi-daemon[5194]: Leaving mDNS multicast group on interface eth0.IPv4 with address 169.254.8.77.
Nov 21 19:28:24 ubuntu NetworkManager: <information>^ISWITCH: no current connection, found better connection 'eth0'. 
Nov 21 19:28:24 ubuntu NetworkManager: <information>^IWill activate connection 'eth0'. 
Nov 21 19:28:24 ubuntu NetworkManager: <information>^IDevice eth0 activation scheduled... 
Nov 21 19:28:24 ubuntu NetworkManager: <information>^IActivation (eth0) started... 
Nov 21 19:28:24 ubuntu avahi-daemon[5194]: Interface eth0.IPv4 no longer relevant for mDNS.
Nov 21 19:28:24 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 1 of 5 (Device Prepare) scheduled... 
Nov 21 19:28:24 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 1 of 5 (Device Prepare) started... 
Nov 21 19:28:24 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 2 of 5 (Device Configure) scheduled... 
Nov 21 19:28:24 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 1 of 5 (Device Prepare) complete. 
Nov 21 19:28:24 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 2 of 5 (Device Configure) starting... 
Nov 21 19:28:24 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 2 of 5 (Device Configure) successful. 
Nov 21 19:28:24 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 3 of 5 (IP Configure Start) scheduled. 
Nov 21 19:28:24 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 2 of 5 (Device Configure) complete. 
Nov 21 19:28:24 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 3 of 5 (IP Configure Start) started... 
Nov 21 19:28:26 ubuntu avahi-autoipd(eth0)[6910]: Successfully claimed IP address 169.254.8.77
Nov 21 19:28:26 ubuntu avahi-autoipd(eth0)[6910]: fopen() failed: Permission denied
Nov 21 19:28:26 ubuntu NetworkManager: <information>^IDHCP daemon state is now 11 (unknown) for interface eth0 
Nov 21 19:28:26 ubuntu NetworkManager: <information>^IDHCP daemon state is now 14 (normal exit) for interface eth0 
Nov 21 19:28:26 ubuntu NetworkManager: <information>^IActivation (eth0) Beginning DHCP transaction. 
Nov 21 19:28:26 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 3 of 5 (IP Configure Start) complete. 
Nov 21 19:28:26 ubuntu NetworkManager: <information>^IDHCP daemon state is now 12 (successfully started) for interface eth0 
Nov 21 19:28:26 ubuntu dhclient: There is already a pid file /var/run/dhclient.eth0.pid with pid 134993440
Nov 21 19:28:27 ubuntu avahi-autoipd(eth0)[6910]: Got SIGTERM, quitting.
Nov 21 19:28:27 ubuntu avahi-autoipd(eth0)[6910]: Callout STOP, address 169.254.8.77 on interface eth0
Nov 21 19:28:27 ubuntu avahi-autoipd(eth0)[6911]: client: RTNETLINK answers: No such device
Nov 21 19:28:27 ubuntu avahi-autoipd(eth0)[6911]: Script execution failed with return value 2
Nov 21 19:28:28 ubuntu NetworkManager: <information>^IDHCP daemon state is now 1 (starting) for interface eth0 
Nov 21 19:28:28 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
Nov 21 19:28:28 ubuntu dhclient: DHCPOFFER from 192.168.15.1
Nov 21 19:28:28 ubuntu dhclient: DHCPREQUEST on eth0 to 255.255.255.255 port 67
Nov 21 19:28:28 ubuntu dhclient: DHCPACK from 192.168.15.1
Nov 21 19:28:28 ubuntu avahi-daemon[5194]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.15.102.
Nov 21 19:28:28 ubuntu avahi-daemon[5194]: New relevant interface eth0.IPv4 for mDNS.
Nov 21 19:28:28 ubuntu avahi-daemon[5194]: Registering new address record for 192.168.15.102 on eth0.IPv4.
Nov 21 19:28:28 ubuntu NetworkManager: <information>^IDHCP daemon state is now 2 (bound) for interface eth0 
Nov 21 19:28:28 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 4 of 5 (IP Configure Get) scheduled... 
Nov 21 19:28:28 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 4 of 5 (IP Configure Get) started... 
Nov 21 19:28:28 ubuntu dhclient: bound to 192.168.15.102 -- renewal in 32948 seconds.
Nov 21 19:28:28 ubuntu NetworkManager: <information>^IRetrieved the following IP4 configuration from the DHCP daemon: 
Nov 21 19:28:28 ubuntu NetworkManager: <information>^I  address 192.168.15.102 
Nov 21 19:28:28 ubuntu NetworkManager: <information>^I  netmask 255.255.255.0 
Nov 21 19:28:28 ubuntu NetworkManager: <information>^I  broadcast 192.168.15.255 
Nov 21 19:28:28 ubuntu NetworkManager: <information>^I  gateway 192.168.15.1 
Nov 21 19:28:28 ubuntu NetworkManager: <information>^I  nameserver 192.168.15.1 
Nov 21 19:28:28 ubuntu NetworkManager: <information>^I  hostname 'ubuntu' 
Nov 21 19:28:28 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 5 of 5 (IP Configure Commit) scheduled... 
Nov 21 19:28:28 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 4 of 5 (IP Configure Get) complete. 
Nov 21 19:28:28 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 5 of 5 (IP Configure Commit) started... 
Nov 21 19:28:28 ubuntu avahi-daemon[5194]: Withdrawing address record for 192.168.15.102 on eth0.
Nov 21 19:28:28 ubuntu avahi-daemon[5194]: Leaving mDNS multicast group on interface eth0.IPv4 with address 192.168.15.102.
Nov 21 19:28:28 ubuntu avahi-daemon[5194]: Interface eth0.IPv4 no longer relevant for mDNS.
Nov 21 19:28:28 ubuntu avahi-daemon[5194]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.15.102.
Nov 21 19:28:28 ubuntu avahi-daemon[5194]: New relevant interface eth0.IPv4 for mDNS.
Nov 21 19:28:28 ubuntu avahi-daemon[5194]: Registering new address record for 192.168.15.102 on eth0.IPv4.
Nov 21 19:28:29 ubuntu NetworkManager: <information>^IClearing nscd hosts cache. 
Nov 21 19:28:29 ubuntu NetworkManager: <WARNING>^I nm_spawn_process (): nm_spawn_process('/usr/sbin/nscd -i hosts'): could not spawn process. (Failed to execute child process "/usr/sbin/nscd" (No such file or directory))  
Nov 21 19:28:29 ubuntu NetworkManager: <information>^IActivation (eth0) successful, device activated. 
Nov 21 19:28:29 ubuntu NetworkManager: <information>^IActivation (eth0) Finish handler scheduled. 
Nov 21 19:28:29 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 5 of 5 (IP Configure Commit) complete. 
Nov 21 19:28:31 ubuntu avahi-daemon[5194]: Registering new address record for fe80::203:25ff:fe3f:b1e6 on eth0.*.
Nov 21 19:28:40 ubuntu ntpdate[7051]: adjust time server 91.189.94.4 offset -0.214165 sec
Nov 21 19:31:42 ubuntu NetworkManager: <information>^ISWITCH: terminating current connection 'eth0' because it's no longer valid. 
Nov 21 19:31:42 ubuntu NetworkManager: <information>^IDeactivating device eth0. 
Nov 21 19:31:42 ubuntu dhclient: There is already a pid file /var/run/dhclient.eth0.pid with pid 6980
Nov 21 19:31:42 ubuntu dhclient: killed old client process, removed PID file
Nov 21 19:31:42 ubuntu dhclient: DHCPRELEASE on eth0 to 192.168.15.1 port 67
Nov 21 19:31:42 ubuntu avahi-daemon[5194]: Withdrawing address record for 192.168.15.102 on eth0.
Nov 21 19:31:42 ubuntu avahi-daemon[5194]: Leaving mDNS multicast group on interface eth0.IPv4 with address 192.168.15.102.
Nov 21 19:31:42 ubuntu avahi-daemon[5194]: Interface eth0.IPv4 no longer relevant for mDNS.
Nov 21 19:31:42 ubuntu avahi-autoipd(eth0)[7153]: Found user 'avahi-autoipd' (UID 104) and group 'avahi-autoipd' (GID 110).
Nov 21 19:31:42 ubuntu avahi-autoipd(eth0)[7153]: Successfully called chroot().
Nov 21 19:31:42 ubuntu avahi-autoipd(eth0)[7153]: Successfully dropped root privileges.
Nov 21 19:31:42 ubuntu avahi-autoipd(eth0)[7153]: fopen() failed: Permission denied
Nov 21 19:31:42 ubuntu avahi-autoipd(eth0)[7153]: Starting with address 169.254.8.77
Nov 21 19:31:43 ubuntu avahi-daemon[5194]: Withdrawing address record for fe80::203:25ff:fe3f:b1e6 on eth0.
Nov 21 19:31:43 ubuntu NetworkManager: nm_device_is_802_3_ethernet: assertion `dev != NULL' failed
Nov 21 19:31:43 ubuntu NetworkManager: nm_device_is_802_11_wireless: assertion `dev != NULL' failed
Nov 21 19:31:43 ubuntu NetworkManager: <information>^IWill activate wired connection 'eth0' because it now has a link. 
Nov 21 19:31:43 ubuntu NetworkManager: <information>^ISWITCH: no current connection, found better connection 'eth0'. 
Nov 21 19:31:43 ubuntu NetworkManager: <information>^IWill activate connection 'eth0'. 
Nov 21 19:31:43 ubuntu NetworkManager: <information>^IDevice eth0 activation scheduled... 
Nov 21 19:31:43 ubuntu NetworkManager: <information>^IActivation (eth0) started... 
Nov 21 19:31:43 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 1 of 5 (Device Prepare) scheduled... 
Nov 21 19:31:43 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 1 of 5 (Device Prepare) started... 
Nov 21 19:31:43 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 2 of 5 (Device Configure) scheduled... 
Nov 21 19:31:43 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 1 of 5 (Device Prepare) complete. 
Nov 21 19:31:43 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 2 of 5 (Device Configure) starting... 
Nov 21 19:31:43 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 2 of 5 (Device Configure) successful. 
Nov 21 19:31:43 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 3 of 5 (IP Configure Start) scheduled. 
Nov 21 19:31:43 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 2 of 5 (Device Configure) complete. 
Nov 21 19:31:43 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 3 of 5 (IP Configure Start) started... 
Nov 21 19:31:45 ubuntu NetworkManager: <information>^IActivation (eth0) Beginning DHCP transaction. 
Nov 21 19:31:45 ubuntu NetworkManager: <information>^ICouldn't send DHCP 'up' message because: name 'com.redhat.dhcp.OperationInProgress', message 'interface eth0 is being released. Please try again later.'. 
Nov 21 19:31:45 ubuntu NetworkManager: <information>^IActivation (eth0) failure scheduled... 
Nov 21 19:31:45 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 3 of 5 (IP Configure Start) complete. 
Nov 21 19:31:45 ubuntu NetworkManager: <information>^IActivation (eth0) failed. 
Nov 21 19:31:45 ubuntu NetworkManager: <information>^IDeactivating device eth0. 
Nov 21 19:31:46 ubuntu NetworkManager: <information>^ISWITCH: no current connection, found better connection 'eth0'. 
Nov 21 19:31:46 ubuntu NetworkManager: <information>^IWill activate connection 'eth0'. 
Nov 21 19:31:46 ubuntu NetworkManager: <information>^IDevice eth0 activation scheduled... 
Nov 21 19:31:46 ubuntu NetworkManager: <information>^IActivation (eth0) started... 
Nov 21 19:31:46 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 1 of 5 (Device Prepare) scheduled... 
Nov 21 19:31:46 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 1 of 5 (Device Prepare) started... 
Nov 21 19:31:46 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 2 of 5 (Device Configure) scheduled... 
Nov 21 19:31:46 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 1 of 5 (Device Prepare) complete. 
Nov 21 19:31:46 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 2 of 5 (Device Configure) starting... 
Nov 21 19:31:46 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 2 of 5 (Device Configure) successful. 
Nov 21 19:31:46 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 3 of 5 (IP Configure Start) scheduled. 
Nov 21 19:31:46 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 2 of 5 (Device Configure) complete. 
Nov 21 19:31:46 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 3 of 5 (IP Configure Start) started... 
Nov 21 19:31:48 ubuntu avahi-autoipd(eth0)[7153]: Callout BIND, address 169.254.8.77 on interface eth0
Nov 21 19:31:48 ubuntu avahi-daemon[5194]: Joining mDNS multicast group on interface eth0.IPv4 with address 169.254.8.77.
Nov 21 19:31:48 ubuntu avahi-daemon[5194]: New relevant interface eth0.IPv4 for mDNS.
Nov 21 19:31:48 ubuntu avahi-daemon[5194]: Registering new address record for 169.254.8.77 on eth0.IPv4.
Nov 21 19:31:48 ubuntu NetworkManager: <information>^IActivation (eth0) Beginning DHCP transaction. 
Nov 21 19:31:48 ubuntu NetworkManager: <information>^ICouldn't send DHCP 'up' message because: name 'com.redhat.dhcp.OperationInProgress', message 'interface eth0 is being released. Please try again later.'. 
Nov 21 19:31:48 ubuntu NetworkManager: <information>^IActivation (eth0) failure scheduled... 
Nov 21 19:31:48 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 3 of 5 (IP Configure Start) complete. 
Nov 21 19:31:48 ubuntu NetworkManager: <information>^IActivation (eth0) failed. 
Nov 21 19:31:48 ubuntu NetworkManager: <information>^IDeactivating device eth0. 
Nov 21 19:31:49 ubuntu avahi-daemon[5194]: Withdrawing address record for 169.254.8.77 on eth0.
Nov 21 19:31:49 ubuntu avahi-daemon[5194]: Leaving mDNS multicast group on interface eth0.IPv4 with address 169.254.8.77.
Nov 21 19:31:49 ubuntu avahi-daemon[5194]: Interface eth0.IPv4 no longer relevant for mDNS.
Nov 21 19:31:49 ubuntu NetworkManager: <information>^ISWITCH: no current connection, found better connection 'eth0'. 
Nov 21 19:31:49 ubuntu NetworkManager: <information>^IWill activate connection 'eth0'. 
Nov 21 19:31:49 ubuntu NetworkManager: <information>^IDevice eth0 activation scheduled... 
Nov 21 19:31:49 ubuntu NetworkManager: <information>^IActivation (eth0) started... 
Nov 21 19:31:49 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 1 of 5 (Device Prepare) scheduled... 
Nov 21 19:31:49 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 1 of 5 (Device Prepare) started... 
Nov 21 19:31:49 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 2 of 5 (Device Configure) scheduled... 
Nov 21 19:31:49 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 1 of 5 (Device Prepare) complete. 
Nov 21 19:31:49 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 2 of 5 (Device Configure) starting... 
Nov 21 19:31:49 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 2 of 5 (Device Configure) successful. 
Nov 21 19:31:49 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 3 of 5 (IP Configure Start) scheduled. 
Nov 21 19:31:49 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 2 of 5 (Device Configure) complete. 
Nov 21 19:31:49 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 3 of 5 (IP Configure Start) started... 
Nov 21 19:31:51 ubuntu NetworkManager: <information>^IActivation (eth0) Beginning DHCP transaction. 
Nov 21 19:31:51 ubuntu NetworkManager: <information>^ICouldn't send DHCP 'up' message because: name 'com.redhat.dhcp.OperationInProgress', message 'interface eth0 is being released. Please try again later.'. 
Nov 21 19:31:51 ubuntu NetworkManager: <information>^IActivation (eth0) failure scheduled... 
Nov 21 19:31:51 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 3 of 5 (IP Configure Start) complete. 
Nov 21 19:31:51 ubuntu NetworkManager: <information>^IActivation (eth0) failed. 
Nov 21 19:31:51 ubuntu NetworkManager: <information>^IDeactivating device eth0. 
Nov 21 19:31:52 ubuntu avahi-autoipd(eth0)[7153]: Successfully claimed IP address 169.254.8.77
Nov 21 19:31:52 ubuntu avahi-autoipd(eth0)[7153]: fopen() failed: Permission denied
Nov 21 19:31:52 ubuntu NetworkManager: <information>^ISWITCH: no current connection, found better connection 'eth0'. 
Nov 21 19:31:52 ubuntu NetworkManager: <information>^IWill activate connection 'eth0'. 
Nov 21 19:31:52 ubuntu NetworkManager: <information>^IDevice eth0 activation scheduled... 
Nov 21 19:31:52 ubuntu NetworkManager: <information>^IActivation (eth0) started... 
Nov 21 19:31:52 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 1 of 5 (Device Prepare) scheduled... 
Nov 21 19:31:52 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 1 of 5 (Device Prepare) started... 
Nov 21 19:31:52 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 2 of 5 (Device Configure) scheduled... 
Nov 21 19:31:52 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 1 of 5 (Device Prepare) complete. 
Nov 21 19:31:52 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 2 of 5 (Device Configure) starting... 
Nov 21 19:31:52 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 2 of 5 (Device Configure) successful. 
Nov 21 19:31:52 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 3 of 5 (IP Configure Start) scheduled. 
Nov 21 19:31:52 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 2 of 5 (Device Configure) complete. 
Nov 21 19:31:53 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 3 of 5 (IP Configure Start) started... 
Nov 21 19:31:53 ubuntu NetworkManager: <information>^IActivation (eth0) Beginning DHCP transaction. 
Nov 21 19:31:53 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 3 of 5 (IP Configure Start) complete. 
Nov 21 19:31:53 ubuntu NetworkManager: <information>^IDHCP daemon state is now 12 (successfully started) for interface eth0 
Nov 21 19:31:53 ubuntu dhclient: There is already a pid file /var/run/dhclient.eth0.pid with pid 134993440
Nov 21 19:31:54 ubuntu avahi-autoipd(eth0)[7153]: Got SIGTERM, quitting.
Nov 21 19:31:54 ubuntu avahi-autoipd(eth0)[7153]: Callout STOP, address 169.254.8.77 on interface eth0
Nov 21 19:31:54 ubuntu avahi-autoipd(eth0)[7154]: client: RTNETLINK answers: No such device
Nov 21 19:31:54 ubuntu avahi-autoipd(eth0)[7154]: Script execution failed with return value 2
Nov 21 19:31:55 ubuntu NetworkManager: <information>^IDHCP daemon state is now 1 (starting) for interface eth0 
Nov 21 19:31:59 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
Nov 21 19:31:59 ubuntu dhclient: DHCPOFFER from 192.168.15.1
Nov 21 19:31:59 ubuntu dhclient: DHCPREQUEST on eth0 to 255.255.255.255 port 67
Nov 21 19:31:59 ubuntu dhclient: DHCPACK from 192.168.15.1
Nov 21 19:31:59 ubuntu avahi-daemon[5194]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.15.102.
Nov 21 19:31:59 ubuntu avahi-daemon[5194]: New relevant interface eth0.IPv4 for mDNS.
Nov 21 19:31:59 ubuntu avahi-daemon[5194]: Registering new address record for 192.168.15.102 on eth0.IPv4.
Nov 21 19:31:59 ubuntu NetworkManager: <information>^IDHCP daemon state is now 2 (bound) for interface eth0 
Nov 21 19:31:59 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 4 of 5 (IP Configure Get) scheduled... 
Nov 21 19:31:59 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 4 of 5 (IP Configure Get) started... 
Nov 21 19:31:59 ubuntu dhclient: bound to 192.168.15.102 -- renewal in 33333 seconds.
Nov 21 19:31:59 ubuntu NetworkManager: <information>^IRetrieved the following IP4 configuration from the DHCP daemon: 
Nov 21 19:31:59 ubuntu NetworkManager: <information>^I  address 192.168.15.102 
Nov 21 19:31:59 ubuntu NetworkManager: <information>^I  netmask 255.255.255.0 
Nov 21 19:31:59 ubuntu NetworkManager: <information>^I  broadcast 192.168.15.255 
Nov 21 19:31:59 ubuntu NetworkManager: <information>^I  gateway 192.168.15.1 
Nov 21 19:31:59 ubuntu NetworkManager: <information>^I  nameserver 192.168.15.1 
Nov 21 19:31:59 ubuntu NetworkManager: <information>^I  hostname 'ubuntu' 
Nov 21 19:31:59 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 5 of 5 (IP Configure Commit) scheduled... 
Nov 21 19:31:59 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 4 of 5 (IP Configure Get) complete. 
Nov 21 19:31:59 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 5 of 5 (IP Configure Commit) started... 
Nov 21 19:31:59 ubuntu avahi-daemon[5194]: Withdrawing address record for 192.168.15.102 on eth0.
Nov 21 19:31:59 ubuntu avahi-daemon[5194]: Leaving mDNS multicast group on interface eth0.IPv4 with address 192.168.15.102.
Nov 21 19:31:59 ubuntu avahi-daemon[5194]: Interface eth0.IPv4 no longer relevant for mDNS.
Nov 21 19:31:59 ubuntu avahi-daemon[5194]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.15.102.
Nov 21 19:31:59 ubuntu avahi-daemon[5194]: New relevant interface eth0.IPv4 for mDNS.
Nov 21 19:31:59 ubuntu avahi-daemon[5194]: Registering new address record for 192.168.15.102 on eth0.IPv4.
Nov 21 19:32:00 ubuntu NetworkManager: <information>^IClearing nscd hosts cache. 
Nov 21 19:32:00 ubuntu NetworkManager: <WARNING>^I nm_spawn_process (): nm_spawn_process('/usr/sbin/nscd -i hosts'): could not spawn process. (Failed to execute child process "/usr/sbin/nscd" (No such file or directory))  
Nov 21 19:32:00 ubuntu NetworkManager: <information>^IActivation (eth0) Finish handler scheduled. 
Nov 21 19:32:00 ubuntu NetworkManager: <information>^IActivation (eth0) successful, device activated. 
Nov 21 19:32:00 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 5 of 5 (IP Configure Commit) complete. 
Nov 21 19:32:01 ubuntu avahi-daemon[5194]: Registering new address record for fe80::203:25ff:fe3f:b1e6 on eth0.*.
Nov 21 19:32:11 ubuntu ntpdate[7302]: adjust time server 91.189.94.4 offset -0.093845 sec
Nov 21 19:32:19 ubuntu avahi-daemon[5194]: Interface eth0.IPv4 no longer relevant for mDNS.
Nov 21 19:32:19 ubuntu avahi-daemon[5194]: Leaving mDNS multicast group on interface eth0.IPv4 with address 192.168.15.102.
Nov 21 19:32:19 ubuntu NetworkManager: <information>^ISWITCH: terminating current connection 'eth0' because it's no longer valid. 
Nov 21 19:32:19 ubuntu NetworkManager: <information>^IDeactivating device eth0. 
Nov 21 19:32:19 ubuntu dhclient: There is already a pid file /var/run/dhclient.eth0.pid with pid 7239
Nov 21 19:32:19 ubuntu dhclient: killed old client process, removed PID file
Nov 21 19:32:19 ubuntu avahi-daemon[5194]: Withdrawing address record for fe80::203:25ff:fe3f:b1e6 on eth0.
Nov 21 19:32:19 ubuntu avahi-daemon[5194]: Withdrawing address record for 192.168.15.102 on eth0.
Nov 21 19:32:19 ubuntu dhclient: DHCPRELEASE on eth0 to 192.168.15.1 port 67
Nov 21 19:32:19 ubuntu dhclient: send_packet: Network is unreachable
Nov 21 19:32:19 ubuntu dhclient: send_packet: please consult README file regarding broadcast address.
Nov 21 19:32:19 ubuntu avahi-autoipd(eth0)[7346]: Found user 'avahi-autoipd' (UID 104) and group 'avahi-autoipd' (GID 110).
Nov 21 19:32:19 ubuntu avahi-autoipd(eth0)[7346]: Successfully called chroot().
Nov 21 19:32:19 ubuntu avahi-autoipd(eth0)[7346]: Successfully dropped root privileges.
Nov 21 19:32:19 ubuntu avahi-autoipd(eth0)[7346]: fopen() failed: Permission denied
Nov 21 19:32:19 ubuntu avahi-autoipd(eth0)[7346]: Starting with address 169.254.8.77
Nov 21 19:32:20 ubuntu NetworkManager: nm_device_is_802_3_ethernet: assertion `dev != NULL' failed
Nov 21 19:32:20 ubuntu NetworkManager: nm_device_is_802_11_wireless: assertion `dev != NULL' failed
Nov 21 19:32:20 ubuntu NetworkManager: <information>^IWill activate wired connection 'eth0' because it now has a link. 
Nov 21 19:32:20 ubuntu NetworkManager: <information>^ISWITCH: no current connection, found better connection 'eth0'. 
Nov 21 19:32:20 ubuntu NetworkManager: <information>^IWill activate connection 'eth0'. 
Nov 21 19:32:20 ubuntu NetworkManager: <information>^IDevice eth0 activation scheduled... 
Nov 21 19:32:20 ubuntu NetworkManager: <information>^IActivation (eth0) started... 
Nov 21 19:32:20 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 1 of 5 (Device Prepare) scheduled... 
Nov 21 19:32:20 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 1 of 5 (Device Prepare) started... 
Nov 21 19:32:20 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 2 of 5 (Device Configure) scheduled... 
Nov 21 19:32:20 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 1 of 5 (Device Prepare) complete. 
Nov 21 19:32:20 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 2 of 5 (Device Configure) starting... 
Nov 21 19:32:20 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 2 of 5 (Device Configure) successful. 
Nov 21 19:32:20 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 3 of 5 (IP Configure Start) scheduled. 
Nov 21 19:32:20 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 2 of 5 (Device Configure) complete. 
Nov 21 19:32:20 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 3 of 5 (IP Configure Start) started... 
Nov 21 19:32:22 ubuntu NetworkManager: <information>^IActivation (eth0) Beginning DHCP transaction. 
Nov 21 19:32:22 ubuntu NetworkManager: <information>^ICouldn't send DHCP 'up' message because: name 'com.redhat.dhcp.OperationInProgress', message 'interface eth0 is being released. Please try again later.'. 
Nov 21 19:32:22 ubuntu NetworkManager: <information>^IActivation (eth0) failure scheduled... 
Nov 21 19:32:22 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 3 of 5 (IP Configure Start) complete. 
Nov 21 19:32:22 ubuntu NetworkManager: <information>^IActivation (eth0) failed. 
Nov 21 19:32:22 ubuntu NetworkManager: <information>^IDeactivating device eth0. 
Nov 21 19:32:23 ubuntu NetworkManager: <information>^ISWITCH: no current connection, found better connection 'eth0'. 
Nov 21 19:32:23 ubuntu NetworkManager: <information>^IWill activate connection 'eth0'. 
Nov 21 19:32:23 ubuntu NetworkManager: <information>^IDevice eth0 activation scheduled... 
Nov 21 19:32:23 ubuntu NetworkManager: <information>^IActivation (eth0) started... 
Nov 21 19:32:23 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 1 of 5 (Device Prepare) scheduled... 
Nov 21 19:32:23 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 1 of 5 (Device Prepare) started... 
Nov 21 19:32:23 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 2 of 5 (Device Configure) scheduled... 
Nov 21 19:32:23 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 1 of 5 (Device Prepare) complete. 
Nov 21 19:32:23 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 2 of 5 (Device Configure) starting... 
Nov 21 19:32:23 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 2 of 5 (Device Configure) successful. 
Nov 21 19:32:23 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 3 of 5 (IP Configure Start) scheduled. 
Nov 21 19:32:23 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 2 of 5 (Device Configure) complete. 
Nov 21 19:32:23 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 3 of 5 (IP Configure Start) started... 
Nov 21 19:32:25 ubuntu avahi-autoipd(eth0)[7346]: Callout BIND, address 169.254.8.77 on interface eth0
Nov 21 19:32:25 ubuntu avahi-daemon[5194]: Joining mDNS multicast group on interface eth0.IPv4 with address 169.254.8.77.
Nov 21 19:32:25 ubuntu avahi-daemon[5194]: New relevant interface eth0.IPv4 for mDNS.
Nov 21 19:32:25 ubuntu avahi-daemon[5194]: Registering new address record for 169.254.8.77 on eth0.IPv4.
Nov 21 19:32:25 ubuntu NetworkManager: <information>^IActivation (eth0) Beginning DHCP transaction. 
Nov 21 19:32:25 ubuntu NetworkManager: <information>^ICouldn't send DHCP 'up' message because: name 'com.redhat.dhcp.OperationInProgress', message 'interface eth0 is being released. Please try again later.'. 
Nov 21 19:32:25 ubuntu NetworkManager: <information>^IActivation (eth0) failure scheduled... 
Nov 21 19:32:25 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 3 of 5 (IP Configure Start) complete. 
Nov 21 19:32:25 ubuntu NetworkManager: <information>^IActivation (eth0) failed. 
Nov 21 19:32:25 ubuntu NetworkManager: <information>^IDeactivating device eth0. 
Nov 21 19:32:26 ubuntu avahi-daemon[5194]: Withdrawing address record for 169.254.8.77 on eth0.
Nov 21 19:32:26 ubuntu avahi-daemon[5194]: Leaving mDNS multicast group on interface eth0.IPv4 with address 169.254.8.77.
Nov 21 19:32:26 ubuntu avahi-daemon[5194]: Interface eth0.IPv4 no longer relevant for mDNS.
Nov 21 19:32:26 ubuntu NetworkManager: <information>^ISWITCH: no current connection, found better connection 'eth0'. 
Nov 21 19:32:26 ubuntu NetworkManager: <information>^IWill activate connection 'eth0'. 
Nov 21 19:32:26 ubuntu NetworkManager: <information>^IDevice eth0 activation scheduled... 
Nov 21 19:32:26 ubuntu NetworkManager: <information>^IActivation (eth0) started... 
Nov 21 19:32:26 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 1 of 5 (Device Prepare) scheduled... 
Nov 21 19:32:26 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 1 of 5 (Device Prepare) started... 
Nov 21 19:32:26 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 2 of 5 (Device Configure) scheduled... 
Nov 21 19:32:26 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 1 of 5 (Device Prepare) complete. 
Nov 21 19:32:26 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 2 of 5 (Device Configure) starting... 
Nov 21 19:32:26 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 2 of 5 (Device Configure) successful. 
Nov 21 19:32:26 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 3 of 5 (IP Configure Start) scheduled. 
Nov 21 19:32:26 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 2 of 5 (Device Configure) complete. 
Nov 21 19:32:26 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 3 of 5 (IP Configure Start) started... 
Nov 21 19:32:28 ubuntu NetworkManager: <information>^IActivation (eth0) Beginning DHCP transaction. 
Nov 21 19:32:28 ubuntu NetworkManager: <information>^ICouldn't send DHCP 'up' message because: name 'com.redhat.dhcp.OperationInProgress', message 'interface eth0 is being released. Please try again later.'. 
Nov 21 19:32:28 ubuntu NetworkManager: <information>^IActivation (eth0) failure scheduled... 
Nov 21 19:32:28 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 3 of 5 (IP Configure Start) complete. 
Nov 21 19:32:28 ubuntu NetworkManager: <information>^IActivation (eth0) failed. 
Nov 21 19:32:28 ubuntu NetworkManager: <information>^IDeactivating device eth0. 
Nov 21 19:32:29 ubuntu avahi-autoipd(eth0)[7346]: Successfully claimed IP address 169.254.8.77
Nov 21 19:32:29 ubuntu avahi-autoipd(eth0)[7346]: fopen() failed: Permission denied
Nov 21 19:32:29 ubuntu NetworkManager: <information>^ISWITCH: no current connection, found better connection 'eth0'. 
Nov 21 19:32:29 ubuntu NetworkManager: <information>^IWill activate connection 'eth0'. 
Nov 21 19:32:29 ubuntu NetworkManager: <information>^IDevice eth0 activation scheduled... 
Nov 21 19:32:29 ubuntu NetworkManager: <information>^IActivation (eth0) started... 
Nov 21 19:32:29 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 1 of 5 (Device Prepare) scheduled... 
Nov 21 19:32:29 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 1 of 5 (Device Prepare) started... 
Nov 21 19:32:29 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 2 of 5 (Device Configure) scheduled... 
Nov 21 19:32:29 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 1 of 5 (Device Prepare) complete. 
Nov 21 19:32:29 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 2 of 5 (Device Configure) starting... 
Nov 21 19:32:29 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 2 of 5 (Device Configure) successful. 
Nov 21 19:32:29 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 3 of 5 (IP Configure Start) scheduled. 
Nov 21 19:32:29 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 2 of 5 (Device Configure) complete. 
Nov 21 19:32:29 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 3 of 5 (IP Configure Start) started... 
Nov 21 19:32:30 ubuntu NetworkManager: <information>^IActivation (eth0) Beginning DHCP transaction. 
Nov 21 19:32:30 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 3 of 5 (IP Configure Start) complete. 
Nov 21 19:32:30 ubuntu NetworkManager: <information>^IDHCP daemon state is now 12 (successfully started) for interface eth0 
Nov 21 19:32:30 ubuntu dhclient: There is already a pid file /var/run/dhclient.eth0.pid with pid 134993440
Nov 21 19:32:30 ubuntu avahi-autoipd(eth0)[7346]: Got SIGTERM, quitting.
Nov 21 19:32:30 ubuntu avahi-autoipd(eth0)[7346]: Callout STOP, address 169.254.8.77 on interface eth0
Nov 21 19:32:30 ubuntu avahi-autoipd(eth0)[7347]: client: RTNETLINK answers: No such device
Nov 21 19:32:30 ubuntu avahi-autoipd(eth0)[7347]: Script execution failed with return value 2
Nov 21 19:32:32 ubuntu NetworkManager: <information>^IDHCP daemon state is now 1 (starting) for interface eth0 
Nov 21 19:32:32 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
Nov 21 19:32:32 ubuntu dhclient: DHCPOFFER from 192.168.15.1
Nov 21 19:32:32 ubuntu dhclient: DHCPREQUEST on eth0 to 255.255.255.255 port 67
Nov 21 19:32:32 ubuntu dhclient: DHCPACK from 192.168.15.1
Nov 21 19:32:32 ubuntu avahi-daemon[5194]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.15.102.
Nov 21 19:32:32 ubuntu avahi-daemon[5194]: New relevant interface eth0.IPv4 for mDNS.
Nov 21 19:32:32 ubuntu avahi-daemon[5194]: Registering new address record for 192.168.15.102 on eth0.IPv4.
Nov 21 19:32:32 ubuntu NetworkManager: <information>^IDHCP daemon state is now 2 (bound) for interface eth0 
Nov 21 19:32:32 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 4 of 5 (IP Configure Get) scheduled... 
Nov 21 19:32:32 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 4 of 5 (IP Configure Get) started... 
Nov 21 19:32:32 ubuntu NetworkManager: <information>^IRetrieved the following IP4 configuration from the DHCP daemon: 
Nov 21 19:32:32 ubuntu NetworkManager: <information>^I  address 192.168.15.102 
Nov 21 19:32:32 ubuntu NetworkManager: <information>^I  netmask 255.255.255.0 
Nov 21 19:32:32 ubuntu NetworkManager: <information>^I  broadcast 192.168.15.255 
Nov 21 19:32:32 ubuntu NetworkManager: <information>^I  gateway 192.168.15.1 
Nov 21 19:32:32 ubuntu NetworkManager: <information>^I  nameserver 192.168.15.1 
Nov 21 19:32:32 ubuntu NetworkManager: <information>^I  hostname 'ubuntu' 
Nov 21 19:32:32 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 5 of 5 (IP Configure Commit) scheduled... 
Nov 21 19:32:32 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 4 of 5 (IP Configure Get) complete. 
Nov 21 19:32:32 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 5 of 5 (IP Configure Commit) started... 
Nov 21 19:32:32 ubuntu dhclient: bound to 192.168.15.102 -- renewal in 33120 seconds.
Nov 21 19:32:32 ubuntu avahi-daemon[5194]: Withdrawing address record for 192.168.15.102 on eth0.
Nov 21 19:32:32 ubuntu avahi-daemon[5194]: Leaving mDNS multicast group on interface eth0.IPv4 with address 192.168.15.102.
Nov 21 19:32:32 ubuntu avahi-daemon[5194]: Interface eth0.IPv4 no longer relevant for mDNS.
Nov 21 19:32:32 ubuntu avahi-daemon[5194]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.15.102.
Nov 21 19:32:32 ubuntu avahi-daemon[5194]: New relevant interface eth0.IPv4 for mDNS.
Nov 21 19:32:32 ubuntu avahi-daemon[5194]: Registering new address record for 192.168.15.102 on eth0.IPv4.
Nov 21 19:32:33 ubuntu NetworkManager: <information>^IClearing nscd hosts cache. 
Nov 21 19:32:33 ubuntu NetworkManager: <WARNING>^I nm_spawn_process (): nm_spawn_process('/usr/sbin/nscd -i hosts'): could not spawn process. (Failed to execute child process "/usr/sbin/nscd" (No such file or directory))  
Nov 21 19:32:33 ubuntu NetworkManager: <information>^IActivation (eth0) successful, device activated. 
Nov 21 19:32:33 ubuntu NetworkManager: <information>^IActivation (eth0) Finish handler scheduled. 
Nov 21 19:32:33 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 5 of 5 (IP Configure Commit) complete. 
Nov 21 19:32:35 ubuntu avahi-daemon[5194]: Registering new address record for fe80::203:25ff:fe3f:b1e6 on eth0.*.
Nov 21 19:32:59 ubuntu ntpdate[7492]: adjust time server 91.189.94.4 offset -0.063306 sec
Nov 21 19:38:05 ubuntu NetworkManager: <information>^IGoing to sleep. 
Nov 21 19:38:05 ubuntu dhclient: There is already a pid file /var/run/dhclient.eth0.pid with pid 7432
Nov 21 19:38:05 ubuntu dhclient: killed old client process, removed PID file
Nov 21 19:38:05 ubuntu avahi-daemon[5194]: Interface eth0.IPv4 no longer relevant for mDNS.
Nov 21 19:38:05 ubuntu avahi-daemon[5194]: Leaving mDNS multicast group on interface eth0.IPv4 with address 192.168.15.102.
Nov 21 19:38:05 ubuntu NetworkManager: <information>^IWaking up from sleep. 
Nov 21 19:38:05 ubuntu NetworkManager: <information>^IDeactivating device eth0. 
Nov 21 19:38:05 ubuntu avahi-daemon[5194]: Withdrawing address record for fe80::203:25ff:fe3f:b1e6 on eth0.
Nov 21 19:38:05 ubuntu avahi-daemon[5194]: Withdrawing address record for 192.168.15.102 on eth0.
Nov 21 19:38:05 ubuntu NetworkManager: <information>^Ieth0: Device is fully-supported using driver 'sky2'. 
Nov 21 19:38:05 ubuntu NetworkManager: <information>^Inm_device_init(): waiting for device's worker thread to start 
Nov 21 19:38:05 ubuntu NetworkManager: <information>^Inm_device_init(): device's worker thread started, continuing. 
Nov 21 19:38:05 ubuntu NetworkManager: <information>^INow managing wired Ethernet (802.3) device 'eth0'. 
Nov 21 19:38:05 ubuntu NetworkManager: <information>^IDeactivating device eth0. 
Nov 21 19:38:05 ubuntu dhclient: DHCPRELEASE on eth0 to 192.168.15.1 port 67
Nov 21 19:38:05 ubuntu dhclient: send_packet: Network is unreachable
Nov 21 19:38:05 ubuntu dhclient: send_packet: please consult README file regarding broadcast address.
Nov 21 19:38:05 ubuntu avahi-autoipd(eth0)[7745]: Found user 'avahi-autoipd' (UID 104) and group 'avahi-autoipd' (GID 110).
Nov 21 19:38:05 ubuntu avahi-autoipd(eth0)[7745]: Successfully called chroot().
Nov 21 19:38:05 ubuntu avahi-autoipd(eth0)[7745]: Successfully dropped root privileges.
Nov 21 19:38:05 ubuntu avahi-autoipd(eth0)[7745]: fopen() failed: Permission denied
Nov 21 19:38:05 ubuntu avahi-autoipd(eth0)[7745]: Starting with address 169.254.8.77
Nov 21 19:38:05 ubuntu NetworkManager: <information>^IWill activate wired connection 'eth0' because it now has a link. 
Nov 21 19:38:05 ubuntu NetworkManager: <information>^ISWITCH: no current connection, found better connection 'eth0'. 
Nov 21 19:38:05 ubuntu NetworkManager: <information>^IWill activate connection 'eth0'. 
Nov 21 19:38:05 ubuntu NetworkManager: <information>^IDevice eth0 activation scheduled... 
Nov 21 19:38:05 ubuntu NetworkManager: <information>^IActivation (eth0) started... 
Nov 21 19:38:05 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 1 of 5 (Device Prepare) scheduled... 
Nov 21 19:38:05 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 1 of 5 (Device Prepare) started... 
Nov 21 19:38:05 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 2 of 5 (Device Configure) scheduled... 
Nov 21 19:38:05 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 1 of 5 (Device Prepare) complete. 
Nov 21 19:38:05 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 2 of 5 (Device Configure) starting... 
Nov 21 19:38:05 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 2 of 5 (Device Configure) successful. 
Nov 21 19:38:05 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 3 of 5 (IP Configure Start) scheduled. 
Nov 21 19:38:05 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 2 of 5 (Device Configure) complete. 
Nov 21 19:38:05 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 3 of 5 (IP Configure Start) started... 
Nov 21 19:38:07 ubuntu NetworkManager: <information>^IActivation (eth0) Beginning DHCP transaction. 
Nov 21 19:38:07 ubuntu NetworkManager: <information>^ICouldn't send DHCP 'up' message because: name 'com.redhat.dhcp.OperationInProgress', message 'interface eth0 is being released. Please try again later.'. 
Nov 21 19:38:07 ubuntu NetworkManager: <information>^IActivation (eth0) failure scheduled... 
Nov 21 19:38:07 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 3 of 5 (IP Configure Start) complete. 
Nov 21 19:38:07 ubuntu NetworkManager: <information>^IActivation (eth0) failed. 
Nov 21 19:38:07 ubuntu NetworkManager: <information>^IDeactivating device eth0. 
Nov 21 19:38:08 ubuntu NetworkManager: <information>^IGoing to sleep. 
Nov 21 19:38:08 ubuntu avahi-autoipd(eth0)[7745]: SIOCSIFFLAGS failed: Permission denied
Nov 21 19:38:08 ubuntu NetworkManager: <information>^IWaking up from sleep. 
Nov 21 19:38:08 ubuntu NetworkManager: <information>^IDeactivating device eth0. 
Nov 21 19:38:08 ubuntu NetworkManager: <information>^Ieth0: Device is fully-supported using driver 'sky2'. 
Nov 21 19:38:08 ubuntu NetworkManager: <information>^Inm_device_init(): waiting for device's worker thread to start 
Nov 21 19:38:08 ubuntu NetworkManager: <information>^Inm_device_init(): device's worker thread started, continuing. 
Nov 21 19:38:08 ubuntu NetworkManager: <information>^INow managing wired Ethernet (802.3) device 'eth0'. 
Nov 21 19:38:08 ubuntu NetworkManager: <information>^IDeactivating device eth0. 
Nov 21 19:38:08 ubuntu NetworkManager: <information>^IWill activate wired connection 'eth0' because it now has a link. 
Nov 21 19:38:08 ubuntu NetworkManager: <information>^ISWITCH: no current connection, found better connection 'eth0'. 
Nov 21 19:38:08 ubuntu NetworkManager: <information>^IWill activate connection 'eth0'. 
Nov 21 19:38:08 ubuntu NetworkManager: <information>^IDevice eth0 activation scheduled... 
Nov 21 19:38:08 ubuntu NetworkManager: <information>^IActivation (eth0) started... 
Nov 21 19:38:08 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 1 of 5 (Device Prepare) scheduled... 
Nov 21 19:38:08 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 1 of 5 (Device Prepare) started... 
Nov 21 19:38:08 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 2 of 5 (Device Configure) scheduled... 
Nov 21 19:38:09 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 1 of 5 (Device Prepare) complete. 
Nov 21 19:38:09 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 2 of 5 (Device Configure) starting... 
Nov 21 19:38:09 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 2 of 5 (Device Configure) successful. 
Nov 21 19:38:09 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 3 of 5 (IP Configure Start) scheduled. 
Nov 21 19:38:09 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 2 of 5 (Device Configure) complete. 
Nov 21 19:38:09 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 3 of 5 (IP Configure Start) started... 
Nov 21 19:38:09 ubuntu NetworkManager: <information>^IActivation (eth0) Beginning DHCP transaction. 
Nov 21 19:38:09 ubuntu dhclient: There is already a pid file /var/run/dhclient.eth0.pid with pid 134993440
Nov 21 19:38:10 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 3 of 5 (IP Configure Start) complete. 
Nov 21 19:38:10 ubuntu NetworkManager: <information>^IDHCP daemon state is now 12 (successfully started) for interface eth0 
Nov 21 19:38:11 ubuntu NetworkManager: <information>^IDHCP daemon state is now 1 (starting) for interface eth0 
Nov 21 19:38:13 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
Nov 21 19:38:13 ubuntu dhclient: DHCPOFFER from 192.168.15.1
Nov 21 19:38:13 ubuntu dhclient: DHCPREQUEST on eth0 to 255.255.255.255 port 67
Nov 21 19:38:13 ubuntu dhclient: DHCPACK from 192.168.15.1
Nov 21 19:38:13 ubuntu avahi-daemon[5194]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.15.102.
Nov 21 19:38:13 ubuntu avahi-daemon[5194]: New relevant interface eth0.IPv4 for mDNS.
Nov 21 19:38:13 ubuntu avahi-daemon[5194]: Registering new address record for 192.168.15.102 on eth0.IPv4.
Nov 21 19:38:13 ubuntu NetworkManager: <information>^IDHCP daemon state is now 2 (bound) for interface eth0 
Nov 21 19:38:13 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 4 of 5 (IP Configure Get) scheduled... 
Nov 21 19:38:13 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 4 of 5 (IP Configure Get) started... 
Nov 21 19:38:13 ubuntu NetworkManager: <information>^IRetrieved the following IP4 configuration from the DHCP daemon: 
Nov 21 19:38:13 ubuntu NetworkManager: <information>^I  address 192.168.15.102 
Nov 21 19:38:13 ubuntu NetworkManager: <information>^I  netmask 255.255.255.0 
Nov 21 19:38:13 ubuntu NetworkManager: <information>^I  broadcast 192.168.15.255 
Nov 21 19:38:13 ubuntu NetworkManager: <information>^I  gateway 192.168.15.1 
Nov 21 19:38:13 ubuntu NetworkManager: <information>^I  nameserver 192.168.15.1 
Nov 21 19:38:13 ubuntu NetworkManager: <information>^I  hostname 'ubuntu' 
Nov 21 19:38:13 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 5 of 5 (IP Configure Commit) scheduled... 
Nov 21 19:38:13 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 4 of 5 (IP Configure Get) complete. 
Nov 21 19:38:13 ubuntu dhclient: bound to 192.168.15.102 -- renewal in 43195 seconds.
Nov 21 19:38:13 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 5 of 5 (IP Configure Commit) started... 
Nov 21 19:38:13 ubuntu avahi-daemon[5194]: Withdrawing address record for 192.168.15.102 on eth0.
Nov 21 19:38:13 ubuntu avahi-daemon[5194]: Leaving mDNS multicast group on interface eth0.IPv4 with address 192.168.15.102.
Nov 21 19:38:13 ubuntu avahi-daemon[5194]: Interface eth0.IPv4 no longer relevant for mDNS.
Nov 21 19:38:13 ubuntu avahi-daemon[5194]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.15.102.
Nov 21 19:38:13 ubuntu avahi-daemon[5194]: New relevant interface eth0.IPv4 for mDNS.
Nov 21 19:38:13 ubuntu avahi-daemon[5194]: Registering new address record for 192.168.15.102 on eth0.IPv4.
Nov 21 19:38:14 ubuntu NetworkManager: <information>^IClearing nscd hosts cache. 
Nov 21 19:38:14 ubuntu NetworkManager: <WARNING>^I nm_spawn_process (): nm_spawn_process('/usr/sbin/nscd -i hosts'): could not spawn process. (Failed to execute child process "/usr/sbin/nscd" (No such file or directory))  
Nov 21 19:38:14 ubuntu NetworkManager: <information>^IActivation (eth0) Finish handler scheduled. 
Nov 21 19:38:14 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 5 of 5 (IP Configure Commit) complete. 
Nov 21 19:38:14 ubuntu NetworkManager: <information>^IActivation (eth0) successful, device activated. 
Nov 21 19:38:15 ubuntu avahi-daemon[5194]: Registering new address record for fe80::203:25ff:fe3f:b1e6 on eth0.*.
Nov 21 19:38:44 ubuntu ntpdate[7895]: can't find host ntp.ubuntu.com 
Nov 21 19:38:44 ubuntu ntpdate[7895]: no servers can be used, exiting
Nov 21 19:40:10 ubuntu gdm[5249]: Restarting computer...
Nov 21 19:40:12 ubuntu init: tty6 main process (4617) killed by TERM signal
Nov 21 19:40:12 ubuntu init: tty1 main process (4616) killed by TERM signal
Nov 21 19:40:12 ubuntu init: tty4 main process (4609) killed by TERM signal
Nov 21 19:40:13 ubuntu init: tty5 main process (4610) killed by TERM signal
Nov 21 19:40:13 ubuntu init: tty2 main process (4612) killed by TERM signal
Nov 21 19:40:13 ubuntu init: tty3 main process (4614) killed by TERM signal
Nov 21 19:41:57 ubuntu NetworkManager: <information>^Istarting... 
Nov 21 19:41:58 ubuntu NetworkManager: <information>^Ieth0: Device is fully-supported using driver 'sky2'. 
Nov 21 19:41:58 ubuntu NetworkManager: <information>^Inm_device_init(): waiting for device's worker thread to start 
Nov 21 19:41:58 ubuntu NetworkManager: <information>^Inm_device_init(): device's worker thread started, continuing. 
Nov 21 19:41:58 ubuntu NetworkManager: <information>^INow managing wired Ethernet (802.3) device 'eth0'. 
Nov 21 19:41:58 ubuntu NetworkManager: <information>^IDeactivating device eth0. 
Nov 21 19:41:58 ubuntu NetworkManager: <information>^IWill activate wired connection 'eth0' because it now has a link. 
Nov 21 19:41:58 ubuntu NetworkManager: <information>^ISWITCH: no current connection, found better connection 'eth0'. 
Nov 21 19:41:58 ubuntu NetworkManager: <information>^IWill activate connection 'eth0'. 
Nov 21 19:41:58 ubuntu NetworkManager: <information>^IDevice eth0 activation scheduled... 
Nov 21 19:41:58 ubuntu NetworkManager: <information>^IActivation (eth0) started... 
Nov 21 19:41:58 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 1 of 5 (Device Prepare) scheduled... 
Nov 21 19:41:58 ubuntu avahi-daemon[5308]: Found user 'avahi' (UID 105) and group 'avahi' (GID 111).
Nov 21 19:41:58 ubuntu avahi-daemon[5308]: Successfully dropped root privileges.
Nov 21 19:41:58 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 1 of 5 (Device Prepare) started... 
Nov 21 19:41:58 ubuntu avahi-daemon[5308]: avahi-daemon 0.6.17 starting up.
Nov 21 19:41:58 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 2 of 5 (Device Configure) scheduled... 
Nov 21 19:41:58 ubuntu avahi-daemon[5308]: Successfully called chroot().
Nov 21 19:41:58 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 1 of 5 (Device Prepare) complete. 
Nov 21 19:41:58 ubuntu avahi-daemon[5308]: Successfully dropped remaining capabilities.
Nov 21 19:41:58 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 2 of 5 (Device Configure) starting... 
Nov 21 19:41:58 ubuntu avahi-daemon[5308]: No service found in /etc/avahi/services.
Nov 21 19:41:58 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 2 of 5 (Device Configure) successful. 
Nov 21 19:41:58 ubuntu avahi-daemon[5308]: Network interface enumeration completed.
Nov 21 19:41:58 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 3 of 5 (IP Configure Start) scheduled. 
Nov 21 19:41:58 ubuntu avahi-daemon[5308]: Registering HINFO record with values 'I686'/'LINUX'.
Nov 21 19:41:58 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 2 of 5 (Device Configure) complete. 
Nov 21 19:41:58 ubuntu avahi-daemon[5308]: Server startup complete. Host name is ubuntu.local. Local service cookie is 1978669938.
Nov 21 19:41:58 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 3 of 5 (IP Configure Start) started... 
Nov 21 19:42:00 ubuntu NetworkManager: <information>^IActivation (eth0) Beginning DHCP transaction. 
Nov 21 19:42:00 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 3 of 5 (IP Configure Start) complete. 
Nov 21 19:42:00 ubuntu NetworkManager: <information>^IDHCP daemon state is now 12 (successfully started) for interface eth0 
Nov 21 19:42:01 ubuntu NetworkManager: <information>^IDHCP daemon state is now 1 (starting) for interface eth0 
Nov 21 19:42:02 ubuntu dhclient: DHCPREQUEST on eth0 to 255.255.255.255 port 67
Nov 21 19:42:02 ubuntu dhclient: DHCPACK from 192.168.15.1
Nov 21 19:42:02 ubuntu avahi-daemon[5308]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.15.102.
Nov 21 19:42:02 ubuntu avahi-daemon[5308]: New relevant interface eth0.IPv4 for mDNS.
Nov 21 19:42:02 ubuntu avahi-daemon[5308]: Registering new address record for 192.168.15.102 on eth0.IPv4.
Nov 21 19:42:02 ubuntu NetworkManager: <information>^IDHCP daemon state is now 4 (reboot) for interface eth0 
Nov 21 19:42:03 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 4 of 5 (IP Configure Get) scheduled... 
Nov 21 19:42:03 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 4 of 5 (IP Configure Get) started... 
Nov 21 19:42:03 ubuntu NetworkManager: <information>^IRetrieved the following IP4 configuration from the DHCP daemon: 
Nov 21 19:42:03 ubuntu NetworkManager: <information>^I  address 192.168.15.102 
Nov 21 19:42:03 ubuntu NetworkManager: <information>^I  netmask 255.255.255.0 
Nov 21 19:42:03 ubuntu dhclient: bound to 192.168.15.102 -- renewal in 36493 seconds.
Nov 21 19:42:03 ubuntu NetworkManager: <information>^I  broadcast 192.168.15.255 
Nov 21 19:42:03 ubuntu NetworkManager: <information>^I  gateway 192.168.15.1 
Nov 21 19:42:03 ubuntu NetworkManager: <information>^I  nameserver 192.168.15.1 
Nov 21 19:42:03 ubuntu NetworkManager: <information>^I  hostname 'ubuntu' 
Nov 21 19:42:03 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 5 of 5 (IP Configure Commit) scheduled... 
Nov 21 19:42:03 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 4 of 5 (IP Configure Get) complete. 
Nov 21 19:42:03 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 5 of 5 (IP Configure Commit) started... 
Nov 21 19:42:03 ubuntu hcid[5569]: Bluetooth HCI daemon
Nov 21 19:42:03 ubuntu avahi-daemon[5308]: Withdrawing address record for 192.168.15.102 on eth0.
Nov 21 19:42:04 ubuntu hcid[5569]: Starting SDP server
Nov 21 19:42:04 ubuntu avahi-daemon[5308]: Leaving mDNS multicast group on interface eth0.IPv4 with address 192.168.15.102.
Nov 21 19:42:04 ubuntu NetworkManager: <debug info>^I[1195692123.633821] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_bluetooth'). 
Nov 21 19:42:04 ubuntu avahi-daemon[5308]: Interface eth0.IPv4 no longer relevant for mDNS.
Nov 21 19:42:04 ubuntu avahi-daemon[5308]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.15.102.
Nov 21 19:42:04 ubuntu avahi-daemon[5308]: New relevant interface eth0.IPv4 for mDNS.
Nov 21 19:42:04 ubuntu avahi-daemon[5308]: Registering new address record for 192.168.15.102 on eth0.IPv4.
Nov 21 19:42:04 ubuntu NetworkManager: <information>^IClearing nscd hosts cache. 
Nov 21 19:42:04 ubuntu NetworkManager: <WARNING>^I nm_spawn_process (): nm_spawn_process('/usr/sbin/nscd -i hosts'): could not spawn process. (Failed to execute child process "/usr/sbin/nscd" (No such file or directory))  
Nov 21 19:42:05 ubuntu NetworkManager: <information>^IActivation (eth0) successful, device activated. 
Nov 21 19:42:05 ubuntu NetworkManager: <information>^IActivation (eth0) Finish handler scheduled. 
Nov 21 19:42:05 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 5 of 5 (IP Configure Commit) complete. 
Nov 21 19:42:06 ubuntu avahi-daemon[5308]: Registering new address record for fe80::203:25ff:fe3f:b1e6 on eth0.*.
Nov 21 19:42:16 ubuntu ntpdate[5789]: adjust time server 91.189.94.4 offset -0.294968 sec
Nov 21 19:42:43 ubuntu NetworkManager: <information>^IUpdating allowed wireless network lists. 
Nov 21 19:42:44 ubuntu NetworkManager: <WARNING>^I nm_dbus_get_networks_cb (): error received: org.freedesktop.NetworkManagerInfo.NoNetworks - There are no wireless networks stored.. 
Nov 21 19:43:29 ubuntu dhclient: There is already a pid file /var/run/dhclient.eth0.pid with pid 5404
Nov 21 19:43:29 ubuntu dhclient: killed old client process, removed PID file
Nov 21 19:43:29 ubuntu dhclient: Internet Systems Consortium DHCP Client V3.0.4
Nov 21 19:43:29 ubuntu dhclient: Copyright 2004-2006 Internet Systems Consortium.
Nov 21 19:43:29 ubuntu dhclient: All rights reserved.
Nov 21 19:43:29 ubuntu dhclient: For info, please visit http://www.isc.org/sw/dhcp/
Nov 21 19:43:29 ubuntu dhclient: 
Nov 21 19:43:29 ubuntu NetworkManager: <information>^IDHCP daemon state is now 14 (normal exit) for interface eth0 
Nov 21 19:43:29 ubuntu dhclient: Listening on LPF/eth0/00:03:25:3f:b1:e6
Nov 21 19:43:29 ubuntu dhclient: Sending on   LPF/eth0/00:03:25:3f:b1:e6
Nov 21 19:43:29 ubuntu dhclient: Sending on   Socket/fallback
Nov 21 19:43:29 ubuntu dhclient: DHCPRELEASE on eth0 to 192.168.15.1 port 67
Nov 21 19:43:29 ubuntu avahi-daemon[5308]: Withdrawing address record for 192.168.15.102 on eth0.
Nov 21 19:43:29 ubuntu avahi-daemon[5308]: Leaving mDNS multicast group on interface eth0.IPv4 with address 192.168.15.102.
Nov 21 19:43:29 ubuntu avahi-daemon[5308]: Interface eth0.IPv4 no longer relevant for mDNS.
Nov 21 19:43:29 ubuntu avahi-autoipd(eth0)[6055]: Found user 'avahi-autoipd' (UID 104) and group 'avahi-autoipd' (GID 110).
Nov 21 19:43:29 ubuntu avahi-autoipd(eth0)[6055]: Successfully called chroot().
Nov 21 19:43:29 ubuntu avahi-autoipd(eth0)[6055]: Successfully dropped root privileges.
Nov 21 19:43:29 ubuntu avahi-autoipd(eth0)[6055]: fopen() failed: Permission denied
Nov 21 19:43:29 ubuntu avahi-autoipd(eth0)[6055]: Starting with address 169.254.8.77
Nov 21 19:43:34 ubuntu avahi-autoipd(eth0)[6055]: Callout BIND, address 169.254.8.77 on interface eth0
Nov 21 19:43:34 ubuntu avahi-daemon[5308]: Joining mDNS multicast group on interface eth0.IPv4 with address 169.254.8.77.
Nov 21 19:43:34 ubuntu avahi-daemon[5308]: New relevant interface eth0.IPv4 for mDNS.
Nov 21 19:43:34 ubuntu avahi-daemon[5308]: Registering new address record for 169.254.8.77 on eth0.IPv4.
Nov 21 19:43:38 ubuntu avahi-autoipd(eth0)[6055]: Successfully claimed IP address 169.254.8.77
Nov 21 19:43:39 ubuntu avahi-autoipd(eth0)[6055]: fopen() failed: Permission denied
Nov 21 19:43:39 ubuntu avahi-daemon[5308]: Interface eth0.IPv4 no longer relevant for mDNS.
Nov 21 19:43:39 ubuntu avahi-daemon[5308]: Leaving mDNS multicast group on interface eth0.IPv4 with address 169.254.8.77.
Nov 21 19:43:39 ubuntu NetworkManager: <information>^ISWITCH: terminating current connection 'eth0' because it's no longer valid. 
Nov 21 19:43:39 ubuntu NetworkManager: <information>^IDeactivating device eth0. 
Nov 21 19:43:39 ubuntu avahi-autoipd(eth0)[6055]: SIOCSIFFLAGS failed: Permission denied
Nov 21 19:43:39 ubuntu avahi-autoipd(eth0)[6055]: Callout STOP, address 169.254.8.77 on interface eth0
Nov 21 19:43:39 ubuntu avahi-daemon[5308]: Withdrawing address record for fe80::203:25ff:fe3f:b1e6 on eth0.
Nov 21 19:43:39 ubuntu avahi-daemon[5308]: Withdrawing address record for 169.254.8.77 on eth0.
Nov 21 19:43:39 ubuntu NetworkManager: nm_device_is_802_3_ethernet: assertion `dev != NULL' failed
Nov 21 19:43:39 ubuntu NetworkManager: nm_device_is_802_11_wireless: assertion `dev != NULL' failed
Nov 21 19:43:39 ubuntu avahi-autoipd(eth0)[6056]: client: RTNETLINK answers: No such device
Nov 21 19:43:39 ubuntu avahi-autoipd(eth0)[6056]: Script execution failed with return value 2
Nov 21 19:45:50 ubuntu NetworkManager: <information>^IWill activate wired connection 'eth0' because it now has a link. 
Nov 21 19:45:51 ubuntu NetworkManager: <information>^IWill activate wired connection 'eth0' because it now has a link. 
Nov 21 19:45:51 ubuntu NetworkManager: <information>^ISWITCH: no current connection, found better connection 'eth0'. 
Nov 21 19:45:51 ubuntu NetworkManager: <information>^IWill activate connection 'eth0'. 
Nov 21 19:45:51 ubuntu NetworkManager: <information>^IDevice eth0 activation scheduled... 
Nov 21 19:45:51 ubuntu NetworkManager: <information>^IActivation (eth0) started... 
Nov 21 19:45:51 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 1 of 5 (Device Prepare) scheduled... 
Nov 21 19:45:51 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 1 of 5 (Device Prepare) started... 
Nov 21 19:45:51 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 2 of 5 (Device Configure) scheduled... 
Nov 21 19:45:51 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 1 of 5 (Device Prepare) complete. 
Nov 21 19:45:51 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 2 of 5 (Device Configure) starting... 
Nov 21 19:45:51 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 2 of 5 (Device Configure) successful. 
Nov 21 19:45:51 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 3 of 5 (IP Configure Start) scheduled. 
Nov 21 19:45:51 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 2 of 5 (Device Configure) complete. 
Nov 21 19:45:51 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 3 of 5 (IP Configure Start) started... 
Nov 21 19:45:52 ubuntu avahi-daemon[5308]: Registering new address record for fe80::203:25ff:fe3f:b1e6 on eth0.*.
Nov 21 19:45:53 ubuntu NetworkManager: <information>^IActivation (eth0) Beginning DHCP transaction. 
Nov 21 19:45:53 ubuntu dhclient: There is already a pid file /var/run/dhclient.eth0.pid with pid 134993440
Nov 21 19:45:53 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 3 of 5 (IP Configure Start) complete. 
Nov 21 19:45:53 ubuntu NetworkManager: <information>^IDHCP daemon state is now 12 (successfully started) for interface eth0 
Nov 21 19:45:54 ubuntu NetworkManager: <information>^IDHCP daemon state is now 1 (starting) for interface eth0 
Nov 21 19:45:58 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
Nov 21 19:45:58 ubuntu dhclient: DHCPOFFER from 192.168.15.1
Nov 21 19:45:58 ubuntu dhclient: DHCPREQUEST on eth0 to 255.255.255.255 port 67
Nov 21 19:45:58 ubuntu dhclient: DHCPACK from 192.168.15.1
Nov 21 19:45:58 ubuntu avahi-daemon[5308]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.15.102.
Nov 21 19:45:58 ubuntu avahi-daemon[5308]: New relevant interface eth0.IPv4 for mDNS.
Nov 21 19:45:58 ubuntu avahi-daemon[5308]: Registering new address record for 192.168.15.102 on eth0.IPv4.
Nov 21 19:45:58 ubuntu NetworkManager: <information>^IDHCP daemon state is now 2 (bound) for interface eth0 
Nov 21 19:45:58 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 4 of 5 (IP Configure Get) scheduled... 
Nov 21 19:45:58 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 4 of 5 (IP Configure Get) started... 
Nov 21 19:45:58 ubuntu dhclient: bound to 192.168.15.102 -- renewal in 39338 seconds.
Nov 21 19:45:58 ubuntu NetworkManager: <information>^IRetrieved the following IP4 configuration from the DHCP daemon: 
Nov 21 19:45:58 ubuntu NetworkManager: <information>^I  address 192.168.15.102 
Nov 21 19:45:58 ubuntu NetworkManager: <information>^I  netmask 255.255.255.0 
Nov 21 19:45:58 ubuntu NetworkManager: <information>^I  broadcast 192.168.15.255 
Nov 21 19:45:58 ubuntu NetworkManager: <information>^I  gateway 192.168.15.1 
Nov 21 19:45:58 ubuntu NetworkManager: <information>^I  nameserver 192.168.15.1 
Nov 21 19:45:58 ubuntu NetworkManager: <information>^I  hostname 'ubuntu' 
Nov 21 19:45:58 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 5 of 5 (IP Configure Commit) scheduled... 
Nov 21 19:45:58 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 4 of 5 (IP Configure Get) complete. 
Nov 21 19:45:58 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 5 of 5 (IP Configure Commit) started... 
Nov 21 19:45:58 ubuntu dhclient: receive_packet failed on eth0: Network is down
Nov 21 19:45:58 ubuntu avahi-daemon[5308]: Interface eth0.IPv4 no longer relevant for mDNS.
Nov 21 19:45:58 ubuntu NetworkManager: <information>^IOld device 'eth0' activating, won't change. 
Nov 21 19:45:58 ubuntu avahi-daemon[5308]: Leaving mDNS multicast group on interface eth0.IPv4 with address 192.168.15.102.
Nov 21 19:45:58 ubuntu avahi-daemon[5308]: Withdrawing address record for fe80::203:25ff:fe3f:b1e6 on eth0.
Nov 21 19:45:58 ubuntu avahi-daemon[5308]: Withdrawing address record for 192.168.15.102 on eth0.
Nov 21 19:45:59 ubuntu NetworkManager: <information>^IClearing nscd hosts cache. 
Nov 21 19:45:59 ubuntu NetworkManager: <WARNING>^I nm_spawn_process (): nm_spawn_process('/usr/sbin/nscd -i hosts'): could not spawn process. (Failed to execute child process "/usr/sbin/nscd" (No such file or directory))  
Nov 21 19:45:59 ubuntu NetworkManager: <information>^IActivation (eth0) successful, device activated. 
Nov 21 19:45:59 ubuntu NetworkManager: <information>^IActivation (eth0) Finish handler scheduled. 
Nov 21 19:45:59 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 5 of 5 (IP Configure Commit) complete. 
Nov 21 19:46:09 ubuntu ntpdate[6382]: can't find host ntp.ubuntu.com 
Nov 21 19:46:09 ubuntu ntpdate[6382]: no servers can be used, exiting
Nov 21 21:17:17 ubuntu gdm[5359]: Restarting computer...
Nov 21 21:17:19 ubuntu init: tty4 main process (4718) killed by TERM signal
Nov 21 21:17:19 ubuntu init: tty5 main process (4719) killed by TERM signal
Nov 21 21:17:19 ubuntu init: tty3 main process (4723) killed by TERM signal
Nov 21 21:17:19 ubuntu init: tty2 main process (4721) killed by TERM signal
Nov 21 21:17:19 ubuntu init: tty1 main process (4725) killed by TERM signal
Nov 21 21:17:19 ubuntu init: tty6 main process (4726) killed by TERM signal
Nov 21 21:19:12 ubuntu NetworkManager: <information>^Istarting... 
Nov 21 21:19:12 ubuntu NetworkManager: <information>^Ieth0: Device is fully-supported using driver 'sky2'. 
Nov 21 21:19:12 ubuntu NetworkManager: <information>^Inm_device_init(): waiting for device's worker thread to start 
Nov 21 21:19:12 ubuntu NetworkManager: <information>^Inm_device_init(): device's worker thread started, continuing. 
Nov 21 21:19:12 ubuntu NetworkManager: <information>^INow managing wired Ethernet (802.3) device 'eth0'. 
Nov 21 21:19:13 ubuntu NetworkManager: <information>^IDeactivating device eth0. 
Nov 21 21:19:13 ubuntu avahi-daemon[5264]: Found user 'avahi' (UID 105) and group 'avahi' (GID 111).
Nov 21 21:19:13 ubuntu avahi-daemon[5264]: Successfully dropped root privileges.
Nov 21 21:19:13 ubuntu avahi-daemon[5264]: avahi-daemon 0.6.17 starting up.
Nov 21 21:19:13 ubuntu avahi-daemon[5264]: Successfully called chroot().
Nov 21 21:19:13 ubuntu avahi-daemon[5264]: Successfully dropped remaining capabilities.
Nov 21 21:19:13 ubuntu avahi-daemon[5264]: No service found in /etc/avahi/services.
Nov 21 21:19:13 ubuntu avahi-daemon[5264]: Network interface enumeration completed.
Nov 21 21:19:13 ubuntu avahi-daemon[5264]: Registering HINFO record with values 'I686'/'LINUX'.
Nov 21 21:19:13 ubuntu avahi-daemon[5264]: Server startup complete. Host name is ubuntu.local. Local service cookie is 189273392.
Nov 21 21:19:15 ubuntu NetworkManager: <information>^IWill activate wired connection 'eth0' because it now has a link. 
Nov 21 21:19:15 ubuntu NetworkManager: <information>^ISWITCH: no current connection, found better connection 'eth0'. 
Nov 21 21:19:15 ubuntu NetworkManager: <information>^IWill activate connection 'eth0'. 
Nov 21 21:19:15 ubuntu NetworkManager: <information>^IDevice eth0 activation scheduled... 
Nov 21 21:19:16 ubuntu NetworkManager: <information>^IActivation (eth0) started... 
Nov 21 21:19:16 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 1 of 5 (Device Prepare) scheduled... 
Nov 21 21:19:16 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 1 of 5 (Device Prepare) started... 
Nov 21 21:19:16 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 2 of 5 (Device Configure) scheduled... 
Nov 21 21:19:16 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 1 of 5 (Device Prepare) complete. 
Nov 21 21:19:17 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 2 of 5 (Device Configure) starting... 
Nov 21 21:19:17 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 2 of 5 (Device Configure) successful. 
Nov 21 21:19:17 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 3 of 5 (IP Configure Start) scheduled. 
Nov 21 21:19:17 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 2 of 5 (Device Configure) complete. 
Nov 21 21:19:18 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 3 of 5 (IP Configure Start) started... 
Nov 21 21:19:18 ubuntu NetworkManager: <information>^IActivation (eth0) Beginning DHCP transaction. 
Nov 21 21:19:18 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 3 of 5 (IP Configure Start) complete. 
Nov 21 21:19:18 ubuntu NetworkManager: <information>^IDHCP daemon state is now 12 (successfully started) for interface eth0 
Nov 21 21:19:18 ubuntu hcid[5510]: Bluetooth HCI daemon
Nov 21 21:19:19 ubuntu hcid[5510]: Starting SDP server
Nov 21 21:19:19 ubuntu NetworkManager: <debug info>^I[1195697957.677692] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_bluetooth'). 
Nov 21 21:19:19 ubuntu NetworkManager: <information>^IDHCP daemon state is now 1 (starting) for interface eth0 
Nov 21 21:19:19 ubuntu dhclient: DHCPREQUEST on eth0 to 255.255.255.255 port 67
Nov 21 21:19:19 ubuntu dhclient: DHCPACK from 192.168.15.1
Nov 21 21:19:19 ubuntu avahi-daemon[5264]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.15.102.
Nov 21 21:19:19 ubuntu NetworkManager: <information>^IDHCP daemon state is now 4 (reboot) for interface eth0 
Nov 21 21:19:19 ubuntu avahi-daemon[5264]: New relevant interface eth0.IPv4 for mDNS.
Nov 21 21:19:19 ubuntu dhclient: bound to 192.168.15.102 -- renewal in 34764 seconds.
Nov 21 21:19:20 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 4 of 5 (IP Configure Get) scheduled... 
Nov 21 21:19:20 ubuntu avahi-daemon[5264]: Registering new address record for 192.168.15.102 on eth0.IPv4.
Nov 21 21:19:20 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 4 of 5 (IP Configure Get) started... 
Nov 21 21:19:39 ubuntu NetworkManager: <information>^IRetrieved the following IP4 configuration from the DHCP daemon: 
Nov 21 21:19:39 ubuntu NetworkManager: <information>^I  address 192.168.15.102 
Nov 21 21:19:39 ubuntu NetworkManager: <information>^I  netmask 255.255.255.0 
Nov 21 21:19:39 ubuntu NetworkManager: <information>^I  broadcast 192.168.15.255 
Nov 21 21:19:39 ubuntu NetworkManager: <information>^I  gateway 192.168.15.1 
Nov 21 21:19:39 ubuntu NetworkManager: <information>^I  nameserver 192.168.15.1 
Nov 21 21:19:39 ubuntu NetworkManager: <information>^I  hostname 'ubuntu' 
Nov 21 21:19:39 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 5 of 5 (IP Configure Commit) scheduled... 
Nov 21 21:19:39 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 4 of 5 (IP Configure Get) complete. 
Nov 21 21:19:39 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 5 of 5 (IP Configure Commit) started... 
Nov 21 21:19:39 ubuntu avahi-daemon[5264]: Withdrawing address record for 192.168.15.102 on eth0.
Nov 21 21:19:39 ubuntu avahi-daemon[5264]: Leaving mDNS multicast group on interface eth0.IPv4 with address 192.168.15.102.
Nov 21 21:19:39 ubuntu avahi-daemon[5264]: Interface eth0.IPv4 no longer relevant for mDNS.
Nov 21 21:19:39 ubuntu avahi-daemon[5264]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.15.102.
Nov 21 21:19:39 ubuntu avahi-daemon[5264]: New relevant interface eth0.IPv4 for mDNS.
Nov 21 21:19:39 ubuntu avahi-daemon[5264]: Registering new address record for 192.168.15.102 on eth0.IPv4.
Nov 21 21:19:40 ubuntu NetworkManager: <information>^IClearing nscd hosts cache. 
Nov 21 21:19:40 ubuntu NetworkManager: <WARNING>^I nm_spawn_process (): nm_spawn_process('/usr/sbin/nscd -i hosts'): could not spawn process. (Failed to execute child process "/usr/sbin/nscd" (No such file or directory))  
Nov 21 21:19:40 ubuntu NetworkManager: <information>^IActivation (eth0) Finish handler scheduled. 
Nov 21 21:19:40 ubuntu NetworkManager: <information>^IActivation (eth0) Stage 5 of 5 (IP Configure Commit) complete. 
Nov 21 21:19:40 ubuntu NetworkManager: <information>^IActivation (eth0) successful, device activated. 
Nov 21 21:19:42 ubuntu avahi-daemon[5264]: Registering new address record for fe80::203:25ff:fe3f:b1e6 on eth0.*.
Nov 21 21:19:51 ubuntu ntpdate[5821]: adjust time server 91.189.94.4 offset -0.076446 sec
Nov 21 21:20:06 ubuntu NetworkManager: <information>^IUpdating allowed wireless network lists. 
Nov 21 21:20:07 ubuntu NetworkManager: <WARNING>^I nm_dbus_get_networks_cb (): error received: org.freedesktop.NetworkManagerInfo.NoNetworks - There are no wireless networks stored.. 
Nov 21 22:30:43 ubuntu gdm[5315]: Restarting computer...
Nov 21 22:30:51 ubuntu init: tty3 main process (4679) killed by TERM signal
Nov 21 22:30:51 ubuntu init: tty6 main process (4682) killed by TERM signal
Nov 21 22:30:51 ubuntu init: tty1 main process (4681) killed by TERM signal
Nov 21 22:30:51 ubuntu init: tty2 main process (4677) killed by TERM signal
Nov 21 22:30:51 ubuntu init: tty5 main process (4675) killed by TERM signal
Nov 21 22:30:51 ubuntu init: tty4 main process (4674) killed by TERM signal
Nov 21 22:32:44 ubuntu NetworkManager: <information>^Istarting... 
Nov 21 22:32:44 ubuntu avahi-daemon[5216]: Found user 'avahi' (UID 105) and group 'avahi' (GID 111).
Nov 21 22:32:44 ubuntu avahi-daemon[5216]: Successfully dropped root privileges.
Nov 21 22:32:44 ubuntu avahi-daemon[5216]: avahi-daemon 0.6.17 starting up.
Nov 21 22:32:44 ubuntu avahi-daemon[5216]: Successfully called chroot().
Nov 21 22:32:44 ubuntu avahi-daemon[5216]: Successfully dropped remaining capabilities.
Nov 21 22:32:44 ubuntu avahi-daemon[5216]: No service found in /etc/avahi/services.
Nov 21 22:32:44 ubuntu avahi-daemon[5216]: Network interface enumeration completed.
Nov 21 22:32:45 ubuntu avahi-daemon[5216]: Registering HINFO record with values 'I686'/'LINUX'.
Nov 21 22:32:45 ubuntu avahi-daemon[5216]: Server startup complete. Host name is ubuntu.local. Local service cookie is 2355172797.
Nov 21 22:32:51 ubuntu hcid[5449]: Bluetooth HCI daemon
Nov 21 22:32:51 ubuntu hcid[5449]: Starting SDP server
Nov 21 22:33:37 ubuntu NetworkManager: <information>^IUpdating allowed wireless network lists. 
Nov 21 22:33:38 ubuntu NetworkManager: <WARNING>^I nm_dbus_get_networks_cb (): error received: org.freedesktop.NetworkManagerInfo.NoNetworks - There are no wireless networks stored.. 
Nov 21 22:38:10 ubuntu dhclient: Internet Systems Consortium DHCP Client V3.0.4
Nov 21 22:38:10 ubuntu dhclient: Copyright 2004-2006 Internet Systems Consortium.
Nov 21 22:38:10 ubuntu dhclient: All rights reserved.
Nov 21 22:38:10 ubuntu dhclient: For info, please visit http://www.isc.org/sw/dhcp/
Nov 21 22:38:10 ubuntu dhclient: 
Nov 21 22:38:11 ubuntu dhclient: Listening on LPF/eth0/00:03:25:3f:b1:e6
Nov 21 22:38:11 ubuntu dhclient: Sending on   LPF/eth0/00:03:25:3f:b1:e6
Nov 21 22:38:11 ubuntu dhclient: Sending on   Socket/fallback
Nov 21 22:38:11 ubuntu dhclient: DHCPREQUEST on eth0 to 255.255.255.255 port 67
Nov 21 22:38:13 ubuntu avahi-daemon[5216]: Registering new address record for fe80::203:25ff:fe3f:b1e6 on eth0.*.
Nov 21 22:38:19 ubuntu dhclient: DHCPREQUEST on eth0 to 255.255.255.255 port 67
Nov 21 22:38:19 ubuntu dhclient: DHCPACK from 192.168.15.1
Nov 21 22:38:19 ubuntu avahi-daemon[5216]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.15.102.
Nov 21 22:38:19 ubuntu avahi-daemon[5216]: New relevant interface eth0.IPv4 for mDNS.
Nov 21 22:38:19 ubuntu avahi-daemon[5216]: Registering new address record for 192.168.15.102 on eth0.IPv4.
Nov 21 22:38:19 ubuntu dhclient: bound to 192.168.15.102 -- renewal in 36896 seconds.
Nov 21 22:38:30 ubuntu ntpdate[6362]: adjust time server 91.189.94.4 offset 0.163613 sec
Nov 21 22:38:55 ubuntu avahi-daemon[5216]: Interface eth0.IPv4 no longer relevant for mDNS.
Nov 21 22:38:55 ubuntu avahi-daemon[5216]: Leaving mDNS multicast group on interface eth0.IPv4 with address 192.168.15.102.
Nov 21 22:38:55 ubuntu avahi-daemon[5216]: Withdrawing address record for fe80::203:25ff:fe3f:b1e6 on eth0.
Nov 21 22:38:55 ubuntu avahi-daemon[5216]: Withdrawing address record for 192.168.15.102 on eth0.
Nov 21 22:38:56 ubuntu dhclient: receive_packet failed on eth0: Network is down
Nov 21 22:43:56 ubuntu gdm[5267]: Restarting computer...
Nov 21 22:43:58 ubuntu init: tty5 main process (4667) killed by TERM signal
Nov 21 22:43:58 ubuntu init: tty2 main process (4669) killed by TERM signal
Nov 21 22:43:58 ubuntu init: tty3 main process (4671) killed by TERM signal
Nov 21 22:43:58 ubuntu init: tty6 main process (4674) killed by TERM signal
Nov 21 22:43:58 ubuntu init: tty4 main process (4666) killed by TERM signal
Nov 21 22:43:58 ubuntu init: tty1 main process (4673) killed by TERM signal
Nov 22 08:07:28 ubuntu NetworkManager: <information>^Istarting... 
Nov 22 08:07:28 ubuntu avahi-daemon[5206]: Found user 'avahi' (UID 105) and group 'avahi' (GID 111).
Nov 22 08:07:28 ubuntu avahi-daemon[5206]: Successfully dropped root privileges.
Nov 22 08:07:28 ubuntu avahi-daemon[5206]: avahi-daemon 0.6.17 starting up.
Nov 22 08:07:28 ubuntu avahi-daemon[5206]: Successfully called chroot().
Nov 22 08:07:28 ubuntu avahi-daemon[5206]: Successfully dropped remaining capabilities.
Nov 22 08:07:28 ubuntu avahi-daemon[5206]: No service found in /etc/avahi/services.
Nov 22 08:07:28 ubuntu avahi-daemon[5206]: Network interface enumeration completed.
Nov 22 08:07:28 ubuntu avahi-daemon[5206]: Registering HINFO record with values 'I686'/'LINUX'.
Nov 22 08:07:28 ubuntu avahi-daemon[5206]: Server startup complete. Host name is ubuntu.local. Local service cookie is 341024180.
Nov 22 08:07:34 ubuntu hcid[5438]: Bluetooth HCI daemon
Nov 22 08:07:34 ubuntu hcid[5438]: Starting SDP server
Nov 22 08:08:19 ubuntu NetworkManager: <information>^IUpdating allowed wireless network lists. 
Nov 22 08:08:20 ubuntu NetworkManager: <WARNING>^I nm_dbus_get_networks_cb (): error received: org.freedesktop.NetworkManagerInfo.NoNetworks - There are no wireless networks stored.. 
Nov 22 08:10:53 ubuntu gdm[5258]: Restarting computer...
Nov 22 08:10:56 ubuntu init: tty5 main process (4658) killed by TERM signal
Nov 22 08:10:56 ubuntu init: tty4 main process (4657) killed by TERM signal
Nov 22 08:10:56 ubuntu init: tty2 main process (4660) killed by TERM signal
Nov 22 08:10:56 ubuntu init: tty3 main process (4662) killed by TERM signal
Nov 22 08:10:56 ubuntu init: tty1 main process (4664) killed by TERM signal
Nov 22 08:10:56 ubuntu init: tty6 main process (4665) killed by TERM signal
Nov 22 22:10:56 ubuntu NetworkManager: <information>^Istarting... 
Nov 22 22:10:57 ubuntu avahi-daemon[5200]: Found user 'avahi' (UID 105) and group 'avahi' (GID 111).
Nov 22 22:10:57 ubuntu avahi-daemon[5200]: Successfully dropped root privileges.
Nov 22 22:10:57 ubuntu avahi-daemon[5200]: avahi-daemon 0.6.17 starting up.
Nov 22 22:10:57 ubuntu avahi-daemon[5200]: Successfully called chroot().
Nov 22 22:10:57 ubuntu avahi-daemon[5200]: Successfully dropped remaining capabilities.
Nov 22 22:10:57 ubuntu avahi-daemon[5200]: No service found in /etc/avahi/services.
Nov 22 22:10:57 ubuntu avahi-daemon[5200]: Network interface enumeration completed.
Nov 22 22:10:57 ubuntu avahi-daemon[5200]: Registering HINFO record with values 'I686'/'LINUX'.
Nov 22 22:10:57 ubuntu avahi-daemon[5200]: Server startup complete. Host name is ubuntu.local. Local service cookie is 508400292.
Nov 22 22:11:02 ubuntu hcid[5431]: Bluetooth HCI daemon
Nov 22 22:11:02 ubuntu hcid[5431]: Starting SDP server
Nov 22 22:11:53 ubuntu NetworkManager: <information>^IUpdating allowed wireless network lists. 
Nov 22 22:11:53 ubuntu NetworkManager: <WARNING>^I nm_dbus_get_networks_cb (): error received: org.freedesktop.NetworkManagerInfo.NoNetworks - There are no wireless networks stored.. 
Nov 22 22:12:51 ubuntu avahi-daemon[5200]: Got SIGTERM, quitting.
Nov 22 22:12:51 ubuntu NetworkManager: <WARNING>^I nm_signal_handler (): Caught signal 15, shutting down normally. 
Nov 22 22:12:51 ubuntu NetworkManager: <information>^ICaught terminiation signal 
Nov 22 22:12:51 ubuntu NetworkManager: <debug info>^I[1195787571.413350] nm_print_open_socks (): Open Sockets List: 
Nov 22 22:12:51 ubuntu NetworkManager: <debug info>^I[1195787571.413466] nm_print_open_socks (): Open Sockets List Done. 
Nov 22 22:12:51 ubuntu hcid[5431]: Got disconnected from the system message bus
Nov 22 22:13:02 ubuntu NetworkManager: <information>^Istarting... 
Nov 22 22:13:02 ubuntu NetworkManager: <information>^IUpdating allowed wireless network lists. 
Nov 22 22:13:02 ubuntu NetworkManager: <WARNING>^I nm_dbus_get_networks_cb (): error received: org.freedesktop.NetworkManagerInfo.NoNetworks - There are no wireless networks stored.. 
Nov 22 22:13:02 ubuntu avahi-daemon[6083]: Found user 'avahi' (UID 105) and group 'avahi' (GID 111).
Nov 22 22:13:02 ubuntu avahi-daemon[6083]: Successfully dropped root privileges.
Nov 22 22:13:02 ubuntu avahi-daemon[6083]: avahi-daemon 0.6.17 starting up.
Nov 22 22:13:02 ubuntu avahi-daemon[6083]: Successfully called chroot().
Nov 22 22:13:02 ubuntu avahi-daemon[6083]: Successfully dropped remaining capabilities.
Nov 22 22:13:02 ubuntu avahi-daemon[6083]: No service found in /etc/avahi/services.
Nov 22 22:13:02 ubuntu avahi-daemon[6083]: Network interface enumeration completed.
Nov 22 22:13:02 ubuntu avahi-daemon[6083]: Registering HINFO record with values 'I686'/'LINUX'.
Nov 22 22:13:02 ubuntu avahi-daemon[6083]: Server startup complete. Host name is ubuntu.local. Local service cookie is 1370485875.
Nov 22 22:15:22 ubuntu gdm[5251]: Restarting computer...
Nov 22 22:15:25 ubuntu init: tty5 main process (4651) killed by TERM signal
Nov 22 22:15:25 ubuntu init: tty3 main process (4655) killed by TERM signal
Nov 22 22:15:25 ubuntu init: tty6 main process (4658) killed by TERM signal
Nov 22 22:15:25 ubuntu init: tty2 main process (4653) killed by TERM signal
Nov 22 22:15:25 ubuntu init: tty1 main process (4657) killed by TERM signal
Nov 22 22:15:25 ubuntu init: tty4 main process (4650) killed by TERM signal
Nov 22 22:25:39 ubuntu NetworkManager: <information>^Istarting... 
Nov 22 22:25:39 ubuntu avahi-daemon[5193]: Found user 'avahi' (UID 105) and group 'avahi' (GID 111).
Nov 22 22:25:39 ubuntu avahi-daemon[5193]: Successfully dropped root privileges.
Nov 22 22:25:39 ubuntu avahi-daemon[5193]: avahi-daemon 0.6.17 starting up.
Nov 22 22:25:39 ubuntu avahi-daemon[5193]: Successfully called chroot().
Nov 22 22:25:39 ubuntu avahi-daemon[5193]: Successfully dropped remaining capabilities.
Nov 22 22:25:39 ubuntu avahi-daemon[5193]: No service found in /etc/avahi/services.
Nov 22 22:25:39 ubuntu avahi-daemon[5193]: Network interface enumeration completed.
Nov 22 22:25:39 ubuntu avahi-daemon[5193]: Registering HINFO record with values 'I686'/'LINUX'.
Nov 22 22:25:39 ubuntu avahi-daemon[5193]: Server startup complete. Host name is ubuntu.local. Local service cookie is 1718656327.
Nov 22 22:25:45 ubuntu hcid[5426]: Bluetooth HCI daemon
Nov 22 22:25:45 ubuntu hcid[5426]: Starting SDP server
Nov 22 22:26:34 ubuntu NetworkManager: <information>^IUpdating allowed wireless network lists. 
Nov 22 22:26:35 ubuntu NetworkManager: <WARNING>^I nm_dbus_get_networks_cb (): error received: org.freedesktop.NetworkManagerInfo.NoNetworks - There are no wireless networks stored.. 
```

---

### Post by lvleph on 2007-11-23
**sudo /etc/init.d/networking restart**
```
* Reconfiguring network interfaces...                                          wlan0: ERROR while getting interface flags: No such device
There is already a pid file /var/run/dhclient.wlan0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

SIOCSIFADDR: No such device
wlan0: ERROR while getting interface flags: No such device
wlan0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up wlan0.
```

---

### Post by lvleph on 2007-11-23
Okay, I reinstalled my system, so now I don't have the Hal error. I think that was caused by an update that I installed. Not sure which update at this point. I have everything working including WPA. However, for some reason I have to **sudo modprobe ndiswrapper** everytime I restart the computer, which I believe was the problem before. Then I have to tell it which network to connect to. Any help on this?

EDIT: I also didn't follow the WPA instructions, which means I have to keep my connection on roaming.

---

### Post by lvleph on 2007-11-23
I fixed my final problem by placing 

sudo modprobe ndiswrapper in /etc/rc.local

---

### Post by kevdog on 2007-11-23
Glad you found a workaround -- You could have also done the following:

echo ndiswrapper | sudo tee -a /etc/modules

---

