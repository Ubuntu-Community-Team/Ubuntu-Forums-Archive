---
title: "Help with wireless configuration."
date: 2008-06-17
forum: Networking &amp; Wireless
---

### Post by pokipoki08 on 2008-06-17
I have installed the Windows drivers for my Broadcom 4328 card successfully but unable to get an IP. I have tried Wicd, CLI method and also editing /etc/network/interfaces.

Please help.

dmesg (cropped)
```
ndiswrapper: driver bcmwl5 (Broadcom,09/20/2007, 4.170.25.12) loaded
ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 17 (level, low) -> IRQ 17
PCI: Setting latency timer of device 0000:03:00.0 to 64
ndiswrapper: using IRQ 17
iTCO_vendor_support: vendor-support=0
iTCO_wdt: Intel TCO WatchDog Timer Driver v1.02 (26-Jul-2007)
wlan1: ethernet device 00:17:f2:99:6b:08 using NDIS driver: bcmwl5, version: 0x4aa190c, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 14E4:4328.5.conf
iTCO_wdt: Found a ICH7-M TCO device (Version=2, TCOBASE=0x0460)
wlan1: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
```

ndiswrapper -l
```
bcmwl5 : driver installed
	device (14E4:4328) present
```

iwlist wlan1 scan
```
wlan1     Scan completed :
          Cell 01 - Address: 00:1E:52:78:CD:4F
                    ESSID:"My Airport"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.472 GHz (Channel 13)
                    Quality:28/100  Signal level:-78 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
```

/etc/network/interfaces
```
auto lo
iface lo inet loopback

auto wlan1
iface wlan1 inet dhcp
wpa-driver wext
wpa-ssid My Airport
wpa-ap-scan 1
wpa-proto WPA RSN
wpa-pairwise CCMP TKIP
wpa-group TKIP
wpa-key-mgmt WPA-PSK
wpa-psk 2ffcca01bee7c77bf0d7b2a06b7215b8b64d8f345a383bfab28a90ac216fc6c8

auto eth0
iface eth0 inet dhcp
```

sudo /etc/init.d/networking restart
```
Listening on LPF/wlan1/00:17:f2:99:6b:08
Sending on   LPF/wlan1/00:17:f2:99:6b:08
Sending on   Socket/fallback
DHCPDISCOVER on wlan1 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan1 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan1 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan1 to 255.255.255.255 port 67 interval 8
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
```

---

### Post by pokipoki08 on 2008-06-18
bump

---

