---
title: "Internet not wrong but network connects"
date: 2014-08-24
forum: Networking &amp; Wireless
---

### Post by billy16 on 2014-08-24
Hi all,

I'm stumped on this issue.  My network shows both via WiFi and wired so connectivity doesn't seem to be an issue.  The Internet however does not work.  All other wired and WiFi enabled devices work throughout my home.

I am running 14.04 have no special settings with my router and it seems to.have magically stopped working.  Additionally after the update my comp went into kernel panic and says something about init.   I figured I would fight that issue once Internet works again.  Currently I'm booting to an older kernel and having to hook up my phone and copy and paste my terminal outputs.  Below are some general codes I ran hopefully they help someone help me :-)

billy@BillyLaptop:~$ ifconfig eth0 Link encap:Ethernet HWaddr 00:1c:23:89:46:5f UP BROADCAST MULTICAST MTU:1500 Metric:1 RX packets:47 errors:0 dropped:0 overruns:0 frame:0 TX packets:48 errors:0 dropped:0 overruns:0 carrier:0 collisions:0 txqueuelen:1000 RX bytes:7200 (7.2 KB) TX bytes:8654 (8.6 KB) Interrupt:21 lo Link encap:Local Loopback inet addr:127.0.0.1 Mask:255.0.0.0 inet6 addr: ::1/128 Scope:Host UP LOOPBACK RUNNING MTU:65536 Metric:1 RX packets:2672 errors:0 dropped:0 overruns:0 frame:0 TX packets:2672 errors:0 dropped:0 overruns:0 carrier:0 collisions:0 txqueuelen:0 RX bytes:233285 (233.2 KB) TX bytes:233285 (233.2 KB) wlan0 Link encap:Ethernet HWaddr 00:1c:26:3a:65:aa inet addr:192.168.11.5 Bcast:192.168.11.255 Mask:255.255.255.0 inet6 addr: fe80::21c:26ff:fe3a:65aa/64 Scope:Link UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1 RX packets:2789 errors:0 dropped:0 overruns:0 frame:0 TX packets:180 errors:0 dropped:0 overruns:0 carrier:0 collisions:0 txqueuelen:1000 RX bytes:365198 (365.1 KB) TX bytes:32067 (32.0 KB) 


billy@BillyLaptop:~$ route -n Kernel IP routing table Destination Gateway Genmask Flags Metric Ref Use Iface 0.0.0.0 192.168.11.1 0.0.0.0 UG 0 0 0 wlan0 192.168.11.0 0.0.0.0 255.255.255.0 U 9 0 0 wlan0 


billy@BillyLaptop:~$ nmcli dev list iface wlan0 GENERAL.DEVICE: wlan0 GENERAL.TYPE: 802-11-wireless GENERAL.VENDOR: Broadcom Corporation GENERAL.PRODUCT: Wireless 1390 WLAN Mini-Card GENERAL.DRIVER: b43 GENERAL.DRIVER-VERSION: 3.13.0-32-generic GENERAL.FIRMWARE-VERSION: N/A GENERAL.HWADDR: 00:1C:26:3A:65:AA GENERAL.STATE: 100 (connected) GENERAL.REASON: 0 (No reason given) GENERAL.UDI: /sys/devices/pci0000:00/0000:00:05.0/0000:0b:00.0/ssb0:0/net/wlan0 GENERAL.IP-IFACE: wlan0 GENERAL.NM-MANAGED: yes GENERAL.AUTOCONNECT: yes GENERAL.FIRMWARE-MISSING: no GENERAL.CONNECTION: /org/freedesktop/NetworkManager/ActiveConnection/2 CAPABILITIES.CARRIER-DETECT: no CAPABILITIES.SPEED: 48 Mb/s CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{0} CONNECTIONS.AVAILABLE-CONNECTIONS[1]: 58555ac2-5665-41c6-98db-633d44173cb7 | HarperBentley WIFI-PROPERTIES.WEP: yes WIFI-PROPERTIES.WPA: yes WIFI-PROPERTIES.WPA2: yes WIFI-PROPERTIES.TKIP: yes WIFI-PROPERTIES.CCMP: yes WIFI-PROPERTIES.AP: yes WIFI-PROPERTIES.ADHOC: yes AP[1].SSID: 'TG862G12' AP[1].BSSID: 14:AB:F0:31:D1:10 AP[1].MODE: Infrastructure AP[1].FREQ: 2462 MHz AP[1].RATE: 54 MB/s AP[1].SIGNAL: 50 AP[1].SECURITY: WPA2 AP[1].ACTIVE: no AP[2].SSID: '2WIRE322' AP[2].BSSID: B8:E6:25:26:7A:51 AP[2].MODE: Infrastructure AP[2].FREQ: 2457 MHz AP[2].RATE: 54 MB/s AP[2].SIGNAL: 60 AP[2].SECURITY: WPA WPA2 AP[2].ACTIVE: no AP[3].SSID: 'HarperBentley' AP[3].BSSID: 00:24:A5:34:98:19 AP[3].MODE: Infrastructure AP[3].FREQ: 2412 MHz AP[3].RATE: 54 MB/s AP[3].SIGNAL: 78 AP[3].SECURITY: WPA WPA2 AP[3].ACTIVE: yes IP4.ADDRESS[1]: ip = 192.168.11.5/24, gw = 192.168.11.1 IP4.DNS[1]: 192.168.11.1 IP4.DOMAIN[1]: satx.rr.com DHCP4.OPTION[1]: domain_name = satx.rr.com DHCP4.OPTION[2]: expiry = 1408997236 DHCP4.OPTION[3]: broadcast_address = 192.168.11.255 DHCP4.OPTION[4]: dhcp_message_type = 5 DHCP4.OPTION[5]: dhcp_lease_time = 172800 DHCP4.OPTION[6]: ip_address = 192.168.11.5 DHCP4.OPTION[7]: routers = 192.168.11.1 DHCP4.OPTION[8]: subnet_mask = 255.255.255.0 DHCP4.OPTION[9]: domain_name_servers = 192.168.11.1 DHCP4.OPTION[10]: network_number = 192.168.11.0 DHCP4.OPTION[11]: dhcp_server_identifier = 192.168.11.1

---

### Post by Doug S on 2014-08-25
It would help us if you could put your listing stuff inside of code tags to protect the formatting so that we can read it. I converted one of them myself:```
billy@BillyLaptop:~$ ifconfig
eth0    Link encap:Ethernet HWaddr 00:1c:23:89:46:5f
    UP BROADCAST MULTICAST MTU:1500 Metric:1
    RX packets:47 errors:0 dropped:0 overruns:0 frame:0 TX
    packets:48 errors:0 dropped:0 overruns:0 carrier:0
    collisions:0 txqueuelen:1000
    RX bytes:7200 (7.2 KB) TX bytes:8654 (8.6 KB)
    Interrupt:21

lo    Link encap:Local Loopback inet addr:127.0.0.1 Mask:255.0.0.0
    inet6 addr: ::1/128
    Scope:Host UP LOOPBACK RUNNING MTU:65536 Metric:1
    RX packets:2672 errors:0 dropped:0 overruns:0 frame:0
    TX packets:2672 errors:0 dropped:0 overruns:0 carrier:0
    collisions:0 txqueuelen:0 RX bytes:233285 (233.2 KB) TX bytes:233285 (233.2 KB)

wlan0    Link encap:Ethernet HWaddr 00:1c:26:3a:65:aa
    inet addr:192.168.11.5 Bcast:192.168.11.255 Mask:255.255.255.0
    inet6 addr: fe80::21c:26ff:fe3a:65aa/64
    Scope:Link UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
    RX packets:2789 errors:0 dropped:0 overruns:0 frame:0
    TX packets:180 errors:0 dropped:0 overruns:0 carrier:0
    collisions:0 txqueuelen:1000 RX bytes:365198 (365.1 KB) TX bytes:32067 (32.0 KB)
```My suggestion, just as a test to try to eliminate variables, is to disable your wlan0 interface and try the eth0 interface (notice how it does not have an IP address right now).

---

### Post by varunendra on 2014-08-25
Please follow the instructions in this post to download and run 'wireless_script' (experimental version) and post back the report it generates : [http://ubuntuforums.org/showpost.php?p=13024222](http://ubuntuforums.org/showpost.php?p=13024222)

If you have to open the generated report file in Windows to copy-paste its contents here, better attach the file itself to avoid messing up of formatting.

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Use Code Tags" link in my signature.

---

