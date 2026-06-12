---
title: "RTL8188FTV wifi loads but does not connect"
date: 2024-05-19
forum: Networking &amp; Wireless
---

### Post by teledyn on 2024-05-19
The [previous thread]("https://ubuntuforums.org/showthread.php?t=2433675&") issue is not resolved, and perhaps no longer valid as the rtl8188fu device is now covered by the kernel rtl8xxxu? It isn't clear from their git pages whether any of the prior rtl8188fu drivers are considered 'better', all are older than the kernel driver, and the dongle is recognized using the driver in UbuntuStudio 24.04 6.8.0-31-lowlatency, but it is not connecting.

dmesg recognizes the dongle:
```

[63322.625818] usb 1-1.1: new high-speed USB device number 6 using ehci-pci
[63322.718181] usb 1-1.1: New USB device found, idVendor=0bda, idProduct=f179, bcdDevice= 0.00
[63322.718198] usb 1-1.1: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[63322.718203] usb 1-1.1: Product: 802.11n
[63322.718207] usb 1-1.1: Manufacturer: Realtek
[63322.718211] usb 1-1.1: SerialNumber: 00E0248FD781
[63322.841902] usb 1-1.1: RTL8188FU rev B (SMIC) romver 0, 1T1R, TX queues 2, WiFi=1, BT=0, GPS=0, HI PA=0
[63322.841913] usb 1-1.1: RTL8188FU MAC: 00:e0:24:8f:d7:81
[63322.841916] usb 1-1.1: rtl8xxxu: Loading firmware rtlwifi/rtl8188fufw.bin
[63322.842221] usb 1-1.1: Firmware revision 4.0 (signature 0x88f1)
[63324.047428] rtl8xxxu 1-1.1:1.0 wlx00e0248fd781: renamed from wlan0

```

Here is a comparison between the HP laptop internal RTL8723BE (wlo1) and the RTL8188etv, hopefully redacting sensitive things:

```

wlo1      IEEE 802.11  ESSID:"<ESSID>"  
          Mode:Managed  Frequency:2.447 GHz  Access Point: <MAC>   
          Bit Rate=72.2 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr=2347 B   Fragment thr:off
          Encryption key:off
          Power Management:on
          Link Quality=70/70  Signal level=-14 dBm  <--- this value seems really suspect!
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:2777   Missed beacon:0

wlx00e0248fd781  IEEE 802.11  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=30 dBm   
          Retry short limit:7   RTS thr=2347 B   Fragment thr:off
          Encryption key:off
          Power Management:off

```

So it is there, but ifconfig says it is both UP and DOWN and setting freq, essid etc with iwconfig has no effect; the values change in iwconfig, but it still does not connect.
```

wlo1: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet <ip4>  netmask 255.255.255.0  broadcast 192.168.0.255
        inet6 <ip6>  prefixlen 64  scopeid 0x20<link>
        ether <MAC>  txqueuelen 1000  (Ethernet)
        RX packets 2411640  bytes 1404071476 (1.4 GB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 1971869  bytes 278238801 (278.2 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

wlx00e0248fd781: flags=4099<UP,BROADCAST,MULTICAST>  mtu 1500
        ether <MAC>  txqueuelen 1000  (Ethernet)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

```

`lsusb` shows this as `Bus 002 Device 004: ID 0bda:f179 Realtek Semiconductor Corp. RTL8188FTV 802.11b/g/n 1T1R 2.4G WLAN Adapter` and I have tested the laptop with another (supported) dongle to assure myself it can run two at once.

Network Manager describes the interface:
```

GENERAL.DEVICE:                         wlx<IF from MAC [IF4]>
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.DBUS-PATH:                      /org/freedesktop/NetworkManager/Devices/
8
GENERAL.VENDOR:                         Realtek Semiconductor Corp.
GENERAL.PRODUCT:                        RTL8188FTV 802.11b/g/n 1T1R 2.4G WLAN Ad
apter
GENERAL.DRIVER:                         rtl8xxxu
GENERAL.DRIVER-VERSION:                 6.8.0-31-lowlatency
GENERAL.FIRMWARE-VERSION:               N/A
GENERAL.HWADDR:                         <MAC 'wlx<IF from MAC [IF4]>' [IF4]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          30 (disconnected)
GENERAL.REASON:                         42 (The supplicant is now available)
GENERAL.IP4-CONNECTIVITY:               1 (none)
GENERAL.IP6-CONNECTIVITY:               1 (none)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:12.0/usb
1/1-1/1-1.2/1-1.2:1.0/net/wlx<IF from MAC [IF4]>
GENERAL.PATH:                           pci-0000:00:12.0-usb-0:1.2:1.0
GENERAL.IP-IFACE:                       --
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     --
GENERAL.CON-UUID:                       --
GENERAL.CON-PATH:                       --
GENERAL.METERED:                        unknown
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     unknown
CAPABILITIES.IS-SOFTWARE:               no
CAPABILITIES.SRIOV:                     no
INTERFACE-FLAGS.UP:                     yes
INTERFACE-FLAGS.LOWER-UP:               no
INTERFACE-FLAGS.CARRIER:                no
INTERFACE-FLAGS.PROMISC:                no
WIFI-PROPERTIES.WEP:                    yes
WIFI-PROPERTIES.WPA:                    yes
WIFI-PROPERTIES.WPA2:                   yes
WIFI-PROPERTIES.TKIP:                   yes
WIFI-PROPERTIES.CCMP:                   yes
WIFI-PROPERTIES.AP:                     yes
WIFI-PROPERTIES.ADHOC:                  no
WIFI-PROPERTIES.2GHZ:                   yes
WIFI-PROPERTIES.5GHZ:                   no
WIFI-PROPERTIES.6GHZ:                   no
WIFI-PROPERTIES.MESH:                   no
WIFI-PROPERTIES.IBSS-RSN:               no
IP4.GATEWAY:                            --
IP6.GATEWAY:                            --
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: --

##### module parameters #################

[rtl8723be] (that works)
ant_sel: 1
aspm: 1
debug_level: 0
debug_mask: 0
disable_watchdog: N
fwlps: Y
ips: Y
msi: N
swenc: N
swlps: N

[rtl8xxxu] (that doesn't)
debug: 0
dma_agg_pages: -1
dma_aggregation: N
dma_agg_timeout: -1
ht40_2g: N


```
Netplan does not list the device, which is interesting as it does list another that I'd used to test two wifi adapters at once, but is no longer installed, replaced by the RTL8188FTV.

In 30 years of Linux, I think this is the first time I've seen a wifi dongle that passes all the tests except actually connecting! I'm stumped (or need more coffee). Any advice, guidance, wild-guesses or additional test results needed, please do let me know!

---

### Post by praseodym on 2024-05-20
Check if more than one driver is loaded:

lsmod

---

